---
title: "freezes while connecting to wireless at startup"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by nyth0 on 2009-08-31
I have an issue that comes now and then with Jaunty where I will start up the computer, get to the log in screen, log in and it starts searching for a wireless network. About 50% of the time (there may be a condition that I am unaware of) ubuntu will freeze completely, forcing a restart, before a connection is made. The little graphic will be spinning and only one orb will be green, then its frozen. This doesn't ALWAYS happen, but I can't figure out why this is going on.
 
It may be helpful to know that I had wireless problems in Gentoo and Sabayon when I had those distro's installed, but never something like this. Any help would be greatly appreciated!
 
I believe this may help:
 
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
 
If I forgot to add anything that I should, please let me know so I can add it.

---

### Post by nyth0 on 2009-09-14
A quick update - the issue has escalated to the point where it is not uncommon for ubuntu to freeze at least once a day, if not more. This usually happens right after startup at some time, but will also happen randomly if I leave the computer on for too long or during when electric sheep is playing as my screensaver. The frustration of freezes is leading me to almost not wanting to run Ubuntu anymore.

If anyone has any idea about this or could at least help point me in the right direction by telling me what I need to provide to help someone help me please let me know!

---

### Post by Sidewinder1 on 2009-09-14
But if it's happening in multiple OSs, as you stated on the irc channel,  that's a pretty good clue favoring hdw. problems.
HTH, Side

PS You may wish to request a Mod. move this to Hardware and Laptops sub-forum; I think you'll get a better response there.

---

### Post by nyth0 on 2009-09-17
As per Sidewinder's request over IRC I ran a memtest this morning on my laptop and the memory all checks out. Any other ideas on what might be the problem besides just hardware conflict?

I'm aware and understanding that it might just be better to run windows on this lappy and vnc to my desktop to use linux, but we'll see what happens.

---

### Post by nyth0 on 2009-10-05
I'm not sure if the problem is fixed or not, but I have left the computer on over 3+ days and it has frozen. I modprobed ndiswrapper, configured wicd and downloaded some backend jaunty modules and it seems to have solved the issue. I will post further if the issue occurs again. If anyone is interested in the name of the modules I installed through Synaptics, I'd be happy to look it up and share.


-nyth0

---

### Post by noobuntu9 on 2009-10-05
Hi, i am having the exact same problem with my Asus F50SV. the wireless card i am using is also the Atheros AR928X. **nyth0**, That would be a great help if you could post the modules you installed though synaptics. thanks in advance.

cheers,

---

### Post by nyth0 on 2009-10-05
Hi Noobuntu9 -

First thing I did was:

modprobe ndiswrapper

Make sure you do this as root. Next, go into Synaptics and search 'linux-backports-modules-jaunty'. This will bring up multiple packages all with identical names. Choose the one that is described as 'Generic Linux backported drivers'. This will include a second package automatically, which is fine. Next search for 'wicd' and mark the only option available (or if there is more than one package, choose the one called 'wicd' and described 'wired and wireless network manager'). Install these packages and restart your computer. Hopefully this will fix your problem!

---

### Post by noobuntu9 on 2009-10-06
Thanks for the quick reply, i will try it out when i get some spare time and post back my results. 

cheers,

-noobuntu9

---

### Post by noobuntu9 on 2009-10-06
Hey, when i tried to do** modprobe ndiswrapper**, it wouldn't work because apparently ndiswrapper was not installed, so i just went ahead with the other Synaptics installs, and everything has been working perfectly. 

Problem fixed! \\:D/ Thanks for the instructions!

-noobuntu9

---

### Post by nyth0 on 2009-10-06
Noobuntu9:

Glad that your problem is solved, and I hope it stays fixed :)

---

