---
title: "Can't get wireless working on Dell Latitude 630"
date: 2012-08-17
forum: Networking &amp; Wireless
---

### Post by johnfromberkeley on 2012-08-17
I am a total ubuntu noob. Not command line friendly, trying to embrace free OS. I have tried googling the forums extensively, but all of the posts I found are too complicated for me to understand.

When I go to my hardware additional drivers, it says that the Broadcom STA driver is activated and currently in use.

But, I don't see any wifi networks.

Help!

---

### Post by Finnicella on 2012-08-17
Hi, 
did you have Ubuntu in dual boot with windows?
Please give me the output of these commands:
```
iwconfig
```
```
sudo rfkill list all
```
```
lspci -nn | grep -i net
```
and
```
sudo lshw -C network
```
I'm not expert, but I try to hel you.
Bye and sorry for my english. :D

---

### Post by OM55 on 2012-08-17
Hello johnfromberkeley,

1. Did you confirm that 'Wireless' and 'Networking' is enabled?
(Click on the wireless icon and verify that both options are checked).

2. Can you confirm that your wireless router is up and running? (can you see wireless networks on another device? smartphone? tablet?)

3. Did you make sure that you are close to the router so wireless reception issues will be a concern?

4. Does your laptop has a hardware button or hotkey to disable/enable the wireless radio? It is common in many laptops. If so, it is possible that you inadvertently turn the wireless radio off and that's why no wireless networks are visible.
As far as I could see in the online manual of Dell Latitude 630, there is a wireless on/off switch on the left side panel, which could be simply turned off. When it is on, the front display with the 'Wi-Fi' logo should be  lit.

(If in your case it is a hotkey, you would normally have a "Fn" key or similar, that when press it with combination with another key (usually one of the function keys at the top of the keyboard) would do something else, like increase/decrease volume, increase/decrease screen brightness and others. One of those functions would also be turn the wireless radio on/off (to save battery power). So make sure it is on, or simply try different positions.)

Usually it takes a few seconds after startup before the wireless driver is activated and starts looking for wireless networks.

Lets start with the above tests, report back here and if none of the above helped, we'll continue.

---

### Post by johnfromberkeley on 2012-08-17
Hey, guys, thanks for your replies.

I actually ~removed~ the broadcom driver, and then it started working!

Thank you so much for your willingness to help!

---

### Post by Finnicella on 2012-08-17
You are welcome, I'm very happy that it works now.
Bye:)

---

