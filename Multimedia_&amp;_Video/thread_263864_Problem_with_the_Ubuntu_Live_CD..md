---
title: "Problem with the Ubuntu Live CD."
date: 2006-09-23
forum: Multimedia &amp; Video
---

### Post by Jadix on 2006-09-23
I just received my Ubuntu installation CD in the mail.  The version is 6.06 LTS for 64 bit PCs.  

My PC has the following specs:

Windows XP Pro SP2
AMD 64 3400+ w/ 2.2 Ghz
1 GB of SDRAM PC 3200
20GB of free space
ATI Radeon x850

when I boot from the ubuntu cd in my CD-Rom drive I have issues.  The Ubuntu menu comes up normally, and I select the option to "Install or Preview" ubuntu.  From there it runs through a few processes before the screen goes black.  The screen stays black until I restart.  I have tried this in graphic safe mode and the monitor turns OFF at the same point.  I figured this was a video driver issue.

Any help?

---

### Post by maigege on 2006-09-23
i have problems too.............

Sorry to hijack this thread. I am newbie here and newbie with Linux, unbuntu. I have tried to post a new thread but could not find to do so.

I have a Pc with Windows 2000 installed on the C: (FAT32 format), there are two other FAT32 partitions D: and E:. I have tried installed Ubuntu to drive D: from the Ubuntu CD but failed miserably for many times. I have looked in internet and this forum but still can not find a way to do it. 

Could anybody give me some help, please......... I am desperately want to install the Ubuntu!!!!!!!!!! But just cannot get it to work!!!!!!!! Uhhhhhhhhhhh!!!!!!!!!!!
Help,,,,,pleeeeeeeeeeeeeeeeeeeeeeeeeeeese!!!!!!!!!

---

### Post by maigege on 2006-09-23
How do i start a new thread?? Sorry for being stupid. Is it now allowed for new user?? i could not find a way to do it. I don't want to hijack other people's thread. sorry

---

### Post by Jadix on 2006-09-23
you have to click on the button that says "New Thread" which is located below the lists of threads.

---

### Post by Jadix on 2006-09-27
bump

---

### Post by tseliot on 2006-09-27
You need to download the alternate installer (I suggest you to download the  32bit one)

1) Install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

If nothing works and the Xserver just crashes, please post the output of the following command:
```
lspci
```

---

### Post by zak- on 2006-09-27
I don't consider using vga or vesa as a solution. Who would be satisfied with such video quality? 

It seems many people with x800/x850 cards are having this blank screen issue with the default "ati" drivers, including myself. I can't even use ati's proprietary drivers (fglrx), because they on the other hand cause x800/x850 cards to overheat. 

I'm really frustrated since both of these issues have been around for such a long time with no improvement in sight.

---

