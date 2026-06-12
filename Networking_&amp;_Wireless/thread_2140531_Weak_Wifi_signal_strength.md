---
title: "Weak Wifi signal strength"
date: 2013-04-30
forum: Networking &amp; Wireless
---

### Post by nns2006 on 2013-04-30
Hello,
After reinstalling ubntu12.04 on dell vostro1500, wi-fi signal strength is weak. After removing bcmwl-kernal-source my wifi started working though, but its too weak. I did tried a few suggestions but no success. 
[HTML]wlan0     IEEE 802.11bg  ESSID:"Patanjali"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:406  Invalid misc:691   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.[/HTML]


Thank you for help.

---

### Post by DuckHook on 2013-04-30
Seems okay to me. Why do you feel this is weak?

(Tip) You can use simple code box with hash marks (#) in reply box menu bar (but must be in advanced reply).

---

### Post by kurt18947 on 2013-04-30
I agree with DuckHook.  The signal strength looks fine.  There is an app you might install to monitor your wifi connection.  It's called "wavemon" found in the repositories and runs in a terminal.  i did have an intermittent condition that 'felt' like a slow connection.  It seems my ISP's DNS servers would infrequently become laggy.  I'd click a link and nothing would happen for a couple seconds.  I switched DNS servers and the perceived speed increased.

---

### Post by coldraven on 2013-04-30
The tech guy at my ISP suggested changing  to channel 8 (UK).
I can't remember the exact reason, maybe to avoid the band that mobile phones use.
My wifi seems to work better now. In India I guess the channels will be different.

---

### Post by DuckHook on 2013-04-30
> **coldraven said:**
> The tech guy at my ISP suggested changing to channel 8 (UK).
I can't remember the exact reason, maybe to avoid the band that mobile phones use.
My wifi seems to work better now. In India I guess the channels will be different.

Wireless is a black art that sometimes requires magic wands to optimize or even to just get working. Like you, I don't know much about Indian spectrum rules, but I vaguely recall that the WIFI band was set aside for its purpose internationally and has been adopted almost universally. I don't see why anyone would want to flout this convention, if only in their own self-interest, except possibly nations for whom flouting convention is a point of misplaced pride, like North Korea. I don't believe there is anything special about Channel 8. Your tech friend may have suggested it because it was the least congested channel in your case.

> **kurt18947 said:**
> ...an app ... called "wavemon"...

+1

Very useful for real time look at connection strength and link quality. However, it bears noting that it must be started in sudo mode for scanning option to work.

@OP

Please post output of:```
sudo iwlist wlan0 scanning | grep -iA3 Channel
```...so we can see how crowded your local WIFI environment is. If you are on a congested channel, then even if you have a good connection, you will experience lots of dropped packets and collisions due to competition for the same bandwidth. In densely populated urban centres, it is sometimes impossible to find a free channel, in which case, you have to choose the best one available. This usually means a balance between lowest competing signal strength, number of networks on that channel, amount of Rx/Tx on those networks, and even time of day. On my network I find that things go pear shaped two times a day: when school is out and after supper, when the kiddies start hitting their games.

---

### Post by nns2006 on 2013-04-30
> **DuckHook said:**
> Seems okay to me. Why do you feel this is weak?

(Tip) You can use simple code box with hash marks (#) in reply box menu bar (but must be in advanced reply).


signal strength is only 52%. Isn't it low? It should be atleast more than 85-90 %.
or I am expecting too much?

---

### Post by nns2006 on 2013-04-30
> **coldraven said:**
> The tech guy at my ISP suggested changing  to channel 8 (UK).
I can't remember the exact reason, maybe to avoid the band that mobile phones use.
My wifi seems to work better now. In India I guess the channels will be different.

I am in Vienna and how do you change to channel 8 ? It works good in w7 though.

---

### Post by nns2006 on 2013-04-30
> **DuckHook said:**
> Wireless is a black art that sometimes requires magic wands to optimize or even to just get working. Like you, I don't know much about Indian spectrum rules, but I vaguely recall that the WIFI band was set aside for its purpose internationally and has been adopted almost universally. I don't see why anyone would want to flout this convention, if only in their own self-interest, except possibly nations for whom flouting convention is a point of misplaced pride, like North Korea. I don't believe there is anything special about Channel 8. Your tech friend may have suggested it because it was the least congested channel in your case.



+1

Very useful for real time look at connection strength and link quality. However, it bears noting that it must be started in sudo mode for scanning option to work.

@OP

Please post output of:```
sudo iwlist wlan0 scanning | grep -iA3 Channel
```...so we can see how crowded your local WIFI environment is. If you are on a congested channel, then even if you have a good connection, you will experience lots of dropped packets and collisions due to competition for the same bandwidth. In densely populated urban centres, it is sometimes impossible to find a free channel, in which case, you have to choose the best one available. This usually means a balance between lowest competing signal strength, number of networks on that channel, amount of Rx/Tx on those networks, and even time of day. On my network I find that things go pear shaped two times a day: when school is out and after supper, when the kiddies start hitting their games.

I have my own internet connection in apartment which works better in w7 and was working good prior to reinstalling ubuntu12.04. Now it seems to have fogotten it route to my laptop ;) . 
Here is the otput ```
nityanand@nityanand-Vostro-1500:~$ sudo iwlist wlan0 scanning | grep -iA3 Channel
[sudo] password for nityanand: 
                   [B] Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Patanjali"[/B]
--
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:""
--
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"UPC0044562"
--
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"madLAN"
--
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"home10"
--
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"KARLKREJCI"
--
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"UPC013637"

```
in bold color is mine.

---

### Post by DuckHook on 2013-04-30
> **nns2006 said:**
> signal strength is only 52%. Isn't it low? It should be atleast more than 85-90 %.
or I am expecting too much?

Ah. I see where it may have confused you. That number is not 52%. It is -52dB which is a measure of signal to noise ratio. It is a negative logarithmic number and the closer it gets to 0 the better your signal. -52dB is very good. -70dB would be something to be concerned about.

As suggested by kurt18947, I too highly suggest that you download wavemon. This gives you a graphical and more intuitive look at your connection strength.```
sudo apt-get install wavemon
```

---

### Post by DuckHook on 2013-04-30
> **nns2006 said:**
> Here is the otput...in bold color is mine.

As you more than likely understand by now, there are a number of other networks competing with yours on channel 11. You also want to avoid channels 1 and 6, but otherwise, your local neighbourhood is surprisingly clear (especially for an apartment). Your best bet would be channel 3 or 4. Channel 8 also works. Any channel that is not in conflict with another network, but the further away, the better. Set your router to these clear channels and I suspect that you will instantly see better results. Make sure to use WPA2 encryption. Some routers will call it WPA personal. If so, be sure to select AES cipher.

---

### Post by DuckHook on 2013-04-30
> **nns2006 said:**
> I am in Vienna and how do you change to channel 8 ? It works good in w7 though.

Channels are set in your router, not your computer. If your router channel is changed to 8, your computer should automatically detect this change and set itself at channel 8 as well. There are as many differing routers as birds in the sky so cannot give you any more than general instructions. All routers will allow you to access their firmware through a web page where one of the tabs will allow you to set wireless settings. Choose channel 8 with WPA2 (or WPA personal) encryption and AES cipher. Make sure you use a strong encryption passphrase, then make sure you use exactly the same passphrase in your computer. Case matters. Be sure to save changes to router and reboot it. Same with computer. Let us know how it goes!

---

### Post by kurt18947 on 2013-04-30
> **nns2006 said:**
> signal strength is only 52%. Isn't it low? It should be atleast more than 85-90 %.
or I am expecting too much?

That can also vary with the adapter & its antenna design and software.  I have two small USB WiFi adapters.  One is a generic ralink rt5370 nano adapter using the rt2800usb driver, the other a TrendNet TEW-649UB using a realtek 8192SU chipset and default Ubuntu driver.  The TrendNet adapter will indicate a much stronger signal when plugged into the same USB port and with the same orientation.  The RealTek may indicate 95-100% signal strength, the Ralink 67%.  Whether it's a more efficient driver or higher quality hardware I'm not sure.  It's not strictly device size because I also have an Edimax EW-7811Un adapter which works as well as the Trendnet-RealTek adapter.  Careful shopping can yield very reasonably priced accessories sometimes:).

---

### Post by wildmanne39 on 2013-04-30
This > Link Quality=51/70is showing the link quality not signal strength.

To see signal strength run ```
nm-tool
```then look for your network and signal strength.
Thanks

---

### Post by coldraven on 2013-05-01
> **nns2006 said:**
> I am in Vienna and how do you change to channel 8 ? It works good in w7 though.

I think that I have remembered the reason, it was to avoid interference from DECT cordless phones.

You need to log in to your router go the the wifi section and change the channel.
Don't do this when connected by wifi! Use a cable.

To log in I go to [http://192.168.2.1/](http://192.168.2.1/) in my browser, yours may be different.
See the screenshot



Edit: From the Wikipedia article on DECT phones: [http://en.wikipedia.org/wiki/DECT](http://en.wikipedia.org/wiki/DECT)

> Frequency: 1880 &#8211; 1900 MHz in Europe, 1900 &#8211; 1920 MHz in China, 1893 &#8211; 1906 MHz in Japan, 1910 &#8211; 1930 MHz in Latin America, 1910 &#8211; 1920 MHz in Brazil and 1920 &#8211; 1930 MHz in the US and Canada, US DECT and DECT 6.0  products may NOT be used in Europe as they cause and suffer from  interference with the European cellular networks. Illegal use of such  products are prohibited by European Telecommunications Authorities, and  European DECT products may NOT be used in the US and Canada as they  cause and suffer from interference with US and Canada cellular networks  and for that reason is deemed illegal to use by the [Federal Communication Commission]("http://en.wikipedia.org/wiki/Federal_Communication_Commission") and [Industry Canada]("http://en.wikipedia.org/wiki/Industry_Canada"). As DECT and DECT 6.0 do not operate in the 2.4 GHz [ISM band]("http://en.wikipedia.org/wiki/ISM_band"), they are not subject to the nor cause interference arising in this band from its use by [802.11b]("http://en.wikipedia.org/wiki/IEEE_802.11b-1999") and [802.11g]("http://en.wikipedia.org/wiki/IEEE_802.11g-2003") Wi-Fi, and 2.4 GHz cordless phones. As such, they are sometimes marketed as 'WiFi friendly'.[SUP][[7]]("http://en.wikipedia.org/wiki/DECT#cite_note-7")[/SUP]

---

### Post by nns2006 on 2013-05-09
> **coldraven said:**
> I think that I have remembered the reason, it was to avoid interference from DECT cordless phones.

You need to log in to your router go the the wifi section and change the channel.
Don't do this when connected by wifi! Use a cable.

To log in I go to [http://192.168.2.1/](http://192.168.2.1/) in my browser, yours may be different.
See the screenshot



Edit: From the Wikipedia article on DECT phones: [http://en.wikipedia.org/wiki/DECT](http://en.wikipedia.org/wiki/DECT)

Hello,
sorry for being late to reply.

I tried to change the channel to different values from 3, 4, 6 and 8. But maximum signal strength I can achieve is 65, originally it was 64 for channel 11. Whereas I do see that someone is achieving it 100. where is wrong in my case?
```


    UPC0044562:  Freq 2412 MHz, Rate 54 Mb/s, **Strength 100** WPA WPA2
    
    *Patanjali:      Freq 2462 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2 ; for channel 3
  
    *Patanjali:      Freq 2462 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2 ; for channel 8
  
    *Patanjali:      Freq 2462 MHz, Rate 54 Mb/s, **Strength [COLOR="#FF8C00"]68[/COLOR]** WPA WPA2 ; for channel 4
    
    *Patanjali:      Freq 2462 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2 ; for channel 6


```

Thank you again for helping me through it.

---

### Post by stylintile on 2013-05-09
Hi.
     That signal strength is 51 of 70 or actually 72.8%.

**Edit**  Sorry, I missed the part in DuckHook's post where he explained that.:oops:

---

### Post by wildmanne39 on 2013-05-09
>     UPC0044562:  Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2This is your signal strength to  UPC0044562 network, is that the network you are trying to connect too?

The real question is are you having any problems with your connection? if not your questions so far have been answered?
Thanks

---

### Post by nns2006 on 2013-05-09
> **Wild Man said:**
> This is your signal strength to  UPC0044562 network, is that the network you are trying to connect too?

The real question is are you having any problems with your connection? if not your questions so far have been answered?
Thanks

This is another network. mine is  
  ```
  *Patanjali:      Freq 2462 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2 ; for channel 3 
```

and for this
```
The real question is are you having any problems with your connection?
```
Yes, I do have problem. As I said in the begining of the post signal strenght is weak. sometimes it take ages to load even a google news page(only text). Signal keeps on fluctuating as I can see on panel.

Thanks for the help.

---

### Post by wildmanne39 on 2013-05-09
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by Bucky Ball on 2013-05-09
*Thread moved to **Networking & Wireless***

---

### Post by nns2006 on 2013-05-09
> **Wild Man said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

since the file size is over 140KB, it can't be ploaded. I am pasting it content. 
```

*************** info trace ****************



**** uname -a ****


Linux nityanand-Vostro-1500 3.5.0-29-generic #49~precise1-Ubuntu SMP Wed May 8 00:10:30 UTC 2013 i686 i686 i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"


**** lspci ****


03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Device [1028:0228]
	Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel driver in use: b43-pci-bridge


**** lsusb ****


Bus 002 Device 003: ID 18ec:3299 Arkmicro Technologies Inc. 
Bus 005 Device 002: ID 192f:0416 Avago Technologies, Pte. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**** iwconfig ****


wlan0     IEEE 802.11bg  ESSID:"Patanjali"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:257  Invalid misc:497   Missed beacon:0



**** rfkill ****


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


**** lsmod ****


Module                  Size  Used by
btrfs                 750081  0 
zlib_deflate           26623  1 btrfs
libcrc32c              12544  1 btrfs
ufs                    78132  0 
qnx4                   13192  0 
hfsplus                83581  0 
hfs                    49480  0 
minix                  31538  0 
ntfs                  100207  0 
msdos                  17133  0 
jfs                   175096  0 
xfs                   754444  0 
reiserfs              235181  0 
ext2                   67991  0 
pci_stub               12551  1 
vboxpci                22911  0 
vboxnetadp             13329  0 
vboxnetflt             27241  0 
vboxdrv               252211  3 vboxpci,vboxnetadp,vboxnetflt
snd_hda_codec_idt      60238  1 
parport_pc             32115  0 
ppdev                  12850  0 
binfmt_misc            17293  1 
xt_hl                  12466  6 
ip6t_rt                12474  3 
nf_conntrack_ipv6      13750  7 
nf_defrag_ipv6         13176  1 nf_conntrack_ipv6
ipt_REJECT             12513  1 
xt_LOG                 17238  9 
xt_limit               12542  12 
xt_tcpudp              12532  18 
xt_addrtype            12597  4 
xt_state               12515  14 
ip6table_filter        12712  1 
ip6_tables             22382  2 ip6t_rt,ip6table_filter
snd_hda_intel          32983  3 
nf_conntrack_netbios_ns    12586  0 
nf_conntrack_broadcast    12542  1 nf_conntrack_netbios_ns
snd_hda_codec         116477  2 snd_hda_codec_idt,snd_hda_intel
snd_usb_audio         106622  1 
nf_nat_ftp             12596  0 
r852                   17906  0 
nf_nat                 20645  1 nf_nat_ftp
arc4                   12474  2 
snd_usbmidi_lib        24590  1 snd_usb_audio
sm_common              16773  1 r852
nf_conntrack_ipv4      14123  9 nf_nat
snd_hwdep              13277  2 snd_hda_codec,snd_usb_audio
nand                   49703  2 r852,sm_common
nf_defrag_ipv4         12650  1 nf_conntrack_ipv4
snd_pcm                81124  3 snd_hda_intel,snd_hda_codec,snd_usb_audio
nand_ids                8548  1 nand
coretemp               13362  0 
nf_conntrack_ftp       13184  1 nf_nat_ftp
i915                  479158  3 
snd_seq_midi           13133  0 
mtd                    38671  2 sm_common,nand
b43                   351631  0 
nf_conntrack           66862  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_rawmidi            25426  2 snd_usbmidi_lib,snd_seq_midi
nand_bch               13004  1 nand
iptable_filter         12707  1 
joydev                 17394  0 
snd_seq_midi_event     14476  1 snd_seq_midi
bch                    21768  1 nand_bch
ip_tables              18107  1 iptable_filter
uvcvideo               72249  0 
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
dell_laptop            17210  0 
r592                   17809  0 
drm_kms_helper         47459  1 i915
drm                   240232  4 i915,drm_kms_helper
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
videobuf2_core         32212  1 uvcvideo
memstick               15886  1 r592
dcdbas                 14099  1 dell_laptop
microcode              18396  0 
gpio_ich               13160  0 
videodev              100265  2 uvcvideo,videobuf2_core
dell_wmi               12602  0 
videobuf2_vmalloc      12757  1 uvcvideo
nand_ecc               13106  1 nand
sparse_keymap          13659  1 dell_wmi
videobuf2_memops       13213  1 videobuf2_vmalloc
snd                    62675  19 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_usbmidi_lib,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              475546  1 b43
x_tables               22012  12 xt_hl,ip6t_rt,ipt_REJECT,xt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
soundcore              14636  1 snd
mac_hid                13078  0 
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13317  1 i915
psmouse                91381  0 
cfg80211              181041  2 b43,mac80211
video                  19117  1 i915
lpc_ich                16993  0 
wmi                    18745  1 dell_wmi
serio_raw              13032  0 
ssb_hcd                12782  0 
lp                     17456  0 
bcma                   34573  1 b43
parport                40931  3 parport_pc,ppdev,lp
b44                    31365  0 
hid_generic            12485  0 
sdhci_pci              18263  0 
sdhci                  32293  1 sdhci_pci
firewire_ohci          36110  0 
firewire_core          61957  1 firewire_ohci
crc_itu_t              12628  1 firewire_core
usbhid                 46054  0 
hid                    82511  2 hid_generic,usbhid
ssb                    50757  3 b43,ssb_hcd,b44


**** nm-tool ****



NetworkManager Tool

State: unknown



**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"Patanjali"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000041870ab73
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 0009506174616E6A616C69
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000378e7615e
                    Extra: Last beacon: 1836ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050600000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0504001E127A
                    IE: Unknown: DD07000C4307000000
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"UPC0044562"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002252e3d919d
                    Extra: Last beacon: 1660ms ago
                    IE: Unknown: 000A55504330303434353632
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"KARLKREJCI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012ee647f18c
                    Extra: Last beacon: 1808ms ago
                    IE: Unknown: 000A4B41524C4B52454A4349
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B000103104700100A73CEE1C2AF47E1B3F0034909FE71661021000D4E4554474541522C20496E632E10230009574E5231303030763310240009574E523130303076331042000538333235381054000800060050F204000110110009574E52313030307633100800020084
                    IE: Unknown: DD090010180200F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401080000000000000000000000000000000000000000
          Cell 05 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"schlazi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007c5450f2d7
                    Extra: Last beacon: 1728ms ago
                    IE: Unknown: 00077363686C617A69
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402080800000000000000000000000000000000000000
                    IE: Unknown: 3D1602080800000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD7A0050F204104A0001101044000102103B0001031047001000000000000010000000841B5E72FD9A102100044E54475210230009776E72323030307633102400016E104200046E6F6E651054000800060050F204000110110016574E5232303030763328576972656C65737320415029100800020086103C000103
          Cell 06 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"home10"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005b0f2fc5183
                    Extra: Last beacon: 1016ms ago
                    IE: Unknown: 0006686F6D653130
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"madLAN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000014576e26237
                    Extra: Last beacon: 1184ms ago
                    IE: Unknown: 00066D61644C414E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 050C010300000000000000000000
                    IE: Unknown: 2A0107
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"UPC013637"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000091bc3d6006
                    Extra: Last beacon: 1164ms ago
                    IE: Unknown: 0009555043303133363337
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR90"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000007001cacaed3
                    Extra: Last beacon: 40ms ago



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1


**** blacklist.conf ****


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


**** dmesg ****


[56707.758189] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[56833.710350] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[56833.711327] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[56959.661320] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[57211.666852] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[57211.670272] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[57337.721312] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[57337.722429] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[57429.182156] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=108.168.209.242 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=50 ID=5082 DF PROTO=TCP SPT=80 DPT=39767 WINDOW=15 RES=0x00 ACK URGP=0 
[57463.648771] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[57589.646873] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[57589.647774] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[57715.666227] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[57715.667268] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[57841.665245] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[57841.666208] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[57967.664426] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[57967.665389] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[58093.663761] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[58093.664550] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[58219.662896] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[58219.663902] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[58345.661994] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[58345.663013] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[58368.915295] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=105 TOS=0x00 PREC=0x00 TTL=49 ID=32812 PROTO=TCP SPT=443 DPT=37097 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[58372.604082] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.113 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=47684 PROTO=TCP SPT=443 DPT=33125 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[58378.915294] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=105 TOS=0x00 PREC=0x00 TTL=49 ID=32812 PROTO=TCP SPT=443 DPT=37097 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[58382.603976] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.113 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=47684 PROTO=TCP SPT=443 DPT=33125 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[58471.661316] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[58471.662304] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[58597.660489] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[58597.661475] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[58723.660702] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[58844.279352] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=91.189.94.12 DST=192.168.0.10 LEN=1214 TOS=0x00 PREC=0x00 TTL=55 ID=63342 DF PROTO=TCP SPT=80 DPT=34903 WINDOW=571 RES=0x00 ACK PSH URGP=0 
[58848.481832] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=184.168.230.128 DST=192.168.0.10 LEN=1049 TOS=0x00 PREC=0x00 TTL=51 ID=6631 DF PROTO=TCP SPT=80 DPT=49271 WINDOW=139 RES=0x00 ACK PSH URGP=0 
[58849.666646] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[58849.667620] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[58857.571666] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=1470 TOS=0x00 PREC=0x00 TTL=48 ID=11178 PROTO=TCP SPT=80 DPT=49127 WINDOW=992 RES=0x00 ACK URGP=0 
[58861.759433] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.136 DST=192.168.0.10 LEN=1470 TOS=0x00 PREC=0x00 TTL=48 ID=4983 PROTO=TCP SPT=80 DPT=49394 WINDOW=1002 RES=0x00 ACK URGP=0 
[58867.571764] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=1470 TOS=0x00 PREC=0x00 TTL=48 ID=11178 PROTO=TCP SPT=80 DPT=49127 WINDOW=992 RES=0x00 ACK URGP=0 
[58871.760494] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.136 DST=192.168.0.10 LEN=1470 TOS=0x00 PREC=0x00 TTL=48 ID=4983 PROTO=TCP SPT=80 DPT=49394 WINDOW=1002 RES=0x00 ACK URGP=0 
[58975.658283] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[58975.659193] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[59101.657735] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[59101.658660] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[59175.362172] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.102 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=45764 PROTO=TCP SPT=443 DPT=37089 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[59185.362411] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.102 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=45764 PROTO=TCP SPT=443 DPT=37089 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[59193.884799] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.68.120 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=42 ID=24663 PROTO=TCP SPT=443 DPT=55721 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[59195.362541] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.102 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=45764 PROTO=TCP SPT=443 DPT=37089 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[59203.883942] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.68.120 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=42 ID=24664 PROTO=TCP SPT=443 DPT=55721 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[59227.657063] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[59227.658070] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[59353.656283] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[59353.657330] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[59392.555456] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.139 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=54071 PROTO=TCP SPT=443 DPT=47344 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[59402.555498] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.139 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=54071 PROTO=TCP SPT=443 DPT=47344 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[59412.555545] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.139 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=54071 PROTO=TCP SPT=443 DPT=47344 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[59479.655641] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[59479.656596] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[59605.654861] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[59605.655903] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[59731.654300] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[59731.655225] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[59857.653266] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[59857.654177] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[59983.652421] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[59983.653455] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[60109.652650] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[60235.650929] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[60235.651961] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[60361.651047] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[60487.649464] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[60487.650448] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[60613.648747] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[60613.649706] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[60739.647926] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[60739.648805] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[60865.647044] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[60865.648099] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[60991.646226] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[60991.647202] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[61117.645533] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[61117.646534] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[61243.644617] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[61243.645520] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[61369.643784] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[61369.644715] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[61495.642905] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[61495.643870] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[61621.642121] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[61621.643118] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[61747.641368] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[61747.642417] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[61873.640305] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[61873.641317] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[61999.639563] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[62125.638764] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[62125.639703] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[62251.638900] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[62377.637067] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[62377.638052] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[62503.636348] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[62503.637321] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[62629.635487] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[62629.636498] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[62755.634662] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[62755.635688] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[62881.634020] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[62881.635014] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[63007.636210] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[63007.637154] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[63133.632629] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[63133.633488] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[63259.631841] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[63259.632816] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[63385.631146] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[63385.632175] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[63637.629712] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[63637.630734] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[63763.629028] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[63763.629966] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[63889.628284] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[63889.629341] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[64015.627678] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[64015.628767] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[64141.627010] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[64141.628085] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[64267.626148] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[64267.627079] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[64393.625497] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[64393.626519] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[64519.624703] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[64519.625720] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[64645.623818] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[64645.624764] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[64716.898832] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=7126 PROTO=TCP SPT=443 DPT=49775 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[64726.899534] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=7126 PROTO=TCP SPT=443 DPT=49775 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[64736.899579] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=7126 PROTO=TCP SPT=443 DPT=49775 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[64872.133291] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.100 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=61465 PROTO=TCP SPT=443 DPT=53508 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[64873.971468] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.139 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=26991 PROTO=TCP SPT=443 DPT=47738 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[64882.133119] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.100 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=61465 PROTO=TCP SPT=443 DPT=53508 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[64892.134942] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.100 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=61465 PROTO=TCP SPT=443 DPT=53508 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[64893.970544] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.139 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=26991 PROTO=TCP SPT=443 DPT=47738 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[64897.622217] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[64897.623231] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[65009.453702] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=54.244.5.212 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=48 ID=25391 DF PROTO=TCP SPT=80 DPT=45509 WINDOW=94 RES=0x00 ACK URGP=0 
[65023.621587] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[65023.622567] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[65149.620820] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[65149.621784] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[65275.619973] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[65297.713992] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.139 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=45508 PROTO=TCP SPT=443 DPT=47986 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[65307.713356] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.139 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=45509 PROTO=TCP SPT=443 DPT=47986 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[65317.713776] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.139 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=45510 PROTO=TCP SPT=443 DPT=47986 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[65401.619303] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[65401.620275] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[65527.618509] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[65527.619435] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[65653.617766] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[65653.618831] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[65779.617271] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[65779.618199] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[65905.617523] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[66031.615755] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[66031.616650] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[66157.614869] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[66157.615780] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[66283.614022] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[66283.614961] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[66409.613273] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[66409.614213] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[66535.612405] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[66535.613412] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[66661.611589] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[66661.612608] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[66736.352142] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.113 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=52446 PROTO=TCP SPT=443 DPT=34401 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[66746.422273] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.113 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=52446 PROTO=TCP SPT=443 DPT=34401 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[66756.352595] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.113 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=52446 PROTO=TCP SPT=443 DPT=34401 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[66787.610694] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[66787.611651] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[66913.609852] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[66913.610882] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[67039.609183] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[67039.610126] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[67044.846310] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.120 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=56453 PROTO=TCP SPT=443 DPT=41073 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[67054.846461] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.120 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=56453 PROTO=TCP SPT=443 DPT=41073 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[67064.846498] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.120 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=56453 PROTO=TCP SPT=443 DPT=41073 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[67157.025474] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=8309 PROTO=TCP SPT=443 DPT=35652 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[67165.608433] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[67165.609379] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[67167.026024] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=8309 PROTO=TCP SPT=443 DPT=35652 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[67291.609416] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[67291.610268] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[67417.606912] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[67417.607813] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[67543.606055] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[67543.606960] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[67669.605217] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[67669.606207] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[67795.604560] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[67795.605454] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[67921.609228] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[68047.602989] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[68047.604031] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[68173.602392] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[68173.603421] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[68299.601617] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[68299.602505] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[68425.600748] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[68425.601699] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[68516.314240] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=2582 PROTO=TCP SPT=443 DPT=38531 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[68516.314472] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.139 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=24619 PROTO=TCP SPT=443 DPT=48441 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[68526.308099] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.139 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=24619 PROTO=TCP SPT=443 DPT=48441 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[68526.308264] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=2582 PROTO=TCP SPT=443 DPT=38531 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[68536.319327] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.139 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=24619 PROTO=TCP SPT=443 DPT=48441 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[68536.319577] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=2582 PROTO=TCP SPT=443 DPT=38531 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[68543.331450] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=46 ID=17704 PROTO=TCP SPT=443 DPT=35749 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[68544.061739] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.100 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=42349 PROTO=TCP SPT=443 DPT=54240 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[68551.600252] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[68551.601216] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[68553.269434] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=46 ID=17704 PROTO=TCP SPT=443 DPT=35749 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[68564.021977] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.100 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=42349 PROTO=TCP SPT=443 DPT=54240 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[68577.972615] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=74.125.218.116 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=54 ID=24256 DF PROTO=TCP SPT=80 DPT=35571 WINDOW=365 RES=0x00 ACK URGP=0 
[68677.625370] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[68677.626453] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[68796.020292] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=18006 PROTO=TCP SPT=443 DPT=35806 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[68803.621167] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[68803.622147] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[68806.054558] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=18006 PROTO=TCP SPT=443 DPT=35806 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[68832.802924] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=64.15.113.81 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=59 ID=37123 DF PROTO=TCP SPT=80 DPT=53231 WINDOW=411 RES=0x00 ACK URGP=0 
[68832.804543] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=64.15.113.81 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=59 ID=7306 DF PROTO=TCP SPT=80 DPT=53230 WINDOW=320 RES=0x00 ACK URGP=0 
[68852.802935] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=64.15.113.81 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=59 ID=37125 DF PROTO=TCP SPT=80 DPT=53231 WINDOW=411 RES=0x00 ACK URGP=0 
[68852.804806] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=64.15.113.81 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=59 ID=7308 DF PROTO=TCP SPT=80 DPT=53230 WINDOW=320 RES=0x00 ACK URGP=0 
[68862.802580] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=64.15.113.81 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=59 ID=37126 DF PROTO=TCP SPT=80 DPT=53231 WINDOW=411 RES=0x00 ACK URGP=0 
[68862.806607] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=64.15.113.81 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=59 ID=7309 DF PROTO=TCP SPT=80 DPT=53230 WINDOW=320 RES=0x00 ACK URGP=0 
[68872.802046] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=64.15.113.81 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=59 ID=37127 DF PROTO=TCP SPT=80 DPT=53231 WINDOW=411 RES=0x00 ACK URGP=0 
[68872.804097] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=64.15.113.81 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=59 ID=7310 DF PROTO=TCP SPT=80 DPT=53230 WINDOW=320 RES=0x00 ACK URGP=0 
[68882.804194] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=64.15.113.81 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=59 ID=7311 DF PROTO=TCP SPT=80 DPT=53230 WINDOW=320 RES=0x00 ACK URGP=0 
[68902.802420] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=64.15.113.81 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=59 ID=37130 DF PROTO=TCP SPT=80 DPT=53231 WINDOW=411 RES=0x00 ACK URGP=0 
[68929.598480] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[69018.238612] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=19870 PROTO=TCP SPT=443 DPT=35857 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69028.238463] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=19870 PROTO=TCP SPT=443 DPT=35857 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69038.238373] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=19870 PROTO=TCP SPT=443 DPT=35857 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69055.598355] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[69055.599289] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[69181.597654] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[69181.598539] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[69229.663496] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.139 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=46 ID=52892 PROTO=TCP SPT=443 DPT=48593 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69231.260616] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=26993 PROTO=TCP SPT=443 DPT=38684 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69239.663923] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.139 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=46 ID=52892 PROTO=TCP SPT=443 DPT=48593 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69241.262414] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=26993 PROTO=TCP SPT=443 DPT=38684 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69249.662249] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.139 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=46 ID=52892 PROTO=TCP SPT=443 DPT=48593 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69251.260717] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=26993 PROTO=TCP SPT=443 DPT=38684 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69260.059625] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=18129 PROTO=TCP SPT=443 DPT=35913 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69260.796713] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=5824 PROTO=TCP SPT=443 DPT=50675 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69261.570218] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=74.125.218.178 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=55 ID=26385 DF PROTO=TCP SPT=80 DPT=60642 WINDOW=320 RES=0x00 ACK URGP=0 
[69270.011644] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=18129 PROTO=TCP SPT=443 DPT=35913 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69280.011778] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=18129 PROTO=TCP SPT=443 DPT=35913 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69307.597028] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[69429.901046] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=38614 PROTO=TCP SPT=443 DPT=52383 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69433.597727] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[69433.598887] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[69439.901601] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=38614 PROTO=TCP SPT=443 DPT=52383 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69449.900735] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=38614 PROTO=TCP SPT=443 DPT=52383 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69473.489929] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=10965 PROTO=TCP SPT=443 DPT=35978 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69483.490349] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=10965 PROTO=TCP SPT=443 DPT=35978 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69493.490495] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=10965 PROTO=TCP SPT=443 DPT=35978 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69559.616520] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[69600.282989] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=796 PROTO=TCP SPT=443 DPT=38777 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69610.280841] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=796 PROTO=TCP SPT=443 DPT=38777 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69620.390331] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=796 PROTO=TCP SPT=443 DPT=38777 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69685.595286] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[69685.596305] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[69779.516422] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.100 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=55443 PROTO=TCP SPT=443 DPT=54532 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69789.518123] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.100 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=55443 PROTO=TCP SPT=443 DPT=54532 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69799.516186] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.100 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=55443 PROTO=TCP SPT=443 DPT=54532 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69811.597772] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[69828.980895] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=27530 PROTO=TCP SPT=443 DPT=36061 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69839.009406] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=27530 PROTO=TCP SPT=443 DPT=36061 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69848.980900] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=27530 PROTO=TCP SPT=443 DPT=36061 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69894.491228] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.113 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=9053 PROTO=TCP SPT=443 DPT=34914 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[69937.594258] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[69937.595256] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[70025.297543] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=48660 PROTO=TCP SPT=443 DPT=36100 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[70035.298150] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=48660 PROTO=TCP SPT=443 DPT=36100 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[70045.297742] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=48660 PROTO=TCP SPT=443 DPT=36100 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[70063.594457] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[70169.247906] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=37782 PROTO=TCP SPT=443 DPT=50874 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[70179.253651] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=37783 PROTO=TCP SPT=443 DPT=50874 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[70189.592988] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[70296.324679] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.120 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=36044 PROTO=TCP SPT=443 DPT=41555 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[70306.324568] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.120 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=36044 PROTO=TCP SPT=443 DPT=41555 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[70315.594513] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[70315.595491] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[70316.335213] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.120 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=36044 PROTO=TCP SPT=443 DPT=41555 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[70441.594259] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[70441.595137] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[70567.592419] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[70567.593409] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[70628.570868] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=18753 PROTO=TCP SPT=443 DPT=52597 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[70638.570956] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=18753 PROTO=TCP SPT=443 DPT=52597 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[70648.570612] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=18753 PROTO=TCP SPT=443 DPT=52597 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[70693.590696] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[70693.591591] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[70716.105160] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=35397 PROTO=TCP SPT=443 DPT=52648 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[70726.081459] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=35397 PROTO=TCP SPT=443 DPT=52648 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[70726.222614] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=46 ID=58248 PROTO=TCP SPT=443 DPT=52647 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[70736.081805] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=35397 PROTO=TCP SPT=443 DPT=52648 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[70736.222653] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=46 ID=58248 PROTO=TCP SPT=443 DPT=52647 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[70746.074205] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=51407 PROTO=TCP SPT=443 DPT=52661 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[70756.075430] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=51407 PROTO=TCP SPT=443 DPT=52661 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[70766.076148] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=51407 PROTO=TCP SPT=443 DPT=52661 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[70819.589801] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[70819.590769] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[70945.589070] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[70945.590091] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[71071.588357] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[71071.589397] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[71197.587682] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[71197.588533] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[71323.587735] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[71449.586075] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[71449.586973] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[71542.850046] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=10609 PROTO=TCP SPT=443 DPT=39185 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[71550.704420] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=29733 PROTO=TCP SPT=443 DPT=36402 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[71552.849717] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=10609 PROTO=TCP SPT=443 DPT=39185 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[71560.707151] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=29733 PROTO=TCP SPT=443 DPT=36402 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[71562.849775] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=10609 PROTO=TCP SPT=443 DPT=39185 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[71563.065495] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=64.15.113.81 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=59 ID=43020 DF PROTO=TCP SPT=80 DPT=53823 WINDOW=320 RES=0x00 ACK URGP=0 
[71570.706408] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=29733 PROTO=TCP SPT=443 DPT=36402 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[71573.066108] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=64.15.113.81 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=59 ID=43021 DF PROTO=TCP SPT=80 DPT=53823 WINDOW=320 RES=0x00 ACK URGP=0 
[71583.065332] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=64.15.113.81 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=59 ID=43022 DF PROTO=TCP SPT=80 DPT=53823 WINDOW=320 RES=0x00 ACK URGP=0 
[71593.064306] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=64.15.113.81 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=59 ID=43023 DF PROTO=TCP SPT=80 DPT=53823 WINDOW=320 RES=0x00 ACK URGP=0 
[71603.064462] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=64.15.113.81 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=59 ID=43024 DF PROTO=TCP SPT=80 DPT=53823 WINDOW=320 RES=0x00 ACK URGP=0 
[71613.064871] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=64.15.113.81 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=59 ID=43025 DF PROTO=TCP SPT=80 DPT=53823 WINDOW=320 RES=0x00 ACK URGP=0 
[71623.064216] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=64.15.113.81 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=59 ID=43026 DF PROTO=TCP SPT=80 DPT=53823 WINDOW=320 RES=0x00 ACK URGP=0 
[71625.303625] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=37994 PROTO=TCP SPT=443 DPT=51197 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[71643.064661] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=64.15.113.81 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=59 ID=43028 DF PROTO=TCP SPT=80 DPT=53823 WINDOW=320 RES=0x00 ACK URGP=0 
[71701.584626] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[71701.585563] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[71753.903227] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=74.125.218.144 DST=192.168.0.10 LEN=1500 TOS=0x00 PREC=0x00 TTL=55 ID=40779 DF PROTO=TCP SPT=80 DPT=56034 WINDOW=274 RES=0x00 ACK URGP=0 
[71792.376162] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=52343 PROTO=TCP SPT=443 DPT=36500 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[71802.376212] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.93 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=52344 PROTO=TCP SPT=443 DPT=36500 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[71827.583961] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[71953.583423] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[71953.584429] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[72079.582800] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[72079.583705] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[72173.617080] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.148 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=46140 PROTO=TCP SPT=443 DPT=45931 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[72183.617327] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.148 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=46140 PROTO=TCP SPT=443 DPT=45931 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[72193.617137] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.148 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=46140 PROTO=TCP SPT=443 DPT=45931 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[72205.632311] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[72205.633378] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[72331.581296] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[72331.582324] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[72457.580768] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[72457.581705] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[72564.401496] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=47981 PROTO=TCP SPT=443 DPT=39425 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[72583.579920] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[72583.580956] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[72709.579269] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[72709.580365] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[72835.585086] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[72835.586100] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[72857.134092] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=63468 PROTO=TCP SPT=443 DPT=51415 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[72867.136672] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=63469 PROTO=TCP SPT=443 DPT=51415 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[72877.135074] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=63470 PROTO=TCP SPT=443 DPT=51415 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[72998.888640] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=60797 PROTO=TCP SPT=443 DPT=39445 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[73008.890167] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=60798 PROTO=TCP SPT=443 DPT=39445 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[73018.889028] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=60799 PROTO=TCP SPT=443 DPT=39445 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[73034.488160] ieee80211 phy0: wlan0: No probe response from AP <MAC address removed> after 500ms, disconnecting.
[73035.793494] wlan0: authenticate with <MAC address removed>
[73035.804624] wlan0: send auth to <MAC address removed> (try 1/3)
[73036.008063] wlan0: send auth to <MAC address removed> (try 2/3)
[73036.212064] wlan0: send auth to <MAC address removed> (try 3/3)
[73036.416071] wlan0: authentication with <MAC address removed> timed out
[73042.936940] wlan0: authenticate with <MAC address removed>
[73042.960327] wlan0: send auth to <MAC address removed> (try 1/3)
[73042.962889] wlan0: authenticated
[73042.964212] wlan0: associate with <MAC address removed> (try 1/3)
[73042.966744] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[73042.968044] wlan0: associated
[73087.974048] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[73087.975014] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[73095.680350] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=105 TOS=0x00 PREC=0x00 TTL=48 ID=27043 PROTO=TCP SPT=443 DPT=51459 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[73105.679990] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=105 TOS=0x00 PREC=0x00 TTL=48 ID=27043 PROTO=TCP SPT=443 DPT=51459 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[73213.981800] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[73213.982972] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[73272.813570] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=105 TOS=0x00 PREC=0x00 TTL=48 ID=56457 PROTO=TCP SPT=443 DPT=51480 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[73275.696843] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.100 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=29610 PROTO=TCP SPT=443 DPT=55216 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[73285.696479] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.100 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=29611 PROTO=TCP SPT=443 DPT=55216 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[73295.696503] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.100 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=29612 PROTO=TCP SPT=443 DPT=55216 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[73339.982805] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[73339.983815] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[73465.983130] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[73591.981387] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[73591.982382] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[73717.980627] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[73717.981631] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[73843.984750] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[73843.985759] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[73969.979042] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[73969.980062] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[74095.978141] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[74095.979055] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[74221.978927] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[74221.979920] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[74347.977605] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[74347.978525] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[74473.977974] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[74473.978939] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[74599.975223] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[74599.976146] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[74619.073702] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.139 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=18182 PROTO=TCP SPT=443 DPT=49734 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[74629.073630] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.139 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=18183 PROTO=TCP SPT=443 DPT=49734 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[74639.073636] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.139 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=18184 PROTO=TCP SPT=443 DPT=49734 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[74725.974081] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[74851.975812] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[74851.976803] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[74856.509410] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.139 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=4087 PROTO=TCP SPT=443 DPT=49812 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[74866.509386] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.139 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=4078 PROTO=TCP SPT=443 DPT=49812 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[74876.509341] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.139 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=4079 PROTO=TCP SPT=443 DPT=49812 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[74888.953259] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=60411 PROTO=TCP SPT=443 DPT=39903 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[74896.085114] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=105 TOS=0x00 PREC=0x00 TTL=48 ID=21191 PROTO=TCP SPT=443 DPT=51880 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[74898.953112] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=60412 PROTO=TCP SPT=443 DPT=39903 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[74906.085181] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=105 TOS=0x00 PREC=0x00 TTL=48 ID=21191 PROTO=TCP SPT=443 DPT=51880 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[74908.954545] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=60413 PROTO=TCP SPT=443 DPT=39903 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[74977.973039] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[74977.973976] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[75103.971706] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[75103.972640] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[75229.992757] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[75229.993698] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[75355.996249] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[75414.032385] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=60958 PROTO=TCP SPT=443 DPT=53563 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[75420.052072] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=85 TOS=0x00 PREC=0x00 TTL=48 ID=13855 PROTO=TCP SPT=443 DPT=52662 WINDOW=1002 RES=0x00 ACK PSH URGP=0 
[75424.031121] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=60959 PROTO=TCP SPT=443 DPT=53563 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[75430.051830] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=85 TOS=0x00 PREC=0x00 TTL=48 ID=13856 PROTO=TCP SPT=443 DPT=52662 WINDOW=1002 RES=0x00 ACK PSH URGP=0 
[75434.031628] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=60960 PROTO=TCP SPT=443 DPT=53563 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[75440.051785] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=85 TOS=0x00 PREC=0x00 TTL=48 ID=13857 PROTO=TCP SPT=443 DPT=52662 WINDOW=1002 RES=0x00 ACK PSH URGP=0 
[75450.050727] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=85 TOS=0x00 PREC=0x00 TTL=48 ID=13858 PROTO=TCP SPT=443 DPT=52662 WINDOW=1002 RES=0x00 ACK PSH URGP=0 
[75460.050826] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=85 TOS=0x00 PREC=0x00 TTL=48 ID=13859 PROTO=TCP SPT=443 DPT=52662 WINDOW=1002 RES=0x00 ACK PSH URGP=0 
[75470.051931] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=85 TOS=0x00 PREC=0x00 TTL=48 ID=13860 PROTO=TCP SPT=443 DPT=52662 WINDOW=1002 RES=0x00 ACK PSH URGP=0 
[75480.052184] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=85 TOS=0x00 PREC=0x00 TTL=48 ID=13861 PROTO=TCP SPT=443 DPT=52662 WINDOW=1002 RES=0x00 ACK PSH URGP=0 
[75481.992619] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[75481.994138] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[75490.051658] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=85 TOS=0x00 PREC=0x00 TTL=48 ID=13862 PROTO=TCP SPT=443 DPT=52662 WINDOW=1002 RES=0x00 ACK PSH URGP=0 
[75500.051872] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.83 DST=192.168.0.10 LEN=85 TOS=0x00 PREC=0x00 TTL=48 ID=13863 PROTO=TCP SPT=443 DPT=52662 WINDOW=1002 RES=0x00 ACK PSH URGP=0 
[75607.989602] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[75607.990483] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[75649.916800] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=31022 PROTO=TCP SPT=443 DPT=39957 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[75733.989209] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[75733.995511] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[75859.988813] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[75859.989814] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[75985.988029] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[75985.989059] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[76111.987472] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[76237.986921] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[76237.987961] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[76363.986391] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[76363.987503] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[76489.985937] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[76489.986899] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[76615.985440] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[76615.986441] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[76741.984696] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[76741.985731] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[76867.984336] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[76867.985323] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[76986.349757] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=46123 PROTO=TCP SPT=443 DPT=52152 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[76986.363765] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=18654 PROTO=TCP SPT=443 DPT=52153 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[76993.983799] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[76993.985510] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[76996.349681] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=46124 PROTO=TCP SPT=443 DPT=52152 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[77001.323915] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.73.120 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=41 ID=58182 PROTO=TCP SPT=443 DPT=35468 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[77006.349861] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=46125 PROTO=TCP SPT=443 DPT=52152 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[77011.323887] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.73.120 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=41 ID=58183 PROTO=TCP SPT=443 DPT=35468 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[77012.056514] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.100 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=50025 PROTO=TCP SPT=443 DPT=55937 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[77022.056343] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.100 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=50025 PROTO=TCP SPT=443 DPT=55937 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[77032.056441] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.100 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=50026 PROTO=TCP SPT=443 DPT=55937 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[77119.983172] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[77119.984156] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[77245.982999] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[77245.984029] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[77371.982118] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[77371.983078] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[77497.981687] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[77497.982638] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[77623.981224] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[77623.982157] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[77749.980678] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[77749.981602] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[77875.980216] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[77875.981170] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[78001.979206] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[78001.980188] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[78127.978335] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[78127.979308] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[78253.977447] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[78253.978496] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[78379.976602] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[78379.977698] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[78505.976816] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[78631.976137] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[78757.974225] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[78757.980290] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[78883.973402] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[78883.974365] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[79009.973390] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[79135.971697] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[79135.972634] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[79261.970945] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[79261.971896] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[79387.970167] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[79387.971233] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[79513.969200] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[79513.970166] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[79639.968445] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[79639.969509] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[79765.967708] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[79765.968683] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[79891.966909] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[79891.967866] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[80017.966064] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[80017.967034] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[80143.965263] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[80143.966275] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[80269.966274] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[80269.967379] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[80395.964000] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[80395.964908] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[80521.962704] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[80521.963626] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[80647.970656] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[80647.971749] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[80774.025224] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[80774.026354] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[80899.980196] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[80899.981218] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[81025.980416] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[81151.978818] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[81151.979817] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[81277.988104] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[81277.989064] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[81403.987149] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[81403.988234] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[81529.986326] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[81529.987336] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[81655.985481] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[81655.986423] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[81781.985722] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[81907.983861] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[81907.984651] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[82033.983119] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[82033.984109] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[82159.982312] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[82159.983253] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[82285.982369] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[82285.983276] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[82411.980554] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[82411.981514] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[82537.979747] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[82537.980758] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[82663.980402] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[82663.981474] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[82789.978356] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[82789.979323] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[82915.977533] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[82915.978507] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[83041.976953] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[83041.977940] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[83167.976079] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[83167.976991] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[83293.975251] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[83293.976355] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[83419.974564] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[83419.975602] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[83545.973768] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[83545.974708] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[83671.972973] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[83671.973987] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[83797.972138] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[83797.973112] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[83923.973349] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[83923.974326] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[84049.970505] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[84049.971489] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[84175.969790] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[84175.970754] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[84301.968914] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[84301.969892] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[84427.969078] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[84553.967268] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[84553.968194] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[84679.966483] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[84679.967488] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[84805.965776] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[84805.966771] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[84931.964897] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[84931.965816] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[85057.964177] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[85057.965230] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[85183.963238] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[85183.964255] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[85309.962555] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[85309.963599] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[85435.961835] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[85435.962865] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[85561.960930] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[85561.961993] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[85687.960203] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[85687.961229] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[85813.959446] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[85813.960324] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[85939.958568] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[85939.959553] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[86065.957823] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[86065.958774] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[86191.957076] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[86191.958113] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[86317.956113] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[86317.957030] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[86443.955315] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[86443.956341] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[86569.954452] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[86569.955406] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[86695.953582] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[86695.954672] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[86821.952856] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[86821.953762] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[86947.952077] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[86947.953164] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[87073.951289] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[87073.952143] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[87199.950560] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[87199.952482] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[87325.949562] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[87325.950583] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[87451.948887] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[87451.949985] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[87577.948105] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[87577.949095] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[87703.947401] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[87703.948321] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[87829.946525] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[87955.945717] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[87955.946662] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[88081.945945] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[88207.944260] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[88207.945215] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[88333.943349] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[88333.944279] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[88459.942684] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[88459.943716] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[88585.943646] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[88585.944580] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[88711.941118] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[88711.942139] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[88837.940265] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[88837.941322] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[88963.951030] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[88963.952045] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[89089.939626] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[89089.940591] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[89215.937996] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[89215.938998] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[89341.937276] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[89341.938270] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[89467.936536] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[89467.937455] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[89593.935800] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[89593.936648] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[89719.936062] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[89845.934428] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[89845.935396] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[89971.934892] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[90097.933063] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[90097.933971] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[90208.718119] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=55721 PROTO=TCP SPT=443 DPT=52540 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[90211.161266] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.100 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=47 ID=44 PROTO=TCP SPT=443 DPT=56259 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[90218.716147] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=55721 PROTO=TCP SPT=443 DPT=52540 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[90223.932407] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[90223.933335] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[90228.716224] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=48 ID=55721 PROTO=TCP SPT=443 DPT=52540 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[90349.931518] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[90349.932414] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[90466.564285] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=105 TOS=0x00 PREC=0x00 TTL=47 ID=62257 PROTO=TCP SPT=443 DPT=52671 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[90476.563699] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.132 DST=192.168.0.10 LEN=105 TOS=0x00 PREC=0x00 TTL=47 ID=62258 PROTO=TCP SPT=443 DPT=52671 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[90511.060898] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=45742 PROTO=TCP SPT=443 DPT=40722 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[90520.169931] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.73.120 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=43 ID=13583 PROTO=TCP SPT=443 DPT=36001 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[90521.059448] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=45742 PROTO=TCP SPT=443 DPT=40722 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[90530.168984] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.73.120 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=43 ID=13584 PROTO=TCP SPT=443 DPT=36001 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[90531.060208] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.70.101 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=49 ID=45742 PROTO=TCP SPT=443 DPT=40722 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[90540.169269] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=173.194.73.120 DST=192.168.0.10 LEN=185 TOS=0x00 PREC=0x00 TTL=43 ID=13585 PROTO=TCP SPT=443 DPT=36001 WINDOW=992 RES=0x00 ACK PSH URGP=0 
[90601.930253] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[90601.931277] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC address removed>:fc:94:e3:92:43:02:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 


**************** done ********************


```

Thank you for help.

---

### Post by wildmanne39 on 2013-05-09
Please try:
```
echo "options b43 nohwcrypt=1" | sudo tee /etc/modprobe.d/b43.conf
sudo modprobe -rfv b43
sudo modprobe -v b43
```
Looks like UFW is blocking almost all traffic that is most like a problem, I recommend looking into it.
Thanks

---

### Post by nns2006 on 2013-05-10
> **Wild Man said:**
> Please try:
```
echo "options b43 nohwcrypt=1" | sudo tee /etc/modprobe.d/b43.conf
sudo modprobe -rfv b43
sudo modprobe -v b43
```
Looks like UFW is blocking almost all traffic that is most like a problem, I recommend looking into it.
Thanks

here is the output of these commands.

```
nityanand@nityanand-Vostro-1500:~$ echo "options b43 nohwcrypt=1" | sudo tee /etc/modprobe.d/b43.conf
[sudo] password for nityanand: 
options b43 nohwcrypt=1

nityanand@nityanand-Vostro-1500:~$ sudo modprobe -rfv b43
rmmod /lib/modules/3.5.0-29-generic/kernel/drivers/net/wireless/b43/b43.ko
rmmod /lib/modules/3.5.0-29-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.5.0-29-generic/kernel/net/wireless/cfg80211.ko
rmmod /lib/modules/3.5.0-29-generic/kernel/drivers/bcma/bcma.ko

nityanand@nityanand-Vostro-1500:~$ sudo modprobe -v b43
insmod /lib/modules/3.5.0-29-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.5.0-29-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.5.0-29-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.5.0-29-generic/kernel/drivers/net/wireless/b43/b43.ko nohwcrypt=1
```

After runing the secong command I got the option of installing the diver from STA wireless driver. 
Thank you for helping.

---

### Post by wildmanne39 on 2013-05-10
Hi, I hope you did not install the sta driver?
Thanks

---

### Post by nns2006 on 2013-05-11
No, I have installed b43-firmware. Do you see any problem with my connections? I did see ufw blocking and despite unblocking, I am still having the same problem.

---

