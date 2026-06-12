---
title: "Soft AP (hostapd &amp; dnsmasq)"
date: 2012-09-22
forum: Networking &amp; Wireless
---

### Post by ctownstud00 on 2012-09-22
I have a soft access point set up via hostapd and dnsmasq in my Ubuntu 10.04 gnome environment. The problem is that after I log in, the access point wireless device tries to connect to the nearest open wireless network. When this happens, it seems to break my dnsmasq, because when I attempt to connect to my soft AP with a wireless device, it won't assign a proper IP--it just gives a random IP.

Is there a way to stop the wireless device that runs the soft AP from trying to auto-connect to open wireless networks after I log in?

Thanks

---

### Post by ctownstud00 on 2012-09-25
Can anyone help me on this one?

---

### Post by ctownstud00 on 2012-10-02
Bump.

---

### Post by ctownstud00 on 2012-10-08
Bump! Please!

---

### Post by ctownstud00 on 2012-10-16
Bump?

---

### Post by ctownstud00 on 2012-10-18
Tried adding a couple of lines to /etc/rc.local that turns off the internal wireless card, then calls the software AP.

```
sudo ifdown wlan0
sudo ap_ctl --start
sudo ap_ctl --ics
```

Still doing testing, but first run, it seemed to work.

---

### Post by ctownstud00 on 2012-10-19
Could I use $ifconfig instead of $ifdown ? What is the difference there? Also, once I use $ifdown in the rc.local file, I can't figure out how to re-enable the interface. Could anyone share some advice or insight here? What is the best way to do this?

---

### Post by ctownstud00 on 2012-10-29
This is still not working properly. It doesn't keep the DHCP assignments going right when both wireless cards try to connect to the network upon startup. Can anyone advise?

---

### Post by cellarweasel on 2012-10-29
So Ctown, which implementation of hostapd are you using. 
After looking it up(wikipedia) it looks like there are flavors of it. 
[http://en.wikipedia.org/wiki/Hostapd]("http://en.wikipedia.org/wiki/Hostapd")
 

Also it seems that you are having a fight with network manager. It may be that you need to figure out what the network manager applet is doing because it will overwrite alot of files dynamically which in your senario are already being used by dnsmasq/hostapd. I would just send an email to the network manager mailing list asking what kind of interaction with dnsmasq/hostapd is happening and whether or not you should completely disable Network Manager or if it can co-exist with your set up. 

-cellarweasel

---

