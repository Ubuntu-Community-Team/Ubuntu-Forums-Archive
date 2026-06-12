---
title: "Mythbuntu 9.10 will not boot up"
date: 2009-11-06
forum: Mythbuntu
---

### Post by MountainX on 2009-11-06
I hope I'm posting this in the right place now... I have a grub2 boot partition on (hd0,1). I installed Mythbuntu 9.10 32bit on (hd0,9), a logical partition and I installed the boot loader into that partition using the advanced option at the end of the installation process. I have the grub2 on the boot partition set to chainload Mythbuntu on (hd0,9).

What happens is that Mythbuntu seems to go through the bootup process correctly but it stops at the console login and the whole screen is flashing/blinking. In fact, even keyboard input is sporatic. I'm afraid the system is in a state that could damage the harrdware. It is not even possible to type enough to log in. The only option is to reboot.

I thought the problem was related to a defective installtion, so I installed fresh again (reformatted partition). I get the exact same problem after the second install.

I have Kubuntu, sidux and openSUSE on other partitions. All will boot up correctly. Mythbuntu is the only OS that will not boot. However, if I install Mythbuntu without putting the boot loader into its partition (i.e., using the whole hard drive) Mythbuntu will boot correctly on this computer.

My computer is a Thinkpad T61p.

There is some background in [this thread]("http://www.linuxquestions.org/questions/linux-general-1/opensuse-wont-boot-after-i-resized-its-partition-grub2-related-766528/"), but it is largely unrelated.
 		                   		  		  		 		 			 				__________________

---

### Post by MountainX on 2009-11-06
Is there anything that would prevent Mythbuntu from booting from a logical partition?

I used Super Grub Disk 0.9799 to boot up Mythbuntu with these commands:

```
kernel (hd0,8)/vmlinuz
initrd (hd0,8)/initrd.img
boot
```I get the same error as described in the post above.

---

### Post by geolizardo on 2009-11-07
Not that this helps you, but I am experiencing the same issue.  The install goes perfectly.  And after the first restart away from the LiveCD environment, I am presented with a flickering screen and a rapidly flashing Num Lock key.  It is also a tty login, even though I asked for automatic login.
 
I thought at first it might be the video driver. I would always change from the opensource to the NVIDIA driver during the install.  This allowed me to specify TV Out, where the Open source driver kept that grayed out.  But a video diver that affects a keyboard?  Is this a world I want to live in?
 
I ran the install through the liveCD environment (3x) as well as running setup right from boot(once), all to the exact same result. I am currently running the install a 4th time.  This time I am using the Open Source driver.  I'll let you know how it goes. 
 
It might be worth mentioning that with the exception of the HDD, I had version 8.04 running on this system for over a year.  But the primary drive failed and, well, you know that song already.
 
Compaq D510 2Ghz, 1 gig ram, 2x 500Gig IDE HDD, NVIDIA 9400 series, Hauppage 150 tuner. Front/back end combo

---

### Post by MountainX on 2009-11-07
> **geolizardo said:**
> Not that this helps you, but I am experiencing the same issue.  The install goes perfectly.  And after the first restart away from the LiveCD environment, I am presented with a flickering screen and a rapidly flashing Num Lock key.  It is also a tty login, even though I asked for automatic login.
...
Front/back end combo

Yes, sounds exactly like my situation. Thanks for replying.

---

### Post by geolizardo on 2009-11-07
That last approach was unsuccessful...but different.  I got an IO error 80% in to the install.  I am DL-ing a new ISO, and will try that once I get back from the kids' skating lessons.

---

### Post by MountainX on 2009-11-07
I think this bug report may be related.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/444395](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/444395)

---

### Post by geolizardo on 2009-11-07
Here is an update on my struggle.  
I Dl'd another Mythbuntu ISO, this time using the Direct Desktop option.  After many attempts at installation, I still had no success.  This time, the IO error would pop up after 40%.  Okay...so then I replaced the DVD Drive.  Same result.
I then went back to the torrented Download ISO.  This time with the new DVD drive.  Well whaddayaknow?  It installed!  At this point, I hope it goes without mentioning that I didn't select the NVIDIA driver during installation.  So right now the VGA output works fine, but SVIDEO output looks slightly worse than Intellivision football.
Now I am going to struggle through running the driver file from the NVIDIA website.  I'm somewhat new to this, but I think I'll be OK.

---

### Post by MountainX on 2009-11-07
> **geolizardo said:**
> 
Now I am going to struggle through running the driver file from the NVIDIA website.  I'm somewhat new to this, but I think I'll be OK.

I have found the nvidia driver installation method you mention to be fairly easy, but you can also consider using EnvyNG.

---

### Post by geolizardo on 2009-11-08
The NVIDIA driver install went well.  No issues to report on driver install.  I now have the TV Out working on the Myth.

However...

I have a couple issues that have to do with the placement/resolution of the screens.  I will start a new thread as it has nothing to do with this issue.

But my flickering video issue was resolved by installing with the Open Source Driver and then once that was stable switching to the NVIDIA driver.  For any N00b's out there, I do recommend the EnvyNG tool.  I tried that afterwards and it can't be much easier.

Good luck MountainX. I hope it works out for you.

---

