---
title: "Dell Hotkeys Problem"
date: 2010-02-22
forum: Networking &amp; Wireless
---

### Post by Whisp3r on 2010-02-22
I have a Dell 14Z, dual boot Windows Vista and Ubuntu. I use the Ubuntu 99 percent of the time, and basically use the windows only when I'm presenting since Linux doesn't like to play well with projectors in my experience. 

The problem I'm encountering is when I accidently hit the wireless on/off hot key, it disables wireless. When I hit it again, it does not en-enable it. It disables wireless completely, and no matter how much I poke and prod it with ifconfig and so forth, I can't get my wireless to come back on. The only way I have gotten it to return to service is to boot into windows, hit the hot key, and reboot back to Linux. 

Any suggestions? At the very least, is there anyway to kill these hot keys I never use?

---

### Post by chili555 on 2010-02-23
Is the driver module *dell-laptop* loaded?```
lsmod | grep dell
```Does it help to remove it?```
sudo rmmod -f dell-laptop
```Or maybe to remove it, get the wireless going and re-insert it?```
sudo rmmod -f dell-laptop
```Fn+Fwhatever_the_wireless_key_is```
sudo modprobe dell-laptop
```

---

### Post by Whisp3r on 2010-02-24
Removing the hot keys doesn't do any good. I still can't reactivate my wireless. It acts as if I have no networking period. How do I restart my wireless manually?

I tried an /etc/init.d/networking stop/start, and when I run ifconfig, all my connections are there, but Network Manager still doesn't show any networks to connect too. :( It almost seems the problem lays within Network Manager?

I tried rebooting after restarting networking, and the wireless aspect is still dead. The only way I have to restart the wireless is through Windows. And that isn't too pleasant of a solution. The other solution I have found is to plug another wireless card (USB) in, which seems to kick the internal card in the butt and say "Wireless is working again, lets go!"

---

