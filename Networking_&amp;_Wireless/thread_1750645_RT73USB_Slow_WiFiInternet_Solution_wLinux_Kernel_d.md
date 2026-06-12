---
title: "RT73USB Slow WiFi/Internet Solution w/Linux Kernel downgrade"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by Utew on 2011-05-05
Hi All.. After hours of scouring the Net and the Forums here, I have finally solved my intermittent/slow WiFi connection issues by downgrading the kernel to a previous version. 

Though I am still testing for stability issues, so far I have found none with my install of 64bit Linux Mint 10 (based on Ubuntu 10.10 Maverick). 

Having not been able to live with the slow quirky wireless issues I was suffering, I un-installed 11.04 Natty and switched to Linux Mint 10 instead, hoping to see some improvement. Sadly, I had the same connection issues... slow, then the speed would increase, then drop to nothing.. rinse and repeat. Extremely frustrating to say the least.. as so many here have had wireless connection issues. I though that by posting my results, I might help at least one person.

System: HP 9250f Quad Core Intel.. the built in wireless solution is a Ralink chip (2571w) usb WiFi module. which doesn't seem to be well supported though it does connect and transfer data both under 11.04 Natty and 10.10 Maverick, using the RT73USB driver 

Reading that someone else had only started having issues after an upgrade from 10.04 Lucid to 10.10 Maverick, I tried playing around with several kernel versions. 

The latest kernel, released today 2.6.39-rc6 ( which I had hopes for) had no affect on my wireless connection/speed. However downgrading to linux kernel 2.6.32-02063209-generic and suddenly bingo! Speeds back to what my Win7 install provides. Happy Day!!!

Ok, what's the downside? None for me, so far.... but YMMV... and 11.04 Natty might need the newer kernel that is stock to work without issues... but I doubt it. I may re-install Natty and downgrade the kernel soon myself. But for now.. all is welll and this might be a solution for (some) of you having issues.. as earlier kernels (pre- 10.10 Maverick) seem to include the wireless drivers needed (at least in my case). Obviously they have been removed from more current kernels for reasons unknown.

Sorry for the VERY long post, but this has been akin to the search for the Holy Grail. ;)

Ubuntu Mainline Kernel Repository is here [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

Again, my solution came from installing the 2.6.32 Lucid kernel from June 11, 2010.

AS a disclaimer, update your kernel at your own risk.. and read up on how to, if you should attempt to do so.

Cheers, Utew


*Just an Update.. after several hours of testing... I am having _zero_ WiFi issues, since I changed kernels. Also, no glitches in system operation/efficiency/stability. I just hope a future kernel release solves a majority of the wireless issues, that a lot of us have been having. It's hard for me to see more recent kernels as an improvement, at least in the arena of wireless functionality. *

---

