---
title: "Auto Ethernet stop working in Ubuntu 12.10"
date: 2013-02-05
forum: Networking &amp; Wireless
---

### Post by paramjeet on 2013-02-05
Hi
I am using ubuntu 12.10 on DELL Laptop XPS. I am not able to connect   with Wired Internet. It was working fine, justbefore  one day  but not   now. Wireless is working fine. I tried some  options discussed in earlier threads but   didn't help me out. Please help me.

---

### Post by varunendra on 2013-02-06
Hi Paramjeet,

Please run the following commands in a terminal and post back their outputs here -
```
lspci -nnk | grep -iA2 net
lsmod
ifconfig
nm-tool
```
While posting the outputs, make sure to wrap them in 'Code' tags. See the 'example' link in my signature to see an example of how to do it.

---

### Post by paramjeet on 2013-02-06
lspci -nnk | grep -iA2 net
```

12:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:422c] (rev 35)
    Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN [8086:1321]
    Kernel driver in use: iwlwifi
--
16:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Dell Device [1028:0468]
    Kernel driver in use: r8169

```

 lsmod
```

Module                  Size  Used by
dm_crypt               23012  0 
rfcomm                 46620  12 
parport_pc             32689  0 
bnep                   18141  2 
ppdev                  17074  0 
snd_hda_codec_hdmi     32049  4 
binfmt_misc            17501  1 
joydev                 17458  0 
arc4                   12530  2 
snd_hda_codec_realtek    78048  1 
uvcvideo               76750  0 
snd_hda_intel          33492  5 
iwlwifi               386874  0 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
videobuf2_core         32852  1 uvcvideo
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
videodev              120310  2 uvcvideo,videobuf2_core
snd_rawmidi            30513  1 snd_seq_midi
videobuf2_vmalloc      12861  1 uvcvideo
coretemp               13401  0 
videobuf2_memops       13405  1 videobuf2_vmalloc
i7core_edac            23572  0 
btusb                  22475  0 
lp                     17760  0 
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
kvm_intel             132760  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
bluetooth             209249  22 rfcomm,bnep,btusb
mac80211              539958  1 iwlwifi
nvidia              11263008  43 
kvm                   414071  1 kvm_intel
cfg80211              206797  2 iwlwifi,mac80211
parport                46346  3 parport_pc,ppdev,lp
snd                    78921  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                95595  0 
soundcore              15048  1 snd
edac_core              52452  1 i7core_edac
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
serio_raw              13216  0 
mei                    40691  0 
dell_laptop            17370  0 
dell_wmi               12682  0 
dcdbas                 14439  1 dell_laptop
sparse_keymap          13891  1 dell_wmi
mxm_wmi                13022  0 
mac_hid                13206  0 
jmb38x_ms              17417  0 
lpc_ich                17062  0 
wmi                    19071  2 dell_wmi,mxm_wmi
memstick               16555  1 jmb38x_ms
microcode              22804  0 
sdhci_pci              18617  0 
r8169                  61651  0 
sdhci                  32646  1 sdhci_pci
video                  19336  0 

```

 ifconfig
```

eth0      Link encap:Ethernet  HWaddr b8:ac:6f:c5:1f:39  
          inet6 addr: fe80::baac:6fff:fec5:1f39/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:432 (432.0 B)  TX bytes:12868 (12.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1400 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:173934 (173.9 KB)  TX bytes:173934 (173.9 KB)

```

 nm-tool
```
NetworkManager Tool

State: connecting

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        B8:AC:6F:C5:1F:39

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unavailable
  Default:           no
  HW Address:        58:94:6B:E5:55:4C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points
```

---

### Post by chili555 on 2013-02-06
My good friend varunendra is probably going to walk you through this: [http://code.google.com/p/r8168/downloads/list](http://code.google.com/p/r8168/downloads/list)

In preparation, if your wireless will connect, please open a terminal and do:```
sudo apt-get install linux-headers-generic build-essential
cd Desktop
wget http://r8168.googlecode.com/files/r8168-8.035.00.tar.bz2
```He will take it from here.

---

### Post by paramjeet on 2013-02-06
Thanks for your response.
```

sudo apt-get install linux-headers-generic build-essential
[sudo] password for param: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

I have downloaded the file r8168-8.035.00.tar.bz2 on Desktop. What next?

---

### Post by chili555 on 2013-02-06
I was hoping Varun would be able to help. I know he's quite busy these days and so I'll jump in.

Find the file on your desktop. Right-click it and select 'Extract Here.' Now open a terminal and do:```
cd Desktop/r8168-8.035.00
sudo ./autorun.sh
```It will unload the apparently defective r8169 and replace it with r8168. Does your ethernet work now?

The new driver is built for the currently running kernel version only. When Update Manager installs a newer kernel, also known as linux-image, repeat the process above after you reboot as instructed by Update Manager.

---

### Post by varunendra on 2013-02-06
> **chili555 said:**
> I was hoping Varun would be able to help. I know he's quite busy these days and so I'll jump in.

Evidently, I'm at least 30 minutes late, :) but it's a great pleasure to have you on the thread.

Yeah that used to be the usual solution for RTL8168B/r8169 driver combination issue. However in this case I would do a few tests before trying the r8168 driver for **[COLOR="Navy"]mainly two reasons-[/COLOR]**
[LIST=1]
[*][COLOR="Navy"]Ever since 12.04 has come out, I have rarely seen anyone having this problem *[COLOR="DarkSlateGray"](must admit I have seen one or two, but they were negligible compared to the no. of cases we used to see earlier)[/COLOR]*. On the other hand, I've seen quite a few posts reporting that although the posters used to resort to r8168 earlier, r8169 is working flawlessly for them since 12.04.[/COLOR]
[*][COLOR="DarkRed"]The cases where this problem used to prevail, were cases of 'intermittent' connections, not a complete blackout. That is, the interface used to get an IP, but kept disconnecting, especially during heavy traffic.[/COLOR]
[/LIST]

**@ parminder,**
First of all, please make it a habit to post the output codes within 'Code' tags. It preserves formatting and makes the post look neat and more readable. I'm going to do this for you now, but please keep this in mind next time you post - for your own good *[COLOR="DarkSlateGray"](once again, follow the example link in my signature if you're wondering 'how to do that')[/COLOR]*.

Onto your problem -
I usually bow to the divine instincts of chili555, but it won't hurt to check/try a couple of things befor you try what he suggested *[COLOR="DarkSlateGray"](or I would have suggested if these don't work)[/COLOR]*-
[LIST]
[*]Check your physical connection - the cable and possibility of loose connections
[*]Power off your router/network switch > wait for at least 20 seconds > power on again > then on your ubuntu system, do-
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient
```
[*]If the above doesn't bring the ethernet to life, try manually assigning an IP address to it. For example, if your router/modem's IP is 192.168.1.1, then try -
```
sudo ifconfig eth0 192.168.1.**60**
```(you may replace the last "60" with whatever number between 2 and 254 that is not 'taken' by another device on your network)
Then test -
```
ping 192.168.1.1
``` (assuming your router is indeed 192.168.1.1)
Do you get any replies? If yes, it's a good news. If not, it's probably time to do what chili555 suggested above.
[/LIST]
Although, as I suspect, if the reason is something other than driver, then the problem will prevail even with r8168. That's why I'm trying to rule out other possibilities first.

And oh, please don't forget the code tags next time when you post output codes :)

---

### Post by paramjeet on 2013-02-07
Thanks Varun and Chili555. 
I  already adopted the suggestion given by Chili555 (before the reply of  Varun) and replaced the driver. After replacement internet was not working at home. Now I bring my laptop at my office. I have two LAN connection for  Internet in my office. Now LAN is working by using one line, not in other.  There is no problem with wired connection as it is working in my desktop from both the lines.  Even I checked the port at home with another laptop, LAN is working. Now driver in use is r8168. I tried ifconfig up and down and dhclient but still internet not working... 

Regarding posting of code: Thanks Varun, I will keep in mind next time.

---

### Post by varunendra on 2013-02-07
A few questions -

* Can you confirm if your home router/modem has DHCP enabled? If not, dhclient command would do nothing, and you need to manually assign the IP.

* Do you know the IP of your router at home? Can you share it with us? There are no security issues in sharing your LAN side IP (often 192.168... pattern)

* Did you contact tech support in your office? What did they say?

* Can you confirm if both your office networks have DHCP enabled or not?

Since your desktop in office is able to connect with both networks, you may try to manually assign the same configuration to your laptop to see if it can connect this way to the one which was not working.

You already know the Ubuntu command to see the network configuration - **nm-tool**

The Windows command to see the network configuration is (@ command prompt) - **ipconfig**
(the gui method varies per windows version)
Note down the confguration (IP, Gateway and DNS) and assign the same in Network Manager in Ubuntu. See if it helps it connect to the problematic network.

Whether or not you can connect this way may decide our next course of action.

---

### Post by paramjeet on 2013-02-07
@ Varun: Reply of your questions:

1. Both the Internet connection  has same properties and settings, provided by our university. Automatic  DHCP.  We never need to assign any IP etc. 
I don't know IP of home router but here is 137.158.125.120 in my desktop with same wired connection. 

2.  I don't know the IP of home router. But both the internet are same, provided by our university. 

3. I am still waiting for reply of e-mail from our tech support team.  But  they provide limited support for ubuntu. I mean not too many   expectations from them.

4. I confirmed from a colleague that all office networks have DHCP enabled. 

I  tried  manually assign the same configuration to my laptop. Internet  connected immediately (Icon of connectivity appears , two parallel rows) but I  can't use internet in browser. Nothing happens.

---

### Post by chili555 on 2013-02-07
Are you hooked to a router? 137.158.x.y sounds like a public IP address, like you are hooked directly to the cable or DSL modem.

Capetown?

---

### Post by paramjeet on 2013-02-07
Yea its wired internet. I dont know much about the technical details. Is there any possibility to solve this issue? Internet is conecting by manual assigning the IPs etc but not useful. Also working from other wired conection in office, not from home.

---

### Post by paramjeet on 2013-02-13
I guess a fresh reinstall will be only option. Thanks for all helping me in the matter.

---

