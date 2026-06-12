---
title: "Fail to initialize the NVIDIA kernel module"
date: 2010-09-29
forum: Multimedia Software
---

### Post by aleska on 2010-09-29
Problem: computer and graphics card had been running for months without problem.  For some reason, last night, things locked up...wouldn't think it's related, but happened when I noticed I was locked out of creating new folders on my usb attached My Book storage drive.  So, from terminal I tried to sudo change permissions to read/write.  Everything locked up...

Now, every time I reboot it states needing to use low graphics mode "Screen, graphics card, and input device settings could not be detected correctly."  

When I check the error log I see:
"(EE) Failed to initialize the NVIDIA kernel module..."

"(EE) NVIDIA(0): ***Aborting***
Screens found but none have a usable configuration.
Fatal Server Error - no screens found"

If I try to then start in safe low graphics mode or restart X, I get the Ubuntu splash screen with the 5 dots that turn red to show progress...but nothing ever happens.  

I can switch to VT 1, login at command line, and type "startx" and then the graphical desktop loads just fine.  Video playback, etc. is perfect and fine - not in low graphics mode at all.  System seems totally normal.  

However, I have to go through these steps each time I reboot.  

Also, I noticed that when I try to boot from Ubuntu Live CD I can't.  I get as far as picking English as a language, then screen goes blank and goes to power saving mode (no signal being sent).  This greatly concerns me as even though I have a work around for now - getting to command line then startx'ing - if I ever needed to reinstall from the CD, it seems I can't.  

Some info on my pc:
[LIST]
[*]Running 10.04 on Compaq Presario SR1950NX
[*]AMD 64
[*]GeForce 6150 LE/PCI/SSE2/3DNow! <- believe built onto motherboard
[/LIST]

Any ideas on what I can do to fix?  Is this a sign that something is wrong with my video card?  Any help appreciated.  Thanks!
-Alex (aleska)

---

### Post by 23dornot23d on 2010-09-29
This could possibly be related to the USB device .....

I have had a similar problem ..... getting as far as English .... what it then tries to do
is unmount devices to continue .....

if it hangs .... its probably because its having trouble with the USB drive .....

maybe you should check it out first  ..... 

Have a look at the disk with gparted first ...... see if it looks ok .....

and post a screen shot ....... of what it shows .... thats if it lets you run it .....

( Sounds like the graphics card is ok if it starts and runs ok using startx ..... )

---

### Post by aleska on 2010-09-29
Do I just run gparted from terminal?  Not familiar with this tool.  Are there options I should run with it?  Thx!

---

### Post by aleska on 2010-09-29
Tried rebooting without the USB MyBook storage device attached.  Same issue and error.

---

