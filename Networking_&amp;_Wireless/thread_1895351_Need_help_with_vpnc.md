---
title: "Need help with vpnc"
date: 2011-12-14
forum: Networking &amp; Wireless
---

### Post by danielsender on 2011-12-14
Hi,

At work they set up a vpn cisco machine. They also provide a web page that after entering some validation dialogs, it inserts a certificate on the windows machine where the web page is being opened. They also provide the executable of the cisco client that in turn uses that certificate. I would like to run vpnc on my ubuntu 11.10 machine to replace the windows machine. So here is what I did:

1. I opened the certificate page on windows and exported the certificate in ".cer" format that is a bunch of ASCII lines.

2. I opened the client version on the windows machine to see some of the settings and try to reproduce them in the vpnc gui, such as the UDP option. I also imported the certificate that I got from the windows machine into vpnc.

3. After I click on "save" I also click on the connection and immediately after it comes back with the "failed" message. On the other hand if I use a terminal and type "sudo vpnc" entering the IP as well as my username and password, it comes back with the message "vpnc: no response from target", which takes a few seconds more that what the "failed" message takes when I use the gui.

I would appreciate any help.

Daniel

---

