---
title: "Acer 4551g Wireless is Disabled"
date: 2011-06-25
forum: Networking &amp; Wireless
---

### Post by kalookp on 2011-06-25
Hi, my laptop is an Acer 4551g with Acer Nplify 802.11b/gn as the connection chip. I've just installed ubuntu 11.04 today and when i got to the connection column, it greyed out my Wireless Networks and said that wireless is disabled.

The Ubuntu dual boots with my Windows 7 and the connection works perfectly fine on Windows 7. But once it got onto Ubuntu, the wifi led just goes off and never comes on. 

I'm new to Ubuntu but i really wanna learn how to use it, so please can someone help resolve this problem?

Thanks in advance!

---

### Post by chili555 on 2011-06-25
Let's take a look under the hood and see what you have. Please open a terminal and run and post:```
lspci -nn
lsmod | grep acer
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by kalookp on 2011-06-25
Hey, thanks for replying! 

I entered the codes and this was what it showed me :

 [FONT=Calibri]SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 41)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c] (rev 40)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Redwood [Radeon HD 5600 Series] [1002:68c1]
02:00.1 Audio device [0403]: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series] [1002:aa60]
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
06:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
acer@ubuntu:~$ lsmod | grep acer
acer_wmi 23771 0 
sparse_keymap 13898 1 acer_wmi
acer@ubuntu:~$ rfkill list all
0: acer-wireless: Wireless LAN
Soft blocked: yes
Hard blocked: no
1: acer-bluetooth: Bluetooth
Soft blocked: yes
Hard blocked: no
2: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
3: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
acer@ubuntu:~$ ^C
acer@ubuntu:~$ 
 
 [/FONT]
  I do realise that the Acer Wireless was soft blocked, but i have no idea what's happening....please take a look.

Thanks again!

---

### Post by chili555 on 2011-06-26
The module acer-wmi often, not always, blocks wireless because it doesn't always properly translate key presses into action. The tell-tale symptom is often:> the wifi led just goes off and never comes on. Let's remove it and see if the wireless comes to life:```
sudo rmmod -f acer-wmi
```You may also need to install the correct driver for your card. We can tell if it's installed by looking at the list of loaded modules:```
lsmod | grep wl
```If it is not installed, the command above will return nothing. If so, walk the Acer over to the router, get a wired ethernet connection and do:```
sudo apt-get install bcmwl-kernel-source dkms
sudo modprobe wl
```If removing acer-wmi helps, we'll need to tweak one file to make it persistent.

---

### Post by kalookp on 2011-06-26
Oh cool! Thanks! turns out it was the Acer-wmi causing the problem, it came back to life and detected the router afterwards.

So how are we going to make it permanent?

---

### Post by chili555 on 2011-06-26
> So how are we going to make it permanent?We will blacklist acer-wmi:```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```You should be all set. Please use the thread tools at the top to mark the thread Solved.

---

### Post by kalookp on 2011-06-26
sorry, but when i typed in 
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
nothing seems to have happened...it just brought me back to 
root@ubuntu/home/acer#

When i typed 
echo "blacklist acer-wmi"

it came back with
blacklist acer-wmi

what am i doing wrong??

---

### Post by walt.smith1960 on 2011-06-26
Try a restart and see if your wireless comes alive.

---

### Post by chili555 on 2011-06-26
> sorry, but when i typed in
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
nothing seems to have happened...it just brought me back to
root@ubuntu/home/acer#Something did happen; it echo'ed the line into the file. A common misunderstanding is that not every command returns a concrete confirmation, smoke, sparks, music, etc.

When a command simply comes back to the command prompt, it means, roughly, "Command executed as requested, sir, and I have no errors or warnings to report. Next?" In fact, the smartest go-fast diagnosticians on this forum, the guys who I learn from, often ask for the results of a command they are pretty sure *isn't* going to work so they can learn the specific warning or error. The specifics sometimes tell us what's needed and currently missing.

When you next boot, I'm confident the wireless will work as expected.

Just for giggles, if you want to check, ask for the file to be read out and see if the line is now at the end of the file:```
cat /etc/modprobe.d/blacklist.conf
```If it's there, and I'm confident it is, you should be all set.

---

### Post by Ildanach on 2011-08-22
I am having the exact same problems. However, after following all the steps my wireless still isn't work. I had been using the command ```
sudo modprobe -r acer-wmi
``` in order to enable it (however, i had to do this every time I restarted). However, this just stopped working. I'm now getting the message that the wireless is disabled by hardware switch (it isn't). Help?

---

### Post by chili555 on 2011-08-22
> **Ildanach said:**
> I am having the exact same problems. However, after following all the steps my wireless still isn't work. I had been using the command ```
sudo modprobe -r acer-wmi
``` in order to enable it (however, i had to do this every time I restarted). However, this just stopped working. I'm now getting the message that the wireless is disabled by hardware switch (it isn't). Help?Please post:```
rfkill list all
lsmod | grep wmi
```Thanks.

---

### Post by Ildanach on 2011-08-23
well, it just started working again... it seems to be going on and off. Here it is with it working, if it goes out again i'll post that too. 

Here's the output of rfkill list all:
```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

Here's the output of lsmod | grep wmi:
```
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

```

Thank you so much for the help, i really didn't want to give up on ubuntu, but i wasn't sure i'd be able to get it working.

---

### Post by chili555 on 2011-08-23
> if it goes out again i'll post that too.I hope it won't go out, but if it does, post back and I'll be glad to help.

---

