---
title: "Can't connect to Yahoo or Hulu.com?"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by justinram22 on 2011-04-01
I seem to be having a very strange problem.  I have 5 computers, 3 of them have windows XP Pro, 1 has Ubuntu 10.04, and the other has Windows 7 Ult.

On all the machines except the windows 7 machine whenever I attempt to go to yahoo.com it says "waiting for l.yimg.com" and after awhile will load without any CSS at all.  When the same machines (all except for the Windows 7 one) attempt to go to Hulu.com it can connect to the website just fine, but whenever it attempt to play a video, the ad will not play, and hulu is designed to not play the video if the ad does not play.  I do not have any ad blocking addons installed at all.  This occurs on both chrome and firefox.  And lastly the oddest problem out of them all I think is that on the same machines I can play youtube videos fine, but if i log into an account, it will not play the video.... it just shows a "spinning wheel of death."

I can also ping [www.yimg.com](www.yimg.com) with no package loss...

On all of the machines I have reinstalled the browser and updated to the newest flash player.  On one of the windows XP machines I even tried a system restore too 2 months ago, but that did not work.

This all started 2 days ago, all at the same time.  I would say that it is my ISP's fault or my routers, but that wouldn't make sense since my Windows 7 machine can connect fine to all the websites.

Thank you guys soooo much for any help!!
I've been tearing my hair out over this for 2 days and have made no progress.

---

### Post by Ron F. on 2011-04-06
I have the same problem, and was not able to figure it out, and have since given up. The hangup appeared to occur when downloading content from yimg.com, making it impossible to load yahoo.com. 

My findings:
This problem is occurring on my two Ubuntu machines that are behind a Cisco router (IAD2400 series,) provided by CBeyond. One is running 10.04 32-bit, the other 10.04 64-bit. This occurs in every browser I tried: FF 3.6, FF 4, Chrome 12, Opera, Midori, and FF 4 for Windows running with WINE installed.

DNS lookup works fine, and I can ping yimg.com, with no problem. I can also download individual images if I use a direct URL into yimg.com/..., but loading the yahoo front page stalls out. I tried turning on the iptables firewall in Ubuntu, turning it off, etc... no difference.

It appeared in Wireshark, that requests to yimg did not get responses. It made no sense.

If I switch my Ubuntu machine to another network (I attached a 3G wireless USB modem,) then everything worked fine - of course. So, the obvious culprit is the router, but we turned off everything - no filtering at all. It is only running NAT and DHCP, but no dice. The browser waits forever on yimg.com again.

Other tests conducted:
I tested a Windows XP SP2 machine behind this router, and got exactly the same problem! A Windows XP SP3 machine was tested, but with no further updates downloaded from MS, exhibited extreme slowness when loading yahoo.com into Firefox or IE, but it did eventually load. Next, installing all updates to the Windows XP SP3 machine eliminated the problem completely. Windows 7 machines do not exhibit this problem at all, and work fine.

At that point, I gave up. I am behind a company firewall, and cannot change out the router to suite my taste. I am the only Linux user here, and the only person now with this problem.

So I ask, what problem did M$ apparently solve years ago, that Linux has yet to address in the IP stack?

-Ron

---

### Post by Ron F. on 2011-04-08
Problem Solved!

It is an MTU problem. It may be that if TCP MTU probing is running, the problem would not occur, Regardless, I found that on my Ubuntu 10.04 machines, the mtu for my eth0 interface was set to 1500. This worked much of the time, but apparently the Cisco router I am behind has a problem with that for some websites, such as yahoo.com.

I set mtu to 1492, using the command: **sudo ifconfig eth0 mtu 1492**, and instantly the problem was gone. I also found that adjusting the mtu value in similar fashion on a Windows XP machine that had been exhibiting the same problem fixed it there as well.

This setting can be made permanent, see: [http://superuser.com/questions/213264/cant-access-select-websites-on-linux-but-can-on-windows](http://superuser.com/questions/213264/cant-access-select-websites-on-linux-but-can-on-windows)

These kind of things seem so obvious after they have been cleared up.

-Ron

---

### Post by justinram22 on 2011-04-09
> **Ron F. said:**
> Problem Solved!

It is an MTU problem. It may be that if TCP MTU probing is running, the problem would not occur, Regardless, I found that on my Ubuntu 10.04 machines, the mtu for my eth0 interface was set to 1500. This worked much of the time, but apparently the Cisco router I am behind has a problem with that for some websites, such as yahoo.com.

I set mtu to 1492, using the command: **sudo ifconfig eth0 mtu 1492**, and instantly the problem was gone. I also found that adjusting the mtu value in similar fashion on a Windows XP machine that had been exhibiting the same problem fixed it there as well.

This setting can be made permanent, see: [http://superuser.com/questions/213264/cant-access-select-websites-on-linux-but-can-on-windows](http://superuser.com/questions/213264/cant-access-select-websites-on-linux-but-can-on-windows)

These kind of things seem so obvious after they have been cleared up.

-Ron

THANK YOU!!!!!!! My god words cannot express the gratitude that I am feeling towards you!!! I never would have found that out on my own, thank you thank you thank you! (My family also thanks you very much!)

---

