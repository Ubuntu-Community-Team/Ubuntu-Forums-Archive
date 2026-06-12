---
title: "network-manager-gnome expert needed"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by linuxNewb on 2006-07-13
Step1: I apt-getted network-manager-gnome, no problems
Step2: I ran Alt-F2, then nm-applet, it appears on panel
Step3: I openned network manager and disabled eth0 and eth1
Step4: I commented out everything but lo in /etc/network/interfaces
Step5: I rebooted

I can now see a bunch of wireless networks appear when I click on the nm-applet. When I select my ssid then enter my WEP key, it just won't connect to my network!!! All available wireless networks are locked (encrypted), so I can't troubleshoot by connecting to an unprotected network. I don't think that's the problem anyway.

The original network manager applet is still running, and shows a strong wireless signal even though eth1 (wireless connection) shows as 'not configured' when I click 'configure' on the original network manager applet. I'm thinking that somehow the original network manager is trying to run the show, and preventing the new network-manager-gnome from actually connecting to a network, but I could be wrong.

Please help. Thanks in advance. Note: specs below in signature.

---

### Post by orb9220 on 2006-07-13
Do forum search on yer Linksys WPC11 v3 pcmcia. I think if my brain is booted 
this morning that I have seen multiple threads on this.

---

### Post by linuxNewb on 2006-07-14
I have done this with no solutions found. It is scanning fine and detecting available wireless networks it just won't connect.

---

