---
title: "Disconnect wireless automatically when wired available"
date: 2013-01-19
forum: Networking &amp; Wireless
---

### Post by samwillc on 2013-01-19
Hi,

As the title says, is there a way to set this up? I have my ethernet plugged into the laptop but the wireless is still connected when it doesn't need to be.

I tried 'Edit connections' at the bottom of the dropdown but can't find anything obvious to suggest getting this behaviour. I'm sure it's possible but need a pointer!

Conversely, when I unplug the ethernet, I need wireless to kick in, for example, when I move away from my desk and park myself on the couch.

Thanks for any input.

Sam.

---

### Post by Hadaka on 2013-01-19
Hi, you could...
click wireless icon --> Edit Connections --> click Wireless tab
click YOUR ssid --> click Edit --> uncheck Connect Automatically  (upper left corner)

you would have to choose a wireless connection each time you wanted to use
the wifi by doing this.

Or...you could put a script in /etc/init that would check the status of ethernet or
wireless and do it atuomatically.

---

### Post by samwillc on 2013-01-20
> **Hadaka said:**
> Hi, you could...
click wireless icon --> Edit Connections --> click Wireless tab
click YOUR ssid --> click Edit --> uncheck Connect Automatically  (upper left corner)

you would have to choose a wireless connection each time you wanted to use
the wifi by doing this.

Or...you could put a script in /etc/init that would check the status of ethernet or
wireless and do it atuomatically.

Hi, thanks.

That wouldn't be too bad a way of doing it, it's easy enough to reconnect.

I have installed jupiter and disabled wifi via the yellow lightning bolt dropdown menu. I have yet to see whether this is automatic and will re-enable automatically when I unplug the ethernet.

Sam.

---

### Post by beefcakefu on 2013-03-22
> **samwillc said:**
> Hi, thanks.

That wouldn't be too bad a way of doing it, it's easy enough to reconnect.

I have installed jupiter and disabled wifi via the yellow lightning bolt dropdown menu. I have yet to see whether this is automatic and will re-enable automatically when I unplug the ethernet.

Sam.
Hey there, I came across this thread as I was attempting to do the same myself. The script that I eventually used is [here]("http://askubuntu.com/questions/112968/automatically-disable-wifi-wireless-when-wired"). Needs elevated privileges to create the file and don't forget to chmod +x after.

---

