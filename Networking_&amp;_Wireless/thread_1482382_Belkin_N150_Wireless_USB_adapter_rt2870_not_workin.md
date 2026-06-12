---
title: "Belkin N150 Wireless USB adapter rt2870 not working"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by ddmits on 2010-05-13
Hi

I tried getting a Belkin USB Wireless adapter:N150 to work in a fresh installation of 10.4 with no success.  After reading several forum posts I tried both solutions with ndiswrapper and the XP driver and with the Ralink native driver with no luck.
```

lsusb
Bus 005 Device 008: ID 050d:935a Belkin Components 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```ndiswrapper
---------------
```
sudo ndiswrapper -i F6D4050v1-XP_2K/rt2870.inf 
```

```
ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
rt2870 : driver installed
    device (050D:935A) present
```

Output of dmesg:
```
[ 5697.732170] usb 5-1: new high speed USB device using ehci_hcd and address 8
[ 5697.884764] usb 5-1: configuration #1 chosen from 1 choice
[ 5698.008141] usb 5-1: reset high speed USB device using ehci_hcd and address 8
[ 5698.165388] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress'
[ 5698.166015] ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
[ 5698.168919] ndiswrapper (load_wrap_driver:108): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
```Ralink rt2870
----------------
I have followed step by step the instructions at: [http://ubunturt2870.pbworks.com/FrontPage](http://ubunturt2870.pbworks.com/FrontPage) 
No success.

I would appreciate your help.

---

### Post by ddmits on 2010-05-19
:( No answers at all.....

---

### Post by Kubaceski on 2010-05-19
I have a similar issue.  I have 10.4 (LM9), and using a D-Link DWA-140 (also rt2870 ralink), mine "sees" the available wireless networks, but won't actually connect.  It attempts to connect, then keeps asking me for the WPA password every few minutes while still not connecting successfully.  Is your experience going similar to this?  Or is yours not even seeing the networks?

---

### Post by sinclair86 on 2010-05-19
i dont know if this helps or if this helps you or not but on both fedora 13 and kubuntu 10.04 I had problem with the driver they were loading for my wireless rt2870 card. they were loading rt2800usb even tho I had the rt2870 installed. Had to blacklist the rt2800usb and give it a reboot and it worked.

---

### Post by Kubaceski on 2010-05-20
Pardon me for being ignorant, but how did you go about blacklisting the rt2800 driver?  Thx

Drew

---

### Post by ddmits on 2010-05-20
> **Kubaceski said:**
> I have a similar issue.  I have 10.4 (LM9), and using a D-Link DWA-140 (also rt2870 ralink), mine "sees" the available wireless networks, but won't actually connect.  It attempts to connect, then keeps asking me for the WPA password every few minutes while still not connecting successfully.  Is your experience going similar to this?  Or is yours not even seeing the networks?

No networks for me.

---

### Post by ddmits on 2010-05-20
> **Kubaceski said:**
> Pardon me for being ignorant, but how did you go about blacklisting the rt2800 driver?  Thx

Drew

Everything is written on the guide I have followed, including:

```
sudo echo blacklist rt2800usb > /etc/modprobe.d/blacklist.conf
```

Didn't work for me :(

---

### Post by stinkeye on 2010-05-20
I am using a belkin N router and a belkin USB Wireless which uses the rt2870 chpset.
I didn't have to use ndiswrapper, I just used the rt2870 drivers that are included with the default lucid install.

My wireless usb will only connect at 802.11g speeds(54 Mbps) though and wont connect using
the wpa and wpa2 standards.
Will connect using 128bit wep.


All I had to do was blacklist rt2800usb
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
and add **blacklist rt2800usb** to the bottom of the file.

and in the router settings change 
the security mode to 128bit wep.

Also in the router settings I have the wireless mode set to
**802.11n & 802.11g & 802.11b**
so any compliant device can join the network.

---

### Post by sinclair86 on 2010-05-20
do

[```
lsmod | grep "rt2"
```

if you see a rt2x00usb and/or rt2x00lib you are going to have to blacklist them as well or its not going to work

---

### Post by Kubaceski on 2010-05-20
Hey, thanks for the tip.  Mine works (D-Link DWA-140) now with WEP 128-bit.  Didn't like the other security options.  Now I just have to change the other six zillion computers on my network...

---

### Post by ddmits on 2010-05-20
I have made the changes you have suggested at the router.  I have removed the ndiswrapper and tried again with rt2870sta (Ralink)

When I startup lsmod shows no such modules loaded
After I load manually I can see the module
```
sudo modprobe rt2870sta 
lsmod | grep rt28
rt2870sta             461811  0 
```Then I insert the USB and dmesg shows:
```
[   43.760131] end_request: I/O error, dev fd0, sector 0
[  277.748602] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[  277.766861] rtusb init --->
[  277.766977] usbcore: registered new interface driver rt2870
[  409.516090] usb 5-1: new high speed USB device using ehci_hcd and address 2
[  409.667551] usb 5-1: configuration #1 chosen from 1 choice

```The USB led does not flash as it does usually in Windows. The light is permanently one.
```
 sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 20
       serial: 00:08:02:d1:d4:0b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139cp driverversion=1.3 duplex=full ip=192.168.2.3 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:11 ioport:8800(size=256) memory:f4013000-f40130ff

```
I don't see anything apart from my etherned wired connection.  After that if I execute dmesg I see some extra messages:
```
[  668.431288] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  668.431300] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  668.431305] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[  668.431526] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
[  668.451826] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[  668.472099] pcmcia_socket pcmcia_socket0: cs: warning: no high memory space available!
```The USB is inserted in a USB2.0 pcmcia card which works with other devices. I have tested that with an external hard disc.  No problems there.

It is an old laptop but it works and I would not like to buy a new one just because my USB wireless stick does not work.  Still if I don't solve this problem my only solution would be to use Windows :(
Should I do anything else... am I missing something? How can I know that it works?

---

### Post by stinkeye on 2010-05-20
> Should I do anything else... am I missing something? How can I know that it works?

Sorry, I can't offer any troubleshooting for this.
I am a noob when it comes to networking.
I more or less stumbled upon the solution to get my wireless adaptor to work.

---

### Post by ddmits on 2010-05-22
FINALLY!!! I write this message connected with my USB Wireless adapter.:popcorn:

Many many thanks to flash63 who saved me with his post:
[http://ubuntuforums.org/showpost.php?p=8591348&postcount=6](http://ubuntuforums.org/showpost.php?p=8591348&postcount=6)

I followed the steps and added my USB ID.  To find my ID i typed lsusb.

```
cd
cd RT2870_LinuxSTA_V2.3.0.0
sudo make uninstall
```In the following change to match your ID. To find my ID i typed lsusb.

```
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig
```Initially I had some errors. After rebooting however it worked!
Finally I did
```
echo rt2870sta | sudo tee -a /etc/modules

```to load it at startup....

May thanks flash63!:)

---

### Post by stinkeye on 2010-05-22
Congrats.
It makes your day when you see that connection established notification.
I also found out it will connect using wpa2 authentication.
In my router settings 
**wpa+wpa2** won't connect
but if I choose just
**wpa2** it connects.

---

### Post by ddmits on 2010-05-24
**UPDATE: **
The default driver rt2870sta supports only WEP and the max Bit Rate I got was 1Mb/s.
I decided to investigate other drivers and finally succeeded in installing and using the rt3070 driver from Ralink.  

_**Now it supports WPA also and the Bit Rate is 54Mb/s.**_:popcorn:

Let me share with you the details:

Download the latest driver from: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
RT3070USB(RT307x) 
The file is called: DPO_RT3070_LinuxSTA_V2.3.0.2_20100412.bz2
Unzip and extract and then cd to the extracted folder.

Unfortunately the installation does not work without changes....
To make it work you need to make the following changes (found at: [http://www.linuxforums.org/forum/wireless-internet/161550-solved-rt3070sta-module-license-unspecified-taints-kernel.html](http://www.linuxforums.org/forum/wireless-internet/161550-solved-rt3070sta-module-license-unspecified-taints-kernel.html))

```
cp RT2870STA.dat RT3070STA.dat
```edit os/linux/usb_main_dev.c and add the following red line after: MODULE_DESCRIPTION(.....
```
MODULE_DESCRIPTION("RT2870 Wireless Lan Linux Driver");
[COLOR=Red]MODULE_LICENSE("GPL");[/COLOR]
```[COLOR=Red]

[COLOR=Black]Then follow the steps below (found at: [http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593))

Execute lsusb to find the id of your device. Mine is:
[/COLOR][/COLOR]```
lsusb
Bus 005 Device 002: ID 050d:935a Belkin Components 
```[COLOR=Red][COLOR=Black]

Edit common/rtusb_dev_id.c and add the following line (change to match your id) to the list of devices (do not forget the 0x before the numbers)

        [/COLOR][/COLOR]```
{USB_DEVICE(0x050d,0x935a)}, /* Belkin N 150 */
```[COLOR=Red][COLOR=Black]

Then compile and install:

[/COLOR][/COLOR]```
sudo make
sudo make install
```[COLOR=Red][COLOR=Black]

If you use the old driver  to remove it [/COLOR][/COLOR][COLOR=Red][COLOR=Black]type[/COLOR][/COLOR][COLOR=Red][COLOR=Black]:
[/COLOR][/COLOR]```
sudo modprobe -r rt2870sta

```Test the new driver:
```
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt3070sta.ko
sudo /etc/init.d/networking restart
sudo restart network-manager
```If this works then append the following line to /etc/modules
```
echo rt3070sta | sudo tee -a /etc/modules
```so that the new driver loads at boot.

Good luck!
[COLOR=Red][COLOR=Black]

[/COLOR][/COLOR]

---

### Post by Blümchen Blau on 2010-05-24
Maybe it makes sense to take a look at [[URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093"]Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093/comments/54")[/URL] especially at Post #54 and following. Seems to be a similar problem with a lot of different solution suggestions.

It helped me solving issues with my RT2860 with WPA2+WPA-protected networks.

---

### Post by darkSo on 2010-06-02
double post, sorry

---

### Post by darkSo on 2010-06-02
Hi ddmits!

i followed your howto to get running my belkin wlan usb (the windows   installation cd is giving me the rt2780.inf). but the only one thing i   got back is while printing "iwconfig":


```
lo        no wireless extensions.
 
 eth0      no wireless extensions.
 
 ra0       Ralink STA  ESSID:""  
           Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated     
           Bit Rate:1 Mb/s   
           RTS thr:eek:ff    Fragment thr:eek:ff
           Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
``` 


network manager is saying me the device is not ready :sad:

how can get it work. maybe u can give me a hint!

it should be a "new" pc 4 my sister and i have to leave during the next   10 hours...

so please answer if you are online!

thnak u very many :smile:

p.s.: i had an error during this attempt:

```
sudo insmod /lib/modules/`uname  -r`/kernel/drivers/net/wireless/rt2870sta.ko
```ang got this:

```
insmod: can't read  '/lib/modules/2.6.32-22-generic-pae/kernel/drivers/net/wireless/rt2870sta.ko':  No such file or directory
```
in this folder is no rt2870sta.ko only the rt3070sta.ko
so i modified your entry:

```
sudo insmod  /lib/modules/2.6.32-22-generic-pae/kernel/drivers/net/wireless/rt3070sta.ko

```but then i got:

```
insmod: error inserting  '/lib/modules/2.6.32-22-generic-pae/kernel/drivers/net/wireless/rt3070sta.ko':  -1 File exists
```


please i need help and as soon as you can....

---

### Post by Talon2 on 2010-06-02
This [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801") may help.  Please feel free to add to this bug.

---

### Post by ddmits on 2010-06-03
> **darkSo said:**
> 

```
sudo insmod  /lib/modules/2.6.32-22-generic-pae/kernel/drivers/net/wireless/rt3070sta.ko

```but then i got:

```
insmod: error inserting  '/lib/modules/2.6.32-22-generic-pae/kernel/drivers/net/wireless/rt3070sta.ko':  -1 File exists
```
please i need help and as soon as you can....

I guess that you have already installed the rt3070.  Can you write the outputs of the commands:

lsmod | grep rt3
lsmod | grep rt2

when you start your system?

---

### Post by darkSo on 2010-06-05
hi,

after booting and using 

```
lsmod |grep rt3
```I got:

```
rt3070sta            571016   0
```and after

```
grep |grep rt2
```nothing

---

### Post by darkSo on 2010-06-05
by the way here is my output for 

```
lsmod
``````

Module                  Size  Used by
snd_opl3_synth         10388  0 
snd_seq_midi_emul       5492  1 snd_opl3_synth
binfmt_misc             6587  1 
snd_wavefront          33098  0 
snd_cs4236             25546  0 
snd_wss_lib            23442  2 snd_wavefront,snd_cs4236
snd_cmipci             30469  3 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_mpu401              5187  0 
snd_pcm                70886  4 snd_cs4236,snd_wss_lib,snd_cmipci,snd_pcm_oss
snd_page_alloc          7172  2 snd_wss_lib,snd_pcm
snd_opl3_lib            8998  4 snd_opl3_synth,snd_wavefront,snd_cs4236,snd_cmipci
snd_hwdep               5412  2 snd_wavefront,snd_opl3_lib
snd_mpu401_uart         5649  4 snd_wavefront,snd_cs4236,snd_cmipci,snd_mpu401
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  8 snd_opl3_synth,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  4 snd_wss_lib,snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          5700  7 snd_opl3_synth,snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
rt3070sta             571016  0 
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
ppdev                   5259  0 
snd                    54148  23 snd_opl3_synth,snd_wavefront,snd_cs4236,snd_wss_lib,snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_mpu401,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia               4701947  22 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
ns558                   3280  0 
psmouse                63245  0 
intel_agp              24473  1 
serio_raw               3978  0 
gameport                9089  3 snd_cmipci,ns558
soundcore               6620  1 snd
parport_pc             26250  1 
shpchp                 28884  0 
agpgart                31788  2 nvidia,intel_agp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
8139too                18673  0 
8139cp                 16602  0 
mii                     4381  2 8139too,8139cp
floppy                 53080  0 
```

---

### Post by ddmits on 2010-06-05
The rt3070sta driver is installed and loaded.
I suggest that you open a terminal and execute:

tail -f /var/log/syslog

and then plug in your Wireless USB to see what are the messages.

---

### Post by darkSo on 2010-06-06
hi,

last night I was trying the rt2870 driver. so I unloaded rt3070, installed rt2870 and loaded the module. blacklisted rt2800usb. but no result. then I unloaded rt2870 and loaded rt3070 and I got my connection :) even using WPA!

Today I'll reboot the machine and see if it will work after booting. But I think so.

---

### Post by ddmits on 2010-06-06
That's good news...

I still have some problems with network getting disconnected... but life is not perfect.

---

### Post by Alexis Wilke on 2011-07-07
> **ddmits said:**
> Many many thanks to flash63 who saved me with his post:
[http://ubuntuforums.org/showpost.php?p=8591348&postcount=6](http://ubuntuforums.org/showpost.php?p=8591348&postcount=6)
...

Well... I tried using the newest version of the module from ralink and it didn't work at all on 11.04. The default compile generated a module named rt5370sta, I forced the chipset to rt3070sta (as I have an N150 I would imagine I have the same chip?!), but either way the wireless is not detected at all... I will try to copy the .conf file though because the make install only copies the RT28070STA.conf file and it could very well be that the right name is required there! Oh! And there was one small fix I needed to apply to the code to get the rt3070sta to compile (a test about RT33xx which I commented out.)

I finally got the rt2870sta to connect full speed (54mb/s once I setup an Ad-Hoc wireless connection with auto for the frequency), but to no avail.

So... I have a connection showing up, but when I try to ping my computer (198.168.1.1) or even the wireless router (192.168.1.254) I get Network Unreachable.

As suggested I tried with just WPA2 instead of WPA/WPA2, but that did not work. Maybe I'll try without encryption just to see whether the encryption is the culprit. But I was hoping that by now all these problem would have been solved...

Anyway, wondering whether someone has had this problem on Ubuntu 11.04?

---

### Post by unixlike on 2012-05-11
Anyone has this wireless adapter working with ubuntu 12.04?

---

