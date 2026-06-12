---
title: "Update killed all network con. on my asus 1000h"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by nyarnon on 2010-02-25
Latest opdate today killed all network connectivity on my asus 1000h today and I just cant figure out why. need some help please.

Some data:


Attached because on posting I get an error even though there is not a singel image or smiley:

You have included 11 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again. 

Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.

Couldn't upload either it gives invalid file so I resort to Google docs now :-(

[http://docs.google.com/Doc?docid=0AcDkCTml_yWQZGNzazQ3Y3pfNjRzdnc0c3pnMw&hl=en]("http://docs.google.com/Doc?docid=0AcDkCTml_yWQZGNzazQ3Y3pfNjRzdnc0c3pnMw&hl=en")

---

### Post by chili555 on 2010-02-25
Do you mean it killed wired and wireless both? If you detach the ethernet cable and reboot, does the wireless try to connect? When you click the Network Manager icon, do you see your network, "SpeedTouch47876A"? Are you asked for your WPA details? 

If my guess is wrong and you are really trying to get your wired ethernet going, please let me know and we'll shift our attention there.

---

### Post by nyarnon on 2010-02-25
> **chili555 said:**
> Do you mean it killed wired and wireless both? If you detach the ethernet cable and reboot, does the wireless try to connect? When you click the Network Manager icon, do you see your network, "SpeedTouch47876A"? Are you asked for your WPA details? 

If my guess is wrong and you are really trying to get your wired ethernet going, please let me know and we'll shift our attention there.

Yes both won't budge this is weird normaly I can fallback to the wired connection but that doesn't respond either.

---

### Post by chili555 on 2010-02-25
Please post:```
dmesg | grep -e rt2 -e ra0
```Let's see what's going on ... or not.

---

### Post by nyarnon on 2010-02-25
Not much actually:

[   18.313544] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[   18.495939] rt2860 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   18.496490] rt2860 0000:01:00.0: setting latency timer to 64
[   30.756045] ra0: no IPv6 routers present

---

### Post by nyarnon on 2010-02-25
I removed the setup for the router in the network manager. Then clicked it again in the wireless window, I am asked for the password fill it in and......
Nothing, like before the applet keeps spinning and no connection.

There seems to be a problem with the i915 setup also see a lot of invalid EDID errors in dmesg

---

### Post by skeve on 2010-02-25
I have a similar problem - no wired or wireless connection. It seems it has something to do with the update from network-manager ppa. I can get the connection using 
```
sudo dhclient wlan0
```
for wireless or
```
sudo dhclient eth0
```
for wired.
But the applet icon still keeps spinning.

---

### Post by chili555 on 2010-02-25
> There seems to be a problem with the i915 setup also see a lot of invalid EDID errors in dmesgI suggest you google those and try to solve that issue first.

---

### Post by nyarnon on 2010-02-25
Confirmed, reinstalled network-manager and network-manager-gnome from the regular repository and I am cool. Thanks guys. Gonna shut down the ppa for the moment.

---

### Post by chili555 on 2010-02-25
> **skeve said:**
> I have a similar problem - no wired or wireless connection. It seems it has something to do with the update from network-manager ppa. I can get the connection using 
```
sudo dhclient wlan0
```
for wireless or
```
sudo dhclient eth0
```
for wired.
But the applet icon still keeps spinning.Please take a look at:```
cat /etc/network/interfaces
```It should contain no more than:```
auto lo
iface lo inet loopback
```If that file is correct, you might open System -> Administration -> Synaptic and find Network Manager and mark it for re-installation and click Apply. Perhaps that will fix what sounds like an error in the installation of NM. Usually, the manual methods, iwconfig, dhclient, etc. will not work at all if NM is operating correctly.

---

### Post by nyarnon on 2010-02-25
> **chili555 said:**
> I suggest you google those and try to solve that issue first.

Dont think they are connected, still got that error but my network is up.

---

### Post by skeve on 2010-02-25
I'm pretty sure this problem is connected with the network-manager ppa. Look at this thread: [http://ubuntuforums.org/showthread.php?t=1415174](http://ubuntuforums.org/showthread.php?t=1415174)

Someone says that dhcp3-client is incompatible with network-manager 0.8

---

### Post by webheadjunky on 2010-02-27
Hi there

I think I might have the same problem so didn't want to start a new thread

We were happily running 9.10 on a Dell Inspiron. Yesterday, the update manager icon indicated there were 84mb worth of updates available so I downloaded them all and installed them. I then got a message requesting restart so i did and after that I can't connect at all

All I get is the little spinning propeller animation and it just spins endlessly. I can see my wireless network and the settings are all there but it just won't connect

I tried connecting direct via a cable and it still won't connect that way either

My desktop in the bedroom upstairs is running Kubuntu Karmic and has a wireless connection that works fine (it's what I'm using now) so I don't think there is a problem with the router

So any help and advice would be gratefully received

Are you aware of any known bugs with recent updates? 

Apart from this blip, our laptop has been running flawlessly for months

Thanks in advance 

Raaj

---

### Post by webheadjunky on 2010-02-27
Whoops ! Just noticed the link in an earlier post! I will try that first!
Cheers
Raaj

---

