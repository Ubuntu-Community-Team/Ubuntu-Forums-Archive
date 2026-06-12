---
title: "Lenovo Thinkpad Edge, Ubuntu 10.10, wifi connection troubleshoot"
date: 2011-03-12
forum: Networking &amp; Wireless
---

### Post by byrdiblack on 2011-03-12
Sorry if this is in the wrong place, feel free to delete if the thread is misplaced! 

thank you in advance to anyone for taking the time to help!

Level of User: 
I am an absolute beginner on Ubuntu. I can paste code into the terminal but beyond hitting enter, I don't really know what I'm looking for. 

Computer: 
Lenovo Thinkpad Edge 14 inch, Intel. 

Wireless: 
In Lenovo is a Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10). My wireless network is a WEP Password protected network from a D-Link -524 router. 

Installation and Version: 

I used Ubunto Destop version 10.10 Maverick Meerkat. I downloaded the ISO, burnt it to a CD-R, then booted from the disk, and installed completely replacing/deleting Windows 7. 
I opted to not install the 3rd party software. 

The Issue(s): 
After starting up the computer, Ubunto desktop loads fine and connects right away to my wireless network. After 15 minutes or so the connection is lost and no matter how hard I try to reconnect it will not unless I restart the machine. 

I've been looking on forums and trying troubleshoots for 5 hours now! :sad:

I've tried installing a different wireless control application called WICD Network Manager, but that didn't connect at all, even on startup. 

On my mac, the signal drops sometimes, but returns right away. So I know the wireless is available to reconnect with. Sometimes it says its connected 100% but no web pages will load. 

Thank you again!

---

### Post by rCXer on 2011-03-14
Try [this thread]("http://ubuntuforums.org/showthread.php?t=1700636"). [This thread]("http://ubuntuforums.org/showthread.php?t=1412406") also has alot of info but it's a bit of a long read...

---

### Post by byrdiblack on 2011-03-15
On the one thread the Thinkpad is an AMD processor and I am working on an Intel one..do you think I should follow the same directions installing the driver as outlines in your link: install realtek driver ([http://blog.maniac.nl/2010/11/06/thi...untu-gnulinux/]("http://blog.maniac.nl/2010/11/06/thinkpad-edge-11-amd-nile-and-using-it-with-ubuntu-gnulinux/")) ???

I appreciate your suggestions!

---

### Post by rCXer on 2011-03-17
Hi byrdiblack,  I got your PM.  Do you know what wireless card you have?

---

### Post by byrdiblack on 2011-03-23
After a great deal of research, it would seem that this is the bug associated with my problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/687692](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/687692)
 
Is there hope for this being patched or should I just walk away from Ubuntu on this particular laptop? It's unfortunate but I just can't use this OS if the wifi doesn't work the way it should.

---

### Post by Andavane on 2011-03-23
Just a thought ~ I think if you had put the tick in for install 3rd party software, you might have got the proprietary driver. Not sure about your model, but mine an HP Pavilion dm1 ultramobile. I ticked the 3rd party software option and after installation, a jagged thing appeared at the top. There were a couple of speed options (or something) to tick. I tried each one, and kept the one that worked best.

Oh yes, while doing all this I had to use the crossover cable to access the net (which it needs for update & also for installing wireless drier) Itall works fine.

I wondered if your case was similar.

I was thinking of getting the model you've got as a backup laptop, so am very interested in this thread.

---

### Post by byrdiblack on 2011-04-04
I installed the latest Natty kernal and the problem subsided..I was ecstatic for about a week, but then the dreaded wifi trouble returned. 

I think I'm just about ready to give up, and reinstall windows. It would seem that this particular model is just not compatible with ubuntu.

---

### Post by Andavane on 2011-04-04
When you were installing Ubuntu 10.10, did you tick all those boxes (especially the 'tick 3rd party software box)?
Did you have a crossover cable in the machine, to give you internet during the installation?

Did you install extra drivers for the wifi after the installation?

---

### Post by byrdiblack on 2011-04-04
During 11.04 installation, I ticked the box to install 3rd party software with the internet cable in. 

I did not tick the box for 10.04 installation. 

I did not install extra drivers for the wifi, I'm not really sure how to do that!

---

### Post by emtdan on 2011-04-26
Many - if not all - of us with Realtek 8192 have the same problem.  Switch to WICD to manage your networks, and delete Network Manager.  It is a NM bug, not ubuntu kernel.  

The one problem with this is that Wicd is not longer updated so it is very buggy.  It works best with WPA connections, but WEP does work as well - just takes 5 minutes to connect.

---

