---
title: "puddletag: An audio tag editor for Linux (that happens to run on OS X)"
date: 2010-07-17
forum: Multimedia Software
---

### Post by egd on 2010-07-17
For those amongst us that use Linux and haven't found an audio tagger  they're happy with...

puddletag is in effect [COLOR=Red]**a drop-in Linux  based replacement for mp3tag**[/COLOR] borne out of frustration with the audio tag  editing toolset available under Linux.  Anyone familiar with mp3tag  will immediately feel at home working with puddletag. Whilst it's  loosely based on mp3tag (and incorporates most of the functionality  available in mp3tag) it also incorporates many enhancements we wanted to  see and allows efficient tag handling in ways not possible with most  editors we'd tried.

Examples include:

[LIST]
[*]a spreadsheet-like layout that enables  selection of individual tags/cells across multiple files and performing  operations on the selected tags only
[*]copying selected tag(s)  from one track to many tracks in a single operation
[*]quick search  and replace of text across selected tags/ cells or entire tracks using  Ctrl-H (no need to write an action for a quick search/ replace  operation)
[*]extended tags view that uses colour feedback to show  you what will be added, altered and edited on hitting OK
[*]ability  to see stored tags as written to file (i.e. without tagname  translation) to help resolve pesky issues like id3 and vorbis tag types  in a single file
[*]ability to tag single tracks using tag sources  (handy when the album you're looking for doesn't exist in tag sources,  but the songs do exist in other albums found in tag sources (why tag by  hand when you can just take track metadata from other albums)
[*]ability  to include/ exclude specific tags from tag sources
[*]easily  select all tracks in a folder using a hotkey (Ctrl-Shift-S)  (no more  dragging the mouse cursor around and shift-clicking)
[*]resize/relocate/close  windows (configure your workspace to suit you)
[*]realtime results  feedback when defining actions (so you can see the results an action  will generate as you define it)
[*]importing tags from clipboard in  much the same way one would from text file (why copy track data from a  website, save it to a file and only then write it... pop it into the  clipboard and write it from memory)
[*]dynamically change main  window font size to suit your needs
[*]launch puddletag with a  predefined font size
[*](optionally) dynamically size columns to  match tag metadata
[*]drag and drop tag columns in main view to  reorder them
[*]predefined, customisable and readily editable tag  patterns always available to you through a pulldown menu
[*]customisable  hotkeys
[*]ability to import and edit tags directly in the  QuodLibet library
[*]tag source -> tag name mapping so users can  customise tag names per web source.
[/LIST]

As an added bonus,  it's reported to run equally well under OS X (after dependencies are  installed).

Last, but not least, puddletag's been developed using Python and is free as in free by being licencsed under  GPLv2

Downloads and additional information at: [_**puddletag on  freshmeat**_]("http://freshmeat.net/projects/puddletag") and **[puddletag:  A tag editor for Linux]("http://puddletag.sourceforge.net/index.html")**.

---

### Post by egd on 2010-10-17
puddletag 0.96 has been released and includes a host of additional features and enhancements.

_**Highlights include:**_

[LIST]
[*]Ability to accept/ reject changes to existing tag metadata **_at a track and/or field level_** when using Tag Sources (including Masstagging).  Fields that will be changed are formatted bold and can be viewed/edited in main view, Tag Panel or Extended Tags view.  Unchanged fields are shown in italics.
[*]Ability to remove ID3 and APEv2 tags from files that shouldn't contain these tag types.
[*]Ability to toggle confirmations for Renaming Directories, Exiting Preview Mode and Deleting files.
[*]Ability to rename folders via an action specifying a value for the __dirname field.
[*]Support for UFID frames for ID3v2 Tags.
[*]Monkey's Audio File's are now fully supported.
[*]The Actions and Functions dialogs can now be tool windows too (See Windows Menu).
[*]Actions and Functions now operate and write multiple-valued fields.
[*]Two new scripting functions copied straight from Mp3tag: $meta_sep and $meta. See the [**Scripting page**]("http://puddletag.sourceforge.net/scripting.html") for details.
[/LIST]


_**Numerous new functions that can be used on a standalone basis or used in actions.  These include ability to:**_

[LIST]
[*] import text file to field
[*] embed artwork
[*] merge fields
[*] remove specified fields
[*] remove ALL BUT specified fields
[*] remove duplicate values in a field
[*] sort multivalue fields (ascending, descending and with or without case sensitivity)
[*] rename file using tag values
[/LIST]


See the [**Functions page**]("http://puddletag.sourceforge.net/functions.html") for a detailed listing and description of each.

All documentation has been updated.  If you're in need of any assistance or have suggestions, please post them on the [**puddletag forum**]("http://sourceforge.net/apps/phpbb/puddletag/").

Last, but not least, puddletag [COLOR=red]**_[can now be downloaded as a .deb file]("http://sourceforge.net/projects/puddletag/files/puddletag_0.9.6-1_all.deb")_**[/COLOR] meaning installation on Debian based Linux systems is as simple as double-clicking on the file to get it and all dependencies installed.  In Ubuntu it will appear in the Applications/Sound & Video menu.

---

