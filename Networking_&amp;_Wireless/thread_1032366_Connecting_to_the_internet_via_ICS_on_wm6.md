---
title: "Connecting to the internet via ICS on wm6"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by Fxy on 2009-01-06
Hi 
 
Since i installed ubuntu on my laptop over a month ago ive been trying to conenct to the internet on it via "Internet Connecting Sharing" on my windows mobile... Earlirer on today while in starbucks i managed to get connected to an unsecured wireless network and after i googled a few things, i found something that i thought might work... Below is what i found and did ;)
 
[FONT=Helvetica]First, you need to make sure you have the right Ubuntu packages installed:[/FONT]
 
 
 
[FONT=Helvetica]sudo apt-get install subversion build-essential[/FONT]
 
 
 
[FONT=Helvetica]Now do the following in a terminal:[/FONT]
 
 
 
[FONT=Helvetica]svn co [http://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite](http://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite)[/FONT]
 
[FONT=Helvetica]cd usb-rndis-lite/[/FONT]
 
[FONT=Helvetica]make[/FONT]
 
[FONT=Helvetica]sudo ./clean.sh[/FONT]
 
[FONT=Helvetica]sudo make install[/FONT]
 
 
[FONT=Helvetica]That should be all you need on the Ubuntu side. On the phone, start ICS. There’s no shortcut on the Start Menu, so use the File Manager to browse to /Windows and look for IntShrUI.exe. To make things easier, you can click Menu>File>Create Shortcut and create a shortcut in Windows/Start Menu. Once you start ICS, click the left soft key (”Connect”) and plug in the USB cable. That should be it.[/FONT]

[FONT=Helvetica]So i did all that but i still have a problem, ever time i connect my phone via its usb cable and connect via ICS it comes up on my phone as connected but i still cannot surf the web on ubuntu... I have made sure that under the wired connection is selected from under the icon placed on the taskbar, but still no joy :confused:...[/FONT]

[FONT=Helvetica]You help will be much apprichated :D[/FONT]

---

### Post by Fxy on 2009-01-07
Any ideas anyoone...

---

### Post by Fxy on 2009-01-14
Bump*
 
Since ive yet to get any kind of reply here i thought i should try a few things....  First was googling my problem and looking for answers...  Second was that i connected my device to the internet on a windows vista laptop and wrote down the ip's etc etc, i then added them in ubuntu to see what happened, yet no joy...  If anyone can tell me what im doing wrong or what i have missed then pls post, you help is really wanted ;)...

---

### Post by Forlornity on 2009-03-06
I'm having similar issue myself, whenever I want to use the internet on the go I have to boot into my Windows partition (originally intended solely for gaming) and use that, I can get an ssh connection going over ICS on Ubuntu strangely enough, but no web pages will come through, and using lynx (and, I assume, other text-based applications) over ICS had the same issue as firefox straight from the machine: all pages are blank.
It's been a while since I last tried, so I can't remember if pinging worked or suchlike (though I'd assume so, considering I connected to my ssh box)
My thoughts now are that it's a proxy issue.
I'm looking into it.

EDIT: Proxy seems to be a no, I've disabled proxy on my windows boot and no change, still loads pages fine.
Now suspect usb-rndis is to fault.

---

### Post by ZoFreX on 2009-12-08
Running Xubuntu here. Wasn't even an issue on the old version on my old laptop, but I just installed 9.10 on this ThinkPad and, although the tethered connection shows up as normal, I couldn't get to any web pages (unless they were REALLY small). It seemed that any connection would only work for a small time / amount of data, and I was getting a LOT of Rx errors (over 95% of total).

I'm currently on a train so as you can see I have fixed it (or at least improved it!). I was fiddling with various things and I noticed the MTU was very high (4700 or so). I tried 4700, 4500, 1500, and then 500. Once I set it to 500, everything started working!

Hope this helps someone out there!

---

