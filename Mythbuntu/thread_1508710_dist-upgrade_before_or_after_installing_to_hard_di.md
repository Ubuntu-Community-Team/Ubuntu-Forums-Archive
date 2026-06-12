---
title: "dist-upgrade before or after installing to hard disk?"
date: 2010-06-13
forum: Mythbuntu
---

### Post by brianafischer on 2010-06-13
I am doing a "clean install" of MythBuntu 10.04 to my system.  What is the intended installation procedure by the MythBuntu developers?


1. Boot into live environment, install to hard disk, then dist-upgrade

2. Boot into live environment, dist-upgrade, then install to hard disk

My guess is that #1 is the preferred method, or else they would have added a dist-upgrade in the installation process.  Any opinions?

Thanks!

---

### Post by ankit singh on 2010-06-13
2nd method does not exist "i think". In live-environment entire system is loaded in ram(hard disk is not touched at all except data files).few question arrive here is:
1)After u upgrade ur disk, the system will ask for reboot as it is necessary because a lot of files changes had taken place,but after rebooting where will be the upgraded OS with us?
2)What will happen to those users who have less ram?

No 2nd method does not exist.

---

### Post by ankit singh on 2010-06-13
But i think the 2nd method can be applicable for usb-hdd.However method 1# is always recommended

---

### Post by brianafischer on 2010-06-14
> **ankit singh said:**
> 2nd method does not exist "i think". In live-environment entire system is loaded in ram(hard disk is not touched at all except data files).few question arrive here is:
1)After u upgrade ur disk, the system will ask for reboot as it is necessary because a lot of files changes had taken place,but after rebooting where will be the upgraded OS with us?
2)What will happen to those users who have less ram?

No 2nd method does not exist.
Your repsonse brings up another question.  The procedures I have listed above are not including a reboot to apply the dist-upgrade items that require such.

My assumption would be that all dist-upgrade files would be written to the RAM disk and used upon the "install to hard disk" option.  Due to this, the install files may be different than what the original developer (and users up to this date) used during the install process and could lead to new bugs.

I went the safe route and did the dist-upgrade after the "install to hard disk" and reboot into the actual mythbuntu installation.

I am still interested to hear opinions on this.

---

### Post by DougieFresh4U on 2010-06-14
> **brianafischer said:**
> 

2. Boot into live environment, dist-upgrade, then install to hard disk


I don't think that's gonna happen.
Puppy Linux has the ability to 'save changes to cd' upon shut down if you choose to when asked. Nice feature.

---

### Post by brianafischer on 2010-06-14
> **DougieFresh4U said:**
> I don't think that's gonna happen.
Puppy Linux has the ability to 'save changes to cd' upon shut down if you choose to when asked. Nice feature.

Aren't the contents of the dist-upgrade written to the RAM disk?

So if a dist-upgrade is done (without rebooting) and then "install to hard disk" option, the files recently obtained from the dist-upgrade will not be installed to the hard disk (as if you never ran the dist-upgrade command)?

My understanding was the current contents of the RAM disk were written to the hard drive upon the "install to hard disk" option.

---

