---
title: "Cannot activate wifi via hardware on a laptop"
date: 2005-12-13
forum: Networking &amp; Wireless
---

### Post by syroz on 2005-12-13
hi 
i have little problem with the wifi module activation. like u know on laptop you need a switch to activate the wifi. the thing is the button doesn't work under breezy. the strange thing is the other one (sound  nav, messenger) do work. 
i've tried to 

```


echo 1> /...../acpi/asus/wled.


```

but it doesn't work at all. 

can u help me?

thx


laptop asus m5a centrino with intel 2200bg wifi and last version of ipw2200.

---

### Post by CrunchyDoodle on 2005-12-13
I have a notebook with a similar button for WiFi. On mine, the blue light never comes on when I press it, as it does in XP. However, WiFi does work. I need to use a WiFi software tool to see that it's working.

Bye.     :cool:

---

### Post by 23meg on 2005-12-13
Do you get any error messages when you enter the echo command? And did you try doing it with a "sudo" prefix?

---

### Post by syroz on 2005-12-14
nope no error even with the sudo echo no error but no reaction. it's like a gambling game. if i activate the wifi in windows before reboot then it'll be ok until i press fn+f2. it turn off and then there's no way to turn it of. i'm completly lost to this.

---

### Post by ckempo on 2005-12-14
There's an Acer hotkey driver that sounds like it does what you want here: [http://rfswitch.sourceforge.net/]("http://rfswitch.sourceforge.net/")

Don't know any more about it though as my laptop isn't an Acer.

---

### Post by syroz on 2005-12-14
[QUOTE=ckempo]There's an Acer hotkey driver that sounds like it does what you want here: [http://rfswitch.sourceforge.net/]("http://rfswitch.sourceforge.net/")

Don't know any more about it though as my laptop isn't an Acer.[/QUOTE]
Nor do i. i have an asus

---

