---
title: "Wireless does not work, my first Linux experience"
date: 2012-10-28
forum: Networking &amp; Wireless
---

### Post by Lunestic on 2012-10-28
I downloaded Lubuntu 12.10, my first time using Linux.

The wireless connection does not work.
Ethernet does.

Please help, thank you!

---

### Post by Linuxisfast on 2012-10-28
> **Lunestic said:**
> I downloaded Lubuntu 12.10, my first time using Linux.

The wireless connection does not work.
Ethernet does.

Please help, thank you!
Go to hardware drivers and enable drivers for your wireless chipset as indicated there, reboot and it will work.

---

### Post by chili555 on 2012-10-28
Please open a terminal and run and then post:```
lspci -nn | grep 0280
lsusb
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by Lunestic on 2012-10-28
> **Linuxisfast said:**
> Go to hardware drivers and enable drivers for your wireless chipset as indicated there, reboot and it will work.

How do you do that?

> **chili555 said:**
> Please open a terminal and run and then post:```
lspci -nn | grep 0280
lsusb
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

```
user@ubuntu:~$ lspci -nn | grep 0280
0a:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev c4)
user@ubuntu:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 138a:0018 Validity Sensors, Inc. 
Bus 001 Device 005: ID 04b3:310c IBM Corp. Wheel Mouse
Bus 001 Device 004: ID 0bda:58d8 Realtek Semiconductor Corp. 
user@ubuntu:~$ 

```

---

### Post by chili555 on 2012-10-28
> Intel Corporation Centrino Wireless-N 2230 [8086:0887]Hmmm. No 'additional drivers' for this Intel, I bet.

The driver is built-in already. If it's not working, there is another reason. Please run and post:```
dmesg | grep iwl
rfkill list all
```What kind of laptop is it?

---

### Post by Lunestic on 2012-10-28
> **chili555 said:**
> Hmmm. No 'additional drivers' for this Intel, I bet.

The driver is built-in already. If it's not working, there is another reason. Please run and post:```
dmesg | grep iwl
rfkill list all
```What kind of laptop is it?


```
user@ubuntu:~$ dmesg | grep iwl
[    5.781011] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    5.781014] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[    5.781138] iwlwifi 0000:0a:00.0: >pci_resource_len = 0x00002000
[    5.781141] iwlwifi 0000:0a:00.0: >pci_resource_base = ffffc900117fc000
[    5.781143] iwlwifi 0000:0a:00.0: >HW Revision ID = 0xC4
[    5.781289] iwlwifi 0000:0a:00.0: >irq 45 for MSI/MSI-X
[    5.839056] iwlwifi 0000:0a:00.0: >loaded firmware version 18.168.6.1
[    5.839291] iwlwifi 0000:0a:00.0: >CONFIG_IWLWIFI_DEBUG disabled
[    5.839294] iwlwifi 0000:0a:00.0: >CONFIG_IWLWIFI_DEBUGFS enabled
[    5.839296] iwlwifi 0000:0a:00.0: >CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    5.839298] iwlwifi 0000:0a:00.0: >CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[    5.839300] iwlwifi 0000:0a:00.0: >CONFIG_IWLWIFI_P2P disabled
[    5.839302] iwlwifi 0000:0a:00.0: >Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[    5.839413] iwlwifi 0000:0a:00.0: >L1 Enabled; Disabling L0S
[    5.846946] iwlwifi 0000:0a:00.0: >RF_KILL bit toggled to disable radio.
[    5.857336] iwlwifi 0000:0a:00.0: >device EEPROM VER=0x81c, CALIB=0x6
[    5.857339] iwlwifi 0000:0a:00.0: >Device SKU: 0x150
[    5.857342] iwlwifi 0000:0a:00.0: >Valid Tx ant: 0x3, Valid Rx ant: 0x3
[    5.857363] iwlwifi 0000:0a:00.0: >Tunable channels: 13 802.11bg, 0 802.11a channels
[    5.866268] ieee80211 phy0: >Selected rate control algorithm 'iwl-agn-rs'
user@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
user@ubuntu:~$ 

```

The laptop is a HP Pavillion dv6t-7000 qe.

---

### Post by chili555 on 2012-10-28
> 0: phy0: Wireless LAN
	Soft blocked: yes
	[COLOR="Red"]Hard blocked: yes[/COLOR]> [    5.846946] iwlwifi 0000:0a:00.0: >RF_KILL bit toggled to disable radio.Do you have a little slider or switch on that HP to turn on the wireless? Can you please switch it?

---

### Post by Lunestic on 2012-10-28
> **chili555 said:**
> Do you have a little slider or switch on that HP to turn on the wireless? Can you please switch it?

That's the thing, it does not switch on.  But when I'm on Windows, it turns on.

---

### Post by chili555 on 2012-10-28
> That's the thing, it does not switch on. But when I'm on Windows, it turns on.If you have any other confessions or relevant data, please tell me now.

Please do:```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
rfkill list all
```Any improvement from the button?

---

### Post by Lunestic on 2012-10-28
> **chili555 said:**
> If you have any other confessions or relevant data, please tell me now.

Please do:```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
rfkill list all
```Any improvement from the button?

```
user@ubuntu:~$ sudo modprobe -r hp-wmi
[sudo] password for user: 
user@ubuntu:~$ sudo rfkill unblock all
user@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
user@ubuntu:~$ 

```

Still cannot turn on the switch (a light is supposed to go on).

---

### Post by chili555 on 2012-10-29
> **Lunestic said:**
> ```
user@ubuntu:~$ sudo modprobe -r hp-wmi
[sudo] password for user: 
user@ubuntu:~$ sudo rfkill unblock all
user@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
user@ubuntu:~$ 

```

Still cannot turn on the switch (a light is supposed to go on).After you run this sequence of commands, does the button press change anything? Don't worry about the light for now:```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
rfkill list all
```Press wireless button.```
rfkill list all
```Press wireless button.```
rfkill list all
```Any changes?

I worked on a case a few weeks ago where the correct operation of the keys was restored by resetting the BIOS to Default. Please try that.

---

### Post by Lunestic on 2012-10-29
> **chili555 said:**
> After you run this sequence of commands, does the button press change anything? Don't worry about the light for now:```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
rfkill list all
```Press wireless button.```
rfkill list all
```Press wireless button.```
rfkill list all
```Any changes?

I worked on a case a few weeks ago where the correct operation of the keys was restored by resetting the BIOS to Default. Please try that.

Pressing the button yields no changes:

```
user@ubuntu:~$ sudo modprobe -r hp-wmi
[sudo] password for user: 
user@ubuntu:~$ sudo rfkill unblock all
user@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
user@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

I then rebooted and set BIOS to default, nothing changed.

Something I've noticed: before I installed Lubuntu, the wireless automatically turned on when I was on Windows.  But now, when I power on into Windows, the wireless does not automatically turn on, I have to press the button first.

---

### Post by chili555 on 2012-10-29
I am continuing to search, but you might check posts #8 and following here: [http://ubuntuforums.org/showthread.php?t=1793994](http://ubuntuforums.org/showthread.php?t=1793994)

You might also run:```
sudo tail -f /var/log/syslog
```Press the wireless button and see if there is any recognition of the key. If there are any messages printed, please post them here.

Get out of *tail* with Ctrl+c.

---

### Post by chili555 on 2012-10-29
In the BIOS, are Action Keys Enabled or Disabled?

---

### Post by Lunestic on 2012-10-30
> **chili555 said:**
> Please try:```
sudo su
echo "blacklist hp-wmi" >> /etc/modprobe.d/blacklist.conf
gedit /etc/rc.local
```Add a line above exit 0:```
rfkill unblock all
```Proofread, save and close gedit.```
exit
```Reboot and you should be all set.

This fixed the problem, thank you chili555!

PS: I have another problem unrelated to networking.  My cursor randomly clicks by itself and it's especially annoying when I'm typing...
Is there a solution for this?  
Thanks.

---

### Post by chili555 on 2012-10-30
> **Lunestic said:**
> This fixed the problem, thank you chili555!

PS: I have another problem unrelated to networking.  My cursor randomly clicks by itself and it's especially annoying when I'm typing...
Is there a solution for this?  
Thanks.That's not my specialty. I suggest a post in General Help.

Glad it's working.

---

