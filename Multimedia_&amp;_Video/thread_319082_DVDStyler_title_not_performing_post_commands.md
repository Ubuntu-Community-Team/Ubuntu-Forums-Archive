---
title: "DVDStyler title not performing post commands"
date: 2006-12-15
forum: Multimedia &amp; Video
---

### Post by Shay Stephens on 2006-12-15
I have dvdstyler 1.5b4 with wxsvg_1.0b5.  

 I have a fairly simple DVD setup:
1) A vmMenu that has a play button and a button to jump to a chapter menu.  
2) On the chapter menu there is a back button that takes you back to the vmMenu and 13 chapter buttons.  
3) There is a title with chapters set, and a post command to call the vmMenu when the video stops playing.

The problem is that the post command on the title is not running, the video just stops about a second or so too soon leaving a faint trace of the video frame there and it just stays that way, it does not load the vmMenu.  The other two menus also have post commands to replay themselves, and those do work just fine.  This is the title setup:

Chapters: 1:43,5:56,10:36,21:31,24:07,26:06,28:28,33:08,36:16,38:38
pause: 0
Pre commands:
Post commands: call vmgm menu 1;

vmMenu1 Setup
Format: NTSC 720x480
Pause: 0
Pre commands:
Post commands: jump vmgm menu 1;

Just to try, I put a single jpg image slideshow in there too and had the title jump to it and the from the slideshow call the vmMenu1, but that did not change a thing.  Anyone have an idea of what is going on?  Any dvdstyler users out there?

---

### Post by Shay Stephens on 2006-12-15
**Update:**
No matter what I tried, the problem was persistent.  So I basically just gave up.  I installed qdvdauthor and rebuilt the project the same way.  It works perfect.  And a bonus, the buttons don't flicker, and the text looks much nicer on qdvdauthor than it does in dvdstyler.

So I got it working with qdvdauthor and I am uninstalling dvdstyler...problem solved :-)

---

