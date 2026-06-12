---
title: "Wireless-less P dv6"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by owiknowi on 2011-03-09
Have both U10.04.2 and U10.10 installed (separate partitions) on a HP dv6.
After initial boot in the network manager applet wireless is available and even displays two wireless routers in the neighborhood.

After the first reboot the applet shows wireless in grey as 'Disconnected'.
After updating through ehernet nothing changes.

It's a Ralink RT3090 chipset.

Extra information (gained from other installations where wireless does come up):
Pardus 2 corporate provides the following information:
- kernel driver rt2860
- kernel module rt2860 sta

Mandirva needs the rt3060 driver to be installed in order to make wireless work.

Any help is much appreciated!

Btw. Neither with other Ubuntu derivatives or other tuxes (Red Hat) the wireless is working.

---

### Post by chili555 on 2011-03-09
The module rt2860sta is built in to the current 10.10 kernel. In some cases, the device is also claimed by conflicting drivers. Let's check a few things. Please open a terminal and post:```
lspci -nn
lsmod | grep -e rt2 -e rt3
```Thanks.

---

### Post by owiknowi on 2011-03-09
> **chili555 said:**
> The module rt2860sta is built in to the current 10.10 kernel. In some cases, the device is also claimed by conflicting drivers. Let's check a few things. Please open a terminal and post:```
lspci -nn
lsmod | grep -e rt2 -e rt3
```Thanks.

thanks for your very quick response.
first have to install U10.xx again (been very busy with all kinds of distro's :/ )

i'll get to it right away and get back to you asap with the output from the commands as you suggested (right after initial boot).

---

### Post by owiknowi on 2011-03-09
> **chili555 said:**
> The module rt2860sta is built in to the current 10.10 kernel. In some cases, the device is also claimed by conflicting drivers. Let's check a few things. Please open a terminal and post:```
lspci -nn
lsmod | grep -e rt2 -e rt3
```Thanks.

I'm sorry for the delay but as attachment the output from the two commands (unmodified installation ubuntu 10.04.2 LTS _64 kernel 2.6.32-28-generic).

---

### Post by chili555 on 2011-03-09
The module rt3090sta is loaded. Did it create an interface, wlan0 perhaps?```
iwvonfig
sudo iwlist wlan0 scan
```Thanks.

---

### Post by owiknowi on 2011-03-10
thanks again for your reply.
hereby as requested the output from the two other commands (in a root terminal).

could it perhaps be an irq problem since there are many devices loaded (bluetooth, hdmi, vga port, network, 3x usb, etc.)?
the hp dv6 is rather bloated with hw and is used for testing newer hardware with linux (7 different tuxes installed).

additional information:
i did after the first test reduce some services  by disabling them in 'startup applications preferences' (bluetooth manager, check for new hardware drivers, evolution alarm notifier, personal file sharing, remote desktop, ubuntu one, update notifier).
on other computers all works well with these same settings.

---

### Post by chili555 on 2011-03-10
An interface, wlan0 is created. Let's do a bit more diagnostics:```
dmesg | grep -e rt3 -e wlan
rfkill list all
```> could it perhaps be an irq problem since there are many devices loaded (bluetooth, hdmi, vga port, network, 3x usb, etc.)I doubt it, but you could check for errors or warnings:```
dmesg | grep -e warn -e err
```

---

### Post by owiknowi on 2011-03-10
thanks again for your help.
attached you'll find the results of all suggested commands.

add 1. it says something about bluetooth but i've turned if off in 'startup applications'.

add 2. installed sabayon 5.5 as well and wireless networks were detected.

---

### Post by owiknowi on 2011-03-13
still putting op a fight with ubuntu 10.xx_64 and the not functioning hp dv6 wireless.
since in pardus kurumsal 2 (corporate) the wireless does come up and wireless is available, i'm trying to find out why.

amongst the drivers already described above also found the following packages installed:
- atmel-firmware (for 76c50cx network chips)
- b43-firmware
- b43-fwcutter
- crda (compliance daemon)
- ifplugd
- iw (nl80211-based conf. util.)
- wireless-regdb
- wireless-tools
-wpa_supplicant
- openvpn (although vpn stands for virtual private networks it seems to provide some other services too)

hope this info is of any use for those who understand what a penguin does in a computer...

---

### Post by Shriner on 2011-03-13
<<<<following closely as I just upgraded to 10.04 and am having a similar problem. I'm using a USB radio (Linksys WUSB-54) - wlan0 is created, etc....All was fine with 9.04, Now it looks like sometimes the radio is being powered down. A quick fix is to disable/re-enable networking, but I'd like to find a permanent solution.....watching.....

---

### Post by Shriner on 2011-03-13
Thought that I'd share this, it may help.....

Found another thread, that reports that if you are using a kernel before  2.6.34 this problem occurs. It is reported that manually updating your  kernel to 2.6.34 will cure the drops with all wireless cards. I'm not  willing to verify this at this time because my ISP has oversold their  DSL capablities and my connection sucks at this time. I guess I'm  fortunate that I have a WET-11 to use in the interim.

Instructions for manually updating your kernel can be found @
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild]("http://ubuntuforums.org/view-source:https://wiki.ubuntu.com/KernelTeam/GitKernelBuild")

You can determine your current kernel with uname -a

I'm not sure that will work for this, but I'm posting for your info.

---

### Post by Shriner on 2011-03-13
Seem to have solved mine by turning off the power saving mode of the card. 
"iwconfig" will tell you if it is on, disable with "sudo iwconfig wlan0 power off". Assuming that your wireless is wlan0.

---

### Post by owiknowi on 2011-03-14
thanks for the information, shriner. very much appreciated!

will now leave pardus and boot into u10.04 and try what you've suggested.
i'll get back here with the results asap.

---

### Post by owiknowi on 2011-03-14
hi shriner,

tried the iwconfig command with the results as can be seen in the attached file.

updated u10.04.2 (even with suggested updates) but to no avail.
installed kernel is now 2.6.32-30 (<2.6.34) so that would be the last resort...

but since i want to use a lts version i hesitate on updating the kernel other then trough the official supported channels...

but i really appreciate your suggestions very much and learned a few new things too.

regards, owiknowi

edit: tried kademar with kernel 2.6.37 and wireless came up without a problem.
so i'll give a kernel upgrade to >=2.6.34 a try.

---

### Post by owiknowi on 2011-03-29
in the latest newsletter on distrowatch.com there's an interesting article written by jesse smith ([http://distrowatch.com/weekly.php?issue=20110328#qa](http://distrowatch.com/weekly.php?issue=20110328#qa)) on this topic.

since i did not succeed in getting the intel wireless to work neither with u10.04.2 nor u10.10, i've switched to penguins who do support it (mandriva 2010.2, unity 2010.2, pardus kurumsal 2, etc).

another -maybe better- solution for me seems to avoid intel and switch to amd in the future?

---

### Post by chili555 on 2011-03-29
> another -maybe better- solution for me seems to avoid intel and switch to amd in the future?Does AMD make a wireless card?

The trouble is that 99% of all Intel wireless cards, including three in my house, work flawlessly. If the card works flawlessly with, for example, Mandriva, how is this an Intel problem?

---

### Post by owiknowi on 2011-03-29
er, right, dunno... they should, i think... or not? yes: they should, definitely!

btw. never understood the closed source hardware troubles:
1. i do get and need(!) a cd with drivers in order to make everything work with windos
2. i can't however get (read: buy) one to make things work with an open source os

so it's indeed not just an intel problem: it goes way beyond just the chips bakery.

---

### Post by chili555 on 2011-03-29
> **owiknowi said:**
> er, right, dunno... they should, i think... or not? yes: they should, definitely!

btw. never understood the closed source hardware troubles:
1. i do get and need(!) a cd with drivers in order to make everything work with windos
2. i can't however get (read: buy) one to make things work with an open source os

so it's indeed not just an intel problem: it goes way beyond just the chips bakery.If you have a proprietary, closed-source driver because you imagine you have trade secrets, you bind it up in a .exe that's only available on a CD if you buy the product.

Open source drivers are freely available for anyone to see and are therefor included in the kernel by default.

---

### Post by owiknowi on 2011-03-29
nice point of view.

i'll switch myself off for the next 3.86 years and ponder on that a bit more.

---

