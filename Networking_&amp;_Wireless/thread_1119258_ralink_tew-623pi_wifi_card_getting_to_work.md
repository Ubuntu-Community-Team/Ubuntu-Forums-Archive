---
title: "ralink tew-623pi wifi card getting to work"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by kcihtred2 on 2009-04-07
ok, now i need to get my wifi workin on my desktop it has a tew 623pi wireless card by trendnet...  its ralink also...  and its offline completely no way to get it online cause of reasons beyond my control (AKA parents)  so if someone could give me the .deb for ndiswrapper i can get the rest

ty

kc

---

### Post by 73ckn797 on 2009-04-12
I just fixed a weak signal with the Trendnet TEW-423Pi wireless card in Jaunty & Intrepid.

In Synaptic Package Manager look for "ndisgtk". selecting that will also load the other necessary ndiswrapper files. Once installed you will find it under System/Administration as wireless drivers. Insert the CD that came with the card and copy the WINXP directory from the drivers dirctory to your download or document directory.

Open the new program and from there select the *.inf file from the directory you copied off of the disk. Once that is completed reboot your system. You may have to re-enter any password(s) for the wireless access.

There is also a thread about doing this via terminal but I like to provide graphical solutions as much as possible. Let me know how this works for you. I did an advanced search for "trendnet" and found the terminal method.

I went from 10% signal strength to 95% in Jaunty. The router is only 10 feet away. The Intrepid signal went from 8% to 95% and that computer is at the other end of the house and upstairs from where the router is.

---

### Post by RedSingularity on 2009-04-12
You want a link to the .deb file?

---

