---
title: "Fan control in Linux - with a little help from Windows?"
date: 2019-04-15
forum: MINT
---

### Post by enverhoxha on 2019-04-15
Hi
Running Linuxmint 19.1 (Ubuntu) on my new Asus FX504GM laptop.
One of the issues I have in Linux is lack of fan control.

I was wondering if I install Windows too (dual boot) and use a Windows utility like Asus Fan Xpert, will the settings 'stick' when I reboot into Linux? 
(I've read somewhere that this trick works for the battery charging level - Asus Battery Health Charging).

---

### Post by jeremy31 on 2019-04-15
Moved to Mint

---

### Post by CatKiller on 2019-04-15
> **enverhoxha said:**
> I was wondering if I install Windows too (dual boot) and use a Windows utility like Asus Fan Xpert, will the settings 'stick' when I reboot into Linux? 
No.

For fan control to work, you need something running that, second-to-second, will check the output from your temperature sensors and send a signal to your fans.

Your BIOS can do this, and probably has profiles already for whether you prioritise cooling or quietness.

If you want finer control through software you'll need something to read the sensors (**lm-sensors**) and something that can send signals to your fans (**fancontrol**). Neither of these are installed by default, but they are fairly straightforward to install and use, and there is quite a lot of information available for them.

The only issue with doing it through software is that information about the sensors used in computers is not generally published, so someone will have had to reverse-engineer the signals from the sensor chips your computer uses before you'll be able to use them.

---

### Post by enverhoxha on 2019-04-15
Well, although I bought the laptop last friday, the BIOS doesn't seem to include any cooling profiles.

---

### Post by CatKiller on 2019-04-15
Apparently that laptop has a key combination to switch between the profiles. The choices are "Silent," "Balanced," or "Overboost."

If it were mine, I would see if the sensors are detected, at least. As well as being useful for controlling the fans, it means you can display the temperatures in something like conky.

---

