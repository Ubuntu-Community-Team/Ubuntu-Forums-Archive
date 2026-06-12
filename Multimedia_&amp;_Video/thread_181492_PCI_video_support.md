---
title: "PCI video support"
date: 2006-05-24
forum: Multimedia &amp; Video
---

### Post by ed_d on 2006-05-24
here is an odd one.
I installed a Radeon 9100 128mb pci video card into slot 1 of my xseries 220, went through the install fine on Ubuntu, but as soon as it tries to start the gdi, all I get is a blinking cursor in the upper left corner. I tried reloding with an older nvidia 16 mb pci card, same thing. Is there no support for pci video cards? just seems odd that I get the nice screens all the way through the install, then nothing. I have since re-installed with the base 8mb built in video, a savage chip.
Any help will be great.

---

### Post by az on 2006-05-24
[QUOTE=ed_d]here is an odd one.
I installed a Radeon 9100 128mb pci video card into slot 1 of my xseries 220, went through the install fine on Ubuntu, but as soon as it tries to start the gdi, all I get is a blinking cursor in the upper left corner. I tried reloding with an older nvidia 16 mb pci card, same thing. Is there no support for pci video cards? just seems odd that I get the nice screens all the way through the install, then nothing. I have since re-installed with the base 8mb built in video, a savage chip.
Any help will be great.[/QUOTE]
This is something that needs to be addressed in future releases.


The problem is that your video card is configured at install time, and it is not autodetected if you change it.

You need to 
1- change your card
2- boot your computer and go into recovery mode
3- run
dpkg-reconfigure -phigh xserver-xorg 
4- run
init 2

and it will detect and use your new card properly.  As it is, you are not given any reason to tell you why your graphics are not working.  But it is an easy enough fix....

---

### Post by ed_d on 2006-05-24
well, like i said, had either card in at install time. Went through the first part of install fine, rebooted, finished install, says on bottom starting gdm, then black screen and cursor in upper left corner.
Ill give you suggestion a try.

---

### Post by ed_d on 2006-05-24
Oh, just thought of this too. When I would try off a live CD it did the same thing as in installing it.

---

### Post by az on 2006-05-24
Sorry, I misread your message.  Can you dissable the onboard video, or at least give priority to the pci one from within your bios?

Thry changing that and then reconfiguring Xorg.

---

### Post by ed_d on 2006-05-25
I can. BIOS seems to do theis when it senses a video card inserted in the slots to. But I can hard disable via a jumper on the board too. Its odd as I have tried a similar 16mb nvida in my x240 at work and got the same deal. 
Maybe the same deal with how the splash screen works on systems with IDE but reverts back to text ont the machines with SCSI ( the screen that shows the status bar when loading the modules)
Has anyone else been able to get PCI graphics cards to work? If so, what brand? The 8mb savage works fine, but seeing as its on board video, it really uses cpu cycles...

---

### Post by az on 2006-05-25
[QUOTE=ed_d]I can. BIOS seems to do theis when it senses a video card inserted in the slots to. But I can hard disable via a jumper on the board too. Its odd as I have tried a similar 16mb nvida in my x240 at work and got the same deal. 
Maybe the same deal with how the splash screen works on systems with IDE but reverts back to text ont the machines with SCSI ( the screen that shows the status bar when loading the modules)
Has anyone else been able to get PCI graphics cards to work? If so, what brand? The 8mb savage works fine, but seeing as its on board video, it really uses cpu cycles...[/QUOTE]
Well, all of the pci video cards that I have work fine.  I have one card that does not work with a particular motherboard, but works fine elsewhere.  However, in that case, the machine won't even boot.  The machine does not even power up the drives with it in place.

When you boot with the pci card, what happens when you hit CTRL-ALT-F1, after you have booted and X has failed to start?  Can that get you into a console?  If so, post the Xorg logs in /var/log

Maybe 
cat /var/log/Xorg.log > file
and save that file to usb disk?

---

### Post by ed_d on 2006-05-25
Ill do that this weekend. with my work schedule and my commute, i have enought time when I get home to eat and shower. Will get that up here soon. thanks again.

---

### Post by ed_d on 2006-05-25
Also, if I use the old Nvida card, what drive set should I down load and install? Ill update when I get home with the type of card it actually is.

---

### Post by az on 2006-05-25
[QUOTE=ed_d]Also, if I use the old Nvida card, what drive set should I down load and install? Ill update when I get home with the type of card it actually is.[/QUOTE]
I am pretty sure that you will need the nvidia-legacy driver to use hardware acceleration.  But you should get proper 2d video by default, using the nv driver that will be autodetected and used by xorg.

So, you shouldn't need to do anything special to get to the desktop.  Just install the nvidia-glx-legacy packages if you want to use hardware acceleration.  The default desktop does not use it (hardware acceleration)- you get no benefit from it unless you want to play tuxracer and neverball...

---

### Post by ed_d on 2006-05-25
ok, the board is a nvidia 9629U. Ill grab the legacy drivers and test it out and keep you updated.
Thanks again

---

### Post by ed_d on 2006-06-06
Azz, sent you an email with the log, let me know what you think.

---

### Post by ed_d on 2006-06-10
Well, i used the jumper to disable the on board video and that did it. Thanks for the help in pointing that out.

---

