---
title: "Wifi Slow on Battery Power"
date: 2011-01-29
forum: Networking &amp; Wireless
---

### Post by speedemonV12 on 2011-01-29
Hey guys, just installed Ubuntu on my Macbook Pro and im loving it right now, but whenever I disconnect from the power source and run from battery, my wifi Internet slows down to a crawl. As soon as i plug the power back in, the internet is back to normal. 
Any explanation for this?

---

### Post by SaintDanBert on 2011-01-29
Check you CMOS and power-manager configuration. Most laptops have a setting that will reduce power consumption while on battery power.
Common victims are wifi radio power, cpu speed, and screen brightness.

~~~ 0;-Dan

---

### Post by speedemonV12 on 2011-01-30
Thanks, I have turned off all the power saving options in Power Management, still no change.  But what is CMOS?

---

### Post by SaintDanBert on 2011-01-30
Your PC hardware (motherboard) uses CMOS memory to store its most basic software settings. When you power-on, the Basic Input Output System (BIOS) reads the CMOS settings. One of the most important is which disks are available for boot and in which order. You access these settings but running "setup" or similar immediately following a power-on. Every system has a special keystroke or special button to activate this setup utility. 

All of my laptops have settings that say "behave this way on battery" versus "behave that way on AC power".

Bonne chance,
~~~ 0;-Dan

---

### Post by scarleo on 2011-01-30
You can try this:

Do: sudo iwconfig
Find the name for your WLAN adapter, like wlan0, eth0 or whatever
Do: sudo iwconfig wlan0 power off <-swap "wlan0" for your adapter name
This turns off powersaving feature on your wireless and should help speed.

EDIT: Do the above when on battery

---

### Post by SaintDanBert on 2011-01-30
You might need to issue the iwconfig command each time that you boot.

Since much of hardware configuration happens automatically at power-on and system start using "upstart" and "acpi" and "udev" I'm still trying to sort out how to make some configuration settings survive restart. (grinning) *Not part of this question, but I'd sure like an explanation if anyone knows those details.*

~~~ 0;-Dan

---

### Post by speedemonV12 on 2011-02-01
thank you very much, that worked!! but yes, I do need to re-issue the command every time I restart my computer. Anyway to prevent this?

---

### Post by hambletonh83 on 2011-06-06
I have this exact problem. Running a Dell Inspiron 1545 with 11.04 32-bit. Unplugging and plugging in the laptop is literally like using a wifi switch. Running iwconfig showed power management as off. I tried 'sudo iwconfig eth1 power off' anyway, but it didn't work. Does this depend on anything else? Is there anything else that it could possibly be?
I'm a relative newbie, and am getting a little desperate here, as wifi is essential for me at uni and I can't always have my laptop plugged in.
Any help would be MASSIVELY appreciated...
and please try and be kind if you're able to give me instructions, I'm not completely useless but I probably won't understand everything.
Thanks

---

### Post by sbjaved on 2011-08-13
I have the same issue. Running natty on dell xps 15. Is this a known bug? btw "iwconfig wlan0 power off" fixes it for me too.

---

### Post by sbjaved on 2011-08-13
> **hambletonh83 said:**
> I have this exact problem. Running a Dell Inspiron 1545 with 11.04 32-bit. Unplugging and plugging in the laptop is literally like using a wifi switch. Running iwconfig showed power management as off. I tried 'sudo iwconfig eth1 power off' anyway, but it didn't work. Does this depend on anything else? Is there anything else that it could possibly be?
I'm a relative newbie, and am getting a little desperate here, as wifi is essential for me at uni and I can't always have my laptop plugged in.
Any help would be MASSIVELY appreciated...
and please try and be kind if you're able to give me instructions, I'm not completely useless but I probably won't understand everything.
Thanks
I think you need to run:
sudo iwconfig **wlan0** power off

Instead of:
sudo iwconfig **eth1** power off

---

### Post by Skorzen on 2011-08-19
I am currently facing the same issue, and I am here to tell you that the command stated above resolves the problem, but you also have to issue it not only when the machine is rebooted, but also when it enters Suspend mode and then Normal mode.

By the way, does anyone know if is there a way to add this to system boot? Maybe editing /etc/rc.local?

Best regards.

---

### Post by mhall119 on 2011-10-04
The script that turns on powersave mode is /usr/lib/pm-utils/power.d/wireless

If you want to override that script, create a new one at /etc/pm/power.d/wireless

If you don't want it to change anything, just have your new script call: exit 0

Or you can make a copy of /usr/lib/pm-utils/power.d/wireless and tweak it to your liking.

---

### Post by Hatsune Miku on 2012-05-06
> **mhall119 said:**
> The script that turns on powersave mode is /usr/lib/pm-utils/power.d/wireless

If you want to override that script, create a new one at /etc/pm/power.d/wireless

If you don't want it to change anything, just have your new script call: exit 0

Or you can make a copy of /usr/lib/pm-utils/power.d/wireless and tweak it to your liking.

Can we just delete this file? I'd rather my battery die then it to slow my performance to the point where it is not worth having wireless at all.

---

