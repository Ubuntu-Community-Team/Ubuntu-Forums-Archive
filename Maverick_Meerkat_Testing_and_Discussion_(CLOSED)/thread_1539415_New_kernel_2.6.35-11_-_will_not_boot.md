---
title: "New kernel 2.6.35-11 - will not boot"
date: 2010-07-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2010-07-26
Well, with today's new kernel update to 35-11, I can no longer boot Maverick. It just stays on the plymouth splash screen and after 30 seconds or so, all activity seems to stop. I attempted three times.

Any suggestions on how to get around this? Or, just do a full reinstallation from an iso?

Tim

---

### Post by xebian on 2010-07-26
> **ratcheer said:**
> Well, with today's new kernel update to 35-11, I can no longer boot. It just stays on the plymouth splash screen and after 30 seconds or so, all activity seems to stop. I attempted three times.

Any suggestions on how to get around this? Or, just do a full reinstallation from an iso?

Tim

Don't you have an older or known to work kernels?  Boot with them until a newer one comes along that will work for you.

---

### Post by ratcheer on 2010-07-26
> **xebian said:**
> Don't you have an older or known to work kernels?  Boot with them until a newer one comes along that will work for you.

Ok, I'll see if rev 10 will still come up. Sometimes, when I install a newer kernel, the previous one's video driver will no longer work.

Thanks,
Tim

---

### Post by paul_in_london on 2010-07-26
Working here, albeit without nvidia because I have xorg-edgers enabled. I don't think that'll change until we get a new nvidia driver.

Have you tried removing **quiet splash** from your boot stanza(s)?

Another thing to try is booting 2.6.35-11 into recovery mode and reinstalling your video driver.

---

### Post by xeizo on 2010-07-26
2.6.35-11 works just fine here with Nvidia 256.35, but I don't use Plymouth which is the probable explanation. As someone said above, edit your boot-parameters to remove splash!  Also, you must have linux-kernel-headers-2.6.35-11-generic installed to get the Nvidia driver to compile correctly, otherwise it will not be installed at all on your new kernel.

---

### Post by cariboo on 2010-07-26
I just installed 11 on my netbook with Intel chipset, it booted just fine, and I am typing this on my netbook.

---

### Post by ratcheer on 2010-07-26
> **xeizo said:**
> 2.6.35-11 works just fine here with Nvidia 256.35, but I don't use Plymouth which is the probable explanation. As someone said above, edit your boot-parameters to remove splash!  Also, you must have linux-kernel-headers-2.6.35-11-generic installed to get the Nvidia driver to compile correctly, otherwise it will not be installed at all on your new kernel.

I am sure the 35-11 headers were installed along with the kernel. It was a total of three packages (not including the other software that was updated today, too).

Tim

---

### Post by mc4man on 2010-07-26
nevermind

Edit: as I was typing the final 2 packages became available - 5 in total

---

### Post by ratcheer on 2010-07-26
> **ratcheer said:**
> Ok, I'll see if rev 10 will still come up. Sometimes, when I install a newer kernel, the previous one's video driver will no longer work.

Thanks,
Tim

Ok, I purged the rev 11 kernel and the rev 10 kernel is running just fine. I guess I'll wait for rev 12 before I update, again.

Thanks,
Tim

---

### Post by ve3tru on 2010-07-26
I get all new errors with the new kernal but eventually it boots up fine. Things like you have to go into low graphics mode (not true), screwed up splash, but..I know they will sort it out.
All you need is a little faith.

---

### Post by clhsharky on 2010-07-26
.35-11 would only boot in safe mode here, ATI OSS.
.35-6 would not boot after update, this was on fresh install, I only waited a couple minutes.
.35rc6 booted fine, will wait for next kernel update to go back.

Sharky

---

### Post by sgage on 2010-07-26
Just another data point:

-11 is working fine here, with the nvidia drivers. Stock install, plymouth and all, all updated. No change in any behaviors from -10 that I can detect.

---

### Post by andrewthomas on 2010-07-26
> **clhsharky said:**
> .35-11 would only boot in safe mode here, ATI OSS.
.35-6 would not boot after update, this was on fresh install, I only waited a couple minutes.
.35rc6 booted fine, will wait for next kernel update to go back.

Sharky
I was having a similar problem ( using ATI OSS-xorg-edgers.)  Gnome-panel would freeze up when I had compiz enabled.  The problem turned out to be mesa 7.9.0+git20100725, once I updated to 7.9.0+git20100726 I was able to boot normally

---

### Post by ratcheer on 2010-07-28
Ok, 2.6.35-12 is running fine on my system. I have no idea what happened with rev 11. I did nothing special to install rev 12, but it works and 11 did not.

Tim

---

### Post by clhsharky on 2010-07-28
> Ok, 2.6.35-12 is running fine on my system. I have no idea what happened with rev 11. I did nothing special to install rev 12, but it works and 11 did not.
Same here.

Except my sound is now muted at startup with todays updated, go figure.

Sharky

---

### Post by VMC on 2010-07-28
> **clhsharky said:**
> Same here.

Except my sound is now muted at startup with todays updated, go figure.

Sharky

Have you checked out this [fix]("http://ubuntuforums.org/showpost.php?p=9349048&postcount=10") for muted sound on Maverick?

---

### Post by clhsharky on 2010-07-28
VMC

Thanks 
Yes it worked.
I've fixed the sound before on my last M&M.
This is a fresh install and was working fine till todays updates, I thought it might have been fixed, Wrong.

Sharky

---

