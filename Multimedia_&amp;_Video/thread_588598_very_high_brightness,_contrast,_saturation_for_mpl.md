---
title: "very high brightness, contrast, saturation for mplayer,vlc etc"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by anilv on 2007-10-23
Hi

I am in a deep problem. All movies played using mplayer, smplayer, vlc etc have high brightness contrast and saturation which makes the movie unwatchable.

I found that the issue is with the XV video output ... I tried to change to X11, gl and gl2. Brightness issue was resolved but the rendering speed is  slow which cause flickering ... So I switched backed to xv itself. Then I found a tool called "xvattr" that can be used to alter 'xv' settings ... This tool is good evenif I need to change settings (not so perfect. but better than nothing) every time I play movie ... 

Do any of you have this problem? If yes please let me know how you corrected this permanently. What are default values for "xv" that is set using 'xvcreator' (I think these values on my laptop is not correct)

My display is,
> 00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

Please help me .... 

Thank you.
Anil

---

### Post by anilv on 2007-10-23
a small break through  .... I changed the X11 driver from intel to i810 ... That corrected the saturation problem ... Anyways ... Please give some opinions to tweak X11 for intel based cards

---

### Post by anilv on 2007-10-23
Please someone answer .... 

Thanks

---

### Post by rankie on 2007-10-25
I have exactly same problem. Can anyone help?

---

### Post by anilv on 2007-10-25
Hi ... 

Please some one ... provide some thoughts on this ... Please spend a little time for this ....

Thank you ...

Anil

---

### Post by xeth_delta on 2007-10-30
Your problem might be related to the one discussed in this thread [http://ubuntuforums.org/showthread.php?t=209986&highlight=mplayer+brightness+totem+915&page=2]("http://ubuntuforums.org/showthread.php?t=209986&highlight=mplayer+brightness+totem+915&page=2").

A method to reset the contrast levels to normal values is described in there.

Xeth

---

