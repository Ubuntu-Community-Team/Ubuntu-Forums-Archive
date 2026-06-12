---
title: "Openbox ubuntu wifi manager - how to?"
date: 2013-04-02
forum: Networking &amp; Wireless
---

### Post by navoye on 2013-04-02
Hi!
I getting problems from wpa-supplicant(i think) - my card sometimes work great after power up system but when i restart my system it hangs for a while during loading os (waiting for network configuration). After that sometimes wifi work, sometimes doesnt. When i keep restarting usualy it start working without a reason - just few restarts, sometimes power down - power up and works. I was getting mad with that(esspecialy that sometimes i need to remote reboot this mashine and i never sure if it comes up) so i deciced to do someting with this - i read many things on forum/google and tried(etc networking restart) but nothing help me. I read about network manager and i think this is it - but i cant get it to work - allways something wrong. I use specyfic build system with openbox, so next i'll present how my system is build:

Ubuntu server default installation with server ssh and next:
```
aptitude install xserver-xorg xserver-xorg-core  xserver-xorg-input-evdev xserver-xorg-video-ati lightdm unity-greeter  openbox roxterm echo 'export DISPLAY=:0' >> ~/.bashrc aptitude install build-essential dkms unzip aptitude build-dep fglrx 

  
```
I add auto-login to /etc/lightdm/lightdm.conf

```
[SeatDefaults] greeter-session=unity-greeter user-session=openbox autologin-user=my_username autologin-user-timeout=0 


```
and add my user to login without a password
```
usermod -a -G nopasswdlogin my_username 
 
```
after that reboot

I know it's specific and may look strange but this is what i need.

Can someone please tell me how to add something like tray with some kind of wifi manager which could store password and auto conect after login? It would be nice to remove unnecessary packages from system (i guess wpa-supplicant and some build in network manager) and change it to something that works like network manager for gnome. 
Step by step instruction will be nice - im learning but for this moment im frustrated.

---

### Post by Irihapeti on 2013-04-02
Which version of Ubuntu server are you using?

---

### Post by navoye on 2013-04-03
sorry, forgot to write - im using ubuntu server 12.04 with kernel 3.2

---

### Post by Irihapeti on 2013-04-03
Good, since I'm running 12.04 myself.

wpasupplicant is a dependency of Network Manager and also Wicd, so you won't be able to uninstall it. If it's misbehaving, that suggests that something else is faulty - maybe your wireless card or even the way your router is set up. Fixing that is probably beyond my abilities.

But regard your question about installing Network Manager. I use Openbox with Tint2 as a taskbar and Network-manager-gnome. (It's not actually a server install, but I think that shouldn't make any difference.) When you install, use
```
apt-get install --no-install-recommends <package>
```
or
```
aptitude -R install <package>
```

That stops all the recommended packages from being installed, which is a lot of stuff that's not needed. This way, only the bare minimum of Gnome libraries get installed.

I can't remember at the moment if Tint2 needs to have its system tray enabled or if it works out of the box.

---

### Post by navoye on 2013-04-03
Thank You very much - ill try it after i go back home. You said about router and network card - I'm 100% sure about router (i use it all the time, but with windows. Never have problem, to be honest i'v got 2 diffrent routers, two diffrent ssid and and one is wpa, second wpa2 - problem is no matter witch one i tried to use). But i'm wondering is this could be problem with initate usb network card - my card is tp-link tl-wn422g ver.2.4 - maybye like You said its no problem with wpa-supplicant but with network card - is there any special way i should go with usb adapter?

---

### Post by Irihapeti on 2013-04-03
USB wireless cards are definitely outside of my experience. I suggest searching on the forums to see what works with Ubuntu.

And let's hope that one of the wireless experts on the forum will have something to say.

---

### Post by navoye on 2013-04-03
i will do like You said - thank You again

---

