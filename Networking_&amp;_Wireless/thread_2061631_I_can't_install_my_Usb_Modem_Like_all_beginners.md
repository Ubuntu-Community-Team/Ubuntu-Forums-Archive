---
title: "I can't install my Usb Modem Like all beginners"
date: 2012-09-23
forum: Networking &amp; Wireless
---

### Post by djibrilcoulibaly on 2012-09-23
hello guys ,
I'm new in Ubuntu  area and Like most of people I can't Install my Usb modem Driver .
I spent hours reading over forum and wiki but unfortinately I couldn't  solve it .
I expected to get help here to start profite  ubuntu .. 

this is my Modem Info Huawei BCM328

**Prompt Log **
> :~$ lsusb
Bus 001 Device 003: ID 198f:0220 Beceem Communications Inc. BCSM250 WiMAX Adapter
:~$ 

T:  Bus=01 Lev=01 Prnt=01 Port=06 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=198f ProdID=0220 Rev=00.01
S:  Manufacturer=HUAWEI
S:  Product=WiMAX USB Stick
S:  SerialNumber=0
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=usbbcm

---

### Post by djibrilcoulibaly on 2012-09-23
always eyes on my post , nothing yet for me ..

I forgot some usfull info what I had put since long .. 

 Ubuntu Version is : **ubuntu-12.04.1-desktop-i386**
Computer : **Destkop  Clone **( mainboard Mercury , ram 2 giga ) 
a Computer where I decided to beginning with it firstly before install on My Pc ..

---

### Post by djibrilcoulibaly on 2012-09-24
PFFF none to guide me ?

---

### Post by Toz on 2012-09-24
Hello and welcome to the forums.

Have you come across this thread in your travels: [http://ubuntuforums.org/showthread.php?t=1969322]("http://ubuntuforums.org/showthread.php?t=1969322")? It might be of some assistance.

---

### Post by djibrilcoulibaly on 2012-09-24
> **Toz said:**
> Hello and welcome to the forums.

Have you come across this thread in your travels: [http://ubuntuforums.org/showthread.php?t=1969322](http://ubuntuforums.org/showthread.php?t=1969322)? It might be of some assistance.


at least one here cares about me , i'm checking and I will inform you soon .
thx advanced ...

---

### Post by djibrilcoulibaly on 2012-09-24
yes I readed this thread Saturday night .. I spent more than 1 hours trying this ...
as told by sir ALex but no thing happened on mine .. state 0%  positive...

---

### Post by Toz on 2012-09-24
Although I don't have a modem myself, I can try to lead you through the steps to see we can figure it out.

Can you post back the results of:
```
lsusb
```

...and:
```
usb-devices | pastebinit
```
...and post back the link that is generated.

---

### Post by djibrilcoulibaly on 2012-09-24
> **Toz said:**
> Although I don't have a modem myself, I can try to lead you through the steps to see we can figure it out.

Can you post back the results of:
```
lsusb
```...and:
```
usb-devices | pastebinit
```...and post back the link that is generated.

ofcourse it's possible but it could take few hours before .
becoz I haven't Computer now . I will report once I done it .

---

### Post by djibrilcoulibaly on 2012-09-25
detail like requested : 
[B]
lsusb command[/B]

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 002: ID 0421:01c7 Nokia Mobile Phones N900 (Storage Mode) 
Bus 001 Device 011: ID 198f:0220 Beceem Communications Inc. BCSM250 WiMAX Adapter 

**usb-devices command **

 T:  Bus=01 Lev=01 Prnt=01 Port=07 Cnt=01 Dev#= 11 Spd=480 MxCh= 0
  D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
  P:  Vendor=198f ProdID=0220 Rev=00.01
  S:  Manufacturer=HUAWEI
  S:  Product=WiMAX USB Stick
  S:  SerialNumber=0
  C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
  I:  If#= 0 Alt= 0 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=usbbcm

---

### Post by Toz on 2012-09-25
Looks like the modem is being detected. What happens when you try to create an internet connection with Network Manager?

---

### Post by djibrilcoulibaly on 2012-09-25
not device's showed when I try . Mobile Broadband connection

---

### Post by Toz on 2012-09-25
What happens if you:
```

sudo bash
echo 198f 0220 > /sys/bus/usb-serial/drivers/option1/new_id
```

Does modem get recognized? 

Can you post back results of "usb-devices" again after issuing that command and post back contents of "/var/log/dmesg"?

Also, post back any entries in "/var/log/syslog" after you insert usb modem.

EDIT: And also post back results of:
```
lsmod
```

---

### Post by djibrilcoulibaly on 2012-09-25
> echo log : 
 :~# echo 198f 0220 > /sys/bus/usb-serial/drivers/option1/new_id
  bash: /sys/bus/usb-serial/drivers/option1/new_id: No such file or directory
  Lsmod log : 

> Module                  Size  Used by
  nls_iso8859_1          12617  1 
  nls_cp437              12751  1 
  vfat                   17308  1 
  fat                    55605  1 vfat
  bcm_wimax             244941  0 
  uas                    17828  0 
  usb_storage            39646  1 
  snd_hda_codec_realtek   174222  1 
  snd_hda_intel          32765  3 
  snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
  snd_hwdep              13276  1 snd_hda_codec
  snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
  rfcomm                 38139  0 
  bnep                   17830  2 
  ppdev                  12849  0 
  bluetooth             158438  10 rfcomm,bnep
  psmouse                72919  0 
  snd_seq_midi           13132  0 
  snd_rawmidi            25424  1 snd_seq_midi
  snd_seq_midi_event     14475  1 snd_seq_midi
  snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
  serio_raw              13027  0 
  snd_timer              28931  2 snd_pcm,snd_seq
  snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
  i915                  414739  3 
  snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
  parport_pc             32114  1 
  drm_kms_helper         45466  1 i915
  soundcore              14635  1 snd
  snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
  drm                   197692  4 i915,drm_kms_helper
  i2c_algo_bit           13199  1 i915
  mac_hid                13077  0 
  video                  19068  1 i915
  lp                     17455  0 
  parport                40930  3 ppdev,parport_pc,lp
  r8169                  56321  0 
  

one thing on echo command , it's option1 or optionl (L) ?

---

### Post by Toz on 2012-09-25
How about /var/log/dmesg and /var/log/syslog (syslog after you've inserted the usb modem)?

---

### Post by Toz on 2012-09-25
Just came across this that might be helpful: [http://minhazulhaque.blogspot.ca/2012/05/gui-for-bcs-mobile-wimax-on-linux.html]("http://minhazulhaque.blogspot.ca/2012/05/gui-for-bcs-mobile-wimax-on-linux.html"). 

The model that you have is supported.

---

### Post by djibrilcoulibaly on 2012-09-25
> **Toz said:**
> Just came across this that might be helpful: [http://minhazulhaque.blogspot.ca/2012/05/gui-for-bcs-mobile-wimax-on-linux.html](http://minhazulhaque.blogspot.ca/2012/05/gui-for-bcs-mobile-wimax-on-linux.html). 

The model that you have is supported.


ok I will try it tommorow , thx for you time you spending on my pb .

---

### Post by djibrilcoulibaly on 2012-09-25
> **Toz said:**
> How about /var/log/dmesg and /var/log/syslog (syslog after you've inserted the usb modem)?

sorry I forgot that                                                    .

---

### Post by djibrilcoulibaly on 2012-09-26
I follow all proced but sometime missed again, Ive installed GUI .. 
but I don't know where these files are located on my System . I should copy them 

cp -f libcrypto.so.0.9.8 /lib
cp -f libeap_supplicant.so /lib
cp -f libengine_beceem.so /lib
cp -f libssl.so.0.9.8 /lib
cp -f libxvi020.so /lib
cp -f macxvi200.bin /lib/firmware
cp -f macxvi.cfg /lib/firmware
cp -f wimax /etc/init.d
cp -f wimaxc /usr/bin
cp -f wimaxcert.pem /etc
cp -f wimaxd /usr/bin
cp -f wimaxd.conf /etc

---

### Post by Toz on 2012-09-26
In those instructions, there is a link under the words "Click here" to get the files. I believe those files are pre-compiled for 32-bit. Are you running 32 or 64-bit ubuntu?

---

### Post by djibrilcoulibaly on 2012-09-26
> **Toz said:**
> In those instructions, there is a link under the words "Click here" to get the files. I believe those files are pre-compiled for 32-bit. Are you running 32 or 64-bit ubuntu?

mine is 32-bit, I've downloaded files on the link  and installed ( he asked ) . 
after what some files should be copied on some directories .I didn't find them ..

we are not far , just few details again chief TOZ ...

---

### Post by djibrilcoulibaly on 2012-09-27
this is the Device Diagnosic Log below , hopefull to get help with its . 

> ~$ **lsusb**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 198f:0220 [COLOR=Red]**Beceem Communications Inc. BCSM250 WiMAX Adapter**[/COLOR]

**USb-devices Log **

> T:  Bus=01 Lev=01 Prnt=01 Port=06 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=198f ProdID=0220 Rev=00.01
S:  Manufacturer=HUAWEI
S:  Product=WiMAX USB Stick
S:  SerialNumber=0
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=usbbcm

> ~$ **lsmod**
Module                  Size  Used by
[COLOR=Red]**bcm_wimax             244941  0 **[/COLOR]
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
ppdev                  12849  0 
snd_hda_codec_realtek   174222  1 
psmouse                72919  0 
serio_raw              13027  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
parport_pc             32114  1 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13077  0 
i915                  414739  3 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
r8169                  56321  0 

        **             Var/log/dmesg**
> [    7.475086] bcm_wimax: module is from the staging directory, the quality is unknown, you have been warned.
[    7.476662] beceem: Beceem Communications Inc. WiMAX driver, 5.2.45
[    7.476665] Copyright 2010. Beceem Communications Inc
[    7.476754] usbbcm_device_probe:subtype[1] = 0x000000ff
[    7.476757] usbbcm_device_probe:subtype[2] = 0x00000000
[    7.476759] usbbcm_device_probe:subtype[4] = 0x00000000
[    7.476762] usbbcm_device_probe:subtype[8] = 0x00000000
[    7.476764] InitAdapter:Initialising Adapter = f2f20480
[    7.476788] InitAdapter:Adapter initialised
[    7.476791] usbbcm_device_probe:psIntfAdapter 0xf5010000
[    7.477112] usb 1-7: RDM Chip ID 0xbece3301
[    7.502524] beceemUnable To Open File /lib/firmware/macxvi.cfg, err -2
[    7.502529] bcm_parse_target_params:NOT ABLE TO OPEN THE /lib/firmware/macxvi.cfg FILE
[    7.502532] beceemInitCardAndDownloadFirmware failed.
[    7.502535] usbbcm_device_probe:File Not Found.  Use app to download.
[    7.502569] usbcore: registered new interface driver usbbcm
[    7.510425] init: failsafe main process (591) killed by TERM signal
[    7.783150] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input8
[    7.807234] r8169 0000:02:00.0: eth0: link down
[    7.807425] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.807735] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.836661] type=1400 audit(1348750851.521:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=750 comm="apparmor_parser"
[    7.837181] type=1400 audit(1348750851.521:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=750 comm="apparmor_parser"
[    7.837418] type=1400 audit(1348750851.521:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=749 comm="apparmor_parser"
[    7.837480] type=1400 audit(1348750851.521:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=750 comm="apparmor_parser"
[    7.843504] type=1400 audit(1348750851.525:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=753 comm="apparmor_parser"
[    8.504943] init: plymouth-stop pre-start process (1025) terminated with status 1
[   24.673549] audit_printk_skb: 36 callbacks suppressed
[   24.673553] type=1400 audit(1348750868.357:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1615 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
root@Jibril:/var/log# 




---

### Post by Toz on 2012-09-27
From dmesg:
```

[ 7.502524] beceemUnable To Open File /lib/firmware/macxvi.cfg, err -2
[ 7.502529] bcm_parse_target_params:NOT ABLE TO OPEN THE /lib/firmware/macxvi.cfg FILE
[ 7.502532] beceemInitCardAndDownloadFirmware failed.
```

Did you copy the macxvi.cfg file to /lib/firmware?

> mine is 32-bit, I've downloaded files on the link and installed ( he asked ) .
after what some files should be copied on some directories .I didn't find them ..

Which ones did you not find?

---

### Post by Toz on 2012-09-27
If you are missing the macxvi.cfg and macxvi200.bin files, it appears that they are part of the **linux-firmware-nonfree** package. Make sure it is installed.

---

### Post by djibrilcoulibaly on 2012-09-27
> Did you copy the macxvi.cfg file to /lib/firmware? > Which ones did you not find?no yet because I don't know where their are . I've download the files .
which are zip I've unzipped and chech into but I didn't see ...
I went on their wiki ( google projet ) for more but nothing also . 

always eyes on you chief **TOZ** , you only can help ..

---

### Post by Toz on 2012-09-27
See my post #23.

---

### Post by djibrilcoulibaly on 2012-09-27
I've downloaded this **wimaxcmgui-1.0.0-no-fw-cert-cfg** , I make it Executable ( x ) and 2x click .
after what i got GUI . I downloaded also this **Beceem-API.tar **I checked into nothing .

---

### Post by djibrilcoulibaly on 2012-09-27
:lolflag:  yes I began laughting now because I could copied necessary files .
I got files on wimax installation under windows 7 ... not finsh yet I didn't configurated ISP . but it will soon bcoz I get off , I will make it later ..
Device is detected in GUI . just need to confugurate ISP and all ok . thx you sir **Toz** being there for assit me .

---

### Post by mdminhazulhaque on 2012-09-28
Yes it is necessary to put "**firmware files from your ISP**" at /lib/fimrware. The module bcm_wimax requires "**/lib/fimrware/macxvi200.bin**" and "**/lib/firmware/macxvi.cfg**" before plugging the device in. And installing **linux-firmware-nonfree** won't solve the problem, it doesn't have that **ISP specific** firmwares.

You can get latest updates, installers, sources and scratches at my [Google Code Project]("http://code.google.com/p/wimaxcmgui/").

---

### Post by djibrilcoulibaly on 2012-09-28
> **mdminhazulhaque said:**
> Yes it is necessary to put "**firmware files from your ISP**" at /lib/fimrware. The module bcm_wimax requires "**/lib/fimrware/macxvi200.bin**" and "**/lib/firmware/macxvi.cfg**" before plugging the device in. And installing **linux-firmware-nonfree** won't solve the problem, it doesn't have that **ISP specific** firmwares.

You can get latest updates, installers, sources and scratches at my [Google Code Project]("http://code.google.com/p/wimaxcmgui/").

Thx you to be here sir , if I understood I have to download the new one to reinstalled ?
latest**'s   wimaxcmgui-1.0.1.tar.gz **I downloaded but how to proced with it ? I have to make executable or what ?

---

### Post by djibrilcoulibaly on 2013-04-01
how long ... about many months later , still issue not yet solved ... 
what's I noticed early is that .. why dongle serial number stay =0 .. is it normal ? 
[IMG]http://img42.imageshack.us/img42/60/screenshotfrom201304010b.png[/IMG]

---

### Post by alexfish on 2013-04-01
Hi

can have a look here , but not sure if on right track
[h=1][SIZE=1][install wimax usb modem "huawei BM338" driver on ubuntu 12.04]("http://ubuntuforums.org/showthread.php?t=2128413")[/SIZE][/h]
Alex.

---

### Post by djibrilcoulibaly on 2013-04-01
welcome @alexfish , you are here sure problem will b solved .. link is too cool ..
but I bypass these steps , I installed modem driver , modem Led  blink when it's connected . what was not before .
but it look like driver missing again . I used **[Minhazul blog  ]("http://minhazulhaque.blogspot.co.uk/2012/01/run-beceem-wimax-devices-on-linux-mint.html")**Tools but can't get internet over it ...

---

### Post by lud on 2013-04-26
Not sure if this thread is still active, but definitely try to google sakis3g script. It helped me greatly.

And only to add, despite being connected via sakis3g script, internet connection is not showing in graphical interface as being connected, but nevertheless I am able to use web browser, email client and also terminal is connected to the internet. On the other hand, I am not able to use Ubuntu Software Center to download programmes, as it does not recognize the internet connection. Nevertheless it's still possible to install software via terminal.

---

### Post by djibrilcoulibaly on 2013-04-26
oops I get tired then thrown that ... I use my broad-band usb modem which supported .. 
bye bye Huawei Wimax . thx anyway

---

