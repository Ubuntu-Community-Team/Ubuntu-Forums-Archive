---
title: "Wireless... again"
date: 2006-02-17
forum: Networking &amp; Wireless
---

### Post by dcast on 2006-02-17
Hi, I just bought a gigafast wireless g router and two usb adapters for $29 canadian, anyway I have the hardware setup sort it is working for my windows computer as it just connects without wireless. with the linux box it is wireless but this isnt working. I installed ndiswrapper and the  driver for it as well as ndisgtk which is the front end. When i use ndisgtk it says the driver is installed and hardware present. However when I click "COnfigure Network" i see in the terminal it says "sh: network-admin: command not found" the adapter is recognized as wlan0. i know this through "ifconfig wlan0". Does anyone know how to connect to my router? thanks if you have any ideas. Oh by the way im on ubuntu lite and icewm.

---

### Post by TheIdiotThatIsMe on 2006-02-17
You could try configuring your network through the terminal. Maybe try something like:

```
iwconfig wlan0 **yourkey**
iwconfig wlan0 **yourencyption**
iwconfig wlan0 **youressid**
/sbin/dhclient wlan0
```

EDIT: By any chance that does work, they will be reset on reboot. You can save these settings by:

If you're ndiswrapper does not load up automatically at boot:
```
sudo nano /etc/modules  #add ndiswrapper at the end of the file
```

If you're ndiswrapper DOES load up automatically at boot, or after you've added the line:
```
sudo nano /etc/network/interfaces
```

Add an entry that looks like this:
```
iface wlan0 inet dhcp
wireless-essid XXXXXXXXXXX
wireless-key XXXXXXXXXXX
```

Find the line that starts with **auto** and add wlan0 to it.

Hope this helps :)

---

### Post by dcast on 2006-02-19
ok il try that out but what is an essid? lol I know nothing about networking whatsoever.

---

### Post by dcast on 2006-02-19
ok i looked up essid, also what you said when i used it in the terminal it came up with "unrecognized wireless request." now what should i do?

---

### Post by TheIdiotThatIsMe on 2006-02-22
[QUOTE=dcast]ok i looked up essid, also what you said when i used it in the terminal it came up with "unrecognized wireless request." now what should i do?[/QUOTE]

At which command does it give you the error?

---

### Post by dcast on 2006-02-23
nevermind it is a driver issue. Im taking it back and getting a different one. Thanks for your help anyway though.

David

---

### Post by TheIdiotThatIsMe on 2006-02-23
[QUOTE=dcast]nevermind it is a driver issue. Im taking it back and getting a different one. Thanks for your help anyway though.

David[/QUOTE]

Oh okay, sorry I couldn't help you. I know ndiswrapper doesn't fully work with all cards, but at least it's a step to get some online. At least you wont have to deal with it after you get a new card ;)

---

