---
title: "bad xorg.conf boot freeze"
date: 2010-09-29
forum: Multimedia Software
---

### Post by jgw on 2010-09-29
I have installed 10.04 on a system I built for a friend.  The machine has a unichrome pro built in video.  The driver was automatically loaded.  My problem was that I wanted it to have at least a 1024x768 or 1152x864  the max was 800x700 (I think).  Anyway, I messed with the xorg.conf file and screwed it up. being lazy I never tested it (I know!)  Now, when it boots its gets to "UBUNTU" with 5 red dots and freezes.  Then I tried the pressing the shift key and actually got the grub menu one time and got rid of the splash thing and pressed the wrong key instead of inserting "text" so, now I am doubly screwed (I am working very hard at screwing the pooch here!).  So, first I gotta get a minimal boot so that I can deal with the xorg.conf file but I cannot get the boot to stop until it freezes (I have tried - for 2 hours).

I have another machine running so I can receive any replies.  

I apologize for all the words and would be grateful for any help!

---

### Post by Yellow Pasque on 2010-09-29
Press 'Esc' right after BIOS initialization done to access grub and boot to 'safe mode'
Delete/rename your /etc/X11/xorg.conf
You should only need a very generic xorg.conf. The only change you'll probably need to make is in the Monitor section (use the monitor manufacturer's specs for vertical refresh and horizontal sync if you can find them, otherwise use the ones in the example):
```
Section "Monitor"
    HorizSync    28-72
    VertRefresh  43-60
    # Leave other lines as they are
EndSection
```

---

### Post by jgw on 2010-09-29
Again, thanks for the reply. 

I now have a machine that boots.  The interesting thing is that it booted up with a HUGE screen, 15??xwhatever.  I used xrandr to reset the size to something I could deal with.  Then I rebooted and it came back up with the huge screen again.  My question now is how do I set the resolution so that it remains from boot to boot.  This is a brand new problem with me - I am usually fighting for a bigger resolution, not smaller.

Oh, I checked the xorg.conf file.  There are no references to the resolution of the screen.

---

### Post by Yellow Pasque on 2010-09-30
Post your /var/log/Xorg.0.log. Most likely, you need to set the size of the virtual screen manually in xorg.conf

---

### Post by jgw on 2010-09-30
Makes sense to me!
Thank you!

---

### Post by Yellow Pasque on 2010-09-30
Is your issue resolved?

---

### Post by jgw on 2010-09-30
[SOLVED]  Sorry - forget to tell you that.  I did, however, have to removed a bunch of stuff from the screen section that were automatically inserted on creation.

---

