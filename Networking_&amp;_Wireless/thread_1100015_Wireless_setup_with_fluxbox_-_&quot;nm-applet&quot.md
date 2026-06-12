---
title: "Wireless setup with fluxbox - &quot;nm-applet&quot;"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by 4dplane on 2009-03-18
Hi,

I am using Ubuntu with Fluxbox installed to control my desktop. I am using a wireless card and I am having troubles getting it to work. Looking around the web I see that I must use nm-applet inside of my startup script - which I am. I then go to fluxbox's KNetworkManager and select my network and put in my network key. But I do not have a connection. I know the web is fine because I can log into a regular account and get on the wireless just fine; so what am I missing with fluxbox and how it controls wireless connections

After all this I type ifconfig and I do not have an ip; it looks just as it did before I used the KNetworkManager.

Also if I do an ifup wlan0 it says Ignoring unknown interface wlan0=wlan0

What else can I do?

Thanks,
4dplane

---

### Post by kerry_s on 2009-03-18
nm-applet is gnome
knetworkmanager is kde

you can not run more than 1 network manager.
fluxbox does not have a network manager.
if you have nm-applet in your startup than you should get a icon on the panel and you use that to set up the network.

---

### Post by 4dplane on 2009-03-18
Thanks kerry_s,

that helps! When you say the nm-applet shows up in the panel; what panel do you mean - right click menu or toolbar?

Thanks,
4dplane

***
so why can't I use knetworkmanager inside of fluxbox? It's in the fluxbox menu.

---

### Post by 4dplane on 2009-03-18
Ah, got it working with knetworkmanager after I got ride of nm-applet in my startup script.

Don't know why nm-applet is not wroking; when I type nm-applet in a terminal I get this reply:
"WARNING **: No connection defined"

But knetworkmanager will do the job fine.

Thanks kerry_s, you took me over the top!

---

### Post by kerry_s on 2009-03-18
> **4dplane said:**
> Ah, got it working with knetworkmanager after I got ride of nm-applet in my startup script.

Don't know why nm-applet is not wroking; when I type nm-applet in a terminal I get this reply:
"WARNING **: No connection defined"

But knetworkmanager will do the job fine.

Thanks kerry_s, you took me over the top!

add>
 
kmix &
knetworkmanager &

to your fluxbox startup since your base system is kde.

---

### Post by Lesseps on 2011-01-12
> **kerry_s said:**
> nm-applet is gnome
...
you can not run more than 1 network manager.
fluxbox does not have a network manager.
if you have nm-applet in your startup than you should get a icon on the panel and you use that to set up the network.

Thanks Kerry,

Each line above helped me very much!

---

