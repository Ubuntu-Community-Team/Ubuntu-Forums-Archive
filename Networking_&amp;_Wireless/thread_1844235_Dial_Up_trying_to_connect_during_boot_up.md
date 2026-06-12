---
title: "Dial Up trying to connect during boot up"
date: 2011-09-14
forum: Networking &amp; Wireless
---

### Post by iheartubuntu on 2011-09-14
I am trying to help a friend with his internet problems. He is on a fixed income and using dial up internet. He has two problems...

1 - during the boot up process the modem attempts to dial out and connect to the internet. Can I fix this somehow? Is this an issue with "startup applications"? I have not looked at his computer yet, just by telephone but Im trying to troubleshoot this before I need to go to his house.

2 - after boot up, he attempt to dial into his local internet access number and it never connects. It does dial out, but never connects. Any recommendations? I havent used dial up for many years! Im thinking to change the access phone number as the current one may not be working.

He is currently using Ubuntu 10.04.

Thanks for any tips!

---

### Post by iheartubuntu on 2011-09-19
OK! I got over to his house to troubleshoot the problem. He does not have Windows so was unable to see if the dial up works with that. 

[LIST=1]
[*]I removed wvdial,kppp, and gnome-ppp and the modem still attempts to dial out upon boot. I have not fixed this issue yet. 

[*]When attempting to dial out to his carrier, the modem works fine in gnome-ppp and kppp, although both return a "NO CARRIER" message. I tried a different dial up ISP and get the same NO CARRIER message. Any advice? I cannot find any solutions online through forum or goog searching. Thanks for any tips!
[/LIST]

---

### Post by jonobr on 2011-09-19
For the dialup on boot up, Sounds like there may be a startup script that is performing the dialout.

Dod yuou try looking at the /etc/rcx.d startup scripts to see if any were modified to do this?
[Here]("http://www.unixtutorial.org/2009/01/disable-service-startup-in-ubuntu/") is an old link with startup in

Also Im thinking if you disconnect the phone from the modem, stick on  a telephone and pick up the receiver, do you get regular dial tone?
IS the line going through anything funky ?

Can you call the ISP number directly with the phone?
Do you hear modem tones when you call their number?

---

### Post by praseodym on 2011-09-19
Check:

```
rfkill list
cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by iheartubuntu on 2011-09-19
would "rfkill" help me since its dialup?

i think a clean install of ubuntu might fix the dial out at startup. this might be a lot easier then fighting the prob.

his phone line does work and the ISP does work. I contacted his ISP today and they think its a modem issue since we can see & hear the modem dialing out, but his ISP said it has not connected to them in over a month.

---

### Post by praseodym on 2011-09-20
```
cat /var/lib/NetworkManager/NetworkManager.state
```shows here:
```

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=[COLOR="Red"]true[/COLOR]
```
Change **true** in **false**

---

### Post by dineshs on 2011-09-20
> When attempting to dial out to his carrier, the modem works fine in gnome-ppp and kppp, although both return a "NO CARRIER" message. I tried a different dial up ISP and get the same NO CARRIER messageUntick the option `check carrier line' in gnome-ppp.
Can you post the result of ```
cat /etc/ppp/peers/provider
```

---

