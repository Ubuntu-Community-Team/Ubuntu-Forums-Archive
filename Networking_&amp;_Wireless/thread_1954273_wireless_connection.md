---
title: "wireless connection"
date: 2012-04-07
forum: Networking &amp; Wireless
---

### Post by deephorizon on 2012-04-07
Hello, using Ubuntu 11.10 in a Dell 8300 tower connect to the net using a wireless Belkin G Plus Mimo router, it connect fine to the net from day one, the problem arise when I set the security WPA & WPA2 it ask for password I put it in but not connection it keep trying but nothing happen, remove the inscription and it connect fine, IM missing something but I do not know what is, I been reading a lot trying to find what is wrong but I give up I have to ask, appreciate any input.

---

### Post by dylan07 on 2012-04-07
**If WPA does not work, make sure that wpa-supplicant is installed. No further configuration is neede[COLOR=Black]d Network manager s[/COLOR]**[B]hould handle the rest.

To install it run this through a terminal (ctrl + alt + T)
[/B]
```
sudo apt-get install wpasupplicant
```

---

### Post by deephorizon on 2012-04-07
> **dylan07 said:**
> **If WPA does not work, make sure that wpa-supplicant is installed. No further configuration is neede[COLOR=black]d Network manager s[/COLOR]****hould handle the rest.**
 
**To install it run this through a terminal (ctrl + alt + T)**
 
```
sudo apt-get install wpasupplicant
```
 Than you I will try it.

---

### Post by wildmanne39 on 2012-04-07
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # and paste the information between the brackets.

Also ubuntu connects best with wpa2 only not mixed mode.
Thank you

---

### Post by dylan07 on 2012-04-07
Wildman, What do you think about my suggestion? Also, If you are good with hardware, can you help me with an audio issue I am having, I posted in another section?

P.S. I don't know how to PM

---

### Post by wildmanne39 on 2012-04-08
Hi, will I have not really done any work with audio issues.

As for wpa-supplicant you are correct but in many cases it just does not work correctly and a parameter can be added to the driver to make it connect, also wicd can be used instead of network manager becuase it handles encryption better.
Thanks

---

### Post by dylan07 on 2012-04-08
> wicd can be used instead of network manager becuase it handles encryption better.

very true, is network manager installed by default, and is wicd extra? (I used to use backtrack 5 R1, and it had wicd pre-installed, so, I honestly dont know)

---

### Post by dylan07 on 2012-04-08
[B]Here is what you need to put for wireless interface 
           ```
auto wlan0 
iface wlan0 inet dhcp 
wpa-conf /etc/wpa_supplicant.conf
``` /etc/wpa_supplicant.conf for WPA2 / WPA:
           ```
network={
         ssid="[COLOR=Red]ADD-YOUR-SSID-HERE[/COLOR]"         
        proto=RSN         
        key_mgmt=WPA-PSK         
        pairwise=CCMP TKIP         
        group=CCMP TKIP         
        psk="[COLOR=Red]ADD-YOUR-WPA-PASSWORD-HERE[/COLOR]" 
}
``` once done restart networking:
           ```
sudo  /etc/init.d/networking restart
```Give that a try![/B]

---

