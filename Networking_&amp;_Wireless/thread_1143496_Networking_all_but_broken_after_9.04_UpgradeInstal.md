---
title: "Networking all but broken after 9.04 Upgrade/Install"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by linuxdave1 on 2009-04-30
After upgrading from 8.10 to 9.04 all LAN access and all incoming requests to ubuntu machine fail.

I use a D-Link DWA-542 Wireless N adapter (no cable connected to eth0). Wireless was a bit iffy with 8.10 in so much as that large data xfers would time out, and the connection wouldn't always come up the first try, but at least I could run services like Apache, SSH, VSFTPD, Postfix, and the like and access them from the outside world with 8.10, and I could also create shares on 8.10 and access them from my Windows machines, and vice-versa, but after upgrading to 9.04 I can't even browse the network, nor can I get to my Ubuntu machine from the outside world via http, ftp, etc.

So I tried wiping everything and going with a fresh install and the exact same problem.

What did you change Ubuntu? :confused: Please change it back!

---

### Post by jrz on 2009-04-30
Same problem here. After 3 fresh installs I still can't get networking to work reliably, and the Network Manager appears to be a problem, not a solution to setting up  the network.
Hopefully someone will read this post and direct me to some instructions on how to properly set up networking from a terminal. I've googled and asked questions on IRC to no avail. Luckily I still have another system running on 8.10 or I would be totally isolated from the Internet and the world considering where I live - 2 clicks from Laos.

Any help would be greatly appreciated.

---

### Post by linuxdave1 on 2009-04-30
I'm giving Ubuntu about 2 days to come out with a hotfix for this (based on the huge number of posts in this forum all saying pretty much the same thing), and then I'll either revert back to 8.10 or go with Fedora.

Hurry up guys! :P

---

### Post by t0mppa on 2009-04-30
> **jrz said:**
> Hopefully someone will read this post and direct me to some instructions on how to properly set up networking from a terminal.

Well, chances are you tried this as well, but in case you didn't, [take a look]("http://ubuntuforums.org/showthread.php?t=571188").

---

### Post by linuxdave1 on 2009-04-30
That's not exactly my problem. My wirless adapter connects just fine (usually), and I can browse the web, FTP, etc, but I can't see my LAN from 9.04, nor can I see my shares in 9.04 from Windows.

Also, no incoming requests work such as HTTP, FTP, SSH, and so on, so this isn't about getting the wireless adapter working, it's more about fixing whatever they broke (probably some "security" enhancement) in 9.04 because I could do all of this in 8.10 even if large data xfers would routinely time out.

But that's a great thread t0mppa.

---

### Post by jrz on 2009-04-30
I'll give your link a try as it has a few additional things I haven't seen before.
It appears things get worse as I now find files containing entries that didn't exist previously and have no idea what they are. Also I notice my router displays the computer connected with it's static IP address showing, and I can ping my router, but when I ping anything on the Internet I obviously access my ISP's DNS server as the ping displays the IP address of the site I am pinging, but returns:
From 169.254.4.215 icmp_seq={n} Destination Host Unreachable
The From does not match the IP of the site I am pinging, and searching the content of my systems files I found /var/lib/avahi-autoipd contains what appears to be files named with the MAC address of my wired and wireless hardware which contains only their assigned static IP, but there is also an additional file which looks like a MAC address that contains 169.254.4.215 (the IP returned by the ping). Ifconfig now also has some additional entries which I had not seen when first starting, eth1:avahi and pan0:avahi, both of which have 169.254.xxx.xxx IP addresses.
I installed 9.04 from an alternate CD, using ext4 FS, but am now downloading the desktop CD, and will reinstall again and use ext3 this time too as I'm beginning to lose confidence in any changes from 8.10 having been tested thoroughly enough to be trusted.
Personally I think 2 distribution upgrades per year is creating an accumulation of unsolved problems which may begin to drive away possible new converts to Ubuntu. I think more emphasis should be placed on making the installation more troublefree and a working network should be very near if not at the top of priorities. I have 3 other systems I would like to upgrade, but they are much newer and I'm almost certain I will have hardware support problems with them so I am working on my most generic system first, an old IBM Thinkpad R40.

Thanks for the help. I'll try and return later and post the results.

---

### Post by jrz on 2009-05-01
After 5 clean installs of 9.04, verifying the CD's, both alternate and desktop, checking the computers RAM memory, and following the instructions you provided, I was still unable to get the wired or wireless connection to work. As a last resort I have installed 8.10 and now have a working wired connection, and will try and see if I can also get the wireless working on that and then apply the nearly 300MB's of updates before trying to upgrade from 8.10 to 9.04 via the Internet. All in all I'm not too pleased with 9.04 and hope 9.10 will be more thoroughly tested before it becomes final.
Thanks for your help.

---

### Post by t0mppa on 2009-05-01
If you got everything working on 8.10, is there really any reason to update to 9.04? I mean, what does it really offer that's worth the trouble?
[LIST]
[*]Lots of look and feel changes? They're nice, but hardly crucial and there are tons of free themes online anyway.
[*]A few seconds quicker boot time? Unless you boot your system dozens of times per day, it's not going to save you that much time.
[*]Supposedly better hardware support? If your system works on earlier versions, this is irrelevant.
[/LIST]
I was thinking about downgrading to 8.10 myself, since the new ATI driver's 3D acceleration is not on par with that of 8.10. But I ended up postponing that project for a while to see if some fixes emerge, since I only need 2D to do my work.

Note: just asking, since I'm curious if there's really something useful in 9.04. :)

---

### Post by jrz on 2009-05-01
It's not so much for the OS changes as it is for the updates to addons, Firefox, Open Office, etc. Currently I have one system still on 7.04, and three on 8.10, and will try moving one of them to 9.04 shortly. Network Manager was a problem in 8.10 also but much worse in 9.04. After removing it an installing Wicd, I was able to quickly access both the wired and the wireless network, and would like to see how it will perform under 9.04. If Wicd works as well with 9.04 I will put it on all my systems now and in the future. There are so many programs that require the latest OS to make them easy to update from Synaptic, and even then they lag behind a little.
Boot times and OS look and feel don't mean much to me.

---

### Post by t0mppa on 2009-05-01
Allright, thanks for clearing that up. And best of luck with your issue, hope you get it working.

---

### Post by sfled on 2009-05-01
I don't know if this will work in your situation, but back when I installed Ubuntu 6 (Dell Inspiron 4100, D-Link DWL-650 Air V.M1 RTL8180 Realtex chipset), it found the WEP network and connected after I gave it the password.
   After upgrading to 7 then 8.10 the wireless stopped working. Didn't even get a power light on the Air card.
   The fix? I hit ESC during boot and picked the previous Kernel from the boot list (2.6.15-52-386) Got power and connectivity to the card during boot. Hope this helps.

---

