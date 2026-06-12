---
title: "Help installing SMC USB Ez Connect g wireless adapter"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by Macslayer on 2010-04-19
Hi, I have Ubuntu 9.10, which I just now installed on my Dell Dimension 3000.  The computer has all of its USB ports working perfectly; tested in Windows.  I plugged in my SMC USB Ez Connect g wireless adapter, and it isn't even recognized by the system.  I used lsusb, and nothing except the USB keyboard and mouse shows up.  Every time I boot or shut down, I get tons of errors saying that it's "unable to enumerate USB device on Port...," then the port number of whichever port I plug the wireless adapter into.  I've tried using ndiswrapper, and have completely installed the Windows drivers using that (which were the same ones that worked perfectly in Windows XP Pro).  I've tried looking into compat-wireless and Linux Wireless, and have successfully installed the zd1211rw drivers and everything.  The drivers install completely and work, there is just no hardware present, or so it says.  
  This is what the terminal says when I type dmesg, and also part of what shows up on booting and shutdown:
[  212.048364] hub 1-0:1.0: unable to enumerate USB device on port 8
[  212.252252] hub 1-0:1.0: unable to enumerate USB device on port 8
[  212.452339] hub 1-0:1.0: unable to enumerate USB device on port 8
[  212.660440] hub 1-0:1.0: unable to enumerate USB device on port 8
[  212.848312] hub 1-0:1.0: unable to enumerate USB device on port 8
[  213.036309] hub 1-0:1.0: unable to enumerate USB device on port 8
[  213.224310] hub 1-0:1.0: unable to enumerate USB device on port 8
[  213.412306] hub 1-0:1.0: unable to enumerate USB device on port 8
[  213.600298] hub 1-0:1.0: unable to enumerate USB device on port 8
[  213.788299] hub 1-0:1.0: unable to enumerate USB device on port 8
[  213.976290] hub 1-0:1.0: unable to enumerate USB device on port 8
[  214.164291] hub 1-0:1.0: unable to enumerate USB device on port 8
[  214.352290] hub 1-0:1.0: unable to enumerate USB device on port 8
[  214.540283] hub 1-0:1.0: unable to enumerate USB device on port 8
[  214.728280] hub 1-0:1.0: unable to enumerate USB device on port 8
[  214.972022] usb 1-8: new high speed USB device using ehci_hcd and address 29
[  215.040297] hub 1-0:1.0: unable to enumerate USB device on port 8
[  215.228314] hub 1-0:1.0: unable to enumerate USB device on port 8
[  215.416311] hub 1-0:1.0: unable to enumerate USB device on port 8
[  215.604304] hub 1-0:1.0: unable to enumerate USB device on port 8
[  215.792307] hub 1-0:1.0: unable to enumerate USB device on port 8
[  215.980298] hub 1-0:1.0: unable to enumerate USB device on port 8
[  216.168297] hub 1-0:1.0: unable to enumerate USB device on port 8
[  216.356292] hub 1-0:1.0: unable to enumerate USB device on port 8
[  216.544421] hub 1-0:1.0: unable to enumerate USB device on port 8
[  216.732415] hub 1-0:1.0: unable to enumerate USB device on port 8
[  216.920289] hub 1-0:1.0: unable to enumerate USB device on port 8
[  217.108282] hub 1-0:1.0: unable to enumerate USB device on port 8
[  217.296282] hub 1-0:1.0: unable to enumerate USB device on port 8
[  217.484275] hub 1-0:1.0: unable to enumerate USB device on port 8
[  217.728024] usb 1-8: new high speed USB device using ehci_hcd and address 43
[  217.796293] hub 1-0:1.0: unable to enumerate USB device on port 8
[  217.984313] hub 1-0:1.0: unable to enumerate USB device on port 8
[  218.172310] hub 1-0:1.0: unable to enumerate USB device on port 8
[  218.360309] hub 1-0:1.0: unable to enumerate USB device on port 8
[  218.552298] hub 1-0:1.0: unable to enumerate USB device on port 8
[  218.740295] hub 1-0:1.0: unable to enumerate USB device on port 8
[  218.930989] hub 1-0:1.0: unable to enumerate USB device on port 8
[  219.123865] hub 1-0:1.0: unable to enumerate USB device on port 8
[  219.312283] hub 1-0:1.0: unable to enumerate USB device on port 8
[  219.500279] hub 1-0:1.0: unable to enumerate USB device on port 8
[  219.696270] hub 1-0:1.0: unable to enumerate USB device on port 8
[  219.892262] hub 1-0:1.0: unable to enumerate USB device on port 8
[  220.096377] hub 1-0:1.0: unable to enumerate USB device on port 8
[  220.340020] usb 1-8: new high speed USB device using ehci_hcd and address 56
[  220.408252] hub 1-0:1.0: unable to enumerate USB device on port 8
[  220.596273] hub 1-0:1.0: unable to enumerate USB device on port 8
[  220.784272] hub 1-0:1.0: unable to enumerate USB device on port 8
[  220.972259] hub 1-0:1.0: unable to enumerate USB device on port 8
[  221.160264] hub 1-0:1.0: unable to enumerate USB device on port 8
[  221.348257] hub 1-0:1.0: unable to enumerate USB device on port 8
[  221.536256] hub 1-0:1.0: unable to enumerate USB device on port 8
[  221.728396] hub 1-0:1.0: unable to enumerate USB device on port 8
[  221.916246] hub 1-0:1.0: unable to enumerate USB device on port 8
[  222.104389] hub 1-0:1.0: unable to enumerate USB device on port 8
[  222.292244] hub 1-0:1.0: unable to enumerate USB device on port 8
[  222.480232] hub 1-0:1.0: unable to enumerate USB device on port 8
[  222.668371] hub 1-0:1.0: unable to enumerate USB device on port 8
[  222.856362] hub 1-0:1.0: unable to enumerate USB device on port 8
[  223.044222] hub 1-0:1.0: unable to enumerate USB device on port 8
[  223.288023] usb 1-8: new high speed USB device using ehci_hcd and address 71
[  223.357373] hub 1-0:1.0: unable to enumerate USB device on port 8
[  223.551765] hub 1-0:1.0: unable to enumerate USB device on port 8


I hope I've given enough information.  Oh, and I downloaded Ubuntu a few days ago from their website, burned to a CD-R, installed, and downloaded all updates that it asked me to.  Other than that and the ndiswrapper and driver installation, I've done nothing on the system.

I just want the bloody thing to work.

---

### Post by Macslayer on 2010-04-24
Oh, and the wireless adapter worked perfectly on the same desktop with Windows XP, so the only difference is the operating system... I have no idea what the problem could be, though, because others have gotten it to work in Ubuntu before...

---

