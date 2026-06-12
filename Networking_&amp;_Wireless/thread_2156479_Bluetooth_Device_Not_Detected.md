---
title: "Bluetooth Device Not Detected"
date: 2013-06-21
forum: Networking &amp; Wireless
---

### Post by adam.webb on 2013-06-21
Hi Everyone,
I'm having some issues with Bluetooth on my new laptop. Ubuntu does not appear to detect the Bluetooth device at all. Details below:

OS: Ubuntu Gnome 13.04
PC: ASUS K56C
Kernel 3.8.0-25

Following outputs:

```

adam@zeta:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 13d3:5165 IMC Networks 

adam@zeta:~$ sudo lshw | grep Bluetooth

adam@zeta:~$ lspci | grep Bluetooth

adam@zeta:~$ sudo hcitool dev
Devices:

adam@zeta:~$ sudo hcitool scan[SIZE=2][FONT=arial]
Device is not available: No such device

```

Which has lead me to believe that Ubuntu doesn't seem to know that a Bluetooth device exists. I have looked through the BIOS which makes no reference to Bluetooth, but reset defaults there just in case.

I've also installed Bluetooth Manager from Software Centre, as well as  bluetooth blueman bluez-hcidump bluewho python-bluez  bluez-tools. 

Any suggestions? I've tried everything I can think of!

Thanks in advance!
[/FONT][/SIZE]
Adam

---

### Post by scbingham on 2013-06-22
There can be conflicts between BT managers. I had problems, so uninstalled all BT packages from Software Centre & then only installed Blueman.

Are you absolutely sure your laptop model has BT built in? Is there a function key or physical switch to turn it on?

---

### Post by satyamdhaker on 2013-06-22
Dear adam,

If you sure that in your machine has inbuilt bluetooth and not detected or something then use below command

"rfkill list all"
It will display all wifi, bluetooth etc. settings and if any one of these are soft blocked or by hardware blocked
Then run below command 
"rfkill unblock all"

i hope it will work for you.

Regards,
satyamDhaker

---

### Post by praseodym on 2013-06-22
Are you sure there is a device? Is it "bluetooth ready"?!

Check also

```
cat /var/lib/NetworkManager/NetworkManager.state
lsmod
usb-devices
hciconfig --all 
```

---

### Post by herrwinkler on 2013-06-23
Do you have the ar9485 wireless card?  There is a bug with the ath9k driver that causes low wifi reception as well as not recognizing the bluetooth, which is a part of it.  I have an asus with this problem.  A patch has been submitted and will be released soon.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1160188](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1160188)

---

### Post by adam.webb on 2013-06-26
> **herrwinkler said:**
> Do you have the ar9485 wireless card?  There is a bug with the ath9k driver that causes low wifi reception as well as not recognizing the bluetooth, which is a part of it.  I have an asus with this problem.  A patch has been submitted and will be released soon.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1160188](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1160188)

Thanks herrwinkler! Yes I do have that card - hopefully when the patch comes out my problems will be fixed. 

I'll eagerly await for the patch.

Cheers

Adam

---

