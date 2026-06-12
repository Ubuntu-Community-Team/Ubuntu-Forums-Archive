---
title: "Wrt54gs"
date: 2009-09-19
forum: Networking &amp; Wireless
---

### Post by Merrib64 on 2009-09-19
[B]How do I install this wireless router under Ubuntu 9.04. I am at a complete loss.
I have a Cable modem with internet and the router is good. Any help will be
appreciated.

Bob[/B]

---

### Post by jefnert on 2009-09-19
Are you just trying to figure out how to setup the wireless on the router?

If so you will need to plug the cable coming from the cable modem into the internet port on the back of the Wrt54g.  Then plug a network cable from the Wrt54g to the network port on your laptop or desktop. It should assign an ip with dhcp to your computer. 

then access the wrt54g setup via a web browser usually using 192.168.1.1.  You might have to search the internet for the default password for the wrt54g.  Right now I cant think what it is.

Once you get into the setup you will need to configure the wireless information.

Hope this helps.

---

### Post by tgalati4 on 2009-09-19
In addition to what jefnert said:

You need to turn the wireless radio on.

Choose an SSID--a network name that is useful to you

Choose a security model:  Open, WEP, WPA (best)

Pick a useful passphrase that generates a security key.  Write this key down somewhere.  You will need it when you log in (once) with wireless.

---

### Post by kevdog on 2009-09-20
I'm not going to be a smartass, however the installation of this modem is the exact same as in windows.  Just plugin the power and connect it to your cable modem and then connect the computer.  Turn your browser to [http://192.168.1.1](http://192.168.1.1) to login to the configuration screen.  

That's about it!

---

### Post by Merrib64 on 2009-09-20
Many thanks to those that responded, with your help I managed to get up and running.

Bob

---

