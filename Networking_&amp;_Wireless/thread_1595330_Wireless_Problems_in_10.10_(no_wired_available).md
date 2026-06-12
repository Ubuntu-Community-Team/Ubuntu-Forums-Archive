---
title: "Wireless Problems in 10.10 (no wired available)"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by -Morgoth- on 2010-10-13
For reasons unknown to me my wireless seems to be gone. Fresh install of 10.10 64bit on an acer aspire 5740g laptop. I can't find anything saying wireless when I click on the network icon in the notification area and only wired is shown there. I know that connecting it to the wired first usually helps, but I don't have that opportunity :/
No drivers are listed in the restricted drivers list since I've no internet connection. I don't have the exact name on the wireless card, but its a broadcom.

Any solutions to this problem is much appreciated since I really can't do anything without internet.

---

### Post by johnnytm on 2010-10-13
You are going to have to find a way to download the broadcom sta driver. It is not included in Ubuntu because it is a propietary driver. The easiest way would  be to find somewhere you can connect to wired connection and use system-->administration-->additional drivers to enable the broadcom sta driver. If you can't do that the only option is to find a way to download the driver from broadcom's site copy it to a flash drive or something and build/install the package on your Ubuntu machine.

---

### Post by -Morgoth- on 2010-10-13
I kinda did that but nothing really happened when I ran the .tar.gz file

---

### Post by kkobashi on 2010-10-13
Same problem going on here. Using Linksys WMP300N on 64-bit Ubuntu 10.10. Had problems first attempting download new Broadcom STA wireless driver.
Download apparently worked on the second attempt. First attempt came back with some sort of archive error. Been getting a lot of those on this release.

After activating the Broadcom driver, my wireless network doesnt appear in the top bar like it used to.

---

### Post by johnnytm on 2010-10-13
u have to build tar files they are not normally self installing. You have to build the driver package and then install it. This link [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt) will give u directions on how to do that for whatever version of the tar file you have.

---

