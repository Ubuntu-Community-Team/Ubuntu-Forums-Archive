---
title: "Backtrack 4 wireless"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by duds2008 on 2010-08-24
Hello all. I love testing different distros and very seldom do I encounter a problem that I have not been able to solve.
I have just installed Backtrack 4 F on a USB key. I love it. I now want to dual boot it with 10.04. No problems there. The only problem I am having is my lack of understanding the KDE. While running BT4 live off the USB, I am unable to connect to my wireless n/work. The facility does not *seem* to be provided.
Any clues that may point me in the right direction are sincerely appreciated in advance.
Many thanks. Dudley.

---

### Post by duds2008 on 2010-08-24
Computer is Acer Aspire One net book.

---

### Post by duds2008 on 2010-08-24
Wireless router is DLINK.

---

### Post by duds2008 on 2010-08-24
Sorry. I never meant to *screw* up by multiple posts :(

---

### Post by duds2008 on 2010-08-25
Okay. I solved it. And to anyone who *may* be interested, the solution is as follows:
Once you have booted up BT 4F you have to bring your w/less if up:
#ifup wlan0
Then start the network:
#start-network
Fire up x:
#startx
Once you have your graphical Desktop, navigate to Internet -> wicd network manager (I had *tried* all this before but never realised I had to manually start the n/work first)
Thanks to all who took the time to read my posts. Sorry once again for my clumsiness by *multi* posting ;)

---

