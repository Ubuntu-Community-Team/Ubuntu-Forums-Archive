---
title: "Where to post Myth 0.22 feedback?"
date: 2009-11-13
forum: Mythbuntu
---

### Post by 365nice on 2009-11-13
Where do I post Myth TV feedback (and is it worth it?).

I have been running myth for a few years (since 0.18 - and having upgraded recently to 0.22 - I am pleased with some of the features but quite a few things have gone backwards in the UI (in my opinion - and certainly watching my wife's reaction - she thinks so to).

It always seemed to me that the original myth goals were to make it easy to use on a TV screen with a remote control. They seemed to emphasize how to make it quick to make changes to recordings, delete things and handle wrong remote control presses.

I now find that in 0.22 - some of this ethos has disappeared - eg.

In the Media Library Recordings - a right arrow click on a recoding would open a menu to let you delete/info something. Now it just jumps back to the first list of recordings (you have to press a separate menu key now, which is just not as fast). Furthermore - if you want to delete something - when you press menu - delete isn't even on the visible list (with the mythbuntu theme) you have to press up arrow and wrap around to the bottom of the list where delete appears. This is not very user friendly (I suppose I will have to map a separate remote key for delete - but grrrr).

Similarly - the new approach to dropdown lists has changed. If you want to record something and pick a recording repeat pattern, you used to be able to click (ok) on the list and it would open a submenu showing all the available recording schedule options) - now you can't do this and have to right arrow through them (and of course my favourite - record on any channel, or record at any time on this channel - are at the the end of the list). Again  - it seems like the principle of helpful shortcuts for a tv screen and remote control have disappeared.

I am wondering if there is someone new at the project helm - as they seem to have changed the vision somehow. Don't get me wrong - I do like the many new features - but I miss the smooth operation of the old way.

Tim

---

### Post by superm1 on 2009-11-13
Hi Tim:

The bug you speak of with delete recordings being off screen has been fixed in newer myththemes snapshots.  You can upgrade to a newer -fixes snapshot from mythbuntu.org/auto-builds or by grabbing the updated mythbuntu theme deb from [https://launchpad.net/~mythbuntu/+archive/trunk-0.22](https://launchpad.net/~mythbuntu/+archive/trunk-0.22)

---

### Post by 365nice on 2009-11-14
Thanks for the reply - I'm not sure I quite understand how I get the deb you mention? Do I have to add something to my list of apt-get repositories - or can I wget something (sorry - I'm still learning some of the way things work).

Tim

---

### Post by superm1 on 2009-11-14
Tim:

From your mythbuntu install, open up firefox, click that link and it will install it for you.  No command line necessary.

---

### Post by 365nice on 2009-11-14
OK - actually when I tried it in firefox on my myth box it just opened a normal page, however this time I noticed there are instructions near the top of the page about how to add it to your repositories.

When I did this it offers to upgrade quite a few things - so I think I'll make a backup using clonezilla first (so I can roll back if screw up).

Presumably I can just untick everything but the themes I want - and that will fix one of my issues.

I do notice there are other fixes - is it safe to apply those? I saw something about VDPAU which I am also interested in - can I add those as well (after the backup though).

thanks again for the tip,

Tim

---

### Post by alexyz on 2009-11-14
> **365nice said:**
> When I did this it offers to upgrade quite a few things

You don't necessarily need to upgrade everything.  It should work to only install the .deb for the theme you're using.  I just did this and it seems to work - and the delete button is now visible.  (I assume you're using the same theme.  The package name is mythtv-theme-mythbuntu)

Also be sure you get the .deb that matches your ubuntu distribution - the download area is a little confusing.

---

### Post by alexyz on 2009-11-14
On the original point, I couldn't agree more.  See comments by me and others in this thread:  [http://ubuntuforums.org/showthread.php?t=1318267](http://ubuntuforums.org/showthread.php?t=1318267)

The official place to comment would be the mythtv-users list.  You might want to read this thread:  [http://www.gossamer-threads.com/lists/mythtv/users/405546](http://www.gossamer-threads.com/lists/mythtv/users/405546) .  Now that was a flame, but I think the response also indicates that some people simply don't understand the problem here.  Maybe it depends on what kind of remote you have, or some other factor.  But if you ask me, some of the changes are just brain-dead, same feeling I have when I sit down at a mac and grab the mouse and say, aaaaahhh#@%*$&~! :P

---

### Post by 365nice on 2009-11-15
Ah, I see what you mean about the comments - maybe I will just downgrade back to 0.21 (I liked that version - and maybe I can figure out the instructions for backporting VDPAU to it as well).

Thanks for the help.

Tim

---

