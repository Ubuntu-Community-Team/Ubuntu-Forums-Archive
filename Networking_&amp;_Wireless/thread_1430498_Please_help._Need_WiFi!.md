---
title: "Please help. Need WiFi!"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by JDuBZisFADED on 2010-03-15
I own a WUSB300n from linksys. I am using ubuntu 9.10. I have followed this tutorial on the second post [http://ubuntuforums.org/showthread.php?t=530772](http://ubuntuforums.org/showthread.php?t=530772) to the t and my connection constantly falls and requires me to restart and reload driver to get connection back. I have heard that the drivers for D-Links DWA-142 (1.20BETA)work from this thread [http://ubuntuforums.org/showthread.php?t=499758](http://ubuntuforums.org/showthread.php?t=499758) on the fourth post. My problem is how do i extract the data1.cab,data1.hdr, and data2.cab from the drivers. I have tried to use wine (didnt work) also cabextract and unshield fail. I have also tried i6comp from windows and that basically tells me my installshield .cabs are too new. Please can anyone help me to extract the .cabs from either windows or good old ubuntu.

---

### Post by JDuBZisFADED on 2010-03-15
i have a feeling the only way i can get a response is to bump. please please help me out. i want to keep ubuntu as my main os but cant without internet!

---

### Post by pastalavista on 2010-03-15
Have you installed the 'wireless-tools' package from the repositories? I didn't think you needed special drivers for Linksys USB sticks. Was it plugged in when you installed Ubuntu? Did it work on the Live CD? Those posts you followed were 4 years old. (7 or 8 releases ago)

---

### Post by pastalavista on 2010-03-15
I guess I was wrong...  I found [this more recent information]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#USB") though (scroll down a little for your card)

---

### Post by JDuBZisFADED on 2010-03-15
yes to all ur questions. wireless tools is installed aka ndiswrapper. i just need to know how to extract .cab files from those drivers. anyone know how to extract a new installshield cab?

---

### Post by pastalavista on 2010-03-15
7zip will extract cabs, in the Software Center or```
sudo apt-get install p7zip-full
```

---

### Post by JDuBZisFADED on 2010-03-15
> **pastalavista said:**
> 7zip will extract cabs, in the Software Center or```
sudo apt-get install 7zip
```

i thank you much for your suggestions but i have tried in 7zip and archive manager and its a no go. i dont think your recognizing the problem. newer .cabs from installshield have certain dependencies. my file setup is data1.cab data1.hdr and data2.cab. i want all the files from both those cabs

---

### Post by cake nom nom on 2010-04-01
maybe this can help

[http://wifi-radar.berlios.de/](http://wifi-radar.berlios.de/)

---

