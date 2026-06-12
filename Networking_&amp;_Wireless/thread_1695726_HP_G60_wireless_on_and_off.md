---
title: "HP G60 wireless on and off"
date: 2011-02-26
forum: Networking &amp; Wireless
---

### Post by Oberon1 on 2011-02-26
I have an HP G60 running 10.10 and I love it. I have converted the whole family to the Ubuntu mindset. Only issue is after some family used it over the weekend the wireless has stopped working. We are now 4 weeks without wireless on th esystem and the wife is threatening Windows. My guess is some key combination was pressed and or the "patch" that affected RFKILL is screwing things up. I have read the threads Chilli posted and that helped when I initially set the machine up. But nothing works and I cannot get the damn light to turn red(used to be red when wireless was working). Help me Obiwon.

---

### Post by inobe on 2011-02-26
please specify the model, you've already given us the make!

g60 has about fifty models.

---

### Post by chili555 on 2011-02-26
Please take a seat while Dr. Chili snaps on the latex gloves. First, some diagnostics. Please open Applications > Accessories >Terminal and run and post:```
rfkill list all
sudo rfkill unblock all
rfkill list all
lsmod | grep hp
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

If some of these commands produce no output, that's useful information we need.> the "patch" that affected RFKILL is screwing things up.I am not familiar with this patch; please tell me more.

---

### Post by Oberon1 on 2011-02-26
Hpg60 243dx

---

### Post by Oberon1 on 2011-02-26
LSmod out put:
hp_wmi    5223 0
 
RFkill list all output:
0: hp-wifi: Wireless LAN
  Soft blocked: yes
  Hard blocked: yes
1: phy0: Wireless LAN
  Soft blocked: no
  Hard blocked: no

---

### Post by Oberon1 on 2011-02-26
Here is the article I found about the paytch error. Not sure if its related:
[http://www.geekmind.net/2011/01/linux-wifi-operation-not-possible-due.html](http://www.geekmind.net/2011/01/linux-wifi-operation-not-possible-due.html)

---

### Post by chili555 on 2011-02-26
Now try this:```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
```If this helps, we can blacklist hp-wmi and write a polite note to the developers. Thanks.

---

### Post by Oberon1 on 2011-02-26
Now the list all does not show HP-wifi. List all shows:
1: phy0: Wireless LAN
  Soft blocked: no
  Hard blocked: no
 
Is that the expected result. Should we reboot?

---

### Post by chili555 on 2011-02-26
> Is that the expected result. Should we reboot?Yes, that's the expected result and no, *do not* reboot yet. Is the wireless working now? Do you see any networks when you click the Network Manager icon?

---

### Post by Oberon1 on 2011-02-26
You mean going to system>administration>network?
I see my wireless connection and it is checked off but I am unable to get the browser to work.

---

### Post by chili555 on 2011-02-26
> You mean going to system>administration>network?Nope, I mean the Network Manager icon at the top right; on my system it looks like a radio antenna with waves radiating out. When you click it, you should see several networks to select from and when you click yours, it ought to ask for your password and then connect. Please see attached.

---

### Post by Oberon1 on 2011-02-26
Icon does not show. That was apparently not installed when I loaded gnome and now I cannot get the packages because of the wireless not working. I plugged into a wired connection and cannot get it running that way either. Damn thing just does not want to get online. I rebooted and still nothing. Arggg Windows is looking sexier every minute...LOL.

---

### Post by chili555 on 2011-02-26
> Arggg Windows is looking sexier every minute...LOL. Don't even think that. Are you going to give up this easy? I guess you never had a racecar, a teen-aged daughter or a first wife!

In a terminal, type:```
nm-applet &
```Leave the terminal open. Does the icon show up? If not, are there errors we can learn from?

---

