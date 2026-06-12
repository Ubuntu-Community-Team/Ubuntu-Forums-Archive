---
title: "wireless got very slow on ubuntu 11.10"
date: 2012-03-06
forum: Networking &amp; Wireless
---

### Post by cyb0t on 2012-03-06
i have been using ubuntu 11.10 64-bit for 3 months..it was working fine.

But yesterday internet got very slow. So I checked with windows xp in vmware in the same system it is normal..but ubuntu has the problem.

Im using a Dell studio laptop
which has 
```
id:    network
description:     Wireless interface
product:     WiFi Link 5100
vendor:     Intel Corporation
physical id:     0
bus info:     pci@0000:04:00.0
logical name:     wlan0
version:     00
serial:     00:22:fb:47:2e:ba
width:     64 bits
clock:     33MHz
capabilities:     pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration:    
broadcast    =    yes
driver    =    iwlagn
driverversion    =    3.0.0-16-generic
firmware    =    8.83.5.1 build 33692
ip    =    192.168.0.106
latency    =    0
link    =    yes
multicast    =    yes
wireless    =    IEEE 802.11abgn
resources:    
irq    :    46
memory    :    f8000000-f8001fff
```it has no problem connecting to wireless networks but internet got very slow.
'iwconfig' gives 
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"XXXX"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 98:FC:11:C9:65:21   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:72   Missed beacon:0

```i tried things from this thread ([http://ubuntuforums.org/showthread.php?t=1592846](http://ubuntuforums.org/showthread.php?t=1592846)) but no solution. And disactivating IPv6 doesn't help either.

Any one has a solution pls let me know :)

---

### Post by cyb0t on 2012-03-08
it seems there is some problem with browsing because when I'm downloading with JDownloader its getting the normal speed. browsing is too slow.
When I open a link in firefox it keeps looking up for that link for a long time without connecting (in status bar). And in chromium it says sending request and after sometime it gives[COLOR=#000000][FONT=Helvetica] an error 'This webpage is not available (took too long to respond)'. 
The good thing in firefox is it connects but it taked a lot of time to connect and to load a page. In chromium sometimes it connects but most of the time it fails.
[/FONT][/COLOR]

---

### Post by wildmanne39 on 2012-03-09
Hi, try this please:
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up
```
do not restart the computer after you run these commands and if it helps we will need to make it permanent.
Thanks

---

### Post by cyb0t on 2012-03-10
thanx for the reply :)

but nothing changed with those commands!!

---

### Post by wildmanne39 on 2012-03-10
Hi, how did you deactivate IPV6?

You need to go into network manager settings at the top of the screen and click on it then edit connections, wireless and change your settings to look like mine.
Thanks

---

### Post by cyb0t on 2012-03-11
by the following commands
```
echo "#disable ipv6" | sudo tee -a /etc/sysctl.conf 
echo "net.ipv6.conf.all.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf 
echo "net.ipv6.conf.default.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf 
echo "net.ipv6.conf.lo.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
```

I changed the DNS as you told and saved..still it is slow (no change).
And when i check the Connection Information it seems DNS is not changing..it is showing the previous DNS. Not the one I defined. 
Do I have to restart after changing the DNS?

---

### Post by wildmanne39 on 2012-03-11
Hi, yes you need to restart and make sure you put the comma as it shows in the screenshot.
thanks

---

### Post by cyb0t on 2012-03-11
Hi, thanx for the reply!

DNS changed after a reboot but it doesn't help with the browsing speed.

---

### Post by wildmanne39 on 2012-03-11
Hi, I am sorry but we have tried everything that I know to try.

---

### Post by cyb0t on 2012-03-12
Ok. Thanx a lot!!

---

### Post by cyb0t on 2012-03-22
hey guys, 
i found a solution from [this thread]("http://ubuntuforums.org/showthread.php?t=1778622")

what to do is: 
```
sudo nano /etc/nsswitch.conf
```Find the line:
hosts: files mdns4_minimal [NOTFOUND=retutrn] dns mdns4
Change the order so it says:
hosts: files dns mdns4_minimal [NOTFOUND=retutrn] mdns[FONT=monospace]4[/FONT]
[FONT=monospace]**Ctrl+X and be done**[/FONT]

I have no idea what it is but it is working.

And I have no clue why it caused a problem after so many days??

---

### Post by Ferrom on 2012-04-08
> **wildmanne39 said:**
> Hi, try this please:
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up
```do not restart the computer after you run these commands and if it helps we will need to make it permanent.
Thanks
I apologize for the grave-dig but this worked very well for me - now how do I make it permanent?

---

### Post by kevdog on 2012-04-08
> **Ferrom said:**
> I apologize for the grave-dig but this worked very well for me - now how do I make it permanent?

sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up

What these commands did was basically to reload the iwlagn driver or kernel module with the 11n_disable option enabled (1=enable, 0=disable).  You basically want to load this kernel module at boot with the 11n_disable option enabled.  This would be done by modifying your /etc/modules file by the following:

echo "iwlagn 11_ndisable=1" | sudo tee -a /etc/modules

Hopefully that works for you!  To revert the changes, edit the /etc/modules file as root and remove the line starting with iwlagn.

---

### Post by Ferrom on 2012-04-08
> **kevdog said:**
> sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up

What these commands did was basically to reload the iwlagn driver or kernel module with the 11n_disable option enabled (1=enable, 0=disable).  You basically want to load this kernel module at boot with the 11n_disable option enabled.  This would be done by modifying your /etc/modules file by the following:

echo "iwlagn 11_ndisable=1" | sudo tee -a /etc/modules

Hopefully that works for you!  To revert the changes, edit the /etc/modules file as root and remove the line starting with iwlagn.
Thank you very much!

---

### Post by Ferrom on 2012-04-09
> **kevdog said:**
> sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up

What these commands did was basically to reload the iwlagn driver or kernel module with the 11n_disable option enabled (1=enable, 0=disable).  You basically want to load this kernel module at boot with the 11n_disable option enabled.  This would be done by modifying your /etc/modules file by the following:

echo "iwlagn 11_ndisable=1" | sudo tee -a /etc/modules

Hopefully that works for you!  To revert the changes, edit the /etc/modules file as root and remove the line starting with iwlagn.
It seems that after rebooting the problem emerged again. I copy-pasted your command into Terminal. Any other ideas?

---

### Post by wildmanne39 on 2012-04-09
Hi, did you make it permanent?

```
gksudo gedit /etc/modprobe.d/iwlagn.conf
```
is there anything in this file?

If not Add a single line:
```
options iwlagn nohwcrypt=1

```
Proofread carefully, save and close gedit. Reboot.
Thanks

---

### Post by Ferrom on 2012-04-09
> **wildmanne39 said:**
> Hi, did you make it permanent?

```
gksudo gedit /etc/modprobe.d/iwlagn.conf
```
is there anything in this file?

If not Add a single line:
```
options iwlagn nohwcrypt=1

```
Proofread carefully, save and close gedit. Reboot.
Thanks
There was nothing in the file and I copied the line as it was written. After rebooting I couldn't even connect to any wireless connections. I removed the line and reboot again and now I can connect to wireless networks but I still have to enter:```
"sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up
```
to be able to use the internet effectively. Could kevdog's solution be interfering with yours in any way? I haven't reverted his changes yet as it has not affected me detrimentally.

---

### Post by kevdog on 2012-04-09
Try listing iwlagn by itself on a line within the /etc/modules file.  I think the problem is still the option is not being passed when the module is loading

---

### Post by wildmanne39 on 2012-04-15
Hi, it sounds like you may have had a typo, just copy and paste for accuracy the line in post 16.
Thanks

---

### Post by sharkey77 on 2012-04-26
None of these work for me.

I'm pulling over 13MB wireless (other computers) and in windows wired (this computer) but only 3 in Ubuntu with wired connection.  Excessive timeouts while looking up domains.  It is not a DNS issue or this computer.  It is Ubuntu.

Any other ideas?

3:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Dell Device [1028:04ed]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 43
	Region 0: I/O ports at e000 [size=256]
	Region 2: Memory at d0004000 (64-bit, prefetchable) [size=4K]
	Region 4: Memory at d0000000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

eth0      Link encap:Ethernet  HWaddr d4:be:d9:bc:23:48  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::d6be:d9ff:febc:2348/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32747 errors:0 dropped:32747 overruns:0 frame:32747
          TX packets:28895 errors:0 dropped:169 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41885273 (41.8 MB)  TX bytes:5095384 (5.0 MB)
          Interrupt:43 Base address:0xc000 

EDIT:  I am in the wrong forum as this is a wired connection.  :oops:

---

### Post by wildmanne39 on 2012-04-26
Hi sharkey77, most likely you are using the wrong driver for your wired connection, but this is a wireless thread.

Please post the output of:
```
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by sharkey77 on 2012-04-26
> **wildmanne39 said:**
> Hi sharkey77, most likely you are using the wrong driver for your wired connection, but this is a wireless thread.

Please post the output of:
```
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

r8169 .. Posting in [http://ubuntuforums.org/showthread.php?t=1904264](http://ubuntuforums.org/showthread.php?t=1904264) now.

Thanks

---

### Post by sharkey77 on 2012-04-26
Wireless is slow too.  Been using it about 1 min .. does not seem as slow as ethernet but time will tell.

 Link encap:Ethernet  HWaddr e4:d5:3d:53:0e:9a  
          inet addr:192.168.0.87  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::e6d5:3dff:fe53:e9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2511841 (2.5 MB)  TX bytes:462563 (462.5 KB)

Edit:  Dns is faster (still not instant like I'm used to) with wireless but download speed is similar to ethernet in Ubuntu. Around 3 megs vs 13-14 in windows and on other computers.

---

### Post by wildmanne39 on 2012-04-26
Hi, post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by sharkey77 on 2012-04-26
```
patrick@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux ubuntu 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
patrick@ubuntu:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Dell Device [1028:0204]
	Kernel driver in use: ath9k
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Dell Device [1028:04ed]
	Kernel driver in use: r8169
patrick@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 046d:0a0c Logitech, Inc. Clear Chat Comfort USB Headset
Bus 002 Device 004: ID 413c:2107 Dell Computer Corp. 
Bus 002 Device 005: ID 046d:c05a Logitech, Inc. Optical Mouse M90
patrick@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Sharkey"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: CC:7D:37:6E:D3:32   
          Bit Rate=12 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=35/70  Signal level=-75 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:85  Invalid misc:4524   Missed beacon:0

patrick@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
patrick@ubuntu:~$ lsmod
Module                  Size  Used by
iwlagn                314257  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_conexant    62197  1 
snd_usb_audio         118122  2 
snd_usbmidi_lib        25371  1 snd_usb_audio
arc4                   12529  2 
snd_hda_intel          33390  2 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                96714  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30547  2 snd_usbmidi_lib,snd_seq_midi
ath9k                 127538  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mac80211              462046  2 iwlagn,ath9k
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
dcdbas                 14490  0 
ath9k_common           13839  1 ath9k
ath9k_hw              312914  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
snd                    68266  20 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199630  4 iwlagn,ath9k,mac80211,ath
i915                  571251  3 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41480  0 
drm_kms_helper         42558  1 i915
drm                   236290  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
psmouse                73882  0 
serio_raw              13166  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
r8169                  52788  0 

```

---

### Post by sharkey77 on 2012-04-26
Wireless is fine.  I don't use it on this computer (hard wired) so I never connected the attenas.  I put them on and my speed is; 

Download Speed: 14086 kbps (1760.8 KB/sec transfer rate)
Upload Speed: 14625 kbps (1828.1 KB/sec transfer rate)

---

### Post by wildmanne39 on 2012-04-26
Hi, your wireless probably will work better if you do this and make sure you copy and paste all commands for accuracy.
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```

Add a this one line:

```
options ath9k nohwcrypt=1
```

Proofread carefully, save and close gedit. Reboot.

If you have not got helped with wired yet, you are using the wrong driver, here is a link you need post 6.
[http://ubuntuforums.org/showthread.php?t=1955569&highlight=8168](http://ubuntuforums.org/showthread.php?t=1955569&highlight=8168)
Thanks

---

