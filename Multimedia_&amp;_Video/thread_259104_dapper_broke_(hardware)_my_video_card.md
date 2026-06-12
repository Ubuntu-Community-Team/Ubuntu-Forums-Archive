---
title: "dapper broke (hardware) my video card?"
date: 2006-09-16
forum: Multimedia &amp; Video
---

### Post by SC2Sick on 2006-09-16
I finally got my 865PE Neo2 system to boot the hard drive i had ubuntu installed on (from another pc)

it ran great.  going from the 766 celeron (512mb RAM) system i was using to see if i like ubuntu.. to a 2.4HT 800mhz FSB P4 with 1.5GB RAM it was better.

i mean the system just flew..  but to my point.  on this system i had an ATI Radeon 9600 PRO.  before i could run X i reconfiged xorg.conf to use the ati drive and as you can see above it ran well.

I set the screensaver as matrix since it ran like crap on my work comptuer presumable because of the graphics card it had.  looked fine in the preview.  i installed wine and xmms easily enough..

then i used easyubuntu to install the ATI 3d drivers (don't know if they're different or not).

rebooted the system after closing X to install the 686 kernel.  then i was installing steam via wine so i could CS and then i went to get some pizza (sausage if you're intersted) and the screensaver was on, i watched it for probably 10 seconds before i noticed it seemed frozen.  i tried to move the mouse with no success, so i figured X crashed like i've heard it does with dapper from time to time.

so i pressed the reset button.. and i get no display, just see my screen (17" Samsung Syncmaster (LCD)) searching between analog and digital.  in this case my system was plugged into the analog because i can't find my DVI cable.

has anyone heard of software damaging hardware?  i'm trying to find my DVI cable to see if that will work..

---

### Post by SC2Sick on 2006-09-16
update, using DVI to vga adapter.  no luck

---

### Post by SC2Sick on 2006-09-16
further update..

removed video card and installed in my Sempron 2400+ system and it posted... weird.  so i put it back in this system and booted to XP.  odd.  makes me aprehensive..

---

### Post by tseliot on 2006-09-17
boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "ati" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

On next reboot the Xserver should work fine

NOTE: if the problem is not solved try using "vesa" or "vga" instead of "ati" and try again.

---

### Post by SC2Sick on 2006-09-17
when in windows couterstrike crashed and pulled the same stuff...  i'm not sure if the card is done or the rest of it....

:(

---

### Post by Kimon2 on 2006-09-23
OMG. This literally just happened to me 5 minutes ago. I was installing some updates in Ubuntu 6.06. While doing this I decided to change my current theme. I did so and the system froze. I could move the mouse cursor but it would not respond when i clicked on anything. I then decided to push the reset button. So I booted up and selected Windows Xp on the GRUB boot menu. So it did the windows loading bar, and then my lcd would just switch to the other computer.....i pressed the input button again...and nothing...it wouldnt find the computer on my monitor. I could hear the windows startup music but i didn't see anything on the screen. So naturally I reset the computer again and to my demise it wouldn't even see the BIOS boot up screen. My computer screen led would just turn amber.

My system specs are as follows
AMD Duron 950mhz
20GB Seagate Barracuda
256mb PC133 SDRAM
64mb nVidia GeForce 4 MX
etc....

I will try the things that are mentioned above, and get back.

Any help much appreciated. Cheers :KS

---

### Post by george314 on 2007-04-19
I would try using an external monitor to back up all non-replaceable (important) data.
Then I may try unplugging my cards from the motherboard, and the re plugging them.  Of course I would unplug all cables from the computer and ground myself first by touching a metal part of the computer before unplugging any cards.  

Then I would replug all my cards, plug in all the cables in the back of the computer and try restarting.  If no BIOS screen shows up still I would swap video cards with a new one or a spare one that works and then reboot.

Computer should work by then.

George

:guitar:

---

