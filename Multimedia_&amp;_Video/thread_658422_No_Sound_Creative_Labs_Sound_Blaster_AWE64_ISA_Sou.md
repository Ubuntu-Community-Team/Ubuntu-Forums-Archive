---
title: "No Sound Creative Labs Sound Blaster AWE64 ISA Sound Card (CT4520)"
date: 2008-01-04
forum: Multimedia &amp; Video
---

### Post by knw on 2008-01-04
I'm not that experianced with llinux in general...I'v installed Ubuntu on couple machines in the past...now on this p3 750mhz machine I can't get sound to work...it's a Creative Labs Sound Blaster AWE64 ISA Sound Card (CT4520) I'v done all the updates of the OS and Gstreamer plugin is installed and pretty much everything that had Gstreamer in the name.

Now when I ran ```
lspci
```

I get ```
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 23)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11)
00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
```

When I try to run ```
alsamixer
```

I get ```
alsamixer: function snd_ctl_open failed for default: No such device
```

So I'm pretty sure my card is not being detected now I'v read a lot about this and now I'm stuck at the point where I have to use ```
modprobe
```

BTW I'm pretty sure the card is working cuase it was working fine under WinME before installing Ubuntu.

I'm not sure how to modprobe the card...Could be also IRQ setting in the bios...if so what should I channel should I set for the sound card. 

There is few post for the Sound Blaster 16 and Sound Blaster 16 awe...but none for the 64AWE ones...I just don't know what to use when trying ```
sudo modprobe ??
```

Please help!

Thanks in Adavnce.

---

### Post by jrusso2 on 2008-01-04
I had the same problem and those cards used to be the ones that worked great in Linux.  It seems a lot of ISA sound support was removed from ALSA.

You can try this see if it help

[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)

---

### Post by knw on 2008-01-04
yes I was already on the site that you poster pre creating this post...there is nothing noted on the card that have...=[

---

### Post by knw on 2008-01-04
It would help if someone can post a step to step how to for this card if they ever had to configure one...Thanks

---

### Post by knw on 2008-01-07
Help! =\

---

### Post by AlexEagar on 2008-02-16
[Solution Source]("http://ubuntuforums.org/archive/index.php/t-115697.html")
[Explanation]("http://www.osnews.com/permalink?f298700")

Add the following line to /etc/modules and then reboot.

snd-sbawe

---

