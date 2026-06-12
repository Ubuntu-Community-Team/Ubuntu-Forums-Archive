---
title: "Broadcom b43 &quot;device not ready, firmware missing&quot;"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by CasparGrigoriNovykh on 2010-12-05
```

lspci -nn | grep -i 14e4

```

yields:
```

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY
 [14e4:4315] (rev 01)

```
~
```

ls -al /lib/firmware

```

yields:

drwxr-xr-x  2 root root     4096 2010-12-05 16:37 b43
drwxr-x---   2 root root     4096 2010-12-02 02:06 b43Legacy

I look forward to all your help, and appreciate it!  Thank you so much in advance.


Caspar

---

### Post by northd_tech on 2010-12-05
Hello Caspar,

That is a Broadcom 4312 that should have Ubuntu support under the proprietary Broadcom "STA" hardware driver.  What do you see if you go into System > Administration > Hardware Drivers?  Is there anything about a Broadcom "STA" or "b43" driver listed there, and is the LED-like icon green or grayed out?  Could you attach a screenshot of what is there under Hardware Drivers perhaps?

Can you also post the output from these terminal commands:

```
lsmod
ifconfig
iwconfig

uname -a
lsb_release -d
```

---

### Post by Habeouscorpus on 2010-12-05
I'm having the same problem with mine. I have the same exact wireless device.

lsmod;
```
Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
arc4                    1165  0 
joydev                  8735  0 
mac80211              231541  0 
i915                  292683  3 
snd_hda_codec_idt      54887  1 
drm_kms_helper         30168  1 i915
drm                   168054  4 i915,drm_kms_helper
snd_hda_intel          22107  0 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
videodev               43098  1 uvcvideo
cfg80211              144470  1 mac80211
v4l1_compat            13359  2 uvcvideo,videodev
dell_laptop             5730  0 
dell_wmi                2852  0 
snd                    49006  9 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                  5402  1 dell_laptop
intel_agp              26424  2 i915
led_class               2633  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
psmouse                59033  0 
serio_raw               4022  0 
agpgart                32011  2 drm,intel_agp
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19013  0 
usb_storage            40172  0 
libahci                21667  4 ahci
sky2                   45127  0 
```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr a4:ba:db:a4:34:bb  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a6ba:dbff:fea4:34bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2457 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2099 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3165949 (3.1 MB)  TX bytes:323805 (323.8 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2880 (2.8 KB)  TX bytes:2880 (2.8 KB)

```

iwconfig;

lo        no wireless extensions.

eth0      no wireless extensions.

uname -a:

Linux inspiron 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686 GNU/Linux

lsb_release: 

Description:    Ubuntu 10.10

---

### Post by northd_tech on 2010-12-05
> **Habeouscorpus said:**
> 
**lsmod;**
Module                  Size  Used by
mac80211              231541  0 
cfg80211              144470  1 mac80211

Yours is a 32-bit version HC, and curiously, you seem to be missing both the "wl"(STA) and/or the "b43"/"ssb" modules, but the 80211 encryption/authentication modules that are usually loaded afterward for their use ARE present!

Can you also post the results of these commands, HC:
```
less /etc/modules
ls /etc/modprobe.d
lspci

```

---

### Post by CasparGrigoriNovykh on 2010-12-05
Hello northd_tech!  Thanks for the quick reply, and the help, man.  

One moment as I gather all the info (it takes me a few, bouncing between two computers - one offline, and one online) and I will post in a bit. 

As for the drivers, both b43 and the STA wireless drivers are available.  I have tried them both before; STA was originally the working driver.  I made the switch to b43 for numerous reasons, one being the evident stronger signal present.  All was hunky dory, b43 running very well, up until about two days ago, though I made no conscious changes to my setup.  If it is possible to hang tight to b43, I would prefer it.  

However, one tidbit of interesting info I just stumbled across is that my iwconfig readout is missing wlan0, it's usual.  It is replaced by vboxnet0, which must have come about as I was installing guest additions within VirtualBoxOSE.  These installations took place before the successful installation of the b43 drivers, but there it is.  

Now, after entering "sudo modprobe -r b43 ssb" and subsequently, "sudo modprobe b43", my wireless enables, kicking out the vbox listing under iwconfig, and replacing it with proper wlan0.  Still no connection available, with the message still displaying "device not ready, firmware missing.  It seems that this vbox intrusion is not the cause of my main problem, but when all is said and done, a lesson in how to automatically load the proper drivers upon boot would be much appreciated!

All the info is on its way in my next post.  Thank you, again!

---

### Post by CasparGrigoriNovykh on 2010-12-06
I'm so sorry for the delay in delivering this information!  Comcast is having terrible server issues here in Detroit.

```

caspar@Pluto:~$ lsmod
Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
vboxnetadp              6454  0 
vboxnetflt             15152  0 
vboxdrv               190199  2 vboxnetadp,vboxnetflt
snd_hda_codec_idt      54887  1 
snd_hda_codec_intelhdmi     9812  1 
pcmcia                 35973  0 
pcmcia_core            14657  1 pcmcia
joydev                  8735  0 
snd_hda_intel          22107  2 
snd_hda_codec          87552  3 snd_hda_codec_idt,snd_hda_codec_intelhdmi,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
mac80211              239420  0 
snd_seq_midi            4588  0 
i915                  292683  4 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
cfg80211              139907  1 mac80211
drm_kms_helper         30168  1 i915
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168054  5 i915,drm_kms_helper
r852                    9536  0 
sm_common               3285  1 r852
nand                   34905  2 r852,sm_common
nand_ids                2903  1 nand
snd                     49006  13  snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               55847  0 
nand_ecc                3938  1 nand
dell_wmi                2852  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
compat                  4020  1 cfg80211
mtd                    18877  2 sm_common,nand
intel_agp              26424  2 i915
i2c_algo_bit            5168  1 i915
dell_laptop             5730  0 
video                  18712  1 i915
dcdbas                  5402  1 dell_laptop
psmouse                59033  0 
serio_raw               4022  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
output                  1883  1 video
agpgart                32011  2 drm,intel_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
usb_storage            40172  1 
firewire_ohci          21106  0 
sdhci_pci               6339  0 
sdhci                  15890  1 sdhci_pci
firewire_core          46643  1 firewire_ohci
ahci                   19013  0 
libahci                21667  3 ahci
ssb                    39288  0 
led_class               2633  1 sdhci
sky2                   45127  0 
crc_itu_t               1383  1 firewire_core

``````

caspar@Pluto:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:9b:e4:49:ac  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18112 (18.1 KB)  TX bytes:18112 (18.1 KB)

``````

caspar@Pluto:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

``````

caspar@Pluto:~$ uname -a
Linux Pluto 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686 GNU/Linux

```~~
AFTER APPLYING "sudo modprobe b43" commands, the above commands then yield:

```

caspar@Pluto:~$ lsmod
Module                  Size  Used by
arc4                    1165  2 
b43                   228124  0 
ssb                    44520  1 b43
pcmcia                 35973  2 b43,ssb
pcmcia_core            14657  1 pcmcia
mac80211              239420  1 b43
cfg80211              139907  2 b43,mac80211
compat                  4020  1 cfg80211
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
vboxnetadp              6454  0 
vboxnetflt             15152  0 
vboxdrv               190199  2 vboxnetadp,vboxnetflt
snd_hda_codec_idt      54887  1 
snd_hda_codec_intelhdmi     9812  1 
joydev                  8735  0 
snd_hda_intel          22107  2 
snd_hda_codec          87552  3 snd_hda_codec_idt,snd_hda_codec_intelhdmi,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
i915                  292683  4 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
drm_kms_helper         30168  1 i915
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168054  5 i915,drm_kms_helper
r852                    9536  0 
sm_common               3285  1 r852
nand                   34905  2 r852,sm_common
nand_ids                2903  1 nand
snd                     49006  13  snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               55847  0 
nand_ecc                3938  1 nand
dell_wmi                2852  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
mtd                    18877  2 sm_common,nand
intel_agp              26424  2 i915
i2c_algo_bit            5168  1 i915
dell_laptop             5730  0 
video                  18712  1 i915
dcdbas                  5402  1 dell_laptop
psmouse                59033  0 
serio_raw               4022  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
output                  1883  1 video
agpgart                32011  2 drm,intel_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
usb_storage            40172  1 
firewire_ohci          21106  0 
sdhci_pci               6339  0 
sdhci                  15890  1 sdhci_pci
firewire_core          46643  1 firewire_ohci
ahci                   19013  0 
libahci                21667  3 ahci
led_class               2633  2 b43,sdhci
sky2                   45127  0 
crc_itu_t               1383  1 firewire_core

``````

caspar@Pluto:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:9b:e4:49:ac  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1060 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1060 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78752 (78.7 KB)  TX bytes:78752 (78.7 KB)

``````

caspar@Pluto:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

Btw, I'm running Ubuntu 10.10, Maverick

---

### Post by northd_tech on 2010-12-06
> **CasparGrigoriNovykh said:**
> 
  uname -a
Linux Pluto 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686 GNU/Linux

AFTER APPLYING "sudo modprobe b43" commands, the above commands then yield:

 ** lsmod**
Module                  Size  Used by
**b43 **                  228124  0 
ssb                    44520  1 **b43**
pcmcia                 35973  2 **b43**,ssb
pcmcia_core            14657  1 pcmcia
mac80211              239420  1 **b43**
cfg80211              139907  2 **b43**,mac80211
compat                  4020  1 cfg80211

vboxnetadp              6454  0 
vboxnetflt             15152  0 
vboxdrv               190199  2 vboxnetadp,vboxnetflt

 ** iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
[/CODE]Btw, I'm running Ubuntu 10.10, Maverick

Hi again Caspar.  It has been quite a while since I worked with b43 Broadcom drivers, but that looks like the correct collection of wireless modules from what I remember, and I don't see any conflict with the "STA" driver module(s).  It doesn't look like your wireless is seeing any router communication though from the **iwconfig** output.

Can you verify this by trying the following terminal command (that you will need to press CTRL-C to exit out of):

```
ping www.linux.org
```I expect that you will get error messages from that. If you click the Network Manager icon (at the very upper right corner in your screenshots), are all the choices for wireless networks grayed out?  Also, are you still getting the error message about missing firmware?

If you can't get any communication using the ping command above and cannot see your wireless router, let's try to undo the modprobe command above:

```
sudo rmmod b43
lsmod | grep b43
iwconfig
```After you have saved that output, try going into System > Administration > Hardware Drivers and then clicking on the b43 Broadcom driver, and the "Activate" button (shown in your attached screenshots above)- that should make the LED-like icon turn green for the b43 driver.   From what I've been reading, the b43 driver seems to work better/faster with the Broadcom 4312 and 4313 than the "STA" driver has been with Ubuntu 10.xx versions lately.

After activating the b43 hardware driver, see if you can find any wireless routers with the Network Manager icon (at upper right). If you do see your wireless router, try to connect and give it the appropriate encryption key if needed for WPA or WEP access, then see if you can access a webpage in Firefox or by running another ping command.

You will very likely need to restart the computer after activating the b43 hardware driver and try to connect again if you don't see it at first after Activating the b43 hardware driver.

edit:  There might be a problem with that "compat" module, but I will need to read up a little on the wireless-compat package- that has been several years ago for me.  If you still don't have a wireless connection but you do have a working cabled ethernet conneciton, let's try to get the Broadcom b43 firmware onto your system by running this terminal command:

```
sudo apt-get install b43-fwcutter

```Restart after that one and try connecting again.

I'll be going to sleep soon and possibly skiing tomorrow, but here are 2 good pages with Broadcom b43 information if you want to read up on that wireless interface:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access")

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by CasparGrigoriNovykh on 2010-12-06
Hello northd-tech!

I think you might have missed my post preceding the list of outputs.  I included some extra information before I got around to posting the outputs, and the information might help.  I'll be back soon with the new outputs.  Thank you again for baring with me!

---

### Post by CasparGrigoriNovykh on 2010-12-06
Activation via the Additional Drivers has not worked since the initial replacement of the STA driver for b43. 

Removal of b43 was successful (sorry, forgot to grab the output), and now iwconfig is back to listing lo, eth0, and vboxnet0; all with no wireless extensions, and the latter unwanted!  Also, upon removal, I am now looking at an icon that displays only a greyed out "Wired Network  disconnected" and an available option for VPN Connections.  Upon attempting to activate either driver, Ubuntu searches for them in the repositories, and (obviously) is unable to resolve the server.  

Previous to removing b43, the icon displayed the "device not ready, firmware missing" message.

What a headache!  haha

---

### Post by mvllc on 2010-12-28
I have a gateway mx6124 notebook and try to set up the wireless connection; I follow the instruction on the ubuntu forum and i type this code: lspci -nn | grep -i 14e4 on the terminal and this is the info shows:

mvllc@mvllc-MX6124:~$ lspci -nn | grep -i 14e4

06:04.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

So please any suggestion? Somebody that help with this.

---

### Post by Bucky Ball on 2010-12-28
All b43 requirements now in repositories.

With ethernet cable in and online go to Synaptic package manager and search for:

'b43-fwcutter' and 'firmware-b43-installer'. One of these maybe already installed.

---

### Post by PatchesTheCaveman on 2010-12-29
@CasparGrigoriNovykh:  I find it odd that you got better results with the b43 driver.  Everyone including myself seems to have better luck with the STA driver.

At any rate, you'll need to plug in via Ethernet to be able to redownload the STA driver.  If that's not possible, download one of these two files depending on which version of Ubuntu you're running at flash drive it over to the computer you need:
32-bit (x86):  [http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb)
64-bit (x86_64/amd64):  [http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb)

Then run *sudo dpkg -i bcmwl-kernel-source_5.60.246.2+bdcom-0ubuntu3_*.deb* to install the driver.

@mvllc:  Go to System > Administration > Additional Drivers in your top panel.  You should see the *Broadcom STA wireless driver*.  Click on it and click Install.  If you have still have trouble, please let us know in a new thread.  It gets confusing when we have too many different people's problems in one thread.

---

### Post by chrisman01 on 2011-03-17
so... uh... sorry for reviving a rather old thread, but I have the same issue, and my laptop doesn't have ethernet or any other way to connect to the internet other than the wireless card.

Which doesn't work >.<

Is there any way to activate the drivers without connecting to the internet?  It comes up as the Broadcom Air Force One, and I already have the drivers transferred over to the desktop via thumb drive, but no matter what I try the drivers won't activate...

---

### Post by Bucky Ball on 2011-03-18
Welcome.

You'd be way better off starting a new thread with an appropriate title and giving as much details about your specific problem as you can. ;)

---

### Post by Wazz72 on 2011-05-07
I added the legacy files in the package manager and mine worked straight away.

---

### Post by Sparnauskis on 2012-05-23
> **PatchesTheCaveman said:**
> @CasparGrigoriNovykh:  I find it odd that you got better results with the b43 driver.  Everyone including myself seems to have better luck with the STA driver.

At any rate, you'll need to plug in via Ethernet to be able to redownload the STA driver.  If that's not possible, download one of these two files depending on which version of Ubuntu you're running at flash drive it over to the computer you need:
32-bit (x86):  [http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb)
64-bit (x86_64/amd64):  [http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb)

Then run *sudo dpkg -i bcmwl-kernel-source_5.60.246.2+bdcom-0ubuntu3_*.deb* to install the driver.

@mvllc:  Go to System > Administration > Additional Drivers in your top panel.  You should see the *Broadcom STA wireless driver*.  Click on it and click Install.  If you have still have trouble, please let us know in a new thread.  It gets confusing when we have too many different people's problems in one thread.

I used 32-bit package for my acer aspire 5050 under Ubuntu 10.04 LTS, and got "Error: Dependency is not satisfiable: dkms".

Still no wireless :(

---

### Post by Bucky Ball on 2012-05-23
> **Bucky Ball said:**
> Welcome.

You'd be way better off starting a new thread with an appropriate title and giving as much details about your specific problem as you can. ;)

This thread is a year old and hasn't seen any action in that long ... you'll get more help starting a new one.

---

### Post by oldos2er on 2012-05-23
Old thread closed.

---

