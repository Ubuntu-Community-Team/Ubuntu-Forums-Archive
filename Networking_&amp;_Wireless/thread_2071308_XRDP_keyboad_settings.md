---
title: "XRDP keyboad settings"
date: 2012-10-15
forum: Networking &amp; Wireless
---

### Post by tweetysat on 2012-10-15
Hello.

I'm using ubuntu 12.04 in french with belgian keyboard.
I have installed xrdp 0.5.0-2.

First connection using windows 7 remote desktop.  In the login screen the keyboard is us.  In the console, the keyboard is also us.

So I tried :
setxkbmap -layout be
sudo cp km-0409.ini km-0409.ini.bak
sudo xrdp-genkeymap km-0409.ini

Ok, now in the login screen the keyboard is belgian.  The numeric keypad is working and also the alt-gr keys.  But in the console the numeric keypad  and  the alt gr keys are not working.
What can I do ?

Thanks.

---

