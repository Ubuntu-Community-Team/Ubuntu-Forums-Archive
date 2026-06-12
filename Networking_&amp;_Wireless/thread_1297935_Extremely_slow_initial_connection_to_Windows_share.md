---
title: "Extremely slow initial connection to Windows share"
date: 2009-10-22
forum: Networking &amp; Wireless
---

### Post by matthock on 2009-10-22
I'm having a problem with extremely slow initial connections to Windows file shares over my home network. Once the share is connected, it runs quickly - I can stream H.264 video off the share and watch it on the Ubuntu machine - but when I initially try to connect to the share, it will hang for 20-30 seconds before between clicking on the share and finally showing me a file listing.

For a little background, I store most of my files on an HP Mediasmart EX475 server running Windows Home Server (essentially a specialized version of Server 2003). WHS exposes the files it stores as 8-9 separate windows file shares. This is connected to the rest of my network via a D-Link DIR655 gigabit wireless router. I also have a small gigabit switch that connects to the router to connect several devices elsewhere in the apartment that are next to each other.

When connecting to the file server from a Windows machine, the connection is essentially instant. My original computers are a desktop and a laptop running Win7 and Vista Home, respectively, and as soon as I click one of the shares on either machine, it comes up and shows me the files. It is not a problem with the file server or the network - I can work at nearly full gigabit speeds between the server and the Win7 desktop. However, I just got another system up running Ubuntu, as the amount of time I spend gaming has been declining and I am considering switching to it as my main desktop environment. This problem, while not a deal breaker since it does eventually start working, has been quite annoying and distracting.

---

### Post by matthock on 2009-10-27
Ok, fixed the problem - I can now connect to the SMB shares on my WHS server as quickly from Ubuntu as I can from Windows.

Problem was with DNS. No domain was set, so it wasn't checking .local very quickly. Added the line "domain .local" to the top of my resolv.conf before the nameserver entries, and now it works quite well :)

---

### Post by matthock on 2009-11-10
Coming back to this...

Just wanted to correct some things about my "resolution" to the problem, in case anybody came by in the future - wouldn't want to give bad advice.

The resolv.conf fix was quite temporary - it lasted until I restarted my box (which I don't do often, so it took me a bit to notice it). Ubuntu rebuilds resolv.conf from scratch every reboot, so changes directly to that file are kind of pointless.

The change that is actually working long term is to enable WINS support. Once I knew what I actually needed to do to get it working, it was pretty quick to find an answer - there's complete instructions at [http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206) - that will get things running so that you can resolve host names.

---

