---
title: "Wireless Problem w/ Sony Vaio VGN-FE770G"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by lsward on 2011-08-10
Still a noob to the Linux thing and thought I would try out the new Ubuntu.  Eveything seems to have come out fine, but I'm having an issue with my wireless that I can't figure out.  When I first configured the wireless it hooked up fine.  Then it disconnected.  Then it connected again.  I checked out some of the pages on wireless and I can't figure it out.  I tried to scan for wireless signals through the terminal and it says the wireless has been disabled.  I read some where that if the wireless was turned off in the old windows os then I have to reboot into Windows and turn it back on for it to work.  Is this true, because if it is then I have no way of doing this.  Any one have any suggestions?  I will run what ever terminal reports you need.  I just can seem to crack this.  Thanks.

---

### Post by lkjoel on 2011-08-10
Do you have Ubuntu or Kubuntu?

---

### Post by lsward on 2011-08-10
I'm using Ubuntu 11.04.

---

### Post by lkjoel on 2011-08-10
Could you give me the output of these Terminal commands?
```
sudo ifconfig
iwconfig
sudo nm-tool
sudo rfkill list all
sudo iwlist scan

```

---

### Post by lsward on 2011-08-10
Here you go:
```

eth0      Link encap:Ethernet  HWaddr 00:13:a9:46:92:ab  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:a9ff:fe46:92ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2305 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3962214 (3.9 MB)  TX bytes:333022 (333.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```
```

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        00:13:A9:46:92:AB

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             unavailable
  Default:           no
  HW Address:        00:13:02:D4:D6:47

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

```
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

```

---

### Post by lkjoel on 2011-08-10
Try this: [http://ubuntuforums.org/showpost.php?p=11139742&postcount=4](http://ubuntuforums.org/showpost.php?p=11139742&postcount=4)

---

### Post by lsward on 2011-08-10
I did what you said and this is what happen:
```

16%
32%

```
and then it stop and has been hanging there for the past couple of minutes.

---

### Post by lkjoel on 2011-08-10
Do you have a wireless switch/button? Switch/press it on a few times, and it should de-hang.

---

### Post by lsward on 2011-08-10
Okay it finished but my terminal window closed and I still don't have wireless.  I noticed it said the device wasn't ready.

---

### Post by lkjoel on 2011-08-10
Try it again.

---

### Post by lsward on 2011-08-10
Okay.  I'm trying again right now.

---

### Post by lsward on 2011-08-10
It's hung up again on the 32% mark.  I switch the wireless on and off a couple of times and I'm going to wait to see what happens.

---

### Post by lsward on 2011-08-10
Computer is acting a bit weird and I had to jump on to another laptop.  The cursor was getting a bit jumpy and it was locking up so I couldn't close windows.

---

### Post by lsward on 2011-08-10
The computer is totally locked up and will not respond to any input.  Any suggestions?

---

### Post by nm_geo on 2011-08-10
After nearly wearing out my laptop shutting down someone gave me the sequence to cleanly shutdown when terminal is stuck.

ALT & SYSRq HOLD THEM e, i, o, s, u, b

SYSRq is also print screen on my laptop

Saves a hard shutdown when terminal will not respond..usually

---

### Post by lsward on 2011-08-10
Thanks I'll try that out.

---

### Post by lsward on 2011-08-10
nm_geo it didn't work.  Now the cursor won't move either.  Could explain the exact sequence the keys should be pressed in.  Should I hold ALT & SYSRq together while pressing each individual key in the rest of the sequence or do I need to hold them all together.  I'm at a loss here and I don't want to do a hard shut down, but I'm running out of options.  Thanks for your help.

---

### Post by lsward on 2011-08-11
I had to do a hard shut down unfortunately and when I was snooping around the computer I found a log file and it repeated this for 23,002 lines:
```

SIOCSIFFLAGS: Operation not possible due to RF-kill

```
Any suggestions?

---

### Post by nm_geo on 2011-08-11
```
rfkill list all
```

Then if you see any that are yes 

```
rfkill unblock all
```

Sorry yes hold down ALT & SYSSq
then hit e i o s u b individually

---

### Post by nm_geo on 2011-08-11
From time to time when you want to shutdown .. Just try the sequence .. It cleanly shuts the computer down.  Of course, I mainly use it when the terminal is not working too, and that happens quite often in testing the new to come version like Oneiric 11.10.

---

### Post by nm_geo on 2011-08-11
Use that sequence and then restart your computer..

Then let's check the```
 rfkill list all
```

Try to reboot without the ethernet cable connected.  If you get no wireless then plug in the cable it should pick right up.

---

### Post by lsward on 2011-08-11
Thanks for the advice.
I entered rfkill list all in the terminal and this is what it spit out:
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

---

### Post by nm_geo on 2011-08-11
> **lsward said:**
> Thanks for the advice.
I entered rfkill list all in the terminal and this is what it spit out:
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

Okay shutdown with the sequence it will build your confidence in it. Reboot without ethernet cable and let's see if wireless comes up.  If not just plug in the cable it should connect ..

---

### Post by lsward on 2011-08-11
nm_geo you are awesome!  So far so good.  Wireless is up and running.  I really appreciate all help.

---

### Post by lsward on 2011-08-11
Dang!  It just disconnected and won't let me connect again.  It said wireless is disabled by hardware switch, but I didn't touch the switch for the wireless.

---

### Post by lsward on 2011-08-11
Got up this morning and fired up the computer.  Guess what.  I got a connection, but last night I could get the computer to reconnect for the life of me.  Any one got any insight as to how I can prevent this from happening again.

---

### Post by nm_geo on 2011-08-11
> **lsward said:**
> Got up this morning and fired up the computer.  Guess what.  I got a connection, but last night I could get the computer to reconnect for the life of me.  Any one got any insight as to how I can prevent this from happening again.


Let see the following 

```
lsmod
``````
lspci -nn | grep 0280
``````
sudo lshw -C network
```

---

### Post by lsward on 2011-08-11
Here you go:
```

Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
binfmt_misc            13213  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
arc4                   12473  2 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
i915                  450934  3 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
iwl3945               126017  0 
iwlcore               148965  1 iwl3945
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              257001  2 iwl3945,iwlcore
pcmcia                 39671  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
gspca_vc032x           32072  0 
gspca_main             27894  1 gspca_vc032x
tifm_7xx1              12898  0 
snd_timer              28659  2 snd_pcm,snd_seq
drm_kms_helper         40745  1 i915
joydev                 17322  0 
videodev               75143  1 gspca_main
tifm_core              15040  1 tifm_7xx1
sony_laptop            34432  0 
drm                   180037  4 i915,drm_kms_helper
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              156212  3 iwl3945,iwlcore,mac80211
i2c_algo_bit           13184  1 i915
psmouse                73312  0 
soundcore              12600  1 snd
serio_raw              12990  0 
video                  18951  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
e100                   40108  0 
crc_itu_t              12627  1 firewire_core


```

```

06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)

```

```

  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:d4:d6:47
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.38-10-generic firmware=15.32.2.9 ip=192.168.1.103 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:cc000000-cc000fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:0a:08.0
       logical name: eth0
       version: 02
       serial: 00:13:a9:46:92:ab
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 memory:d0005000-d0005fff ioport:6000(size=64)


```
Thanks again for all this help.  Any suggestions would be appreciated.

---

### Post by nm_geo on 2011-08-11
Your wireless driver looks good to me..
It is a Intel chipset that is generally quite good and works right out of the box.  In fact I am considering getting one for my laptop.
Since this is a new install correct?

Do these and let's see if you get better results.

```
sudo apt-get update && sudo apt-get upgrade
```

Those will get everything up-to-date and I often forget to tell everyone to do that first with ethernet attached ( it may take awhile).  If that doesn't help we might try to temporarily remove the sony_laptop module to see what we get.

---

### Post by lsward on 2011-08-12
Yes, it is a fresh install.  I ran those commands and everything has been updated and upgraded according to the feedback I received.  I always do all the updates on fresh installs.  Thanks for all your help.  The wireless has been working for sometime now.

---

### Post by nm_geo on 2011-08-12
> **lsward said:**
> Yes, it is a fresh install. I ran those commands and everything has been updated and upgraded according to the feedback I received. I always do all the updates on fresh installs. Thanks for all your help. The wireless has been working for sometime now.
 
Excellent..if you do get the intermitant wireless problems.. Running the following might help give us some more useful information.
 
```
 
dmesg | tail

```

---

### Post by lsward on 2011-08-12
Will do, but as for now I'm just enjoying this wireless.  Thanks again.

---

### Post by nm_geo on 2011-08-13
if you areppy I am happy.  Please mark solved with thread tools.

---

