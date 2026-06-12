---
title: "IWLAGN Firmware"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by Chickenhead on 2011-05-06
Hi Folks:

Does anyone know how to get the iwlagn driver to load the newer firmware?  I've got my system set up to grab the pre-release updates from upstream...the linux-firmware package has been updated a number of times now.  My laptop uses the iwlagn driver, which, according to the intellinuxwireless.org site, has been updated several times.  The latest version IS on my system, however, the iwlagn driver keeps loading the OLD version:

[1205882.622904] iwlagn 0000:02:00.0: Loaded firmware version: 8.24.2.12

How do I make the driver load the latest version?  The driver IS on my system under /lib/firmware/iwlwifi-5000-5.ucode.  However, this is not the version being loaded, which is under /lib/firmware/iwlwifi-5000-2.ucode.

---

### Post by chili555 on 2011-05-07
I have been handed latex gloves, eye protection and a plasma cutter; I am assumed to be the resident iwlagn mechanic. Usually the driver version relates to the specific hardware and grabs the firmware it needs and none other. I have never had experience through the forum, Google or personal, with trying to force another firmware version than the driver and hardware want. You will be our test case!

It's simple to rename the firmware you do *not* want:```
sudo mv /lib/firmware/iwlwifi-5000-2.ucode /lib/firmware/iwlwifi-5000-2.test
```Reboot and see if your wireless loads 5000-5.ucode and, most importantly, your wireless works. 

I think it won't, but I am open to being proven wrong!

---

### Post by Chickenhead on 2011-05-10
Hmm, well no dice.  I re-named it...I even tried moving it out of /lib/firmware.  dmesg still reports the same version number.

I do have this driver actually working at "kinda" Wireless-N speeds.  It does about 64M which I guess is better than Wireless-G.  And even more interesting is that it reports the same speed whether under Windows Vista or under Kubuntu.  Not sure what Intel is doing to this driver...

---

