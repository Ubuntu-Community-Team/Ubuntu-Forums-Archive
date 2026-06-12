---
title: "Please help me"
date: 2009-07-27
forum: Multimedia Software
---

### Post by anis745 on 2009-07-27
is what works with vdr map pinnacle 400i.
I try several times but to no avail.:confused:
[IMG]http://www.cadsoft.de/vdr/vdr-logo-small.jpg[/IMG]

---

### Post by anis745 on 2009-07-27
[COLOR="Red"]OK it works. 
but someone help me solve this problem with xine.[/COLOR]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=122617&stc=1&d=1248710219[/IMG]

---

### Post by thewolfman on 2009-07-27
Hi,

I think if you explain yourself a bit more; people will be more than willing to help you, what you have written does not explain what your problem is.

If you are having trouble playing back video or audio; make sure you have all the appropriate codecs installed, go to this link and follow the instructions: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Also install gstreamer10 flac and faad; Windows32codecs is a must; plus all xine plugins.

When you have done that; let us know if you have any more problems.

A good multimedia player worth installing is VLC as is Mplayer.

Regards thewolfman.:D

---

### Post by anis745 on 2009-07-31
[B][FONT=Courier New][COLOR=Red]by typing this command:
> /usr/bin/xine -V xv -f -r anamorphic --post vdr_video --post vdr_audio --post upmix_mono --post vdr --verbose=2 "vdr:/tmp/vdr-xine/stream#demux:mpeg_pes"
[/COLOR][/FONT][COLOR=Red] the result and the next [/COLOR][COLOR=Red]:[/COLOR][/B]
[B][FONT=Courier New][COLOR=Red]> - Xine engine error --

There is no input plugin to handle 'vdr: / tmp / vdr-xine / stream # demux: mpeg_pes.
This may be due to bad syntax of the MRL
or stream / file does not exist.
------------------ (END OF ERROR) -------------------


---------------------- (ERROR) ----------------------
- Xine engine error --

There is no input plugin to handle 'vdr: / tmp / vdr-xine / stream # demux: mpeg_pes. [/COLOR][/FONT][/B][IMG]http://img220.imageshack.us/img220/8052/capturefentresansnomi.png[/IMG]

---

### Post by anis745 on 2009-07-31
[CENTER][FONT=Courier New][COLOR=Red]**[SIZE=5]Please help me[/SIZE]**[/COLOR][/FONT][/CENTER]

---

### Post by martinbaselier on 2009-07-31
You can ask "please help me" as many times as you want, but unless you clarify what you want to do and what the problem is, it won't be possible to help you.

---

### Post by anis745 on 2009-07-31
> **martinbaselier said:**
> You can ask "please help me" as many times as you want, but unless you clarify what you want to do and what the problem is, it won't be possible to help you.

[COLOR=Red]**I have installed VDR 1.7.8 and cccam with my satellite card pinnacle PCTSAT 400i. **
** works plugins, codec, except that IR, but when I run  **[/COLOR][COLOR=Red]** VDR **[/COLOR][COLOR=Red]**this message appears **[/COLOR].

> [B][FONT=Courier New][COLOR=Red]-[COLOR=Black] Xine engine error --

There is no input plugin to handle 'vdr: / tmp / vdr-xine / stream # demux: mpeg_pes.
This may be due to bad syntax of the MRL
or stream / file does not exist.
------------------ (END OF ERROR) -------------------


---------------------- (ERROR) ----------------------
- Xine engine error --

There is no input plugin to handle 'vdr: / tmp / vdr-xine / stream # demux: mpeg_pes.                [/COLOR]          [/COLOR][/FONT][/B]

---

### Post by anis745 on 2009-09-19
Can someone help me please

---

### Post by steefjeqv on 2009-09-22
Hi,

I suppose you've compiled VDR and the plugins from source.

Make sure VDR is running :

sudo /etc/init.d/vdr start

Then enable multi-user for your X server :

sudo xhost +

Start your Xine frontend.

Greetings,
Steven

---

