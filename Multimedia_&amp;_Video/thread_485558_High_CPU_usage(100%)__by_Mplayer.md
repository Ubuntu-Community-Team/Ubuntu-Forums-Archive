---
title: "High CPU usage(100%)  by Mplayer"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by sunshine12 on 2007-06-27
Hi to all, 

I have a problem with Mplayer. It uses 100% CPU while playing realvideo files (.rmvb, .rm). And after sometime it freezes the pc.

I am not using any other program or application while playing mplayer.

where is the problem and how to solve it??

using 
alsa in the audio preference &
xv  xv/x11 in video preference.

thank you.

---

### Post by derby007 on 2007-06-27
Try Kaffeine ([http://qdvdauthor.sourceforge.net/]("http://qdvdauthor.sourceforge.net/")) instead. Also have u the various plugins installed...

---

### Post by sunshine12 on 2007-06-27
thanks for suggestion. Is high cpu usage is normal with mplayer? Any tweaking that can change that? or have to change the whole player?

Thank you.

---

### Post by sunshine12 on 2007-06-27
switching to kaffeine is the only solution for this problem? please suggest.
I have tried playing realvideo files with realplayer, and that also consume 100% CPU..
will it change with kaffeine?
Try to provide solution with mplayer if possible..

thanks.

---

### Post by sunshine12 on 2007-06-28
Waiting for reply..
thanks in advance

---

### Post by ericsond on 2008-05-08
Suggest editing xorg.conf file to set 'Defaultdepth 16' and 'Depth 16', may be in several places.  For me running 24 bits took too much CPU time on Linux Mint 4.0 with ATI Rage 128 card.

---

