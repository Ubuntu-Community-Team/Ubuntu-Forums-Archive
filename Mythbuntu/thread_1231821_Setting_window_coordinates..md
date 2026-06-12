---
title: "Setting window coordinates."
date: 2009-08-04
forum: Mythbuntu
---

### Post by jmail524 on 2009-08-04
I am running Mythbuntu 9.04 on my Sony TV.  I have the video output set to 1920x1080 but I have a bit of overscan so I adjusted the MythTV GUI to 1806x1048 with an offset of 57 (X) and 16 (Y).  This centers everything built into MythTV very nicely on my screen.  The problem is when I run external programs from MythTV (ie., zSNES, TOTEM, Firefox).  I have managed to find ways to set their X&Y windows sizes, but I cannot seem to make them open up a couple of pixels to the right and down of the absolute top-left of the screen.

Is it possible to tell XFCE/Mythbuntu to open certain windows/programs at predetermined coordinates?

Thanks.
Brian

---

### Post by stevanbt on 2009-08-05
Hi Brian,
I had the same problem.  Have you tried to use modelines in the /etc/X11/xorg.conf?  Our samsung tv has a 'just scan' option in the picture size options - that gets rid of the overscanning too.

Hope this helps, Steve.

---

### Post by jmail524 on 2009-08-05
Hi Steve,

Thanks for the reply.  I have tried creating my own modelines using a utility that has been recommended by other users on this board. (Can't remember the name of the utility.)  However, when I use a custom modeline either the TV doesn't display anything or Mythbuntu generates and error message and defaults to 640x480 after a reboot.

I was just hoping that there was a commad line option or a config file that I could use to set the absolute positioning of certain windows.

Thanks.
Brian

---

### Post by stevanbt on 2009-08-06
Hi Brian,
I've seen the tool mentioned in the forums too, but I followed this guide (I have to say with limited success, but others have had more success).  The editing is manual, but it may be worth a try:-

[http://ubuntuforums.org/showthread.php?t=1003099&page=2]("http://ubuntuforums.org/showthread.php?t=1003099&page=2")

Have you check to see if your TV has a 'just scan' or similiar?

Thanks, Steve.

---

### Post by jmail524 on 2009-08-06
Hi Steve.

I tried the instructions on the post you linked to.  The default EDID settings do work, but as soon as I try to modify any of the settings the display shows a double image.  However, now the TV does not have to be on before booting up the HTPC to get a picture.  (It used to be if I had the TV off when X initialized, X would not activate the DVI port.) 

Thanks.
Brian

---

### Post by jb5 on 2009-08-11
Have you tried the Workspaces option under XFCE 4 settings?

In this window it is possible to define a set of margins. 

HTH

---

### Post by jmail524 on 2009-08-15
Hi jb5,

I did like you said and setup margins under the Workspaces & Margins icon.  Unfortunately, it didn't seem to do anything for me.  I even tried some ridiculous numbers (left & right margins at 500px each) and nothing seemed to change. I also tried logging out/in and then rebooting, but it made no difference.  I do appreciate the suggestion.

I'm going to do a little research to see how exactly to use the Margin's settings (Maybe I'm missing a step.)

Thanks.
Brian

---

### Post by jb5 on 2009-08-16
On my system (I'm outputting to a CRT) I'm using margins of 200, so it does take a pretty large adjustment to see anything useful.

I will try and check what my over/under scan settings are, when I'm at my MythBox, to see if that sheds any light on the situation.

EDIT - I'm running an nvidia card, and I've got the overscan slider set to 11. 
That probably doesn't help much but these are the settings I'm using.

---

### Post by jmail524 on 2009-08-25
Hi again jb5,

Thanks for the "margins" suggestion.  I got the margins functioning and I think that this will be a viable solution (until I get a new TV with 1:1 scaling). My margins were not working on my system which I upgraded from 8.10 to 9.04.  Now that I have reinstalled 9.04 from scratch, the margin settings are working.

Thanks.
Brian

---

### Post by nickrout on 2009-08-25
Most linux programs that run a gui respect the -geometry switch.

program -geometry 1000x1000+0+0

---

