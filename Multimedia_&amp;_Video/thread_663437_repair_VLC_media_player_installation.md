---
title: "repair VLC media player installation"
date: 2008-01-10
forum: Multimedia &amp; Video
---

### Post by singachris on 2008-01-10
After having tried the various media players in the repository, my VLC player is now no more working properly. When playing Quicktime movies, the picture is completely blurr and when playing DVDs the picture shakes. Only MPlayer is now working but the quality is poor. 

There seem to be some interdependencies I don't grasp. Can anyone help me to get a clean install of VLC? 

thanks in advance
Singachris

---

### Post by singachris on 2008-01-11
I found a posting which solved my problem:
++++

  #3  
Old November 1st, 2006
kecsap kecsap is offline
5 Cups of Ubuntu
	  	
Join Date: Sep 2006
Beans: 19
Thanks: 0
Thanked 0 Times in 0 Posts
Re: Using totem with beryl
The configuration of the VLC is very easy under beryl:

1. Go to Settings/Preferences/Video/Output modules/XVideo
2. Check the Advanced options below.
3. X11 display name change to 0, XVideo adaptor number to 0.

gstreamer works only with Video output "X Window System (No Xv)". To setup it launch the gstreamer-properties.

gxine works for me without any configuration...
++++

Great thanks to kecsap. The online help, the common questions, no postings with the right formula for me...  This allows me now to play Quicktime, DVD with menus, etc. in good quality! 

Matter is closed. :guitar:

---

