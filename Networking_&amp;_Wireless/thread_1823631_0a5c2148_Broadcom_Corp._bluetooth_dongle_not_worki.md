---
title: "0a5c:2148 Broadcom Corp. bluetooth dongle not working?!?!"
date: 2011-08-12
forum: Networking &amp; Wireless
---

### Post by Ashrael on 2011-08-12
Hi all,

decided to upgrade my usb bluetooth dongle because it is slow, old and bulky. Bought a Konig (broadcom) mini dongle. Ubuntu (natty) shows me a bluetooth icon and appears to be working. But: It doesn't find anything, nor can it be found...

lsusb:

> Bus 003 Device 004: ID 046d:c714 Logitech, Inc. diNovo Edge Keyboard
Bus 003 Device 003: ID 046d:c713 Logitech, Inc. 
Bus 003 Device 002: ID 046d:0b04 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0a5c:2148 Broadcom Corp. 
Bus 002 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 002 Device 003: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 002 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 079b:0062 Sagem XG-76NA 802.11bg
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

It looks like there is no module loaded for it. Does there need to be?

lsmod:

> Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  2 
aes_generic            38023  1 aes_i586
snd_intel8x0           33213  3 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  3 snd_intel8x0,snd_ac97_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
rfcomm                 38125  8 
zd1211rw               52419  0 
snd_rawmidi            25269  1 snd_seq_midi
i915                  450934  2 
mac80211              257001  1 zd1211rw
sco                    17827  2 
snd_seq_midi_event     14475  1 snd_seq_midi
hid_logitech           17421  0 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
ff_memless             12945  1 hid_logitech
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            13213  1 
ppdev                  12849  0 
joydev                 17322  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39671  0 
cfg80211              156212  2 zd1211rw,mac80211
usbhid                 41704  1 hid_logitech
btusb                  18160  2 
drm_kms_helper         40745  1 i915
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
drm                   180037  3 i915,drm_kms_helper
snd                    55295  12 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
hid                    77084  2 hid_logitech,usbhid
serio_raw              12990  0 
shpchp                 32345  0 
soundcore              12600  1 snd
parport_pc             32111  1 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
toshiba_acpi           13796  0 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
sparse_keymap          13666  1 toshiba_acpi
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
e100                   40108  0 


Anybody have a clue why this isn't working?


Thanks!

---

### Post by Nevyn on 2011-08-18
Do you have a bluetooth manager installed? If you just search Synaptic for 'bluetooth', you can check this. If you need to download one, they generally appear in System -> Preferences

---

### Post by Ashrael on 2011-09-07
@nevyn: do you mean blueman with that? I mean, the dongle shows up in my bluetootmanager but doesn't work.

---

### Post by tomek_wap on 2011-11-02
i have the same problem with 11.10, and built in bluetooth module.

bluetooth manager shows that BT is ON, but after opening the manager it shows that it is actually disabled.

looking at Lenovo (G770 model) drivers, it is Broadcom.

---

### Post by Ashrael on 2011-11-25
Upgraded to 11.10 and still the problem persists. It shows up as working, but when I scan it finds no devices. Also my phone doesnt find the pc. 
When I plug in my old BT 1.1 adapter it does work, so is this a driver issue?

Why does it take so long for this to be fixed? I see that there is a lot of people that have the same BT dongle or built in chipset with the same problem.... Is Broadcom not playing nice, or is this a maintainer issue?

It would be nice if someone would help me fix this problem, as I can not do this alone because of lack of knowledge on this subject...

This is the fifth product I buy that is supposed to be compatible with linux according to the HCl, but doesnt work... I keep selling all this stuff with a loss...:(


HELP me help everybody please....

TIA!

---

### Post by tomek_wap on 2011-11-25
have you tried to turn on BT on windows?
it worked for me with built-in BT module.

---

### Post by Ashrael on 2011-12-18
Thanks Tomek, but I do not have windows anywhere in the house, as I like my house clean.... :) Also it is not a built in adapter so I do not think this would work for me anyway....

I will keep searching.....

---

### Post by Ashrael on 2012-01-07
I found out that in 11.10 I cannot change the "switch" from off to on...Below it the message "Bluetooth is diabled"... I had this with my logitech dinovo too, but that somehow started working again...

Still this dongle is not working......

---

### Post by Ashrael on 2012-04-26
Found out some more info on this thing:

Bus 004 Device 017: ID 0a5c:2148 Broadcom Corp. BCM92046DG-CL1ROM Bluetooth 2.1 Adapter
Bus 004 Device 016: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
Bus 004 Device 015: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 004 Device 014: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)

Compared to what I get:

Bus 002 Device 005: ID 0a5c:2148 Broadcom Corp.
Bus 002 Device 004: ID 0a5c:4503 Broadcom Corp.
Bus 002 Device 003: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 002 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)

---

### Post by Ashrael on 2012-05-27
still not working......:confused::confused:

---

### Post by followurdrmz on 2013-04-13
> **tomek_wap said:**
> have you tried to turn on BT on windows?
it worked for me with built-in BT module.

This worked for me on 12.04. Mine is dual boot. Turned off the bluetooth adapter in windows 7 and it stopped working in ubuntu as far as i can remember.

---

### Post by wildmanne39 on 2013-04-13
Reopened at request of OP.

---

### Post by Ashrael on 2013-06-29
Still not working, not under 12.10 or 13.04.... Symptoms still the same, it shows, driver seems to load, but still I cannot make any connection or even find another device...

I have done a usb-devices for all three my dongles, the first (broadcom) is not working, the other two are... I would love to be able to swap those bulky sticks for the small Broadcom one....

> 
usb-devices output BROADCOM stick (not working):

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0a5c ProdID=4500 Rev=01.00
S:  Manufacturer=Broadcom
S:  Product=BCM2046B1
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=94mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0a5c ProdID=4502 Rev=01.00
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid

T:  Bus=02 Lev=02 Prnt=02 Port=01 Cnt=02 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0a5c ProdID=4503 Rev=01.00
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=02 Lev=02 Prnt=02 Port=02 Cnt=03 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0a5c ProdID=2148 Rev=08.18
S:  Manufacturer=Broadcom Corp
S:  Product=BCM92046DG-CL1ROM
S:  SerialNumber=001986000CAE
C:  #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=00 Driver=(none)

=============================================


usb-devices output LOGITECH stick (working)

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  6 Spd=12  MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=0b04 Rev=49.00
S:  Manufacturer=Logitech
S:  Product=Logitech BT Mini-Receiver
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=02 Prnt=06 Port=00 Cnt=01 Dev#=  9 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=046d ProdID=c709 Rev=49.00
S:  Manufacturer=Logitech
S:  Product=Logitech BT Mini-Receiver
S:  SerialNumber=0007617183A5
C:  #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=00 Driver=(none)

T:  Bus=03 Lev=02 Prnt=06 Port=01 Cnt=02 Dev#=  7 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c713 Rev=49.00
S:  Manufacturer=Logitech
S:  Product=Logitech BT Mini-Receiver
S:  SerialNumber=0007617183A5
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid

T:  Bus=03 Lev=02 Prnt=06 Port=02 Cnt=03 Dev#=  8 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c714 Rev=49.00
S:  Manufacturer=Logitech
S:  Product=Logitech BT Mini-Receiver
S:  SerialNumber=0007617183A5
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

=============================================

usb-devices output CAMBRIDGE (working)

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  8 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0a12 ProdID=0001 Rev=15.93
C:  #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb






Is there really noone who can help me (and probably many others) to get this thing to work?

Anyone????

---

### Post by Ashrael on 2013-09-16
HELLOOOOOOO! ANYONE? Does anyone read this at all???

---

### Post by dvdmrs09 on 2013-09-16
on my first cup if coffee so pardon if Im a little slow, let me do some research on your issue and I will try to debug it for you

---

### Post by dvdmrs09 on 2013-09-16
run these commands one after another into the terminal and post the results, it might be blocked from operating 
lsusb
sudo hcitool dev
sudo hcitool scan
sudo rfkill list

---

