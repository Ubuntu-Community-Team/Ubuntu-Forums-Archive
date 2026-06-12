---
title: "Can't connect wirelessly, but it says I am?"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by YMS_1975 on 2013-01-20
I just installed Ubuntu 12.10 on my Dell Studio 540 desktop.
When I try to connect wirelessly, the wireless connection icon (in the top right corner of the screen) says I'm connected. If I select "Connection Information" it shows that I'm connected.

But when I try to surf or update my OS, it gives me one of those failed to connect messages.

Can somebody help me???

---

### Post by ahallubuntu on 2013-01-20
Open a terminal window (search for "terminal" in dash).

Then in the terminal type:

```
sudo lshw -C network
```

and

```
iwconfig
```

and please produce the output here.

---

### Post by YMS_1975 on 2013-01-20
**lshw -C Network** : 

```
yousaf@yousaf-Studio-540:~$ sudo lshw -C network

[sudo] password for yousaf: 

  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:5b:c4:2b
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:e800(size=256) memory:feaff000-feafffff memory:fdff0000-fdffffff memory:feac0000-feadffff

  *-network
       description: Wireless interface
       product: BCM4321 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:22:6b:9e:14:be
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.112 ip=10.42.0.1 latency=64 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:febfc000-febfffff

yousaf@yousaf-Studio-540:~$ 

**iwconfig** :

yousaf@yousaf-Studio-540:~$ iwconfig

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:199  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

lo        no wireless extensions.


yousaf@yousaf-Studio-540:~$
```

---

### Post by ahallubuntu on 2013-01-20
This may solve your problem:

[http://askubuntu.com/questions/214156/wireless-does-not-work-anymore-after-software-update-with-ubuntu-12-10-on-a-dell](http://askubuntu.com/questions/214156/wireless-does-not-work-anymore-after-software-update-with-ubuntu-12-10-on-a-dell)

---

### Post by YMS_1975 on 2013-01-20
> **ahallubuntu said:**
> This may solve your problem:

[http://askubuntu.com/questions/214156/wireless-does-not-work-anymore-after-software-update-with-ubuntu-12-10-on-a-dell](http://askubuntu.com/questions/214156/wireless-does-not-work-anymore-after-software-update-with-ubuntu-12-10-on-a-dell)

Actually I came across that very same post in my online search, and I already tried that.

Didn't work.  :(

---

### Post by YMS_1975 on 2013-01-22
Bump!!!!

---

### Post by ubfan1 on 2013-01-23
You have an ip address, so edit the connection and see that you have the  type "automatic DHCP" selected, and NOT "DHCP no addresses".  Of  course, you router may also be unplugged from the WAN.
fourth attempt with preview

---

### Post by bogan on 2013-01-24
Hi!, **YMS_1975,**

Checkout your other THREAD:

[http://ubuntuforums.org/showthread.php?p=12471832#post12471832](http://ubuntuforums.org/showthread.php?p=12471832#post12471832)

**bogan.**

---

### Post by YMS_1975 on 2013-01-25
> **ubfan1 said:**
> You have an ip address, so edit the connection and see that you have the  type "automatic DHCP" selected, and NOT "DHCP no addresses".  Of  course, you router may also be unplugged from the WAN.
fourth attempt with preview

I checked this but still nothing. I have another laptop that connects to the wireless network just fine.

All it does is attempt to connect to the network (the wireless icon [the one with the wavy lines] moves up and down in an attempt to connect to the network) but it won't connect. Instead it says "Authentication required by wireless network" and it prompts me to enter my networks password. I KNOW that I'm entering the correct password, so that's not the problem. 


Is there any other suggestions? I'M STARTING TO GET REAL DESPARATE HERE. My desktop has been down for a few days now.  :(

---

### Post by chili555 on 2013-01-25
> configuration: broadcast=yes driver=wl0 driverversion=5.100.82.112 [COLOR="Red"]ip=10.42.0.1[/COLOR] latency=64 multicast=yes wireless=IEEE 802.11bgnYes, indeed, you have an IP address. Addresses in the range of 10.42.x.x are generally used for ad-hoc, that is computer-to-computer arrangements. Is that what you intended? No?? Is that the range used by other computers on your network? I suspect they are typical home network addresses, something likke 192.168.x.x.

Please right-click the Network Manager icon and edit connections. Select Wireless and go through each tab and remove, delete, purge all extra settings except one. Be sure Mode is set to infrastructure. Please see attached. Close everything and tell us if Network Manager finds and connects to your network as expected. It may take a reboot.

---

### Post by YMS_1975 on 2013-01-26
> **chili555 said:**
> Yes, indeed, you have an IP address. Addresses in the range of 10.42.x.x are generally used for ad-hoc, that is computer-to-computer arrangements. Is that what you intended? No?? Is that the range used by other computers on your network? I suspect they are typical home network addresses, something likke 192.168.x.x.

Please right-click the Network Manager icon and edit connections. Select Wireless and go through each tab and remove, delete, purge all extra settings except one. Be sure Mode is set to infrastructure. Please see attached. Close everything and tell us if Network Manager finds and connects to your network as expected. It may take a reboot.


I did everything as you explained, but it's still not connecting. What else can I try?

---

### Post by chili555 on 2013-01-26
> but it's still not connecting.Meaning what? Does it see networks in the dropdown? When you select yours, does it try? Does it ask for your password and time out? What does it do and not do??

---

### Post by YMS_1975 on 2013-01-26
> **chili555 said:**
> Meaning what? Does it see networks in the dropdown? When you select yours, does it try? Does it ask for your password and time out? What does it do and not do??

Sorry for not providing adequate information. Yes, it does show my network. I am typing in the correct password.

Then it attempts to connect the network, but it won't connect. Instead, a dialog box appears asking me for the password (again).When I type in the password, it continues to search, but still won't connect.

---

### Post by chili555 on 2013-01-26
Let's see what Network Mangler is doing all this time. The Broadcom STA driver is usually pretty solid.```
cat /var/log/syslog | grep etwork | tail -n20
```Please run and post that immediately after you tried and failed to connect. Be sure any ethernet cable is detached as NM will disable wireless in favor of faster and more secure ethernet if available.

---

### Post by YMS_1975 on 2013-01-26
yousaf@yousaf-Studio-540:~$ cat /var/log/syslog | grep etwork | tail -n20 
Jan 26 08:33:30 yousaf-Studio-540 NetworkManager[813]: <info> Activation (eth1/wireless): connection 'Yousaf' has security, and secrets exist.  No new secrets needed. 
Jan 26 08:33:30 yousaf-Studio-540 NetworkManager[813]: <info> Config: added 'ssid' value 'Yousaf' 
Jan 26 08:33:30 yousaf-Studio-540 NetworkManager[813]: <info> Config: added 'scan_ssid' value '1' 
Jan 26 08:33:30 yousaf-Studio-540 NetworkManager[813]: <info> Config: added 'key_mgmt' value 'WPA-PSK' 
Jan 26 08:33:30 yousaf-Studio-540 NetworkManager[813]: <info> Config: added 'psk' value '<omitted>' 
Jan 26 08:33:30 yousaf-Studio-540 NetworkManager[813]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jan 26 08:33:30 yousaf-Studio-540 NetworkManager[813]: <info> Config: set interface ap_scan to 1 
Jan 26 08:33:30 yousaf-Studio-540 NetworkManager[813]: <info> (eth1): supplicant interface state: inactive -> scanning 
Jan 26 08:33:56 yousaf-Studio-540 NetworkManager[813]: <warn> Activation (eth1/wireless): association took too long. 
Jan 26 08:33:56 yousaf-Studio-540 NetworkManager[813]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0] 
Jan 26 08:33:56 yousaf-Studio-540 NetworkManager[813]: <warn> Activation (eth1/wireless): asking for new secrets 
Jan 26 08:33:56 yousaf-Studio-540 NetworkManager[813]: <warn> Couldn't disconnect supplicant interface: This interface is not connected. 
Jan 26 08:33:56 yousaf-Studio-540 NetworkManager[813]: <warn> Couldn't disconnect supplicant interface: This interface is not connected. 
Jan 26 08:33:58 yousaf-Studio-540 NetworkManager[813]: <info> (eth1): supplicant interface state: scanning -> inactive 
Jan 26 08:34:00 yousaf-Studio-540 NetworkManager[813]: <warn> No agents were available for this request. 
Jan 26 08:34:00 yousaf-Studio-540 NetworkManager[813]: <info> (eth1): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7] 
Jan 26 08:34:00 yousaf-Studio-540 NetworkManager[813]: <info> Marking connection 'Yousaf' invalid. 
Jan 26 08:34:00 yousaf-Studio-540 NetworkManager[813]: <warn> Activation (eth1) failed for connection 'Yousaf' 
Jan 26 08:34:00 yousaf-Studio-540 NetworkManager[813]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0] 
Jan 26 08:34:00 yousaf-Studio-540 NetworkManager[813]: <info> (eth1): deactivating device (reason 'none') [0] 
yousaf@yousaf-Studio-540:~$

---

### Post by ubfan1 on 2013-01-26
So it gave up after 20+ seconds trying to connect, maybe interference? Try 
sudo iwlist scan |egrep -i "ssid|quality|channel:"
and see what channel other access points are on and how strong they are.

---

### Post by chili555 on 2013-01-26
I'd like to be sure no conflicting drivers are loaded and that *wl* is most appropriate for your device:```
lsmod
lspci -nn | grep 0280
```

---

### Post by besial on 2013-01-26
You could try to connect manually...
Save this to a file named 'wpa_supplicant.conf'
```
# WPA-PSK/TKIP

ctrl_interface=/var/run/wpa_supplicant

network={
    ssid="your_router_name_here"
    key_mgmt=WPA-PSK
    proto=WPA
    pairwise=TKIP
    group=TKIP
    psk="your_wifi_password_here"
}
```...Then run your wpa_supplicant in debug mode...
```
wpa_supplicant -iwlan0 -c ./wpa_supplicant.conf -d
```

---

### Post by YMS_1975 on 2013-01-27
> **chili555 said:**
> I'd like to be sure no conflicting drivers are loaded and that *wl* is most appropriate for your device:```
lsmod
lspci -nn | grep 0280
```

```
yousaf@yousaf-Studio-540:~$ lsmod 
Module                  Size  Used by 
dm_crypt               23011  1 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_realtek    77876  1 
parport_pc             32688  0 
ppdev                  17073  0 
bnep                   18140  2 
rfcomm                 46619  0 
bluetooth             209199  10 bnep,rfcomm 
coretemp               13400  0 
snd_usb_audio         130279  1 
snd_usbmidi_lib        24953  1 snd_usb_audio 
gpio_ich               13383  0 
dcdbas                 14438  0 
lib80211_crypt_tkip    17379  0 
microcode              22803  0 
wl                   2573568  0 
snd_hda_intel          33491  5 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec 
psmouse                95552  0 
serio_raw              13215  0 
snd_pcm                96580  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec 
lib80211               14381  2 lib80211_crypt_tkip,wl 
lpc_ich                17061  0 
snd_seq_midi           13324  0 
snd_rawmidi            30512  2 snd_usbmidi_lib,snd_seq_midi 
snd_seq_midi_event     14899  1 snd_seq_midi 
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event 
snd_timer              29425  2 snd_pcm,snd_seq 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq 
snd                    78734  24 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
pwc                    74022  0 
videobuf2_core         32851  1 pwc 
videodev              120309  2 pwc,videobuf2_core 
videobuf2_vmalloc      12860  1 pwc 
videobuf2_memops       13368  1 videobuf2_vmalloc 
joydev                 17457  0 
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp 
soundcore              15047  1 snd 
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm 
hid_generic            12493  0 
hid_microsoft          12798  0 
usbhid                 46947  0 
hid                   100366  3 hid_generic,hid_microsoft,usbhid 
uas                    17844  0 
usb_storage            48838  0 
firewire_ohci          40401  0 
radeon                895653  3 
firewire_core          64368  1 firewire_ohci 
crc_itu_t              12707  1 firewire_core 
ttm                    83595  1 radeon 
drm_kms_helper         46784  1 radeon 
drm                   275528  5 radeon,ttm,drm_kms_helper 
i2c_algo_bit           13413  1 radeon 
r8169                  61650  0 
yousaf@yousaf-Studio-540:~$ 
```

```

yousaf@yousaf-Studio-540:~$ lspci -nn | grep 0280 
05:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01) 
yousaf@yousaf-Studio-540:~$
```

---

### Post by YMS_1975 on 2013-01-27
> **ubfan1 said:**
> So it gave up after 20+ seconds trying to connect, maybe interference? Try 
sudo iwlist scan |egrep -i "ssid|quality|channel:"
and see what channel other access points are on and how strong they are.

```
yousaf@yousaf-Studio-540:~$ sudo iwlist scan |egrep -i "ssid|quality|channel:" 
[sudo] password for yousaf: 
eth0      Interface doesn't support scanning. 

lo        Interface doesn't support scanning. 

yousaf@yousaf-Studio-540:~$ 
```

*NOTE* I don't think it's interference, as I am currently in the same room as the Dell Studio 540 desktop I'm having problems with, but on a laptop running Ubuntu 12.10 and I can connect wirelessly just fine with that laptop.

So I think the desktops connectivity issues are something else. I noticed that under "Additional Drivers", it lists the Broadcom Corporation: BCM4321 802.11 b/g/n and directly below that it states : "This device is using an alternative driver".

There are 2 radio button options below that (Option #1 is selected); 

1) Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source(open source)

2) Do not use the device.

---

### Post by ubfan1 on 2013-01-27
The signal strength was just one more thing to eliminate.  Looks like you have a stray network driver r8169 that somehow got loaded.  In file /etc/modprobe.d, add the line:
blacklist r8169
That might help.

---

### Post by chili555 on 2013-01-30
> **ubfan1 said:**
> The signal strength was just one more thing to eliminate.  Looks like you have a stray network driver r8169 that somehow got loaded.  In file /etc/modprobe.d, add the line:
blacklist r8169
That might help.> In file /etc/modprobe.dThat's a directory, not a file.

That's not the proper way or place to blacklist a driver. That is also not a wireless driver; it's ethernet. Blacklisting it will do nothing to help here.

---

### Post by chili555 on 2013-01-30
May I see:```
nm-tool
```Thanks.

---

### Post by YMS_1975 on 2013-01-30
> **chili555 said:**
> May I see:```
nm-tool
```Thanks.

```
yousaf@yousaf-Studio-540:~$ nm-tool 

NetworkManager Tool 

State: disconnected 

- Device: eth1 ----------------------------------------------------------------- 
  Type:              802.11 WiFi 
  Driver:            wl 
  State:             disconnected 
  Default:           no 
  HW Address:        00:22:6B:9E:14:BE 

  Capabilities: 

  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 

  Wireless Access Points 


- Device: eth0 ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            r8169 
  State:             unavailable 
  Default:           no 
  HW Address:        00:21:70:5B:C4:2B 

  Capabilities: 
    Carrier Detect:  yes 

  Wired Properties 
    Carrier:         off 


yousaf@yousaf-Studio-540:~$ ^C 
yousaf@yousaf-Studio-540:~$
```

---

### Post by chili555 on 2013-01-30
It ought to see wireless access points here. I am mystified because previously it did:> Jan 26 08:33:30 yousaf-Studio-540 NetworkManager[813]: <info> Activation (eth1/wireless): connection '[COLOR="Red"]Yousaf[/COLOR]' has security, and secrets exist. No new secrets needed. Is there an informative message here?```
rfkill list all
sudo iwlist eth1 scan
dmesg | grep -e eth1 -e wl
```Off for a few hours, see you this evening.

---

### Post by YMS_1975 on 2013-02-04
> **chili555 said:**
> It ought to see wireless access points here. I am mystified because previously it did:Is there an informative message here?```
rfkill list all
sudo iwlist eth1 scan
dmesg | grep -e eth1 -e wl
```Off for a few hours, see you this evening.

Sorry for the delay; I had problems with my laptop as well (not Ubuntu related). Anyways, here are the results.


```
yousaf@yousaf-Studio-540:~$ rfkill list all 
0: brcmwl-0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 

yousaf@yousaf-Studio-540:~$ sudo iwlist eth1 scan 
[sudo] password for yousaf: 
eth1      No scan results 

yousaf@yousaf-Studio-540:~$ dmesg |grep -e eth1 -e wl 
[   14.317399] wl: module license 'MIXED/Proprietary' taints kernel. 
[   14.376299] eth1: Broadcom BCM4329 802.11 Hybrid Wireless Controller 5.100.82.112 

yousaf@yousaf-Studio-540:~$
```

---

### Post by Cyclops_ on 2013-02-04
I actually have the same problem.  Only it just started today after an update yesterday.

I'm running regular Ubuntu, but I do believe that I am running some "Studio" stuff.  I may even have installed the Studio package.

One interesting thing on my end (you may check yours), is that, even though it shows "connected" to the wireless network, I can't access the router through a browser (192.168.1.1).

It also can't connect to the wired network.

Finally - I know it's not hardware related.  I'm dual booted into Windows, and it's working just fine (as evidenced by this post).

I think there was some kind of update that destroyed things.  (I'm on an ASUS laptop.)

---

### Post by ozhank on 2013-02-05
In network settings, change to automatic DHCP addresses only and manually add your DNS servers ie opendns at 208.67.222.222, 208.67.220.220. This solved my problem with connection - something to do with modem thinking computer was Windows based.

---

### Post by Cyclops_ on 2013-02-05
@ozhank:  I tried that myself and it didn't really do anything :(

---

### Post by YMS_1975 on 2013-02-08
Any developments on this problem? I'm still without a functioning PC. In desparation, I tried installing Linux Mint. But I still had the exact same problem.

I know Mint is based on Ubuntu but thought I'd try it anyways.
HELLLLLPPPPPPPPPP ME.      :(

---

### Post by YMS_1975 on 2013-02-21
> **Cyclops_ said:**
> @ozhank:  I tried that myself and it didn't really do anything :(

Just curious, were you able to get your Ubuntu up and running? My PC is basically a paperweight now (I'm writing this from another PC).   ](*,)

---

### Post by varunendra on 2013-02-21
@ YMS_1975,
Please always use 'Code' tags to put your output codes in a 'code' box.
It preserves its formatting and makes the post more readable.

I have edited all your previous posts in this thread to put the codes in code box. To see an example of how to do it yourself next time, please follow the 'Code tags example' link in my signature. It is really easy and good for your posts :)

Onto your problem-

As you are already getting help from chilli555, I really can't offer any better help.

However, just to see a detailed report on current status of wireless, please follow the 'Wireless Script' link in my signature and post back its result as suggested in the linked page.

As per outputs in post #26 -
> **YMS_1975 said:**
> 
```
yousaf@yousaf-Studio-540:~$ sudo iwlist eth1 scan 
[sudo] password for yousaf: 
eth1      No scan results
```
.. it seems that either you are too far away from the access point, or there are no wireless networks in the range at all!

So please make sure there is an active wireless network within the range, and it is strong enough where you are while running the wireless script.


**@ Cyclops_**,
> **Cyclops_ said:**
> I actually have the same problem.  Only it just started today after an update yesterday.
Wireless problems are often very subjective and their cause as well as solutions may be very different for different people, although the symptoms may look the same.

As such, unless you are absolutely sure that yours is the same card, same driver and same issue, you should start a new thread of your own.

---

### Post by YMS_1975 on 2013-02-21
> **varunendra said:**
> @ YMS_1975,
Please always use 'Code' tags to put your output codes in a 'code' box.
It preserves its formatting and makes the post more readable.

I have edited all your previous posts in this thread to put the codes in code box. To see an example of how to do it yourself next time, please follow the 'Code tags example' link in my signature. It is really easy and good for your posts :)

Onto your problem-

As you are already getting help from chilli555, I really can't offer any better help.

However, just to see a detailed report on current status of wireless, please follow the 'Wireless Script' link in my signature and post back its result as suggested in the linked page.

As per outputs in post #26 -

.. it seems that either you are too far away from the access point, or there are no wireless networks in the range at all!

So please make sure there is an active wireless network within the range, and it is strong enough where you are while running the wireless script.


**@ Cyclops_**,

Wireless problems are often very subjective and their cause as well as solutions may be very different for different people, although the symptoms may look the same.

As such, unless you are absolutely sure that yours is the same card, same driver and same issue, you should start a new thread of your own.

When you say "there are no wireless networks in the range at all!" that's what I'm having trouble understanding because my phone (PDA) connects to the same wireless network from the exact same spot as the desktop that won't connect.

Anyways.....I think I'll have to go with plan B for now. ):P

---

