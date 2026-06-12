---
title: "NVIDIA 9400gs doesn't detect LCD tv"
date: 2008-06-30
forum: Mythbuntu
---

### Post by Crusty Juggler on 2008-06-30
After having a perfectly working Mythbuntu set-up for several weeks, last week it froze up in the middle of watching TV and I had to do a hard reboot.  After the reboot, my LCD TV was no longer detected through my DVI-HDMI connection.  I was able to connect with a VGA cable, but only at 640 x 480 and as a CRT.  

I didn't have anything irreplaceable on there, so I figured I'd just do a quick re-install and everything would work itself out.  Wrong.  So where I am right now is at a fresh, fully updated install with the newest NVIDIA driver (173.17.09, newer than the Envy installed driver) that doesn't detect my LCD and is currently running off a VGA cable at a terrible resolution.  

Any advice?  One of the real drawbacks to Mythbuntu is that it is so stripped down that it can be difficult for a relative linux noob like myself to do much more than the very basic.  Thanks for any help.

NB: [This guy]("http://ubuntuforums.org/showthread.php?t=844911") is having the same problem as me, except I'm not running a 64 bit machine.  I will try starcannon's suggestions, but I am not particularly hopeful.

---

### Post by Crusty Juggler on 2008-06-30
I have run through [starcannon]("http://ubuntuforums.org/showpost.php?p=5086971&postcount=6")'s guide and it has solved my issue about 50%.  Using my LCD TV as a monitor via the VGA cable works now and offers a wide range of resolutions, with 1024 x 768 as the optimal, but the TV is not detected via the DVI cable as it previously was.  

Any suggestions anyone?

---

### Post by Crusty Juggler on 2008-07-01
I thought it would be smart to add the following line to xorg.conf under "Devices"
Options "UseEDID" "True"

But nothing changed.  Still no detection of the TV, though it works decently well as a "CRT" monitor with a VGA cable.

Does anyone have any advice?  I have pretty much exhausted my knowledge base here.

---

### Post by larsolav on 2008-07-01
Forgive me if I am way off base here, but because nobody else has responded I thought I might just confuse the issue further...

When you power up the machine, do you get the pre-operating system screens (the bios loading etc)? when connected through the DVI-HDMI? If not, do you remember if you did before? 

I also have a DVI-HDMI connection to my LCD TV and I see the startup page for my motherboard. So that means that the video card (7600) sees my TV before Ubuntu loads up.

Also, have you tried staring with the Muthbuntu live CD? Maybe you can compare the xorg files when loading the live CD with the file on your hard drive (I think I remember some posts about that a few months ago)

Good luck!

---

### Post by Crusty Juggler on 2008-07-01
> **larsolav said:**
> Forgive me if I am way off base here, but because nobody else has responded I thought I might just confuse the issue further...

When you power up the machine, do you get the pre-operating system screens (the bios loading etc)? when connected through the DVI-HDMI? If not, do you remember if you did before? 

I also have a DVI-HDMI connection to my LCD TV and I see the startup page for my motherboard. So that means that the video card (7600) sees my TV before Ubuntu loads up.

Also, have you tried staring with the Muthbuntu live CD? Maybe you can compare the xorg files when loading the live CD with the file on your hard drive (I think I remember some posts about that a few months ago)

Good luck!

Thanks for the reply.  When it was working correctly, I would get the bios loading and mythbuntu splash screens via the DVI cable, but only if the VGA cable was not connected.  If VGA was connected, the DVI input would show nothing until Mythbuntu loaded and went to the Pre-scaling themes... load screen.

Now, of course, I see nothing with the DVI connection...

I will try checking the xorg files when loading off of the live cd today and let you know what I find.

---

### Post by Crusty Juggler on 2008-07-01
xorg.conf when running the live cd is very vanilla.  Everything is "Configured Video Device" and "Configured Monitor" presumably because none of the nvidia drivers come pre-installed.

---

### Post by larsolav on 2008-07-02
I wonder if it could be a hardware problem? If you before were able to see the bios loading on the LCD TV when only it was attached, and now you don't, maybe it could be a problem with the DVI port of your graphics card?

---

