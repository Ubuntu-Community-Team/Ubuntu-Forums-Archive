---
title: "Problem with Belkin N150 Micro Wireless USB Adapter"
date: 2011-04-15
forum: Networking &amp; Wireless
---

### Post by skiabox on 2011-04-15
I have this specific adapter (its code is #F7D1102) attached to my sony vaio but it does not work on ubuntu 10.10.
This device is working properly in windows 7 (the system is dual boot).
Any ideas?
Thank you.

---

### Post by KegHead on 2011-04-15
Hi!

Can you click on the network Icon?

If so, you might be able to select your wifi connection.

KegHead

---

### Post by skiabox on 2011-04-15
The laptop is using its internal adapter and connects using g protocol to the router, but I want to use the usb dongle so that I have the n protocol in use.

---

### Post by KegHead on 2011-04-15
Hi!

Were you able to determine if your wifi is available via the icon?

KegHead

---

### Post by skiabox on 2011-04-16
Yes it is available but using laptop's internal network card.

---

### Post by leillo1975 on 2011-04-24
I have the same problem. I´m can´t connect with Ubuntu using the Belkin usb wireless micro adapter N150 (F7D1102nt). If I use lsusb in terminal, this adapter have the following ID:

ID 050d:1102 Belkin Components

---

### Post by cubefish on 2011-05-08
Hey guys,

  I've been trying to have this card working on Natty for some time, now. I've been reporting my progress in [another]("http://ubuntuforums.org/showthread.php?t=1712138")  thread (by the way: it's marked as "solved", but it really isn't, at  least for Natty. I don't know if I should ask the guy who opened the  thread to remove the "solved" tag, or if I should just continue the  discussion here.. any idea? It would make sense to stay there, since my  approach is a direct consequence of what has been initially written in  that thread).

Basically, I got to the point where I found out  that under some versions of the kernel (like the current one in Natty)  it's not possible to compile the linux driver for the belkin micro n150,  but under other versions it's actually possible (so if you don't mind  using the 2.6.37 mainline kernel you should be fine, for example). 

My  main problem is that I don't know where I should file a bug about this  (and I really want to file a bug; I really want to see this driver  compiling on a fresh Natty install). Any idea? I mean, it looks like a  problem with the kernel, but I don't really know what to do (I mean:  I'll probably try to file it [here]("https://bugs.launchpad.net/bugs/bugtrackers/linux-kernel-bugs"), but I'm not sure..)

Cheers!

PS:  anyway, if anybody else would like to test whether he/she's getting the  same results as me by following the procedure documented in the other  thread, please do and report!

---

### Post by cubefish on 2011-07-15
Problem solved, at least for me. As I explained in more detail [here]("http://ubuntuforums.org/showthread.php?p=11050155"), the **linux-backports-modules-cw-2.6.39-generic** metapackage does the trick on Natty, and I believe that (since the driver version in 2.6.39 seems to work) the Belkin N150 should work out-of-the-box in Oneiric.

---

### Post by Back to Basics on 2013-01-29
I had a similar issue with Belkin N150 USB B/G/N wireless adapter in Ubuntu 12.04 on an inspiron 1545 Laptop.
 Firstly you need an internet connection,download the driver RTL8188CUS from Realtek for linux.
 Site location [http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true). 
 Next extract the folder because it is zipped. Right click and extract.
 Next right click on the folder in ubuntu and make all files in the folder executable.
 Next right click on the folder (unzipped, executable) and open in terminal folder – you will be allowed this option.
 Next type *sudo bash install.sh*
 Next fill in the prompts in the terminal window as required.
 

 When all is done reboot the computer.
 If the computer has an internal Wireless card press F12 at start-up and disable it in the  bios otherwise you will get a conflict (you can always go backin and renable it if required.)
 

 I had difficulty following the instructions that are available but managed to figure it out.
 Works great now.

---

### Post by overdrank on 2013-01-29
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

