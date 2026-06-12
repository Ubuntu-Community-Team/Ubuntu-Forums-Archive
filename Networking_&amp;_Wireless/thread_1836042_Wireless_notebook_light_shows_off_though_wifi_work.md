---
title: "Wireless notebook light shows off though wifi works fine"
date: 2011-08-30
forum: Networking &amp; Wireless
---

### Post by pretty_whistle on 2011-08-30
I have Ubuntu desktop 11.04 installed by itself on my laptop.

My notebook wireless button was fine-glowing blue, then it just stopped and glows red which should mean the wifi connection is off but it's not-the wireless connection is working fine (I'm using it now to post this!).

Weird.

Why would the light show off when the wireless connection is working?  What would cause this, does anyone know?

I just migrated from Windows 7 and it worked fine there.  I had this happen a few months ago when I dual booted Windows and Ubuntu, so it's being caused by having Ubuntu installed for some reason.  But why?

---

### Post by Wayne_V on 2011-08-30
what type of laptop and what type of wireless NIC?

is there a switch for the wireless?  possibly the switch is controlling the led but the linux driver ignores it ...

---

### Post by pretty_whistle on 2011-08-30
> **Wayne_V said:**
> what type of laptop and what type of wireless NIC?

is there a switch for the wireless?  possibly the switch is controlling the led but the linux driver ignores it ...
My laptop is HP Compaq Presario CQ50 210US.

As to the rest, where/how can I find out this info?

---

### Post by pretty_whistle on 2011-08-30
> **Wayne_V said:**
> what type of laptop and what type of wireless NIC?

is there a switch for the wireless?  possibly the switch is controlling the led but the linux driver ignores it ...

The light that glows blue when on is the switch as well.

I don't know what's happening but I had an idea to simply restart the notebook and see if there's a difference.  Now the thing shows 'on'.

Weird I still say.

Sometimes restarts can fix things I guess.   Reminds me of my BlackBerry.

---

### Post by northd_tech on 2011-08-30
> **pretty_whistle said:**
> My laptop is HP Compaq Presario CQ50 210US.

As to the rest, where/how can I find out this info?

Could you post the results of the following terminal commands:
```
sudo lshw -C network 
lspci -nnvv | egrep 'etwork|ireless|thernet' 
ifconfig
iwconfig 
nm-tool 
cat /etc/lsb-release 
lsmod 
rfkill list all
```My HP has an old-fashioned electromechanical switch, but I remember it having a module called "hp_wmi" that I believe regulates the laptop multimedia and wireless "hotkeys."  Yours probably has something similar and that **lsmod** command above should point us that direction.

---

### Post by wildmanne39 on 2011-08-30
Hi, it sounds like the light is back on and since it did not cause connection issues I would not worry about it.

There are some drivers that have a bug in them and the light does not work with them, a long time ago I had one like that but my connection worked great like yours.

---

### Post by pretty_whistle on 2011-08-30
> **wildmanne39 said:**
> Hi, it sounds like the light is back on and since it did not cause connection issues I would not worry about it.

There are some drivers that have a bug in them and the light does not work with them, a long time ago I had one like that but my connection worked great like yours.


Thanks for the input.

I was thinking along those lines.

I'll not worry about then.

---

### Post by wildmanne39 on 2011-08-30
Hi, your welcome! if you for some strange reason do get where you can not connect then post back and we can help with that but I do not see that happening because of the light issue.

---

### Post by pretty_whistle on 2011-08-30
> **wildmanne39 said:**
> Hi, your welcome! if you for some strange reason do get where you can not connect then post back and we can help with that but I do not see that happening because of the light issue.

I don't see that happening either.
Thanks again.

---

