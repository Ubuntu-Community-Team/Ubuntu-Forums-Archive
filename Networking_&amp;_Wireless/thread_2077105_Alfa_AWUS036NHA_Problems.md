---
title: "Alfa AWUS036NHA Problems"
date: 2012-10-27
forum: Networking &amp; Wireless
---

### Post by akashi on 2012-10-27
[Previous thread]("http://ubuntuforums.org/showthread.php?t=2071129&highlight=awus036h")

First, I had problems with the AWUS036H as it was painfully slow. I later brought the newer AWUS036NHA which seemed like working perfectly. However, problems have started again!

If this device is connected to the computer whilst booting up, the boot process freezes. Removing the device resumes the boot-up.

Websites are taking a long time to load. I compared the speed with my laptop's built-in "**Intel® Centrino® Wireless-N 2230**"

The [COLOR="Red"]**[COLOR="RoyalBlue"]AWUS036NHA[/COLOR]**[/COLOR] connects at **135Mbps**
Download: **0.26Mbps**
Upload: **0.12Mbps**

The **[COLOR="RoyalBlue"]Centrino Wireless-N 2230[/COLOR]** connects at **26Mbps**
Download: **6.54Mbps**
Upload: **1.38Mbps**

I have attached screenshots from Windows 7 x64 and the problem is exactly the same in Ubuntu.

I am wondering if I am just having bad luck with Alfa products or can someone recommend me a long range card that can provide good throughput speed.

Thanks in advance.

---

### Post by TobiMensch on 2013-02-14
Hi there, i know its been a while since you've posted here, but i've kinda found a workaround over on the Backtrack-Forums.

I've had exactly the same Problem as you with my AWUS036H!
It regularly had slow speeds under Ubuntu-Linux as it also did with Backtrack 5R3!
It worked kinda fine under Windows 7 x64 though..

Had the same Intel Centrino WIreless N2230, and therefore thinking that it might have something to do with Driver-Issues between the both, but anyways to the solution i've found!

You've simply have to set down the RATE-Value of the wifi device like so:

> 

Before connecting to a Wifi-Network type the following into the Terminal

**sudo iwconfig wlan* rate 1M**

(replace * by the appropriate Number)

After that i could achieve Download-Speeds of about ~590kb/s which should be about the speed you'd get with 6Mbit-DSL.
Not sure if its maxed out though, as there's quite some distance between the Wifi-Adapter and the Router approximately 50-60Meters (65yards) with some walls and stuff in between.

This might be also working for your Alfa AWUS036NHA, check it out if you still didnt fix it.
Otherwise my post might also be helpful for other users having the same issues as i did, and ive spend hours searching for the solution!


BTW. how is the overall Reception of the AWUS036NHA compared to the AWUS036H?
If it would be as comparable  to the old "H" i've would eventually considering buying that one as it has N-Connectivity!


Hope i'd might be helpful for one or another!
Have a nice Day!

---

