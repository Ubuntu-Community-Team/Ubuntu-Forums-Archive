---
title: "Login screen error. GUI / X error"
date: 2008-04-01
forum: Multimedia &amp; Video
---

### Post by The Pinny Parlour on 2008-04-01
Hello

When I start my PC, I can see the initial BIOS screen, then I see the Ubuntu Progress Bar then it attempts to go into GUI and fails to black screen or standby mode.  I Ctrl,Alt,F3 to get to a prompt, I then tried to Atl,F7 and startx and they fail as well.

Can anybody help me get this thing to start please?   

I have not done anything that would make it become unstable.

Thank You

---

### Post by pbcartwright on 2008-04-01
sounds like a video driver problem, do you have an ATI or NVIDIA video card??
you might want to look here:
[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

basically:
 Step 2: Run the reconfiguration

First start by making a manual backup (even though one will be auto-generated in the form xorg.conf.YearMonthDayTime):
Code:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

Now run the configuration:
Code:

sudo dpkg-reconfigure xserver-xorg

---

### Post by The Pinny Parlour on 2008-04-01
Thanks mate.

Funnily enough, I just booted in a live cd and mounted a USB HDD.  I then made a root user so I could copy my data from hdd to backup USB hdd.   Upon rebooting the system, it all works.  :confused:

anyway, I hope it holds out till the next release.

---

### Post by pbcartwright on 2008-04-01
no worries Mate!

you may want to look in /var/log for logs that may have info on your problem. you can also look under your home directory at .xsession-errors . It may give you a hint as to what happened..

---

### Post by The Pinny Parlour on 2008-04-02
Ok the issue is back.

This happens when I boot the computer at the start of the day.

I turn it on, I see BIOS screen, I then see the Ubuntu progress bar.

After that, the PC monitor will go into standby mode.  I can however enter in my username and password without seeing it on the screen, and I can hear Ubuntu startup.  

I then press Ctrl+Alt+F3 to get to a prompt and attempt to restartx but it doesn't work.

Nvidia 7600GS


Any ideas?

Thank you

---

