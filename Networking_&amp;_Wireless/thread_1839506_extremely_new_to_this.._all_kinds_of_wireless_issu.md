---
title: "extremely new to this.. all kinds of wireless issues"
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by CJJones829 on 2011-09-05
OK.. please help me, if possible.  I'm completely new to ALL of this.

I installed Ubuntu today and everything was going smoothly.  After the installation, it asked if I wanted to do all the necessary updates.  I said yes!  It downloaded all of the updates.

After restarting my computer after the updates, I've all of a sudden been completely unable to connect to my my home wireless connection.

Either 1 of 2 things happen.. NONE of the connections show up and I'm shown as "disconnected", OR, it asks me for my password/key/whatever, I enter it, and it still doesn't go through.

I've tried to search topics similar on here, but I just cannot follow what everybody's saying in the topic.

Anybody willing to help a REAL beginner here on solving the issue?

Thank you!!!

---

### Post by praseodym on 2011-09-05
Hello,

can you show the following outputs of "terminal" commands:

```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
copy/paste them by line and press enter. Then you can copy the outputs here in.

---

### Post by CJJones829 on 2011-09-05
How do you guys do this when you're on a completely different computer?  Wireless doesn't work on the laptop that I'm having issues on, so I can't be logged on there to copy/paste.

I'll try this by copying and pasting to a jump drive.  Hold on just a sec.  Thanks for your help.

---

### Post by praseodym on 2011-09-05
Yes, c/p the outputs into a .txt file and upload it

---

### Post by CJJones829 on 2011-09-05
> **praseodym said:**
> Hello,

can you show the following outputs of "terminal" commands:

```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
copy/paste them by line and press enter. Then you can copy the outputs here in.

OK.. Like I said.. I'm an extremely newbie on this.

I'm on the terminal, and it comes up with the computer name with some letters and #'s.  

Do I just type in everything you wrote up there?  How do you space down?

Sorry.... :confused:

---

### Post by CJJones829 on 2011-09-05
OK I just typed them in one-by-one..

```
corey@CJ-Satellite-C655D:~$ uname -a
Linux CJ-Satellite-C655D 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 athlon i386 GNU/Linux
corey@CJ-Satellite-C655D:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8182]
	Kernel driver in use: rtl8192ce
--
06:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
	Subsystem: Toshiba America Info Systems Device [1179:ff1e]
	Kernel driver in use: atl1c
corey@CJ-Satellite-C655D:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 10f1:1a34  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
corey@CJ-Satellite-C655D:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_conexant    43782  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
radeon                900494  3 
snd_seq_midi_event     14475  1 snd_seq_midi
arc4                   12473  2 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
rtl8192ce             120858  0 
rtlwifi                78961  1 rtl8192ce
binfmt_misc            13213  1 
snd_timer              28659  2 snd_pcm,snd_seq
mac80211              257001  2 rtl8192ce,rtlwifi
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    65184  1 radeon
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
drm_kms_helper         40745  1 radeon
uvcvideo               66851  0 
shpchp                 32345  0 
cfg80211              156212  2 rtlwifi,mac80211
drm                   184164  5 radeon,ttm,drm_kms_helper
videodev               75143  1 uvcvideo
sp5100_tco             13456  0 
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_piix4              13095  0 
k10temp                12951  0 
i2c_algo_bit           13184  1 radeon
sparse_keymap          13666  0 
video                  18951  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  1 
uas                    17676  0 
atl1c                  36237  0 
ahci                   21591  2 
libahci                25548  1 ahci
corey@CJ-Satellite-C655D:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"2WIRE082"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
corey@CJ-Satellite-C655D:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
corey@CJ-Satellite-C655D:~$ 

```

Hopefully this helps!

---

### Post by praseodym on 2011-09-05
Type one of the command lines and press ENTER. One by one.

---

### Post by CJJones829 on 2011-09-05
```
corey@CJ-Satellite-C655D:~$ uname -a
Linux CJ-Satellite-C655D 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 athlon i386 GNU/Linux
corey@CJ-Satellite-C655D:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8182]
	Kernel driver in use: rtl8192ce
--
06:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
	Subsystem: Toshiba America Info Systems Device [1179:ff1e]
	Kernel driver in use: atl1c
corey@CJ-Satellite-C655D:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 10f1:1a34  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
corey@CJ-Satellite-C655D:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_conexant    43782  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
radeon                900494  3 
snd_seq_midi_event     14475  1 snd_seq_midi
arc4                   12473  2 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
rtl8192ce             120858  0 
rtlwifi                78961  1 rtl8192ce
binfmt_misc            13213  1 
snd_timer              28659  2 snd_pcm,snd_seq
mac80211              257001  2 rtl8192ce,rtlwifi
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    65184  1 radeon
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
drm_kms_helper         40745  1 radeon
uvcvideo               66851  0 
shpchp                 32345  0 
cfg80211              156212  2 rtlwifi,mac80211
drm                   184164  5 radeon,ttm,drm_kms_helper
videodev               75143  1 uvcvideo
sp5100_tco             13456  0 
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_piix4              13095  0 
k10temp                12951  0 
i2c_algo_bit           13184  1 radeon
sparse_keymap          13666  0 
video                  18951  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  1 
uas                    17676  0 
atl1c                  36237  0 
ahci                   21591  2 
libahci                25548  1 ahci
corey@CJ-Satellite-C655D:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"2WIRE082"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
corey@CJ-Satellite-C655D:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
corey@CJ-Satellite-C655D:~$ 

```

OK.. let's try this again.  Bare with me guys..

---

### Post by praseodym on 2011-09-05
Ok,

the driver "rtl8192ce" is loaded, the card is "on" and it finds your network:

```
wlan0     IEEE 802.11bgn  ESSID:"[COLOR="Red"]2WIRE082[/COLOR]"  
          Mode:Managed  Frequency:2.417 GHz  Access Point:
          Not-Associated   
          [COLOR="Red"]Tx-Power=20 dBm[/COLOR]
```
Which encryption mode do you use? Mixed WPA/WPA2 encryption often causes problems with the Network-Manager. Can you change to WPA2-AES only?

Please show additionally:

```
dmesg | egrep 'rtl8|r8'
sudo iwlist scan
```
After the second "sudo"-command you are asked to type in your password, without ****** or other hints.

---

### Post by CJJones829 on 2011-09-05
```
corey@CJ-Satellite-C655D:~$ dmesg | egrep 'rtl8|r8'
[   12.569446] rtl8192ce 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.569467] rtl8192ce 0000:02:00.0: setting latency timer to 64
corey@CJ-Satellite-C655D:~$ sudo iwlist scan
[sudo] password for corey: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

corey@CJ-Satellite-C655D:~$ 
```

Where do you want me to try and change that WPA2 setting?  I edited the the specific connection I'm trying to jump on, 2WIRE082, but it didn't have an option for WPA2 only.

---

### Post by CJJones829 on 2011-09-05
Oh, and I currently use WPA & WPA2 Personal.  Hopefully this is what you're looking for.  Thanks a TON for your help.

---

### Post by praseodym on 2011-09-05
The encryption mode can be changed if you connect via cable to the router and type in the router IP-adress in your browser. Does the router accept new clients (MAC-address filter turned **off**)? If you dont know the IP address, show:

```
cat /etc/resolv.conf
route -n
```

---

### Post by CJJones829 on 2011-09-05
```
corey@CJ-Satellite-C655D:~$ cat /etc/resolv.conf
# Generated by NetworkManager
corey@CJ-Satellite-C655D:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
corey@CJ-Satellite-C655D:~$ 


```

I have no idea as far as the router goes.  It's an AT&T router, and I don't have anything to plug it into my laptop.

Also, I don't know if this info helps.. but when I installed the new OS, the internet WORKED, it installed all of the updates available, and after the restart, only THEN did it stop working.  Makes me wonder if one of those billions of updates messed me up.

Thanks for being patient with me on this..

---

### Post by praseodym on 2011-09-05
Ok, I see, you dont have nameservers in you /etc/resolv.conf. Add those of the google public nameservers by hand:

```
echo "nameserver 8.8.8.8" | sudo tee -a /etc/resolv.conf
echo "nameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by CJJones829 on 2011-09-05
OK, typed all of that in.  Now what do I do?  I still have the Terminal open, just incase!

---

### Post by CJJones829 on 2011-09-05
OH.. and this is what came up after all of that:

```
corey@CJ-Satellite-C655D:~$ echo "nameserver 8.8.8.8" | sudo tee -a /etc/resolv.conf
[sudo] password for corey: 
nameserver 8.8.8.8
corey@CJ-Satellite-C655D:~$ echo "nameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
nameserver 8.8.4.4
corey@CJ-Satellite-C655D:~$ sudo service network-manager restart
network-manager start/running, process 2450
corey@CJ-Satellite-C655D:~$ 


```

---

### Post by praseodym on 2011-09-05
Can you connect now?

Check:

```
route -n
iwconfig
sudo iwlist scan
ping -c 4 213.95.41.11
```

---

### Post by CJJones829 on 2011-09-05
It's all showing as "device not ready" now, instead of "disconnected".

```
corey@CJ-Satellite-C655D:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
corey@CJ-Satellite-C655D:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
corey@CJ-Satellite-C655D:~$ sudo iwlist scan
[sudo] password for corey: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

corey@CJ-Satellite-C655D:~$ ping -c 4 213.95.41.11
connect: Network is unreachable
corey@CJ-Satellite-C655D:~$ 

```

---

### Post by praseodym on 2011-09-05
Hmmm,

checkbox _all_ user rights under "Users&Groups"->"Advanced Setting" (I dont know the exact reading on that button in english) and login again. After that remove your profile in the network-manager applet and setup a new wireless connection in "Infrastructure"-modus using your ESSID and key.

---

### Post by CJJones829 on 2011-09-05
Restarted and now it's TRYING to connect again.  It's showing all of the available networks too.  But it just keeps trying and trying with no avail.

---

### Post by CJJones829 on 2011-09-05
> **praseodym said:**
> Hmmm,

checkbox _all_ user rights under "Users&Groups"->"Advanced Setting" (I dont know the exact reading on that button in english) and login again. After that remove your profile in the network-manager applet and setup a new wireless connection in "Infrastructure"-modus using your ESSID and key.

OK, I deleted the previous wireless connection.  I'm stuck on adding the new one.  I see SSID field is blank.  Mode says "Infrastructure" and the rest of the fields are blank, BSSID, Device MAC Address, Cloned MAC Address, and the bottom says MTU: automatic.

What exactly do I type in and where?  What's the ESSID?  I know the network key.

---

### Post by praseodym on 2011-09-05
On page 1 this was your ESSID (name of the network):

```
wlan0     IEEE 802.11bgn  ESSID:"[COLOR="Red"]2WIRE082[/COLOR]" 
```

If this is your network. Type the ESSID into the SSID field and the key into the "network security" rider, chosing your encryption mode you are using. Normally its "WPA & WPA2 Personal".

---

### Post by CJJones829 on 2011-09-05
> **praseodym said:**
> On page 1 this was your ESSID (name of the network):

```
wlan0     IEEE 802.11bgn  ESSID:"[COLOR="Red"]2WIRE082[/COLOR]" 
```

If this is your network. Type the ESSID into the SSID field and the key into the "network security" rider, chosing your encryption mode you are using. Normally its "WPA & WPA2 Personal".

OK.. did this.. now it's asking me for "authentication required for wireless network".  Is this the key again?

---

### Post by praseodym on 2011-09-05
no, its your password, you need admin rights for setting up a new connection

---

### Post by CJJones829 on 2011-09-05
OK.  I put my password in and it started trying to connect again.  And now I just got the same "authentication required by wireless network" message again.  Almost like something is holding it back..

---

### Post by CJJones829 on 2011-09-05
And the password is fine, because I've used the same password for other admin fuctions perfectly fine.

So frustrating.  :(

What do you think?

Thanks again for your patience.

---

### Post by praseodym on 2011-09-05
Did you try the key instead?

---

### Post by CJJones829 on 2011-09-05
Everything froze up on me..

Restarting and I will try the key instead.  Thanks. 

This is so weird.. considering it worked before the updates.

---

### Post by CJJones829 on 2011-09-05
After restarting, I got a message stating "Enter password for keyring 'Default' to unlock", "an application wants access to the keyring 'Default', but it is locked", then asks for a password.

What is this??  Admin password again??  Maybe it's related to the problem.

I also get 3 radio button options to:
-"lock this keyring when I log out"
-"Lock this keyring after __ mins"
-"Lock this keyring if idle for __ mins"
(there's also a radio button for "Automatically unlock this keyring whenever I'm logged in", but it's grayed out.  Maybe I need this?)

Thoughts?  I'll wait to proceed.

---

### Post by praseodym on 2011-09-05
Yes, admin password. You can checkbox "available for all users" and "connect automatically" in the network-manager applet.

You can change the password of the gnome-keyring ("passwords & keys") in the rider Passwords by right klick->Passwords:login->change password to your login PW.

---

### Post by CJJones829 on 2011-09-05
OK!  I added the connection again after changing all of the password stuff.. it said "Connection established".. but I can't actually do anything online!

So confused..

The wifi symbol also isn't "lit up" like it was before I downloaded the updates.. indicating that it's not really connected to anything.

What do you think?

---

### Post by praseodym on 2011-09-05
Check:

```
iwconfig
ifconfig -a
sudo iwlist scan
iwlist chan
cat /var/lib/NetworkManager/NetworkManager.state
rfkill list
route -n
cat /etc/resolv.conf
cat /etc/network/interfaces
```
Have to go to bed now, will answer tomorrow.

---

### Post by CJJones829 on 2011-09-05
```
corey@CJ-Satellite-C655D:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"2WIRE028"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 36:CC:6F:5D:36:E1   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
corey@CJ-Satellite-C655D:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:26:6c:c1:9b:5e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:40 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19768 (19.7 KB)  TX bytes:19768 (19.7 KB)

wlan0     Link encap:Ethernet  HWaddr b4:74:9f:f7:7d:64  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::b674:9fff:fef7:7d64/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:20036 (20.0 KB)

corey@CJ-Satellite-C655D:~$ sudo iwlist scan
[sudo] password for corey: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 36:CC:6F:5D:36:E1
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:on
                    ESSID:"2WIRE028"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 106640ms ago
                    IE: Unknown: 00083257495245303238
                    IE: Unknown: 010882040B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD070050F202000100

corey@CJ-Satellite-C655D:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency=2.412 GHz (Channel 1)

corey@CJ-Satellite-C655D:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
corey@CJ-Satellite-C655D:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
corey@CJ-Satellite-C655D:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.43.0      0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
corey@CJ-Satellite-C655D:~$ cat /etc/resolv.conf
# Generated by NetworkManager
corey@CJ-Satellite-C655D:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

corey@CJ-Satellite-C655D:~$ 

```

---

### Post by bkratz on 2011-09-05
> **CJJones829 said:**
> ```
corey@CJ-Satellite-C655D:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"2WIRE028"  
         [COLOR="Red"] Mode:Ad-Hoc[/COLOR]  Frequency:2.412 GHz  Cell: 36:CC:6F:5D:36:E1   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
corey@CJ-Satellite-C655D:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:26:6c:c1:9b:5e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:40 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19768 (19.7 KB)  TX bytes:19768 (19.7 KB)

wlan0     Link encap:Ethernet  HWaddr b4:74:9f:f7:7d:64  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::b674:9fff:fef7:7d64/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:20036 (20.0 KB)

corey@CJ-Satellite-C655D:~$ sudo iwlist scan
[sudo] password for corey: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 36:CC:6F:5D:36:E1
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:on
                    ESSID:"2WIRE028"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 106640ms ago
                    IE: Unknown: 00083257495245303238
                    IE: Unknown: 010882040B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD070050F202000100

corey@CJ-Satellite-C655D:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency=2.412 GHz (Channel 1)

corey@CJ-Satellite-C655D:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
corey@CJ-Satellite-C655D:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
corey@CJ-Satellite-C655D:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.43.0      0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
corey@CJ-Satellite-C655D:~$ cat /etc/resolv.conf
# Generated by NetworkManager
corey@CJ-Satellite-C655D:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

corey@CJ-Satellite-C655D:~$ 

```



Do you mean to be in ad-hoc mode( usually from computer to computer)? Your earlier listing showed "managed" which is more usual.

If not try

sudo iwconfig wlan0 mode managed

---

### Post by CJJones829 on 2011-09-05
I don't even know man.. like I said, this is all new to me.  I've just been following the instructions.

Since he went to sleep.. would you be able to give me a hand in troubleshooting this?  I'm begging you!

I literally think I've been working on this since 3 or 4 pm today.  Whether it was Google searches or on Twitter.

To sum up.. I installed the OS.. internet worked fine.. then it asked me to install the latest updates.. and I did.  After the restart, the internet hasn't worked since.

Now.. when I start the computer.. my router is the 1st option, I'll click connect, it'll ask for a Password, I'll enter the network key, and then it'll ask for the "keyring password", and then I enter my admin password.  It proceeds to "search" for the connection, and then we just repeat that whole same process again.

It's extremely frustrating, especially because I just got the laptop today and I was so ridiculously excited to get going!

Would you be able to give me a hand?  Please!

---

### Post by CJJones829 on 2011-09-05
> **bkratz said:**
> Do you mean to be in ad-hoc mode( usually from computer to computer)? Your earlier listing showed "managed" which is more usual.

If not try

sudo iwconfig wlan0 mode managed

Typed that in..

Having the same issues.

I actually deleted what you saw up there and re-did it, because the actual router ends with 82, not 28.

---

### Post by nm_geo on 2011-09-05
When you do the - again please

```
sudo iwlist scan
```

Do you see any other wireless access points.

Can you log into your AP (wireless access point) maybe with ethernet cable.

---

### Post by CJJones829 on 2011-09-05
OK.. check this out..

I grabbed our USB wireless adapter and plugged that into the laptop.

Surfed the apps available and found one called Wicd Network Manager and downloaded it.

Restarted the computer (without the USB wireless adapter).. and the internet WORKED!  Without having to type a password in or anything.  It just automatically worked.  I didn't even start the Wicd Network Manager program either, so I guess that was pointless.

Who can explain this?? Kinda crazy!

Thanks again for the help.  Hopefully it keeps on working.

---

### Post by nm_geo on 2011-09-05
Let's go back to the wifi connection area.. Edit connection..password
Below is what mine looks like in pictures. We are not sure what you security requirements are and my ESSID is "gfk"

---

### Post by nm_geo on 2011-09-05
> **CJJones829 said:**
> OK.. check this out..

I grabbed our USB wireless adapter and plugged that into the laptop.

Surfed the apps available and found one called Wicd Network Manager and downloaded it.

Restarted the computer (without the USB wireless adapter).. and the internet WORKED!  Without having to type a password in or anything.  It just automatically worked.  I didn't even start the Wicd Network Manager program either, so I guess that was pointless.

Who can explain this?? Kinda crazy!

Thanks again for the help.  Hopefully it keeps on working.

WOW excellent that ad-hoc is driving me crazy,, oh well good luck

---

### Post by bkratz on 2011-09-06
> **CJJones829 said:**
> OK.. check this out..

I grabbed our USB wireless adapter and plugged that into the laptop.

Surfed the apps available and found one called Wicd Network Manager and downloaded it.

Restarted the computer (without the USB wireless adapter).. and the internet WORKED!  Without having to type a password in or anything.  It just automatically worked.  I didn't even start the Wicd Network Manager program either, so I guess that was pointless.

Who can explain this?? Kinda crazy!


Thanks again for the help.  Hopefully it keeps on working.



Glad to see you figured out a solution! it always feels better  that way.  Enjoy your wireless.

---

### Post by praseodym on 2011-09-06
Hi,

congratulations for your solution. The NetworkManager and Wicd dont work in parallel, you should un-check the network-manager in "Autostart" and:

```
sudo service network-manager stop
sudo service wicd restart
```
If you want to install some templates for different wireless encryption modes you can install an Add-On for Wicd (from one of the developers):


```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service wicd restart
```

---

### Post by CJJones829 on 2011-09-06
Well, everything seems to being OK now with the Network Manager that I was having troubles with initially.  In fact, I just connected wirelessly here at work in our lunch room with no problem.

I'm pretty pumped!  Hopefully everything goes well when I get home.  If not, I'll definitely check back here.

I was really discouraged at first, as this is my first attempt to use Ubuntu and with a brand new laptop at that (literally just got it yesterday morning).

But you guys are awesome.. I can't wait to continue to tinker around and find out new things.  I feel like I'm also learning more about computers.

Thanks again for all of your help!

---

### Post by nm_geo on 2011-09-06
> **CJJones829 said:**
> Well, everything seems to being OK now with the Network Manager that I was having troubles with initially.  In fact, I just connected wirelessly here at work in our lunch room with no problem.

I'm pretty pumped!  Hopefully everything goes well when I get home.  If not, I'll definitely check back here.

I was really discouraged at first, as this is my first attempt to use Ubuntu and with a brand new laptop at that (literally just got it yesterday morning).

But you guys are awesome.. I can't wait to continue to tinker around and find out new things.  I feel like I'm also learning more about computers.

Thanks again for all of your help!
  In Thread tools mark it Solved please

---

### Post by praseodym on 2011-09-06
I would prefer Wicd with the Add-On if you often use public networks, because these normally use WEP or mixed WPA/WPA2-encryption. Wicd makes less/no problems with that.

---

