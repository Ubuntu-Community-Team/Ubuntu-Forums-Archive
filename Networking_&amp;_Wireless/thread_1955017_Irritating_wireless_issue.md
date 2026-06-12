---
title: "Irritating wireless issue"
date: 2012-04-09
forum: Networking &amp; Wireless
---

### Post by mooroha on 2012-04-09
Hi all 

I've just got an Asus Eee PC 901 with Ubuntu 11.10, which is great apart from problems getting the wireless up and running. 

Basically, when I boot up the machine the wireless is enabled but is not picking up anything. It displays 'wireless networks device not ready'. 

The only solution to this is to switch the wireless on and off, or reboot if that doesn't work, until eventually it will start to work. I should say that when it is up and running it works fine. 

Obviously, I know next to nothing about Ubuntu apart from what I've picked up on these forums. So any help would be much appreciated. 

Here's the wireless status if it's any help. 

sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID: off/any  
          Mode: Managed  Access Point: Not-Associated   Tx-Power= 20 dBm   
          Retry  long limit: 7   RTS thr: off   Fragment thr: off
          Encryption key: off
          Power Management: off
          
Thanks

Mooroha

---

### Post by shakabra on 2012-04-09
Have you tried this...

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/339891]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/339891")

I'm referring to the first sentence about the linux-backport-modules.

---

### Post by varunendra on 2012-04-09
Welcome to the forums mooroha.

Please provide the outputs of the following (including iwconfig again):
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
iwconfig
rfkill list all
dmesg | grep firmware
```

While posting these outputs, please click on # symbol at the top of the edit box (in which you create new posts) to auto-generate [ code] and [ /code] tags, then copy-paste the output codes in-between those tags. It preserves the code formatting and keeps the post neat and easily readable.

**_PS_:**
I've got extremely busy for last few weeks, so may not get enough time to respond. **So anybody having any idea about the OP's problem please jump in**! Thanks.

---

### Post by mooroha on 2012-04-09
Hi Varunendra - here are the outputs as requested. Thanks to you and anyone else for taking a look at this.



uname -mr
```

3.0.0-17generic i686

```
```
lspci -nnk | grep -iA2 net

01:00.0 Network controller [0280]: Ralink corp. RT2860 [1814:0781]
	Subsystem: Ralink corp. Device [1814:2790]
	Kernel driver in use: rt2800pci
--
03:00.0 Ethernet controller [0200]: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8324]
	Kernel driver in use: ATL1E
```

lsmod
```

Module                  Size  Used by
nls_iso8859_1          12617  2 
nls_cp437              12751  2 
vfat                   17308  2 
fat                    55577  1 vfat
rfcomm                 38408  8 
bnep                   17923  2 
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_realtek   254163  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
joydev                 17393  0 
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
i915                  509519  3 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17292  1 
btusb                  18160  2 
uvcvideo               67271  0 
bluetooth             148839  23 bnep,rfcomm,btusb
usb_storage            44173  2 
uas                    17699  0 
videodev               85626  1 uvcvideo
psmouse                73673  0 
rt2800pci              18340  0 
serio_raw              12990  0 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
rt2800lib              48909  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
drm                   192194  4 i915,drm_kms_helper
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48146  3 rt2800pci,rt2800lib,rt2x00pci
eeprom_93cx6           12653  1 rt2800pci
eeepc_laptop           19464  0 
soundcore              12600  1 snd
sparse_keymap          13658  1 eeepc_laptop
i2c_algo_bit           13199  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
b43                   318816  0 
ssb                    50682  1 b43
mac80211              393421  4 rt2800lib,rt2x00pci,rt2x00lib,b43
cfg80211              172427  3 rt2x00lib,b43,mac80211


lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
atl1e                  32809  0 

```

ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr 00:22:15:6b:e6:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7872 (7.8 KB)  TX bytes:7872 (7.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:e6:0e:a5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

rfkill list all
```

0: eeepc-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: eeepc-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
37: phy34: Wireless LAN
	Soft blocked: no
	Hard blocked: no
user@ubuntu:~$ ^C
```

dmesg | grep firmware
(nothing came up for this)

---

### Post by praseodym on 2012-04-09
Why is a Broadcom driver loaded?

> sudo modprobe -rfv b43 rt2800pci
sudo modprobe -v rt2800pci
Additionally, if necessary:

> echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf
if its loaded again.

---

### Post by varunendra on 2012-04-09
> **praseodym said:**
> Why is a Broadcom driver loaded?I'm wondering that too ;)
It is definitely a "conflict-over-resources" scenario:
> **mooroha said:**
> 
```

**mac80211              **393421  4 rt2800lib,rt2x00pci,rt2x00lib,[COLOR=Red]**b43**[/COLOR]
**cfg80211              **172427  3 rt2x00lib,[COLOR=Red]**b43**[/COLOR],mac80211

```

*@mooroha*,
Did you try to manually install any drivers following any of the threads around here? As for now, please blacklist the b43 driver as praseodym suggested. It should be all you need. Should anything more need to be done, you are now in perfect hands..

*@praseodym*,
Thank you for picking it up. I couldn't have asked for better ! :)

---

### Post by mooroha on 2012-04-09
Thanks guys. Yes I did get the b43 from digging around the forum. 

I tried the commands and b43 was gone when I tried lsmod again. However it still hasn't solved my problem. In actual fact, when I put the sudo modprobe -rfv b43 rt2800pci command in it disconnected the wireless. Since then I haven't been able to connect the wireless at all - its always on wireless networks device not ready. 

One other thing. When it is booting up, it does so without network configuration. 

Any other suggestions or help would be most appreciated. 

Thanks

Mooroha

---

### Post by varunendra on 2012-04-09
Oops! Sorry, I completely misread the card's name. I was under impression of RT2**7**60 which usually works with RT2800 driver, but yours is RT2**8**60. Accordingly, please do as this post suggests: [http://ubuntuforums.org/showthread.php?p=11729874](http://ubuntuforums.org/showthread.php?p=11729874)

By the way, don't be confused by associating no-connection status with the removal of b43. It was NOT the correct driver for your card anyway. If the above link doesn't help, post the outputs of the following again:
```
lspci -nnk | grep -iA2 net
lsmod
dmesg | grep -i rt2
```

---

### Post by mooroha on 2012-04-09
Hi Varun

Is there anywhere else I could get the driver? Every time I try to extract the driver an error occurs (while it seems to work fine on the others). It extracts as a tar-4 file but when I click on that it says the extraction has failed.

Thanks

Mooroha

---

### Post by varunendra on 2012-04-09
Is the error same or similar to [post #16]("http://ubuntuforums.org/showthread.php?p=11731772") in the thread I linked to? If so, then you are making the same mistake as the OP in that thread did. Solution is in the next post (#17) there. (that is- either use exact commands as in the linked guide, or remove '.bz' from its name then retry).

---

### Post by mooroha on 2012-04-10
Sorry I'm being a total newbie here but how/ where do you enter the command? ```
tar -xvf ~/2010*
``` Do you open a terminal window?

---

### Post by mooroha on 2012-04-10
Ok sorted the silly problem above. Amended the files and have got up to number 5 on the [guide]("http://michael-peeters.blogspot.in/2011/06/fixing-rt2860-wifi-chipset-under-ubuntu.html") but unsure what GCC is. Also I tried entering sudo make and got...

```
make: *** no targets specified and no makefile found. Stop
```

I'm sure this is a dumb question to the initiated but any help is v gratefully received. I don't want to end up paying someone to fix it and going back to windows.

---

### Post by varunendra on 2012-04-10
> **mooroha said:**
> Sorry I'm being a total newbie here but how/ where do you enter the command? ```
tar -xvf ~/2010*
``` Do you open a terminal window?Yes that command had to be entered in a terminal. But it is okay if you managed to do it via GUI.

> **mooroha said:**
> Ok sorted the silly problem above. Amended the files and have got up to number 5 on the [guide]("http://michael-peeters.blogspot.in/2011/06/fixing-rt2860-wifi-chipset-under-ubuntu.html") but unsure what GCC is.
GCC is a GNU C compiler package which is usually installed with "build-essential" package, and in 11.10, I think it is installed by default, so you shouldn't need to worry about it.

To confirm its availability via commandline you may run the following command in a terminal:
```
dpkg --get-selections | grep gcc
```
It should return a list of all the packages whose names contain the word "gcc". Alternately you may install synaptic to see (and install, if required) it via synaptic's GUI.

> **mooroha said:**
> 
Also I tried entering sudo make and got...
```
make: *** no targets specified and no makefile found. Stop
```I'm sure this is a dumb question to the initiated but any help is v gratefully received. I don't want to end up paying someone to fix it and going back to windows.I read somewhere that the only dumb question is the one that is 'Not asked'. As for the above issue, it is a really tricky one especially for beginners. While running the command, you are supposed to be 'in the directory' where you have extracted the packages. That is where the required 'makefile' is located.

For example, if you extracted the tar package in a directory named 'xyz' in your home, then before running "make" and the subsequent commands, you need to get 'into' that directory by ***cd xyz*** command (by default, the name of the directory would be same as the name of the tar package, except the '.tar' extension.)

(**Tip:** type only a few initial characters of the extracted directory's name, then press 'Tab' key to auto-complete the full name for you)

Feel free to ask as many question as you have, as long as they are related to your current problem. For others, you may open new threads, and they would be answered too.

**_PS_:**
Please don't mind if I get absent for long as I already stated in my first post. I've become very irregular due to heavy workload these days.

---

### Post by mooroha on 2012-04-10
Thanks v much for your patience on this Varun and the time you've taken to explain things. I think I need to learn a little more about how the Ubuntu works but I'll give it a go tomorrow (a bit late in the day now). Besides at the very least I understand what the problem is now. 

Thanks again

---

### Post by mooroha on 2012-05-07
Hi all 

Trying to wireless install driver using the following instructions...

[http://michael-peeters.blogspot.in/2011/06/fixing-rt2860-wifi-chipset-under-ubuntu.html](http://michael-peeters.blogspot.in/2011/06/fixing-rt2860-wifi-chipset-under-ubuntu.html)

However, I am sure about the bit at the end. 

> In the terminal window perform the following command:gksudo gedit /etc/modulesAdd "rt2860sta" on a line at the end of the file then save and close it.

How do you amend and save a file in terminal window?

Many thanks

M

---

### Post by mooroha on 2012-05-07
Don't worry. I can't even get beyond the sudo make part of these commands -even though Im in the right directory it still doesn't recognise the file. 

I give up. I can get wireless it just take about 30 mins of switching on and off. Love Ubuntu apart from this, so maybe I just need to get a notebook that doesn't have this Ralink chip in it.

---

