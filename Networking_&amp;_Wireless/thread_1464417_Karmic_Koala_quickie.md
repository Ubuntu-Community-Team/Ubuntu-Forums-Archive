---
title: "Karmic Koala quickie"
date: 2010-04-28
forum: Networking &amp; Wireless
---

### Post by chumbo on 2010-04-28
Given that:

* My wifi works perfect.
* On WiFi enable wmaster0 and wlan0 get created (wlan0 in managed mode)
* I would like wlan0 not to get created when I turn on (enable) WiFi
* I have *options ath5k autocreate=none* in /etc/modprobe.d/modprobe.conf

* wlan0 *still* gets created ?!

* I remove the options line from modprobe.conf
* I run *modprobe -r ath5k* followed by *modprobe ath5k autocreate=none*
* I get *ath5k: Unknown parameter 'autocreate'*?!

Which parameter do I use instead of autocreate (if any)?

What am I doing wrong?

Any help is greatly appreciated.

C.

---

### Post by chili555 on 2010-04-28
> * I would like wlan0 not to get created when I turn on (enable) WiFiI don't understand. How are you going to enable wireless *without* wlan0, which is the interface that ath5k uses?

wmaster0 is a virtual interface that the system uses and can and should be ignored. Unless you take extraordinary steps to do otherwise, your wireless will have to use wlan0. Some wireless cards use different interface designations, such as eth1, ra0, etc., but without a lot of hard-coding, you can't get ath5k to use other than wlan0.

Please help us understand what you are trying to accomplish.

---

### Post by 98cwitr on 2010-04-28
why not just copy and paste *wlan0 autocreate=none* in /etc/modprobe.d/modprobe.conf? Would that work?

---

### Post by chili555 on 2010-04-28
> **98cwitr said:**
> why not just copy and paste *wlan0 autocreate=none* in /etc/modprobe.d/modprobe.conf? Would that work?No. Please see:```
modinfo ath5k
```Autocreate is not a listed parameter.

The correct way to load a parameter on boot is to create a file such as */etc/modprobe.d/ath5k.conf* and place the parameter in it like this:```
options ath5k some_parameter
```It must be a parameter that the module recognizes; those are always, as far as I know, listed in *modinfo*.

---

### Post by chumbo on 2010-04-28
> **chili555 said:**
> I don't understand. How are you going to enable wireless *without* wlan0, which is the interface that ath5k uses?

wmaster0 is a virtual interface that the system uses and can and should be ignored. Unless you take extraordinary steps to do otherwise, your wireless will have to use wlan0. Some wireless cards use different interface designations, such as eth1, ra0, etc., but without a lot of hard-coding, you can't get ath5k to use other than wlan0.

Please help us understand what you are trying to accomplish.

Yeah sorry, I would like to create it myself, i.e. I would like to 'create' wlan0 myself using airmon-ng or similar - so how do I avoid *it* being created automagically?

Hope this helps,

C.

---

### Post by chili555 on 2010-04-28
I have never played with airmon-ng for more than a few minutes, but isn't this all you need to do?```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
airmon-ng whatever
```Not all drivers support monitor mode.

---

### Post by chumbo on 2010-04-28
> **chili555 said:**
> I have never played with airmon-ng for more than a few minutes, but isn't this all you need to do?```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
airmon-ng whatever
```Not all drivers support monitor mode.

Correct, however one should be able to control how the 'initial' interface gets created in the first place (if at all) no?

Regards, 

C.

Edit: Actually not, have to correct myself here, airmon will actually create mon0 in addition to wlan0 so one now has two interfaces in monitor mode.

---

