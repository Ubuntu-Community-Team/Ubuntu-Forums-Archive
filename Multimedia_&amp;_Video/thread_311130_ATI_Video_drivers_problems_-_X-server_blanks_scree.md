---
title: "ATI Video drivers problems - X-server blanks screen upon shutdown"
date: 2006-12-02
forum: Multimedia &amp; Video
---

### Post by nikdo on 2006-12-02
Hello you all wonderful ubuntu/linux folks.

I was hoping you could help me with this one, I've been working on it on and off for past 2 weeks:

setup:

- Gateway machine, AMD 64bit dual core, 2Gig ram
- HP w19b 1440x900 wide screen LCD
- on board nvidia (can't remember which one)
- added PCI express ATI Radeon X800 XL 256Mb video card
- running Ubuntu Edgy Eft 6.10 64bit

When running with the ATI board, then one serious problem I have is that I cannot really shut down. When I try, screen goes blank, but no shutdown has been initiated. Need to actually power off the machine. Same problem happens if I try to go to console from x-server ALT+F1...F6. System is blank and I can't even go back to x-server or reset or anything else.
Tried 'vanilla' install of ubuntu 6.10 64bit and ubuntu 6.06 64bit. Installed the ATI drivers via apt-get. The drivers seem to work fine and even the glx gears worked. Not sure if the problem is related to the combination of ATI drivers + 64bit ubuntu. Can't seem to find an answer anywhere.


As an alternative, I have removed the ATI board, reinstalled ubuntu 6.10 64bit and installed the nvidia drivers via apt-get. Strangely enough, when I run the x-server after that, I have two problems:

1) can't get the proper resolution, even though I specified it in xorg.conf as 1440x900
2) can't get to see the mouse cursor. IT is weird, because the mouse works (you can see it activating on mouse-over events on buttons, etc, but can't see the actual cursor.

If I switch the driver to vesa or to nv, then I get the cursor, but the resolution drops to 640x480 and can't get it higher - despite my settings of 1440x900 in xorg.cong - (and of course the screen is not accelerated and just scrolling the web pages is slow as molasses). There is a mention in the console that the mouse pointer failed.

[If you require any output from some logs, please let me know the commands, thank you.]

I am sorry if I posted in the wrong forum, I am not sure if this is a 64bit problem or just video drivers one. I am quite new at using linux and would appreciate any help as I refuse to give up and return to windows - I have tasted the freedom and don't want to be caged again.

Thank you sincerely for all your help

Peter

---

### Post by Patrick-Ruff on 2006-12-02
I hope you have access to your xorg.conf file . . . I'm pretty sure the problem lies in there. I've never really heard of this, I had some crazy errors upon booting with compiz, but nothing like this (and compiz when I was using it, was very unstable.) also, as of removing your ati-board, that probably wasn't a very good idea, lol.  if your xorg.conf was still using the other drivers, there would be many complications.

this could merely be some conflicting settings, but its really nothing that I've ever heard of . . . sorry I can't be of much help.  you could try backing up and reformatting, and then thoroughly installing it again and perhaps you'll notice you may have done something wrong.


good luck

---

### Post by nikdo on 2006-12-02
thanks for your reply.

Yes, it's probably some stupid option in the screen section of the xorg.conf - I just dunno which.

By the way, I did reinstall (reformatted the hdd) ubuntu after having removed the ATI video card. I didn't want to have any additional variables to enter into the equation. At this point I was hoping to at least get the nvidia board (Geforce 6100 by the way) working. But I am having issues with that as well - like I said, I loose the cursor display. The 'nv' driver works but it's painfully slow.

Once I resolve the nvidia drivers issue, then I will grab another spare HDD, and try to make the ATI card work, because at that point I can totally screw up the installation - I won't care.

Anyways I have noticed that a lot of people are contributing to the sticky threads for nvidia and ati; so I am slowly making my way through it and trying anything that might help and once I get my setup working I will post it there as well.

Thanks for your post, I do appreciate it!

Peter

---

### Post by witiwap on 2006-12-18
I´m having this problem also, and it appears to have been solved here:

[http://ubuntuforums.org/showpost.php?p=1221148&postcount=5](http://ubuntuforums.org/showpost.php?p=1221148&postcount=5)

---

