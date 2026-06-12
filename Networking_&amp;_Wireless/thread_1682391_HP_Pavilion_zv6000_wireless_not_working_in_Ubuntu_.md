---
title: "HP Pavilion zv6000 wireless not working in Ubuntu 10.10"
date: 2011-02-05
forum: Networking &amp; Wireless
---

### Post by Rikeshar on 2011-02-05
Hello everyone. I've searched the forums and the link to getting this works is no longer working, and refers to a version ubuntu older thatn 10.10....


Anyone know how to get an HP Pavilion zv6000 working with Ubuntu 10.10? It shows that the firmware isn't loaded, but I'm not sure where to find it. I'm new to Linux, so please go easy on me! Please help!

Wired isn't an option, since I don't have an ethernet cable long enough, but I have a windows system I can download from.

---

### Post by VetterZor on 2011-03-11
I too have the same laptop and the same problem. Maybe I should just go back to Vista. LOL heck no. know come on you Linuts help us noobs out. I tried all the fixes on the forums to no avail. What is the answer? reformat install Windows?

---

### Post by grahammechanical on 2011-03-11
The best I can do for you is this link:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

When the page is open, go to the link Device Drivers. When that page opens look for the link that says full information on ndiswrapper kept on this page. When the page opens scroll down and look for the headings Installing Packages (without Internet Access) and Downloading Windows Drivers.

You should slowly read the whole document. It is best to have a wired connection to solve this problem but the other way is to get the drivers you need onto a CD and install them from there. The document gives you a method for doing that.

Regards.

---

### Post by Altay_H on 2011-06-03
There's a better solution. All I had to do was install the following two packages:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

This should work assuming you have a BCM4306 (rev 3) card. If you're not sure, you can run:
```
lspci | grep Net
```

More information can be found here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)

---

### Post by section128drunk on 2011-07-11
thanks, this worked for me on 11.04

---

### Post by pixelpadre on 2012-03-10
Worked for me too.  Although finding a terminal screen took quite some time.

---

