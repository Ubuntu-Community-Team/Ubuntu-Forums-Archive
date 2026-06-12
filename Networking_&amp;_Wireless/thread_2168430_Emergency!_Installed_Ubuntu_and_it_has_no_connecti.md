---
title: "Emergency! Installed Ubuntu and it has no connection to internet whatsoever."
date: 2013-08-17
forum: Networking &amp; Wireless
---

### Post by martinbohman on 2013-08-17
I bought a new computer, hoping to dual boot Win 8 and Ubuntu 13.04. 
I have successfully installed both OS, but in Ubuntu I have no connection to the internet, even though the ethernet cable is plugged in and internet works perfectly in Win 8. Already in the Ubuntu installer, it says that I have no internet connection.

Things that might be of interest:

* I have this motherboard: MSI Z87-G45 Gaming ([http://www.msi.com/product/mb/Z87-G45-GAMING.html#specification](http://www.msi.com/product/mb/Z87-G45-GAMING.html#specification))
* Internet did not work in Win 8 until I installed the networking drivers that came with the motherboard (Killer Ethernet something)
* I have tried different installation configurations, tried v. 13.04, 12.04 and 12.10, and tried installing on a separate hard drive. (the fact that the installer says "no internet connection" seems to indicate that the problem has nothing to do with the installation though.)
* I can't even reach my router at 192.168.0.1. 
* The motherboard has no wireless capabilities. 

I have spent hours and hours googling, trying many different suggested methods and not quite finding someone who seems to be having the same problem. 

PLEASE help me!
I am happy to provide any additional information, terminal outputs etc.
If I run the terminal command lspci I get the  following output (among other things): 
03:00.0 Ethernet controller:  Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller (rev 13)

Many thanks,
Martin

---

### Post by bart.a on 2013-08-17
Hi martin,

I have seen your post on ask ubuntu also.. I think the answer you are looking for is already posted in this forum..
Check out[ this link]("http://ubuntuforums.org/showthread.php?t=2008332").
The poster had the same problem and used existing driver.. Maybe this will work for you too..

---

### Post by martinbohman on 2013-08-21
> **bart.a said:**
> Hi martin,

I have seen your post on ask ubuntu also.. I think the answer you are looking for is already posted in this forum..
Check out[ this link]("http://ubuntuforums.org/showthread.php?t=2008332").
The poster had the same problem and used existing driver.. Maybe this will work for you too..

Thank you! My problem is now solved. However, I used a different method.

I got information from another source that kernel 3.10 had support  for this networking card. So what I did was install the kernel using  this guide [http://www.ubuntubuzz.com/2013/07/how-to-install-linux-kernel-3101-on.html](http://www.ubuntubuzz.com/2013/07/how-to-install-linux-kernel-3101-on.html)

  Very simple and the connection started working right away after  update and restart. I haven't experienced any problems with the new  kernel yet so as long as I don't I will stick with this solution. It  seems though as the thread you linked to me described the same problem  and I'm sure that would've fixed the problem aswell. 


  For those of you who might want to follow the instructions in that  thread, on the top of page 7 there is a post from someone who had made a  patch for this issue (not sure exactly how it worked but I guess it was  to simplify and reduce the manual hacking as described in the first  post).

---

