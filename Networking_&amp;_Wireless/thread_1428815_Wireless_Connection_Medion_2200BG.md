---
title: "Wireless Connection Medion 2200BG"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by Iffraen on 2010-03-13
Hello people!
I installed Ubuntu on my Medion Laptop.
Though I can't get my wireless internet working.
I checked Google for answers and several ubuntu forum topics, though the question remains unanswered.
My laptop has an On/Off button for my wireless internet and I have read that this button doesnt work in Ubuntu. But there's got to be an answer, right?
So, can anyone help me?
( Btw, my English sucks, sorry ( I'm Dutch ) )
Ps. I'm new with Ubuntu so explain it easy :P
Thanks in advance!

---

### Post by Iffraen on 2010-03-13
Please help?

---

### Post by chili555 on 2010-03-13
Please open Applications > Accessories > Terminal and do:```
sudo lshw -C network
dmesg | grep ipw
```Post the results and we'll proceed.

---

### Post by Iffraen on 2010-03-13
sudo kevin@kevin-laptop:~$ sudo lshw -C network
[sudo] password for kevin: 
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth1
       version: 05
       serial: 00:15:00:20:54:69
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=radio off
       resources: irq:19 memory:c8006000-c8006fff
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:b0:ce:70
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:18 ioport:4000(size=256) memory:c8007000-c80070ff memory:24000000-2401ffff(prefetchable)

kevin@kevin-laptop:~$ dmesg | grep ipw
[   11.834552] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   11.834557] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   11.834643] ipw2200 0000:06:05.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   11.834721] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   11.834771] ipw2200 0000:06:05.0: firmware: requesting ipw2200-bss.fw
[   12.202714] ipw2200: Radio Frequency Kill Switch is On:
[   12.204736] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)


Here you are :)

---

### Post by chili555 on 2010-03-13
> ipw2200: Radio Frequency Kill Switch is On:And here *you* are! We must figure out how to trigger the switch.

Maybe it is just the LED that doesn't light up when the button is pressed. Let's take a look at:```
sudo rfkill unblock all
rfkill list
lsmod | grep -e wmi -e acpi
```Thanks.

---

### Post by Iffraen on 2010-03-13
kevin@kevin-laptop:~$ sudo rfkill unblock all
[sudo] password for kevin: 
kevin@kevin-laptop:~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
kevin@kevin-laptop:~$ lsmod | grep -e wmi -e acpi
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

This is what it says.
It is like Chinese to me haha :P

---

### Post by chili555 on 2010-03-13
> It is like Chinese to me hahaSometimes, it is just as important to see what is *not* there. In this case, nothing that can help us.

Is this machine dual-booting with Windows? Have you checked in the BIOS?

[http://superuser.com/questions/40702/wireless-on-medion-md96500-intel-pro-wireless-2200bg-running-windows-7](http://superuser.com/questions/40702/wireless-on-medion-md96500-intel-pro-wireless-2200bg-running-windows-7)> For some reason - which I am still trying to get to the bottom of - when you use the repair option "wireless adapter" is "disabled" in the BIOS. This happens rarely but occasionally - it has happened to me twice!

Solution - Press F2 to enter SETUP when rebooting your laptop and set "wireless adaptor" to "last status"

No amount of downloading drivers and changing firmware will improve your situation until you change your BIOS setting.

---

### Post by Iffraen on 2010-03-13
Nope, it isnt.
Its just plain Ubuntu, nothing more.

Thanks for helping me by the way :)

---

### Post by Iffraen on 2010-03-13
Anyone?

---

### Post by chili555 on 2010-03-13
Please do:```
sudo rmmod -f iwp2200
sudo modprobe ipw2200 bt_coexist=1
```Any improvements?

---

### Post by Iffraen on 2010-03-15
Hey!
Yesterday I was in France, so I couldn't answer your post.

I put in the code and when I pressed 'Enter' a pop-up showed up.
It said: Network
You are now offline/disconnected (Don't know which of the 2)

---

### Post by Iffraen on 2010-03-15
When i try to ping to my router it says: connect: Network is unreachable.
Maybe useful info?

---

### Post by Iffraen on 2010-03-15
Solved!
It had to change my wireless adapter to Last State in the BIOS.
I thought you had to do this if your system was dualbooting, so I didn't check that out earlier.
Haha Thanks, Chili555! :D

---

### Post by chili555 on 2010-03-15
> Network
You are now offline/disconnectedThat means your card is working and Network Manager is reporting that you are not connected to any of the available networks. Click the Network Manager icon and select from the available networks, supply any encryption details and connect.

Let's create a file to make the command permanent. Please do:```
sudo gedit /etc/modprobe.d/ipw2200.conf
```It will be a new file. Add two lines:```
alias eth1 ipw2200
options ipw2200 bt_coexist=1
```Proofread save and close gedit. Usually, ipw2200 creates a wireless interface eth1. Check with:```
iwconfig
```If the wireless details are associated with other than eth1, substitute the interface in the file above.

---

