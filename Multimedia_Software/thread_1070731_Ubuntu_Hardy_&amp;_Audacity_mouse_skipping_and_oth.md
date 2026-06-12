---
title: "Ubuntu Hardy &amp; Audacity mouse skipping and other weird behaviour"
date: 2009-02-15
forum: Multimedia Software
---

### Post by Metoshade on 2009-02-15
I installed Ubuntu on a friends computer and occasionally help her out by providing support using remote desktop. I discovered a rather bizar problem when using Audacity.

The problem is as follows: The mouse pointer works properly in the Audacity UI except when hovering above a project/song (the field with the blue oscilloscope). The mousepointer disappears in about 1/4 of the field in which the song is displayed. When she clicks to drop the "bar / line" to start songplayback or edit from that point, the bar is dropped somewhere else to the right in the field. To her it seems her mouse is operating about 1/4 of the screen to the right of the position where she actually sees her mousepointer. The displacement seems to be similar in size to the part of the field over which her mousepointer is invisible.

When observing this with remote-desktop, i see her mouse-pointer behaves completely normal, everything functions as it should. On her screen, things are acting very strange.

Example: I see her mouse at 1m37s and she sees her mous at 42s, she clicks and I see her select a point at 1m37 as does she. This is rather confusing for her as her mousepointer hangs over a totally different section of the song / project. 

Details: Her computer is rather old and her graphics card is not 3d capable. We have tried 3 versions of audacity: 3.1.2, 3.1.5 and 3.1.6. which led to no change in behaviour. The problem does not exist in other programs or other parts of the Audacity UI, just in the large field in which the song / project is displayed and can be edited.

Can anyone explain this behaviour and help us find a solution?

---

### Post by Metoshade on 2009-02-15
I have searched the audacity forums and found a post reporting the same problem:

[http://audacityteam.org/forum/viewtopic.php?f=18&t=6386](http://audacityteam.org/forum/viewtopic.php?f=18&t=6386)

I am going to try this solution as well and report back here.

---

### Post by Metoshade on 2009-02-19
It turns out the problem indeed lies with xorg and its default settings. Xorg seems to be stripped of just about everything when running with 'generic' hardware.

I installed Intrepid to see if the problem would fix itself, but no luck there. I found myself unable to select or configure a monitor of graphix card manually (why is this in Intrepid and Hardy??) and had to edit the xorg.conf myself.

Just adding some mode-lines was not enough, i had to add subsections containing proper info for both the monitor and the screen section.

I know the system in question is an old one, with an old GFX-card and an old monitor, a bit of a mix and match thing, but still, I was hoping it would be easier...

Now things work as they should, but this took way too much work for a regular user. I also had to write a small how-to for the user on how to correct the problem if xorg.conf would ever be overwritten by updates. Not a very good thing if you want to be able to trust your OS...

---

