---
title: "Intel 4965 AGN suspend issue in 11.04"
date: 2011-07-12
forum: Networking &amp; Wireless
---

### Post by Sim-I-Am :} on 2011-07-12
Hello, I have a Gateway P-6860FX laptop with Intel 4965AGN WiFi.

Works great and I've been running 11.04 on it for a while now with only minor issues. However, whenever I resume from suspend/sleep mode, the Wifi seems to have been shut off; the indicator applet menu says "Wireless is disabled" and the indicator light below my touchpad is off. 
The only way I have been able to fix this is by booting into Windows (dual boot) and pressing Fn+F2 which turns on the indicator light, allowing me to connect to wifi. Then I boot into Ubuntu again and everything is fine.

I've seen that alot of other people have had this problem, especially with Atheros wifi chips/cards, but I haven't had any luck finding a solution for my situation...

I'm a moderately technical/advanced user -- I know how to use the terminal, etc...

Any help would be greatly appreciated....

Thanks in advance!

Sim

---

### Post by chili555 on 2011-07-12
This often helps. In a terminal do:```
sudo gedit /etc/pm/config.d/config
```Add one line:```
SUSPEND_MODULES="iwlagn"
```Proofread, save and close. I am not sure the change is immediate; it may take a reboot.

---

### Post by Sim-I-Am :} on 2011-07-12
Ok, thanks for the response! I'll give it a shot later this evening and report back. :)

---

### Post by Sim-I-Am :} on 2011-07-13
You, my friend, are a genius. That worked like a charm!

Thank you oodles. :)

---

### Post by chili555 on 2011-07-13
I, my friend, am a thief! This particular fix I found elsewhere searching for the same fix on my own computer. It worked and I saved the method in my super-secret Forum file. I am glad it works for you, too.

So the searchers will find this a bit easier, please use thread tools at the top and Mark Solved.

---

### Post by Sim-I-Am :} on 2011-07-13
Ah yes... Well you are a genius thief then, just for posting -- whether the solution was originally yours or not. :P

Already marked it. :)

Thanks again!

---

