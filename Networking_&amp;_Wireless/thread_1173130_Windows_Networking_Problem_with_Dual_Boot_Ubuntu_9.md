---
title: "Windows Networking Problem with Dual Boot Ubuntu 9.04"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by ptorpey on 2009-05-29
I had Windows XP Pro, SP3 installed on my system.  Networking worked fine via an ethernet cable connected to my home router.


Then I installed Ubuntu 9.04 on a separate partition of my hard drive.  I now have a dual boot Windows/Ubuntu system.

When I run Ubuntu, I can connect to the internet fine.

If, however, I restart the computer and boot into Windows, I cannot connect to the internet.  In Control Panel / Network Settings, Windows indicates that my Broadcom Internal Network Adapter is unplugged.  The ethernet cable is definitely plugged in and worked before installing Ubuntu.

Next, I re-installed Windows from a disk image backup.  Then, I was able to conenct to the internet when using Windows.  However, if I then reboot into Ubuntu and connect (successfully) to the internet, and then reboot into Windows again, I cannot connect to the internet using Windows and Windows reports that the cable is unplugged.  Thus, this behavior is quite reproducible.

What is the problem here?  How can Ubuntu be affecting my Windows drivers?

This is very frustrating and I'm afraid to boot into Ubuntu again for fear that it will destroy my internet connectivity when I use Windows the next time.

These two operating systems ought to be able to co-exist.

Any help or suggestions are appreciated.

Thanks.

-- Pete[/U]

---

### Post by Iowan on 2009-05-29
> **ptorpey said:**
> These two operating systems ought to be able to co-exist. They can... 
I've seen another thread with similar problem, and a couple going the other way.  Do you do a full power-down reboot?  Apparently, sometimes the driver's don't (always) get completely reset on a "3-finger salute."  I'll see if I can find one of the other threads - but it might take awhile.

---

### Post by ptorpey on 2009-05-29
I have tried turning off the computer and then re-booting into Windows.  Once that worked and several other times it did not seem to work.

This is terrible!

---

### Post by saisai on 2009-05-29
I had a similar problem. I used to use Ubuntu 8.10 and then I think after some updates that I installed the wired internet stopped working suddenly, when I went into my windows XP partition it stopped working there also. I tried to reformat my whole laptop with 8.10 but no luck and then I tried to reformat with 9.04 but it didnt work either. Now I am considering reformatting it to windows XP. and see if I can get internet.

---

### Post by ptorpey on 2009-05-29
The first time this happened to me I restored my Windows partition from a backup disk image and then I could connect to the internet again using Windows.

However, after this, I rebooted into Ubuntu, used the internet successfully, and then rebooted into Windows once more.  At this point, the network connectivity in Windows was broken again.

I'm reluctant to boot in Ubuntu any more once I get my Windows connection working again.

There must be something wrong with the Ubuntu drivers that is leaving the network card in a strange state.

I have a Dell computer with an integrated Broadcom Network Adapter.

-- Pete

---

### Post by saisai on 2009-05-29
my comp is dell too. check out this thread, I havnt tried it yet, but they might be on to something. 
[http://ubuntuforums.org/showthread.php?t=1141608](http://ubuntuforums.org/showthread.php?t=1141608)

if u figure it out can you post how you solved it. thanks

---

