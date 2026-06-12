---
title: "I broke my &quot;xorg.conf&quot; file"
date: 2006-07-15
forum: Multimedia &amp; Video
---

### Post by mjpatey on 2006-07-15
Hi, Group-

I'm very inexperienced with Ubuntu (and Linux for that matter).

To make a long story short... while joyfully poking around, a tutorial I decided to follow had me editing my /etc/X11/xorg.conf file.  After applying the suggested change and rebooting, I was faced with a window whose border was drawn with ASCII characters (as a Win user, I'd call it a DOS screen), telling me I broke "xorg.conf".

So I'm trying to get into that file from a command prompt so I can edit out the changes I'd made.

Problem is, I can "CD" the /etc directory, but once into it, I can't just CD /X11... it says there's no such directory.  When I type "ls" to list the directory contents, it does show a directory called "X11", but for some reason I can't get into it.  I tried adding "sudo" before the command because I'd seen it done before when trying to access privileged files, but I don't know the proper syntax for its use.

Does anybody know how to get into the /x11 directory, so I can re-edit my xorg.conf file?  At this point I just want to get into it and undo the damage.

Thanks for any help you may have!

-Mark

---

### Post by jordilin on 2006-07-15
Try to boot from an Ubuntu Live Cd and try to get into that directory.

---

### Post by jordilin on 2006-07-15
When you are going to touch system files always do a backup of that file and leave it in your home directory. If something goes wrong you can always go back by booting from a livecd and replacing the corrupted file

---

### Post by mjpatey on 2006-07-15
jordilin-

Thanks for the reply, the tutorial I was working from actually had me keep a backup of the file, renamed xorg.conf.bak.

So the original version of the file is still there if I want to simply rename it to xorg.conf, but the problem is still that I don't know how to access the directory it's in.

If I reboot from the Live CD, won't I just run into the same problem, only from the terminal window?

Unfortunately, I can't test the suggestion to boot from CD right now, as I'm at work for the next 7 hours :-(  But I do appreciate your help, and if no ground-breaking solution comes in, it'll be the first thing I try.

-Mark

---

### Post by dtfinch on 2006-07-15
cd X11 not cd /X11, or just do cd /etc/X11

To just edit the file, type "sudo vi /etc/X11/xorg.conf" and enter your password, press 'i' to enter insert mode, make your changes, press esc to return to command mode, type 'wq', and press enter to save and exit.

---

### Post by jordilin on 2006-07-15
> **dtfinch said:**
> cd X11 not cd /X11, or just do cd /etc/X11

To just edit the file, type "sudo vi /etc/X11/xorg.conf" and enter your password, press 'i' to enter insert mode, make your changes, press esc to return to command mode, type 'wq', and press enter to save and exit.

Of course, :oops:  I didn't note that. You must provide the full path, or just cd X11 , do not type cd /X11.

---

### Post by mjpatey on 2006-07-15
Thank you, everyone!

All this makes sense.  I think I also may have failed to observe case... if I remember correctly, the X11 directory uses a capital "X", and by default I bet I typed it in lowercase (old habits die hard!)

I appreciate the help.  As soon as I get home tonight, I'll try everything!

-Mark

---

### Post by mjpatey on 2006-07-16
OK, I've booted from my live CD in order to revert my "xorg.conf" file to its pre-broken state... unfortunately, the only "xorg.conf" file I can find is the one created during my live session.

I've looked into System -> Administration -> Disks, and do indeed see the partition that my real install lives on, but I don't know how to mount the partition, or be able to access it in any way during the live session.

All this is even more necessary right now because for some reason, GRUB (dual boot loader) is not working properly either.  It slows to a crawl during boot-up, and eventually either returns an error #21, or finally gives me the boot selection screen.  When it does give the selection screen and I select any Ubuntu option (I have 4, including 2 safe modes or whatever Ubuntu calls it), it fails during boot, I assume due to the bad xorg.conf file.  All I get is white text on a black background (like a DOS screen), with the # symbol as the prompt.

Thankfully, GRUB is able to boot to Windows, so I'm not completely hosed yet! :-)

I thought that the source of GRUB's trouble was that the hard drive that Ubuntu is on (my secondary drive, "E:" in Windows) was failing... but it mounts just fine in Windows, and I can even record several tracks of 24/96 audio to it just fine.

So it seems the problem is somewhere in my Ubuntu install, which I take full responsibility for screwing up.

Am I better off just re-installing Ubuntu at this point?  That would reinstall GRUB, I assume, and I'd start with a clean xorg.conf file.  Or is there some way to access the files I need to change from within my live session?

Thanks again for any help you may be able to provide!

-Mark --> ](*,)

---

### Post by jordilin on 2006-07-16
> GRUB (dual boot loader) is not working properly either. It slows to a crawl during boot-up, and eventually either returns an error #21, or finally gives me the boot selection screen Well, I think that due to this you 'll get the problem solved faster if you definetely have a fresh install of Dapper. You'll take less than half an hour :-D Perhaps it is not a proper answer but when system files get corrupted and you are not able to go backwards, the quicker solution is to reinstall.

---

### Post by mjpatey on 2006-07-16
Jordilin-

Wow, I can't believe it... I was finally able to boot to a $ prompt!  Then I did a "sudo vi /etc/X11/xorg.conf" and decided I didn't want to risk destroying the file even more, so I hit "F1" (on a hunch that it would give me help with Vim).  It did, and in the instructions I found a note about editing system files, saying that if I wanted I could type one line of text at the $ prompt to update my xorg.conf file with a fresh one from the Internet.

I did.  Then I rebooted.  So did Ubuntu, in all its fully-functioning glory!  I feel like such a geek now! :D 

I still think the drive Ubuntu is on will need to be replaced, so I'll eventually re-install.  But that aside, it's a great feeling to have dug myself out of this situation successfully.

Thanks everyone for your help!  I'm starting to learn this second language of Linux, thanks to you.

-Mark

---

