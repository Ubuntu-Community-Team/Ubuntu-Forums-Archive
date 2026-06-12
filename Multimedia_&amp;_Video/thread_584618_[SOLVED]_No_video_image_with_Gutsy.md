---
title: "[SOLVED] No video image with Gutsy"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by vmalep on 2007-10-21
Hello,

I recently installed the new version of Ubuntu (7.10). Everything looks fine, except that I have the sound, but no image when reading a video file (DVD, flv, etc.). I installed all the plugins and codecs suggested in different forums and howto, but to no avail.

If I watch a video on internet (youtube), it works fine.

Thanks for your suggestions,
Pierre

---

### Post by por100pre1 on 2007-10-22
Have you enabled visual effects? If so, check if disabling them in **Appearance** helps.

---

### Post by vmalep on 2007-10-25
Hi,

Thanks for this suggestion. I tried with the visual effect enabled and disabled. No change...

The video players (vlc, gxine,etc.) only show a blue screen...

Any other idea?
Pierre

---

### Post by por100pre1 on 2007-10-27
Check if [this]("http://ubuntuforums.org/showthread.php?p=3640659") helps, I'm not sure how effective it can be. Just in case, backup your xorg.conf before trying it:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

### Post by aberadam on 2007-10-27
I had the same problem.  From the looks of this forum it's common.   

I used add/remove to install the xine version of Totem and now I can play DVDs.

---

### Post by aberadam on 2007-10-27
*You'll need the xine DVD codec/package/whatever for it to work obviously. 

I used Automatix which installed all sorts of stuff, including this.

---

### Post by grEnAlEins on 2007-10-27
In order to get my DVD play working, I used:

[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

Just put the appropriate code into terminal and voila!  You have DVD playback in totem.  It worked like a champ for me:guitar:

---

### Post by vmalep on 2007-10-28
Hi,

Thanks for these suggestions. It made me think at the driver used for my graphic card.

And the problem has indeed nothing to do with the codecs (already installed).

This is my graphic card:
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)

This was the xorg.conf part after fresh install og Gutsy:
Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

I changed for this:
Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Boardname	"Intel 915"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
EndSection

I would not say it is better (the quality is lower and because I have a wide screen, the image is stretched horizontally, but when playing a video file, I got the image!

So I will keep trying in order to find the best setting for the video card.

Best regards,
Pierre

----------------------

Updated:
So, I put "i810" as driver in the Device section of xorg.conf and I installed the "i915resolution" package. Now, it works fine.

---

### Post by por100pre1 on 2007-10-28
> **vmalep said:**
> Hi,

Thanks for these suggestions. It made me think at the driver used for my graphic card.

And the problem has indeed nothing to do with the codecs (already installed).

This is my graphic card:
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)

This was the xorg.conf part after fresh install og Gutsy:
Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

I changed for this:
Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Boardname	"Intel 915"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
EndSection

I would not say it is better (the quality is lower and because I have a wide screen, the image is stretched horizontally, but when playing a video file, I got the image!

So I will keep trying in order to find the best setting for the video card.

Best regards,
Pierre

----------------------

Updated:
So, I put "i810" as driver in the Device section of xorg.conf and I installed the "i915resolution" package. Now, it works fine.

Glad to know you sorted it out! :)

---

