---
title: "Macbook Pro 8,3 Single Boot 13.04 - Enable BCM4331 out of box"
date: 2013-05-01
forum: Networking &amp; Wireless
---

### Post by pacpod on 2013-05-01
I can't guarantee it will work for everyone but it worked for me and I thought I would share. 

Keep in mind, this is only tested for a single boot of 13.04, not a dual boot with mac. Also, I only found it to work through the daily build of 13.04 on DVD and not USB. This came about by several different install combos, tinkering,  etc to get Ubuntu to install, much less get the wifi working. Also, keep in mind I'm a super beginner at Linux so if this is well known, please disregard. ;)

1. Boot into a mac rescue USB drive (I used Mountain Lion) to use the disk utility to partition the drive into a single portion (pick something, it seemed to work _as long as I didn't pick free space for some reason_)

2. Insert the daily build AMD64 iso DVD of Ringtail and boot into the live disk.

3. Once booted, just follow the prompts and enable the BCM drivers when it prompts to get updates while installing. 

4. When you get to the window that asks how you want to divvy out the hard drive, choose "something else". I gave 2x RAM to SWAP (16 GB in my case - gratuitous, I know hehe), made a bios partition, and the remainder was set as ext4.

Once the install was finished, the BCM drivers enabled without any problem through the "Additional Drivers" Tab of "Software & Updates" in System Settings. Up until I followed this path, they would enable no problem when using the live CD but would always fail to enable once the install was finished. I tried all the other fixes with downloading the drivers with another computer since my Ethernet was on the fritz too but had no luck with them.

So I know this sounds simple, but this was the only combo of steps that worked to get everything going on my machine. I hope it is able to benefit someone.

---

