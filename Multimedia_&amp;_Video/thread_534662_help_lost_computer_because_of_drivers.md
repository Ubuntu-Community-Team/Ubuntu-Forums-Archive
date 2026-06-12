---
title: "help lost computer because of drivers"
date: 2007-08-25
forum: Multimedia &amp; Video
---

### Post by nynoah on 2007-08-25
OK slightly complicated.........OK    I have I 386 fiesty.  I was just setting it up.  I was trying to get compiz fusion to run right but the computer was locking.

I have Nvidia graphics card

Here is the progression of events.  I originally downloaded the drivers from Automatix2.  I was reading that the drivers that Envy provided were better.  So I loaded those instead.  I got fusion to work but it started locking up on me.  So I tried to switch back to the drivers from Automatix2 and then upon the next reboot the computer defaults to a screen telling me there is something wrong with my Xorg.  I checked my Xorg and it says my Nvidia drivers are enabled, but it still does not work

What do I need to do to just default back the standard drivers in Ubuntu so I can fix this.  Right now I can not even do anything other than command prompt interface.  I am horrible at that too.

Thanks
NOah

---

### Post by vpjr on 2007-08-26
hi, 

when you wrote that nvdia is enabled, you mean that when you look at the xorg.conf, the Section "Device" has a Driver "nvdia"?

i think for old drivers that should be Driver "nv"

or may i suggest a workaround:

if you have the Live CD and your setup runs with, then:

   a. boot with Live CD
  
   b. mount your harddisk

   c. go to /etc/X11, and, as root, copy the xorg.conf to your harddisk's /etc/X11.

   d. boot

   e. i'm assuming you've restored the old drivers of course.

i hope that helps. please feedback me.

regards,

ven

---

### Post by tseliot on 2007-08-26
Boot in Recovery Mode (select it from the GRUB menu)

type:
```
dpkg-reconfigure xserver-xorg
```

select the "vesa" driver and press ENTER whenever you don't know the answer to a question.

then type:
```
reboot 
```

and boot as usual

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

---

### Post by nynoah on 2007-08-28
Thanks...........I thought no one could help me......I will try what you were sugesting and keep you posted.

Noah

---

### Post by nynoah on 2007-08-28
Actually wait.  I can not get into recovery mode from where I am at.  The computer defaults to a script log in.  It does not get me to the area where I can choose recovery mode.  Is there a way to use the script mode to get to the recovery.  

Have I explained what I am talking about?   Or should I try again.

Noah

---

### Post by tseliot on 2007-08-29
Turn on your computer, then, after the BIOS screen, you should see a countdown. Press the down keyboard arrow and select recovery mode.

---

### Post by nynoah on 2007-08-29
Tseliot............Thank you so much for taking the time to answer my question.  People like you are an asset to the Ubuntu community.  I got my computer back up with you help.  

grazie

Noah

---

### Post by nynoah on 2007-08-30
Tseliot..............I now can not get into my gnome interface.  I have KDE working fine.  I think this has something to do with my video drivers.  How can I just set them to what they were when they came from my original install disk?  I think if I do that, I can get my Gnome back.

Noah

---

