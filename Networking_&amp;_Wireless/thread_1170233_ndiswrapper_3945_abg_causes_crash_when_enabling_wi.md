---
title: "ndiswrapper 3945 abg causes crash when enabling wifi ?"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by crazybuntu on 2009-05-26
i tried ndiswrapper with ndisgtk and installed the .conf file from the CD driver . 

it says unable to see hardware, but it detects the wifi when i did lshw , iwconfig

problem is when i enable the wifi with Fn+f12 key , the laptop crashes and shuts down instantly ???

i already did a blacklist on the iwl3945 

what would cause this ???

---

### Post by cariboo on 2009-05-26
If ndiswrapper doesn't list the device, then you have the wrong driver installed. I would try a driver for a different version of windows.

---

### Post by t0mppa on 2009-05-26
Check your system logs first to be sure it's NDISWrapper that causes the crash.

I had a similar issue, where NDISWrapper just started producing kernel panics and freezing the OS whenever the wireless got enabled. First it worked fine for a couple of weeks and then it just crashed out of the blue in the middle of my work one day. After removing ndiswrapper everything went back to normal. And when I filed a bug report, noticed that there were other reports where for instance Network Manager had caused the crash.

---

### Post by crazybuntu on 2009-05-26
too tired to analyze every little thing... y dont they have paid support

---

### Post by crazybuntu on 2009-05-26
im sure its the ndiswrapper because i didnt change anything else

---

