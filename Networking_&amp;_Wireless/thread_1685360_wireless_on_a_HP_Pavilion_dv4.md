---
title: "wireless on a HP Pavilion dv4"
date: 2011-02-10
forum: Networking &amp; Wireless
---

### Post by cindyq on 2011-02-10
I installed the latest version of Kubuntu on a friend's HP Pavilion dv4 laptop.  Everything worked - including wireless, at least on my home network.  Unfortunately wireless did not  work once I brought it to my friend's house. We both have FIOS and nearly identical Verizon supplied wireless routers (her's is a bit newer and unlike mine has a white reset button on the front).

I know from perusing the forum that some others have had wireless problems with the Broadcom chip.   In my case wireless worked perfectly at my house and on my network.  Has anyone else who has had a similar problem getting their HP Pavilion to work on more than just one network discovered why or found a solution?

---

### Post by cindyq on 2011-02-11
Still no  wireless so I decided to try a USB wireless adapter that I have long used on a desktop running another distribution (PCLinuxOS).  Turns out that didn't work either. After some googling I found out that this adapter uses a driver - RT2870 - that is not already installed. What luck!  

[http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html](http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html)

---

### Post by cindyq on 2011-02-20
Problem solved.  The wireless worked after I installed PCLinuxOS.

Not a Linux expert by any means so I can't explain why.  

I like Kubuntu - I chose to install it on a Sony laptop because I found the installation of skim (chinese input) to be straightforweard compared to PCLinuxOS, my usual OS.

---

### Post by grahammechanical on 2011-02-20
You do not say how it did not work once your friend took his machine to his house. The fact that it was working in your house shows that it was working.

Of course you need to set up a new connection when at your friend's house. Did this happen? Or was your friend trying to connect to his modem/router using the connection information for your modem/router? The two modems would have different pass phrases.

A new installation of any Linux OS would start off with a blank connection. I bet the wireless on your friend's laptop will stop working when he brings it to your house.

Regards.

---

### Post by cindyq on 2011-02-21
Thank you for the suggestions.

I did in fact try to set up a new connection at my friend's house using her SSID and password.

I briefly summarized what I did in this post on the PCLinuxOS user forum:

[http://www.pclinuxos.com/forum/index.php/topic,87406.0.html](http://www.pclinuxos.com/forum/index.php/topic,87406.0.html)

[]("http://www.pclinuxos.com/forum/index.php/topic,87406.0.html")

---

