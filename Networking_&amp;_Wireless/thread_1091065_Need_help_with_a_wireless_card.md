---
title: "Need help with a wireless card"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by freddie3782 on 2009-03-09
have a Belkin N Wireless notebook card with part # F5D8013 Tried use it with Ubuntu 8.10, Tried to use ndiswrapper by using "sudo apt-get install ndiswrapper-utils" and "sudo apt-get install ndiswrapper" none worked. Terminal stated (E: Couldn't find package ndiswrapper) How do I use my wireless card on my Toshiba Tecra 8100 with ubuntu 8.10? Some one help please. Want to rid myself of my dependence on windows.HELP!

---

### Post by agim on 2009-03-09
The reason you got that error message is that apt is trying to download ndiswrapper from the internet. You, of course, are not connected. Which is why it can't find what it is looking for.

I will look here in the forums and google to see if I can help you. I have never used belkin before.

How are you online now? Are you using another computer, or did you plug in the computer with the belkin card? (I'm guessing the former, because the apt error message says that you are not connected.)

---

### Post by agim on 2009-03-09
[http://www.ubuntukungfu.org/blog/2008/11/make-almost-any-wifi-card-work-with-ubuntu/](http://www.ubuntukungfu.org/blog/2008/11/make-almost-any-wifi-card-work-with-ubuntu/)

This looks like a pretty good all purpose site. I am kind of surprised that belkin doesn't work out of the box. Maybe someone could shed some more light?

Are you sure you are using ubuntu 8.10?

---

### Post by freddie3782 on 2009-03-13
yes I am using ubuntu 8.10 I downloaded it from the website
And I have it on a partition on my daily laptop which has a 
integrated wireless hardware. Ubuntu found the driver I needed for this and installed it no problem. but the toshiba is the one I cant get to work. it is an older model but I also installed ubuntu on a old dell desktop and it worked fine.

Thank you for the link to the guide.
will read it know it will help.

---

### Post by klafilin on 2009-03-14
Hi freddie, I am trying to solve the same Problem. To download and
install the ndiswrapper I used the following command:
sudo apt-get install ndiswrapper-common
This worked for me, but still didn't get the wireless going just jet.
Good luck for you.

---

