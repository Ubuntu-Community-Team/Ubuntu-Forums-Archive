---
title: "Firefox and mime types that aren't listed"
date: 2008-11-17
forum: Multimedia Software
---

### Post by Hooya on 2008-11-17
In Edit>Preferences>Applications for Firefox there is not an entry for mp3.  Whenever I click on an mp3 file in a webpage it automatically opens in mplayer, with no GUI.  I then can't seek or stop the file, I only have the option to kill the mplayer process.  So I have no control at all over mp3 files unless I "Save As" and go that route.  Since there's no entry in the Applications window I can't edit what it opens with.  Is there some under the hood way of adjusting mime types that aren't shown in the Applications window?

Thanks in advance.

---

### Post by __Ryan__ on 2008-11-19
If your application isn't listed, select the dropdown box and select "Use Other" then find the executable you want the file to be run under.

---

### Post by Hooya on 2009-01-17
I'm still having problems with this.  The above post isn't relevent to my issues.  I have two problems that happen:

1. Occasionally a forum I vew gets bogged down and the /forum.php file doesn't get loaded properly.  It used to ask me what I wanted to do with the file when this happened.  One time though I told it to "Open with Firefox" from the dropdown window.  Now this results in an endless creation of new tabs with 100% CPU use and I need to kill the firefox process to get control of my computer back.  I cannot find how to remove the "open with firefox" option from .php files anywhere so it goes back to the previous behavior so I at least don't have to kill my browser to regain control.

2.  .avi files only ask me where to save the file.  There is no option to open with an application.  This file type also does not show up under the mime filetypes preferences box.  There's no dropdown menu to select to open a program, my only options are "save file" or "cancel".  I always want it to open in gmplayer.

I managed to fix .mp3 files by changing the default action for .mpeg media files.  Apparently they're all lumped together in one setting.  I now have them open in gmplayer like I want.

Recap:  I need to change the default settings for .avi and .php files, or remove Firefox's familiarity with those files so it goes to normal behavior.

Would deleting my /.firefox directory and starting fresh fix this?  I'm willing to reload plugins/saved forms and I use Foxmarks, so I won't lose my bookmarks.

---

