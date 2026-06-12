---
title: "Netgear WNA3100 issues"
date: 2012-04-26
forum: Networking &amp; Wireless
---

### Post by mathsgeek on 2012-04-26
Hi, I'm having issues getting my Netgear WNA3100 to connect to the web. I have tried every method described on these forums and none work. Can anyone help troubleshoot my problems? I'm running 12.04 64 bit. When I run lsusb I get (only listing relevant entries):
```

...
Bus 001 Device 003 : ID 0846:9020 Netgear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231

...
```And iwconfig gives:
```

lo   no wireless extensions

etho     no wireless extensions

```I am getting access to the internet via my laptop and another wireless stick (which cannot be permanent).

Any help will be much appreciated.

---

### Post by chili555 on 2012-04-26
Did you try the driver files attached? Please let me know if you need assistance removing the defective files and installing these.

---

### Post by mathsgeek on 2012-04-26
Yeah, I've tried your drivers chili555, the stick still doesn't work. :( I followed the instruction for those drivers that were on the last page of the thread you posted them on: [http://ubuntuforums.org/showthread.php?t=1946875](http://ubuntuforums.org/showthread.php?t=1946875) and the ubuntu wiki page on getting ndiswrapper to work. If you can help I would be most grateful.

---

### Post by chili555 on 2012-04-26
Would you please round up the usual suspects?```
sudo modprobe ndiswrapper
ndiswrapper -l
dmesg | grep ndis
```Thanks.

---

### Post by hopeless8009 on 2012-04-27
im am also having problems with same set up only I'm running 32bit. the Netgear card and 12.04 LTS are the same

---

### Post by chili555 on 2012-04-27
> **hopeless8009 said:**
> im am also having problems with same set up only I'm running 32bit. the Netgear card and 12.04 LTS are the samePlease see post #4.

---

### Post by mathsgeek on 2012-04-27
sudo modprobe ndiswrapper returns (My brother is a relatively good with ubuntu and was playing with the blacklist):
```

WARNING: All config files need .conf : /etc/modprobe.d/blacklist, it will be ignored in a future release.

```ndiswrapper -l gives:
```

WARNING: All config files need .conf : /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwlhigh5 : driver installed
     device (0846:9020) present

```dmesg | grep ndis outputs
```

[     9.436697] ndiswrapper version 1.57 loaded (smp=yes) (preempt=no)
[    11.105885] ndiswrapper (check_nt_hdr:141): kernel is 64 bit, but Windows driver is not 64 bit;bad magic: 010B
[    11.105889] ndiswrapper (load_sys_files:199): couldn't load driver 'bcmwlhigh5'
[    11.105960] ndiswrapper (load_wrap_driver:121): couldn't load driver 'bcmwlhigh5'
[    11.106027] usbcore: registered new interface driver ndiswrapper

```Does this help?

Would I be right in thinking it isn't working because your drivers are not 64bit?

---

### Post by chili555 on 2012-04-27
> Would I be right in thinking it isn't working because your drivers are not 64bit?Sort of. Here is a snip from the .inf file:> ;-----------------------------------------------------------------
; x64 (AMD64, Intel EM64T) - WinXP
;
[BROADCOM.NT[COLOR="Red"]amd64[/COLOR]]
        %BCM430ND_DeviceDesc% = BCM43XNMD, USB\VID_[COLOR="Red"]0846[/COLOR]&PID_[COLOR="Red"]9020[/COLOR]

As you can see, it references your device and clearly is a 64-bit .inf file. I suspect what happened is that the 32-bit .cat file is in the same folder as the .inf. I think ndiswrapper grabbed it instead of the 64-bit .cat file. Let's see if we can fix it. Go to the folder you extracted and look for and delete bcmh43xx.cat leaving only bcmh43xx64.cat. Now we erase the old install:```
sudo ndiswrapper -e bcmwlhigh5
```And let's do some housekeeping:```
sudo rm -rf /etc/ndiswrapper/*
```Now, let's clean this up:> WARNING: All config files need .conf : /etc/modprobe.d/blacklist, it will be ignored in a future release.Let's see what your brother blacklisted:```
cat /etc/modprobe.d/blacklist
```Whatever is in there is either not needed, in which case we can delete the file altogether; or it should be added to /etc/modprobe.d/blacklist.conf, a file that already exists on your system. Then the blacklist (not conf) can be deleted. If you are in doubt, post the result here.

Now let's try again:```
cd Desktop/wna3100-drivers  <--or wherever you extracted them
sudo modprobe -r ndiswrapper
sudo ndiswrapper -i bcmlhigh5.inf
sudo modprobe ndiswrapper
dmesg | grep ndis
```Now at a later timestamp than here: [    [COLOR="Red"]11.105960[/COLOR]] ndiswrapper (load_wrap_driver:121): couldn't load driver 'bcmwlhigh5', did we get rid of the bad magic?

---

### Post by mathsgeek on 2012-04-27
catting the blacklist gives:
```

blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb

```

Unfortunately we haven't got rid of the bad magic... :(

---

### Post by chili555 on 2012-04-27
None of those blacklists add or detract from your case. I suggest you remove the file altogether:```
sudo rm /etc/modprobe.d/blacklist
```Please delete the bcmwlhigh5 as above and try these files. You will be installing bcmn43xx64.inf.

As you have seen, this device on 64-bit is quite tricky.

---

### Post by mathsgeek on 2012-04-27
Right, installed new drivers. I did get and error whilst installing: 
```

couldn't find SourceDiskFiles section - continuing anyway
...

```Is this an error my end or with the drivers or ndiswrapper?
I am still getting nothing under iwconfig.
Are there any other commands I need to run other than ```
ndiswrapper -i driver.inf
```?

---

### Post by chili555 on 2012-04-27
It's a big finger-pointing conflict between ndiswrapper and Broadcom. I don't believe the comes-on-the-disc .inf file works with 64-bit. Some enterprising person emailed Broadcom and they sent along bcmn43xx64.inf and the accessory .cat and .sys files tweaked for ndiswrapper. The trouble is, in many cases, that doesn't work either!

I noticed it said 'continuing anyway.' Any useful clues in here:```
dmesg | grep ndis
```

---

### Post by mathsgeek on 2012-04-27
I get:
```

[    11.488405] ndiswrapper version 1.57 loaded (smp=yes) (preempt=no) 
[    14.245972] ndiswrapper (check_nt_hdr:141): kernel is 64 bit, but Windows driver is not 64 bit;bad magic: 010B 
[    14.245977] ndiswrapper (load_sys_files:199): couldn't load driver 'bcmwlhigh5' 
[    14.246054] ndiswrapper (load_wrap_driver:121): couldn't load driver 'bcmwlhigh5' 
[    14.246153] usbcore: registered new interface driver ndiswrapper

```

---

### Post by chili555 on 2012-04-27
My friend, I have been working on this for hours, both for you and other clients. I'm sure a Google search for WNA3100 and 64-bit will find dozens of my threads. I am not able to find any *working* 64-bit install. I am not sure it's even possible.  

You could reinstall a 32-bit system and I'm very confident it will work perfectly. You could buy a different device. I don't really have any other answer for you.

---

### Post by michael495 on 2012-04-28
Wait i have the same problem and i was wondering if u could give me full instructions.:confused:

---

### Post by chili555 on 2012-04-28
> **michael495 said:**
> Wait i have the same problem and i was wondering if u could give me full instructions.:confused:Did you read my post above?> I'm sure a Google search for WNA3100 and 64-bit will find dozens of my threads. I am not able to find any working 64-bit install. ***I am not sure it's even possible.***


---

### Post by ghoulnet on 2012-04-28
Using the following I was able to get my netgear WNA3100 to show up: [http://forums.linuxmint.com/viewtopic.php?f=42&t=97610](http://forums.linuxmint.com/viewtopic.php?f=42&t=97610)

> 

root@desktop:/home/edward/Downloads# lsusb | grep NetGear
Bus 001 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]


root@desktop:/home/edward/Downloads# iwconfig 
lo        no wireless extensions.

wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




This is on a 64bit AMD machine:

> root@desktop:/home/edward/Downloads# uname -a
Linux desktop 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


I am however struggling to get it to connect to a network that uses WPA/WPA2, it just kicks out the password which I know is right as my Ralink dongle can connect. If I disable security on the router it can connect though. This has me stumped right now, anyone come across that problem before?

---

### Post by ghoulnet on 2012-04-28
Fixed the password problem, well at least I know that it's caused by using N, switched my router to just use b/g and it's now allowing my adapter to connect :)

I've also upgraded the version of ndiswrapper mentioned in that post on linuxmint to 1.9 and made it so modprobe kicks the fob into action on bootup by adding ndiswrapper to /etc/modules :)

Now to find a fix for the N Protocol and i'll be happy :)

---

### Post by mathsgeek on 2012-04-29
Quick question, will running 32 bit allow me to utilise the most of 3Gb of RAM? If so I will do a 32bit re-install

Thanks for all your help and time, Chilli555, I am most grateful for your help with this matter.

:)

---

### Post by chili555 on 2012-04-29
> **mathsgeek said:**
> Quick question, will running 32 bit allow me to utilise the most of 3Gb of RAM? If so I will do a 32bit re-install

Thanks for all your help and time, Chilli555, I am most grateful for your help with this matter.

:)Absolutely, with a PAE kernel. Here is mine:> chili@LAPTOP60:~$ uname -r
3.2.0-24-generic-[COLOR="Red"]pae[/COLOR]
chili@LAPTOP60:~$ arch
[COLOR="Red"]i686[/COLOR]
chili@LAPTOP60:~$ free
             total       used       free     shared    buffers     cached
[COLOR="Red"]Mem:       3914368[/COLOR]    1045580    2868788          0     107972     540948
-/+ buffers/cache:     396660    3517708
Swap:      6914044          0    6914044The install ought to install a PAE kernel by default, but, if not, you can install it from Synaptic immediately.

I am happy to help. I look forward to our next steps.

---

### Post by mathsgeek on 2012-04-29
I've got the 32bit install done. Which set of drivers will I need? And what commands, the same as above?

---

### Post by mathsgeek on 2012-04-29
Used the drivers and commands above and the output from dmesg | grep ndis gives (different from normal :)):
```

[ 2441.475863] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[ 2441.731994] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
[ 2441.756268] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[ 2441.756273] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[ 2441.756280] ndiswrapper (mp_halt:254): device f094a480 is not initialized - not halting
[ 2441.756283] ndiswrapper: device eth%d removed
[ 2441.756344] ndiswrapper: probe of 1-4:1.0 failed with error -22
[ 2441.756384] usbcore: registered new interface driver ndiswrapper

```

---

### Post by chili555 on 2012-04-29
Not the set from which you removed the 32-bit cat and sys files, I hope.

Try this.

---

### Post by mathsgeek on 2012-04-30
No, no, not the ones I removed the 32bit cat from. :)
I will try those now.

---

### Post by mathsgeek on 2012-04-30
Good news, :D the stick can now connect to the internet but I'm getting the issue of not being able to connect to my password protected homehub and I can't unencrypt my homehub.
Do you know of a way of getting connected?

---

### Post by chili555 on 2012-04-30
I don't understand. How can you get to the internet but not the Homehub? Is the encryption set to WPA2 only or the dreaded mixed mode WPA and WPA2? Can you change it to WPA2 only?

Good news indeed!

---

### Post by mathsgeek on 2012-04-30
Well..I assume it can connect to the internet as it shows stuff under network manager but I don't know as my homehub is WPA2(I think) and yes I have put the key in right. How can I check what encryption key type my homehub is using?

---

### Post by chili555 on 2012-04-30
> How can I check what encryption key type my homehub is using?I assume you'd need to log on to the Homehub from another, ideally ethernet machine and look around in its settings.> as my homehub is WPA2(I think) What does scan tell us?```
sudo iwlist wlan0 scan
```Here is a snipped result from mixed mode WPA and WPA2:> Cell 02 - Address: 1C:AF:F7:16:A1:80
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Semenenko"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master                    
                        IE: [COLOR="Red"]WPA Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/[COLOR="Red"]WPA2 Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSKHere is mine:> Cell 01 - Address: XX:13:10:62:8D:XX
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                        IE: IEEE 802.11i/[COLOR="Red"]WPA2 Version 1[/COLOR]
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
I don't know if it's wpa_supplicant or Network Manager that has trouble, but many connection issues have been resolved with WPA2 only.

---

### Post by mathsgeek on 2012-04-30
sudo iwlist wlan0 scan gives:
```

 Address: 00:25:56:0A:35:4A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"BTHomeHub2-KQT2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a27b4ba6c
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 000F4254486F6D65487562322D4B515432
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00

```I'm guessing this means my homehub is WPA/WPA2 combination. So how do I change the setting?

---

### Post by chili555 on 2012-04-30
You log on the the administration pages of the Homehub and change it. Please see attached. Even thought the title is 'WEP shared,' you can see in the drop-down that there is an option for WPA, WPA2 or mixed WPA and WPA2 encryption. You will likely have the best luck with WPA2 *only*.

Obviously, this is not from a BT Homehub, but the concept is the same. We are not blessed/cursed with BT here in South Carolina.

---

### Post by mathsgeek on 2012-04-30
Sorry to be thick but how do I get to those pages? I have never seen anything like those before.

---

### Post by chili555 on 2012-04-30
The gateway address is usually something like 192.168.x.y. You can find it in ipconfig /a on any Windows machine. You should be able to log in the Homehub using that number in Firefox: [http://192.168.1.1](http://192.168.1.1) or whatever the number is.

I hope BT doesn't have all those settings locked out from the consumer who is *paying the monthly charges and therefor their very salaries!!!* I hope you don't need to call them.

Off to an appointment. See you later.

---

### Post by mathsgeek on 2012-04-30
See you, enjoy your appointment, found the page. :) it was bthomehub.home/
Do I want WEP as that is the only other option to WPA2&WPA mix?

---

### Post by mathsgeek on 2012-04-30
Here is a screenshot of the options

---

### Post by chili555 on 2012-04-30
> Do I want WEP as that is the only other option to WPA2&WPA mix?No; WEP is about as secure as a shoebox on the front porch. It looks like we'll have to try to approach it another way. Just verify that the key you are using is correct and try to connect. Then let's see what syslog has to say:```
sudo cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
```Thanks.

---

### Post by mathsgeek on 2012-04-30
The output from the cat command is this:
```

Apr 30 18:48:25 james-desktop NetworkManager[846]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Apr 30 18:48:25 james-desktop NetworkManager[846]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 30 18:48:25 james-desktop NetworkManager[846]: <info> Activation (wlan1/wireless): connection 'BTHomeHub2-KQT2 1' has security, and secrets exist.  No new secrets needed.
Apr 30 18:48:25 james-desktop NetworkManager[846]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Apr 30 18:48:26 james-desktop NetworkManager[846]: <info> (wlan1): supplicant interface state: disconnected -> scanning
Apr 30 18:48:31 james-desktop NetworkManager[846]: <info> (wlan1): supplicant interface state: scanning -> associating
Apr 30 18:48:31 james-desktop NetworkManager[846]: <info> (wlan1): supplicant interface state: associating -> associated
Apr 30 18:48:31 james-desktop NetworkManager[846]: <info> (wlan1): supplicant interface state: associated -> 4-way handshake
Apr 30 18:48:41 james-desktop NetworkManager[846]: <info> (wlan1): supplicant interface state: 4-way handshake -> disconnected
Apr 30 18:48:46 james-desktop NetworkManager[846]: <info> (wlan1): supplicant interface state: disconnected -> associating
Apr 30 18:48:47 james-desktop NetworkManager[846]: <info> (wlan1): supplicant interface state: associating -> associated
Apr 30 18:48:47 james-desktop NetworkManager[846]: <info> (wlan1): supplicant interface state: associated -> 4-way handshake
Apr 30 18:48:57 james-desktop NetworkManager[846]: <info> (wlan1): supplicant interface state: 4-way handshake -> disconnected
Apr 30 18:49:02 james-desktop NetworkManager[846]: <info> (wlan1): supplicant interface state: disconnected -> associating
Apr 30 18:49:03 james-desktop NetworkManager[846]: <info> (wlan1): supplicant interface state: associating -> associated
Apr 30 18:49:03 james-desktop NetworkManager[846]: <info> (wlan1): supplicant interface state: associated -> 4-way handshake
Apr 30 18:49:13 james-desktop NetworkManager[846]: <info> (wlan1): supplicant interface state: 4-way handshake -> disconnected
Apr 30 18:49:18 james-desktop NetworkManager[846]: <info> (wlan1): supplicant interface state: disconnected -> associating
Apr 30 18:49:19 james-desktop NetworkManager[846]: <info> (wlan1): supplicant interface state: associating -> associated
Apr 30 18:49:19 james-desktop NetworkManager[846]: <info> (wlan1): supplicant interface state: associated -> 4-way handshake

```

I'm afraid there is quite a lot there.

---

### Post by chili555 on 2012-04-30
While I Google and scratch my gray beard, please run and post:```
dmesg | grep -e wlan -e ndis
```Thanks.

---

### Post by mathsgeek on 2012-04-30
Here it is:
```

[   11.538189] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.538772] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.970358] wlan0: authenticate with 00:25:56:0a:35:4a (try 1)
[   14.972742] wlan0: authenticated
[   15.030854] wlan0: associate with 00:25:56:0a:35:4a (try 1)
[   15.036020] wlan0: RX AssocResp from 00:25:56:0a:35:4a (capab=0x411 status=0 aid=2)
[   15.036024] wlan0: associated
[   15.047644] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   25.952008] wlan0: no IPv6 routers present
[  102.076314] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[  102.393129] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
[  102.682507] wlan1: ethernet device e0:46:9a:a2:91:ea using NDIS driver: bcmwlhigh5, version: 0x53cb40b, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
[  102.687010] wlan1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[  102.691604] usbcore: registered new interface driver ndiswrapper
[  102.696074] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  102.696363] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  102.698260] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  113.759112] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  183.718254] wlan0: deauthenticating from 00:25:56:0a:35:4a by local choice (reason=3)
[  189.479887] wlan0: authenticate with 00:25:56:0a:35:4a (try 1)
[  189.481686] wlan0: authenticated
[  189.503988] wlan0: associate with 00:25:56:0a:35:4a (try 1)
[  189.507623] wlan0: RX ReassocResp from 00:25:56:0a:35:4a (capab=0x411 status=0 aid=2)
[  189.507627] wlan0: associated
[  200.672017] wlan0: no IPv6 routers present
[ 1913.282825] wlan0: deauthenticating from 00:25:56:0a:35:4a by local choice (reason=3)
[ 1949.619723] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1949.620314] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1951.684606] ndiswrapper: device wlan1 removed
[ 1953.071391] wlan0: authenticate with 00:25:56:0a:35:4a (try 1)
[ 1953.074033] wlan0: authenticated
[ 1953.129264] wlan0: associate with 00:25:56:0a:35:4a (try 1)
[ 1953.132524] wlan0: RX AssocResp from 00:25:56:0a:35:4a (capab=0x411 status=0 aid=2)
[ 1953.132528] wlan0: associated
[ 1953.144710] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1963.376008] wlan0: no IPv6 routers present
[ 6246.484014] ieee80211 phy1: wlan0: No probe response from AP 00:25:56:0a:35:4a after 500ms, disconnecting.
[ 6262.590833] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6297.960863] wlan0: authenticate with 00:25:56:0a:35:4a (try 1)
[ 6297.962994] wlan0: authenticated
[ 6298.018487] wlan0: associate with 00:25:56:0a:35:4a (try 1)
[ 6298.021623] wlan0: RX ReassocResp from 00:25:56:0a:35:4a (capab=0x411 status=0 aid=1)
[ 6298.021627] wlan0: associated
[ 6298.033795] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6309.072005] wlan0: no IPv6 routers present
[ 6819.639364] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
[ 6820.226247] wlan1: ethernet device e0:46:9a:a2:91:ea using NDIS driver: bcmwlhigh5, version: 0x53cb40b, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
[ 6820.229389] wlan1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[ 6820.246589] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 6820.246917] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 6820.250136] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 6831.820571] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 7995.168868] wlan0: deauthenticating from 00:25:56:0a:35:4a by local choice (reason=3)
[19377.531150] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[19377.531547] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[19380.876458] wlan0: authenticate with 00:25:56:0a:35:4a (try 1)
[19380.879372] wlan0: authenticated
[19380.937583] wlan0: associate with 00:25:56:0a:35:4a (try 1)
[19380.940845] wlan0: RX AssocResp from 00:25:56:0a:35:4a (capab=0x411 status=0 aid=1)
[19380.940849] wlan0: associated
[19380.952638] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[19391.456010] wlan0: no IPv6 routers present
[19930.973631] wlan0: deauthenticating from 00:25:56:0a:35:4a by local choice (reason=3)
[21521.819280] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[21521.819703] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[21525.159835] wlan0: authenticate with 00:25:56:0a:35:4a (try 1)
[21525.207099] wlan0: authenticated
[21525.263830] wlan0: associate with 00:25:56:0a:35:4a (try 1)
[21525.266721] wlan0: RX AssocResp from 00:25:56:0a:35:4a (capab=0x411 status=0 aid=2)
[21525.266724] wlan0: associated
[21525.278515] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[21536.160009] wlan0: no IPv6 routers present

```

Hope this helps you stroke your grey beard. :P

---

### Post by chili555 on 2012-04-30
Is power management on or off?```
iwconfig
```> wlan0     IEEE 802.11abg  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:13:10:62:8D:xx  
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          [COLOR="Red"]Power Management:off[/COLOR]
          Link Quality=50/70  Signal level=-60 dBm  


---

### Post by mathsgeek on 2012-04-30
Nah, power management is off.

---

### Post by ghoulnet on 2012-04-30
Try making it so your bt home hub only uses the wireless protocols b/g.

I have the home hub and when using the n protocol it won't accept the password.

Haven't tried to work out why yet, good luck!

---

### Post by chili555 on 2012-04-30
> Try making it so your bt home hub only uses the wireless protocols b/g.Please do so, mathsgeek. Is there then any improvement?

---

### Post by mathsgeek on 2012-04-30
How do you do that? Sorry I am a complete noob at networking. :)

---

### Post by ghoulnet on 2012-04-30
Log on to the hub, select settings -> advanced settings -> wireless -> wireless interface type.

---

### Post by chili555 on 2012-04-30
> **ghoulnet said:**
> Log on to the hub, select settings -> advanced settings -> wireless -> wireless interface type.Although I don't have a Homehub, I suspect you can set it for 802.11B and G or else, B, G and N. We think you will connect easier with B and G only; *no N*.

---

### Post by mathsgeek on 2012-05-01
Thank you guys!! It works. :D You guys are great, btw this is posted with only the netgear wna3100 stick.

Thank you so much for your valuable time as I am incredibly greatful for the web connection. Right, only my graphics card to sort out, bloomin' NVDIA :(

---

### Post by chili555 on 2012-05-01
Was this what did it?> Try making it so your bt home hub only uses the wireless protocols b/g.Inquiring minds, including the searchers, want to know.

I was glad to help.I learned a lot.

---

### Post by mathsgeek on 2012-05-01
Yeah, changing the protocol from b/g/n to b/g did it. :)
For those who want to know the exact button, there is a screenshot attached.

---

### Post by chili555 on 2012-05-01
Thank you. I'm pretty confident that you've helped quite a few searchers. Have fun!

---

### Post by ramsesra200 on 2012-05-03
[http://www.youtube.com/watch?v=ZMYBWMD6cg8&feature=youtu.be](http://www.youtube.com/watch?v=ZMYBWMD6cg8&feature=youtu.be)

---

### Post by Oasix on 2012-07-10
Hi guys,

thank you so much for your help.
[B]I was able to install 64bit driver on Ubuntu 12.04 64bit
[/B]
I downloaded the driver from the link below and followed your instructions
[http://forums.linuxmint.com/viewtopic.php?f=42&t=97610](http://forums.linuxmint.com/viewtopic.php?f=42&t=97610)

Thanks again
Ciao :popcorn:

---

### Post by mathsgeek on 2012-08-22
Oasix, you have internet with your 64bit system now?
Thats pretty remarkable, well done on getting it to work. :D

---

### Post by mathsgeek on 2012-08-27
[LEFT]I know I probably shouldn't ask a further question on this thread, but I have a new kernel  and when I run ```
sudo modprobe ndiswrapper
``` to connect to the net it says ```
FATAL: Module ndiswrapper not found.
``` now with some of the older kernels I could just copy the ndiswrapper.ko file from the directory and put it in the corresponding place in the new kernel i.e. /lib/modules/KERNEL_NAME/misc/ndiswrapper.ko and it would work....But with the newer kernels it doesn't work. Is there a way to get modprobe to find ndiswrapper?
[/LEFT]

---

### Post by chili555 on 2012-08-27
> **mathsgeek said:**
> [LEFT]I know I probably shouldn't ask a further question on this thread, but I have a new kernel  and when I run ```
sudo modprobe ndiswrapper
``` to connect to the net it says ```
FATAL: Module ndiswrapper not found.
``` now with some of the older kernels I could just copy the ndiswrapper.ko file from the directory and put it in the corresponding place in the new kernel i.e. /lib/modules/KERNEL_NAME/misc/ndiswrapper.ko and it would work....But with the newer kernels it doesn't work. Is there a way to get modprobe to find ndiswrapper?
[/LEFT]Please do:```
sudo apt-get install ndiswrapper-dkms
sudo modprobe ndiswrapper
```Any improvement?

---

### Post by mathsgeek on 2012-08-27
Recently, I upgraded to quantal quetzal, for the improved graphics drivers, after being told it was relatively stable.
However, when I try to install ndiswrapper-dkms I get a compiler error: ```
/var/lib/dkms/ndiswrapper/1.57/build/ndis.c:2657:24: error: 'struct kernel_stat' has no member named 'cpustat' 
```
Should I build ndiswrapper-dkms from source?

---

### Post by chili555 on 2012-08-27
> **mathsgeek said:**
> Recently, I upgraded to quantal quetzal, for the improved graphics drivers, after being told it was relatively stable.
However, when I try to install ndiswrapper-dkms I get a compiler error: ```
/var/lib/dkms/ndiswrapper/1.57/build/ndis.c:2657:24: error: 'struct kernel_stat' has no member named 'cpustat' 
```
Should I build ndiswrapper-dkms from source?I don't believe ndiswrapper is yet optimized for 12.10. So yes; build from source. If you need assistance, please post back.

---

### Post by mathsgeek on 2012-08-27
Hi,
After some googling, I discovered that to build ndiswrapper-dkms from source is equivalent to building ndiswrapper from source, however I get teh same error as last time: ```
 error: 'struct kernel_stat' has no member named 'cpustat' 
```What should I do to circumvent this issue?

---

### Post by chili555 on 2012-08-27
> **mathsgeek said:**
> Hi,
After some googling, I discovered that to build ndiswrapper-dkms from source is equivalent to building ndiswrapper from source, however I get teh same error as last time: ```
 error: 'struct kernel_stat' has no member named 'cpustat' 
```What should I do to circumvent this issue?Nothing, probably. I get:> /home/chili/ndiswrapper-1.57/driver/ndis.c: In function ‘NdisGetCurrentProcessorCounts’:
/home/chili/ndiswrapper-1.57/driver/ndis.c:2657:24: error: ‘struct kernel_stat’ has no member named ‘cpustat’
/home/chili/ndiswrapper-1.57/driver/ndis.c:2658:31: error: ‘struct kernel_stat’ has no member named ‘cpustat’
/home/chili/ndiswrapper-1.57/driver/ndis.c:2659:17: error: ‘struct kernel_stat’ has no member named ‘cpustat’
make[3]: *** [/home/chili/ndiswrapper-1.57/driver/ndis.o] Error 1And I Google: [https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1023645](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1023645)

You'll probably have better luck with ndiswrapper-1.58rc1. It 'makes' for me without error or warning on kernel 3.4.0-030400-generic-pae.

---

### Post by mathsgeek on 2012-08-27
Thanks, 1.58rc1 now builds and I have installed it, and even better ```
sudo modprobe ndiswrapper
``` doesn't throw any errors and I can now connect to the net... Thanks very much again for getting my 'stick sorted....

---

### Post by chili555 on 2012-08-27
Awesome! Glad it's working. You will have helped some searchers, too.

---

### Post by tahdas on 2012-12-29
Do I need Internet to install it?

---

### Post by chili555 on 2012-12-30
It will certainly be a lot easier, but you can, with hard work and determination, download the packages on another computer and transfer them on a USB drive.

---

### Post by tahdas on 2013-01-02
Wait is there something i can just download and the Netgear thing will work? Or do i still have to do all this stuff in the terminal? 
My computer is dual boot so i can get internet on the vista half. Do i need internet in the ubuntu to half to get the netgear to work?

The installation guide im using is this: [http://forums.linuxmint.com/viewtopic.php?f=197&t=92044](http://forums.linuxmint.com/viewtopic.php?f=197&t=92044)
It was the easiest to understand but im not sure what the download links on the bottom are for.

Thanks so much for your help! I dont what i would do without you!

---

### Post by chili555 on 2013-01-02
> **tahdas said:**
> Wait is there something i can just download and the Netgear thing will work? Or do i still have to do all this stuff in the terminal? 
My computer is dual boot so i can get internet on the vista half. Do i need internet in the ubuntu to half to get the netgear to work?

The installation guide im using is this: [http://forums.linuxmint.com/viewtopic.php?f=197&t=92044](http://forums.linuxmint.com/viewtopic.php?f=197&t=92044)
It was the easiest to understand but im not sure what the download links on the bottom are for.

Thanks so much for your help! I dont what i would do without you!The link you provided is pretty stale in Ubuntu years. Depending on your Ubuntu version, those instructions may not work. If you have the install CD, it may be easier. There is no single package you can just download and install. You probably can not install this wiithout at least a few terminal steps. I wish the answer was different, but it just isn't.

Do you have the install CD? If so, drop the CD in the tray and navigate to pool > main > n > ndiswrapper and drag and drop both ndiswrapper-common and ndiswrapper-utils to your desktop. Then right-click them each and select 'Open with Software Center' (or whatever the package installer is in your Ubuntu version) and install them both.

Now it depends on your Ubuntu version and exact device. Please reluctantly open a terminal and run and post:```
lsb_release -d
arch
lsusb
```We'll figure out a strategy once we know your exact details.

---

### Post by tahdas on 2013-01-02
By install cd you mean the cd that came with the wireless adapter?
I typed in your code: 

tahdas@tahdas:~$ lsb_release -d 
Description:	Ubuntu 12.10 
tahdas@tahdas:~$ 
tahdas@tahdas:~$ lsb_release -d 
Description:	Ubuntu 12.10 
tahdas@tahdas:~$ arch 
i686 
tahdas@tahdas:~$ lsusb 
Bus 002 Device 002: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231] 
Bus 004 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 


Thanks!
tahdas

---

### Post by chili555 on 2013-01-02
> By install cd you mean the cd that came with the wireless adapter?By install CD, I meant the CD you used to install Ubuntu. Do you have it and can you get the ndiswrapper pieces installed as above?

You have a 32-bit system and need the files I attached. Download the file to your desktop and right-click it and select Extract Here. Now open the terminal and do:```
cd Desktop/wna3100-drivers
sudo ndiswrapper -i bcmwlhigh5
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```Your wireless device should now be working.

If there is any error, please post back and we'll be glad to help.

---

### Post by tahdas on 2013-01-02
I used a USB drive to install Ubuntu, I deleted Ubuntu off the USB drive afterwards. Do I need to put Ubuntu back onto the USB drive?

Thanks again!
Tahdas

---

### Post by chili555 on 2013-01-03
No, that would have been a quick and easy way to get the ndiswrapper packages. Let's go here: [http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=quantal&section=all](http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=quantal&section=all)

Download the i386 versions of ndiswrapper-common and ndiswrapper-utils. Transfer them on the USB key to the desktop of your Ubuntu machine. Then open the terminal and do:```
sudo dpkg -i Desktop/ndis*.deb
cd Desktop/wna3100-drivers
sudo ndiswrapper -i bcmwlhigh5
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```I have my fingers and toes crossed.

---

### Post by tahdas on 2013-01-03
tahdas@tahdas:~$ sudo dpkg -i Desktop/ndis*.deb; 
[sudo] password for tahdas: 
2Sorry, try again. 
[sudo] password for tahdas: 
Selecting previously unselected package ndiswrapper-source. 
(Reading database ... 155054 files and directories currently installed.) 
Unpacking ndiswrapper-source (from .../ndiswrapper-source_1.57-1ubuntu1_all.deb) ... 
dpkg: dependency problems prevent configuration of ndiswrapper-source: 
 ndiswrapper-source depends on module-assistant; however: 
  Package module-assistant is not installed. 
 ndiswrapper-source depends on debhelper (>= 5); however: 
  Package debhelper is not installed. 

dpkg: error processing ndiswrapper-source (--install): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 ndiswrapper-source 
tahdas@tahdas:~$ cd Desktop/wna3100-drivers 
tahdas@tahdas:~/Desktop/wna3100-drivers$ sudo ndiswrapper -i bcmwlhigh5 
sudo: ndiswrapper: command not found 
tahdas@tahdas:~/Desktop/wna3100-drivers$ 

Did i do something wrong? 

Thanks,
tahdas

---

### Post by chili555 on 2013-01-03
> dpkg: dependency problems prevent configuration of ndiswrapper-source:
ndiswrapper-source depends on module-assistant; however:
[COLOR="Red"]Package module-assistant is not installed.[/COLOR]
ndiswrapper-source depends on debhelper (>= 5); however:
[COLOR="Red"]Package debhelper is not installed.[/COLOR] Let's go get them: [http://packages.ubuntu.com/quantal/debhelper](http://packages.ubuntu.com/quantal/debhelper)

[http://packages.ubuntu.com/quantal/module-assistant](http://packages.ubuntu.com/quantal/module-assistant)

Follow the same process as above, but install with:```
sudo dpkg -i ~/Desktop/*.deb
```The wildcard * means install *all* the deb packages, including the ndis parts.

---

### Post by tahdas on 2013-01-03
I think I downloaded the wrong thing, because when I type in the code it tells me something like the file archive you requested does not exist.

I'm sorry I'm so bad at this. Could I put Ubuntu back on the USB drve and reinstall Ubuntu then do thing you suggested or does that only work with disks?

Thanks so much!

Edit here is what it said: tahdas@tahdas:~$ sudo dpkg -i ~/Desktop/*.deb 
[sudo] password for tahdas: 
dpkg: error processing /home/tahdas/Desktop/*.deb (--install): 
 cannot access archive: No such file or directory 
Errors were encountered while processing: 
 /home/tahdas/Desktop/*.deb

---

### Post by tahdas on 2013-01-04
Maybe you could just give me a link to another Wifi Usb adapter thats easier to install and i can buy it and Ubuntu will be usable for me.

---

### Post by chili555 on 2013-01-05
> **tahdas said:**
> 
dpkg: error processing /home/tahdas/Desktop/*.deb (--install): 
 cannot access archive: No such file or directory 
Errors were encountered while processing: 
 /home/tahdas/Desktop/*.debSorry for my tardy reply. Let's go about this another way. ```
cd Desktop && ls
```Do you see the files in the listing; ndiswrapper-common, ndiswrapper-utils, debhelper and module-assistant? If so,let's try installing them one at a time:```
sudo dpkg -i debhelper*.deb
sudo dpkg -i module-assistant*.deb
sudo dpkg -i ndiswrapper*.deb
```Then proceed:```
cd wna3100-drivers
sudo ndiswrapper -i bcmwlhigh5
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```> Maybe you could just give me a link to another Wifi Usb adapter thats easier to install and i can buy it and Ubuntu will be usable for me.There are many threads on this forum that ask and answer the same question.

---

### Post by tahdas on 2013-01-06
tahdas@tahdas:~$ sudo dpkg -i ~/Desktop/*.deb 
[sudo] password for tahdas: 
dpkg: error processing /home/tahdas/Desktop/*.deb (--install): 
 cannot access archive: No such file or directory 
Errors were encountered while processing: 
 /home/tahdas/Desktop/*.deb 

It said that for every command. I think i'll just buy another usb adapter that works easily with ubuntu. 

Thanks so much for your help!

---

### Post by chili555 on 2013-01-06
That's not what I requested, please show me:```
cd Desktop && ls
sudo dpkg -i debhelper*.deb
sudo dpkg -i module-assistant*.deb
sudo dpkg -i ndiswrapper*.deb
```I want to see it.

---

### Post by tahdas on 2013-01-06
tahdas@tahdas:~$ cd Desktop && ls 
debhelper_9.20120608ubuntu1_all.deb.lnk 
module-assistant_0.11.4_all.deb.lnk
ndiswrapper-source_1.57-1ubuntu1_all.deb 
ndiswrapper-source_1.57-1ubuntu1_all.deb.lnk 
wna3100-drivers 
tahdas@tahdas:~/Desktop$ sudo dpkg -i debhelper*.deb 
[sudo] password for tahdas: 
dpkg: error processing debhelper*.deb (--install): 
 cannot access archive: No such file or directory 
Errors were encountered while processing: 
 debhelper*.deb 
tahdas@tahdas:~/Desktop$ sudo dpkg -i module-assistant*.deb 
dpkg: error processing module-assistant*.deb (--install): 
 cannot access archive: No such file or directory 
Errors were encountered while processing: 
 module-assistant*.deb 
tahdas@tahdas:~/Desktop$ sudo dpkg -i ndiswrapper*.deb 
(Reading database ... 155060 files and directories currently installed.) 
Preparing to replace ndiswrapper-source 1.57-1ubuntu1 (using ndiswrapper-source_1.57-1ubuntu1_all.deb) ... 
Unpacking replacement ndiswrapper-source ... 
dpkg: dependency problems prevent configuration of ndiswrapper-source: 
 ndiswrapper-source depends on module-assistant; however: 
  Package module-assistant is not installed. 
 ndiswrapper-source depends on debhelper (>= 5); however: 
  Package debhelper is not installed. 

dpkg: error processing ndiswrapper-source (--install): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 ndiswrapper-source 
tahdas@tahdas:~/Desktop$

---

### Post by chili555 on 2013-01-06
> debhelper_9.20120608ubuntu1_all.deb.[COLOR="Red"]lnk[/COLOR]
module-assistant_0.11.4_all.deb.[COLOR="Red"]lnk[/COLOR]You have *links* to the packages and not the actual packages themselves. Please go back and try again: > Let's go get them: [http://packages.ubuntu.com/quantal/debhelper](http://packages.ubuntu.com/quantal/debhelper)

[http://packages.ubuntu.com/quantal/module-assistant](http://packages.ubuntu.com/quantal/module-assistant)


---

### Post by tahdas on 2013-01-06
What do i click on to download? That what confused me.

Thanks!

---

### Post by chili555 on 2013-01-06
For each, down at the lower left, click 'all.' You will be taken to a list of mirrors. Select one near you and click it. The deb will download and not a link. If none of the mirrors appear near to you, pick any. Drag and drop the debs to your desktop and try again. 

Please see attached.

---

### Post by tahdas on 2013-01-06
tahdas@tahdas:~$ cd Desktop && ls 
debhelper_9.20120608ubuntu1_all.deb 
module-assistant_0.11.4_all.deb 
ndiswrapper-source_1.57-1ubuntu1_all.deb 
ndiswrapper-source_1.57-1ubuntu1_all.deb.lnk 
wna3100-drivers 
tahdas@tahdas:~/Desktop$ sudo dpkg -i debhelper*.deb 
[sudo] password for tahdas: 
Selecting previously unselected package debhelper. 
(Reading database ... 155060 files and directories currently installed.) 
Unpacking debhelper (from debhelper_9.20120608ubuntu1_all.deb) ... 
dpkg: dependency problems prevent configuration of debhelper: 
 debhelper depends on dpkg-dev (>= 1.16.2); however: 
  Package dpkg-dev is not installed. 
 debhelper depends on html2text; however: 
  Package html2text is not installed. 
 debhelper depends on po-debconf; however: 
  Package po-debconf is not installed. 
 debhelper depends on dh-apparmor; however: 
  Package dh-apparmor is not installed. 

dpkg: error processing debhelper (--install): 
 dependency problems - leaving unconfigured 
Processing triggers for man-db ... 
Errors were encountered while processing: 
 debhelper 
tahdas@tahdas:~/Desktop$ sudo dpkg -i ndiswrapper*.deb 
(Reading database ... 155421 files and directories currently installed.) 
Preparing to replace ndiswrapper-source 1.57-1ubuntu1 (using ndiswrapper-source_1.57-1ubuntu1_all.deb) ... 
Unpacking replacement ndiswrapper-source ... 
dpkg: dependency problems prevent configuration of ndiswrapper-source: 
 ndiswrapper-source depends on module-assistant; however: 
  Package module-assistant is not installed. 
 ndiswrapper-source depends on debhelper (>= 5); however: 
  Package debhelper is not configured yet. 

dpkg: error processing ndiswrapper-source (--install): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 ndiswrapper-source 
tahdas@tahdas:~/Desktop$ sudo dpkg -i module-assistant*.deb 
Selecting previously unselected package module-assistant. 
(Reading database ... 155421 files and directories currently installed.) 
Unpacking module-assistant (from module-assistant_0.11.4_all.deb) ... 
Setting up module-assistant (0.11.4) ... 
Processing triggers for man-db ... 
tahdas@tahdas:~/Desktop$ cd Desktop/wna3100-drivers 
bash: cd: Desktop/wna3100-drivers: No such file or directory 
tahdas@tahdas:~/Desktop$ cd wna3100-drivers 
tahdas@tahdas:~/Desktop/wna3100-drivers$ sudo ndiswrapper -i bcmwlhigh5 
sudo: ndiswrapper: command not found 
tahdas@tahdas:~/Desktop/wna3100-drivers$

---

### Post by chili555 on 2013-01-07
> debhelper depends on dpkg-dev (>= 1.16.2); however:
Package dpkg-dev is not installed.
debhelper depends on html2text; however:
Package html2text is not installed.
debhelper depends on po-debconf; however:
Package po-debconf is not installed.
debhelper depends on dh-apparmor; however:
Package dh-apparmor is not installed.
I had no idea this would become an ordeal. However, let's press on regardless. We are going to solve it! Please download and install the packages as before:

[http://packages.ubuntu.com/quantal/dpkg-dev](http://packages.ubuntu.com/quantal/dpkg-dev)

[http://packages.ubuntu.com/quantal/html2text](http://packages.ubuntu.com/quantal/html2text) This package has a 32-bit package and a 64-bit package. Be sure to get the one appropriate to your install. Confirm:```
arch
```32-bit will return i686 and 64-bit will return x86_64. For reasons unknown to me, the packages at the link are labelled i386 for 32-bit and amd64 for 64-bit.

[http://packages.ubuntu.com/quantal/po-debconf](http://packages.ubuntu.com/quantal/po-debconf)

[http://packages.ubuntu.com/quantal/dh-apparmor](http://packages.ubuntu.com/quantal/dh-apparmor)

---

### Post by tahdas on 2013-01-07
I downloaded  the the two things, transferred them to Ubuntu. then I typed in the command arch and it said i686. And I did the same  the other two links at the bottom at the bottom. What are the next commands I should type in?

I'm sorry I made this so complicated.

Thanks again!

---

### Post by chili555 on 2013-01-07
> I'm sorry I made this so complicated.Not at all, my friend. It's only complicated because you have no internet access. We'll solve it! 

Next,install them one at a time:```
cd Desktop
sudo dpkg -i dpkg-dev*.deb
sudo dpkg -i html2text*.deb
sudo dpkg -i po-debconf*.deb
sudo dpkg -i dh-apparmor*.deb
sudo dpkg -i debhelper*.deb

```You need more than ndiswrapper-source. You need ndiswrapper-common and ndiswrapper-utils: [http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=quantal&section=all](http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=quantal&section=all)

Please get those two and skip ndiswrapper-source. That may be why we're getting more and more dependencies!!!

Then do:```
sudo dpkg -i ndiswrapper-utils*.deb
sudo dpkg -i ndiswrapper-common*.deb
cd wna3100-drivers
sudo ndiswrapper -i bcmwlhigh5
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

---

### Post by tahdas on 2013-01-07
Everything went fine until i got to the darn ndiswrapper-utils.

tahdas@tahdas:~$ cd Desktop 
tahdas@tahdas:~/Desktop$ sudo dpkg -i dpkg-dev*.deb 
[sudo] password for tahdas: 
Selecting previously unselected package dpkg-dev. 
(Reading database ... 155476 files and directories currently installed.) 
Unpacking dpkg-dev (from dpkg-dev_1.16.7ubuntu6_all.deb) ... 
Setting up dpkg-dev (1.16.7ubuntu6) ... 
Processing triggers for man-db ... 
tahdas@tahdas:~/Desktop$ sudo dpkg -i html2text*.deb 
Selecting previously unselected package html2text. 
(Reading database ... 155677 files and directories currently installed.) 
Unpacking html2text (from html2text_1.3.2a-15build1_i386.deb) ... 
Setting up html2text (1.3.2a-15build1) ... 
Processing triggers for man-db ... 
Processing triggers for mime-support ... 
tahdas@tahdas:~/Desktop$ sudo dpkg -i po-debconf*.deb 
Selecting previously unselected package po-debconf. 
(Reading database ... 155691 files and directories currently installed.) 
Unpacking po-debconf (from po-debconf_1.0.16+nmu2ubuntu1_all.deb) ... 
Setting up po-debconf (1.0.16+nmu2ubuntu1) ... 
Processing triggers for doc-base ... 
Processing 1 added doc-base file... 
Processing triggers for man-db ... 
tahdas@tahdas:~/Desktop$ sudo dpkg -i dh-apparmor*.deb 
Selecting previously unselected package dh-apparmor. 
(Reading database ... 155758 files and directories currently installed.) 
Unpacking dh-apparmor (from dh-apparmor_2.8.0-0ubuntu5_all.deb) ... 
Setting up dh-apparmor (2.8.0-0ubuntu5) ... 
Processing triggers for man-db ... 
tahdas@tahdas:~/Desktop$ sudo dpkg -i debhelper*.deb 
(Reading database ... 155765 files and directories currently installed.) 
Preparing to replace debhelper 9.20120608ubuntu1 (using debhelper_9.20120608ubuntu1_all.deb) ... 
Unpacking replacement debhelper ... 
Setting up debhelper (9.20120608ubuntu1) ... 
Processing triggers for man-db ... 
tahdas@tahdas:~/Desktop$ sudo dpkg -i ndsiwrapper-utils*.deb 
dpkg: error processing ndsiwrapper-utils*.deb (--install): 
 cannot access archive: No such file or directory 
Errors were encountered while processing: 
 ndsiwrapper-utils*.deb

---

### Post by chili555 on 2013-01-08
> tahdas@tahdas:~/Desktop$ sudo dpkg -i ndsiwrapper-utils*.deb
dpkg: error processing [COLOR="Red"]ndsiwrapper[/COLOR]-utils*.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
ndsiwrapper-utils*.debOh, man, you are so close!

You mis-spelled ndiswrapper. Please try again.

---

### Post by tahdas on 2013-01-08
I spelled it right and got the same result.

---

### Post by chili555 on 2013-01-08
Is the file actually downloaded to your desktop?```
cd Desktop && ls
```Is it maybe ndiswrapper-util and not utils? Did you accidentally again get a link instead of the actual .deb?

---

### Post by tahdas on 2013-01-08
I download the files on windows, put them on a usb drive, then i restart and open with ubuntu, i plug in the usb drive and copy the needed files to desktop.

tahdas@tahdas:~$ cd Desktop && ls 
debhelper_9.20120608ubuntu1_all.deb 
dh-apparmor_2.8.0-0ubuntu5_all.deb 
dpkg-dev_1.16.7ubuntu6_all.deb 
html2text_1.3.2a-15build1_i386.deb 
module-assistant_0.11.4_all.deb 
ndiswrapper-common_1.57-1ubuntu1_all.deb 
ndiswrapper-source_1.57-1ubuntu1_all.deb.lnk 
ndiswrapper-utils-1.9_1.57-1ubuntu1_i386.deb 
po-debconf_1.0.16+nmu2ubuntu1_all.deb 
wna3100-drivers



This is what happens when i typed in the commands:
tahdas@tahdas:~$ sudo dpkg -i ndiswrapper-common*.deb 
[sudo] password for tahdas: 
dpkg: error processing ndiswrapper-common*.deb (--install): 
 cannot access archive: No such file or directory 
Errors were encountered while processing: 
 ndiswrapper-common*.deb 
tahdas@tahdas:~$ sudo dpkg -i ndiswrapper-utils*.deb 
dpkg: error processing ndiswrapper-utils*.deb (--install): 
 cannot access archive: No such file or directory 
Errors were encountered while processing: 
 ndiswrapper-utils*.deb

I even re-downloaded them in windows and brought them over to Ubuntu again but the same thing still happened.

Thanks!

---

### Post by chili555 on 2013-01-08
> tahdas@tahdas:[COLOR="Red"]~[/COLOR]$ sudo dpkg -i ndiswrapper-common*.deb That little cidilla indicates you are in your user directory, not Desktop. I requested:> cd Desktop && ls Evidently, you closed the terminal and started over which took you back to ~ also known as /home/tahdas. If you cd to Desktop, the prompt will look like this:```
chili@Think410:~/Desktop$
```Then you will be able to install your packages.

---

### Post by tahdas on 2013-01-08
I did the ```
cd Desktop && ls
``` and the ndiswrappers installed. Then i did```
cd wna3100-drivers
sudo ndiswrapper -i bcmwlhigh5
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```
I didnt work, so i tried it again making sure i spelled every thing right and got: ```
tahdas@tahdas:~$ cd wna3100-drivers
tahdas@tahdas:~/wna3100-drivers$ sudo ndiswrapper -i bcmwlhigh5
[sudo] password for tahdas: 
install argument must be .inf file
tahdas@tahdas:~/wna3100-drivers$ sudo ndiswrapper -m
module configuration already contains alias directive

tahdas@tahdas:~/wna3100-drivers$ sudo modprobe ndiswrapper 
FATAL: Module ndiswrapper not found.
```

Thanks!

---

### Post by chili555 on 2013-01-09
> $ sudo modprobe ndiswrapper 
FATAL: Module ndiswrapper not found.Ouch! The ndiswrapper system is a bit faulty right now and I'd hoped you might escape it. The Force is not with us today. Please go back here: [http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=quantal&section=all](http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=quantal&section=all)

Download ndiswrapper-dkms and follow the same process to install it. Then try:```
cd ~/Desktop/wna3100-drivers
sudo ndiswrapper -i bcmwlhigh5[COLOR="Red"].inf[/COLOR]
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```Thanks.

---

### Post by tahdas on 2013-01-09
```
tahdas@tahdas:~$ cd ~/desktop/wna3100-drivers 
bash: cd: /home/tahdas/desktop/wna3100-drivers: No such file or directory 
tahdas@tahdas:~$ cd ~/Desktop/wna3100-drivers 
tahdas@tahdas:~/Desktop/wna3100-drivers$ sudo ndiswrapper -i bcmwlhigh5.inf 
[sudo] password for tahdas: 
installing bcmwlhigh5 ... 
tahdas@tahdas:~/Desktop/wna3100-drivers$ sudo ndiswrapper -m 
module configuration already contains alias directive 

tahdas@tahdas:~/Desktop/wna3100-drivers$ sudo modprobe ndiswrapper 
FATAL: Module ndiswrapper not found. 
tahdas@tahdas:~/Desktop/wna3100-drivers$
``` 

Grrr. Everything was fine until the last command. 

Thanks!

---

### Post by chili555 on 2013-01-09
> **tahdas said:**
> 

Grrr. Everything was fine until the last command. 

Thanks!Were you able to download and install ndiswrapper-dkms successfully?

---

### Post by tahdas on 2013-01-09
I thought i had, then i checked again and it seems i haven't:
```

tahdas@tahdas:~$ cd Desktop && ls 
debhelper_9.20120608ubuntu1_all.deb 
dh-apparmor_2.8.0-0ubuntu5_all.deb 
dpkg-dev_1.16.7ubuntu6_all.deb 
html2text_1.3.2a-15build1_i386.deb 
module-assistant_0.11.4_all.deb 
ndiswrapper-common_1.57-1ubuntu1_all.deb 
ndiswrapper-dkms_1.57-1ubuntu1_all.deb 
ndiswrapper-source_1.57-1ubuntu1_all.deb.lnk 
ndiswrapper-utils-1.9_1.57-1ubuntu1_i386.deb 
po-debconf_1.0.16+nmu2ubuntu1_all.deb 
wna3100-drivers 
tahdas@tahdas:~/Desktop$ sudo dpkg -i ndiswrapper-dkms*.deb 
[sudo] password for tahdas: 
(Reading database ... 155825 files and directories currently installed.) 
Preparing to replace ndiswrapper-dkms 1.57-1ubuntu1 (using ndiswrapper-dkms_1.57-1ubuntu1_all.deb) ... 
Unpacking replacement ndiswrapper-dkms ... 
dpkg: dependency problems prevent configuration of ndiswrapper-dkms: 
 ndiswrapper-dkms depends on dkms (>= 2.1.0.0); however: 
  Package dkms is not installed. 

dpkg: error processing ndiswrapper-dkms (--install): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 ndiswrapper-dkms 
tahdas@tahdas:~/Desktop$ 

```

---

### Post by chili555 on 2013-01-09
> ndiswrapper-dkms depends on dkms (>= 2.1.0.0); however: 
  Package dkms is not installed. Are you going to make me say it, or do you know what needs to be done?

[http://packages.ubuntu.com/quantal/dkms](http://packages.ubuntu.com/quantal/dkms)

---

### Post by tahdas on 2013-01-09
Ok i downloaded the file on to my usb. I need to wait 20 minutes until switch to ubuntu because im downloading a game on my windows half, so i'll ask to be sure: Do i need to type in a command  to install "Package dkms"? Or do i just type in:
```
cd Desktop && ls
sudo dpkg -i ndiswrapper-dkms*.deb 
```?

Sorry when i look at the terminal all i see is letters that are meaningless unless you're smart.

Thanks so much!
tahdas

---

### Post by chili555 on 2013-01-09
> **tahdas said:**
> Ok i downloaded the file on to my usb. I need to wait 20 minutes until switch to ubuntu because im downloading a game on my windows half, so i'll ask to be sure: Do i need to type in a command  to install "Package dkms"? Or do i just type in:
```
cd Desktop && ls
sudo dpkg -i ndiswrapper-dkms*.deb 
```?

Sorry when i look at the terminal all i see is letters that are meaningless unless you're smart.

Thanks so much!
tahdasAfter you get the package dkms downloaded to your desktop, do:```
cd Desktop
sudo dpkg -i dkms*.deb
sudo dpkg -i ndiswrapper-dkms*.deb
sudo modprobe ndiswrapper
```It may be that dkms will fail because it wants even more dependencies. We have no way to know until you try it.

---

### Post by tahdas on 2013-01-09
```
tahdas@tahdas:~$ cd Desktop 
tahdas@tahdas:~/Desktop$ sudo dpkg -i dkms*.deb 
[sudo] password for tahdas: 
Selecting previously unselected package dkms. 
(Reading database ... 155825 files and directories currently installed.) 
Unpacking dkms (from dkms_2.2.0.3-1.1ubuntu1_all.deb) ... 
Setting up dkms (2.2.0.3-1.1ubuntu1) ... 
Processing triggers for man-db ... 
tahdas@tahdas:~/Desktop$ sudo dpkg -i ndiswrapper-dkms*.deb 
(Reading database ... 155872 files and directories currently installed.) 
Preparing to replace ndiswrapper-dkms 1.57-1ubuntu1 (using ndiswrapper-dkms_1.57-1ubuntu1_all.deb) ... 
Unpacking replacement ndiswrapper-dkms ... 
Setting up ndiswrapper-dkms (1.57-1ubuntu1) ... 
Loading new ndiswrapper-1.57 DKMS files... 
First Installation: checking all kernels... 
Building only for 3.5.0-17-generic 
Building initial module for 3.5.0-17-generic 
Error! Bad return status for module build on kernel: 3.5.0-17-generic (i686) 
Consult /var/lib/dkms/ndiswrapper/1.57/build/make.log for more information.

```

---

### Post by chili555 on 2013-01-09
> Consult /var/lib/dkms/ndiswrapper/1.57/build/make.log for more information.Let's consult it then:```
cat /var/lib/dkms/ndiswrapper/1.57/build/make.log
```

---

### Post by tahdas on 2013-01-09
```
tahdas@tahdas:~$ cat /var/lib/dkms/ndiswrapper/1.57/build/make.log 
DKMS make.log for ndiswrapper-1.57 for kernel 3.5.0-17-generic (i686) 
Wed Jan  9 17:04:06 EST 2013 
make -C /usr/src/linux-headers-3.5.0-17-generic M=/var/lib/dkms/ndiswrapper/1.57/build 
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic' 
  LD      /var/lib/dkms/ndiswrapper/1.57/build/built-in.o 
  MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/crt_exports.h 
  MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/hal_exports.h 
  MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/ndis_exports.h 
  MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/ntoskernel_exports.h 
  MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/ntoskernel_io_exports.h 
  MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/rtl_exports.h 
  MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/usb_exports.h 
  CC [M]  /var/lib/dkms/ndiswrapper/1.57/build/crt.o 
  CC [M]  /var/lib/dkms/ndiswrapper/1.57/build/hal.o 
  CC [M]  /var/lib/dkms/ndiswrapper/1.57/build/iw_ndis.o 
  CC [M]  /var/lib/dkms/ndiswrapper/1.57/build/loader.o 
  CC [M]  /var/lib/dkms/ndiswrapper/1.57/build/ndis.o 
/var/lib/dkms/ndiswrapper/1.57/build/ndis.c: In function &#8216;NdisGetCurrentProcessorCounts&#8217;: 
/var/lib/dkms/ndiswrapper/1.57/build/ndis.c:2657:24: error: &#8216;struct kernel_stat&#8217; has no member named &#8216;cpustat&#8217; 
/var/lib/dkms/ndiswrapper/1.57/build/ndis.c:2658:31: error: &#8216;struct kernel_stat&#8217; has no member named &#8216;cpustat&#8217; 
/var/lib/dkms/ndiswrapper/1.57/build/ndis.c:2659:17: error: &#8216;struct kernel_stat&#8217; has no member named &#8216;cpustat&#8217; 
make[2]: *** [/var/lib/dkms/ndiswrapper/1.57/build/ndis.o] Error 1 
make[1]: *** [_module_/var/lib/dkms/ndiswrapper/1.57/build] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic' 
make: *** [modules] Error 2 
```
My brain may have just imploded!

Thanks tahdas

---

### Post by chili555 on 2013-01-09
> /var/lib/dkms/ndiswrapper/1.57/build/ndis.c:2657:24: error: ‘struct kernel_stat’ has no member named ‘cpustat’ Congratulations! You are the proud owner of an official bug! [https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1023645](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1023645)

Tomorrow, after a nights sleep, we shall undertake the fix.

---

### Post by tahdas on 2013-01-09
And i thought  the X-files was complicated! :)

Thanks For helping me! 
tahdas

---

### Post by NomCarver on 2013-01-09
I have been following along with  you tahdas! Users like me who are VERY new to all this are grateful for all the work YOU and chili555 have done to sort out all this!

I'm gratified to hear that it's a bug, and not something I was doing wrong in my inexperience.

---

### Post by tahdas on 2013-01-10
Wait how am I getting credit? Chili555 is the only person who is doing here. I'm typing in codes that chili somehow figured out. There is no way i would ever be able to install something like this-even if wasn't a newbie- without tons of help. 

So let's not give credit for something I'm not even doing, but Let's give Chili a round of applause!

Thanks!
Tahdas

---

### Post by chili555 on 2013-01-10
Thank to both of you for your kind comments.

You thought is was tedious before? Now it gets even worse! Hang in there, we can do it. As was pointed out in the bug report, you must compile ndiswrapper from source. Get the file here: [http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/)

Download the file to your desktop and right click it and select Extract Here.

In order to compile it, you need linux-headers and build-essential and all their dependencies. [http://packages.ubuntu.com/quantal/build-essential](http://packages.ubuntu.com/quantal/build-essential)

[http://packages.ubuntu.com/quantal/linux-headers-generic](http://packages.ubuntu.com/quantal/linux-headers-generic)

It appears to me that you now have the headers, but check:```
sudo dpkg -s linux-headers-generic | head -n3
```If it says 'installed OK' then you can mercifully skip that part!

The dependencies means you will also have to get all the packages meentioned with a red dot, i.e. dpkg-dev, g++, gcc, libc6-dev, and make. Before you get them, check to see if they are already installed:```
sudo dpkg -s dpkg-dev  [COLOR="Red"]<--and the others[/COLOR]
```Once all of them are installed:```
sudo dpkg -i build-essential*.deb  [COLOR="Red"]<--and the others[/COLOR]
```Next do:```
cd Desktop/ndiswrapper-1.58rc1
sudo su
make
make install
modprobe ndiswrapper
exit
```As always, post back any errors or questions.I have my fingers crossed and know you will do well.

---

### Post by tahdas on 2013-01-11
I do not have headers. DARN IT! 

 I forgot to mention before that I have wine, would that help?  Also it seem that my dads computer is connected to the Internet via a wire. I could move his computer and conect to the Internet if that would make things faster. 

Thanks again! 
Tahdas

---

### Post by chili555 on 2013-01-11
> Entering directory `/usr/src/*linux-headers-3.5.0-17-generic*' ...from post #100. I was pretty sure you had at least the headers for your current kernel. Please check:```
sudo dpkg -s linux-headers-`uname -r` | head -n3
```Those backticks are on the left side of my US keyboard on the same key with ~.

Of course, if you could manage to get on line for a few moments, it's easy!```
sudo apt-get install build-essential linux-headers-generic
cd Desktop/ndiswrapper-1.58rc1
sudo su
make
make install
modprobe ndiswrapper
exit
```

---

### Post by tahdas on 2013-01-11
Never mind I've got the stuff. I forgot  the s in headers. So I should I do the command you just posted?

---

### Post by chili555 on 2013-01-12
> **tahdas said:**
> Never mind I've got the stuff. I forgot  the s in headers. So I should I do the command you just posted?
Yes, please.

---

### Post by tahdas on 2013-01-12
And no cigar. It didn't work.

Edit:
I think I'm going to just buy another wifi adapter. I heard that the asus USB-n13 worked By just plugging it in. It will work right? The problem is just the USB WNA wifi thing not the computer?

I really appreciate you help, but I think this is just above my current brain and patience level.

Thank so much!
Tahdas

---

### Post by dtucker on 2013-02-15
I was following this trouble-shooting and am pretty much in the same  boat in terms of Linux experience...but I am willing to struggle with it  a little more in order to:
a)  Not have to crack the precious wallet open to buy a new non-cheapo-crap USB Wireless Adapter; and
b)  Hopefully learn a bit more.

> **chili555 said:**
> ```
sudo dpkg -s dpkg-dev  [COLOR=Red]<--and the others {Dave: [/COLOR][COLOR=Red]dpkg-dev, g++, gcc, libc6-dev, and make} [/COLOR]
```Once all of them are installed:```
sudo dpkg -i build-essential*.deb  [COLOR=Red]<--and the others [/COLOR][COLOR=Red][/COLOR]
```

I have been chasing this beast for about 9 hours now, with a break for supper...my neck is cramped and I ran out of junk food! ...I feel I'm close; I was able to install all the above along with the 40 or so dependencies (by USB stick from one online laptop to stranded desktop with fancy new O/S).

But when I go into the ndiswrapper-1.57 directory (1.57 vs 1.58 shouldn't be a huge diff, should it?) and attempt the make command I get the following:[INDENT]**root@beefcake*yadda yadda*/ndiswrapper-1.57# make**
[B]make -C utils
make[1]: Entering directory `/home/.../ndiswrapper-1.57/utils'
make[1]: Nothing to be done for `all'.[/B]
[B]make[1]: Leaving directory `/home/.../ndiswrapper-1.57/utils'
make -C driver
[/B]**make[1]: Entering directory `/home/.../ndiswrapper-1.57/driver'**
**Makefile:36: *** Cannot find kernel version in /lib/modules/3.5.0-17-generic/build, is it configured?.   Stop.**
**make[1]: Leaving directory `/home/.../ndiswrapper-1.57/driver'**
[B]make: *** [driver] Error 2
[/B][/INDENT]Any thoughts?

Cheers!
Dave

---

### Post by chili555 on 2013-02-16
> Cannot find kernel version in /lib/modules/3.5.0-17-generic/build, is it configured?. Stop.This strongly suggests you haven't yet installed linux-headers-`uname -r`. The uname -r refers to your running kernel version, evidently 3.5.0-17-generic. So,you need linux-headers-3.5.0-17-generic and then try again.> 1.57 vs 1.58 shouldn't be a huge diff, should it?Yes, it probably will. If it were me, I'd compile 1.58rc1 instead.

---

### Post by gs44 on 2013-02-16
Hello chili555 and all others,

I have been able to get my wnda3100v2 to work with ubuntu by following great threads such as these.  I have been running Ubuntu 12 lts with my wnda3100v2 for over a year now.  So MANY thanks to chili555 and the rest here!!!

I Do have a question though...  Has anyone been able to connect to a 5ghz connection?  So far mine will only connect to 2.4 ghz connections.

Thanks in advance!!!

---

### Post by chili555 on 2013-02-16
Thanks for your kind comments. I don't have the device, so I can't comment. Perhaps someone else will jump in here.

---

### Post by dtucker on 2013-02-16
Thanks chili555, you were certainly right...I had linux-headers-3.5.0-23-generic downloaded and using 1.58rc1 seemed much more cooperative.

> **chili555 said:**
> This strongly suggests you haven't yet installed linux-headers-`uname -r`. The uname -r refers to your running kernel version, evidently 3.5.0-17-generic. So,you need linux-headers-3.5.0-17-generic and then try again.Yes, it probably will. If it were me, I'd compile 1.58rc1 instead.

Good_News...I was able to get the following to work:
```
iwconfig
```...and it spit out my wlan was recognized!

BAD_NEWS...I believe one or more of the approximately 210 "dependancies" I spent the afternoon manually downloading on my windows laptop one by one and transferring to my ubuntu desktop is not cooperating.

Once I restarted to see if I could get online...the startup screen font is now different and the "status" bar is indicating it will be done at infinity.

...I am now trying to recover. Argh...maintenance shell.

---

### Post by dtucker on 2013-02-16
"If you are running Ubuntu, it is strongly suggested to use a package manager like [aptitude]("http://packages.ubuntu.com/quantal/aptitude") or [synaptic]("http://packages.ubuntu.com/quantal/synaptic") to download and install packages, instead of doing so manually via this website."

...I believe that! ...It seems like I went through a geometric multiplication of depends/depends/depends for every file I downloaded today!

---

### Post by chili555 on 2013-02-16
> **dtucker said:**
> "If you are running Ubuntu, it is strongly suggested to use a package manager like [aptitude]("http://packages.ubuntu.com/quantal/aptitude") or [synaptic]("http://packages.ubuntu.com/quantal/synaptic") to download and install packages, instead of doing so manually via this website."

...I believe that! ...It seems like I went through a geometric multiplication of depends/depends/depends for every file I downloaded today!Indeed! However, if you have no connectivity any other way, you have no choice.> I am now trying to recover.And did you?

---

### Post by dtucker on 2013-02-16
> **chili555 said:**
> Indeed! However, if you have no connectivity any other way, you have no choice.And did you?

Not yet...but let me put it this way: suddenly, the 10 minutes it'll take me to unplug everything from the back of my tower and drag it all to the livingroom to do a setup with ethernet access seems MUCH more reasonable!

;)

...I'll post back tonight or tomorrow with a "huzzah" of success...otherwise you can infer my failure by following Tennessee newspaper headlines describing a man going berzerk and flinging a computer from an overpass.

---

### Post by chili555 on 2013-02-16
> **dtucker said:**
> Not yet...but let me put it this way: suddenly, the 10 minutes it'll take me to unplug everything from the back of my tower and drag it all to the livingroom to do a setup with ethernet access seems MUCH more reasonable!

;)

...I'll post back tonight or tomorrow with a "huzzah" of success...otherwise you can infer my failure by following Tennessee newspaper headlines describing a man going berzerk and flinging a computer from an overpass.You might try just that; hook up the ethernet, that is, and then try:```
sudo apt-get install linux-headers-generic
sudo apt-get update && sudo apt-get -y upgrade
```You might have to recompile ndiswrapper after a reboot; something like:```
cd Desktop/ndiswrapper-1.58rc1
sudo su
make clean
make
make install
modprobe ndiswrapper
exit
```

---

### Post by dtucker on 2013-02-17
I am writing this from Firefox on my desktop using my **_wireless connection_**!

...I'm still setup in the living room...but *baby*-steps!

Thanks so much chili555; without your help I probably would have given up and just slogged through on Windows using Cygwin.  This will be much better for Computational Fluid Dynamics simulations!

To anyone following along, the quote below plus the discussions on which drivers to use in the 1st two pages is pretty much all you need ```
sudo ndiswrapper -i drivername.inf
```...as long as you [COLOR=Red]_**BRING YOUR COMPUTER TO AN ETHERNET CONNECTION!!!**_[/COLOR]

...it is worth a drive if necessary.  I tried to do it by manually installing all the dependencies and got completely lost and ended up needing to reinstall Ubuntu completely.

> **chili555 said:**
> You might try just that; hook up the ethernet, that is, and then try:```
sudo apt-get install linux-headers-generic
sudo apt-get update && sudo apt-get -y upgrade
```You might have to recompile ndiswrapper after a reboot; something like:```
cd Desktop/ndiswrapper-1.58rc1
sudo su
make clean
make
make install
modprobe ndiswrapper
exit
```

---

### Post by dtucker on 2013-02-17
...just as a small follow-up; I had gotten the wireless working - but when I restarted I had to re-initiate in order for it to be recognized again!

I had recalled seeing something about this in the last 48 hours of effort to get this working, so I will refer you to the following thread if you are having a similar issue:
**[COLOR=Blue][http://ubuntuforums.org/showthread.php?t=1733253](http://ubuntuforums.org/showthread.php?t=1733253)[/COLOR]**

...it is by [COLOR=Blue][k3lt01]("http://ubuntuforums.org/member.php?u=397303")[/COLOR] as a response to the **ndisgtk won't install** thread:
```

cd Where your driver files are 
sudo ndiswrapper -i driverfile.inf 
ndiswrapper -l 
sudo depmod -a 
sudo modprobe ndiswrapper 
sudo ndiswrapper -m 
echo "ndiswrapper"|sudo tee -a /etc/modules 
sudo shutdown -r now

```

This worked on restart...although I would not be able to explain how! ...anyone who cares to please do!

Thanks again!!

---

### Post by Silverflyer on 2013-03-24
ok.  I have a problem  I tried everything I can and I get nothing.  the steps I followed are here in another thread that apparently no one in this thread can find without a direct link.  I am posting it here because a forum mod told me to.  My problem is with ndiswrapper.  I have not gotten to the point to have a driver problem yet...

[http://ubuntuforums.org/showthread.php?t=2128034](http://ubuntuforums.org/showthread.php?t=2128034)

---

### Post by Silverflyer on 2013-03-24
Alright, I got it working.  Believe it or not, I compiled ndiswrapper 1.58 and it worked.  I am on the wifi now.

---

### Post by Silverflyer on 2013-03-24
I got a bit upset by this problem, it took my entire weekend, but at least it is done in time for Monday...

---

### Post by Silverflyer on 2013-03-24
well, I spoke too soon apparently...  I did in  fact write my last post using the WiFi, However it will connect to my wifi, but not any webpages now.  I rebooted.  That is all I did.  I can see a bunch of wireless networks and can connect to my own, but can not get a webpage to come up.

---

### Post by chili555 on 2013-03-24
> **Silverflyer said:**
> well, I spoke too soon apparently...  I did in  fact write my last post using the WiFi, However it will connect to my wifi, but not any webpages now.  I rebooted.  That is all I did.  I can see a bunch of wireless networks and can connect to my own, but can not get a webpage to come up.Let's see:```
iwconfig
cat /etc/network/interfaces
```Thanks.

---

### Post by Silverflyer on 2013-03-24
> **chili555 said:**
> Let's see:```
iwconfig
cat /etc/network/interfaces
```Thanks.

iwconfig

```
jason@jason-desktop:~$ iwconfig
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.447 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.


```

```
jason@jason-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


```

---

### Post by chili555 on 2013-03-24
> wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.447 GHz  [COLOR="#FF0000"]Access Point: Not-Associated   [/COLOR]
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
I thought you said it will connect to your wifi; it doesn't seem to be connected now.

---

### Post by Silverflyer on 2013-03-24
I connected back to the ethernet cable, I will connect to wifi and re run.

---

### Post by Silverflyer on 2013-03-24
it is no longer connecting to the WiFi.  I can see it, and many others, and select it, but it does not connect.

---

### Post by Silverflyer on 2013-03-24
> jason@jason-desktop:~$ iwconfig
wlan0     IEEE 802.11g  ESSID:"SOUTHSIDEOFFICE"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: AC:81:12:19:EA:97   
          Bit Rate=65 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.



and

> jason@jason-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

jason@jason-desktop:~$ iwconfig
wlan0     IEEE 802.11g  ESSID:"SOUTHSIDEOFFICE"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: AC:81:12:19:EA:97   
          Bit Rate=65 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

jason@jason-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback



---

### Post by Silverflyer on 2013-03-24
> jason@jason-desktop:~$ iwconfig
wlan0     IEEE 802.11g  ESSID:"SOUTHSIDEOFFICE"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: AC:81:12:19:EA:97   
          Bit Rate=65 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.



and

> 

jason@jason-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback



---

### Post by chili555 on 2013-03-25
Now let's see:```
ifconfig 
nm-tool
```Thanks.

---

### Post by Silverflyer on 2013-03-25
ifconfig, wired and wireless.

> jason@jason-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 44:87:fc:ad:f5:c2  
          inet addr:192.168.15.212  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::4687:fcff:fead:f5c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71801 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56720 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70255375 (70.2 MB)  TX bytes:8590844 (8.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:217046 (217.0 KB)  TX bytes:217046 (217.0 KB)

wlan0     Link encap:Ethernet  HWaddr 30:46:9a:22:e2:80  
          inet addr:192.168.15.234  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::3246:9aff:fe22:e280/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:168107 (168.1 KB)  TX bytes:20632 (20.6 KB)

jason@jason-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 44:87:fc:ad:f5:c2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:71894 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56818 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70263665 (70.2 MB)  TX bytes:8599032 (8.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:219930 (219.9 KB)  TX bytes:219930 (219.9 KB)

wlan0     Link encap:Ethernet  HWaddr 30:46:9a:22:e2:80  
          inet addr:192.168.15.234  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::3246:9aff:fe22:e280/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:169596 (169.5 KB)  TX bytes:21882 (21.8 KB)



nm-tool wireless

> jason@jason-desktop:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [SOUTHSIDEOFFICE] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        30:46:9A:22:E2:80

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Kelly Manor:     Infra, 68:7F:74:4D:3C:47, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    WiFiRSU_96540:   Infra, 20:10:7A:1E:60:2A, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA2
    WhiteMaple:      Infra, 58:6D:8F:2C:01:ED, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    WiFiRSU_d6:      Infra, AC:81:12:1D:03:92, Freq 2447 MHz, Rate 54 Mb/s, Strength 34 WPA2
    Blessing Way:    Infra, 40:4A:03:DB:FF:91, Freq 2427 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Kelly Manor-guest: Infra, 68:7F:74:4D:3C:48, Freq 2412 MHz, Rate 54 Mb/s, Strength 55
    HOME-E798:       Infra, B8:9B:C9:69:E7:98, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    YellowMoose:     Infra, 68:7F:74:31:F6:FA, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    WhiteMaple-guest:Infra, 58:6D:8F:2C:01:EF, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
    orangeid:        Infra, 00:1F:41:77:30:78, Freq 2457 MHz, Rate 54 Mb/s, Strength 29
    *SOUTHSIDEOFFICE:Infra, AC:81:12:19:EA:97, Freq 2447 MHz, Rate 54 Mb/s, Strength 78 WPA2
    isaias-b3d013cf-Wireless: Infra, 00:26:F2:07:1F:1E, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Roslyn:          Infra, 00:24:7B:7C:03:B8, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    Private 023:     Infra, 06:1B:63:18:20:59, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    mike:            Infra, 40:4A:03:DE:69:82, Freq 2417 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    TMobile:         Infra, 00:24:7B:0D:FB:2C, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2

  IPv4 Settings:
    Address:         192.168.15.234
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.15.1

    DNS:             192.168.15.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        44:87:FC:AD:F5:C2

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off



---

### Post by Silverflyer on 2013-03-25
At the moment, the wireless seems to be working.  The ethernet cable is disconnected.

---

### Post by chili555 on 2013-03-25
It looks pretty healthy from here. Please post back if you have more trouble.

---

### Post by Silverflyer on 2013-03-25
> **chili555 said:**
> It looks pretty healthy from here. Please post back if you have more trouble.  It does seem to be working.  It remained working after a restart too.  I don't know why it stopped working yesterday, but it is working today just fine so far.  Thanks for your help.

---

### Post by Systmfdwn147 on 2013-04-02
Hi, first off let me say how thankful I am for all of this info and to chili555, but I've run into a problem. I can't stay connected to the internet for no longer than 10 minutes at the most.

I have Ubuntu 12.04  64-bit running and am using ndiswrapper 1.58. I also have my router set to wpa2 only which I saw suggested, but that didn't seem to help.

Could it be possible that Ubuntu 12.10 would be a better solution or perhaps ndiswrapper 1.57?

---

### Post by chili555 on 2013-04-03
> **Systmfdwn147 said:**
> Hi, first off let me say how thankful I am for all of this info and to chili555, but I've run into a problem. I can't stay connected to the internet for no longer than 10 minutes at the most.

I have Ubuntu 12.04  64-bit running and am using ndiswrapper 1.58. I also have my router set to wpa2 only which I saw suggested, but that didn't seem to help.

Could it be possible that Ubuntu 12.10 would be a better solution or perhaps ndiswrapper 1.57?It's easy enough to try 1.57. Simply open a terminal and uninstall 1.58:```
cd Desktop/ndiswrapper-1.58  [COLOR="#FF0000"]<--or wherever you extracted the package[/COLOR]
sudo su
make uninstall
exit
```Now get a temporary ethernet connection and do:```
sudo apt-get install --reinstall ndiswrapper-utils-1.9
sudo apt-get install --reinstall ndiswrapper-dkms
sudo apt-get install --reinstall ndiswrapper-common
```As for 12.10, I always believe newer is better and more likely to be successful.

---

### Post by Systmfdwn147 on 2013-04-04
I was able to get it figured out. I now have it working for 12.04 64 bit with ndiswrapper 1.58.

if anyone else is having this disconnecting problem see this thread post #6:
[http://ubuntuforums.org/showthread.php?p=12171877#post12171877](http://ubuntuforums.org/showthread.php?p=12171877#post12171877)

---

### Post by lucasme on 2013-04-06
[PROBLEM SOLVED =), PLEASE IGNORE THIS]

Hello, 

 I wouldn't like to bother chili555 anymore but I was having this same problem and after 7 hours and reading through this whole thread I believe I'm really close to get it working. I installed ndiswrapper and WINE, 
   downloaded the WNDA3100 adapter driver: bcmn43xx32 and installed it using ndiswrapper. The system now finally recognizes my wireless connections, but when I try to connect to my home network, it keeps trying to connect but without success, 
   and keeps prompting me to enter the password even when I'm using wired connection, which I do, correctly.

**ndiswrapper -l**

   ```
bcmn43xx32 : driver installed
              device (0846:9011) present
   
```



**iwconfig**

  ```
  wlan0     IEEE 802.11g  ESSID:"Mezalira"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:B8:20:50:4D   
          Bit Rate=65 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:70/100  Signal level:-51 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

               lo        no wireless extensions.

               eth0      no wireless extensions.


```


**ifconfig**

```
eth0      Link encap:Ethernet  HWaddr f4:6d:04:65:3a:b0  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f66d:4ff:fe65:3ab0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2001 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2499690 (2.4 MB)  TX bytes:336010 (336.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:962 errors:0 dropped:0 overruns:0 frame:0
          TX packets:962 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79043 (79.0 KB)  TX bytes:79043 (79.0 KB)

wlan0     Link encap:Ethernet  HWaddr e0:46:9a:04:60:1a  
          inet6 addr: fe80::e246:9aff:fe04:601a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2568 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:291588 (291.5 KB)  TX bytes:15993 (15.9 KB)



```


I am now connected to my wired network. I run Ubuntu 12.10   32bit.

Thank you =)

---

### Post by lucasme on 2013-04-07
Well I couldnt find a way to delete my last post, so please disregard it...The wireless connection is miraculously working =)

---

### Post by Silverflyer on 2013-04-12
Question.  How long should "modprobe ndiswrapper" take to run?  I ask because I recently had to reinstall Linux due to an update that hosed my system so I am back to getting my wireless to run.  I followed the steps, downloaded 1.58 and ran the terminal commands, it seems to be stuck on the modprobe step.

---

### Post by chili555 on 2013-04-12
> **Silverflyer said:**
> Question.  How long should "modprobe ndiswrapper" take to run?  I ask because I recently had to reinstall Linux due to an update that hosed my system so I am back to getting my wireless to run.  I followed the steps, downloaded 1.58 and ran the terminal commands, it seems to be stuck on the modprobe step.It should take less than a second. You may be able to see what's wrong by monitoring the logs:```
cat /var/log/syslog | tail -n20
```

---

### Post by Silverflyer on 2013-04-12
I ran the commands, then your command above and this is what I get.

> jason@jason-b628:~$ cat /var/log/syslog | tail -n20
Apr 12 10:26:44 jason-b628 kernel: [ 1200.220219]  [<c13bf759>] ? pm_runtime_barrier+0x49/0xb0
Apr 12 10:26:44 jason-b628 kernel: [ 1200.220222]  [<c13b5b6a>] driver_probe_device+0x3a/0x60
Apr 12 10:26:44 jason-b628 kernel: [ 1200.220226]  [<c13b5c21>] __driver_attach+0x91/0xa0
Apr 12 10:26:44 jason-b628 kernel: [ 1200.220229]  [<c13b5b90>] ? driver_probe_device+0x60/0x60
Apr 12 10:26:44 jason-b628 kernel: [ 1200.220233]  [<c13b42ca>] bus_for_each_dev+0x4a/0x80
Apr 12 10:26:44 jason-b628 kernel: [ 1200.220237]  [<c13b55a1>] driver_attach+0x21/0x30
Apr 12 10:26:44 jason-b628 kernel: [ 1200.220240]  [<c13b5b90>] ? driver_probe_device+0x60/0x60
Apr 12 10:26:44 jason-b628 kernel: [ 1200.220244]  [<c13b5207>] bus_add_driver+0x187/0x260
Apr 12 10:26:44 jason-b628 kernel: [ 1200.220248]  [<c12fbd70>] ? pci_device_probe+0x90/0x90
Apr 12 10:26:44 jason-b628 kernel: [ 1200.220251]  [<c13b60d6>] driver_register+0x66/0x110
Apr 12 10:26:44 jason-b628 kernel: [ 1200.220255]  [<c13a2e98>] ? misc_register.part.1+0x78/0xe0
Apr 12 10:26:44 jason-b628 kernel: [ 1200.220258]  [<c12fbb12>] __pci_register_driver+0x42/0xa0
Apr 12 10:26:44 jason-b628 kernel: [ 1200.220272]  [<f986d67a>] loader_init+0x8a/0x140 [ndiswrapper]
Apr 12 10:26:44 jason-b628 kernel: [ 1200.220286]  [<f987c0e7>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
Apr 12 10:26:44 jason-b628 kernel: [ 1200.220297]  [<f989a077>] wrapper_init+0x77/0x1000 [ndiswrapper]
Apr 12 10:26:44 jason-b628 kernel: [ 1200.220301]  [<c1003034>] do_one_initcall+0x34/0x170
Apr 12 10:26:44 jason-b628 kernel: [ 1200.220313]  [<f989a000>] ? 0xf9899fff
Apr 12 10:26:44 jason-b628 kernel: [ 1200.220318]  [<c10a56ad>] sys_init_module+0xad/0x200
Apr 12 10:26:44 jason-b628 kernel: [ 1200.220322]  [<c1151dc3>] ? sys_close+0x73/0xc0
Apr 12 10:26:44 jason-b628 kernel: [ 1200.220326]  [<c15e791f>] sysenter_do_call+0x12/0x28
jason@jason-b628:~$ 



---

### Post by chili555 on 2013-04-12
You either have the wrong inf file for your device or the 1.58 compile didn't go well. Please confirm your device, architecture and tell us where you got the inf and sys files:```
lsusb
arch
```

---

### Post by Silverflyer on 2013-04-12
I downloaded ndiswrapper 1.58 from the link provided by you earlier in this thread.  The commands above gave this.

> jason@jason-b628:~$ lsusb
Bus 001 Device 004: ID 1307:0330 Transcend Information, Inc. 63-in-1 Multi-Card Reader/Writer
Bus 001 Device 006: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 002 Device 002: ID 046d:0a01 Logitech, Inc. USB Headset
Bus 003 Device 002: ID 04f2:0116 Chicony Electronics Co., Ltd KU-2971/KU-0325 Keyboard
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jason@jason-b628:~$ arch
i686
jason@jason-b628:~$ 



---

### Post by Silverflyer on 2013-04-12
The driver files came from the first link in this thread.

---

### Post by Silverflyer on 2013-04-12
I got it.  I installed 1.57, then installed 1.58 and it worked.  very odd.

---

### Post by chili555 on 2013-04-12
I'm glad it's working by whatever means. Have fun!

---

### Post by jurgenvanimpe_7 on 2013-10-27
Hi, I've been through this forum, this topic and other ones... But I came to a point where I'm stuck...
Any help would be appreciated!

The usb-adater:
*************
Netgear N300 WNA3100**M** (most of the others on this forum are not with M on the end I think)

Descriptions of my system:
***********************
I do have Win7 64-bit working fine with the Netgear USB adapter, so the USB adapter is working fine (newly bought so it beter should be! :p )
But the problem is on my Ubuntu 10.4 LTS; which itself is running from a USB stick but I think that doesn't matter, because it is also persistent.

```
root@bt:~# uname -a
Linux bt 3.2.6 #1 SMP Fri Feb 17 10:40:05 EST 2012 i686 GNU/Linux
```

Internet connections:
******************
As you can see below, I do have a hard wired working internet connection working fine at the moment.
```
root@bt:~# ifconfig
eth3      Link encap:Ethernet  HWaddr 64:70:02:03:8a:3e  
          inet addr:192.168.0.xxx  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::xxxx:2ff:fe03:8a3e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16609 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13191 errors:0 dropped:0 overruns:3 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19381663 (19.3 MB)  TX bytes:1787903 (1.7 MB)
          Interrupt:18 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15913632 (15.9 MB)  TX bytes:15913632 (15.9 MB)
```

```
root@bt:~# iwconfig
eth3      no wireless extensions.

lo        no wireless extensions.
```
The above is even with the USB adapter plugged in...

Things I've done and tried:
***********************
- Tried several versions of ndiswrapper thinking that that could have been the problem. 
The current version is:
```
root@bt:~# ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/3.2.6/misc/ndiswrapper.ko
version:        1.58
vermagic:       3.2.6 SMP mod_unload CORE2 

```
I've tried different drivers, but the latest one also came from a suggestion of chili555, I made sure to use the 32-bit files .cat .inf .dll and .sys.
Note that there was only one .dll file available in the zipped file I downloaded from here.

```
root@bt:~# ndiswrapper -l
bcmwlhigh5 : driver installed
    device (0846:9021) present
```

Also interesting to see is the following:
```
root@bt:~# lsusb | grep NetGear
Bus 002 Device 004: ID 0846:90**21** NetGear, Inc.
```
Note that the last number differs from the **20** that the first person in this thread had; see post #1
I putted here under
```
Bus 001 Device 003 : ID 0846:9020 Netgear, Inc. **WNA3100(v1) Wireless-N 300 [Broadcom BCM43231**
```
and also mine isn't giving anything like "WNA3100(v1) wireless-N 300 [Broadcom BCM43231" at the end of it's description

Info from dmesg:
***************
Do note that I retried modeprobe a bouple of times, but it never changes anything...
```
root@bt:~# dmesg | grep ndiswrapper
[  355.143951] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[  355.333811] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[  355.339457] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[  355.339463] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[  355.339470] ndiswrapper (mp_halt:254): device f616d480 is not initialized - not halting
[  355.339473] ndiswrapper: device eth%d removed
[  355.339522] ndiswrapper: probe of 2-1.7:1.0 failed with error -22
[  355.339536] usbcore: registered new interface driver ndiswrapper
[ 3958.028567] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[ 3958.033477] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[ 3958.033483] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[ 3958.033489] ndiswrapper (mp_halt:254): device f6baf480 is not initialized - not halting
[ 3958.033492] ndiswrapper: device eth%d removed
[ 3958.033570] ndiswrapper: probe of 2-1.7:1.0 failed with error -22
[ 5077.990652] usbcore: deregistering interface driver ndiswrapper
[ 5083.985083] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[ 5084.156024] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[ 5084.161250] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[ 5084.161253] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[ 5084.161258] ndiswrapper (mp_halt:254): device f6ba8480 is not initialized - not halting
[ 5084.161259] ndiswrapper: device eth%d removed
[ 5084.161314] ndiswrapper: probe of 2-1.7:1.0 failed with error -22
[ 5084.161332] usbcore: registered new interface driver ndiswrapper
[ 5807.086154] usbcore: deregistering interface driver ndiswrapper
[ 5825.617222] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[ 5825.787914] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[ 5825.792596] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[ 5825.792602] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[ 5825.792609] ndiswrapper (mp_halt:254): device f69a8480 is not initialized - not halting
[ 5825.792612] ndiswrapper: device eth%d removed
[ 5825.792675] ndiswrapper: probe of 2-1.7:1.0 failed with error -22
[ 5825.792701] usbcore: registered new interface driver ndiswrapper
```

So as you can see from above, the following is the problem according to me:
```
[ 5825.787914] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[ 5825.792596] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
```

I also read somewhere that I should take it the hard wired internet connection and reboot, but this still doesn't let
me see the USB adapter in iwconfig although it's being detected by the "lsusb" command ...

Do I need to adjust the network manager or something?

Sorry for the long post, but I wanted to give as much details as possible.

PS: it could be that I can't reply before next week..

---

### Post by chili555 on 2013-10-27
First, I know nothing about Backtrack and I don't want to study up and learn everything there is to know about Backtrack, Debian, Mint, and all the other Ubuntu cousins. Second, if yours is a 64-bit system, this device may *NEVER* work using ndiswrapper; meaning it will never work. Third, I hate the WNA3100 more than I hate an impacted wisdom tooth and even more than my first wife's lawyer! Finally, here is a forum post where the same error was enumerated:> ndiswrapper (mp_init:211): couldn't initialize device: C0000001[http://ubuntuforums.org/showthread.php?t=1965989&page=3](http://ubuntuforums.org/showthread.php?t=1965989&page=3) I suggested and attached a different set of inf and sys files. I suggest you try the same. If that doesn't help, I really have no other suggestions. Perhaps one of my esteemed colleagues will.

---

### Post by jurgenvanimpe_7 on 2013-10-27
Thank you very much for the very fast response!
I looked over that set of drivers, so i will give it a try.
And i appreciate your honest answer, but if there is a way to make it work, i will find it!
I dondt want you to read up on bt, it doesnt matter.

I will let you know how it went :-)

---

### Post by jurgenvanimpe_7 on 2013-10-27
Apperently i allready tried these drivers after all without any succes again...
Other suggestions are welcome, in the meantime i'll keep looking to get it working.
Thanks again

---

### Post by zack796 on 2013-12-16
This issue is with Ubuntu 12.04 LTS

So far, i've installed ndiswrapper-common, ndiswrapper-dkms, ndiswrapper-source, and ndiswrapper-utils-1.9 using sudo apt-get install. I've installed the appropriate driver on the Windows Wireless drivers program (bcmn43xx64 and bcmwlhigh5) and I even used lsusb to make sure it could see my WNA3100 usb adapter. It still isn't detecting the wireless network. Also doing sudo modprobe ndiswrapper presents me with the whole **FATAL: ndiswrapper module not found**.

Am I missing something?

---

### Post by ajgreeny on 2013-12-16
**ndiswrapper** in 12.04 seems to be broken, and I think you need to compile it yourself, or perhaps search for a ppa with a version that works.

See Section 4 of [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) which may help you.  Don't be dismayed by the web instructions, use a cable connection if possible then just copy/paste the commands for ease of attacking the problem.

More info also at [http://ubuntuforums.org/showthread.php?t=1987695](http://ubuntuforums.org/showthread.php?t=1987695)
and [https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1023645](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1023645)

This is an old bug which I am surprised has not been sorted by now, but it appears not to have been.

---

### Post by mörgæs on 2013-12-16
Threads merged.

---

### Post by dahltonguilbeau on 2014-04-21
[QUOTE=chili555;11879280]None of those blacklists add or detract from your case. I suggest you remove the file altogether:```
sudo rm /etc/modprobe.d/blacklist
```Please delete the bcmwlhigh5 as above and try these files. You will be installing bcmn43xx64.inf.

As you have seen, this device on 64-bit is quite tricky.

---

### Post by tji on 2014-09-30
I am trying to get my WNDA3100v2 working on a 12.04 system.   I have gotten it to connect to a 2.4GHz wireless network, but there is too much interference there.  I need to use the 5GHz band.   But, I cannot get it to show anything by 2.4GHz networks available.


Is there some trick to getting it to see / use 5GHz channels?

---

### Post by mörgæs on 2014-09-30
Are you sure that all 11 / 13 channels of the 2.4 GHz band are congested?

---

### Post by tji on 2014-09-30
Yes, I have many neighbors.  Other reasons include contention from many devices and better performance with 5GHz (yes, I have tested it in my environment).   

Can this adapter do 5ghz in Linux?   The hardware is capable, but I only see 2.4ghz channels available.

---

### Post by chili555 on 2014-09-30
ndiswrapper is a crutch to use Windows XP drivers where no native Linux driver is available. We are gratified when it works at all! 

I know of no method to manipulate the 2.4 vs. 5 gHz connection.

---

