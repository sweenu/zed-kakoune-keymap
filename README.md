# Kakoune keymap for Zed
This keymap tries to emulate kakoune's behavior as close as possible, using vim and helix mode in Zed.

## Kakoune Keymap Implementation Status for Zed

This document shows all Kakoune keybindings organized by section, with checkboxes indicating implementation status in Zed.

**Summary:** 98/211 keys implemented

---

### Insert mode

- [x] **`<esc>`** - leave insert mode
- [x] **`<backspace>`** - delete characters before cursors
- [x] **`<del>`** - delete characters under cursors
- [x] **`<left>, <right>, <up>, <down>`** - move the cursors in given direction
- [x] **`<home>`** - move cursors to line begin
- [x] **`<end>`** - move cursors to end of line
- [x] **`<c-r>`** - insert contents of the register given by next key
- [x] **`<c-v>`** - insert next keystroke directly into the buffer, without interpreting it
- [ ] **`<c-u>`** - commit changes up to now as a single undo group
  - *Not implementable: Zed's undo system doesn't support explicit undo groups via keybinding*
- [x] **`<a-;>, <a-semicolon>`** - escape to normal mode for a single command

### Insert mode completion

- [ ] **`<c-o>`** - toggle automatic completion
  - *Not implementable: Zed has different completion toggle mechanism*
- [x] **`<c-n>`** - select next completion candidate
- [x] **`<c-p>`** - select previous completion candidate
- [ ] **`<c-x> f`** - explicit file completion
  - *Not implementable: Zed doesn't support Kakoune's explicit completion query system with sub-modes*
- [ ] **`<c-x> w`** - explicit word completion (current buffer)
  - *Not implementable: Zed doesn't support Kakoune's explicit completion query system with sub-modes*
- [ ] **`<c-x> W`** - explicit word completion (all buffers)
  - *Not implementable: Zed doesn't support Kakoune's explicit completion query system with sub-modes*
- [ ] **`<c-x> l`** - explicit line completion (current buffer)
  - *Not implementable: Zed doesn't support Kakoune's explicit completion query system with sub-modes*
- [ ] **`<c-x> L`** - explicit line completion (all buffers)
  - *Not implementable: Zed doesn't support Kakoune's explicit completion query system with sub-modes*

### Movement

- [x] **`h`** - select the character on the left of the end of each selection
- [x] **`j`** - select the character below the end of each selection
- [x] **`k`** - select the character above the end of each selection
- [x] **`l`** - select the character on the right of the end of each selection
- [x] **`w`** - select the word and following whitespaces on the right of the end of each selection
- [x] **`b`** - select preceding whitespaces and the word on the left of the end of each selection
- [x] **`e`** - select preceding whitespaces and the word on the right of the end of each selection
- [x] **`<a-[wbe]>`** - same as [wbe] but select WORD instead of word
- [x] **`f`** - select to the next occurrence of given character
- [x] **`t`** - select until the next occurrence of given character
- [x] **`<a-[ft]>`** - same as [ft] but in the other direction
- [x] **`<a-.>`** - repeat last object or f/t selection command
- [x] **`m`** - select to the next sequence enclosed by matching characters
- [x] **`M`** - extend the current selection to the next sequence enclosed by matching character
- [ ] **`<a-m>`** - select to the previous sequence enclosed by matching characters
- [ ] **`<a-M>`** - extend the current selection to the previous sequence enclosed by matching characters
- [x] **`x`** - expand selections to contain full lines (including end-of-lines)
- [x] **`<a-x>`** - trim selections to only contain full lines (not including last end-of-line)
- [x] **`%, <percent>`** - select whole buffer
- [x] **`<a-h>`** - select to line begin
- [x] **`<a-l>`** - select to line end
- [x] **`<pageup>, <c-b>`** - scroll one page up
- [x] **`<pagedown>, <c-f>`** - scroll one page down
- [x] **`<c-u>`** - scroll half a page up
- [x] **`<c-d>`** - scroll half a page down
- [x] **`;, <semicolon>`** - reduce selections to their cursor
- [x] **`<a-;>, <a-semicolon>`** - flip the direction of each selection
- [ ] **`<a-:>`** - ensure selections are in forward direction (cursor after anchor)

### Changes

- [x] **`i`** - enter insert mode before selections
- [x] **`a`** - enter insert mode after selections
- [x] **`d`** - yank and delete selections
- [x] **`c`** - yank and delete selections and enter insert mode
- [ ] **`.`** - repeat last insert mode change
- [x] **`<a-d>`** - delete selections (not yanking)
- [x] **`<a-c>`** - delete selections and enter insert mode (not yanking)
- [x] **`I`** - enter insert mode at the beginning of the lines containing the start of each selection
- [x] **`A`** - enter insert mode at the end of the lines containing the end of each selection
- [x] **`o`** - enter insert mode in a new line below the end of each selection
- [x] **`O`** - enter insert mode in a new line above the beginning of each selection
- [ ] **`<a-o>`** - add an empty line below cursor
- [ ] **`<a-O>`** - add an empty line above cursor
- [x] **`y`** - yank selections
- [x] **`p`** - paste after the end of each selection
- [x] **`P`** - paste before the beginning of each selection
- [ ] **`<a-p>`** - paste all after the end of each selection, and select each pasted string
- [ ] **`<a-P>`** - paste all before the start of each selection, and select each pasted string
- [x] **`R`** - replace selections with yanked text
- [ ] **`<a-R>`** - replace selections with every yanked text
- [x] **`r`** - replace each character with the next entered one
- [x] **`<a-j>`** - join selected lines
- [x] **`<a-J>`** - join selected lines and select spaces inserted in place of line breaks
- [ ] **`<a-_>`** - merge contiguous selections together (works across lines as well)
- [ ] **`<+>, <plus>`** - duplicate each selection (generating overlapping selections)
- [ ] **`<a-+>, <a-plus>`** - merge overlapping selections
- [x] **`>, <gt>`** - indent selected lines
- [ ] **`<a->>, <a-gt>`** - indent selected lines, including empty lines
- [x] **`<, <lt>`** - unindent selected lines
- [ ] **`<a-<>, <a-lt>`** - unindent selected lines, do not remove incomplete indent
- [x] **`u`** - undo last change
- [x] **`U`** - redo last change
- [ ] **`<c-j>`** - move forward in changes history
- [ ] **`<c-k>`** - move backward in changes history
- [ ] **`<a-u>`** - undo last selection change
- [ ] **`<a-U>`** - redo last selection change
- [ ] **`&`** - align selections
  - *Not implementable: Zed doesn't have alignment commands*
- [ ] **`<a-&>`** - copy indent
  - *Not implementable: Zed doesn't have alignment commands*
- [x] **```** - to lower case
- [x] **`~`** - to upper case
- [x] **`<a-`>`** - swap case
- [ ] **`@`** - convert tabs to spaces in each selection
  - *Not implementable: Not exposed as keybindable command in Zed*
- [ ] **`<a-@>`** - convert spaces to tabs in each selection
  - *Not implementable: Not exposed as keybindable command in Zed*
- [ ] **`_`** - unselect whitespace surrounding each selection
- [ ] **`<a-)>`** - rotate selections content
- [ ] **`<a-(>`** - rotate selections content backward

### Changes through external programs

- [ ] **`|`** - pipe each selection through the given external filter program and replace the selection with its output
  - *Not implementable: Zed doesn't support shell command piping through selections*
- [ ] **`<a-|>`** - pipe each selection through the given external filter program and ignore its output
  - *Not implementable: Zed doesn't support shell command piping through selections*
- [ ] **`!`** - insert and select command output before each selection
  - *Not implementable: Zed doesn't support shell command piping through selections*
- [ ] **`<a-!>`** - append and select command output after each selection
  - *Not implementable: Zed doesn't support shell command piping through selections*

### Searching

- [x] **`/`** - select next match after each selection
- [x] **`<a-/>`** - select previous match before each selection
- [ ] **`?`** - extend to next match after each selection
- [ ] **`<a-?>`** - extend to previous match before each selection
- [x] **`n`** - select next match after the main selection
- [x] **`N`** - add a new selection with next match after the main selection
- [ ] **`<a-n>`** - select previous match before the main selection
- [ ] **`<a-N>`** - add a new selection with previous match before the main selection
- [x] **`*`** - set the search pattern to the main selection (automatically detects word boundaries)
- [x] **`<a-*>`** - set the search pattern to the main selection (verbatim, no smart detection)

### Goto commands

- [x] **`g h`** - go to line begin
- [x] **`g l`** - go to line end
- [x] **`g i`** - go to non blank line start
- [x] **`g g, g k`** - go to the first line
- [x] **`g j`** - go to the last line
- [x] **`g e`** - go to last char of last line
- [x] **`g t`** - go to the first displayed line
- [x] **`g c`** - go to the middle displayed line
- [x] **`g b`** - go to the last displayed line
- [ ] **`g a`** - go to the previous (alternate) buffer
- [x] **`g f`** - open the file whose name is selected
- [x] **`g .`** - go to last buffer modification position

### View commands

- [x] **`v v, v c`** - center the main selection in the window (vertically)
- [ ] **`v m`** - center the main selection in the window (horizontally)
- [x] **`v t`** - scroll to put the main selection on the top line of the window
- [x] **`v b`** - scroll to put the main selection on the bottom line of the window
- [ ] **`v <`** - scroll to put the main cursor on the leftmost column of the window
- [ ] **`v >`** - scroll to put the main cursor on the rightmost column of the window
- [x] **`v h`** - scroll the window count columns left
- [x] **`v j`** - scroll the window count line downward
- [x] **`v k`** - scroll the window count line upward
- [x] **`v l`** - scroll the window count columns right
- [ ] **`V`** - lock view mode (until <esc> is pressed)
  - *Not implementable: Zed doesn't have a lock view mode*

### Marks

- [x] **`Z`** - save selections to the register
- [x] **`z`** - restore selections from the register
- [ ] **`<a-z>, <a-Z>`** - combine selections from register with current ones
  - *Not implementable: Zed doesn't support complex selection set operations (union, intersection, etc.)*

### Macros

- [x] **`Q`** - start or end macro recording
- [x] **`q`** - play a recorded macro

### Jump list

- [x] **`<c-i>`** - jump forward
- [x] **`<c-o>`** - jump backward
- [ ] **`<c-s>`** - create a jump step

### Multiple selections

- [x] **`s`** - create a selection for each match of the given regex
- [ ] **`S`** - split selections with the given regex
- [x] **`<a-s>`** - split selections on line boundaries
- [x] **`<a-S>`** - select first and last characters of each selection
- [x] **`C`** - duplicate selections on the lines that follow them
- [x] **`<a-C>`** - duplicate selections on the lines that precede them
- [x] **`,`** - clear selections to only keep the main one
- [ ] **`<a-,>`** - clear the main selection
- [ ] **`<a-k>`** - keep selections that match the given regex
- [ ] **`<a-K>`** - clear selections that match the given regex
- [ ] **`$`** - pipe each selection to the given shell command and keep the ones for which the shell returned 0
  - *Not implementable: Zed doesn't support shell piping with exit code filtering*
- [ ] **`)`** - rotate main selection (the main selection becomes the next one)
- [ ] **`(`** - rotate main selection backward (the main selection becomes the previous one)

### Object Selection - Whole object

- [x] **`<a-a>`** - select the whole object
- [ ] **`[`** - select to the whole object start
- [ ] **`]`** - select to the whole object end
- [ ] **`{`** - extend selections to the whole object start
- [ ] **`}`** - extend selections to the whole object end

### Object Selection - Inner object

- [x] **`<a-i>`** - select the inner object
- [ ] **`<a-[>`** - select to the inner object start
- [ ] **`<a-]>`** - select to the inner object end
- [ ] **`<a-{>`** - extend selections to the inner object start
- [ ] **`<a-}>`** - extend selections to the inner object end

### Objects types
**Object types** work through Zed's existing vim text object system (already defined in vim.json)

- [ ] **`b, (, )`** - parenthesis block
- [ ] **`B, {, }`** - braces block
- [ ] **`r, [, ]`** - brackets block
- [ ] **`a, <, >`** - angle brackets block
- [ ] **`Q, "`** - double quoted string
- [ ] **`q, '`** - single quoted string
- [ ] **`g, ``** - grave quoted string
- [ ] **`w`** - word
- [ ] **`<a-w>`** - WORD
- [ ] **`s`** - sentence
- [ ] **`p`** - paragraph
- [ ] **`␣`** - whitespaces
- [ ] **`i`** - indentation block
- [ ] **`n`** - number
- [ ] **`u`** - argument
- [ ] **`c`** - user defined object

### Prompt commands
**Prompt commands** use Zed's built-in command palette key bindings

- [ ] **`<ret>`** - validate prompt
- [ ] **`<esc>`** - abandon without validating prompt
- [ ] **`<left>, <c-b>`** - move cursor to previous character
- [ ] **`<right>, <c-f>`** - move cursor to next character
- [ ] **`<home>, <c-a>`** - move cursor to first character
- [ ] **`<end>, <c-e>`** - move cursor past the last character
- [ ] **`<backspace>, <c-h>`** - erase character before cursor
- [ ] **`<del>, <c-d>`** - erase character under cursor
- [ ] **`<a-f>`** - advance to next word begin
- [ ] **`<a-F>`** - advance to next WORD begin
- [ ] **`<a-b>`** - go back to previous word begin
- [ ] **`<a-B>`** - go back to previous WORD begin
- [ ] **`<a-e>`** - advance to next word end
- [ ] **`<a-E>`** - advance to next WORD end
- [ ] **`<c-w>`** - erase to previous word begin
- [ ] **`<c-W>`** - erase to previous WORD begin
- [ ] **`<a-d>`** - erase to next word begin
- [ ] **`<a-D>`** - erase to next WORD begin
- [ ] **`<c-k>`** - erase to end of line
- [ ] **`<c-u>`** - erase to begin of line
  - *Not implementable: Zed's undo system doesn't support explicit undo groups via keybinding*
- [ ] **`<c-y>`** - insert clipboard content before cursor
- [ ] **`<up>, <c-p>`** - select previous entry in history
- [ ] **`<down>, <c-n>`** - select next entry in history
- [ ] **`<tab>`** - select next completion candidate
- [ ] **`<s-tab>`** - select previous completion candidate
- [ ] **`<c-r>`** - insert the content of the register given by next key
- [ ] **`<c-v>`** - insert next keystroke without interpreting it
- [ ] **`<c-x> f`** - explicit file completion
  - *Not implementable: Zed doesn't support Kakoune's explicit completion query system with sub-modes*
- [ ] **`<c-x> w`** - explicit word completion
  - *Not implementable: Zed doesn't support Kakoune's explicit completion query system with sub-modes*
- [ ] **`<c-o>`** - toggle automatic completion
  - *Not implementable: Zed has different completion toggle mechanism*
- [ ] **`<a-!>`** - expand the typed expansions in currently entered text
  - *Not implementable: Zed doesn't support shell command piping through selections*
- [ ] **`<a-;>, <a-semicolon>`** - escape to normal mode for a single command

### User commands
**User mode** (`<space>`) is repurposed for Helix-style leader key commands in Zed

- [ ] **`<space>`** - enter default user mode to access custom commands
  - *Not implementable: Space is used for core helix commands in Zed; custom user modes are not supported*

### Cancelling operations

- [ ] **`<c-c>`** - stop any external processes
- [ ] **`<c-g>`** - cancel a long-running Kakoune operation

---
