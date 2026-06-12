---
title: "i need help finding wireless files!"
date: 2011-09-18
forum: Networking &amp; Wireless
---

### Post by slixz85 on 2011-09-18
hi i have a 1 hard drive system split into a few partitions. i have peppermint ice on it working with wireless but now it is not working the system crashed. i have ubuntu installed but it is the old 9.10 version and the wireless doesn't work on it. this is what i am needing is to find the files from the peppermint ice folders that are for the wireless to get ubuntu 9.10 to work since peppermint is a ubuntu derivative. i would just download a new iso but i cant because i only have wifi and cant get on it since ubuntu 9.10 don't have it working.

also i believe i need to be logged into root on ubuntu 9.10 to be able to copy and paste the files into the folders since i dont know how to do it from terminal and it tells me permission denied, however i dont know the password it is not root only the login is.

i don't have a usb flash drive anymore it broke and also not a cd burner, so this is the only way i can think of is finding the wireless files in my peppermint filesystem since the wireless worked.

GREATLY APPRECIATED TO ANY HELP!

i know that 9.10 is unsupported by ubuntuforums personnel now so community peoples please help.

---

### Post by think13 on 2011-09-18
> **slixz85 said:**
> hi i have a 1 hard drive system split into a few partitions. i have peppermint ice on it working with wireless but now it is not working the system crashed. i have ubuntu installed but it is the old 9.10 version and the wireless doesn't work on it. this is what i am needing is to find the files from the peppermint ice folders that are for the wireless to get ubuntu 9.10 to work since peppermint is a ubuntu derivative. i would just download a new iso but i cant because i only have wifi and cant get on it since ubuntu 9.10 don't have it working.

also i believe i need to be logged into root on ubuntu 9.10 to be able to copy and paste the files into the folders since i dont know how to do it from terminal and it tells me permission denied, however i dont know the password it is not root only the login is.

i don't have a usb flash drive anymore it broke and also not a cd burner, so this is the only way i can think of is finding the wireless files in my peppermint filesystem since the wireless worked.

GREATLY APPRECIATED TO ANY HELP!

i know that 9.10 is unsupported by ubuntuforums personnel now so community peoples please help.

I can't help with everything, but here's what I can think of for your situation.

The best solution IMO would be to find a friend with a working Internet connection and blank CD-Rs (or you can buy them for very cheap) to burn a newer version of Ubuntu. Or if you have a friend who uses Linux or a Linux User Group in the area, they would probably have access to a CD. Or, you can buy them straight from Canonical (but only in packs of 5 or more: [http://shop.canonical.com/index.php?cPath=17](http://shop.canonical.com/index.php?cPath=17))

If you have physical access to the router, you should be able to plug in an ethernet cable into the back to get internet. Or if you have physical access to the modem, you can unplug the router and plug an ethernet cable straight from the laptop to the modem.

As for looking for the files on your peppermint partition, some of the cached package files are in /var/cache/apt/archives. It's a long shot, but maybe the required package will be in there. I would strongly discourage trying to just copy files to get it to work. It will most likely not work and you will mess up the package management system.

For moving the files, the root password should be the same one for your account that you set up when you installed Ubuntu. To move files, you can run "gksudo nautilus" from the command line.

Hope that helped.

---

