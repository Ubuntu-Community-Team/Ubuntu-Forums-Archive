---
title: "Wireless Shows Connection But Doesn't Work"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by europabloke on 2010-06-07
This is my first post, so hello to all of you and thank you for taking the time to answer!


I just installed Ubuntu on my windows pc with no problems....except for wireless that is.

I have a USB Linksys WUSB54G adapter to access my 2WIRE, WEP network.

The thing is, it shows up in the top right hand corner.  It even gives me the signal strength.  But when it comes to using Mozilla, it is never able to access a page.  

If I try to Ping something, it's unable to.

So I thought maybe I need to use ndiswrapper with my .inf and .sys files from the driver for my windows.

I installed it, and added the driver to it...everything went O.K.

I check it and it says it's installed and working.

Again, I can see the wireless networks, and "connect" but when I try to use the connection there is nothing.

I have also tried my neighbours non-WEP connection, but it still doesn't work.

So I'm sort of at a loss with what I should do now.

I see the networks, can "connect" but can't browse.

I installed the drivers from my windows, and it still doesn't work.

What's the next step?

PS I used a LIVE CD of Knoppix and I can connect to the Network within 30 seconds and start browsing the net.

Hope I covered it all clearly enough, please let me know if you need me to clarify any points.

Thanks again for your time in this matter!  Cheers!

---

### Post by b k on 2010-06-08
> **europabloke said:**
> 
 
I have a USB Linksys WUSB54G adapter to access my 2WIRE, WEP network.

 
Hi, I will try to help.
 
I am assuming you are using Ubuntu 10.04 LTS.
 
As there are several versions of Linksys WUSB54G adapter , please identify your device ID:
 
May I suggest you go to *Applications*, *Accessories*, *Terminal* and do :
 
Code:
[COLOR=blue]**lsusb**[/COLOR] (Please post your output)
 
 
*If* one of the lines of your **[COLOR=#0000ff]lsusb [/COLOR]**output is something like:
 
[COLOR=#ff0000][COLOR=black]Bus 001 Device 002:[/COLOR] ID 1737:0077 Linksys[/COLOR]
 
 
[COLOR=black]Do this:[/COLOR]
 
Code:
[COLOR=blue]sudo gedit /etc/modprobe.d/blacklist.conf[/COLOR]
 
and add the following line to the end of the opened file:
 
[COLOR=red]blacklist rt2800usb[/COLOR]
[COLOR=#ff0000]blacklist rt2870sta[/COLOR]
 
**[COLOR=black]save[/COLOR]** and close
 
[COLOR=#0000ff]Reboot[/COLOR] and create your wireless connection if you have not previously done so.
 
If it does not work please also post the output of:
 
Code:
[COLOR=blue]lsmod[/COLOR]
 
 
Good luck

---

### Post by europabloke on 2010-06-10
Thank you for your reply!  I apologise for being so late, I was fitting my hardware into a new case and so haven't been onilne.

I finally got it working.

I still have no idea what the  problem was, but I just installed and uninstalled everything like 5 times, after which my wireless didn't show up anymore.  

I thought I'd broke it and had to uninstall and reinstall another 3 times, after which my wireless showed up again.

I also, through luck, found out that I cannot be in roaming mode, but rather have to specify all the details.

So after many uninstalls, reinstalls, and reboots, it is finally -for some reason- now working.

Thank you again for the information though!

---

