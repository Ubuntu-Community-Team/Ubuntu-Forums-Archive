---
title: "DWA-140 (2001:3c15) doesnt work"
date: 2012-03-30
forum: Networking &amp; Wireless
---

### Post by Nartales on 2012-03-30
Hello There,

I do have a new problem :/
I did get a new wireless USB-Stick (D-Link DWA-140 (2001:3c15)).
So I did install the the driver vom Ralink [B][RT8070 /RT3070 /RT3370 /RT5370 /RT5372 USB]("http://www.ralinktech.com/en/04_support/license.php?sn=5016")
and did load the module [/B]rt5370sta

now the problem is with iwconfig I see this:
nartales@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

Can somebody please help me :)

Greetings Nartales

---

### Post by Nartales on 2012-03-30
No one rly?
or you need more information?

Greetings

Nartales

---

### Post by Nartales on 2012-03-31
Sorry but I have to try it one more time maybe today someone can help me :)
Here some more infos:
```
nartales@ubuntu:~$ lsmod
Module                  Size  Used by
vsock                  47098  0 
vmblock                18170  0 
vmsync                 12872  0 
vmhgfs                 57265  0 
bnep                   17923  0 
rfcomm                 38408  0 
ppdev                  12849  0 
vmw_balloon            12729  0 
rt5370sta             721872  0 
snd_ens1371            24820  2 
gameport               15060  1 snd_ens1371
snd_ac97_codec        106082  1 snd_ens1371
ac97_bus               12642  1 snd_ac97_codec
btusb                  18160  0 
bluetooth             148839  5 bnep,rfcomm,btusb
snd_pcm                80435  2 snd_ens1371,snd_ac97_codec
parport_pc             32114  1 
psmouse                63474  0 
serio_raw              12990  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17393  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17292  1 
snd                    55902  11 snd_ens1371,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14108  1 snd_pcm
shpchp                 32356  0 
vmci                   71337  2 vsock,vmhgfs
i2c_piix4              13093  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
floppy                 60310  0 
mptspi                 22475  2 
mptscsih               39377  1 mptspi
mptbase                96811  2 mptspi,mptscsih
vmxnet                 22375  0 
vmw_pvscsi             18334  0 
vmxnet3                44926  0 

```
```
nartales@ubuntu:~$ sudo lshw -C network
[sudo] password for nartales: 
  *-network               
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0c:29:7e:67:66
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical logical tp 1000bt-fd
       configuration: autonegotiation=off broadcast=yes driver=vmxnet driverversion=2.0.10.0 duplex=full firmware=N/A ip=172.16.145.150 latency=64 link=yes maxlatency=255 mingnt=6 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:19 ioport:2000(size=128) memory:d8400000-d840ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: ra0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN multicast=yes wireless=Ralink STA
```

If you need more just tell me :)

Greetings Benjamin

---

### Post by praseodym on 2012-03-31
Hi,

please show
```

rfkill list
sudo iwlist scan
```

---

### Post by lJ9%3MR&gt;sa on 2012-03-31
I'm having the same problem as you with the RT5370 driver. I just used the built in driver. The only problem I have is not being able to make it load at startup...:mad:

Open terminal.
Type this.

```
modprobe rt2800usb
sudo -s
echo 2001 3c15 > /sys/bus/usb/drivers/rt2800usb/new_id
exit
```(this part im not sure about... I'm just changing it to your hw id.)

It should say new Network found or found wireless network...
If that doesn't work reboot; we are going to change the hw id in terminal.

Open terminal.
Type this.

```
modprobe rt2800usb
sudo -s
echo 148F 5370 > /sys/bus/usb/drivers/rt2800usb/new_id
exit
```Please remember that I'm not a Terminal geek. :P That was just from some of my problems. Also, I was NEVER able to get the compiled drivers to work...

---

### Post by Nartales on 2012-03-31
Ok thx first the information:

```
nartales@ubuntu:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

```
nartales@ubuntu:~$ sudo iwlist scan
[sudo] password for nartales: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:02:A5:2E:22:17
                    Protocol:802.11b
                    ESSID:" "
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/100  Signal level=-77 dBm  Noise level=-80 dBm
                    Encryption key:on
                    Bit Rates:11 Mb/s
          Cell 02 - Address: C0:3F:0E:48:78:58
                    Protocol:802.11b/g/n
                    ESSID:"ipmedia"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/100  Signal level=-83 dBm  Noise level=-86 dBm
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:80:48:6B:F4:7F
                    Protocol:802.11b/g
                    ESSID:"redbox"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality=47/100  Signal level=-71 dBm  Noise level=-76 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:02:A5:6E:AB:81
                    Protocol:802.11b
                    ESSID:" "
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality=23/100  Signal level=-81 dBm  Noise level=-86 dBm
                    Encryption key:on
                    Bit Rates:11 Mb/s
          Cell 05 - Address: 00:0F:61:80:B3:26
                    Protocol:802.11b/g
                    ESSID:"S&F-Zurich"
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality=31/100  Signal level=-77 dBm  Noise level=-86 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: 00:0F:61:80:B3:28
                    Protocol:802.11b/g
                    ESSID:"S&F Zuerich Guests"
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality=31/100  Signal level=-77 dBm  Noise level=-86 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s
          Cell 07 - Address: 00:18:39:83:44:E5
                    Protocol:802.11b/g
                    ESSID:"CAPSWLAN"
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality=13/100  Signal level=-85 dBm  Noise level=-93 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 08 - Address: E0:46:9A:68:34:7F
                    Protocol:802.11b/g/n
                    ESSID:"WISS-211"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=89/100  Signal level=-55 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A00011010440001021047001042E8E2C46C927A458343B8388233845C103C000103
          Cell 09 - Address: 00:25:9C:C0:74:24
                    Protocol:802.11b/g/n
                    ESSID:"Jeremy"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=7/100  Signal level=-87 dBm  Noise level=-82 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102

nartales@ubuntu:~$ 
```

@faxmanloveswaffles I will try this thx alot

Greetings Nartales

---

