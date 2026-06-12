---
title: "Acer TravelMate 8103WLMi Blank Screen"
date: 2006-08-13
forum: Multimedia &amp; Video
---

### Post by snapper64 on 2006-08-13
Hi Guys,

I've reposted this here as it seems more appropriate than where i posted my orginal thread. Im not sure how to remove the old post . . .

Im installing on an Acer TravelMate 8103WLMi. Basically it loads the cd on boot and gives me the option screen, i press enter to start or install Ubuntu. It runs through a load of checks, all seems fine up to now. It starts to fail though, my screen seems not only to turn blank, but off. I hear few noises and then nothing much happens. I tried hooking up my external display and everything works fine on this monitor, i get the gui and everything. My question is, how do i get my laptop display to work so i can install Ubuntu on it ??

Any help is much appreciated,

Thanks,

Charlie

---

### Post by tseliot on 2006-08-13
Please follow these instructions:

1) Install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

The Xserver should work fine

---

