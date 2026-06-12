---
title: "iwconifg essid not being set"
date: 2006-01-01
forum: Networking &amp; Wireless
---

### Post by guttley on 2006-01-01
Hi,


I have a Acer Aspire 1800 with a IPN2220 wirless card and ive installed the ndiswrapper and drivers.
Using iwlist i can see the access point i want to connect to and the essid of it.
However when i try to set the essid using iwconfig it dosnt seem to take the setting although no error is reported.

any ideas? :???:

---

### Post by daller on 2006-01-01
[QUOTE=guttley]Hi,


I have a Acer Aspire 1800 with a IPN2220 wirless card and ive installed the ndiswrapper and drivers.
Using iwlist i can see the access point i want to connect to and the essid of it.
However when i try to set the essid using iwconfig it dosnt seem to take the setting although no error is reported.

any ideas? :???:[/QUOTE]

How do you set the essid? are you using /etc/network/interfaces? - or a GUI?

See this:

[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)

---

### Post by guttley on 2006-01-01
[QUOTE=daller]How do you set the essid? are you using /etc/network/interfaces? - or a GUI?

See this:

[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)[/QUOTE]

i used 
```
iwconfig wlan0 essid essid_name
```

after setting the mode to be managed and setting the key in a similar fashion to the above. 

I did take a look at the wiki but it is pretty similar to what i have done before.
I used to have another Acer Aspire with a broadcom driver via the ndis drivers.

---

### Post by guttley on 2006-01-01
Interestingly enough if i disable WEP its all working like a dream. 
I turned WEP back on and checked the keys which i set to FFFFFFFFFF on both the router and the laptop.
Still didnt work, guess ill leave WEP off and just use the MAC filter.

---

### Post by daller on 2006-01-01
What is the exact make & model of the card?

Look here:

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

---

### Post by tgoose on 2006-03-29
[QUOTE=guttley]Interestingly enough if i disable WEP its all working like a dream. 
I turned WEP back on and checked the keys which i set to FFFFFFFFFF on both the router and the laptop.
Still didnt work, guess ill leave WEP off and just use the MAC filter.[/QUOTE]
I have exactly this problem, but since it's not my network I don't want to disable WEP (I have access to controls but I'd have to convince other people that it'd be safe enough to unencrypt the network with MAC filters in place...)

---

