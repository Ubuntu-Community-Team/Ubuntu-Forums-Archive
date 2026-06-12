---
title: "Locked Bios settings after installing distro"
date: 2020-03-31
forum: MINT
---

### Post by nerazim1 on 2020-03-31
After installing a Linux distro(mint 19.3)(yes I know I am in the Ubuntu forum, I'll get to that later) it locked my bios settings - it couldn't boot because it was missing files( I can't change anything, neither restore to default settings, also relocked my secure boot) - picture : 

[https://ibb.co/xfkqZrQ](https://ibb.co/xfkqZrQ)
[https://ibb.co/NtfpCwq](https://ibb.co/NtfpCwq)
(Majority of options are grey, cannot access them)

I managed to install a version of Windows and get it boot(after removing the HDD and plugging it while the windows setup was loading, from there I managed to access an Ubuntu live installation usb key using advanced system restart option in windows(the mint one won't boot and neither Manjaro this way, only Ubuntu - secure boot related). Then I installed Ubuntu alongside Windows, now only windows boots. For unlocking the bios settings I also tried( while booting from a live usb without HDD attached) :
Resetting the CMOS manually - the motherboard has no jumpers, unplugging the battery doesn't work(left it off for 8 hours, it only reset the clock but not other settings
Deleting the EFI partition - using gparted from Ubuntu - didn't work and I had to reinstall windows again
Trying sudo modprobe nvram from Ubuntu terminal, commands return no error but it didn't do anything.

The "EFI file boot 0 :yes" In the second picture is the mint installation that locked my bios settings and then didn't boot, I managed to change boot order from Ubuntu using efibootmgr
I also deleted the "yes" boot entry but it keeps coming back....

Now the laptop only boots windows...is there any way I can unlock the BIOS settings?
Laptop is an Acer es1-531-p7n0

---

### Post by jeremy31 on 2020-03-31
Moved to proper subforum

---

### Post by oldfred on 2020-03-31
You show UEFI password is set.
You have to put your password in, to open all the settings including setting "trust" on any boot option other than default Windows.

Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator)
Acer Travelmate B117 (success - after some UEFI boot troubles) Trust related
[https://forum.siduction.org/index.php?topic=6272.0](https://forum.siduction.org/index.php?topic=6272.0)

Many Acer also need UEFI update.
Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

Acer ES1-331 laptops Strange differences at new installations
[https://ubuntuforums.org/showthread.php?t=2362511](https://ubuntuforums.org/showthread.php?t=2362511)
Boot Parameter required
[http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10](http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10)

Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)

---

