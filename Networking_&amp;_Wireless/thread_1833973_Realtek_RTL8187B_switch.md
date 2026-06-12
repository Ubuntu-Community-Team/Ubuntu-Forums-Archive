---
title: "Realtek RTL8187B switch"
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by tpprynn on 2011-08-26
Should using ndiswrapper and Windows drivers for this chip make the front physical switch on my Toshiba Equium L40 work properly? With the native drivers the wireless works fine but the wireless light stays on whether the switch is in the on or off position. I have not yet tried the ndiswrapper method and don't currently have Linux installed though Ubuntu and Debian are on my other two computers. I'd try this out in a new partition if someone can say it will work.

I've found this with Ubuntu (8.10 and on), Mint, Debian 6.01 and Fedora 10-15.

This laptop uses Fn and F8 to turn wireless on and off too - in Windows this will only work if the physical switch is on. These physical switches are not uncommon so it seems strange that their functioning would be omitted in Linux drivers.

Thanks.

---

### Post by chili555 on 2011-08-27
> Should using ndiswrapper and Windows drivers for this chip make the front physical switch on my Toshiba Equium L40 work properly? No. Generally, the physical switch is just that, a physical switch that interrupts some electrical function and turns the wireless radio off. I am surprised that the operation of the front physical switch is correct in Windows and incorrect in various Linuxes (Linuii??). I would not be surprised that the Fn+F8 function was incorrect.

Laptops use a small program to translate key presses into action; in this case, "Please turn on/off the wireless, Mr. Kernel." They are variously known as acer-wmi, thinkpad-acpi, dell-laptop, toshiba-acpi and others. It wouldn't surprise me at all that the module your laptop uses isn't working correctly. It also wouldn't surprise me that the LED is not operating, either on, off or blinking, as expected. It does surprise me that the front physical switch is affected. 

I would love to see the result of this command with the front physical switch in both positions:```
rfkill list all
```

---

### Post by tpprynn on 2011-08-28
Having read that, it could be that it is merely the light that is not working right - that the physical switch may be working in terms of turning the wireless on and off, but that the light isn't playing along. 

I'm not at home for a few hours but I'll check this and give you those readings. Glad you've chipped in as I see you've got a good track record of solving stuff!

If the switch is working but the light isn't going on and off with it, will that be something that can be solved? I've noticed that with my netbook depending on distro the light behaves differently - with some it blinks if the wireless is doing something but otherwise remains off, and with others, like Ubuntu, the light stays on if wireless is on.

Thanks so far.

---

### Post by tpprynn on 2011-08-28
Okay, lo and behold, as you seem possibly to have guessed, the switch is turning the wireless on and off after all, it is just that the light stays on in both states.

As you'd hope, using the command you suggested when in the on position 'hard blocked' says no for my wireless (phy0). And presumably also correct is that 'soft blocked' changes to yes if I use my Fn and F8 keys. I turned on and off a couple of times and all looks correct there.

Some people might be happy to overlook this, but I'd be Windows-free if I can just get the light to do what it does in Windows. Sounds a bit OCD and probably it is, but it would also do the battery life good. I'd be very pleased if you can solve this. As Ubuntu seems to be able to deal with the light on my netbook hopefully there is a similar way it can be cajoled to work my laptop's?

Thanks.

---

### Post by chili555 on 2011-08-28
I love a mystery! Let's take some readings. Please run and post:```
lsmod | grep -e tosh -e 818
```Maybe we'll find a parameter we can manipulate.

---

### Post by tpprynn on 2011-08-29
Thanks. This is promising... That gives:

rtl8187                608982 0
mac80211          294370 1 rtl8187
cfg80211            178528 2 rtl8187,mac80211
eeprom_93cx6   12725   1 rtl8187

with the 818 always in red. Any use? Good luck...

---

### Post by chili555 on 2011-08-31
I'm sorry. I have no further suggestions.

---

### Post by praseodym on 2011-08-31
Hi,

you may want to try [this]("http://wiki.ubuntuusers.de/Archiv/Toshiba_Satellite_L40#RTL8187b") driver or the patched linux driver from there. This article is not up-to-date anymore, but it may work. For the linux-driver you have to install

```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
```
before compiling. Can you show:

```
lspci -nnk | grep -iA2 Realtek
lsusb
```

---

### Post by tpprynn on 2011-09-01
I've got a bit of a blind spot/fear when it comes to compiling but I may give it a go soon, though I dodn't have the Mobile Broadband credit left to download the ectras needed to compile.

I've tried using NDisWrapper now but when I add suitable drivers the box says the hardware is not present oddly. I have seen NDisWrapper work before on my desktop pc with a wireless dongle.

However, I just wanted ot add in case someone comes to his thread with the right knowledge that curiously the wireless light comes on fairly late into a booting-up. This suggests that a service or other is starting the light up rather than that a lack in drivers is just allowing the circuit ot be powered willy-nilly as it had felt to me.

I'll look back here from time to time. It's so annoying that I'm tempted to take steps towards getting a diffeent laptop with no physical switch, like a ZaReason or a System76. Sigh...

---

### Post by tpprynn on 2011-10-23
asus_laptop is the module dealing with the l.e.d I've now learnt. (I had noticed in the log file viewer how my laptop identified as an Asus T20 for whatever reason.) If anyone knows what I now need to do, please let me know.

I ascertained that asus_laptop is what my laptop is using with Linux by blacklisting the module for one boot. Then oddly some but not Fn keys stopped working. I wonder why this is split, with presumably toshiba_acpi dealing with the other Fn keys.

Thanks for any input.

---

