---
title: "Radio switched off by hibernate mode"
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by Ahlforn on 2009-07-25
Hey,

Im very new to linux, so im having some trouble solving this problem by myself and thought i would ask around here :)

I recently installed 9.04 with Gnome and was pleased to see how easy it was to connect to my wireless network. My laptop have a software wireless kill switch and it had been turned off (or well, the wireless radio was on) from back when Windows was installed. So all worked well, until i put my laptop into hibernation, not knowing it would by default turn the wireless radio off.

My laptop is produced by some tiny danish company that haven't provided updated software for any OS for years, so no chance of a linux driver for the hardware switch.

Now my question is: is there a way to turn the radio on again? I mean, since Ubuntu had no problem switching it off when going into hibernation, it should be possible to turn it back on, shouldn't it?

Heres a bit system info

dmesg | grep ipw
```
[   10.061800] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   10.061805] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   10.062302] ipw2200 0000:02:02.0: power state changed by ACPI to D0
[   10.062315] ipw2200 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[   10.062886] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   10.062932] ipw2200 0000:02:02.0: firmware: requesting ipw2200-bss.fw
[   10.252182] ipw2200: Radio Frequency Kill Switch is On:
[   10.259906] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```
sudo lshw -C network
```
*-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:08:55:cb
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:5f:4b:e2
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=128 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 16:4f:18:aa:40:84
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```
cat /sys/bus/pci/drivers/ipw2200/*/rf_kill
```
2
```

I just want to underline again, that the wireless network worked perfectly. Its just the radio on the wireless card that is turned off. I really hope someone have a solution, cause i really like this system.

---

### Post by martinbaselier on 2009-07-26
Can't you use the wireless switch to turn it back on?

afaik there is no command to switch it back on. There ia a parameter for the kernel module (the driver) which is about the power I haven't experimented with it yet, though.

---

### Post by Ahlforn on 2009-07-26
Hehe if only it was that easy. No the hardware switch (a switch on the side of the laptop with a on and off sate) doesn't work since its software controlled and the software to detect what state the hardware switch is in doesnt exist for Linux (and even is severely outdated on windows).

---

### Post by Ahlforn on 2009-07-27
Nobody knows of any solutions to this? I find it hard to believe that such a stupid little thing is all it takes to stop me from using Linux. But then again, a laptop without wireless network isnt worth much.

---

### Post by martinbaselier on 2009-07-27
I got the same card, but I have a hardware switch.
I've run modinfo ipw2200
The only option I see for radio is to turn it default off.

Still you could try creating a config file:

echo option ipw2200 disable=0 | sudo tee /etc/modprobe.d/ipw2200.conf

And either reload the module or reboot.
reloading:
sudo modprobe -r ipw2200
sudo modprobe ipw2200

I found this link:
[http://ipw2200.sourceforge.net/README.ipw2200](http://ipw2200.sourceforge.net/README.ipw2200)

There is a part there about radio on/off too.

When you do:
```

cat /sys/bus/pci/drivers/ipw2200/0000\:02\:02.0/rf_kill

```
Does it show 0?
If not, try:
```

echo 0 | sudo tee /sys/bus/pci/drivers/ipw2200/0000\:02\:02.0/rf_kill

```

---

### Post by Ahlforn on 2009-07-27
Hi and thanks a lot for responding. I've tried creating the config file and got these results:

When using the line you wrote i got this:
```
ahlforn@Redcube:~$ sudo rm /etc/modprobe.d/ipw2200.conf
ahlforn@Redcube:~$ echo option ipw2200 disable=0 | sudo tee /etc/modprobe.d/ipw2200.conf
option ipw2200 disable=0
ahlforn@Redcube:~$ sudo modprobe -r ipw2200
WARNING: /etc/modprobe.d/ipw2200.conf line 1: ignoring bad line starting with 'option'
ahlforn@Redcube:~$ sudo modprobe ipw2200
WARNING: /etc/modprobe.d/ipw2200.conf line 1: ignoring bad line starting with 'option'
```When i changed "option" to "options" i got this:
```
ahlforn@Redcube:~$ echo options ipw2200 disable=0 | sudo tee /etc/modprobe.d/ipw2200.conf
options ipw2200 disable=0
ahlforn@Redcube:~$ sudo modprobe -r ipw2200
ahlforn@Redcube:~$ sudo modprobe ipw2200
```cat /sys/bus/pci/drivers/ipw2200/0000\:02\:02.0/rf_kill
Returned: 2

echo 0 | sudo tee /sys/bus/pci/drivers/ipw2200/0000\:02\:02.0/rf_kill
No effect :/

As far as i got read from your link, 2 mean the switch it still active, shutting the radio off:
```
rf_kill
    read - 
    0 = RF kill not enabled (radio on)
    1 = SW based RF kill active (radio off)
    2 = HW based RF kill active (radio off)
    3 = Both HW and SW RF kill active (radio off)
    write -
    0 = If SW based RF kill active, turn the radio back on
    1 = If radio is on, activate SW based RF kill

    NOTE: If you enable the SW based RF kill and then toggle the HW

      based RF kill from ON -> OFF -> ON, the radio will NOT come back on

```I have had no success trying to edit the files in /sys/bus/pci/drivers/ipw2200/0000\:02\:02.0/.

If i could just disable the switch it would solve all my problems. I have absolutely no use for that switch so if i could and if it would help i would even rip that damn thing out of my laptop.

---

### Post by martinbaselier on 2009-07-27
> 
echo 0 | sudo tee /sys/bus/pci/drivers/ipw2200/0000\:02\:02.0/rf_kill
No effect :/

Do you mean the value doesn't change or that iwconfig still shows radio is off?
Edit: tested it with hwswitch turned off: The value stays at 2. 


The problem is not the software switch. There is a hardwareswitch too and that's the problem. It's a strange implementation to replace that with a software switch. And the hardware setting is remembered when rebooting. Did you already check the bios and reset it to default? Just a thought. Or take out the accu (without adapter of course) for a few minutes.

---

### Post by Ahlforn on 2009-07-27
Yeah the value doesn't change in the file and iwconfig still says the radio is off after that line.

I've searched the BIOS and there is no mention of anything network related. No wireless settings at all. No switch settings. I've tried pulling the power + battery and it doesn't change anything at all :/

---

### Post by martinbaselier on 2009-07-27
Could you post a link to the switch utility for windows? I hope it is an executable.

---

### Post by Ahlforn on 2009-07-27
Sure, here is a link to the FTP of the danish company that produce these laptops:

[ftp://ftp.abook.dk/ABook%20Drivers/3000txi/Windows%20XP/Easy%20Button/](ftp://ftp.abook.dk/ABook%20Drivers/3000txi/Windows%20XP/Easy%20Button/)

I hope it makes any sense :)

---

### Post by Ahlforn on 2009-08-04
I still havn't found a solution to this problem, so if anyone know of one, please let me know.

---

### Post by U-russia on 2011-05-06
Ok, this is an old topic but somebody could find it through search  so, the solution can be not easy  i had such problem and it`s not OS question, because i got it on Linux as on Win systems.  i just had to disassemble laptop and made hard reset(battery) for BIOS, but may be &quot;load setup defaults&quot;  could help or reinstall just the WIFI card.  other solution not worked for me ; hope this can help!   ps: it was about &quot;Radio Frequency Kill Switch is On&quot;

---

