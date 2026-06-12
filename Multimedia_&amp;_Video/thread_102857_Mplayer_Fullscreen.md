---
title: "Mplayer Fullscreen"
date: 2005-12-13
forum: Multimedia &amp; Video
---

### Post by Crusufix on 2005-12-13
I don't know how petty a question this is, but I'm running a pretty standard Breezy install. The only things I've added to the install so far are the ATI fglxr drivers, NeverWinter Nights, XMMS, Bluefish, Azureus, Wine, Zsnes and Mplayer. My problem is I can't seem to find a way to make Mplayer run in fullscreen mode. I can right click on it and get the option but all it does is make the Mplayer background larger and the video stays the same size.

I'm probably missing something small here but it's really got me stumped.

P4 2.4Ghz, 1GB RAM, ATI 9600 Pro 256MB.

---

### Post by ubuntu27 on 2005-12-13
[QUOTE=Crusufix]I don't know how petty a question this is, but I'm running a pretty standard Breezy install. The only things I've added to the install so far are the ATI fglxr drivers, NeverWinter Nights, XMMS, Bluefish, Azureus, Wine, Zsnes and Mplayer. My problem is I can't seem to find a way to make Mplayer run in fullscreen mode. I can right click on it and get the option but all it does is make the Mplayer background larger and the video stays the same size.

I'm probably missing something small here but it's really got me stumped.

P4 2.4Ghz, 1GB RAM, ATI 9600 Pro 256MB.[/QUOTE]

I also want to know about it.
I don't think it is a hardware problem.

---

### Post by fog on 2005-12-13
Try to use 'xv' as the video output.

---

### Post by Crusufix on 2005-12-13
[QUOTE=fog]Try to use 'xv' as the video output.[/QUOTE]

Thank you very much, Switching the video output to XV does allow me to change the video size.

For those that don't know how to do this. Just right click and go into PREFERENCES. Then into the VIDEO TAB, select X11/xv and click on OK. Then restart Mplayer.

Also as a note, you may need to move your preferences window to reveal an information window for which you have to click OK before you can actually do anything in the preferences window. At least that was the case with me.

---

### Post by nocturn on 2005-12-13
deleted, someone already posted the XV solution

---

### Post by penvzila on 2005-12-13
Question: when you do that, do you get a 1/2 second or so audio delay? Because that' spretty much what is keeping me from using mplayer at this point.

---

### Post by redgilda on 2005-12-18
[QUOTE=Crusufix]Thank you very much, Switching the video output to XV does allow me to change the video size.[/QUOTE]
for me it doesnt work :/ im getting the 'error initializing the selected video_out vo device' or something.... 
what am i doing wrong? :)

---

### Post by Joriz on 2006-02-06
[QUOTE=redgilda]for me it doesnt work :/ im getting the 'error initializing the selected video_out vo device' or something.... 
what am i doing wrong? :)[/QUOTE]

Same here, i want a solution for this...
I use the ati drivers and a mobilty ati 9000

---

