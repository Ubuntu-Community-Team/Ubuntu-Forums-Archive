---
title: "Need Viagra for PPP"
date: 2006-05-03
forum: Networking &amp; Wireless
---

### Post by DiGiTY on 2006-05-03
I'm trying to use my cell phone (Samsung A900) as a dial up usb modem. I set it up running 'wvdialconf' and also got the modem port (/dev/ttyUSB2). I plugged in that info to into the ppp0 section of the Networking applet under Administration. I hit active, it dialed up and connected but for some reason I couldn't switch the gateway from eth0 to ppp0. I even had the 'default as gateway' feature enabled in ppp0 settings. As a result, I couldn't get on the Internet and the connection also dropped about a minute later.

How do I switch the gateway to the modem's Internet connection and how do I get it to stay up (the connection... pervs)???

---

### Post by szweda83 on 2006-09-06
Do this dude!
mothersuperior@mshome:/etc/ppp/peers$ sudo gedit wvdial
Copy & paste this into the file your editing
defaultroute # use the cellular network for default route
usepeerdns # use the DNS servers from remote network
nodetach # keep pppd in the foreground
crtscts # hardware flow control
lock # lock the serial port
lcp-echo-failure 4
lcp-echo-interval 65535
noauth # don't expect the modem authenticate itself



I love linux ... But configuring devices can sometimes be frustrating;)

---

