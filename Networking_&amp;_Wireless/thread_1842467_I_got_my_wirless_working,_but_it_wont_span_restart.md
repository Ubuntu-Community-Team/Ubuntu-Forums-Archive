---
title: "I got my wirless working, but it wont span restarts"
date: 2011-09-11
forum: Networking &amp; Wireless
---

### Post by matthewdowney20 on 2011-09-11
I am running Ubuntu 11.04, on my HP Pavilion tx 1000 laptop. I  did a bunch of ndiswrapper stuff until i finally went up to the  additional drivers menu and (with my Ethernet plugged in) selected  'Additional Drivers', one of the options was the Broadcom STA Wireless  Driver. I clicked 'activate' and everything worked fine with regards to  WiFi. It was only when I rebooted my computer that I realized; the  driver does not span restarts. TO get it working again I went to the  same 'Additional Drivers' screen, the broadcom STA wireless driver was  in fact installed but not working "activated but not in use" said the  program. so no problem I just removed the driver and reinstalled it, it  worked fine, once again until I restarted. Now I am not a lazy person,  so I would be okay with this, except it presents a catch 22 in any place  where i don't have an Ethernet cable, namely I need Internet to get  Internet.

---

### Post by bkratz on 2011-09-11
> **matthewdowney20 said:**
> I am running Ubuntu 11.04, on my HP Pavilion tx 1000 laptop. I  did a bunch of ndiswrapper stuff until i finally went up to the  additional drivers menu and (with my Ethernet plugged in) selected  'Additional Drivers', one of the options was the Broadcom STA Wireless  Driver. I clicked 'activate' and everything worked fine with regards to  WiFi. It was only when I rebooted my computer that I realized; the  driver does not span restarts. TO get it working again I went to the  same 'Additional Drivers' screen, the broadcom STA wireless driver was  in fact installed but not working "activated but not in use" said the  program. so no problem I just removed the driver and reinstalled it, it  worked fine, once again until I restarted. Now I am not a lazy person,  so I would be okay with this, except it presents a catch 22 in any place  where i don't have an Ethernet cable, namely I need Internet to get  Internet.



The following command should add it to the modules loaded at boot time

echo wl | sudo tee -a /etc/modules

---

### Post by ixusubunt on 2011-09-11
bkratz,/
Will this same command work for me, as I have a similar problem?
```
echo wl | sudo tee -a /etc/modules
```My laptop is a Fujitsu Amilo La1703 running Lubuntu and every time I reboot it I have to reload the WLAN driver by entering the following into a terminal:
```
sudo ndiswrapper -l
```The problem seems to be quite common, especially on machines that switch off the wireless when you shut them down i.e I have to press Fn and F2 to get the wireless indicator back on when I reboot ... which I press as soon as I hit the 'on' switch!

Thanks

---

### Post by bkratz on 2011-09-11
> **ixusubunt said:**
> bkratz,/
Will this same command work for me, as I have a similar problem?
```
echo wl | sudo tee -a /etc/modules
```My laptop is a Fujitsu Amilo La1703 running Lubuntu and every time I reboot it I have to reload the WLAN driver by entering the following into a terminal:
```
sudo ndiswrapper -l
```The problem seems to be quite common, especially on machines that switch off the wireless when you shut them down i.e I have to press Fn and F2 to get the wireless indicator back on when I reboot ... which I press as soon as I hit the 'on' switch!

Thanks


No, I'm afraid not unfortunately.  I copied this from the ndiswrapper "sticky" above, 
You might want to read through it.

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

[COLOR=Red]*Loading ndiswrapper automatically at boot:*

In modern versions of Ubuntu, ndiswrapper is supposed to be loaded  automatically at boot.  Sometimes for various reasons that fails to  happen, however.  If this appears to be your problem, run this command:

[/COLOR]       
   ```
echo 'ndiswrapper' | sudo tee -a /etc/modules 

```

[COLOR=DarkOrange][COLOR=Red]and the problem should be resolved.  This command tells the system  explicitly to load the ndiswrapper module while booting, no matter  what.



[/COLOR] [/COLOR] 
[B][SIZE=4]
[/SIZE][/B]

---

### Post by praseodym on 2011-09-11
Please show:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
rfkill list
```
For [COLOR="Red"]F[/COLOR]ujitsu [COLOR="Red"]S[/COLOR]iemens [COLOR="Red"]Am[/COLOR]ilo you can load a module for the wireless kill switch:

```
sudo modprobe -v fsam7400 radio=1
```

---

### Post by ixusubunt on 2011-09-12
Thanks bkratz,

Running:
echo 'ndiswrapper' | sudo tee -a /etc/modules
solved the problem!!!

---

### Post by bkratz on 2011-09-12
> **ixusubunt said:**
> Thanks bkratz,

Running:
echo 'ndiswrapper' | sudo tee -a /etc/modules
solved the problem!!!


Sure glad to hear that, I wasn't totally sure that was what you wanted. Anyway, congratulations!

---

