---
title: "Seahorse, Ubuntu 9.10 wireless not connecting to WPA"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by mikey.duhhh on 2009-12-08
A few days ago I installed Ubuntu 9.10 on a friend's laptop.  He has a 4306 Broadcom wireless card. And having had a laptop with a bcm4312 card I knew there would be an issue with the wireless. 

So, I searched the forums and found the b43legacy/b43 tar, downloaded it, placed the unzipped folders in **/lib/firmware** and rebooted.  Well, at least it was trying to connect now.  But Seahorse wanted a password for me to use the wireless, so I gave it one.  Then, of course so did the WPA wireless spot I was in.  Still no connect. 

So, I found a lan, plugged the laptop in and downloaded all 147 updates for 9.10.   Rebooted, Wow! It connected no problem to the **open** wireless network available to me.  I called my friend and told him it was now working.  Then I drove all the way across the metro area back to the coffee shop and tried to boot up.  First Seahorse wanted a password again,  then the WPA encrypted hot spot wanted it's password, too.   Trying, trying, trying....   Up comes the box for the password again, trying, trying, trying....  Password box reappears.  Etc., etc., and so on.   I won't connect to a WPA connect.


First, off.  I have never seen this behavior from Seahorse before.  Before 9.10  it never bothered me for any sort of prompt unless I PGP'd email.  So what is going on with Seahorse demanding a password to use wireless?   Anyone?  Can I just remove Seahorse without destroying access to Ubuntu?  You know, sudo apt-get purge seahorse?

Could that fix the wireless connect WPA problem?  Or do I need to go back to 9.04?

---

