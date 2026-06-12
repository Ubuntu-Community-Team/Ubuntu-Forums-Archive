---
title: "Wireless notworking"
date: 2005-12-22
forum: Networking &amp; Wireless
---

### Post by GrahamHodgson on 2005-12-22
I've used Linux on and off as a desktop OS for around 6 years now, and have just installed 5.10 on a Dell laptop with a Netgear MA111 USB Wireless device attached. The install went fine and I'm now fighting with the wireless networking. I've googled, I've read fora (including the MA111 v1 guide), I've edited text files, I've used GUIs - all to no avail. Here's the situation as best as I can describe it:

ttgh@paris:~$iwlist wlan0 scanning
wlan0    Scan completed:
            Cell 01 - Address: 00:01:02:03:04:05
                        Essid: MYSID
                        Mode:Master
                        Encryption key:on
                        Channel: 2
                        Quality: 25/92  Signal level: -61 dBm  Noise leve: -86 dBm

(NOTE: The address is altered, but matches the router. Same for ESSID and Channel)


ttgh@paris:~$more /etc/wlan/wlan.conf
(Standard file with comments until:)
SSID_wlan0="MYSID"


ttgh@paris:~$more /etc/wlan/wlancfg-MYSID
(Lot's of comments)
lnxreq_hostWEPEncrypt=true
lnxreq_hostWEPDecrypt=true
dot11PrivacyInvoked=true
dot11WEPDefaultKeyID=0
dot11WEPDefaultKey0=00:00:00:00:00:00:00:00:00:00
IS_ADHOC=n
AuthType="sharedkey"
CHANNEL=2

(NOTE: The rest is as default, again the keys, channels and SSIDs are changed)


ttgh@paris:~$lsmod | grep usb
prism2_usb        67204 0
p80211             30992 1 prism2_usb
usbcore           104188 3 prism2_usb,uhci_hcd


ttgh@paris:~$more /etc/network/interfaces
# The loopback interface
auto lo
iface lo inet loopback

# Unused FA410TX
iface eth0 inet dhcp

# MA111 USB
auto wlan0
iface wlan0 inet dhcp



So the situation as far as I can tell is that the wireless device is working ok (it can see the router ok - Netgear DG834G - so surely that means it's working?). I know the wireless on the router end is ok because an XP laptop connects to it fine. I'm sure I've missed something blindingly obvious and I just need someone to shine the light, hopefully in here before I go mad!

Thanks in advance
Graham

---

### Post by ranf on 2005-12-22
Looks like you are using linux-wlan-ng drivers, aren't you?
What do you get from these two?
```
iwconfig
ifconfig
```

---

### Post by az on 2005-12-22
It is supposded to work, but it does not:

[http://ubuntuforums.org/showpost.php?p=465719&postcount=7](http://ubuntuforums.org/showpost.php?p=465719&postcount=7)

---

### Post by GrahamHodgson on 2005-12-22
[QUOTE=ranf]Looks like you are using linux-wlan-ng drivers, aren't you?
What do you get from these two?
```
iwconfig
ifconfig
```[/QUOTE]

Yes I am. 

ttgh@paris:~$iwconfig
lo no wireless extensions

wlan0  IEEE 802.11-DS ESSID:""
Mode:Ad-Hoc Frequency:2.472 GHz Cell: 00:00:00:00:00:00
Bit Rate:2 Mb/s Tx-Power:18 dBm
Retry min limit:8 RTS thr:off Fragment thr:off
Encryption key:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0 Missed beacon:0

eth0  no wireless extensions


ttgh@paris:~$ifconfig
eth0 (Stuff relating to FA410TX PCMCIA Card)

wlan0     Link encap:Ethernet  HWaddr  xx:xx:xx:xx:xx:xx
 UP BROADCAST MULTICAST  MTU:1500 Metric:1
 RX packets:0  errors:0  dropped:0  overruns:0  frame:0
 TX packets:0  errors:0  dropped:0  overruns:0  carrier:0
 collisions:0  txqueuelen:1000
 RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


(NOTE The HWaddr from ifconfig is correct for the wireless device). Do I take it from the output of iwconfig that something isn't been set up properly, eg. a  config file??

Cheers
Graham

---

### Post by GrahamHodgson on 2005-12-22
[QUOTE=azz]It is supposded to work, but it does not:

[http://ubuntuforums.org/showpost.php?p=465719&postcount=7](http://ubuntuforums.org/showpost.php?p=465719&postcount=7)[/QUOTE]

OK - a few questions:

Here it is:
wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
wlanctl-ng wlan0 lnxreq_hostwep decrypt=true encrypt=true
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11PrivacyInvoked=true
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKeyID=0
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKey0="####PUTYOURWEPHE RE!!!!!###"
wlanctl-ng wlan0 lnxreq_autojoin ssid="###PUT you essid here###" authtype="sharedkey"
sleep 2
dhclient wlan0


1. should that first line be repeated, or should it be something slightly different?
2. should the wep line look like ...Key0="123445", or ...Key0="12:34:45", or ...Key0=12:34:45?
3. Should the ssid line look like ...ssid="MYSID", or ...ssid=MYSID?

Cheers
Graham

---

### Post by ranf on 2005-12-22
That's the official wlan-ng method:
```

sudo /etc/init.d/wlan start

```

But IIRC I had to comment out some lines in `/etc/wlan/shared'.

---

### Post by GrahamHodgson on 2005-12-22
[QUOTE=ranf]That's the official wlan-ng method:
```

sudo /etc/init.d/wlan start

```

But IIRC I had to comment out some lines in `/etc/wlan/shared'.[/QUOTE]
Erm? WTF?? What's the official wlan-ng method???

Confused.
Graham

---

### Post by az on 2005-12-23
[QUOTE=GrahamHodgson]OK - a few questions:

Here it is:
wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
wlanctl-ng wlan0 lnxreq_hostwep decrypt=true encrypt=true
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11PrivacyInvoked=true
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKeyID=0
wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKey0="####PUTYOURWEPHE RE!!!!!###"
wlanctl-ng wlan0 lnxreq_autojoin ssid="###PUT you essid here###" authtype="sharedkey"
sleep 2
dhclient wlan0


1. should that first line be repeated, or should it be something slightly different?
2. should the wep line look like ...Key0="123445", or ...Key0="12:34:45", or ...Key0=12:34:45?
3. Should the ssid line look like ...ssid="MYSID", or ...ssid=MYSID?

Cheers
Graham[/QUOTE]

1.  Yes, it needs to be repeated.  On my device (but not on all devices) it fails nine time out of ten, the first time.  It is benign to do it twice it it works the first time, though.
2.  wlanctl-ng wlan0 dot11req_mibset mibattribute=dot11WEPDefaultKey0="12345678FF" 
That is what a 64-bit wep looks like
3.  wlanctl-ng wlan0 lnxreq_autojoin ssid="MyHouse" authtype="sharedkey"

---

### Post by ranf on 2005-12-23
[QUOTE=azz]1.  Yes, it needs to be repeated.  On my device (but not on all devices) it fails nine time out of ten, the first time.  It is benign to do it twice it it works the first time, though.
[/QUOTE]
How about putting this line twice into `/etc/wlan/shared'?
```
        result=`$WLANCTL $1 lnxreq_ifstate ifstate=enable`

```
This shared file tries to run two additional things not available on my box:
prism2_fwload
prism2_mibset

Your `/etc/hotplug/usb/prism2_usb' would then look like this:
```
#!/bin/sh
/etc/init.d/wlan start

```

and all the wlan related configs are where they belong to (IMHO) in `/etc/wlan'.

---

### Post by ranf on 2005-12-23
[QUOTE=GrahamHodgson]Erm? WTF?? What's the official wlan-ng method???
[/QUOTE]
I'm not sure I understand your question.
I simply read the files in:
```

/usr/share/doc/linux-wlan-ng
/usr/share/doc/linux-wlan-ng-doc

```

---

### Post by az on 2005-12-23
[QUOTE=ranf]How about putting this line twice into `/etc/wlan/shared'?
```
        result=`$WLANCTL $1 lnxreq_ifstate ifstate=enable`

```
.[/QUOTE]

But that is not the only problem with getting the device to work.  I think the linux-wlan-ng scripts do it a second time if there is an implementation failure.  No?

[QUOTE=ranf]
This shared file tries to run two additional things not available on my box:
prism2_fwload
prism2_mibset
.[/QUOTE]

What do you mean by this?

[QUOTE=ranf]
Your `/etc/hotplug/usb/prism2_usb' would then look like this:
```
#!/bin/sh
/etc/init.d/wlan start

```
[/QUOTE]

On my box, (detailed in the bug report mentioned - see below) the wlan-ng scrips do not enable WEP.  

[QUOTE=ranf]
and all the wlan related configs are where they belong to (IMHO) in `/etc/wlan'.[/QUOTE]

Actually, if the linux-wlan-ng scripts worked, I would not have to worry about this.  I agree with you thateverything should be handled by the proper scripts in the proper places.  All I am using is a script to hack the problem (It doesn't even use ifup ifdown!)_  It is easier for me to copy one file into a directory and have it work than to hack several things in different places.

*Please* if you are able to add to the bug report and help fix this, go ahead:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=15346](http://bugzilla.ubuntu.com/show_bug.cgi?id=15346)

I cannot code for beans and I am pretty useless at tracking down this problem.

---

