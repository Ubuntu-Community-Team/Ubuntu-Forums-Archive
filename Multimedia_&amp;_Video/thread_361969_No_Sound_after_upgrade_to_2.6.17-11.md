---
title: "No Sound after upgrade to 2.6.17-11"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by Denis novice on 2007-02-15
No output sound, recording is low level.  Tested using an old Kubuntu live CD, so hardware is working.  Followed suggestions in forum; no change.

In alsamixer all controls and switches are high/on.  I hear a "clunk" when the Analog-digital switch is cycled, but that is the only sound I can get.

Using audigy-2 card. Kubuntu edgy.

I would appreciate any help you can offer.

Thanks,
-Denis

---

### Post by renzokuken on 2007-02-15
have you tried compiling the latest alsa-driver? that solved my sound issues. it has better support for some newer cards/chipsets.

---

### Post by Denis novice on 2007-02-15
> **renzokuken said:**
> have you tried compiling the latest alsa-driver? that solved my sound issues. it has better support for some newer cards/chipsets.

No, I have not.  I use only packages.  But since sound was working fine before I upgraded the kernel from 2.6.17-10 to 2.6.17-11, I think it is very unlikely that it is a driver/card-support issue.

There is a slight chance that it was not the kernel upgrade but another package upgrade which broke the sound.  Around the time of the kernel upgrade, there were other minor package updates downloaded, so one of those could be the cause, at least in theory.

-Denis

---

### Post by Denis novice on 2007-02-15
> **Denis novice said:**
> No, I have not.  I use only packages.  But since sound was working fine before I upgraded the kernel from 2.6.17-10 to 2.6.17-11, I think it is very unlikely that it is a driver/card-support issue.

There is a slight chance that it was not the kernel upgrade but another package upgrade which broke the sound.  Around the time of the kernel upgrade, there were other minor package updates downloaded, so one of those could be the cause, at least in theory.

-Denis

I see this note:

ATTENTION:

Due to an unavoidable ABI change the Ubuntu 6.06 and Ubuntu
6.10 kernel updates have been given a new version number, which
requires you to recompile and reinstall all third party kernel modules
you might have installed. If you use linux-restricted-modules, you
have to update that package as well to get modules which work with the
new kernel version. Unless you manually uninstalled the standard
kernel metapackages (linux-386, linux-powerpc, linux-amd64-generic), a
standard system upgrade will automatically perform this as well.

Is emu10k1 a third party or a linux-restricted-module? 

In the last phrase "...a standard system upgrade will automatically perform this as well." , does "perform this" mean perform the kernel update or perform the package update?

What does ABI stand for?

Thanks for any clarification.

-Denis

---

### Post by Denis novice on 2007-02-16
> **Denis novice said:**
> I see this note:

ATTENTION:

Due to an unavoidable ABI change the Ubuntu 6.06 and Ubuntu
6.10 kernel updates have been given a new version number, which
requires you to recompile and reinstall all third party kernel modules
you might have installed. If you use linux-restricted-modules, you
have to update that package as well to get modules which work with the
new kernel version. Unless you manually uninstalled the standard
kernel metapackages (linux-386, linux-powerpc, linux-amd64-generic), a
standard system upgrade will automatically perform this as well.

Is emu10k1 a third party or a linux-restricted-module? 

In the last phrase "...a standard system upgrade will automatically perform this as well." , does "perform this" mean perform the kernel update or perform the package update?

What does ABI stand for?

Thanks for any clarification.

-Denis

Well I found the answers to the above. And I got the sound to work.  I feel a bit foolish, since the problem was in the mixer settings (they make no sense to me).

thanks for all the help.

---

### Post by eholcroft on 2007-02-18
Denis

I have the same problem you describe but all the mixer settings seem fine. Would you like to share your solution with us?

ed

---

### Post by DarkW0lf on 2007-03-03
For me, after the update and reconfiguring X.
I found that all the volume levels in the mixer were set low.
I had to open up the Vloume Control and set everything back.

I thought I had a more seriuos problem til I read Denis' post about mixers and thought to check the Volume Control.

---

### Post by floke on 2007-03-03
You could try this...

[http://ubuntuforums.org/showthread.php?t=365071](http://ubuntuforums.org/showthread.php?t=365071)

No idea if it works though. I had the same problem, but am now using Feisty, which works fine.

---

