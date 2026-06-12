---
title: "Wifi doesn't work after reinstalling Ubuntu 10.10"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by Milkman99 on 2011-03-28
Hey,

I can't connect to the internet as the wifi hasn't worked since I reinstalled Ubuntu 10.10...It might be a hardware problem as this problem occured, when I tried to install Windows 7 but it didn't work on my computer...than I decided to reinstall Ubuntu 10.10, but than the wifi just wasn't working...but it was working before the win 7 installation and during the installation win 7 recognized my wireless connections...and even when I tried installing win 7 AGAIN it still recognized them...but every time I want to install Ubuntu 10.10...wireless just doesn't work....:S

---

### Post by TBABill on 2011-03-28
We need to know what device you are using or we cannot help. Go to Applications>Terminal and type in ```
lspci
``` and paste the output of that command back here for us to see. Or, if this device is USB instead of internal, do this instead: ```
lsusb
```
 
Note: those are lower case "L's" in the commands...LSPCI and LSUSB

---

### Post by Milkman99 on 2011-03-28
Thank you for the fast response. In the meantime I realised that the problem was the lack of internet connection so during the second and third installations the drivers of the wifi card couldn't be downloaded...:S so I connected with wired connection and I managed to download the drivers I needed...
Sorry, I'm kinda new to Ubuntu....:S

---

### Post by TBABill on 2011-03-28
No problem at all. Normally it's a good idea to connect via ethernet during an install, regardless which distro you install. You can do it without being connected, but sometimes updates come out that fix problems with an initial install from an older iso so it's best to do it all at once. Install....then update....then drivers.

---

