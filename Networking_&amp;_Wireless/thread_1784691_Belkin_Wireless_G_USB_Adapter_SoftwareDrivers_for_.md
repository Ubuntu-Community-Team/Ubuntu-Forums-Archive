---
title: "Belkin Wireless G USB Adapter Software/Drivers for Ubuntu 11.04"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by PiratePete247 on 2011-06-17
Hi all.

I'm new to the forum so please forgive any noob mistakes

I have just installed Ubuntu 11.04 on an old machine to get a feel for it. No problems with the install, but I don't have a LAN connection lead spare so I'm trying to install my Belkin Wireless G USB Adapter (K75-F5D7050B which requires version 3 according to the Belkin site). 

Unfortunately I can't find any Ubuntu software & driver versions on their site and I only have a windows installation disc.

Sorry if this is a daft question, but any advice would be great!

Thanks

Russ

---

### Post by StrayEddy on 2011-06-17
Hi there,
This is a good HOWTO. 

[http://www.linuxforums.org/forum/wir...problem-4.html]("http://www.linuxforums.org/forum/wireless-internet/87162-belkin-802-11g-wireless-g-usb-network-adapter-problem-4.html")

**_Appendix:[_**

- install ndiswrapper
- Start terminal
  Type:   vim /etc/modprobe.d/blacklist
            blacklist rt73usb
            blacklist rt2570
            blacklist rt2500usb


  Download the windows driver rt73 version 3 from Belkin.

  [http://www.belkin.com/support/articl...=5381&scid=221]("http://www.belkin.com/support/article/?lid=en&pid=F5D7050&aid=5381&scid=221")
   or
[http://www.belkin.com/support/articl...=f5d7050v3.exe]("http://www.belkin.com/support/article/?lid=en&pid=f5d7050&aid=5381&scid=221&fid=2395&fn=f5d7050v3.exe")

   Unpack the exe-file 

Follow the HOWTO


Is working...:grin:

Good Luck !

---

### Post by StrayEddy on 2011-06-17
Next time you buy, check compatability before, here:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)

---

### Post by PiratePete247 on 2011-06-17
Hi, 

Many thanks for the quick response. I'll try this now and report back :)

Russ

---

### Post by PiratePete247 on 2011-06-17
Hi again,

Have been following the How to thread, but I'm not clear on how to install the ndiswrapper-1.56 from file I've place in the home folder? I assume that the Konsole I'm supposed to use is part of that software?

Thanks.

---

### Post by StrayEddy on 2011-06-17
konsole is just the terminal in KDE, in your case open a terminal (Ctrl+Alt+T).

Then use 'ls' and 'cd' commands to go to your home folder, then you can continue the how to.

Or in your home folder (if you have the option available), just right click and choose to open a terminal here.

---

### Post by PiratePete247 on 2011-06-17
Hi again. That makes sense, thanks. The how to is making sense now, but the only issue I have is that when I use the SU command and type my normal password in it comes up with Authentication failure. Am I supposed to have a different password? Thanks.

---

### Post by StrayEddy on 2011-06-17
no... same password normally.

try: 'su root'

or you could just use 'sudo' in front of every root command you need to do (ex: sudo iswrapper -l)

---

### Post by PiratePete247 on 2011-06-17
Just wanted to say that I'm all sorted thanks to your help. Many thanks for the continued response. Great forum.

---

