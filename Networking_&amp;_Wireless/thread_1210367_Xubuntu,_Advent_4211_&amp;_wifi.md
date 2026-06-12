---
title: "Xubuntu, Advent 4211 &amp; wifi"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by Evertb on 2009-07-11
Hello,

I've just installed Xubuntu on my Advent 4211 netbook.
Install went fine but I cannot get it to detect my wifi network. Other OS's installed on the netbook detect the wifi network no problem so it must be an issue with Xubuntu. 
has anyone here got pointers on what I should look at?

E.

---

### Post by prshah on 2009-07-11
> **Evertb said:**
> 
but I cannot get it to detect my wifi network.

How far along have you got? Is the wireless hardware detected? Try the following commands in the terminal (Applications-Accessories-Terminal) for more information```
iwconfig
sudo iwlist wlan0 scan
``` and post back the output for further explanation. Replace wlan0 with the correct interface name which will be indicated by the iwconfig command.

---

### Post by Evertb on 2009-07-11
OK, thanks. 
Result as follows:
[I]
"wlan0 No scan results"[/I]

Any suggestions?

---

### Post by superprash2003 on 2009-07-11
many wifi cards come with wireless switches , make sure that the switch in your wifi card is ON

---

### Post by Evertb on 2009-07-11
The wifi is internal so I do not see how I could switch it on OR off....

---

### Post by prshah on 2009-07-12
> **Evertb said:**
> The wifi is internal so I do not see how I could switch it on OR off....

Fn+F11.. you may have to toggle it a few times until the WiFi light comes on; apprently bluetooth and WiFi share the same toggle switch.

And here's a useful resource for you: [http://wiki.msiwind.net/index.php/Ubuntu_9.04_Jaunty_Jackalope](http://wiki.msiwind.net/index.php/Ubuntu_9.04_Jaunty_Jackalope)

---

### Post by Evertb on 2009-07-12
@prshah Thanks, that did the job nicely! Just wonder why Xubuntu would disable the wifi as default...

---

### Post by hansdown on 2009-07-12
Hi Evertb.

I just bought the wind, which is pretty much the same.

The best place for answers is on the wind forums.

[http://forums.msiwind.net/](http://forums.msiwind.net/)

Most of the folks there have advents and winds running mostly linux.

Check it out and have fun!

P.S. It took me awhile to learn about the FN+F11 keys.

---

