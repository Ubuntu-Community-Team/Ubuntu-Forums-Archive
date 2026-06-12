---
title: "Can anyone successfully connect to wireless network with SSID broadcast disabled?"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by RSASKA on 2010-01-09
Hello,

This is a follow-on from my previous post ([http://ubuntuforums.org/showthread.php?t=1371580](http://ubuntuforums.org/showthread.php?t=1371580))

I have enabled SSID broadcast and now as soon as I boot up my Dell Inspiron 1545n, it connects to wireless in a matter of seconds. But I want to disable SSID broadcast. I'm sure someone with enough time and determination can break WPA2 encryption, and can spoof my MAC address.

Currently researching ways that my Ubuntu 9.04 can connect to a wireless network with the third layer of protection of having the SSID broadcast disabled. 

Any recommendations?

---

### Post by efflandt on 2010-01-09
Disabling SSID broadcast does not really add much to security, because it is included in the clear in any actual packets (encrypted or not), otherwise the AP would not know if you were talking to it or if it should ignore you.  No SSID can also result in lag, because your client would not be able to tell if your AP is still up without communicating with it (which reveals its SSID anyway).

I limit my wireless range by having my wireless/modem/router in the basement, so the signal gets up throughout my 2 story home, but not much beyond its walls.  I don't hardly get a signal on my front porch, so a wardriver would have to be in my driveway to get a signal.

---

### Post by RSASKA on 2010-01-10
> **efflandt said:**
> 

I limit my wireless range by having my wireless/modem/router in the basement, so the signal gets up throughout my 2 story home, but not much beyond its walls.  I don't hardly get a signal on my front porch, so a wardriver would have to be in my driveway to get a signal.


I never thought of that...

In my particular case, I live in an apartment building and can clearly see my neighbors' wireless network - which means they can clearly see mine!

Is there anything else I can do to limit the range of my wireless such that it stays in my apartment only?

---

### Post by darthmob on 2010-01-10
> **RSASKA said:**
> I'm sure someone with enough time and determination can break WPA2 encryption, and can spoof my MAC address.Why would someone do that? Especially if you have got neighbours with less secure networks.

Honestly, I would say try to get rid of your paranoia or use a cable instead.

---

### Post by RSASKA on 2010-01-10
> **darthmob said:**
> Why would someone do that? Especially if you have got neighbours with less secure networks.

People do malicious things for all sort of reason, whether for sheer thrill or financial gain (i.e. identity theft)

> **darthmob said:**
> Honestly, I would say try to get rid of your paranoia or use a cable instead.


For usability around my home, I have to use wireless (that's a separate post for another time)

---

### Post by darthmob on 2010-01-10
> **RSASKA said:**
> People do malicious things for all sort of reason, whether for sheer thrill or financial gain (i.e. identity theft)True. Nevertheless I think it's pretty unlikely something like that happens to you. I guess a better reason to hack someone's wireless is to simply gain access to the internet or private files. 
The more people are living around the more likely it is that someone still uses WEP encryption or even no security measures at all (not that there is much difference :D). If I were to be looking for a WLAN to enter I would surely choose that one.

You may have a look if your router is supported by [dd-wrt]("http://www.dd-wrt.com/site/index"). It can be tricky to set up but offers a wide variety of settings you would never imagine your router was capable of (as many default firmwares are rubbish :D).

---

