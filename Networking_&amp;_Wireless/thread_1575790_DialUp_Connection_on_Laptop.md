---
title: "DialUp Connection on Laptop"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by sabajamalian on 2010-09-16
Hi all

I have a Dell, XPS 1330 and recently I have installed Ubuntu10.4. The only problem I`m facing right now is with my internet connection which is on a dial up external usb modem.
How can I configure it ?!

Thanks in advance

---

### Post by grahammechanical on 2010-09-16
Open a terminal Applications >Accessories >Terminal. Code
```
sudo pppconfig
```
You will need to enter your log-on password. A little ulitity will load. Follow the directions. 
if you leave the provider set as provider then typing sudo pon in a terminal will cause the modem to dial the ISP and sudo poff will disconnect.

You will need to have your ISP username and password, as well as the telephone number of your ISP. Set the speed to 115200, the COM to /dev/ttyS0 (that is the number 0, not the letter o), the authentication method is PAP and nameservers should be set to dymanic.

Regards

---

### Post by sabajamalian on 2010-09-17
Thank you very much for your reply.

I did exactly what you said and the new connection was made but when I enter "sudo pon" in my terminal, nothing happens.

Do you think it is because that the driver of my external modem isn`t installed?!
If yes, how should I install it?

Thanks again, and sorry because I`m really new in ubuntu.

---

