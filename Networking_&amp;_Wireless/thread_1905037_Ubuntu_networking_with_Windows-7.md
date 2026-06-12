---
title: "Ubuntu networking with Windows-7"
date: 2012-01-05
forum: Networking &amp; Wireless
---

### Post by algrossi on 2012-01-05
I have stumbled again. I am trying to link my Ubuntu laptop with a Windows-7 laptop. I shared my folder on the Ubuntu machine and then rebooted both machines. The Window machine displays the Ubuntu laptop but when I click on it, it tells me "Windows cannot access \\Ubuntu-laptop". Then there are options to diagnose the problem but that leads me into confusion...
I have read all the material I could find on this subject but none of it is cohesive, so I may be left with some patchwork of settings which are causing the issue. Does anyone have an idea how this could happen in a simple fashion? I also tried using Samba server on Ubuntu but that proved more complex.
Al

---

### Post by 2F4U on 2012-01-06
Samba is the way to go if your Windows machine should access files and folders on Ubuntu:

[https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html)
[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

---

### Post by algrossi on 2012-01-06
I've been hammering away with Samba for a while and didn't get very far, but these two links are quite specific so I will follow them. I think the reason the connection is inconsistent is because of the dynamic IP allocation from the wireless router. From what I remember, the /etc/hosts needs to resolve IP to hostname. This will be messy when the router assigns IP addresses on a first-come-first-served basis. In addition to the two links you provided, I will experiment with static IP and see if two laptops can get along and share.
Thank you
Al

---

### Post by Pat201 on 2012-01-07
Hey Al, if you've just got the two machines, just go into your router and assign both your machines a static IP address and then put those addresses in both your laptops statically.  That'll keep your resources in one place and you won't lose the address if you shut down one of your machines for a period of time longer than the DHCP lease time.  

Doh!  Rereading your message, I see you said you will experiment with static IP.  :redface:  That should get rid of your problems.

---

### Post by rsvancara on 2012-01-07
If your router supports this, for your MAC address, you could associate an IP address so that you are always given the same address on the network.

---

