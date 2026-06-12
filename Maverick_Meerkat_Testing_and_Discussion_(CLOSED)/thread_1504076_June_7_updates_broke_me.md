---
title: "June 7 updates broke me"
date: 2010-06-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by xeddog on 2010-06-07
I have installed VirtualBox 3.2.2 on my 64-bit Lucid system.  Then I Installed 64-bit Maverick as a virtual machine in VirtualBox.  All was good until today.  With the upgrade to the 2.6.35-1 kernel, I now get a kernel panic and my system is completely broken.  Any ideas how I can fix this?  I will probably just wait a couple of days and then get the latest daily build.

Thanks,

xeddog

---

### Post by boonenoob on 2010-06-07
thats why you shouldn't update your kernel to an unstable version :(
did you just update your kernel today?

*EDIT* just looked at screenshot. hmmmm it can't mount the root folder? have you been messing around with ```
sudo nautilus
``` lately?

---

### Post by davideotape on 2010-06-07
Well, for a start if you want a bootable system choose another kernel in grub!

---

### Post by jppr on 2010-06-07
sudo update-grub2

---

### Post by jfernyhough on 2010-06-07
> **jppr said:**
> sudo update-grub2

That relies on being able to get into the system; just to spell it out you'll need to chroot in then run it. :)

This seems to happen from time-to-time; my USB disk installation of Kubuntu has done exactly the same thing (which reminds me, I should really fix it. :D)

--edit
And that's mine fixed. Haven't updated this installation for a while...

---

### Post by xeddog on 2010-06-08
When I start the virtual machine, it boots directly into Ubuntu.  There is no grub menu or anything else.  When this kernel panic occurs is very early in the boot process.  Just a few seconds as a matter of fact.  I don't even get the spash screen.  So with no grub menu there is no recovery console or anything like that, and there is no terminal that I can get to.    I think I am screwed. 

But to answer a few of the responses directly - 

boonenoob - No I have not.  When the installation was running it was pretty much vanilla.  

davideotape - No grub menu so I cannot select any other kernel

jppr & jfernyhough - I never get to a place where I can do the update-grub 


xeddog

---

### Post by philinux on 2010-06-08
> **xeddog said:**
> When I start the virtual machine, it boots directly into Ubuntu.  There is no grub menu or anything else.  When this kernel panic occurs is very early in the boot process.  Just a few seconds as a matter of fact.  I don't even get the spash screen.  So with no grub menu there is no recovery console or anything like that, and there is no terminal that I can get to.    I think I am screwed. 

But to answer a few of the responses directly - 

boonenoob - No I have not.  When the installation was running it was pretty much vanilla.  

davideotape - No grub menu so I cannot select any other kernel

jppr & jfernyhough - I never get to a place where I can do the update-grub 


xeddog
You need to press the shift key straight after post to get in to grub. Then select the older kernel.

[edit] 2.6.35-1 Boots fine here just tested.

---

### Post by xeddog on 2010-06-08
philinux - I didn't know that about the shift key.  It didn't work the first time I tried it so I guess you have to be very quick to get the key pressed at the right time, but it work perfectly the second time. I'm running again on the older kernel.  

Thanks

xeddog

---

### Post by xeddog on 2010-06-08
Well, that got me into the grub menu and I was able to select the older kernel, but it turns out that the file system was toast.  Not sure exactly what happened, but it was corrupted.  I'm just gonna re-install (AGAIN!!) anyway.

Thanks again,

xeddog

---

### Post by philinux on 2010-06-08
> **xeddog said:**
> Well, that got me into the grub menu and I was able to select the older kernel, but it turns out that the file system was toast.  Not sure exactly what happened, but it was corrupted.  I'm just gonna re-install (AGAIN!!) anyway.

Thanks again,

xeddog

Could you not have run fsck from the recovery mode? Or from a chroot?

---

### Post by davideotape on 2010-06-08
> **xeddog said:**
> philinux - I didn't know that about the shift key.  It didn't work the first time I tried it so I guess you have to be very quick to get the key pressed at the right time, but it work perfectly the second time. I'm running again on the older kernel.  

Thanks

xeddog


I think you can hold it down instead of just pressing it to get a 100% success rate :) (not too sure though cause for some reason I always get grub appearing)

---

### Post by xeddog on 2010-06-08
davideotape - I tried just holding down the shift key and it seems as though that is counted as only 1 key press and it does not repeat.  Twice in a row it failed.  What does work is as soon as I see the Oracle splash screen I start pressing both the right and left shift keys alternating as fast as I can.

philinux - I did run fsck and it seemed like there was an error on every single file in the virtual disk.  Rather than screwing around with it, I just re-installed.  That was another story in itself.  The short version is, when I launched VB, I got a message telling me that 3.2.4.somethingsomething was available,  so I upgraded it.  Then I restarted the Maverick install again (and again and again) and had all sorts of problems similar to the filesystem problems.  Then I started thinking that there must have been some "leftover" VB 3.2.2 modules somewhere, so I rebooted.  After the reboot, things went perfectly. So I am finally back to where I started . . .almost.

xeddog

---

### Post by ranch hand on 2010-06-08
> **xeddog said:**
> davideotape - I tried just holding down the shift key and it seems as though that is counted as only 1 key press and it does not repeat.  Twice in a row it failed.  What does work is as soon as I see the Oracle splash screen I start pressing both the right and left shift keys alternating as fast as I can.

philinux - I did run fsck and it seemed like there was an error on every single file in the virtual disk.  Rather than screwing around with it, I just re-installed.  That was another story in itself.  The short version is, when I launched VB, I got a message telling me that 3.2.4.somethingsomething was available,  so I upgraded it.  Then I restarted the Maverick install again (and again and again) and had all sorts of problems similar to the filesystem problems.  Then I started thinking that there must have been some "leftover" VB 3.2.2 modules somewhere, so I rebooted.  After the reboot, things went perfectly. So I am finally back to where I started . . .almost.

xeddog
This is a testing OS.  You may well have a need for the menu.  An easier solution is to have it come up all the time.

Run;
```

gksudo gedit /etc/default/grub

```
and edit that file to read like this;
```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true

```
The above starts at line 4 in mine.

This will give you the menu so you can choose the kernel or recovery mode when you need to.

If you want a longer time out so it stays up longer (or shorter) that is about 2 lines below the above.

---

### Post by xeddog on 2010-06-09
ranch hand - I made the changes as you described and it had no effect.  I still have to beat the livin crap outta my two shift keys during a reset.

xeddog

---

### Post by cariboo on 2010-06-09
Did you run:

```
sudo update-grub
```

after making the change?

---

### Post by ranch hand on 2010-06-09
> **cariboo907 said:**
> Did you run:

```
sudo update-grub
```after making the change?
I never put that in!  Senility and assuming too much is a bad combo.

Thanks for posting that.

---

### Post by cariboo on 2010-06-10
> I never put that in! Senility and assuming too much is a bad combo.

Thanks for posting that.

No problem, I do it once in a while myself. :)

---

### Post by xeddog on 2010-06-11
cariboo907 - well . . .uh . . .ya see . . .uh . . .no.  I guess that puts me in the same boat as ranch hand.  One of those "DUH!" moments.

Thanks,

xeddog

---

### Post by cariboo on 2010-06-11
> **xeddog said:**
> cariboo907 - well . . .uh . . .ya see . . .uh . . .no.  I guess that puts me in the same boat as ranch hand.  One of those "DUH!" moments.

Thanks,

xeddog

Your Welcome, we all have our moments. :)

---

### Post by ranch hand on 2010-06-12
> **Chauncellor said:**
> as for the shift holding problem, I believe it is a bug in grub2; I cannot access the menu that way, it just restarts the entire computer.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/425979](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/425979)
I have several installs so the menu comes up by default so I do not have that problem.

I have no idea how your box is set up but if you can get into your /etc/default/grub file and comment out the "GRUB_HIDDEN_TIMEOUT=0" line it will come up.

Thanks for the link to that bug.  I will have to try that out and see if I have the problem.

---

