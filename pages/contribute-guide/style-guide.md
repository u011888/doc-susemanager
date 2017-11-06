---
title: Markdown Style Guide
keywords: style, guide
sidebar: frontpage_sidebar
toc: true
permalink: style-guide.html
summary: This style guide will help you make basic formatting decisions for your contributions. It helps ensure consistent styling, which can be difficult to guarantee with markdown. If you notice something that can be improved please submit a pull request for this page.
---

## A Readable and portable Markdown style guide by [cirosantilli](https://github.com/cirosantilli/markdown-style-guide)

Licensing: [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/)




## Block elements

### Line breaks

Avoid line breaks, as they don't have generally accepted semantic meaning.

In the rare case you absolutely need them, end a lines with exactly two spaces.

### Headers

#### Option header:atx {#option-header-atx}

Bad:

    Header 1
    ========

    Header 2
    --------

    ### Header 3

Good:

    # Header 1

    ## Header 2

    ### Header 3

-   Rationale: advantages over Setex:

    -   easier to write because in Setex you have to match
        the number of characters in both lines for it to look good

    -   works for all levels, while Setex only goes up to level 2

    -   occupy only one screen line, while Setex occupies 2

    Advantages of Setex

    -   more visible. Not very important if you have syntax highlighting.

-   Include a single space between the `#` and the text of the header.

    Bad:

        #Header

        #..Header

    Good:

        # Header

-   *Don't* use the closing `#` character.

    Bad:

        # Header #

    Good:

        # Header

    Rationale: easier to maintain.

-   *Don't* add spaces before the number sign `#`.

    Bad:

        .# Header

    Good:

        # Header

#### Option header:setex {#option-header-setex}

Bad:

    # Header 1

    ## Header 2

    ### Header 3

Good:

    Header 1
    ========

    Header 2
    --------

    ### Header 3

---

-   *Don't* skip header levels.

    Bad:

        # Header 1

        ### Header 3

    Good:

        # Header 1

        ## Header 2

-   Surround headers by a single empty line except at the beginning of the file.

    Bad:

        Before.
        # Header 1

        ## Header 2
        After.

    Good:

        Before.

        # Header 1

        ## Header 2

        After.

    Bad:

        Before.
        Header 1
        ========

        ## Header 2
        -----------
        After.

    Good:

        Before.

        Header 1
        ========

        ## Header 2
        -----------

        After.

-   *Avoid* using two headers with the same content in the same markdown file.

    Rationale: many markdown engines generate IDs for headers based on the header content.

    Bad:

        # Dogs

        ## Anatomy

        # Cats

        ## Anatomy

    Good:

        # Dogs

        ## Anatomy of the dog

        # Cats

        ## Anatomy of the cat

#### Top-level header

If you target HTML output, write your documents so that it will have one
and only one `h1` element as the first thing in it that serves as the title of the document.
This is the HTML top-level header.

How this `h1` is produced may vary depending on your exact technology stack:
some stacks may generate it from metadata, for example Jekyll through the front-matter.

Storing the top-level header as metadata has the advantage that it can be reused elsewhere more easily,
e.g. on a global index, but the downside of lower portability.

If your target stack does not generate the top-level header in another way,
include it in your markdown file. E.g., GitHub.

Top-level headers on index-like files such as `README.md` or `index.md`
should serve as a title for their parent directory.

Downsides of top-level headers:

-   take up one header level. This means that there are only 5 header levels left,
    and each new header will have one extra `#`, which looks worse and is harder to write.

-   duplicate filename information, which most often can already be seen on a URL.
    In most cases, the filename can be trivially converted to a top-level,
    e.g.: `some-filename.md` to `Some filename`.

Advantages of top-level headers:

- more readable than URL's, especially for non-technically inclined users.

#### Header case

-   Use an upper case letter as the first letter of a header,
    unless it is a word that always starts with lowercase letters, e.g. computer code.

    Good:

        # Header

    Good, computer code that always starts with lower case:

        # int main

    Bad:

        # header

-   The other letters have the same case they would have in the middle of a sentence.

    Good:

        # The header of the example

    Bad:

        # The Header of the Example

    As an exception, [title case](http://en.wikipedia.org/wiki/Title_case#Title_case)
    may be optionally used for the [top-level header](#top-level-header).
    Use this exception sparingly, in cases where typographical perfection is important,
    e.g.: `README` of a project.

    Rationale: why not [Title case](http://en.wikipedia.org/wiki/Title_case#Title_case) for all headers?
    It requires too much effort to decide if edge-case words should be upper case or not.

#### End of a header

Indicate the end of a header's content that is not followed by a new header by an horizontal rule:

    # Header

    Content

    ---

    Outside header.

#### Header length

Keep headers as short as possible.

Instead of using a huge sentence, make the header a summary to the huge sentence,
and write the huge sentence as the first paragraph beneath the header.

Rationale: it is easier to refer to the header later,
specially if automatic IDs or a TOC are generated by the implementation.

Good:

    # Huge header

    Huge header that talks about a complex subject.

Bad:

    # Huge header that talks about a complex subject

#### Punctuation at the end of headers

*Don't* add a trailing colon `:` to headers.

Rationale: every header is an introduction to what is about to come next,
which is exactly the function of the colon.

*Don't* add a trailing period `.` to headers.

Rationale: every header consists of a single short sentence,
so there is not need to add a sentence separator to it.

Good:

    # How to do make omelet

Bad:

    # How to do make omelet:

Bad:

    # How to do make omelet.

#### Header synonyms

Headers serve as an index for users searching for keywords.

For this reason, you may want to give multiple keyword possibilities for a given header.

To do so, simply create a synonym header with empty content just before its main header.

E.g.:

    # Purchase

    # Buy

    You give money and get something in return.

Every empty header with the same level as the following one is assumed to be a synonym.
This is not the case if levels are different:

    # Animals

    ## Dog

### Blockquotes

-   Follow the greater than marker `>` by one space.

    Good:

        > a

    Bad:

        >a

    Bad, 2 spaces:

        >  a

-   Use a greater than sign for every line, including wrapped.

    Bad:

        > Long line
        that was wrapped.

    Good:

        > Long line
        > that was wrapped.

-   *Don't* use empty lines inside a single block quote.

    Good:

        > a
        >
        > b

    Bad:

        > a

        > b

### Lists

#### Marker

##### Unordered

###### Option list-marker:hyphen {#option-list-marker-hyphen}

Use the hyphen marker.

Good:

    - a
    - b

Bad:

    * a
    * b

<!-- -->

    + a
    + b

Rationale:

- asterisk `*` can be confused with bold or italic markers.
- plus sign `+` is not popular

Downsides:

- `*` and `+` are more visible. `*` is more visible

###### Option list-marker:asterisk {#option-list-marker-asterisk}

Use `*`.

###### Option list-marker:plus {#option-list-marker-plus}

Use `+`.

##### Ordered

Prefer lists only with the marker `1.` for ordered lists,
unless you intend to refer to items by their number in the same markdown file or externally.

Prefer unordered lists unless you intent to refer to items by their number.

Best, we will never refer to the items of this list by their number:

    - a
    - c
    - b

Better, only `1.`:

    1. a
    1. c
    1. b

Worse, we will never refer to the items of this list by their number:

    1. a
    2. c
    3. b

Acceptable, refer to them in the text:

    The ouput of the `ls` command is of the form:

        drwx------  2 ciro ciro        4096 Jul  5  2013 dir0
        drwx------  4 ciro ciro        4096 Apr 27 08:00 dir1
        1           2

    Where:

    1. permissions
    2. number of files directory contains

Acceptable, meant to be referred by number from outside of the markdown file:

    Terms of use.

    1. I will not do anything illegal.
    2. I will not do anything that can harm the website.

Rationale:

-   If you want to change a list item in the middle of the list,
    you don't have to modify all items that follow it.

    Diffs will show only the significant line which was modified.

-   Content stays aligned without extra effort if the numbers reach 2 digits. E.g.: the following is not aligned:

        9. a
        10. b

-   References break when a new list item is added. To reduce this problem:

    - keep references close to the list so authors are less likely to forget to update them
    - when referring from an external document, always refer to an specific version of the markdown file

#### Spaces after list marker

##### Option list-space:mixed {#option-list-space-mixed}

-   If the content of every item of the list is fits in a single paragraph, use **1** space.

-   Otherwise, for every item of the list:

    -   use **3** spaces for unordered lists.

    -   use **2** spaces for ordered lists.
        One less than for unordered because the marker is 2 chars long.

Bad, every item is one line long:

    -   a
    -   b

Good:

    - a
    - b

Bad, every item is one line long:

    1.  a
    1.  b

Good:

    1. a
    1. b

Bad: item is longer than one line:

    - item that
      is wrapped

    - item 2

Good:

    -   item that
        is wrapped

    -   item 2

Bad: item is longer than one line:

    - a

      par

    - b

Good:

    -   a

        par

    -   b

##### Option list-space:1 {#option-list-space-1}

Always add one space to the list marker.

Bad, 3 spaces:

    -   a

        b

    -   c

Good:

    - a

      b

    - c

Bad, 2 spaces:

    1.  a

        b

    1.  c

Good:

    1. a

       b

    1. c

##### Rationale: list-space mixed vs 1

The advantages of `list-space:1` are that

-   it removes the decision of how many spaces you should put after the list marker:
    it is always one.

    We could choose to always have list content indented as:

        -   a
        -   b

    but that is ugly.

-   You never need to change the indentation of the entire list because of a new item.

    This may happen in `list-space:mixed` if you have:

        - a
        - b

    and will add a multi-line item:

        -   a

        -   b

        -   c

            d

    Note how `a` and `b` were changed because of `c`.

The disadvantages of `list-space:1`

-   creates three indentation levels for the language:

    - 4 for indented code blocks
    - 3 for ordered lists
    - 2 for unordered lists

    That means that you cannot easily configure your editor indent level to deal with all cases
    when you want to change the indentation level of multiple list item lines.

-   Is not implemented consistently across editors.

    In particular what should happen at:

        - a

                code

    This (2 spaces):

        <pre><code>  code

    Or no spaces:

        <pre><code>code

    Likely the original markdown said no spaces:

    > To put a code block within a list item, the code block
    > needs to be indented twice — 8 spaces or two tabs

    But many implementations did otherwise.

    CommonMark [adds the 2 spaces](http://spec.commonmark.org/0.12/#example-176).

#### Indentation of content inside lists

The indentation level of what comes inside list and of further list items
must be the same as the first list item.

Bad:

    -   item that
      is wrapped

    -   item 2

Good:

    -   item that
        is wrapped

    -   item 2

Bad:

    -   item 1

      Content 1

    -   item 2

          Content 2

Good (if it matches your spaces after list marker style):

    -   item 1

        Content 1

    -   item 2

        Content 2

Bad:

    - item 1

        Content 1

    - item 2

        Content 2

Good (if it matches your spaces after list marker style):

    - item 1

      Content 1

    - item 2

      Content 2

Avoid starting a list item directly with indented code blocks because that is not consistently implemented.
[CommonMark states that](http://spec.commonmark.org/0.12/#example-176) a single space is assumed in that case:

    -     code

      a

#### Empty lines inside lists

If every item of a list is a single line long, don't add empty lines between items.
Otherwise, add empty lines between every item.

Bad, single lines:

    - item 1

    - item 2

    - item 3

Good:

    - item 1
    - item 2
    - item 3

Bad, multiple lines:

    -   item that
        is wrapped
    -   item 2
    -   item 3

Good:

    -   item that
        is wrapped

    -   item 2

    -   item 3

Bad, multiple lines:

    -   item 1

        Paragraph.

    -   item 2
    -   item 3

Good:

    -   item 1.

        Paragraph.

    -   item 2

    -   item 3

Bad, multiple lines:

    -   item 1

        - item 11
        - item 12
        - item 13

    -   item 2
    -   item 3

Good:

    -   item 1

        - item 11
        - item 12
        - item 13

    -   item 2

    -   item 3

Rationale: it is hard to tell where multi-line list items start and end without empty lines.

#### Empty lines around lists

Surround lists by one empty line.

Bad:

    Before.
    - item
    - item
    After.

Good:

    Before.

    - list
    - list

    After.

#### Case of first letter of list item

Each list item has the same case as it would have if it were concatenated with the sentence that comes before the list.

Good:

    I want to eat:

    - apples
    - bananas
    - grapes

because it could be replaced with:

    I want to eat apples
    I want to eat babanas
    I want to eat grapes

Good:

    To ride a bike you have to:

    - get on top of the bike. This step is easy.
    - put your foot on the pedal.
    - push t the pedal. This is the most fun part.

because it could be replaced with:

    To ride a bike you have to get on top of the bike. This step is easy.
    To ride a bike you have to put your foot on the pedal.
    To ride a bike you have to push the pedal. This is the most fun part.

Good:

    # How to ride a bike

    - Get on top of the bike.
    - Put your feet on the pedal.
    - Make the pedal turn.

because it could be replaced with:

    # How to ride a bike

    Get on top of the bike.
    Put your feet on the pedal.
    Push the the pedal.

#### Punctuation at the end of list items

Punctuate at the end of list items if either it:

- contains multiple sentences or paragraphs
- starts with an upper case letter

Otherwise, omit the punctuation if it would be a period.

Bad, single sentences:

    - apple.
    - banana.
    - orange.

Good:

    - apple
    - banana
    - orange

Idem:

    - go to the market
    - then buy some fruit
    - finally eat the fruit

Good, not terminated by period but by other punctuation.

    - go to the marked
    - then buy fruit?
    - of course!

Bad, multiple sentences:

    - go to the market
    - then buy some fruit. Bad for wallet
    - finally eat the fruit. Good for tummy

Good:

    - go to the market
    - then buy some fruit. Bad for wallet.
    - finally eat the fruit. Good for tummy.

Note: nothing forbids one list item from ending in period while another in the same list does not.

Bad, multiple paragraphs:

    -   go to the market

    -   then buy some fruit

        Bad for wallet

    -   finally eat the fruit

        Good for tummy

Good:

    -   go to the market

    -   then buy some fruit.

        Bad for wallet.

    -   finally eat the fruit.

        Good for tummy.

Bad, starts with upper case:

    - Go to the market
    - Then buy some fruit
    - Finally eat the fruit

Good:

    - Go to the market.
    - Then buy some fruit.
    - Finally eat the fruit.

### Definition lists

*Avoid* the definition list extension since it is not present
in many implementations nor in CommonMark.

Instead, use either:

-   formated lists:

    - format the item be defined as either of bold, link or code
    - separate the item from the definition with a colon and a space `:.`
    - don't align definitions as it is harder to maintain and does not show on the HTML output

    Good:

        - **apple**: red fruit
        - **dog**: noisy animal

    Good:

        -   **apple**: red fruit.

            Very tasty.

        -   **dog**: noisy animal.

            Not tasty.

    Good:

        - [apple](http://apple.com): red fruit
        - [dot](http://dog.com): red fruit

    Good:

        - `-f`: force
        - `-r`: recursive

    Bad, no colon:

        - **apple** red fruit
        - **dog** noisy animal

    Bad, space between term and colon:

        - **apple** : red fruit
        - **dog** : noisy animal

    Bad, definitions aligned:

        - **apple**: red fruit
        - **dog**:   noisy animal

-   headers.

    Good:

        # Apple

        Red fruit

        # Dog

        Noisy animal

### Code blocks

#### Option code:fenced {#option-code-fenced}

Only use fenced code blocks.

Comparison to indented code blocks:

- disadvantage: not part of the original markdown, thus less portable, but added to CommonMark.
- advantage: many implementations, including GitHub's, allow to specify the code language with it

*Don't* indent fenced code blocks.

Always specify the language of the code is applicable.

Good:

    ```ruby
    a = 1
    ```

Bad:

    ```
    a = 1
    ```

#### Option code:indented {#option-code-indented}

Only use indented code blocks.

Indent indented code blocks with 4 spaces.

---

Code blocks must be surrounded by one empty line.

Prefer to end the phrase before a code block with a colon `:`.

Good:

    Use this code to blow up your PC:

        sudo rm -rf /

Bad, no colon

    Use this code to blow up your PC

        sudo rm -rf /

### Horizontal rules

*Don't* use horizontal rules except to indicate the [End of a header](#end-of-a-header).

Rationale:

-   headers are better section separators since they say what a section is about.

-   horizontal rules don't have a generally accepted semantic meaning.
    This guide gives them one.

Use 3 hyphens without spaces:

    ---

### Tables

Extension.

-   Surround tables by one empty line.

-   Don't indent tables.

-   Surround every line of the table by pipes.

-   Align all border pipes vertically.

-   Separate header from body by hyphens except at the aligned pipes `|`.

-   Pipes `|` must be surrounded by a space, except for outer pipes
    which only get one space internally, and pipes of the hyphen separator line.

-   Column width is determined by the longest cell in the column.

Good table:

    Before.

    | h    | Long header |
    |------|-------------|
    | abc  | def         |
    | abc2 | def2        |

    After.

Rationale:

-   unaligned tables tables are easier to write, but aligned tables are more readable,
    and people read code much more often than they edit it.

-   preceding pipes make it easier to determine where a table starts and ends.
    Trailing pipes make it look better because of symmetry.

-   there exist tools which help keeping the table aligned.
    For example, Vim has the [Tabular plugin](https://github.com/godlygeek/tabular)
    which allows to align the entire table with `:Tabular /|`.

-   why no spaces around pipes of the hyphen separator line, i.e.: `|---|` instead of `| - |`?
    No spaces looks better, works on GitHub. Downside: harder to implement automatic alignment in editors,
    as it requires a special rule for the separator line.

### Separate consecutive elements

Separate consecutive:

- lists
- indented code blocks
- blockquotes
- list followed by external code block

with an empty HTML comment `<!-- -->`.

<!-- -->

    - list 1
    - list 1

    <!-- -->

    - list 2
    - list 2

<!-- -->

        code 1
        code 1

    <!-- -->

        code 2
        code 2

<!-- -->

    > blockquote 1
    > blockquote 1

    <!-- -->

    > blockquote 2
    > blockquote 2

<!-- -->

    - list
    - list

    <!-- -->

        code outside list
        code outside list

## Span elements

*Don't* use inner spaces.

Good:

    **bold**
    `code`
    [link](http://a.com)
    [text][name]

Bad:

    ** bold **
    ` code `
    [ link ]( http://a.com )
    [text] [name]

For inline code in which the space is crucial:

- explain in writing that the spaces must be there
- add something after the space if possible

Good:

    Use the hyphen marker followed by one space `- a`  for unordered lists.

Rationale: most browsers don't render the surrounding spaces nor add them to the clipboard on copy.

### Links

#### Reference-style links

Links:

-   use the trailing `[]` on implicit links.

    Good:

        [a][]

    Bad:

        [a]

    Rationale: while omitting `[]` works on most major implementations,
    it is not specified in the documentation not implemented in the original markdown.

Definitions:

- must be the last thing on the file
- must be sorted alphabetically by the ID
- don't enclose URLs by angle brackets
- align URLs and link names as in a table
- link IDs use only lowercase letters. Rationale: they are case insensitive,
- lowercase only is easier to write, and the readability gain of mixed case is not very big.

Good:

    [id2]:     http://long-url.com
    [long id]: http://a.com        "name 1"

Bad, not ordered by id:

    [b]: http://a.com
    [a]: http://b.com

Bad, not aligned:

    [id]: http://id.com
    [long id]: http://long-id.com

#### Single or double quote titles

Use double quotes, *not* single quotes.

Rationale: single quotes do not work in all major implementations, double quotes do.

### Emphasis

#### Bold

Use double asterisk format: `**bold**`.

Rationale: more common and readable than the double underline `__bold__` form.

#### Italic

Use single asterisk format: `*italic*`.

Rationale:

- more common and readable than the underscore form
- consistent with the bold format, which also uses asterisks

#### Uppercase for emphasis

*Don't* use uppercase for emphasis: use emphasis constructs like **bold** or *italic* instead.

Rationale: CSS has `text-transform:uppercase` which can easily achieve the same effect consistently
across the entire website if you really want uppercase letters.

#### Emphasis vs headers

*Don't* use emphasis elements (bold or italics) to introduce a multi line named section: use headers instead.

Rationale: that is exactly the semantic meaning of headers,
and not necessarily that of emphasis elements. As a consequence,
many implementations add useful behaviors to headers and not to emphasis elements,
such as automatic `id` to make it easier to refer to the header later on.

Good:

    # How to make omelets

    Break an egg.

    ...

    # How to bake bread

    Open the flour sack.

    ...

Bad:

    **How to make omelets:**

    Break an egg.

    ...

    **How to bake bread:**

    Open the flour sack.

    ...

### Automatic links

#### Automatic links without angle brackets

-   *Don't* use automatic links without angle brackets.

    Good:

        <http://a.com>

    Bad:

        http://a.com

    Rationale: it is an extension, `<>` is easy to type and saner.

-   If you want literal links which are not autolinks, enclose them in code blocks. E.g.:

        `http://not-a-link.com`

    Rationale: many tools automatically interpret any word starting with `http` as a link.

#### Content of automatic links

All automatic links must start with the string `http`.

In particular, *don't* use relative automatic links.
Use bracket links instead for that purpose.

Good:

    [file.html](file.html)

Bad:

    <file.html>

Good:

    <https://github.com>

Bad:

    <github.com>

Rationale: it is hard to differentiate automatic links from HTML tags.
What if you want a relative link to a file called `script`?

#### Email automatic links

*Don't* use email autolinks `<address@example.com>`. Use raw HTML instead.

Rationale: the original markdown specification states it:

> "performs a bit of randomized decimal and hex entity-encoding
> to help obscure your address from address-harvesting spambots".

Therefore, the output is random, ugly, and as the spec itself mentions:

> but an address published in this way will probably eventually start receiving spam


