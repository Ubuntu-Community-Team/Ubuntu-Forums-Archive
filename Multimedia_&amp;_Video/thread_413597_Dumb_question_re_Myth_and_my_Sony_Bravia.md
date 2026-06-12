---
title: "Dumb question re Myth and my Sony Bravia"
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by drifting on 2007-04-19
May or may not be dumb? but I have a good reason for asking.

I have at last managed to get a working Myth system, both front and backend (special thanks to wiki.efficientpc.co.uk, and [www.parker1.co.uk](www.parker1.co.uk))

Anyway back to the plot, I have got a 37" Sony Bravia LCD TV, would X recongnise it? or would I have to muck around with the settings? This machine is going to live on top of a wardrobe, and I have not managed to convince "She who must be obeyed" that a wireless keyboard etc is a must have!

I did find this after a google, but not exactly sure if I remove the current settings in xorg.conf or just add these ?

Section "Monitor"
Identifier "SonyBravia"
HorizSync 47.7
VertRefresh 60
ModeLine "1360x768" 85.500 1360 1424 1536 1792 768 771 777 795 +Hsync +Vsync
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Videocard0"
        Monitor    "SonyBravia"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1366x768"
        EndSubSection
EndSection


Paul.

---

### Post by barney_1 on 2007-04-19
If you're connecting to the TV with a DVI cable the modes should be automatically detected if you use:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by drifting on 2007-04-19
I will be connecting via the normal VGA type plug, so with that in mind I will give it a try.

Thanks for the confirmation.

Paul.

---

### Post by canardo on 2007-04-19
same issue here willlet you know when ifindthe resolution

[http://ubuntuforums.org/showthread.php?t=413869](http://ubuntuforums.org/showthread.php?t=413869)

---

### Post by drifting on 2007-04-19
Argh ! That's what I was afraid of, oh well good job I did not go install it.
I await with baited breath.

Paul.

---

### Post by drifting on 2007-04-22
I have been messing around with this for at least a week, following numerous links to numerous dead ends! My problem is that I am new to Linux and Myth, and really suffer from an understanding problem. 

So here goes:- 

I have a small fujitsu siemens desktop (Nice and quiet) Installed Ubuntu fiesty (7) Installed Myth frontend (backend is already running fine on another machine) 

Connect up to monitor, all works well at 1280*1024. Now after further googling I found out that the defaut resolutions of the Intel graphics does not do the default Bravia resolution of 1280*768 60Hz. So off I went and researched the chipset, and lo and behold found a program called 915 resolution. Following instructions, replaced one of the modes with the required res, restarted X, sadly it still did not show up as an option in resolutions! 

Ok at this stage I read a link about modlines, now this really is getting beyond my very limited understanding. 

Can any kind soul please help, this is driving me nuts. 

Paul.

---

### Post by Arcadian on 2007-10-18
Hi All,

I have a Bravia 32" LCD and an old dunger of a PC running the Mythbuntu Beta. It has an ASUS AGP-V3800 in it (which is Nvidia Riva TNT2 equivalent). I too have been struggling to get anything other than 1024x768. Initially I could only get 800x600 with the Nvidia legacy drivers.

I'm not quite sure what res I have now (it says 1280x720, but I think it's lying), but at least it's now wide-screen & full screen. I'll have to tweak it to 1366x768 later (which is what my Bravia would like).

Now, I'm using the normal VGA without the EDID option so far. All I did to get the best result so far was run "sudo dpg-reconfigure xserver-org" while the video card was plugged into LCD TV (and I suspect it would be fine if I installed it that way, which I didn't).

For now I'm happy :guitar: but I'll let you know if I track down the real 1366x768 resolution! 

Cheers & good luck! :KS

P.s. I think these might be options worth trying (in bold)
[http://ubuntuforums.org/showpost.php?p=2651733&postcount=15]("http://ubuntuforums.org/showpost.php?p=2651733&postcount=15")

---

