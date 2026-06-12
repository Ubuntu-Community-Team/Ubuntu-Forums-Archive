---
title: "Wireless Connectivity Issues..."
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by user 123 on 2009-01-24
Hey. My wireless modem/router is located downstairs. While using Ubuntu, if I move my laptop upstairs, Ubuntu says have around 44% conectivity however I cannot access the internet. If I move downstairs however this problem disappears. I don't get this problem if I switch to Vista and can access the internet anywhere.
Im not sure what the reason for the problem could be here, wireless drivers, router settings etc
If anyone could help out I'd be really grateful as I have to switch operating systems from Ubuntu to Vista to access the internet upstairs.
Thanks.

---

### Post by AlexBellisBrown on 2009-01-24
First we need to know the make and model of your wireless card. Do you know it? Also could you post the outcome of lsusb from terminal? That would tell us if you dont know it. :)

---

### Post by user 123 on 2009-01-24
Bus 006 Device 003: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 006 Device 002: ID 04f2:b064 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Cosimix on 2009-01-24
[B][COLOR=Red][MODIFIED READ THROUGH AGAIN PLEASE]
[/COLOR][/B]
    **[COLOR=Green]YOU ARE A LUCKY BOY WIRELESS IS MY BREAD[/COLOR]**

**Introduction:** microsoft and Linux drivers for network cards might be different and thus they would effectively show different behaviour in terms of connectivity, roaming and so on. 

I am gonna show you how to troubleshoot your WX Network smartly:

Do the following on the command line:

** 1.** INSTALL a very cool tool for troubleshooting wireless connections:
**sudo apt-get install wavemon ** on the CLI

**2.** After connecting to the AP anywhere in your house you can succeed, run wavemon. 

**3.** After checking and taking a note of the following values:
signal level: 0 dBm 
noise level: 0 dBm 
signal-to-noise ratio: 0 dB

...you start moving around in your house while keeping an eye on the signal level and signal-to-noise ratio:
[B]
signal[/B]: should be at least -70dBm to be able to have a decent connection depending also on the NIC card
[B]
signal-to-noise ratio:
0[/B]        means you are gonna get disconnected[B]
+10[/B] means consider to slightly decrease the transmission rate  (Mbps)
**+20** or higher means the higher the better you can increase the transmission rate (Mbps)

To set the bandwidth
**sudo iwconfig wlan0 rate 54M**         <or 48M 36M 24M  and so on >


If you lose the connection you can try a manual connection, run:
**iwlist wlan0 scan**
and take a note of the MAC of your AP like Cell 01 - Address: [COLOR=Red]**XX:XX:XX:XX:XX:XX**[/COLOR]
now use the command 
[B]sudo iwconfig wlan0 ap[COLOR=Red] XX:XX:XX:XX:XX:XX [COLOR=Black]rate[/COLOR][/COLOR] 11M essid "myssid" txpower 15 power off channel auto 
[/B]
debug using the command
**dmesg | tail -n 20**

...check the AP settings in terms of transmission power. Within your house you should have more signal unless you have RF obstacles (i.e. water, metal or very sharp glass surfaces)

If you send me all this information (screenshots or CLI output) I can interpret them for you.

Ciao

---

### Post by user 123 on 2009-01-24
```
wlan0     IEEE 802.11bg  ESSID:"WNETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:AB:9D:3A   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=96/100  Signal level:-23 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



wlan0     Link encap:Ethernet  HWaddr 00:16:44:d7:d0:55  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:fed7:d055/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:667 errors:0 dropped:0 overruns:0 frame:0
          TX packets:668 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:721215 (721.2 KB)  TX bytes:135440 (135.4 KB)



wlan0     Scan completed :
          Cell 01 - Address: 00:1B:2F:AB:9D:3A
                    ESSID:"WNETGEAR"
```

---

### Post by Cosimix on 2009-01-24
[B]Hi read above I have modified my first post to keep the thread short
[/B]


...send me the complete output of your AP info using **iwlist wlan0 scan** run in the room where you can't connect from.

and also run this command a few times in order to detect interferences on the channel from other AP:
**iwlist wlan0 scan | grep Frequency ** 

Cheers

---

### Post by user 123 on 2009-02-02
Sorry for the very late reply, I've been away for a while

i used wavemon in the room where the connectivity is iffy
Signal Level is around -43 dBm
Signal to noise ratio is around +213 dB

I ran sudo iwconfig wlan0 rate 54M (although I don't know what this does exactly or the reason for it)

iwlist wlan0 scan gives this:

```
wlan0     Scan completed :
          Cell 01 - Address: 00:1B:2F:AB:9D:3A
                    ESSID:"WNETGEAR"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/100  Signal level:-52 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000038a8b181
                    Extra: Last beacon: 12ms ago
```


The fault seems pretty intermittent, one second I can load a page no problem, the rest (and majority by far) of the time I can't connect to anything.

---

### Post by user 123 on 2009-02-02
Some other information:

The problem now happens everywhere. Again Vista still works fine.

```
ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1e:68:7a:0a:3e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1368 (1.3 KB)  TX bytes:1368 (1.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:d7:d0:55  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:fed7:d055/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1882 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2386 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1784373 (1.7 MB)  TX bytes:634590 (634.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-44-D7-D0-55-30-35-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"WNETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:AB:9D:3A   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=66/100  Signal level:-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

My laptop is a Toshiba Satellite Pro if that helps too.

---

### Post by user 123 on 2009-02-05
Can anyone help? This is getting pretty desperate now...

---

### Post by Cosimix on 2009-02-08
Hi there,
use the Network Manager Applet to make your life easier. You don't seem to have big problems in terms of signal and SNR (though +213dB sounds a bit odd, typical values go from 0 to +40dB). 

**NOTE** When you are "desperate" and you don't really know what's going on, in order to ease and simplify the troubleshooting you should setup an Open and not Encrypted SSID. This is just for testing any connectivity issue. Upon terminating all your tests, then you can build more security options (Encryption, MAC Authentication, dot1x and so on).   

Assuming that you have created such a basic SSID called **test**, try to establish a manual connection:

**sudo ifconfig wlan0 up**
**sudo iwconfig wlan0 essid "test" power off txpower 15 rate 54M channel 11 ap 00:1B:2F:AB:9D:3A**

...just immediately after running the last command use 
**dmesg | tail -n 20 **to see whether you get authenticated... You should get a line like:
[I] authenticated with station ...
 associated with station ... 
[/I]
if you succeed then run 
[B]sudo dhclient wlan0
[/B]to get an IP address from the AP.

Alternatively, you can check on the AP Client List and Event Log if you are getting connected. 

**Changes to the configuration**
The MTU for wireless is 2304 (excluding IP and 802.11 frame headers), therefore you need to modify your settings. To change it use:

**sudo ifconfig wlan0 mtu 2274**

or make it permanent by adding this line at the bottom of the /etc/rc.local file
[B]
ifconfig wlan0 mtu 2274
[/B]exit 0

*** That's the maximum the driver iwl3945 can accept apparently (dunno why), but 2274 is far better than 1500 anyway.


**NOTE **802.11G in Europe avails of 13 channels but only 3 channels are not overlapping/interfering to each other, thus can be used simultaneously by different APs:
1-6-11
2-7-12
3-8-13

You should never use adjacent channels i.e. 1-2-3-4-5 or 9-10-11-12-13
If you have another AP using the same channel you get packets disruptions. If you are using channel 11 all the APs in your area using channels 7 to 13 will cause interference. This also means that supposing you have your neighboring APs using channel 1 and 11 you would have to use channel 6 to avoid interferences. When packets are corrupted, they would need retransmitting. Typical symptom of this is SNR tending to 0 or lower than 10dB, and the consequence includes general connectivity and performance issues. To determine what the best channel to use is, run this command a few times.
  **iwlist wlan0 scan | grep Frequency ** 

Alternatively and better you can use airodump
[B]sudo apt-get install aircrack-ng
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
sudo ifconfig wlan0 up
sudo airodump -i wlan0 -w /tmp/scan
[/B]
The output will tell you what channel your neighboring APs are using. 

If your Wireless card gets stuck 

1. **sudo ifdown wlan0**

2. Try to physically turn off and back on the Wireless Radio on your laptop using the Wireless button/toggle if there is any (most laptops have one), then use the command:
[B]
3. sudo ifup wlan0 [/B]

**4. **Send me this as well **uname -a**

**5. **The problem might be on the AP side as well. Consider to reset it to factory defaults.

Should all of this fail we need to use tcpdump or Wireshark and things might become a little bit more complicated if you have never used it before.

Ciao

---

### Post by user 123 on 2009-02-08
After I run dmesg | tail -n 20
I get this:

```
[10105.698150] wlan0: associated
[10111.473040] wlan0: no IPv6 routers present
[10131.646882] wlan0: disassociating by local choice (reason=3)
[10131.822383] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[10151.129879] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10151.307102] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[10151.308872] wlan0: authenticated
[10151.308885] wlan0: associate with AP 00:1b:2f:ab:9d:3a
[10151.311110] wlan0: RX AssocResp from 00:1b:2f:ab:9d:3a (capab=0x421 status=0 aid=1)
[10151.311122] wlan0: associated
[10151.311674] wlan0: disassociating by local choice (reason=3)
[10159.289423] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[10159.489043] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[10159.785491] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[10159.785557] wlan0: authenticated
[10159.785566] wlan0: associate with AP 00:1b:2f:ab:9d:3a
[10159.789493] wlan0: RX ReassocResp from 00:1b:2f:ab:9d:3a (capab=0x421 status=0 aid=1)
[10159.789504] wlan0: associated
[10159.791291] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10159.792169] wlan0: disassociating by local choice (reason=3)

```

---

### Post by Cosimix on 2009-02-08
I hope, 
I haven't made you even more confused now!

:)

---

### Post by user 123 on 2009-02-08
You mean thats the response I should expect?

---

### Post by Cosimix on 2009-02-08
This is your problem man:

**[10159.792169] wlan0: disassociating by local choice (reason=3)**

This was reported as a bug / Network Manager conflict resolved in later kernel releases. Next step is checking what Linux you are running:

[B]cat /etc/issue
uname -a
sudo lshw -C network
[/B]

---

### Post by user 123 on 2009-02-08
```
ben@ben-laptop:~$ cat /etc/issue
Ubuntu 8.10 \n \l

ben@ben-laptop:~$ uname -a
Linux ben-laptop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
ben@ben-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 16
       serial: 00:1e:68:7a:0a:3e
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:44:d7:d0:55
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.3 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: be:81:ad:66:2a:aa
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by user 123 on 2009-02-09
I constatly update my software so I wouldn't think my version would be a problem..

---

### Post by Cosimix on 2009-02-09
Hi 
sorry, I wrongly assumed you had an Intel 3945ABG card. Since this card has always had great support with Linux, I ruled out any hardware configuration issue, and I gave you general support for wireless.

From the output of those commands, it seems like there is no driver (module) assigned to the card and your card's manufacturer is LITE-ON Technology Corp.

Please send full output of these commands to double check:

[B]dmesg
lsmod
lspci -vvv[/B]

Check also whether you have any proprietary driver being automatically assigned:  

System > Administration > Hardware Drivers

Ciao

---

### Post by user 123 on 2009-02-10
```
ben@ben-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  263972  10 
aes_i586               15744  1 
aes_generic            35880  1 aes_i586
af_packet              25728  4 
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
ppdev                  15620  0 
powernow_k8            22148  1 
sbs                    19464  0 
pci_slot               12680  0 
container              11520  0 
cpufreq_ondemand       14988  1 
cpufreq_userspace      11396  0 
sbshc                  13440  1 sbs
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
freq_table             12672  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
uvcvideo               63624  0 
rtl8187                53248  0 
snd_pcm_oss            46848  0 
snd_hda_intel         384176  2 
compat_ioctl32          9344  1 uvcvideo
mac80211              216820  1 rtl8187
k8temp                 12416  0 
evdev                  17696  11 
pcspkr                 10624  0 
eeprom_93cx6           10240  1 rtl8187
serio_raw              13444  0 
snd_mixer_oss          22784  1 snd_pcm_oss
psmouse                45200  0 
sdhci_pci              15360  0 
snd_seq_dummy          10884  0 
sdhci                  23940  1 sdhci_pci
videodev               41344  1 uvcvideo
snd_seq_oss            38528  0 
usb_storage            82752  1 
mmc_core               58268  1 sdhci
cfg80211               32392  2 rtl8187,mac80211
snd_pcm                83204  2 snd_pcm_oss,snd_hda_intel
v4l1_compat            22404  2 uvcvideo,videodev
libusual               30356  1 usb_storage
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i2c_piix4              16144  0 
snd_timer              29960  2 snd_pcm,snd_seq
i2c_core               31892  1 i2c_piix4
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  13 snd_pcm_oss,snd_hda_intel,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
video                  25232  0 
output                 11008  1 video
fglrx                1813960  30 
battery                18436  0 
wmi                    14504  0 
ac                     12292  0 
button                 14224  0 
ati_agp                14988  0 
agpgart                42184  2 fglrx,ati_agp
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sd_mod                 42392  5 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  2 
ohci1394               37936  0 
ohci_hcd               32016  0 
ahci                   37132  4 
ieee1394               96324  2 sbp2,ohci1394
ehci_hcd               43788  0 
pata_atiixp            12800  0 
pata_acpi              12160  0 
ata_generic            12932  0 
usbcore               149360  7 uvcvideo,rtl8187,usb_storage,libusual,ohci_hcd,ehci_hcd
libata                178208  4 ahci,pata_atiixp,pata_acpi,ata_generic
scsi_mod              155212  6 sbp2,usb_storage,sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
sky2                   53380  0 
thermal                23708  0 
processor              42156  2 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
ben@ben-laptop:~$ lspci -vvv
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
	Subsystem: Toshiba America Info Systems Device ff50
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 64
	Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: f8000000-f81fffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f7ffffff
	Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel modules: shpchp

00:04.0 PCI bridge: ATI Technologies Inc Device 7914
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: fff00000-000fffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: fff00000-000fffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f8200000-f82fffff
	Prefetchable memory behind bridge: 00000000c2000000-00000000c20fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=05, subordinate=06, sec-latency=0
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: fff00000-000fffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01)
	Subsystem: Toshiba America Info Systems Device ff50
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin A routed to IRQ 22
	Region 0: I/O ports at 8440 [size=8]
	Region 1: I/O ports at 8434 [size=4]
	Region 2: I/O ports at 8438 [size=8]
	Region 3: I/O ports at 8430 [size=4]
	Region 4: I/O ports at 8400 [size=16]
	Region 5: Memory at f8609000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff50
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f8404000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff50
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at f8405000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff50
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at f8406000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff50
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at f8407000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff50
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at f8408000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device ff50
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin D routed to IRQ 19
	Region 0: Memory at f8609400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
	Subsystem: Toshiba America Info Systems Device ff50
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Region 0: I/O ports at 8410 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
	Subsystem: Toshiba America Info Systems Device ff50
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at 8420 [size=16]
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Toshiba America Info Systems Device ff50
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin ? routed to IRQ 16
	Region 0: Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
	Subsystem: Toshiba America Info Systems Device ff50
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=64
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: f8300000-f83fffff
	Prefetchable memory behind bridge: fff00000-000fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR+
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
	Subsystem: Toshiba America Info Systems Device ff50
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at f0000000 (64-bit, prefetchable) [size=128M]
	Region 2: Memory at f8100000 (64-bit, non-prefetchable) [size=64K]
	Region 4: I/O ports at 9000 [size=256]
	Region 5: Memory at f8000000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
	Subsystem: Toshiba America Info Systems Device 7919
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 19
	Region 0: Memory at f8110000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

04:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 436c (rev 16)
	Subsystem: Toshiba America Info Systems Device ff50
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 219
	Region 0: Memory at f8200000 (64-bit, non-prefetchable) [size=16K]
	Region 2: I/O ports at a000 [size=256]
	[virtual] Expansion ROM at c2000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

09:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff50
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at f8301000 (32-bit, non-prefetchable) [size=4K]
	Region 1: Memory at f8300000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

09:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02) (prog-if 01)
	Subsystem: Toshiba America Info Systems Device ff50
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at f8300800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

09:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
	Subsystem: Toshiba America Info Systems Device ff50
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 5
	Region 0: Memory at f8302000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

```


dmesg gives me an output that won't even fit in the terminal ie the top part of it gets cut off....

---

### Post by user 123 on 2009-02-10
This is all of the dmesg output that fits in the terminal...

[```
    1.812475] pci 0000:00:05.0: BAR 9: can't allocate resource
[    1.812475] pci 0000:00:07.0: BAR 7: can't allocate resource
[    1.812475] pci 0000:00:07.0: BAR 8: can't allocate resource
[    1.812475] pci 0000:00:07.0: BAR 9: can't allocate resource
[    1.816042] NET: Registered protocol family 8
[    1.816045] NET: Registered protocol family 20
[    1.820040] NetLabel: Initializing
[    1.820040] NetLabel:  domain hash size = 128
[    1.820040] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.820055] NetLabel:  unlabeled traffic allowed by default
[    1.820065] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    1.820070] hpet0: 4 32-bit timers, 14318180 Hz
[    1.821689] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    1.821692]    actual entries 65620
[    1.821853] AppArmor: AppArmor Filesystem Enabled
[    1.821882] ACPI: RTC can wake from S4
[    1.824052] Switched to high resolution mode on CPU 0
[    1.824068] Switched to high resolution mode on CPU 1
[    1.824098] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    1.824101] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[    1.824113] system 00:08: ioport range 0x1080-0x1080 has been reserved
[    1.824117] system 00:08: ioport range 0x8000-0x805f has been reserved
[    1.824125] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[    1.824128] system 00:09: iomem range 0xff800000-0xff80ffff has been reserved
[    1.859423] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.859426] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    1.859431] pci 0000:00:01.0:   MEM window: 0xf8000000-0xf81fffff
[    1.859434] pci 0000:00:01.0:   PREFETCH window: 0x000000f0000000-0x000000f7ffffff
[    1.859439] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    1.859441] pci 0000:00:04.0:   IO window: disabled
[    1.859445] pci 0000:00:04.0:   MEM window: disabled
[    1.859447] pci 0000:00:04.0:   PREFETCH window: disabled
[    1.859451] pci 0000:00:05.0: PCI bridge, secondary bus 0000:03
[    1.859454] pci 0000:00:05.0:   IO window: disabled
[    1.859457] pci 0000:00:05.0:   MEM window: disabled
[    1.859460] pci 0000:00:05.0:   PREFETCH window: disabled
[    1.859464] pci 0000:00:06.0: PCI bridge, secondary bus 0000:04
[    1.859467] pci 0000:00:06.0:   IO window: 0xa000-0xafff
[    1.859471] pci 0000:00:06.0:   MEM window: 0xf8200000-0xf82fffff
[    1.859474] pci 0000:00:06.0:   PREFETCH window: 0x000000c2000000-0x000000c20fffff
[    1.859479] pci 0000:00:07.0: PCI bridge, secondary bus 0000:05
[    1.859481] pci 0000:00:07.0:   IO window: disabled
[    1.859485] pci 0000:00:07.0:   MEM window: disabled
[    1.859487] pci 0000:00:07.0:   PREFETCH window: disabled
[    1.859498] pci 0000:00:14.4: PCI bridge, secondary bus 0000:09
[    1.859501] pci 0000:00:14.4:   IO window: disabled
[    1.859507] pci 0000:00:14.4:   MEM window: 0xf8300000-0xf83fffff
[    1.859512] pci 0000:00:14.4:   PREFETCH window: disabled
[    1.859528] pci 0000:00:04.0: setting latency timer to 64
[    1.859534] pci 0000:00:05.0: setting latency timer to 64
[    1.859539] pci 0000:00:06.0: setting latency timer to 64
[    1.859544] pci 0000:00:07.0: setting latency timer to 64
[    1.859553] bus: 00 index 0 io port: [0, ffff]
[    1.859555] bus: 00 index 1 mmio: [0, ffffffff]
[    1.859557] bus: 01 index 0 io port: [9000, 9fff]
[    1.859560] bus: 01 index 1 mmio: [f8000000, f81fffff]
[    1.859562] bus: 01 index 2 mmio: [f0000000, f7ffffff]
[    1.859564] bus: 01 index 3 mmio: [0, 0]
[    1.859566] bus: 02 index 0 mmio: [0, fff]
[    1.859568] bus: 02 index 1 mmio: [0, fffff]
[    1.859571] bus: 02 index 2 mmio: [0, 0]
[    1.859573] bus: 02 index 3 mmio: [0, 0]
[    1.859575] bus: 03 index 0 mmio: [0, fff]
[    1.859577] bus: 03 index 1 mmio: [0, fffff]
[    1.859579] bus: 03 index 2 mmio: [0, fffff]
[    1.859581] bus: 03 index 3 mmio: [0, 0]
[    1.859584] bus: 04 index 0 io port: [a000, afff]
[    1.859586] bus: 04 index 1 mmio: [f8200000, f82fffff]
[    1.859588] bus: 04 index 2 mmio: [c2000000, c20fffff]
[    1.859591] bus: 04 index 3 mmio: [0, 0]
[    1.859593] bus: 05 index 0 mmio: [0, fff]
[    1.859595] bus: 05 index 1 mmio: [0, fffff]
[    1.859597] bus: 05 index 2 mmio: [0, fffff]
[    1.859599] bus: 05 index 3 mmio: [0, 0]
[    1.859601] bus: 09 index 0 mmio: [0, 0]
[    1.859604] bus: 09 index 1 mmio: [f8300000, f83fffff]
[    1.859606] bus: 09 index 2 mmio: [0, 0]
[    1.859608] bus: 09 index 3 io port: [0, ffff]
[    1.859610] bus: 09 index 4 mmio: [0, ffffffff]
[    1.859622] NET: Registered protocol family 2
[    1.869076] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.869389] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.870172] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.870585] TCP: Hash tables configured (established 131072 bind 65536)
[    1.870589] TCP reno registered
[    1.873115] NET: Registered protocol family 1
[    1.873259] checking if image is initramfs... it is
[    2.576071] Freeing initrd memory: 8000k freed
[    2.576233] Simple Boot Flag at 0x36 set to 0x1
[    2.577465] audit: initializing netlink socket (disabled)
[    2.577481] type=2000 audit(1234250166.576:1): initialized
[    2.583580] highmem bounce pool size: 64 pages
[    2.583586] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.586118] VFS: Disk quotas dquot_6.5.1
[    2.586210] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.586324] msgmni has been set to 1728
[    2.586454] io scheduler noop registered
[    2.586457] io scheduler anticipatory registered
[    2.586459] io scheduler deadline registered
[    2.586471] io scheduler cfq registered (default)
[    2.586581] pci 0000:01:05.0: Boot video device
[    2.586715] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    2.586739] pcieport-driver 0000:00:04.0: found MSI capability
[    2.586765] pci_express 0000:00:04.0:pcie00: allocate port service
[    2.586814] pci_express 0000:00:04.0:pcie02: allocate port service
[    2.586854] pci_express 0000:00:04.0:pcie03: allocate port service
[    2.586924] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    2.586946] pcieport-driver 0000:00:05.0: found MSI capability
[    2.586967] pci_express 0000:00:05.0:pcie00: allocate port service
[    2.587012] pci_express 0000:00:05.0:pcie02: allocate port service
[    2.587057] pci_express 0000:00:05.0:pcie03: allocate port service
[    2.587133] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    2.587155] pcieport-driver 0000:00:06.0: found MSI capability
[    2.587176] pci_express 0000:00:06.0:pcie00: allocate port service
[    2.587222] pci_express 0000:00:06.0:pcie02: allocate port service
[    2.587260] pci_express 0000:00:06.0:pcie03: allocate port service
[    2.587329] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    2.587351] pcieport-driver 0000:00:07.0: found MSI capability
[    2.587372] pci_express 0000:00:07.0:pcie00: allocate port service
[    2.587414] pci_express 0000:00:07.0:pcie02: allocate port service
[    2.587460] pci_express 0000:00:07.0:pcie03: allocate port service
[    2.587781] isapnp: Scanning for PnP cards...
[    2.944289] isapnp: No Plug & Play device found
[    2.986036] hpet_resources: 0xfed00000 is busy
[    2.986128] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.988857] brd: module loaded
[    2.988941] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.989086] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.991685] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.992512] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.992519] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.992522] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.992524] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.992527] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.992895] mice: PS/2 mouse device common for all mice
[    2.993119] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.993144] rtc0: alarms up to one month, hpet irqs
[    2.993300] EISA: Probing bus 0 at eisa.0
[    2.993307] Cannot allocate resource for EISA slot 1
[    2.993332] Cannot allocate resource for EISA slot 8
[    2.993334] EISA: Detected 0 cards.
[    2.993338] cpuidle: using governor ladder
[    2.993340] cpuidle: using governor menu
[    2.993883] TCP cubic registered
[    2.993912] Using IPI No-Shortcut mode
[    2.994142] registered taskstats version 1
[    2.994303]   Magic number: 13:185:268
[    2.994349] tty ttyud: hash matches
[    2.994511] rtc_cmos 00:04: setting system clock to 2009-02-10 07:16:09 UTC (1234250169)
[    2.994515] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.994517] EDD information not available.
[    2.994836] Freeing unused kernel memory: 424k freed
[    2.994905] Write protecting the kernel text: 2580k
[    2.994946] Write protecting the kernel read-only data: 940k
[    3.026155] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    3.155021] fuse init (API version 7.9)
[    3.240188] ACPI: processor limited to max C-state 1
[    3.240260] processor ACPI0007:00: registered as cooling_device0
[    3.240265] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.240326] processor ACPI0007:01: registered as cooling_device1
[    3.243560] thermal LNXTHERM:01: registered as thermal_zone0
[    3.245237] ACPI: Thermal Zone [THRM] (59 C)
[    3.636307] sky2 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.636319] sky2 0000:04:00.0: setting latency timer to 64
[    3.636345] sky2 0000:04:00.0: v1.22 addr 0xf8200000 irq 18 Yukon-2 Extreme rev 2
[    3.636789] sky2 eth0: addr 00:1e:68:7a:0a:3e
[    3.653484] No dock devices found.
[    3.701036] SCSI subsystem initialized
[    3.770624] libata version 3.00 loaded.
[    3.772341] usbcore: registered new interface driver usbfs
[    3.772368] usbcore: registered new interface driver hub
[    3.772416] usbcore: registered new device driver usb
[    3.775724] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.775765] pata_acpi 0000:00:14.1: setting latency timer to 64
[    3.840730] scsi0 : pata_atiixp
[    3.840860] scsi1 : pata_atiixp
[    3.841842] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8420 irq 14
[    3.841845] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8428 irq 15
[    3.868290] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.005513] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-T40N, JT03, max UDMA/33
[    4.021459] ata1.00: configured for UDMA/33
[    4.180733] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T40N  JT03 PQ: 0 ANSI: 5
[    4.180911] ahci 0000:00:12.0: version 3.0
[    4.180932] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    4.180959] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    4.181079] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    4.181082] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part 
[    4.181503] scsi2 : ahci
[    4.182089] scsi3 : ahci
[    4.182177] scsi4 : ahci
[    4.182235] scsi5 : ahci
[    4.182344] ata3: SATA max UDMA/133 abar m1024@0xf8609000 port 0xf8609100 irq 22
[    4.182348] ata4: SATA max UDMA/133 abar m1024@0xf8609000 port 0xf8609180 irq 22
[    4.182352] ata5: SATA max UDMA/133 abar m1024@0xf8609000 port 0xf8609200 irq 22
[    4.182356] ata6: SATA max UDMA/133 abar m1024@0xf8609000 port 0xf8609280 irq 22
[    4.888039] ata3: softreset failed (device not ready)
[    4.888045] ata3: failed due to HW bug, retry pmp=0
[    5.052048] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.455331] ata3.00: ATA-8: TOSHIBA MK1646GSX, LB113M, max UDMA/100
[    5.455336] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    5.455349] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    5.456251] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    5.456254] ata3.00: configured for UDMA/100
[    5.793042] ata4: SATA link down (SStatus 0 SControl 300)
[    6.128050] ata5: SATA link down (SStatus 0 SControl 300)
[    6.464050] ata6: SATA link down (SStatus 0 SControl 300)
[    6.480125] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK1646GS LB11 PQ: 0 ANSI: 5
[    6.480395] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.480411] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    6.480457] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    6.480487] ohci_hcd 0000:00:13.0: irq 16, io mem 0xf8404000
[    6.487167] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    6.487214] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    6.499919] Driver 'sr' needs updating - please use bus_type methods
[    6.512283] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.512289] Uniform CD-ROM driver Revision: 3.20
[    6.512392] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    6.537216] usb usb1: configuration #1 chosen from 1 choice
[    6.537246] hub 1-0:1.0: USB hub found
[    6.537263] hub 1-0:1.0: 2 ports detected
[    6.640296] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    6.640313] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    6.640338] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    6.640363] ohci_hcd 0000:00:13.1: irq 17, io mem 0xf8405000
[    6.696194] usb usb2: configuration #1 chosen from 1 choice
[    6.696223] hub 2-0:1.0: USB hub found
[    6.696239] hub 2-0:1.0: 2 ports detected
[    6.904522] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    6.904537] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    6.904716] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    6.904746] ohci_hcd 0000:00:13.2: irq 18, io mem 0xf8406000
[    6.960149] usb usb3: configuration #1 chosen from 1 choice
[    6.960177] hub 3-0:1.0: USB hub found
[    6.960191] hub 3-0:1.0: 2 ports detected
[    7.040033] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    7.066152] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    7.066165] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    7.066189] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[    7.066205] ohci_hcd 0000:00:13.3: irq 17, io mem 0xf8407000
[    7.120155] usb usb4: configuration #1 chosen from 1 choice
[    7.120183] hub 4-0:1.0: USB hub found
[    7.120197] hub 4-0:1.0: 2 ports detected
[    7.280374] usb 2-1: configuration #1 chosen from 1 choice
[    7.328180] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    7.328195] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    7.328220] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[    7.328238] ohci_hcd 0000:00:13.4: irq 18, io mem 0xf8408000
[    7.384159] usb usb5: configuration #1 chosen from 1 choice
[    7.384187] hub 5-0:1.0: USB hub found
[    7.384201] hub 5-0:1.0: 2 ports detected
[    7.420033] usb 2-2: new full speed USB device using ohci_hcd and address 3
[    7.488197] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    7.488211] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    7.488238] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[    7.488265] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    7.488285] ehci_hcd 0000:00:13.5: debug port 1
[    7.488305] ehci_hcd 0000:00:13.5: irq 19, io mem 0xf8609400
[    7.568031] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    7.568157] usb usb6: configuration #1 chosen from 1 choice
[    7.568184] hub 6-0:1.0: USB hub found
[    7.568193] hub 6-0:1.0: 10 ports detected
[    7.778355] ohci1394 0000:09:01.0: enabling device (0095 -> 0097)
[    7.778368] ohci1394 0000:09:01.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    7.829154] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[f8301000-f83017ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    7.904329] Driver 'sd' needs updating - please use bus_type methods
[    7.904441] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    7.904459] sd 2:0:0:0: [sda] Write Protect is off
[    7.904461] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.904487] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.904552] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    7.904566] sd 2:0:0:0: [sda] Write Protect is off
[    7.904568] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.904592] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.904596]  sda:<3>usb 2-2: device not accepting address 3, error -62
[    7.991159]  sda1 sda2 sda3 sda4 < sda5<3>hub 2-0:1.0: unable to enumerate USB device on port 2
[    8.021041] usb 2-1: USB disconnect, address 2
[    8.031116]  sda6 >
[    8.031339] sd 2:0:0:0: [sda] Attached SCSI disk
[    8.478490] PM: Starting manual resume from disk
[    8.478495] PM: Resume from partition 8:6
[    8.478497] PM: Checking hibernation image.
[    8.478706] PM: Resume from disk failed.
[    8.516045] usb 6-3: new high speed USB device using ehci_hcd and address 2
[    8.519404] kjournald starting.  Commit interval 5 seconds
[    8.519425] EXT3-fs: mounted filesystem with writeback data mode.
[    8.692513] usb 6-3: configuration #1 chosen from 1 choice
[    8.804053] usb 6-4: new high speed USB device using ehci_hcd and address 3
[    8.943792] usb 6-4: configuration #1 chosen from 1 choice
[    9.057043] usb 6-7: new high speed USB device using ehci_hcd and address 4
[    9.100140] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001b240001012037]
[    9.191327] usb 6-7: configuration #1 chosen from 2 choices
[   15.064025] udevd version 124 started
[   15.386644] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.422832] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.500200] Linux agpgart interface v0.103
[   15.640248] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   15.664038] ACPI: Power Button (FF) [PWRF]
[   15.664128] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[   15.664275] ACPI: Lid Switch [LID]
[   15.664323] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   15.696026] ACPI: Power Button (CM) [PWRB]
[   15.704617] ACPI: AC Adapter [ACAD] (on-line)
[   15.768389] ACPI: WMI: Mapper loaded
[   16.219810] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   16.296407] [fglrx] Maximum main memory to use for locked dma buffers: 2767 MBytes.
[   16.296466] [fglrx]   vendor: 1002 device: 791f count: 1
[   16.297204] [fglrx] ioport: bar 4, base 0x9000, size: 0x100
[   16.297219] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.298272] [fglrx] PAT is enabled successfully!
[   16.298316] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors
[   16.576230] ACPI: Battery Slot [BAT1] (battery present)
[   16.579747] acpi device:1c: registered as cooling_device2
[   16.735843] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8410, revision 0
[   16.741449] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1a/device:1b/input/input5
[   16.760049] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   16.920181] usbcore: registered new interface driver libusual
[   17.157608] Initializing USB Mass Storage driver...
[   17.230549] scsi6 : SCSI emulation for USB Mass Storage devices
[   17.286973] usbcore: registered new interface driver usb-storage
[   17.286979] USB Mass Storage support registered.
[   17.286984] usb-storage: device found at 4
[   17.286987] usb-storage: waiting for device to settle before scanning
[   17.287125] Linux video capture interface: v2.00
[   17.289718] sdhci: Secure Digital Host Controller Interface driver
[   17.289722] sdhci: Copyright(c) Pierre Ossman
[   17.294627] sdhci-pci 0000:09:01.2: SDHCI controller found [1217:7120] (rev 2)
[   17.294647] sdhci-pci 0000:09:01.2: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   17.294665] mmc0: Unknown controller version (2). You may experience problems.
[   17.294727] mmc0: SDHCI controller on PCI [0000:09:01.2] using DMA
[   17.626223] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   17.743591] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input7
[   17.828273] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.885423] HDA Intel 0000:01:05.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   17.898553] uvcvideo: Found UVC 1.00 device CNA7137 (04f2:b064)
[   17.900378] input: CNA7137 as /devices/pci0000:00/0000:00:13.5/usb6/6-3/6-3:1.0/input/input8
[   17.930611] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input9
[   18.157889] rtl8187: 8187B chip detected. Support is EXPERIMENTAL, and could damage your
[   18.157892]          hardware, use at your own risk
[   18.158622] phy0: Selected rate control algorithm 'pid'
[   18.362324] phy0: hwaddr 00:16:44:d7:d0:55, RTL8187BvE V0 + rtl8225z2
[   18.362399] usbcore: registered new interface driver rtl8187
[   18.362420] usbcore: registered new interface driver uvcvideo
[   18.362426] USB Video Class driver (v0.1.0)
[   19.055366] lp: driver loaded but no devices found
[   19.211238] Adding 2514132k swap on /dev/sda6.  Priority:-1 extents:1 across:2514132k
[   19.760732] EXT3 FS on sda5, internal journal
[   20.789292] type=1505 audit(1234250186.919:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4396
[   20.853071] type=1505 audit(1234250186.983:3): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=4401
[   21.065600] type=1505 audit(1234250187.195:4): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4405
[   21.065854] type=1505 audit(1234250187.195:5): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4405
[   21.173885] ip_tables: (C) 2000-2006 Netfilter Core Team
[   21.955423] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-60 processors (2 cpu cores) (version 2.20.00)
[   21.955481] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x11
[   21.955486] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[   21.955489] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x13
[   21.955492] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[   22.288349] usb-storage: device scan complete
[   22.289088] scsi 6:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[   22.300729] sd 6:0:0:0: [sdb] 3999743 512-byte hardware sectors (2048 MB)
[   22.301812] sd 6:0:0:0: [sdb] Write Protect is off
[   22.301815] sd 6:0:0:0: [sdb] Mode Sense: 68 00 00 08
[   22.301818] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   22.308402] sd 6:0:0:0: [sdb] 3999743 512-byte hardware sectors (2048 MB)
[   22.309627] sd 6:0:0:0: [sdb] Write Protect is off
[   22.309633] sd 6:0:0:0: [sdb] Mode Sense: 68 00 00 08
[   22.309635] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   22.309640]  sdb: sdb1 sdb2
[   22.313477] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   22.313612] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   22.580797] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   22.747346] apm: BIOS not found.
[   23.018274] ppdev: user-space parallel port driver
[   23.500048] Clocksource tsc unstable (delta = -167279107 ns)
[   29.725299] Bluetooth: Core ver 2.13
[   29.726255] NET: Registered protocol family 31
[   29.726263] Bluetooth: HCI device and connection manager initialized
[   29.726269] Bluetooth: HCI socket layer initialized
[   29.747161] Bluetooth: L2CAP ver 2.11
[   29.747168] Bluetooth: L2CAP socket layer initialized
[   29.765990] Bluetooth: SCO (Voice Link) ver 0.6
[   29.765997] Bluetooth: SCO socket layer initialized
[   29.783877] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.783884] Bluetooth: BNEP filters: protocol multicast
[   29.819007] Bridge firewalling registered
[   30.109194] Bluetooth: RFCOMM socket layer initialized
[   30.109215] Bluetooth: RFCOMM TTY layer initialized
[   30.109218] Bluetooth: RFCOMM ver 1.10
[   34.244373] sky2 eth0: enabling interface
[   34.621487] [fglrx] GART Table is not in FRAME_BUFFER range 
[   34.625952] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   34.625964] [fglrx] Reserved FB block: Unshared offset:7ffc000, size:4000 
[   41.284640] hda-intel: Invalid position buffer, using LPIB read method instead.
[   50.659606] NET: Registered protocol family 17
[   77.610978] CPU0 attaching NULL sched-domain.
[   77.610999] CPU1 attaching NULL sched-domain.
[   77.616074] CPU0 attaching sched-domain:
[   77.616079]  domain 0: span 0-1 level CPU
[   77.616082]   groups: 0 1
[   77.616087] CPU1 attaching sched-domain:
[   77.616089]  domain 0: span 0-1 level CPU
[   77.616091]   groups: 1 0
[  111.165451] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[  111.167205] wlan0: authenticated
[  111.167221] wlan0: associate with AP 00:1b:2f:ab:9d:3a
[  111.169700] wlan0: RX AssocResp from 00:1b:2f:ab:9d:3a (capab=0x431 status=0 aid=1)
[  111.169714] wlan0: associated
[  114.168649] wlan0: deauthenticated
[  115.165031] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[  115.166582] wlan0: authenticated
[  115.166590] wlan0: associate with AP 00:1b:2f:ab:9d:3a
[  115.169214] wlan0: RX ReassocResp from 00:1b:2f:ab:9d:3a (capab=0x431 status=0 aid=1)
[  115.169220] wlan0: associated
[  118.173431] wlan0: deauthenticated
[  119.172098] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[  119.174317] wlan0: authenticated
[  119.174335] wlan0: associate with AP 00:1b:2f:ab:9d:3a
[  119.176763] wlan0: RX ReassocResp from 00:1b:2f:ab:9d:3a (capab=0x431 status=0 aid=1)
[  119.176777] wlan0: associated
[  122.177607] wlan0: deauthenticated
[  123.177095] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[  123.179057] wlan0: authenticated
[  123.179074] wlan0: associate with AP 00:1b:2f:ab:9d:3a
[  123.181808] wlan0: RX ReassocResp from 00:1b:2f:ab:9d:3a (capab=0x431 status=0 aid=1)
[  123.181822] wlan0: associated
[  126.178981] wlan0: deauthenticated
[  127.185055] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[  127.186576] wlan0: authenticated
[  127.186590] wlan0: associate with AP 00:1b:2f:ab:9d:3a
[  127.189349] wlan0: RX ReassocResp from 00:1b:2f:ab:9d:3a (capab=0x431 status=0 aid=1)
[  127.189363] wlan0: associated
[  130.190568] wlan0: deauthenticated
[  131.188054] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[  131.190110] wlan0: authenticated
[  131.190125] wlan0: associate with AP 00:1b:2f:ab:9d:3a
[  131.192741] wlan0: RX ReassocResp from 00:1b:2f:ab:9d:3a (capab=0x431 status=0 aid=1)
[  131.192754] wlan0: associated
[  134.195422] wlan0: deauthenticated
[  135.193119] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[  135.195305] wlan0: authenticated
[  135.195328] wlan0: associate with AP 00:1b:2f:ab:9d:3a
[  135.197798] wlan0: RX ReassocResp from 00:1b:2f:ab:9d:3a (capab=0x431 status=0 aid=1)
[  135.197819] wlan0: associated
[  138.637215] wlan0: deauthenticated
[  139.645176] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[  139.646791] wlan0: authenticated
[  139.646815] wlan0: associate with AP 00:1b:2f:ab:9d:3a
[  139.649520] wlan0: RX ReassocResp from 00:1b:2f:ab:9d:3a (capab=0x431 status=0 aid=1)
[  139.649546] wlan0: associated
[  142.752639] wlan0: deauthenticated
[  143.749076] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[  143.751302] wlan0: authenticated
[  143.751318] wlan0: associate with AP 00:1b:2f:ab:9d:3a
[  143.753806] wlan0: RX ReassocResp from 00:1b:2f:ab:9d:3a (capab=0x431 status=0 aid=1)
[  143.753821] wlan0: associated
[  146.756653] wlan0: deauthenticated
[  147.756044] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[  147.757691] wlan0: authenticated
[  147.757698] wlan0: associate with AP 00:1b:2f:ab:9d:3a
[  147.760191] wlan0: RX ReassocResp from 00:1b:2f:ab:9d:3a (capab=0x431 status=0 aid=1)
[  147.760197] wlan0: associated
[  150.762856] wlan0: deauthenticated
[  151.760054] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[  151.761606] wlan0: authenticated
[  151.761622] wlan0: associate with AP 00:1b:2f:ab:9d:3a
[  151.764235] wlan0: RX ReassocResp from 00:1b:2f:ab:9d:3a (capab=0x431 status=0 aid=1)
[  151.764248] wlan0: associated
[  154.766093] wlan0: deauthenticated
[  155.768056] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[  155.968054] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[  156.168048] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[  156.169695] wlan0: authenticated
[  156.169704] wlan0: associate with AP 00:1b:2f:ab:9d:3a
[  156.172204] wlan0: RX ReassocResp from 00:1b:2f:ab:9d:3a (capab=0x431 status=0 aid=1)
[  156.172220] wlan0: associated
[  159.177182] wlan0: deauthenticated
[  160.176057] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[  160.177728] wlan0: authenticated
[  160.177743] wlan0: associate with AP 00:1b:2f:ab:9d:3a
[  160.180232] wlan0: RX ReassocResp from 00:1b:2f:ab:9d:3a (capab=0x431 status=0 aid=1)
[  160.180244] wlan0: associated
[  163.182509] wlan0: deauthenticated
[  164.184061] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[  164.185635] wlan0: authenticated
[  164.185649] wlan0: associate with AP 00:1b:2f:ab:9d:3a
[  164.188267] wlan0: RX ReassocResp from 00:1b:2f:ab:9d:3a (capab=0x431 status=0 aid=1)
[  164.188280] wlan0: associated
[  167.189474] wlan0: deauthenticated
[  168.188064] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[  168.189723] wlan0: authenticated
[  168.189746] wlan0: associate with AP 00:1b:2f:ab:9d:3a
[  168.194809] wlan0: RX ReassocResp from 00:1b:2f:ab:9d:3a (capab=0x431 status=0 aid=1)
[  168.194822] wlan0: associated
[  168.196103] wlan0: disassociating by local choice (reason=3)
[  171.193588] wlan0: deauthenticated
[  172.192056] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[  172.193832] wlan0: authenticated
[  172.193848] wlan0: associate with AP 00:1b:2f:ab:9d:3a
[  172.196338] wlan0: RX ReassocResp from 00:1b:2f:ab:9d:3a (capab=0x431 status=0 aid=1)
[  172.196351] wlan0: associated
[  172.197860] wlan0: disassociating by local choice (reason=3)
[  203.666284] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[  203.838586] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[  203.838868] wlan0: authenticated
[  203.838878] wlan0: associate with AP 00:1b:2f:ab:9d:3a
[  203.842319] wlan0: RX ReassocResp from 00:1b:2f:ab:9d:3a (capab=0x431 status=0 aid=1)
[  203.842337] wlan0: associated
[  205.017896] padlock: VIA PadLock not detected.
[  211.545955] NET: Registered protocol family 10
[  211.549869] lo: Disabled Privacy Extensions
[  211.552873] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  221.876033] wlan0: no IPv6 routers present

```

---

### Post by PokerFacePenguin on 2009-02-10
> 
dmesg gives me an output that won't even fit in the terminal ie the top part of it gets cut off....


you can do the following when this happens...

lsmod > filename.txt

     greater than character pipes output to filename.txt

lsmod >> filename.txt

      2 ofthese will append the output to a file named filename.txt

---

### Post by user 123 on 2009-02-10
Thanks for that^

In that case dmesg gives:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7ed0000 (usable)
[    0.000000]  BIOS-e820: 00000000b7ed0000 - 00000000b7ee5000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b7ee5000 - 00000000b7ee7000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7ee7000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xb7ed0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3781f000 - 37fef378
[    0.000000] ACPI: RSDP 000F7E00, 0024 (r2 TOSQCI)
[    0.000000] ACPI: XSDT B7ED94A7, 0064 (r1 TOSQCI TOSQCI00  6040000  LTP        0)
[    0.000000] ACPI: FACP B7EE49FA, 00F4 (r3 TOSQCI TOSQCI00  6040000 LOHR    F4240)
[    0.000000] ACPI: DSDT B7ED950B, B4EF (r1 TOSQCI NOrleans  6040000 MSFT  3000001)
[    0.000000] ACPI: FACS B7EE6FC0, 0040
[    0.000000] ACPI: TCPA B7EE4B62, 0032 (r2 TOSQCI TOSQCI00  6040000 LOHR        0)
[    0.000000] ACPI: SSDT B7EE4B94, 0206 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: APIC B7EE4D9A, 0054 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: MCFG B7EE4DEE, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET B7EE4E2A, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: BOOT B7EE4E62, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SLIC B7EE4E8A, 0176 (r1 TOSQCI TOSQCI00  6040000  LTP        0)
[    0.000000] ACPI: DMI detected: Toshiba
[    0.000000] 2046MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [003781f000 - 0037fef378]          RAMDISK ==> [003781f000 - 0037fef378]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f7ec0] 000f7ec0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x000b7ed0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000b7ed0
[    0.000000] On node 0 totalpages: 753263
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 519378 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x43538310 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
[    0.000000] PM: Registered nosave memory: 00000000000ce000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 746641
[    0.000000] Kernel command line: root=UUID=3ddbb193-4e24-4123-9dad-f5fa7e8b5baf ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: Unable to calibrate against PIT
[    0.000000] TSC: using PMTIMER reference calibration
[    0.000000] Detected 1994.440 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2971708k/3013440k available (2576k kernel code, 40336k reserved, 1165k data, 424k init, 2095936k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004020] Calibrating delay loop (skipped), value calculated using timer frequency.. 3988.88 BogoMIPS (lpj=7977760)
[    0.004067] Security Framework initialized
[    0.004084] SELinux:  Disabled at boot.
[    0.004135] AppArmor: AppArmor initialized
[    0.004152] Mount-cache hash table entries: 512
[    0.004530] Initializing cgroup subsys ns
[    0.004534] Initializing cgroup subsys cpuacct
[    0.004546] Initializing cgroup subsys memory
[    0.004580] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004582] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004585] CPU 0(2) -> Core 0
[    0.004597] using C1E aware idle routine
[    0.004617] Checking 'hlt' instruction... OK.
[    0.024021] ACPI: Core revision 20080609
[    0.032731] ACPI: Checking initramfs for custom DSDT
[    0.876228] ENABLING IO-APIC IRQs
[    0.876403] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.880031] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.880031] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.880031] ..... (found apic 0 pin 0) ...
[    0.923353] ....... works.
[    0.923355] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 02
[    0.924031] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3989.99 BogoMIPS (lpj=7979986)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 1(2) -> Core 1
[    1.008258] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 02
[    1.008289] Brought up 2 CPUs
[    1.008292] Total of 2 processors activated (7978.87 BogoMIPS).
[    1.008310] CPU0 attaching sched-domain:
[    1.008313]  domain 0: span 0-1 level CPU
[    1.008316]   groups: 0 1
[    1.008060] System has AMD C1E enabled
[    1.008327] CPU1 attaching sched-domain:
[    1.008330]  domain 0: span 0-1 level CPU
[    1.008335]   groups: 1 0
[    1.008087] Switch to broadcast mode on CPU1
[    1.008409] Switch to broadcast mode on CPU0
[    1.008409] net_namespace: 840 bytes
[    1.008409] Booting paravirtualized kernel on bare hardware
[    1.008409] Time: 17:01:46  Date: 02/10/09
[    1.008409] NET: Registered protocol family 16
[    1.008409] EISA bus registered
[    1.008409] ACPI: bus type pci registered
[    1.008409] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 8
[    1.008409] PCI: MCFG area at e0000000 reserved in E820
[    1.008409] PCI: Using MMCONFIG for extended config space
[    1.008409] PCI: Using configuration type 1 for base access
[    1.008992] ACPI: EC: Look up EC in DSDT
[    1.016949] ACPI: BIOS _OSI(Linux) query ignored via DMI
[    1.024417] ACPI: Interpreter enabled
[    1.024421] ACPI: (supports S0 S3 S4 S5)
[    1.024435] ACPI: Using IOAPIC for interrupt routing
[    1.024606] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    1.524035] ACPI: EC: missing confirmations, switch off interrupt mode.
[    1.552321] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    1.552321] ACPI: EC: driver started in poll mode
[    1.552321] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.552321] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    1.552321] pci 0000:00:04.0: PME# disabled
[    1.552321] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    1.552321] pci 0000:00:05.0: PME# disabled
[    1.552321] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    1.552321] pci 0000:00:06.0: PME# disabled
[    1.552321] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    1.552321] pci 0000:00:07.0: PME# disabled
[    1.552321] PCI: 0000:00:12.0 reg 10 io port: [8440, 8447]
[    1.552321] PCI: 0000:00:12.0 reg 14 io port: [8434, 8437]
[    1.552321] PCI: 0000:00:12.0 reg 18 io port: [8438, 843f]
[    1.552321] PCI: 0000:00:12.0 reg 1c io port: [8430, 8433]
[    1.552321] PCI: 0000:00:12.0 reg 20 io port: [8400, 840f]
[    1.552321] PCI: 0000:00:12.0 reg 24 32bit mmio: [f8609000, f86093ff]
[    1.552321] pci 0000:00:12.0: set SATA to AHCI mode
[    1.552330] PCI: 0000:00:13.0 reg 10 32bit mmio: [f8404000, f8404fff]
[    1.552386] PCI: 0000:00:13.1 reg 10 32bit mmio: [f8405000, f8405fff]
[    1.552441] PCI: 0000:00:13.2 reg 10 32bit mmio: [f8406000, f8406fff]
[    1.552497] PCI: 0000:00:13.3 reg 10 32bit mmio: [f8407000, f8407fff]
[    1.552553] PCI: 0000:00:13.4 reg 10 32bit mmio: [f8408000, f8408fff]
[    1.552628] PCI: 0000:00:13.5 reg 10 32bit mmio: [f8609400, f86094ff]
[    1.552678] pci 0000:00:13.5: supports D1
[    1.552680] pci 0000:00:13.5: supports D2
[    1.552682] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    1.552687] pci 0000:00:13.5: PME# disabled
[    1.552720] PCI: 0000:00:14.0 reg 10 io port: [8410, 841f]
[    1.552782] PCI: 0000:00:14.1 reg 10 io port: [1f0, 1f7]
[    1.552789] PCI: 0000:00:14.1 reg 14 io port: [3f4, 3f7]
[    1.552796] PCI: 0000:00:14.1 reg 18 io port: [0, 7]
[    1.552804] PCI: 0000:00:14.1 reg 1c io port: [0, 3]
[    1.552811] PCI: 0000:00:14.1 reg 20 io port: [8420, 842f]
[    1.552865] PCI: 0000:00:14.2 reg 10 64bit mmio: [f8400000, f8403fff]
[    1.552907] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    1.552911] pci 0000:00:14.2: PME# disabled
[    1.553094] PCI: 0000:01:05.0 reg 10 64bit mmio: [f0000000, f7ffffff]
[    1.553101] PCI: 0000:01:05.0 reg 18 64bit mmio: [f8100000, f810ffff]
[    1.553105] PCI: 0000:01:05.0 reg 20 io port: [9000, 90ff]
[    1.553109] PCI: 0000:01:05.0 reg 24 32bit mmio: [f8000000, f80fffff]
[    1.553119] pci 0000:01:05.0: supports D1
[    1.553121] pci 0000:01:05.0: supports D2
[    1.553138] PCI: 0000:01:05.2 reg 10 64bit mmio: [f8110000, f8113fff]
[    1.553172] PCI: bridge 0000:00:01.0 io port: [9000, 9fff]
[    1.553175] PCI: bridge 0000:00:01.0 32bit mmio: [f8000000, f81fffff]
[    1.553180] PCI: bridge 0000:00:01.0 64bit mmio pref: [f0000000, f7ffffff]
[    1.553232] PCI: bridge 0000:00:04.0 io port: [0, fff]
[    1.553235] PCI: bridge 0000:00:04.0 32bit mmio: [0, fffff]
[    1.553285] PCI: bridge 0000:00:05.0 io port: [0, fff]
[    1.553288] PCI: bridge 0000:00:05.0 32bit mmio: [0, fffff]
[    1.553292] PCI: bridge 0000:00:05.0 64bit mmio pref: [0, fffff]
[    1.553333] PCI: 0000:04:00.0 reg 10 64bit mmio: [f8200000, f8203fff]
[    1.553340] PCI: 0000:04:00.0 reg 18 io port: [a000, a0ff]
[    1.553362] PCI: 0000:04:00.0 reg 30 32bit mmio: [0, 1ffff]
[    1.553381] pci 0000:04:00.0: supports D1
[    1.553383] pci 0000:04:00.0: supports D2
[    1.553385] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.553390] pci 0000:04:00.0: PME# disabled
[    1.553440] PCI: bridge 0000:00:06.0 io port: [a000, afff]
[    1.553443] PCI: bridge 0000:00:06.0 32bit mmio: [f8200000, f82fffff]
[    1.553495] PCI: bridge 0000:00:07.0 io port: [0, fff]
[    1.553498] PCI: bridge 0000:00:07.0 32bit mmio: [0, fffff]
[    1.553502] PCI: bridge 0000:00:07.0 64bit mmio pref: [0, fffff]
[    1.553547] PCI: 0000:09:01.0 reg 10 32bit mmio: [0, fff]
[    1.553555] PCI: 0000:09:01.0 reg 14 32bit mmio: [f8300000, f83007ff]
[    1.553607] pci 0000:09:01.0: supports D1
[    1.553609] pci 0000:09:01.0: supports D2
[    1.553611] pci 0000:09:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.553616] pci 0000:09:01.0: PME# disabled
[    1.553658] PCI: 0000:09:01.2 reg 10 32bit mmio: [f8300800, f83008ff]
[    1.553719] pci 0000:09:01.2: supports D1
[    1.553722] pci 0000:09:01.2: supports D2
[    1.553724] pci 0000:09:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    1.553729] pci 0000:09:01.2: PME# disabled
[    1.553769] PCI: 0000:09:01.3 reg 10 32bit mmio: [f8302000, f8302fff]
[    1.553830] pci 0000:09:01.3: supports D1
[    1.553832] pci 0000:09:01.3: supports D2
[    1.553834] pci 0000:09:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    1.553840] pci 0000:09:01.3: PME# disabled
[    1.553900] pci 0000:00:14.4: transparent bridge
[    1.553908] PCI: bridge 0000:00:14.4 32bit mmio: [f8300000, f83fffff]
[    1.553928] bus 00 -> node 0
[    1.553934] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.554189] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    1.554353] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    1.554516] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    1.554679] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[    1.554862] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    1.554982] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    1.560195] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    1.560377] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    1.560557] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    1.560738] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    1.560921] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    1.561104] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    1.561286] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    1.561468] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    1.561558] Linux Plug and Play Support v0.97 (c) Adam Belay
[    1.561558] pnp: PnP ACPI init
[    1.561558] ACPI: bus type pnp registered
[    1.565389] pnp 00:08: io resource (0x22-0x23) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x2e-0x2f) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x68-0x68) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x6c-0x6c) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x72-0x73) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xb0-0xb1) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x92-0x92) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x220-0x22f) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x40b-0x40b) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x4d0-0x4d1) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x4d6-0x4d6) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x530-0x537) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xc00-0xc01) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xc14-0xc14) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xc50-0xc52) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xc6c-0xc6c) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xc6f-0xc6f) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xcd0-0xcd1) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xcd2-0xcd3) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xcd4-0xcd5) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xcd6-0xcd7) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xcd8-0xcdf) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xf40-0xf47) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x87f-0x87f) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x22-0x23) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x2e-0x2f) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x68-0x68) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x6c-0x6c) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x72-0x73) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xb0-0xb1) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x92-0x92) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x220-0x22f) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x40b-0x40b) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x4d0-0x4d1) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x4d6-0x4d6) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x530-0x537) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xc00-0xc01) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xc14-0xc14) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xc50-0xc52) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xc6c-0xc6c) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xc6f-0xc6f) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xcd0-0xcd1) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xcd2-0xcd3) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xcd4-0xcd5) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xcd6-0xcd7) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xcd8-0xcdf) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xf40-0xf47) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x87f-0x87f) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x22-0x23) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x2e-0x2f) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x68-0x68) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x6c-0x6c) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x72-0x73) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xb0-0xb1) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x92-0x92) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x220-0x22f) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x40b-0x40b) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x4d0-0x4d1) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x4d6-0x4d6) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x530-0x537) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xc00-0xc01) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xc14-0xc14) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xc50-0xc52) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xc6c-0xc6c) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xc6f-0xc6f) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xcd0-0xcd1) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xcd2-0xcd3) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xcd4-0xcd5) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xcd6-0xcd7) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xcd8-0xcdf) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0xf40-0xf47) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:08: io resource (0x87f-0x87f) overlaps 0000:00:07.0 BAR 7 (0x0-0xfff), disabling
[    1.565389] pnp 00:09: mem resource (0xf0609900-0xf06098ff) overlaps 0000:00:01.0 BAR 9 (0xf0000000-0xf7ffffff), disabling
[    1.565389] pnp 00:09: mem resource (0xe0000-0xfffff) overlaps 0000:00:04.0 BAR 8 (0x0-0xfffff), disabling
[    1.565389] pnp 00:09: mem resource (0xe0000-0xfffff) overlaps 0000:00:05.0 BAR 8 (0x0-0xfffff), disabling
[    1.565389] pnp 00:09: mem resource (0xe0000-0xfffff) overlaps 0000:00:05.0 BAR 9 (0x0-0xfffff), disabling
[    1.565389] pnp 00:09: mem resource (0xe0000-0xfffff) overlaps 0000:00:07.0 BAR 8 (0x0-0xfffff), disabling
[    1.565389] pnp 00:09: mem resource (0xe0000-0xfffff) overlaps 0000:00:07.0 BAR 9 (0x0-0xfffff), disabling
[    1.565389] pnp 00:09: mem resource (0xf0609900-0xf06098ff) overlaps 0000:01:05.0 BAR 0 (0xf0000000-0xf7ffffff), disabling
[    1.565389] pnp: PnP ACPI: found 11 devices
[    1.565389] ACPI: ACPI bus type pnp unregistered
[    1.565389] PnPBIOS: Disabled by ACPI PNP
[    1.568204] PCI: Using ACPI for IRQ routing
[    1.568210] pci 0000:00:04.0: BAR 7: can't allocate resource
[    1.568213] pci 0000:00:04.0: BAR 8: can't allocate resource
[    1.568215] pci 0000:00:05.0: BAR 7: can't allocate resource
[    1.568218] pci 0000:00:05.0: BAR 8: can't allocate resource
[    1.568220] pci 0000:00:05.0: BAR 9: can't allocate resource
[    1.568223] pci 0000:00:07.0: BAR 7: can't allocate resource
[    1.568225] pci 0000:00:07.0: BAR 8: can't allocate resource
[    1.568228] pci 0000:00:07.0: BAR 9: can't allocate resource
[    1.572048] NET: Registered protocol family 8
[    1.572051] NET: Registered protocol family 20
[    1.576041] NetLabel: Initializing
[    1.576041] NetLabel:  domain hash size = 128
[    1.576041] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.576055] NetLabel:  unlabeled traffic allowed by default
[    1.576066] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    1.576071] hpet0: 4 32-bit timers, 14318180 Hz
[    1.577697] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    1.577700]    actual entries 65620
[    1.577856] AppArmor: AppArmor Filesystem Enabled
[    1.577885] ACPI: RTC can wake from S4
[    1.580053] Switched to high resolution mode on CPU 0
[    1.580066] Switched to high resolution mode on CPU 1
[    1.580096] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    1.580099] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[    1.580111] system 00:08: ioport range 0x1080-0x1080 has been reserved
[    1.580116] system 00:08: ioport range 0x8000-0x805f has been reserved
[    1.580123] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[    1.580126] system 00:09: iomem range 0xff800000-0xff80ffff has been reserved
[    1.615416] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.615419] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    1.615423] pci 0000:00:01.0:   MEM window: 0xf8000000-0xf81fffff
[    1.615427] pci 0000:00:01.0:   PREFETCH window: 0x000000f0000000-0x000000f7ffffff
[    1.615432] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    1.615434] pci 0000:00:04.0:   IO window: disabled
[    1.615437] pci 0000:00:04.0:   MEM window: disabled
[    1.615440] pci 0000:00:04.0:   PREFETCH window: disabled
[    1.615444] pci 0000:00:05.0: PCI bridge, secondary bus 0000:03
[    1.615447] pci 0000:00:05.0:   IO window: disabled
[    1.615450] pci 0000:00:05.0:   MEM window: disabled
[    1.615453] pci 0000:00:05.0:   PREFETCH window: disabled
[    1.615458] pci 0000:00:06.0: PCI bridge, secondary bus 0000:04
[    1.615461] pci 0000:00:06.0:   IO window: 0xa000-0xafff
[    1.615464] pci 0000:00:06.0:   MEM window: 0xf8200000-0xf82fffff
[    1.615468] pci 0000:00:06.0:   PREFETCH window: 0x000000c2000000-0x000000c20fffff
[    1.615472] pci 0000:00:07.0: PCI bridge, secondary bus 0000:05
[    1.615475] pci 0000:00:07.0:   IO window: disabled
[    1.615478] pci 0000:00:07.0:   MEM window: disabled
[    1.615481] pci 0000:00:07.0:   PREFETCH window: disabled
[    1.615492] pci 0000:00:14.4: PCI bridge, secondary bus 0000:09
[    1.615494] pci 0000:00:14.4:   IO window: disabled
[    1.615500] pci 0000:00:14.4:   MEM window: 0xf8300000-0xf83fffff
[    1.615505] pci 0000:00:14.4:   PREFETCH window: disabled
[    1.615521] pci 0000:00:04.0: setting latency timer to 64
[    1.615527] pci 0000:00:05.0: setting latency timer to 64
[    1.615532] pci 0000:00:06.0: setting latency timer to 64
[    1.615538] pci 0000:00:07.0: setting latency timer to 64
[    1.615547] bus: 00 index 0 io port: [0, ffff]
[    1.615549] bus: 00 index 1 mmio: [0, ffffffff]
[    1.615551] bus: 01 index 0 io port: [9000, 9fff]
[    1.615554] bus: 01 index 1 mmio: [f8000000, f81fffff]
[    1.615556] bus: 01 index 2 mmio: [f0000000, f7ffffff]
[    1.615558] bus: 01 index 3 mmio: [0, 0]
[    1.615560] bus: 02 index 0 mmio: [0, fff]
[    1.615563] bus: 02 index 1 mmio: [0, fffff]
[    1.615565] bus: 02 index 2 mmio: [0, 0]
[    1.615567] bus: 02 index 3 mmio: [0, 0]
[    1.615569] bus: 03 index 0 mmio: [0, fff]
[    1.615571] bus: 03 index 1 mmio: [0, fffff]
[    1.615574] bus: 03 index 2 mmio: [0, fffff]
[    1.615576] bus: 03 index 3 mmio: [0, 0]
[    1.615578] bus: 04 index 0 io port: [a000, afff]
[    1.615580] bus: 04 index 1 mmio: [f8200000, f82fffff]
[    1.615583] bus: 04 index 2 mmio: [c2000000, c20fffff]
[    1.615585] bus: 04 index 3 mmio: [0, 0]
[    1.615587] bus: 05 index 0 mmio: [0, fff]
[    1.615589] bus: 05 index 1 mmio: [0, fffff]
[    1.615591] bus: 05 index 2 mmio: [0, fffff]
[    1.615593] bus: 05 index 3 mmio: [0, 0]
[    1.615596] bus: 09 index 0 mmio: [0, 0]
[    1.615598] bus: 09 index 1 mmio: [f8300000, f83fffff]
[    1.615600] bus: 09 index 2 mmio: [0, 0]
[    1.615602] bus: 09 index 3 io port: [0, ffff]
[    1.615604] bus: 09 index 4 mmio: [0, ffffffff]
[    1.615617] NET: Registered protocol family 2
[    1.625076] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.625388] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.626168] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.626583] TCP: Hash tables configured (established 131072 bind 65536)
[    1.626586] TCP reno registered
[    1.629116] NET: Registered protocol family 1
[    1.629259] checking if image is initramfs... it is
[    2.332115] Freeing initrd memory: 8000k freed
[    2.332283] Simple Boot Flag at 0x36 set to 0x1
[    2.333551] audit: initializing netlink socket (disabled)
[    2.333567] type=2000 audit(1234285305.332:1): initialized
[    2.339671] highmem bounce pool size: 64 pages
[    2.339677] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.342446] VFS: Disk quotas dquot_6.5.1
[    2.342550] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.342664] msgmni has been set to 1728
[    2.342798] io scheduler noop registered
[    2.342800] io scheduler anticipatory registered
[    2.342803] io scheduler deadline registered
[    2.342815] io scheduler cfq registered (default)
[    2.342921] pci 0000:01:05.0: Boot video device
[    2.343068] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    2.343092] pcieport-driver 0000:00:04.0: found MSI capability
[    2.343117] pci_express 0000:00:04.0:pcie00: allocate port service
[    2.343174] pci_express 0000:00:04.0:pcie02: allocate port service
[    2.343222] pci_express 0000:00:04.0:pcie03: allocate port service
[    2.343304] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    2.343325] pcieport-driver 0000:00:05.0: found MSI capability
[    2.343346] pci_express 0000:00:05.0:pcie00: allocate port service
[    2.343401] pci_express 0000:00:05.0:pcie02: allocate port service
[    2.343448] pci_express 0000:00:05.0:pcie03: allocate port service
[    2.343532] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    2.343554] pcieport-driver 0000:00:06.0: found MSI capability
[    2.343575] pci_express 0000:00:06.0:pcie00: allocate port service
[    2.343627] pci_express 0000:00:06.0:pcie02: allocate port service
[    2.343676] pci_express 0000:00:06.0:pcie03: allocate port service
[    2.343758] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    2.343780] pcieport-driver 0000:00:07.0: found MSI capability
[    2.343801] pci_express 0000:00:07.0:pcie00: allocate port service
[    2.343853] pci_express 0000:00:07.0:pcie02: allocate port service
[    2.343903] pci_express 0000:00:07.0:pcie03: allocate port service
[    2.344266] isapnp: Scanning for PnP cards...
[    2.700663] isapnp: No Plug & Play device found
[    2.742967] hpet_resources: 0xfed00000 is busy
[    2.743057] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.745756] brd: module loaded
[    2.745841] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.745975] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.748966] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.749806] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.749813] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.749815] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.749819] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.749822] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.750173] mice: PS/2 mouse device common for all mice
[    2.750365] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.750391] rtc0: alarms up to one month, hpet irqs
[    2.750551] EISA: Probing bus 0 at eisa.0
[    2.750559] Cannot allocate resource for EISA slot 1
[    2.750584] Cannot allocate resource for EISA slot 8
[    2.750586] EISA: Detected 0 cards.
[    2.750590] cpuidle: using governor ladder
[    2.750592] cpuidle: using governor menu
[    2.751141] TCP cubic registered
[    2.751170] Using IPI No-Shortcut mode
[    2.751403] registered taskstats version 1
[    2.751563]   Magic number: 13:489:36
[    2.751774] rtc_cmos 00:04: setting system clock to 2009-02-10 17:01:48 UTC (1234285308)
[    2.751778] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.751780] EDD information not available.
[    2.752103] Freeing unused kernel memory: 424k freed
[    2.752172] Write protecting the kernel text: 2580k
[    2.752214] Write protecting the kernel read-only data: 940k
[    2.783157] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.923758] fuse init (API version 7.9)
[    2.947293] ACPI: processor limited to max C-state 1
[    2.947388] processor ACPI0007:00: registered as cooling_device0
[    2.947397] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.947490] processor ACPI0007:01: registered as cooling_device1
[    2.957601] thermal LNXTHERM:01: registered as thermal_zone0
[    2.959834] ACPI: Thermal Zone [THRM] (33 C)
[    3.377613] No dock devices found.
[    3.389086] usbcore: registered new interface driver usbfs
[    3.389114] usbcore: registered new interface driver hub
[    3.400793] usbcore: registered new device driver usb
[    3.469476] SCSI subsystem initialized
[    3.471823] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.471838] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    3.471891] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    3.471923] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    3.471944] ehci_hcd 0000:00:13.5: debug port 1
[    3.471964] ehci_hcd 0000:00:13.5: irq 19, io mem 0xf8609400
[    3.480460] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.480612] usb usb1: configuration #1 chosen from 1 choice
[    3.480641] hub 1-0:1.0: USB hub found
[    3.480652] hub 1-0:1.0: 10 ports detected
[    3.522044] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.548092] libata version 3.00 loaded.
[    3.688465] ahci 0000:00:12.0: version 3.0
[    3.688486] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.688510] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    3.688602] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    3.688606] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part 
[    3.688999] scsi0 : ahci
[    3.689928] scsi1 : ahci
[    3.690018] scsi2 : ahci
[    3.690083] scsi3 : ahci
[    3.690186] ata1: SATA max UDMA/133 abar m1024@0xf8609000 port 0xf8609100 irq 22
[    3.690190] ata2: SATA max UDMA/133 abar m1024@0xf8609000 port 0xf8609180 irq 22
[    3.690194] ata3: SATA max UDMA/133 abar m1024@0xf8609000 port 0xf8609200 irq 22
[    3.690198] ata4: SATA max UDMA/133 abar m1024@0xf8609000 port 0xf8609280 irq 22
[    3.800044] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    3.976451] usb 1-3: configuration #1 chosen from 1 choice
[    4.088040] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    4.227972] usb 1-4: configuration #1 chosen from 1 choice
[    4.396039] ata1: softreset failed (device not ready)
[    4.396045] ata1: failed due to HW bug, retry pmp=0
[    4.560044] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.983793] ata1.00: ATA-8: TOSHIBA MK1646GSX, LB113M, max UDMA/100
[    4.983796] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.983809] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    4.984706] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    4.984710] ata1.00: configured for UDMA/100
[    5.320054] ata2: SATA link down (SStatus 0 SControl 300)
[    5.656050] ata3: SATA link down (SStatus 0 SControl 300)
[    5.992059] ata4: SATA link down (SStatus 0 SControl 300)
[    6.008135] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1646GS LB11 PQ: 0 ANSI: 5
[    6.008268] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.008285] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    6.008316] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    6.008341] ohci_hcd 0000:00:13.0: irq 16, io mem 0xf8404000
[    6.064190] usb usb2: configuration #1 chosen from 1 choice
[    6.064218] hub 2-0:1.0: USB hub found
[    6.064233] hub 2-0:1.0: 2 ports detected
[    6.168279] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    6.168296] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    6.168320] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    6.168345] ohci_hcd 0000:00:13.1: irq 17, io mem 0xf8405000
[    6.224187] usb usb3: configuration #1 chosen from 1 choice
[    6.224219] hub 3-0:1.0: USB hub found
[    6.224234] hub 3-0:1.0: 2 ports detected
[    6.328565] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    6.328579] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    6.328609] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    6.328635] ohci_hcd 0000:00:13.2: irq 18, io mem 0xf8406000
[    6.384220] usb usb4: configuration #1 chosen from 1 choice
[    6.384250] hub 4-0:1.0: USB hub found
[    6.384266] hub 4-0:1.0: 2 ports detected
[    6.488329] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    6.488346] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    6.488374] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    6.488391] ohci_hcd 0000:00:13.3: irq 17, io mem 0xf8407000
[    6.544153] usb usb5: configuration #1 chosen from 1 choice
[    6.544182] hub 5-0:1.0: USB hub found
[    6.544197] hub 5-0:1.0: 2 ports detected
[    6.648261] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    6.648277] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    6.648301] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    6.648319] ohci_hcd 0000:00:13.4: irq 18, io mem 0xf8408000
[    6.704180] usb usb6: configuration #1 chosen from 1 choice
[    6.704212] hub 6-0:1.0: USB hub found
[    6.704227] hub 6-0:1.0: 2 ports detected
[    6.808491] sky2 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    6.808503] sky2 0000:04:00.0: setting latency timer to 64
[    6.808531] sky2 0000:04:00.0: v1.22 addr 0xf8200000 irq 18 Yukon-2 Extreme rev 2
[    6.808929] sky2 eth0: addr 00:1e:68:7a:0a:3e
[    6.808973] ohci1394 0000:09:01.0: enabling device (0095 -> 0097)
[    6.808986] ohci1394 0000:09:01.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    6.859737] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[f8301000-f83017ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    6.865321] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.865367] pata_acpi 0000:00:14.1: setting latency timer to 64
[    6.870645] scsi4 : pata_atiixp
[    6.870736] scsi5 : pata_atiixp
[    6.871667] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8420 irq 14
[    6.871670] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8428 irq 15
[    6.914906] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    6.932634] Driver 'sd' needs updating - please use bus_type methods
[    6.933345] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    6.933364] sd 0:0:0:0: [sda] Write Protect is off
[    6.933366] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.933391] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.933460] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    6.933475] sd 0:0:0:0: [sda] Write Protect is off
[    6.933477] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.933500] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.933505]  sda: sda1 sda2 sda3 sda4 <<6>ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-T40N, JT03, max UDMA/33
[    7.045485]  sda5<6>ata5.00: configured for UDMA/33
[    7.059497]  sda6 >
[    7.059728] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.207697] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T40N  JT03 PQ: 0 ANSI: 5
[    7.207879] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[    7.229333] Driver 'sr' needs updating - please use bus_type methods
[    7.240492] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    7.240498] Uniform CD-ROM driver Revision: 3.20
[    7.240600] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    7.713591] PM: Starting manual resume from disk
[    7.713595] PM: Resume from partition 8:6
[    7.713597] PM: Checking hibernation image.
[    7.713776] PM: Resume from disk failed.
[    7.770036] kjournald starting.  Commit interval 5 seconds
[    7.770056] EXT3-fs: mounted filesystem with writeback data mode.
[    8.132147] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001b240001012037]
[   14.514613] udevd version 124 started
[   14.861242] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.913872] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.011911] Linux agpgart interface v0.103
[   15.157214] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   15.189028] ACPI: Power Button (FF) [PWRF]
[   15.189119] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[   15.189265] ACPI: Lid Switch [LID]
[   15.189320] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   15.213055] ACPI: Power Button (CM) [PWRB]
[   15.214823] ACPI: AC Adapter [ACAD] (on-line)
[   15.370329] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   15.396231] [fglrx] Maximum main memory to use for locked dma buffers: 2767 MBytes.
[   15.396294] [fglrx]   vendor: 1002 device: 791f count: 1
[   15.397038] [fglrx] ioport: bar 4, base 0x9000, size: 0x100
[   15.397053] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.398064] [fglrx] PAT is enabled successfully!
[   15.398102] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors
[   15.957247] ACPI: Battery Slot [BAT1] (battery present)
[   15.957815] ACPI: WMI: Mapper loaded
[   15.961541] acpi device:1c: registered as cooling_device2
[   16.158123] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1a/device:1b/input/input5
[   16.177065] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   16.458230] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.514580] HDA Intel 0000:01:05.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   16.564764] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8410, revision 0
[   16.580525] Linux video capture interface: v2.00
[   16.656484] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   16.784638] sdhci: Secure Digital Host Controller Interface driver
[   16.784643] sdhci: Copyright(c) Pierre Ossman
[   16.931930] uvcvideo: Found UVC 1.00 device CNA7137 (04f2:b064)
[   16.936549] input: CNA7137 as /devices/pci0000:00/0000:00:13.5/usb1/1-3/1-3:1.0/input/input7
[   16.937459] sdhci-pci 0000:09:01.2: SDHCI controller found [1217:7120] (rev 2)
[   16.937479] sdhci-pci 0000:09:01.2: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   16.937499] mmc0: Unknown controller version (2). You may experience problems.
[   16.937559] mmc0: SDHCI controller on PCI [0000:09:01.2] using DMA
[   17.096546] usbcore: registered new interface driver uvcvideo
[   17.096551] USB Video Class driver (v0.1.0)
[   17.207738] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input8
[   17.252564] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input9
[   17.631763] rtl8187: 8187B chip detected. Support is EXPERIMENTAL, and could damage your
[   17.631766]          hardware, use at your own risk
[   17.632252] phy0: Selected rate control algorithm 'pid'
[   17.850794] phy0: hwaddr 00:16:44:d7:d0:55, RTL8187BvE V0 + rtl8225z2
[   17.850827] usbcore: registered new interface driver rtl8187
[   18.473054] lp: driver loaded but no devices found
[   18.617539] Adding 2514132k swap on /dev/sda6.  Priority:-1 extents:1 across:2514132k
[   19.165871] EXT3 FS on sda5, internal journal
[   20.184186] type=1505 audit(1234285325.876:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4355
[   20.249480] type=1505 audit(1234285325.943:3): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=4360
[   20.458974] type=1505 audit(1234285326.151:4): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4364
[   20.459224] type=1505 audit(1234285326.151:5): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4364
[   20.568939] ip_tables: (C) 2000-2006 Netfilter Core Team
[   21.383802] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-60 processors (2 cpu cores) (version 2.20.00)
[   21.383859] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x11
[   21.383864] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[   21.383867] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x13
[   21.383869] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[   21.873241] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   21.988224] apm: BIOS not found.
[   22.491095] ppdev: user-space parallel port driver
[   23.000038] Clocksource tsc unstable (delta = -300389653 ns)
[   26.496866] Bluetooth: Core ver 2.13
[   26.499453] NET: Registered protocol family 31
[   26.499466] Bluetooth: HCI device and connection manager initialized
[   26.499476] Bluetooth: HCI socket layer initialized
[   26.549701] Bluetooth: L2CAP ver 2.11
[   26.549717] Bluetooth: L2CAP socket layer initialized
[   26.597965] Bluetooth: SCO (Voice Link) ver 0.6
[   26.597981] Bluetooth: SCO socket layer initialized
[   26.644141] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.644158] Bluetooth: BNEP filters: protocol multicast
[   26.725606] Bridge firewalling registered
[   26.901483] Bluetooth: RFCOMM socket layer initialized
[   26.901526] Bluetooth: RFCOMM TTY layer initialized
[   26.901533] Bluetooth: RFCOMM ver 1.10
[   31.085239] sky2 eth0: enabling interface
[   31.516372] [fglrx] GART Table is not in FRAME_BUFFER range 
[   31.520923] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   31.520936] [fglrx] Reserved FB block: Unshared offset:7ffc000, size:4000 
[   38.184646] hda-intel: Invalid position buffer, using LPIB read method instead.
[   47.409750] NET: Registered protocol family 17
[   69.816019] APIC error on CPU1: 00(40)
[   69.816036] APIC error on CPU0: 00(40)
[   73.049861] CPU0 attaching NULL sched-domain.
[   73.049876] CPU1 attaching NULL sched-domain.
[   73.061132] CPU0 attaching sched-domain:
[   73.061140]  domain 0: span 0-1 level CPU
[   73.061145]   groups: 0 1
[   73.061153] CPU1 attaching sched-domain:
[   73.061155]  domain 0: span 0-1 level CPU
[   73.061158]   groups: 1 0
[  150.485416] wlan0: authenticate with AP 00:1b:2f:ab:9d:3a
[  150.487197] wlan0: authenticated
[  150.487212] wlan0: associate with AP 00:1b:2f:ab:9d:3a
[  150.490656] wlan0: RX AssocResp from 00:1b:2f:ab:9d:3a (capab=0x431 status=0 aid=1)
[  150.490667] wlan0: associated
[  150.654654] padlock: VIA PadLock not detected.
[  153.390085] NET: Registered protocol family 10
[  153.400202] lo: Disabled Privacy Extensions
[  153.403697] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  163.969043] wlan0: no IPv6 routers present
```

---

### Post by user 123 on 2009-02-11
Any ideas?

How do you go about learning to interpret all of this?

---

### Post by PokerFacePenguin on 2009-02-12
> **user 123 said:**
> Any ideas?

How do you go about learning to interpret all of this?

Well, that is a pretty deep rabbit hole to put it in MATRIX terms.  You can start here:

[http://www.ubuntupocketguide.com/download2.html](http://www.ubuntupocketguide.com/download2.html)

He might be grepping that file for particular information or any number of things related to your hardware.

This time it was specifically dmesg, a common troubleshooting file.

[http://en.wikipedia.org/wiki/Dmesg](http://en.wikipedia.org/wiki/Dmesg)

Grab the popcorn.... :popcorn: :popcorn: :popcorn:

---

### Post by user 123 on 2009-02-12
Haha thanks man, hopefully it'll get solved soon though, this is getting pretty annoying.

---

### Post by PokerFacePenguin on 2009-02-12
Personally, I believe that it is the driver implementation of the Realtek Semiconductor Corp. RTL8187B Wireless Adapter.  I have heard strange things happening with the realtek drivers (ie, interference from internal realtek interfaces after they were supposedly disabled, etc).  Since you seem to get ok signal under M$ with this card, I tend to believe that you are dealing with a driver issue.  I personally have an external wifi card (alfa awus036h, realtek driver, rt8187) that performs much better under backtrack than ubuntu.  Fire up a copy of bt3 or bt4 beta and check what kind of signal you are getting under it.  The kernel driver probably hasn't quite matured.  I have seen a link where someone built a kernel module under hardy, but I am not sure how it would perform under intrepid so I have been standoffish in loading that up.  I don't use my wifi primarily under ubuntu anyway, that is what backtrack is for.  If you are not concerned with all features, and are primarily aiming for signal, you might be able to get away with loading up a wrapper and sticking the windows driver in there.  It just depends on if ya got a backup and/or are willing to tinker with it.

---

### Post by user 123 on 2009-02-13
I'm not sure on which windows driver to wrap. I've tried a few but they say the hardware isn't present...

---

### Post by PokerFacePenguin on 2009-02-13
> **user 123 said:**
> I'm not sure on which windows driver to wrap. I've tried a few but they say the hardware isn't present...

I believe this is your fix.

[http://ubuntuforums.org/showthread.php?t=900791](http://ubuntuforums.org/showthread.php?t=900791)

using the compat-wireless drivers and 8.10. check out the link above, about post number 40

---

### Post by user 123 on 2009-02-16
Ok now I've hit another snag. I have no idea how to use tarballs. I've managed to extract the folder onto my desktop but now I don't know how to build or install it. Can anyone give me step-by-step instructions on how to?

---

### Post by PokerFacePenguin on 2009-02-16
> **user 123 said:**
> Ok now I've hit another snag. I have no idea how to use tarballs. I've managed to extract the folder onto my desktop but now I don't know how to build or install it. Can anyone give me step-by-step instructions on how to?

Sounds like you are trying to compile something...

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by vcc on 2009-04-24
> **Cosimix said:**
> [B][COLOR=Red][MODIFIED READ THROUGH AGAIN PLEASE]
[/COLOR][/B]
    
[B]sudo iwconfig wlan0 ap[COLOR=Red] XX:XX:XX:XX:XX:XX [COLOR=Black]rate[/COLOR][/COLOR] 11M essid "myssid" txpower 15 power off channel auto 
[/B]


Ciao


Hi all,

This command solved all my wireless problems but after a reboot I need to apply manualy the command again.

How can I make the changes permanent?


Many thanks in advance

---

### Post by Cosimix on 2010-02-02
Hey Man,
I'm back :D

sorry for not turning up for a while, but glad to hear you've fixed your issue. . . 

To make it permanent use this static conf that will be picked up on startup (your PC will automagically connect to this SSID as long as the WX radio toggle is turned on): 

### add the following to /etc/network/interfaces
### make sure you only have one instance of "iface wlan0 inet dhcp"

auto wlan0
iface wlan0 inet dhcp
wireless-essid myssid
wireless-mode managed 
wireless-ap 00:1b:2f:ab:9d:3a
wireless-rate 11M
wireless-txpower 15 
wireless-power off 
wireless-channel auto 
mtu 2274

TIPS: 
1. put the channel number instead of "auto" if you know it.
2. increase the bandwidth from 11M to 54M gradually if your SNR is higher than +10dB
3. find more info by running command "man wireless 7" 

Cheerio
Cosimix

---

