---
title: "Wi-fi cannot be turned off"
date: 2012-09-11
forum: Networking &amp; Wireless
---

### Post by yogyakor on 2012-09-11
Hi,

My inbuilt wireles is always on. I don't use it, I would like to turn it off. However, pressing the hardware wi-fi button doesn't do anything. The connection doesn't show in the 
'Network Connections' menu.

It shows in the 'Network tools' app. The status is 'enabled'. When I open the 'Configure' option, it takes me to the 'Network Connection' app, and the wireless is not listed there, so I cannot configure it.

I just want to turn it off permanently, I never use the inbuilt wireless, I just use the USB wireless connection.


02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

---

### Post by steeldriver on 2012-09-11
This has worked for me (assuming you are managing your interfaces via NetworkManager)

1. find the MAC address of the card you want to disable, e.g. using

```
lshw -C
```(the MAC is listed as 'serial')

2. edit /etc/NetworkManager/NetworkManager.conf, appending

```
[keyfile]
unmanaged-devices=mac:xx:xx:xx:xx:xx:xx
```where xx:xx:xx:xx:xx:xx is the MAC (serial) from above

3. restart the NetworkManager service

```
sudo service network-manager restart
```This should hard block the device i.e.

```
$ rfkill list all
0: tpacpi_bluetooth_sw: Bluetooth
        Soft blocked: no
        Hard blocked: no
[COLOR=Red]1: phy0: Wireless LAN
[COLOR=Black]        Soft blocked: no[/COLOR]
        Hard blocked: yes[/COLOR]
14: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no

```

---

### Post by yogyakor on 2012-09-11
For some reason  

lshw  -C 

just brings a manual for lshw in my terminal. However I got the serial number from 
'Network tools' app and proceeded with your instructions.
Worked like a charm!:guitar:

Thanks a lot,  I really appreciate that.

---

### Post by steeldriver on 2012-09-11
doh! I'm sorry, that should have been

```
lshw -C **network**
```

Anyhow glad you figured it out :)

---

### Post by yogyakor on 2012-09-12
Oh wait....

After coming back from sleep my wi-fi button is still blue.

However,

~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    [COLOR=Red]Soft blocked: yes
    Hard blocked: yes[/COLOR]

If I type  ~$ lshw -C network

I get the message that wi-fi is *Network disabled.

So why is it still blue? The physical button is OK, I dual boot with another version of Linux and
it shows orange when it's turned off.

If I use the 'Network tools' app it shows ethernet as enabled. Any idea what's going on?

---

### Post by yogyakor on 2012-09-12
And after a system reboot it's off again ... Don't know whether I'm coming or going.
I guess it OTT.   :roll::roll::roll:

It's disabled after boot but gets magically enabled every time after suspend.

---

### Post by chili555 on 2012-09-12
I suggest you blacklist its driver. Find out with:```
sudo lshw -C network
```I believe yours is ath9k. If you confirm it is, do:```
sudo su
echo "blacklist ath9k" >> /etc/modprobe.d/blacklist.conf
modprobe -r ath9k
exit
```It should now be well and truly deceased.

---

### Post by yogyakor on 2012-09-12
Going, going, gone. ):P
RIP ath9k.

Thank you so much for your help.

---

