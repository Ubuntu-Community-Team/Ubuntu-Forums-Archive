---
title: "Is there an extension to &quot;Eye of Gnome&quot; to RENAME or DELETE pictures while viewing?"
date: 2011-04-23
forum: Multimedia Software
---

### Post by rocksockdoc on 2011-04-23
I often "clean up" huge directories of JPEG photos on Windows simply by stepping through each photo in a directory ... and, while viewing any particular photo ... I decide, ad hoc, to rename and/or delete (or copy or move or resize or add a caption to) that photo ... on the fly.

In Windows, there is Irfanview freeware which will easily do all the desired steps while viewing the picture. 
In Ubuntu, most photo viewers/editors won't step through the directory (e.g., The GIMP); but the Eye of Gnome is promising in that it at least steps through the photos rather quickly.

The Eye of Gnome & F-Spot default viewer & editor is just as functional with these two (most) critical needs:

[LIST]
[*]Most important, it is a FAST viewer (when scrolling through hundreds of pics, that matters a lot!)
[*]Second most important, it has an easy NEXT PICTURE (usually spacebar) key!
[/LIST]
But, the Eye of Gnome with F-Spot (and The GIMP) does a lousy job at these critical features:

[LIST]
[*]**Rename the current picture:**
[LIST]
[*]There is no command to rename the current photo:
[*]One must use two sequential menu-driven steps
[LIST]
[*]Eye of Gnome: File -> Save As (insert new name here)
[*]Eye of Gnome: Edit -> Move to Trash (delete the old picture)
[/LIST]
 
[/LIST]
 
[*]**Delete the current picture:**
[LIST]
[*]There is no single keyclick (that I know of) to delete the picture
[*]One must use the menu-driven command:
[LIST]
[*]Eye of Gnome: Edit -> Move to Trash
[/LIST]
 
[/LIST]
 
[/LIST]
  Q1: Is there an Eye of Gnome extension to add a single keypress to RENAME or DELETE the current picture?

NOTE: I already use "feh" to MOVE or COPY the current picture on the fly (but it won't rename or delete!).
Plus "feh" can only do one at a time so I have to go through each directory twice to do such a simple task! :(

```

% feh  /path/*.jpg -A "mv %f ./send-to-mom/%n"
% feh  /path/*.jpg -A "cp %f ./also-send-to-dad/%n"

```QUESTION: 
What is good software in Ubuntu 10.04 which will do rename and delete (and if, possible, the move/copy) ad hoc, while viewing a picture?

[B]What is the quickest way to ad hoc RENAME or DELETE a picture on the fly (while viewing it) in Ubuntu?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189853&stc=1&d=1303623600[/IMG]

[/B]

---

### Post by curbuntuforums on 2011-04-28
[FONT=Verdana][SIZE=2]I too am very interested in concise answers to your questions on minimal keystroke photo album management; but alas, I'm a newb.

[/SIZE][/FONT][FONT=Verdana][SIZE=2]For what it's worth, here's my 2 cents on feh solutions:
[/SIZE][/FONT] [FONT=Verdana][SIZE=2]
1)[/SIZE][/FONT]> NOTE: I already use "feh" to MOVE or COPY the current picture on the fly (but it won't rename or delete!).[FONT=Verdana]
[SIZE=2]- feh's [Ctrl+Del] [/SIZE][/FONT][FONT=Verdana][SIZE=2]will toast 'em even during a filelist slideshow
- [Ctrl+Del] is too many buttons? I agree.  A[/SIZE][/FONT][FONT=Verdana][SIZE=2]ssign a # key to do it [/SIZE][/FONT][FONT=Verdana][SIZE=2]with --action# "rm %f"
- or change [/SIZE][/FONT][FONT=Verdana][SIZE=2]key binding of [Delete] in ~/.config/feh/keys[/SIZE][/FONT] [FONT=Verdana][SIZE=2](v1.11+)[/SIZE][/FONT]

2)> Plus "feh" can  only do one at a time[FONT=Verdana][SIZE=2] 
Arrrrugh?  What version are you using? Reason  I ask is your examples' syntax is:[/SIZE][/FONT]```
feh *.jpg -A "script" 
```[FONT=Verdana][SIZE=2]and not[/SIZE][/FONT]```
feh *.jpg --action0 "rm %f" --action1 "move-to-mom" --action2 "copy-to-dad; move-to-mom"
```[FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2]which would let you delete, move, & copy-move with different buttons.   Adding a semi-colon[/SIZE][/FONT][FONT=Verdana][SIZE=2] before "script" text prevents [/SIZE][/FONT][FONT=Verdana][SIZE=2]cycling to next pic after action, so you can perform multiple actions on same picture.[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2]
3) OK, three cents. 
One Button **Rename [SIZE=3]and/or[/SIZE] Move** while viewing: [/SIZE][/FONT] [FONT=Verdana][SIZE=2]wish I knew..
--action# ;"[crafty script]" will do it. 
:P[/SIZE][/FONT] [FONT=Verdana][SIZE=2]

Just need someone with the script experience to show me how to fetch a little keyboard input and squeeze it into a function of feh's %f and %n format specifiers.  The idea is: with minimal keystrokes still be able to either move or rename [/SIZE][/FONT][FONT=Verdana][SIZE=2]depending on how you type it - with trailing / or not... I guess.. maybe... [/SIZE][/FONT][FONT=Verdana][SIZE=2]by "a function of %f and %n" I mean the mv command's destination is:

[destination] = (%f - %n) + KeyboardInput + %n

which implies I'll be moving only into a sub-dir of current dir or  renaming only with a prefix to current name - but I could live with that.

Alternatively, if one made separate --action# scripts for copy, rename, and move, then one's script wouldn't need to be so crafty and you could move it anywhere, rename it anything, call up a nautilus directory chooser etc.. but it's still beyond my craft to get keyboard input - let alone concatenate the new destination path&name.:([/SIZE][/FONT][SIZE=1][SIZE=2]
[/SIZE][/SIZE]

---

### Post by rocksockdoc on 2011-04-29
> **curbuntuforums said:**
> - feh's [Ctrl+Del] will toast 'em even during a filelist slideshow

Thanks. That works great to delete in a single keystroke set!

[QUOTE=curbuntuforums]What version are you using? [/QUOTE]
```
$ feh -v
feh version 1.3.4
```[QUOTE=curbuntuforums]delete, move, & copy-move with different buttons[/QUOTE]
I had not realized multiple actions were allowed, tied to the numeric buttons!

The '--action0" didn't seem to work syntactically when I pressed the "0" key:
```

 $ feh *.jpg --action0 "rm %f" --action1 "mv %f ./mom/." --action2 "cp %f ./dad/.; mv %f ./mom/."
feh: unrecognized option '--action0'
feh WARNING: rm %f does not exist - skipping
```But, it worked fine when I changed the syntax slightly:
```

$ feh *.jpg --action1 "rm %f" --action2 "mv %f ./mom/." --action3 "cp %f ./dad/.; mv %f ./mom/"

```
[LIST]
[*]Pressing the "1" key deleted the file (and moved to the next file in the sequence)
[*]Pressing the "2" key moved the file to ./mom/%n (and moved to the next file in the sequence)
[*]Pressing the "3" key did both the copy and the move (and moved to the next file in the sequence)
[/LIST]
I added your suggestion to the original question way back when!
- [How do YOU scroll through hundreds of photos & move good ones to a separate folder?]("http://ubuntuforums.org/showthread.php?t=1625745")

This may not be the right forum, but is there a "trash" command (i.e., recoverable) instead of a 'delete' command?
(The other option, if there isn't a "move to trash" command is to simply move the file to a temporary location and then manually trash it later.)

---

