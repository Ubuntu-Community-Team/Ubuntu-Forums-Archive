---
title: "Wireless networking refuses to be enabled"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by cracker89 on 2010-11-03
I have a compaq c784tu and it was shitty with xp. Vista is quite crap, so i turned over to ubuntu 10.4. The configuration of the laptop is: 1.73 GHz Intel Pentium Dual Core Processor T2370 with 1-MB L2 Cache, 533 MHz FSB featuring Intel Mobile 945GML Express Chipset Motherboard, 2-GB PC2-5300 DDR2 667 MHz SDRAM (Maximum 4-GB in 2 slots), a 160-GB SATA 5400 rpm Hard Disk Drive and 8x Super Multi Double Layer (8.5 GB) Slot-in DVD Writer. 
 
Everything worked like a charm and I was able to connect to the internet through a public wifi network. However, I came home this week to my mothers house, where they have a dsl-router to connect to the internet whih uses bridge mode pppoe. I tried to connect to the internet through it, and it initially couldnt. However, I got around that by doing a clean install of ubuntu. I was able to then connect to the internet using "sudo pppoeconf" and "sudo pon dsl-provider"
 
One night the network manager app on the top left disappeared and would not come on. I figured I had fried my wifi adapter, however, lspci -v confirmed its presence. Further, "system>admn>system testing" detected the adapter aswell. I tried the iwconfig command in the terminal the result was:
 
lo no wireless extensions
 
eth0 no wireless extensions
 
wlan0 IEEE 802.11bg ESSID:off/any
Mode: Managed Access Point: Not-Associated Tx-Power off
Retry long limit:7 RTS thr:off Fragment thr: off
Power Management:off
 
I tried to turn it on using the "ifconfig wlan0 up" and "ifconfig eth0 up" but the terminal displays "SIOCSIFFLAGS: Permission denied". 
 
I did a fresh install of ubuntu which re-established the network manager applet on the top panel and the first start after the fresh install was succesful, in the sense that I could detect the wifi connection and use sudo pon to connect to the net. However, one restart later, it was gone again and the "Enable Wireless" option has since become disabled, i.e. I cannot click it. All the above details are also the same.
 
I just cannot get the wireless to get enabled, except for the first session after a fresh install (I have confirmed this with 3-4 fresh installs) :mad::mad::mad:
 
I have an Atheros AR5001 wireless adapter and Realtek RTL-8139/8139C/8139C+ (rev 10). lspci -v confirms the same and the kernel drivers being used are ath5k and 8139too respectively.
 
I am relatively new to linux. Any ideas? 
 
Or what I really mean is HELP! :confused:
 
Everything else works perfectly (I havent tried wired networking yet though. would it make sense?)

---

### Post by abdqayyum on 2010-11-03
rfkill list
rfkill unblock 0
rfkill unblock 1
rfkill unblock 2

hope that works ...

---

### Post by P4man on 2010-11-03
You are probably just missing the firmware for the wifi card, which ubuntu may not redistribute (and the reason it sometimes works may be related to booting windows which loads the firmware to the card and it might stick during a reboot). Connect the wired connection. Then go to system > administration > additional hardware drivers. If it prompts to install drivers for the wifi card, then go ahead and do that.

If that fails to bring up something useful, please post the output of


```
lspci
```

and

```
lsusb
```

and 

```
sudo rfkill list
```

BTW, use [ code ] tags around such output to make it easier for us to read and get rid of the smileys :)

---

### Post by cracker89 on 2010-11-03
Right. First off, thanks for the prompt reply.. ubuntuforums kills!! :guitar:
 
@abdqayyum -that didnt work. nothing is blocked. I ran the unblock commands too, no avail. 
 
@p4man - I only have ubuntu standalone.. no windows anywhere nearby. can u tell me how i can capture sessions on console. couldnt figure it out... 
 
However - the hardware manager does not prompt for any drivers.. It prompts to connect to the internet.. and then says there are no propeitry drivers on the system.. 
 
Ill put the output of ```
 lspci 
``` after a bit.. reformatiing my laptop once more!
 
 
```
 rfkill 
``` does not indicate anything to be blocked. ill put the exact output up of that too.. meanwhile, could you tell me if theres chances that the wifi card might have fried, but it would still appear on the hardware config?

---

### Post by P4man on 2010-11-03
> **cracker89 said:**
> 
 
@p4man - I only have ubuntu standalone.. no windows anywhere nearby. can u tell me how i can capture sessions on console. couldnt figure it out... 

Easiest is just doing it from the ubuntu machine with a wired connection. The Additional hardware drivers applet also requires a working internet connection. If temporarily connecting a cable is not possible, you can redirect the output of the above commands to a file like this:

lspci > lspci.txt

that will create a file lspci.txt in your homefolder, you can copy it to a USB stick and then post if from the other machine. Same with the other commands.

 > 
However - the hardware manager does not prompt for any drivers.. It prompts to connect to the internet.. and then says there are no propeitry drivers on the system.. 

But did or didnt you connect to the internet?
 
>  rfkill does not indicate anything to be blocked. ill put the exact output up of that too.. meanwhile, could you tell me if theres chances that the wifi card might have fried, but it would still appear on the hardware config?

Anything is possible but I highly doubt the hardware was "fried". Im sure its still fine.

---

### Post by cracker89 on 2010-11-03
>  lspci > lspci.txt

that will create a file lspci.txt in your homefolder, you can copy it to a USB stick and then post if from the other machine. Same with the other commands 
Why has noone ever posted this elsewhere on the  net :P
 
 
And no, I didnt connect to the internet. Now even after a fresh install of ubuntu, no connection subsists. I dont have a usb cord or ethernet wire right now, so i cannot connect it yet. Will do later.
 
Heres the outputs of the respective commands. 
[ATTACH]174405[/ATTACH]

[ATTACH]174406[/ATTACH]

[ATTACH]174407[/ATTACH]
 
And wait - the rfkill suddenly displays hard blocked on wlan - i think this should fix it. :confused::confused:

---

### Post by cracker89 on 2010-11-03
```
 [EMAIL="kakar@Cracker:~$"]kakar@Cracker:~$[/EMAIL] sudo rfkill list
0: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: yes
 
```
right i think this is it!
 
...
ermm...
What now?

---

### Post by P4man on 2010-11-03
hard blocked means a hardware switch is set to off. Your laptop probably has a button or keycombo to enable/disable wifi. press it.

---

### Post by cracker89 on 2010-11-03
It does. And I tried that. That was one of the things I tried first. Doesnt do anything. Any other way round it? 
Infact nothing happens..

---

### Post by P4man on 2010-11-03
and if you press it, and rerun the rfkill command, does it keep saying its blocked? Is this a hardware switch or a Fn key combo?

---

### Post by cracker89 on 2010-11-03
Its a hardware switch. I anticipated a keyboard layout defect too and tried the fn keys with all the keys too, no use. And yes, you pretty much have what happens. 
 
I press it on and off, it stays the same and rfkill result subsists

---

### Post by cpmman on 2010-11-03
I had a Medion 96640 which had a HP modified BIOS containing options:

wireless : last state
wireless : off
bluetooth : last state
bluetooth : off

---

### Post by cracker89 on 2010-11-03
Heres an image of the keyboard. Its the highlighted key. The laptop came with vista and then it used to turn blue and red on turning it on and off. I switched to xp, it stayed orange and now it stays blue. The key i mean.
 
[ATTACH]174408[/ATTACH]

---

### Post by cracker89 on 2010-11-03
[quote] 
 
**Re: Wireless networking refuses to be enabled** 
I had a Medion 96640 which had a HP modified BIOS containing options:
 
wireless : last state
wireless : off
bluetooth : last state
bluetooth : off
 
[\quote]
 
right. so i go into the bios? i'll try it and get back to u... ]
Checked the bios. nope. No such option. Any way to get around the hard block? the switch isnt working.. do I open up the casing yet?

---

### Post by P4man on 2010-11-03
Its possible the wifi switch requires firmware/drivers to work properly, so this may be a dead end until you can connect the laptop to the internet.

Two things you might try: if you still have dual boot with windows, boot windows and enable the wifi, then reboot in ubuntu. See if it helps. 

Other thing to try:

```
sudo modprobe -rv ath5k
sudo modprobe acer-wmi
sudo modprobe -v ath5k
```

---

### Post by cracker89 on 2010-11-03
> **P4man said:**
> Its possible the wifi switch requires firmware/drivers to work properly, so this may be a dead end until you can connect the laptop to the internet.
 
Two things you might try: if you still have dual boot with windows, boot windows and enable the wifi, then reboot in ubuntu. See if it helps. 
 
Other thing to try:
 
```
sudo modprobe -rv ath5k
sudo modprobe acer-wmi
sudo modprobe -v ath5k
```
 
Hey man.. got an ethernet wire. Am now online.. ok here is where I have gotten. I am running all updates and upgrades first. Then i came across ndiswrapper. Do you think that would help or be of any relation to this?
 
I do not have a dual book with xp. Wiped it clean off. I tried those commands, will post the output in a min.. 
 
And another thing - under 
 
```
 iwconfig wlan0
----snip-----
----paste----
Mode:Managed   Access Point: Not-Associated  Tx-Power=off  
```
 
And the power management is off. Any way I could by pass the rfkill and make the driver ignore it?

---

### Post by P4man on 2010-11-03
> **cracker89 said:**
> Hey man.. got an ethernet wire. Am now online.. ok here is where I have gotten. I am running all updates and upgrades first. Then i came across ndiswrapper. Do you think that would help or be of any relation to this?

ndiswrapper is a last resort. You shouldnt need it.
 
> I do not have a dual book with xp. Wiped it clean off. I tried those commands, will post the output in a min.. 
 
And another thing - under 
 
```
 iwconfig wlan0
----snip-----
----paste----
Mode:Managed   Access Point: Not-Associated  Tx-Power=off  
```
 
And the power management is off. Any way I could by pass the rfkill and make the driver ignore it?

AFAIK rfkill can only report that hard block, I dont see how it could "get around it". Basically your wifi radio is turned off, it gets no power.

But now that you have a wired connection, try the additional driver applet again.

---

### Post by cracker89 on 2010-11-03
Right. did that > it says no propietry drivers are installed. Doesnt prompt for anything.

And ok. I didnt exactly understand the rfkill process. Meanwhile, i've found a lot of threads concerning atheros wifi cards. But where there dont work at all, mine did initiially - like for a good 4-5 months. During that time the button had no effect on the wifi. 

Can we somehow make the power turn on to the card?

Here's the output for those commands:

```
 

kakar@Cracker:~$ sudo modprobe -rv ath5k
rmmod /lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
rmmod /lib/modules/2.6.32-21-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/2.6.32-21-generic/kernel/net/wireless/cfg80211.ko
rmmod /lib/modules/2.6.32-21-generic/kernel/drivers/leds/led-class.ko

kakar@Cracker:~$ sudo modprobe -v ath5k
insmod /lib/modules/2.6.32-21-generic/kernel/drivers/leds/led-class.ko 
insmod /lib/modules/2.6.32-21-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/2.6.32-21-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko 

kakar@Cracker:~$ sudo modprobe acer-wmi
FATAL: Error inserting acer_wmi (/lib/modules/2.6.32-21-generic/kernel/drivers/platform/x86/acer-wmi.ko): No such device


```

.\
.
.
.
Man - you are the greatest god that ever walked the valkyries. one of those commands got it working... do ubuntu forums have rep points? Its working.

 Thank you a bunch man.. anything I can do, grateful!

---

### Post by P4man on 2010-11-03
well you're not there quite yet I suspect upon rebooting it will fail again. Let me know if thats the case, then we can solve that too.

---

### Post by cracker89 on 2010-11-03
> **P4man said:**
> well you're not there quite yet I suspect upon rebooting it will fail again. Let me know if thats the case, then we can solve that too.

Hmm! I see. And running those commands again will fix it again? I'll let you know, although I wont be rebooting for a loooooooong time :D

---

### Post by cracker89 on 2010-11-07
Alright, P4man, it didnt turn off on reboot. That's right, havent rebooted since tilll a few moments ago :P someday this things going to burn through the table top, however, I would be really grateful if you could explain to me, in a slightly jargon-downed way what exactly we did with modprobe.. ? 
Much grateful-ness

---

### Post by P4man on 2010-11-07
modprobe -r just unloads a linux kernel module (=driver), and modprobe loads it again. loading acer-wmi didnt even work since your machine doesnt support it, so you might as well not have typed that.

 Thats why im confused it "stuck".  Unless the actual solution was something you did earlier.

BTW, if you rebooted, it may still not stick. Try turning the machine off for a while, and power it on again.

---

### Post by cracker89 on 2010-11-07
No I left it off for a bit.. had lunch then got back to it.. Seems to have stuck and its been working smoothly since. Hmm.. ok yea i figured the accer thing.. this worked for me though. Thanks a bunch. I'll try and remember it..

---

### Post by cracker89 on 2010-11-07
P.S.: what did you have in mind for the permanent soln?

---

### Post by P4man on 2010-11-07
I think connecting it to the internet and running the updates is what actually solved it. All it needed then was a reboot or reloading the atheros module. Thats my guess anyway.

---

### Post by cracker89 on 2010-11-07
No, my updates didnt finish till after it started working.. I was probably on update file number 40 or something when it started up.. the output on rfkill changed immediately after running modprobe commands... I'm pretty much convinced it was ur commands that did it.. marking it solved.

---

