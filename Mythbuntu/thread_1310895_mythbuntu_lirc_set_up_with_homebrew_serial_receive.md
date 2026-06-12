---
title: "mythbuntu lirc set up with homebrew serial receiver"
date: 2009-11-02
forum: Mythbuntu
---

### Post by darthik on 2009-11-02
Hi, i need help to get working homebrew serial receiver under fresh 9.10 install. 
I dont see any homebrew serial receiver in mythbuntu control center receivers list, or im wrong?
So can you help me how to add it manually? Im worry to touch my fresh install until i will know how to do it exactly.

Thank for reply

---

### Post by SiHa on 2009-11-02
> **darthik said:**
> Hi, i need help to get working homebrew serial receiver under fresh 9.10 install. 
I dont see any homebrew serial receiver in mythbuntu control center receivers list, or im wrong?
So can you help me how to add it manually? Im worry to touch my fresh install until i will know how to do it exactly.

Thank for reply

It's frustrating that MCC doesn't include this, don't know why.

Anyway.
```
sudo dpkg-reconfigure lirc
```
Will enable you to reconfigure lirc for your receiver.
If you're not familiar with the interface, cursor right will take you from the pick list to OK / Cancel. Space selects.
ttyS0 = COM1.

If you have an old install with this receiver and a remote working, you can copy the lirc.conf and hardware.conf files into /etc/lirc.

Then restart lirc
```
sudo /etc/init.d/lirc restart
```

Also, be warned. I've filed a bug because when I used MCC to enable VNC on both my BE/FE and remote FE it trashed my lirc install.

---

### Post by darthik on 2009-11-02
> It's frustrating that MCC doesn't include this, don't know why.

My words...

BUT after your helpful reply im managed it, irw now prints keystrokes! \\:D/

if you can explain.. firstly irw dont work, because remote config file i created and placed in ?default? "/etc/lircd.conf" even if i set REMOTE_LIRCD_CONF="/etc/lircd.conf" in hardware.conf irw still no response (restarts after changes included)
so i recognized lircd.conf is also in "/etc/lirc/" after i edit it here irw starts working now

was it only my typing mistake or something else what you can explain me?

I'm using vnc also, if i set it up in MCC before lirc this bug dont applies me?
What is "BE/FE"?

---

### Post by SiHa on 2009-11-03
> **darthik said:**
> 
if you can explain.. firstly irw dont work, because remote config file i created and placed in ?default? "/etc/lircd.conf" even if i set REMOTE_LIRCD_CONF="/etc/lircd.conf" in hardware.conf irw still no response (restarts after changes included)
so i recognized lircd.conf is also in "/etc/lirc/" after i edit it here irw starts working now

was it only my typing mistake or something else what you can explain me?


I'm not sure, sorry. But I have found myself, in the past that changes I make in hardware.conf don't seem to have any affect. Glad it's OK now though.

> I'm using vnc also, if i set it up in MCC before lirc this bug dont applies me?
What is "BE/FE"? 

If you've already setup vnc, then yes, you should be OK.

BE/FE = Backend/Frontend machine, as opposed to backend or frontend only.

---

