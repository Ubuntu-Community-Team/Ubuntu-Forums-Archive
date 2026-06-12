---
title: "ATHEROS AR9285 WLAN not working with LENOVO B560 (with ubuntu 11.04)"
date: 2011-06-26
forum: Networking &amp; Wireless
---

### Post by adarsh_chacko on 2011-06-26
[SIZE=2]I am using **LENOVO B560** Laptop (with **Ubuntu 11.04**) which has **ATHEROS AR9285** Wireless Network Adapter but unfortunately the wireless network does not work. [/SIZE]This is after installing Ubuntu 11.04 with the downloaded updates.

---

### Post by MaindotC on 2011-06-26
The first place to start is the Ubuntu Wireless Troubleshooting Guide.  In order for your device to work properly you need the physical connectivity (plugged in all the way and/or turned on via your machine's BIOS), a driver to communicate between the device and the operating system, and then the proper configuration of the device which typically is via DHCP.  Please follow the guide and indicate at what point you are having difficulty.

---

### Post by adarsh_chacko on 2011-06-27
[SIZE=3]I tried the troubleshooter which suggested to run nm-tool in the terminal and in turn gave me an output somewhat as below:

 [SIZE=2]Type:              802.11 WiFi [/SIZE][/SIZE][SIZE=3][SIZE=2]
  Driver:            ath9k
  State:             unavailable
  Default:           no[/SIZE]


I also tried rfkill list which gave me the following:  [/SIZE][SIZE=3]

[SIZE=2]0: ideapad_wlan: Wireless LAN [/SIZE][/SIZE][SIZE=3][SIZE=2]
    Soft blocked: yes
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no[/SIZE]

On unblocking 1 and 4 through refkill I noticed that  the enable wireless option is brought up but WLAN does not work and on rebooting the system it comes to the form as shown above. [/SIZE][SIZE=3]

**(N. B.: I have a dual OS installed in my Laptop and the WLAN works fine in the other OS (i.e. Windows 7).)** [/SIZE]

---

### Post by chili555 on 2011-06-27
> 2: acer-wireless: Wireless LAN
[COLOR="Red"]Soft blocked: yes[/COLOR]This thread may be useful:  [http://ubuntuforums.org/showthread.php?t=1745317&highlight=acer-wmi](http://ubuntuforums.org/showthread.php?t=1745317&highlight=acer-wmi)

---

### Post by adarsh_chacko on 2011-06-27
[SIZE="3"]I used the method shown in the link above. The changes I saw was that the **rfkill list** output changed from this...[/SIZE]

0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes



[SIZE="3"]To this.[/SIZE]


0: acer-wireless: Wireless LAN
	Soft blocked: yes
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


[SIZE="3"]The other change that was noticed was *_Enable Wireless_* option came up in the drop down network menu on the desktop with *_Wireless Networks_* option disabled and *_device not ready_* shown in a disabled form in the same menu.[/SIZE]

---

### Post by chili555 on 2011-06-27
> [SIZE="2"]To this.[/SIZE]


0: [COLOR="Red"]acer-wireless: Wireless LAN
Soft blocked: yes[/COLOR]
Hard blocked: noIf acer-wireless is still showing as soft-blocked, I suspect acer-wmi is still loaded and stopping your wireless. Is it?```
lsmod | grep acer
```

---

### Post by adarsh_chacko on 2011-06-28
[SIZE="3"]On trying [/SIZE]

> 
lsmod | grep acer

[SIZE="3"]This is what I get (**as output**)[/SIZE] 

```
[COLOR="Red"]acer[/COLOR]_wmi               23123  0 
sparse_keymap          13666  2 [COLOR="red"]acer[/COLOR]_wmi,ideapad_laptop
```



[SIZE="3"]And after reboot **rfkill list** showing the same thing as below:[/SIZE]


```

0: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

```

[SIZE="3"]The changes made in the previous attempts don't seem to stay permanently.[/SIZE]

---

### Post by chili555 on 2011-06-28
> The changes made in the previous attempts don't seem to stay permanently.Did you make the change in post #5 in the link I gave you?

---

### Post by adarsh_chacko on 2011-06-28
[SIZE="3"]I didn't get you...

I meant I tried all that you had told me including the ones mentioned in the link given in post #4 [/SIZE]
> 
This thread may be useful: [http://ubuntuforums.org/showthread.p...light=acer-wmi](http://ubuntuforums.org/showthread.p...light=acer-wmi)



and the one mentioned in your last post i.e.> lsmod | grep acer



[SIZE="3"]I would also like to mention that the changes done do not remain after reboot. So please suggest also a way out to keep these changes permanent. Please help.[/SIZE]

---

### Post by chili555 on 2011-06-28
Post #5 in the link I gave you asks that you blacklist acer-wmi so it doesn't load on boot. However, it *did* load:> On trying

Quote:
lsmod | grep acer
This is what I get (as output)

Code:

acer_wmi               23123  0 
sparse_keymap          13666  2 acer_wmi,ideapad_laptop

Let's take a look at your blacklist file so that we can see what has gone wrong:```
cat /etc/modprobe.d/blacklist.conf
```

---

### Post by adarsh_chacko on 2011-06-28
[SIZE="3"]This is what is seen on using[/SIZE]


> Let's take a look at your blacklist file so that we can see what has gone wrong:
Code:
cat /etc/modprobe.d/blacklist.conf

[SIZE="3"]**Output**[/SIZE]

```


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

---

### Post by chili555 on 2011-06-28
Well, I don't see ***blacklist acer-wmi*** in there, do you? So please go back to post #5 in the link I provided you and do the steps called for in there. After a reboot, you should be all set.

---

### Post by moonport on 2011-06-30
> **adarsh_chacko said:**
> [SIZE=2]I am using **LENOVO B560** Laptop (with **Ubuntu 11.04**) which has **ATHEROS AR9285** Wireless Network Adapter but unfortunately the wireless network does not work. [/SIZE]This is after installing Ubuntu 11.04 with the downloaded updates.

You need to update your driver manually.

- Type lspci command to identify your controller 
- go to [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/) and download the first file package (name similar to compat-wireless-2.6.tar.bz2)
- sudo aptitude install build-essential
- sudo aptitude install linux-headers-$(uname -r)
- tar -xjvf compat-wireless-2.6.tar.bz2
- cd compat-wireless-2.6
- scripts/driver-select atl1c
- make
- sudo make install
- restart

I hope it will be useful.

---

### Post by chili555 on 2011-06-30
> **moonport said:**
> You need to update your driver manually.

- Type lspci command to identify your controller 
- go to [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/) and download the first file package (name similar to compat-wireless-2.6.tar.bz2)
- sudo aptitude install build-essential
- sudo aptitude install linux-headers-$(uname -r)
- tar -xjvf compat-wireless-2.6.tar.bz2
- cd compat-wireless-2.6
- scripts/driver-select atl1c
- make
- sudo make install
- restart

I hope it will be useful.I think you meant scripts/driver-select [COLOR="Red"]ath9k[/COLOR]. Moreover, the module *acer-wmi* is clearly soft-blocking his wireless. Until he gets it blacklisted, any and every wireless driver will not help.

---

### Post by adarsh_chacko on 2011-06-30
[SIZE="3"]On repeating the steps given in the link mentioned above and finally typing in [/SIZE]

```
 ifconfig wlan0 up 
```

[SIZE="3"]I notice that the WLAN LED comes up and I see > wireless is disabled in grey form in the network panel on the desktop.[/SIZE]

[SIZE="3"]I also used [/SIZE]

```
 iwlist scan 
``` 

[SIZE="3"]and found that my WLAN network is detected inspite of this it is not able to connect. 

I am [COLOR="Red"]so close[/COLOR]; the WLAN LED has come up and my network is detected through the terminal by iwlist scan but I am not able to connect.[/SIZE]

---

### Post by chili555 on 2011-06-30
Please run and post:```
rfkill list all
lsmod | grep acer
```Thanks.

---

### Post by adarsh_chacko on 2011-07-01
[SIZE="2"]Output for
[/SIZE]
rfkill list all


```
0: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
4: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
```

[SIZE="2"]And the output for 
[/SIZE]
lsmod|grep acer


```
[COLOR="red"]acer[/COLOR]_wmi               23123  0 
sparse_keymap          13666  2 [COLOR="Red"]acer[/COLOR]_wmi,ideapad_laptop
```

with the word acer in RED (as shown above)...

---

### Post by chili555 on 2011-07-01
So, although I have asked you several times to blacklist acer-wmi and checked your blacklist file, it's not blacklisted, it's still loaded and it's still blocking your wireless. I want you to do the following. Please open a terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a line at the very end.```
blacklist acer-wmi
```Proofread twice, save and close gedit. Now do:```
sudo gedit /etc/rc.local
```Add one line ***above*** exit 0```
rfkill unblock all
```Proofread twice, save and close gedit.

Reboot. Post back to confirm to me that every change was done perfectly as requested and to tell me how your wireless is working.

---

### Post by adarsh_chacko on 2011-07-05
I did exactly as you had told me to do and then this is what I did showing you step by step with the output to check if it worked....

[B]Step 1
[/B]

```
rfkill list

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```



[B]Step 2
[/B]
```

ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill
```


[B]Step 3
[/B]
```
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down
```

And then I almost gave up. But after a couple of reboots I saw the Connection established notification.

Then I did 

```
rfkill list
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

I tried connecting... It did... To my surprise... The problem got **SOLVED**.... **THANK YOU SO MUCH....**

---

### Post by chili555 on 2011-07-05
> The problem got SOLVED.... THANK YOU SO MUCH....Outstanding!

Please use thread tools at the top to mark Solved.

---

### Post by extremizt on 2011-08-13
WOW that worked! Million thanks :popcorn:

Sony VAIO E Series laptop with Atheros AR9285 Wireless Adapter.

---

### Post by mcalautt on 2011-08-16
can anyone help me with this ?

I have this card too.. cant get it to work.. I dont appear to be using the acer-wmi though.

 bought a brand new Acer Aspire AS5733Z-4445 Intel Pentium P6100(2.00GHz) 15.6" 3GB Memory 320GB HDD Intel HD Graphics Notebook
 installed the latest ubuntu 11.04.
 Nothing shows up in a wireless scan and if I enter my access point info in manually it doesnt work.





 lshw -C Network
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 68:a3:c4:b8:7f:39
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-10-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2400000-d240ffff




nm-tool
  - Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        68:A3:C4:B8:7F:39
   Capabilities:
   Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
  carcass:         Infra, 00:18:01:EF:6A:BA, Freq 2462 MHz, Rate 54 Mb/s, Strength 68 WPA WPA2
 

lsmod
Module                  Size  Used by
cryptd                 20510  0
aes_x86_64             17208  0
aes_generic            38279  1 aes_x86_64
joydev                 17606  0
parport_pc             36959  0
ppdev                  17113  0
snd_hda_codec_realtek   336771  1
arc4                   12529  2
snd_hda_intel          33211  2
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
ath9k                 116068  0
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            17565  1
i915                  514975  3
snd_timer              29602  2 snd_pcm,snd_seq
mac80211              296672  1 ath9k
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72195  0
sparse_keymap          13898  0
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k_common           14069  1 ath9k
ath9k_hw              329532  2 ath9k,ath9k_common
ath                    23779  2 ath9k,ath9k_hw
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
drm_kms_helper         42136  1 i915
drm                   227495  4 i915,drm_kms_helper
psmouse                73535  0
soundcore              12680  1 snd
intel_ips              18097  0
serio_raw              13166  0
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              181865  3 ath9k,mac80211,ath
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
lp                     17825  0
parport                46458  3 parport_pc,ppdev,lp
usb_storage            53538  0
uas                    17996  0
ahci                   25951  2
libahci                26642  1 ahci
tg3                   141750  0
 Aspire-5733Z:~# rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by mcalautt on 2011-08-19
amazing update.
I have been seeing a bunch of people claiming they can connect but the connection is very unstable.
I was wondering why I cant connect at all.?

so i brought it into work and gave it to a friend. He got it to work.. I said how ?
he did the same things I did.. checked rfkill list and blacklisted acer-wmi.  ( i saw posts about that
but ignored it since I dont have acer-wmi in a lsmod)
but i didnt care . he got it to work !!!

I brought it home... amazing. no connection...
and then it hit me... sun of a beeatch !!! I went down stairs and got closer to the router.
it connected instantly..
but now I have the problem that others are having.. extremely poor speed and unstable connection..

---

### Post by mcalautt on 2011-08-24
added the athr9 conf file to modprobe.d
it worked or seemed to at my house.
brought it to my mothers and it sucks !!!  i cant even be down the hall on the same
floor as the router.. its too far away.. 
now im mad..

its extremely unstable and I can see the router from where I am.. !!!!
take 2 steps foward and it will connect..
the range is miserable !!
so as far as im concerned its not usable and the problem still exists.

---

