---
title: "Radeon HD-3650 Installation"
date: 2009-01-01
forum: Multimedia Software
---

### Post by hzs11112 on 2009-01-01
Hi i am new to ubuntu so pls dnt get mad at me

I have installed ubuntu 8.10 on my desktop through my integrated video card. But now when i insert my Radeon HD-3650 1GB graphics card and plug in my monitor and boot into ubuntu then nothing shows up and there is only a blank screen.

But when i take out my HD-3650 and plug the monitor in the integrated video card then my ubuntu works perfectly.

any help in this issue will be appreciated. I searched a lot but could not understand a thing eventhough i came upon many threads of the same issue.

If anyone can help me then pls tell me everything in detail.

Thank you

---

### Post by zika on 2009-01-01
did You try disabling integrated video? (sorry for asking obvious but I've seen it happen even though in majority of cases it does not matter)

also, You might try to boot in a recovery mode with xfix option.

---

### Post by hzs11112 on 2009-01-01
no luck zika. i did both the options u said. still stuck. Thanks though

---

### Post by markbuntu on 2009-01-01
I have that same card and it works great for me. What you need to do is when the computer first boots enter the bios. Usually you do this by hitting the F1 or F10 key. I need to hit the delete key on my system. There will be directions for how to do that when you boot but they will go by pretty quickly so be prepared.

Once you get in there find the section for the integrated video and disable it. Save the changes and exit, the boot should continue to the grub screen where you need to select the recovery mode option. When you get to the menu select fix x and let it do its thing and then select continue. 

But you probably did all that already. 

Does the bios screen show up when you boot?
If not check is that the card is all the way in the socket and the monitor is properly plugged in. If you have more than one slot that can use that card try the other one.

---

### Post by hzs11112 on 2009-01-01
> **markbuntu said:**
> I have that same card and it works great for me. What you need to do is when the computer first boots enter the bios. Usually you do this by hitting the F1 or F10 key. I need to hit the delete key on my system. There will be directions for how to do that when you boot but they will go by pretty quickly so be prepared.

Once you get in there find the section for the integrated video and disable it. Save the changes and exit, the boot should continue to the grub screen where you need to select the recovery mode option. When you get to the menu select fix x and let it do its thing and then select continue. 

But you probably did all that already. 

Does the bios screen show up when you boot?
If not check is that the card is all the way in the socket and the monitor is properly plugged in. If you have more than one slot that can use that card try the other one.

thnx for the info but i tried all that. I disabled the integrated video from the bios and selected the option which says that "use the add in video controller". Also after that i went to the recovery mode and selected the xfix option and then booted normally but same thing. I see nothing instead of a blank white screen.

Any other ideas any1?

---

### Post by zika on 2009-01-02
shot in the dark: did You try getting in terminal mode on boot and ```
 sudo dpkg -reconfigure -phigh xserver-xorg
``` ...?
(backup Your /etc/X11/xorg.conf !)

---

### Post by hzs11112 on 2009-01-02
> **zika said:**
> shot in the dark: did You try getting in terminal mode on boot and ```
 sudo dpkg -reconfigure -phigh xserver-xorg
``` ...?
(backup Your /etc/X11/xorg.conf !)

when i boot with the hd 3650 inserted nothing shows up after i select ubuntu from the OS selection list. But when i do the same thing with the hd 3650 removed and monitor plugged in the integrated then ubuntu works fine and i can go to the terminal.

BTW what do you mean by getting to terminal mode on boot ??

also is there any other way ???

sry for all the trouble

---

### Post by markbuntu on 2009-01-02
In the os selection list there is a listing for recovery mode right below the one you usually boot into. That will get you to a recovery menu and terminal mode.

---

### Post by hzs11112 on 2009-01-02
> **markbuntu said:**
> In the os selection list there is a listing for recovery mode right below the one you usually boot into. That will get you to a recovery menu and terminal mode.

these are the options i get in the recovery mode
1) RESUME - resume normal boot
2) CLEAN - try to make free space
3) fsck - file system check
4) dpkg - repair broken packages
5) root - drop to root shell prompt
6) xfix - try to fix xserver

which one should i select and what should i do next?

---

### Post by markbuntu on 2009-01-02
try
xfix

and when that menu returns choose resume.

---

### Post by hzs11112 on 2009-01-02
> **markbuntu said:**
> try
xfix

and when that menu returns choose resume.

i did that but still the same thing. blank white screen.
eventhough there is a blank screen i still log in and then i am able to hear the startup audio which means that the problem is with the video card.

i have no idea what is going on.

---

### Post by gasto on 2009-01-02
Seems that video cards are not nicely supported by video card vendors, that is a shame. I have issues with the Nvidia supplied Geforce driver.

---

### Post by hzs11112 on 2009-01-03
thanks a lot for all your help ... i followed the intructions from this page
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

and then the graphics card worked fine.

---

