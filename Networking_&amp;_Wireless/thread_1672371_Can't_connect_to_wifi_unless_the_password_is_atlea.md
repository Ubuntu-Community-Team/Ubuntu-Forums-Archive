---
title: "Can't connect to wifi unless the password is atleast 8 characters long?"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by Blue Dolphins on 2011-01-20
When I need to type in the password to get on a wifi network, the "connect" button is grayed out and unclickable until I've typed in 8 characters for the password, making it impossible to connect to networks with shorter passwords.  I'm not sure if this problem is unique to 10.10 or not, I've been using linux for a couple years now and  I've never tried to connect to a network with such a short password before until last weekend, after my friend figured out how to change his password from the one his ISP set for him.  

I'm running Xubuntu 10.10 on an IBM T42 laptop, here's the relevant hardware from the lspci command,

02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

---

### Post by grahammechanical on 2011-01-21
There is a reason why the minimum is set to 8 characters. It makes the password more difficult to decipher. Linux is helping you secure your data. What Operating System is your friend using? Did he also change the encryption method? Perhaps the failure to connect is due to your machine being set to a different encryption method?

Regards.

---

### Post by Blue Dolphins on 2011-01-21
he changed it from a 10 digit number to a word straight out of the dictionary, which obviously would be **** easy to crack with a dictionary attack, but you try reasoning with computer illiterate people that think defragging their harddrive will remove viruses.  He's using Windows XP.  I'm not sure if he changed the encryption method.  I just tried changing the encryption to WEP from WPA and it allowed me to type in the password.  I haven't actually tried connecting yet as I'm in another state right now, I just have his wifi network saved in VPN connections.  So I'm thinking he just changed the encryption and didn't tell me.

I'm pretty sure that's what the problem is, I'll post back when I go over there this weekend and can try again.

---

### Post by Blue Dolphins on 2011-02-02
Sorry it took so long to get back.

I tried again with no success.  I can set the encryption method in VPN connections, but when I try to actually connect and have to type in the password my only option is WPA, which it can't be since a WPA password must be 8 digits long.  If it can't be WPA, then why is it the only available option?

Is it possible to force another encryption method(or none at all) through the command line or by editing text configuration files? So I can just keep trying different encryptions until I find the correct one.

---

### Post by AlexQM on 2011-02-02
Sorry, are you trying to connect to a wireless network with a VPN!?

> I can set the encryption method in VPN connections, but when I try to actually connect and have to type in the password my only option is WPA, which it can't be since a WPA password must be 8 digits long. If it can't be WPA, then why is it the only available option?

A VPN connection will allow you to transfer data (and other things) to a machine that isn't on your private network. 
e.g. Remotely connect to your work's network from your home machine

---

### Post by Aervanath on 2011-11-16
> **Blue Dolphins said:**
> When I need to type in the password to get on a wifi network, the "connect" button is grayed out and unclickable until I've typed in 8 characters for the password, making it impossible to connect to networks with shorter passwords.  I'm not sure if this problem is unique to 10.10 or not, I've been using linux for a couple years now and  I've never tried to connect to a network with such a short password before until last weekend, after my friend figured out how to change his password from the one his ISP set for him.  

I'm running Xubuntu 10.10 on an IBM T42 laptop, here's the relevant hardware from the lspci command,

02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

I had this exact same problem with a coffee shop where the password was only six characters long. I got around it by pointing my web browser directly at the IP address of the router. This displayed an html page with a password-entry box, after which my laptop connected automatically. (EDIT: I found the router IP by connecting to the network via my iPhone, then looking in Settings->Wi-Fi for the details of that network.)
Your mileage may vary; I did this using:
Web browser:Chromium 14.0.835.202 (Developer Build 103287 Linux)
OS: Lubuntu 11.10
Hope this helps.

> **grahammechanical said:**
> There is a reason why the minimum is set to 8 characters. It makes the password more difficult to decipher. Linux is helping you secure your data.

Respectfully, while helping to secure users' data is a worthy goal, it would be better to let users decide how much security they need than arbitrarily blocking you from accessing a network based on password length. Just my way of thinking.

---

