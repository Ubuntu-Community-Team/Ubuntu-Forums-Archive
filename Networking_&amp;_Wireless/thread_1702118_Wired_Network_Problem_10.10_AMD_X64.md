---
title: "Wired Network Problem 10.10 AMD X64"
date: 2011-03-07
forum: Networking &amp; Wireless
---

### Post by Minisupra on 2011-03-07
THE SOULUTION: 

 Did a Hard/Cold-Boot. 
Step 1: Shut Down your computer.
Step 2: Turn off the Power Switch and unplug the PowerCable. 
Step 3: Wait 4-5 Minutes. 
Step 4: Now plug in your powercable and turn on the witch, Start computer and your internet should work!

---------------------

Hello there everyone!

I'm kinda new to Ubuntu and I've had the 10.10 AMD X64 as dual with Windows 7, main OS for me is Windows. 

Anyways, yesterday I went on to Ubuntu and installed Google Chrome, Worked as a charm. After that i noticed there was some Ubuntu (~300MB + ) Downloaded Installed & Reboot. Then suddenly the internet isn't working. As I'm not very familiar with Ubuntu Settings at all, I rebooted back to Windows 7 (Enterprise 64-bit)to see if the internet works there, wich it does not.

Everything i can see from the Network Connections is that my Local Area Connection 3 is just switching forth and back from Enabled or Network Cable Unplugged. Sometimes when I run the Troubleshoot it turns into Limited Access, but that's just for a while. 

I can't reach the router from this computer anymore either, wich have worked perfect every other day before. 

What I've tried this far is, 
1. Looking through the TCP/IPv4 settings, wich is now set to obtain an IP address /DNS Automatically instead of a static IP, just incase.
2. Restarted Router (Unplug for 10 secs & Back on)
3. Complete Reset of the Router
4. Checked Ethernet-Cable.

I aswell uninstalled Ubuntu from Windows to see if that would solve the problem. 

I've never had a single problem with my Networking. I can't be sure that the Ubuntu updates tossed some settings but it sure came at the right time if it would be something else than Ubuntu :)

Note; I can reach router and access internet with any other computer in the house. 

My Hardware is at the moment:

Motherboard: GA-870A-UD3 ([http://www.gigabyte.com/products/product-page.aspx?pid=3517#sp](http://www.gigabyte.com/products/product-page.aspx?pid=3517#sp))
Network Card: Realtek 8111D chip (10/100/1000 Mbit) (Standard)
Processor: AMD  Athlon II X4 640 3.0 GHz
OS: Windows 7 Enterprise

If anyone got any experience with the problem I'd love If you could have some tips/thought and feel free to ask me anything that could help you get a better picture of the problem!

Thanks in Advance! // Martin J

---

### Post by tyleruk on 2011-03-07
A few other people have been having the same problem with these cards:
[http://ubuntuforums.org/showthread.php?t=1530387]("http://ubuntuforums.org/showthread.php?t=1530387")

It&#8217;s worth putting your card into a different PCI-E slot to see if that helps, or if you can try a different card in your PC.

---

### Post by Minisupra on 2011-03-07
> **tyleruk said:**
> A few other people have been having the same problem with these cards:
[http://ubuntuforums.org/showthread.php?t=1530387]("http://ubuntuforums.org/showthread.php?t=1530387")

It&#8217;s worth putting your card into a different PCI-E slot to see if that helps, or if you can try a different card in your PC.

Thanks for the tip but the card is Onboard. (Standard with my Motherboard)

---

### Post by Minisupra on 2011-03-07
I've just read that a Hard/Cold Boot might solve this problem. I'm trying now as I post this.

---

### Post by Minisupra on 2011-03-07
Problem Solved! Did a Hard/Cold-Boot. 
Step 1: Shut Down your computer. 
Step 2: Turn off the Power Switch and unplug the PowerCable. 
Step 3: Wait 4-5 Minutes. 
Step 4: Now plug in your powercable and turn on the witch, Start computer and your internet should work!

---

### Post by Kymation on 2011-04-15
Thank you! I had the same problem after a kernel update this morning.

For the record, my hardware is slightly different:
Gigabyte GA-890GPA-UD3H motherboard
AMD Phenom II X6 CPU
Ubuntu 10.10

The common component is the Realtek RTL 8111 ethernet chip. That's likely where the problem lies.

Don't forget to completely unplug the computer from the wall power. Just doing a shutdown and cold boot won't work.

Regards
Jim

---

