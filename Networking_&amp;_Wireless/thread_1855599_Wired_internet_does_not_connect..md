---
title: "Wired internet does not connect."
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by Arcx500 on 2011-10-06
I've retired from playing MMO's so I wanted to move from Windows to Ubuntu permanently.

Problem is after I did, I was unable to connect to the internet at all.
I'm not sure if reinstalling may solve the problem but I rather not take the chance of losing that much time.

However, on this very same computer, I once installed Ubuntu next to Windows and had no problem with it whatsoever.

I currently am back on Windows 7 and really want to move to Ubuntu.

Keep in mind as I'm a beginner when it comes to Ubuntu so treat me as if I have never heard of ubuntu.
I only know a little bit about a terminal where commands should be entered and did that a bit.
In any case, any help would be greatly appreciated on how to solve this.

---

### Post by viperdvman on 2011-10-06
Although it's automatic most of the time, sometimes you have to click on the network icon in your system tray (next to your clock in Ubuntu) and select Wired Ethernet, eth0, whatever your Wired Ethernet is. At least it's supposed to be automatic during the Ubuntu Install process. What kind of network adapter does your computer use?

Is Ubuntu being installed by Wubi, or is it being installed on its own partition in a dual-boot environment? Or are you installing it as a stand alone OS?

---

### Post by Arcx500 on 2011-10-06
> **viperdvman said:**
> Although it's automatic most of the time, sometimes you have to click on the network icon in your system tray (next to your clock in Ubuntu) and select Wired Ethernet, eth0, whatever your Wired Ethernet is. At least it's supposed to be automatic during the Ubuntu Install process. What kind of network adapter does your computer use?

Is Ubuntu being installed by Wubi, or is it being installed on its own partition in a dual-boot environment? Or are you installing it as a stand alone OS?
I've clicked the network icon and clicked eth0, it attempted to connect but then a message appeared saying I've been disconnected and that's something I also found strange, during the clean install, it confirmed that I had a working network connection but when I got to the desktop, it didn't work at all.

How do I check in ubuntu what kind of network adapter I'm using? Strangely enough if it's Wubi, I have no problem with internet but if I perform a clean install with only Ubuntu on the hard drive, this happened.

Just now, I finished installing ubuntu inside Windows.

---

### Post by viperdvman on 2011-10-06
Although I'm not sure about how to check what all devices you have in Ubuntu, you can do it in Windows by checking your device manager. It usually tells you what kind of device you're running. I've heard that Ubuntu can be finicky with some devices, whether Wifi or Ethernet.

Another thing to consider as well, does your internet service provider limit you to X number of computers in your house connecting to the internet? I know some providers limit you to, for example, 2 computers, especially if you're using their routers. If you're already using 2 computers, then your provider may be trying to assign a 3rd IP to your Ubuntu install... which wouldn't happen when running Ubuntu within WIndows through Wubi. WIth some providers, it'll really slow down that internet, make it very intermittent, or just not connect at all.

I'd call your ISP and see if they can help you with your connectivity problems.

---

### Post by Arcx500 on 2011-10-06
Isn't it weird enough that if I install Wubi that I don't have network problems at all? I booted into Ubuntu and everything works fine. I'm worried that if I attempt another clean install, my network will just go again.

I want my computer to always start ubuntu when I turn it on.

---

### Post by Arcx500 on 2011-12-04
I take it after all this time nobody has ever experienced this problem before.

---

