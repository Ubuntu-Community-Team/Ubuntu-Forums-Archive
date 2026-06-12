---
title: "wireless works with Live CD session but not without it"
date: 2010-06-30
forum: Networking &amp; Wireless
---

### Post by aleche on 2010-06-30
Hi Everyone,
I am very new to this and tried searching for this problem in the forums but have not find anything.  When I installed ubuntu (formatted HD), the installer gave an error but then seemed to proceed as normal and everything installed (from CD).  However, when I boot up from Live CD all my wireless works fine (it detects networks, connects, etc.)  When I boot up without the CD it says networking disabled and gives me no other options.  Anyone know how to fix this?

Much appreciated.

Alex

---

### Post by snowpine on 2010-06-30
Welcome to the forums Alex! A good first step is to figure out which wireless network card you have. If you are not sure, open a terminal (under Applications, Accessories), copy & paste the following code, then copy & paste the output back here on the forums so we can help you:

```
lspci | grep Network
```

---

### Post by aleche on 2010-06-30
Thank you for your prompt response!

Network controller: Intel Corp. PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

---

### Post by snowpine on 2010-06-30
I am not familiar with the Intel wireless cards, unfortunately. :(

But here are some basic things you can check:

1) Is the card physically connected, no loose wires?
2) Is the card enabled in your BIOS?
3) Is there a key combination you can press (mine is Fn+F2) to toggle wifi on and off? 
4) When you right-click on the Ubuntu Network Manager Icon (on your panel), verify that the Enable Networking and Enable Wireless options are checked.
5) Go to System, Administration, Hardware Drivers to see if any additional drivers are required/available.
6) Use UbuntuForum's Search feature to find other users with this specific card.

Good luck! Sorry I don't have personal experience with that card, but finding out the model number was a good first step. :)

---

### Post by aleche on 2010-06-30
Ok! Thank you for trying.  For those who may read this and follow up I post the following answers:
The problem was Fn + F5 to turn on wireless.  not sure why this was turned on automatically with the CD in there but thanks for your help!

Alex

---

