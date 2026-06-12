---
title: "wireless adapter is unclaimed"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by behnam.mn on 2011-01-06
Hey Guys,
I have HP Pavilion dv2860ee laptop with an intel wireless adapter ipw3945 on it. I recently installed ubuntue 10.10 on the laptop but ubuntu does not recognize my wireless adapter. I'm some how new to ubuntu but I almost tried everything that I could find from google to install drivers but they didn't work and wireless adapter is still unclaimed. :(
any body could help me with that?
thanks
Behnam

---

### Post by chili555 on 2011-01-06
The correct driver is built in to the kernel. If it doesn't load and start the wireless card, something else is wrong. Let's see what it is. We'll load it and check for clues from the kernel. Open Applications > Accessories > Terminal and do:```
sudo modprobe iwl3945
rfkill list all
dmesg | grep iwl
```Post the result and we'll proceed.

---

### Post by behnam.mn on 2011-01-07
Sorry for late reply, I wasn't home for a couple of hours
here is the results:


0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
2: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes



[  148.253128] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[  148.253130] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[  148.253209] iwl3945 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  148.253223] iwl3945 0000:07:00.0: setting latency timer to 64
[  148.308449] iwl3945 0000:07:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[  148.308452] iwl3945 0000:07:00.0: Detected Intel Wireless WiFi Link 3945BG
[  148.308607] iwl3945 0000:07:00.0: irq 48 for MSI/MSI-X
[  148.346066] phy0: Selected rate control algorithm 'iwl-3945-rs'

---

### Post by bkratz on 2011-01-07
I am sure Chili will decode the rest, but the hardblocked comments refer to a (wireless)switch you don't have set to the correct position, or a keystroke combination required for the same thing.

---

### Post by chili555 on 2011-01-07
Exactly. Please switch the switch and I'm confident you'll be all set.

---

### Post by behnam.mn on 2011-01-07
first, there is a physical switch on the laptop and when I change it to the "on" position, the small light near it remains red and do not turn to blue (in Windows when I turn on the wireless adapter with the switch, the light turns to blue)

The other thing is that, when I boot the Ubuntu, the result from the code:
lshw -C network

shows that the wireless is "unclaimed" and ubuntu does not even recognize the wireless adapter and doesn't show it in the network manager but after I run the codes you provided above, Ubuntu will recognize it but it is "disabled".

thank you for your time,
looking forward to hearing from you

---

### Post by behnam.mn on 2011-01-07
first, there is a physical switch on the laptop and when I change it to the "on" position, the small light near it remains red and do not turn to blue (in Windows when I turn on the wireless adapter with the switch, the light turns to blue)

The other thing is that, when I boot the Ubuntu, the result from the code:
lshw -C network

shows that the wireless is "unclaimed" and ubuntu does not even recognize the wireless adapter and doesn't show it in the network manager but after I run the codes you provided above, Ubuntu will recognize it but it is "disabled".

thank you for your time,
looking forward to hearing from you

---

### Post by behnam.mn on 2011-01-07
first, there is a physical switch on the laptop and when I change it to the "on" position, the small light near it remains red and do not turn to blue (in Windows when I turn on the wireless adapter with the switch, the light turns to blue)

The other thing is that, when I boot the Ubuntu, the result from the code:
lshw -C network

shows that the wireless is "unclaimed" and ubuntu does not even recognize the wireless adapter and doesn't show it in the network manager but after I run the codes you provided above, Ubuntu will recognize it but it is "disabled".

thank you for your time,
looking forward to hearing from you

---

### Post by behnam.mn on 2011-01-07
first, there is a physical switch on the laptop and when I change it to the "on" position, the small light near it remains red and do not turn to blue (in Windows when I turn on the wireless adapter with the switch, the light turns to blue)

The other thing is that, when I boot the Ubuntu, the result from the code:
lshw -C network

shows that the wireless is "unclaimed" and ubuntu does not even recognize the wireless adapter and doesn't show it in the network manager but after I run the codes you provided above, Ubuntu will recognize it but it is "disabled".

thank you for your time,
looking forward to hearing from you

---

### Post by behnam.mn on 2011-01-07
Sorry for several duplications of the post,
I tried to submit the reply but it was not working, so I did that several times and after a while all of them submitted at the same time

---

### Post by behnam.mn on 2011-01-07
first, there is a physical switch on the laptop and when I change it to the "on" position, the small light near it remains red and does not turn to blue (in Windows when I turn on the wireless adapter with the switch, the light turns to blue)

The other thing is that, when I boot the Ubuntu, the result from the code:
lshw -C network

shows that the wireless is "unclaimed" and ubuntu does not even recognize the wireless adapter and doesn't even show it in the network manager but after I run the codes you provided above, Ubuntu will recognize it but it is "disabled".

thank you for your time,
looking forward to hearing from you

---

### Post by chili555 on 2011-01-07
Please run:```
sudo rfkill unblock all
rfkill list all
```Does it still show as blocked? Press the switch and try again:```
sudo rfkill unblock all
rfkill list all
```Still blocked? Please let us know if anything has changed.

I hope your six identical postings are an unfortunate mistake. Please do not multiple post the same thing.

---

### Post by behnam.mn on 2011-01-07
Amazing,

Ubuntu detected the wireless adapter and it's working perfect.
thank you very much for your help,
but I think I need to run these two codes:

sudo modprobe iwl3945
sudo rfkill unblock all

every time I restart my laptop. am I right?


about the same posts, as I said in the edit of one of them, it was a mistake. I was trying to post the reply but it failed so I post it several times and after a few minutes, they all appeared at the same time. I couldn't find out how to delete them.

---

### Post by chili555 on 2011-01-07
Let's see if we can coax the laptop a bit. Please do:```
sudo gedit /etc/rc.local
```Add a line above the line Exit 0:```
rfkill unblock all
```Proofread carefully, save and close gedit. The next time you reboot it ought to work perfectly but post back if you need further help.

---

### Post by behnam.mn on 2011-01-07
I also add the code 

modprobe iwl3945

in the file and now wireless is working even after restarting the laptop. there is a small issue which is not really important. Actually I should turn on the physical switch before ubuntu is booting, otherwise it won't work.
thanks,
Behnam

---

