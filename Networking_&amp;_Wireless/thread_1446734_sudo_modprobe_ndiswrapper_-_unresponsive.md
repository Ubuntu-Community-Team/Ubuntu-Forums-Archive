---
title: "sudo modprobe ndiswrapper - unresponsive"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by littlboz on 2010-04-04
I should say that I am a complete beginner and I read posts on this current topic but they are to over my head.

My current situation is that the command "sudo modprobe ndiswrapper" is not responding, nothing happens. I am using [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3) as my guide and the "sudo modprobe ndiswrapper" is my next step.

Here is some general information that you might ask for:
I received ndiswrapper utilities from "Synaptic Package Manager"


~I was using jaunty jackelop before hand and the instructions worked perfectly 
but I decided to update to Karmic Koala 9.10 (I first installed the cloud enterprise version and realized that was way over my head).~

---

### Post by littlboz on 2010-04-04
oh, here is some info that might be useful


[I]boswell@boswell-desktop:~$ ndiswrapper -h
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
boswell@boswell-desktop:~$ [/I]


(I think that 'devid' thing is what might be the problem
[I]

boswell@boswell-desktop:~$ ndiswrapper -l
wg311v3 : driver installed
    device (11AB:1FAA) present[/I]

---

### Post by littlboz on 2010-04-04
here is one more thing as well that might help 

boswell@boswell-desktop:~$ lspci -n
00:00.0 0500: 10de:02f1 (rev a2)
00:00.1 0500: 10de:02fa (rev a2)
00:00.2 0500: 10de:02fe (rev a2)
00:00.3 0500: 10de:02f8 (rev a2)
00:00.4 0500: 10de:02f9 (rev a2)
00:00.5 0500: 10de:02ff (rev a2)
00:00.6 0500: 10de:027f (rev a2)
00:00.7 0500: 10de:027e (rev a2)
00:02.0 0604: 10de:02fc (rev a1)
00:03.0 0604: 10de:02fd (rev a1)
00:04.0 0604: 10de:02fb (rev a1)
00:05.0 0300: 10de:0242 (rev a2)
00:09.0 0500: 10de:0270 (rev a2)
00:0a.0 0601: 10de:0261 (rev a2)
00:0a.1 0c05: 10de:0264 (rev a2)
00:0a.2 0500: 10de:0272 (rev a2)
00:0b.0 0c03: 10de:026d (rev a2)
00:0b.1 0c03: 10de:026e (rev a2)
00:0d.0 0101: 10de:0265 (rev a1)
00:0e.0 0101: 10de:0266 (rev a1)
00:10.0 0604: 10de:026f (rev a2)
00:10.1 0403: 10de:026c (rev a2)
00:14.0 0680: 10de:0269 (rev a1)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
04:06.0 0200: 11ab:1faa (rev 03)
04:07.0 0780: 14f1:2f20
04:08.0 0c00: 1106:3044 (rev 80)

---

### Post by chili555 on 2010-04-04
If you do:```
sudo modprobe ndiswrapper
```And nothing happens; that is, the cursor just pops back, that means the command was accepted and executed with no error or warning.

I thought we fixed that yesterday.

Do you see your network in Network Manager?

---

### Post by littlboz on 2010-04-04
haha, you again. Well yeh, everything was running smoothly but i reinstalled ubuntu because I wanted the 64 - bit version.

anyways, yes the curser just pops back up and where is network manager?

---

### Post by chili555 on 2010-04-04
As you said yesterday, upper-right-ish. Depending on which version you have it might look like two monitors with an **[COLOR="Red"]X[/COLOR]** or an antenna. *Left*-click it and see what you see.

---

### Post by Alfiya on 2010-04-04
have problem with wireless too

it looks just like that:
alfiya@alfiya-laptop:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module ndiswrapper not found.

i almost gave up...

---

### Post by littlboz on 2010-04-04
Nope, its got nothing

---

### Post by littlboz on 2010-04-04
hey alfiya, 

Here was my orginal thread when I had that problem with the warning error
[http://ubuntuforums.org/showthread.php?t=1446138](http://ubuntuforums.org/showthread.php?t=1446138)

however the not module ndswrapper that you posted, I have no idea

---

### Post by chili555 on 2010-04-04
> **Alfiya said:**
> have problem with wireless too

it looks just like that:
alfiya@alfiya-laptop:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module ndiswrapper not found.

i almost gave up...Please start a new thread. Please see the sticky at the top about how to get help and post your details. We'll be glad to help.

---

### Post by chili555 on 2010-04-04
> **littlboz said:**
> Nope, its got nothingPlease post:```
iwconfig
lsmod
```Thanks.

---

### Post by littlboz on 2010-04-04
boswell@boswell-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

boswell@boswell-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27296  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   8232  0 
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
parport_pc             37352  1 
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
amd64_edac_mod         26688  0 
edac_core              48876  1 amd64_edac_mod
k8temp                  5504  0 
i2c_nforce2             8168  0 
lp                     11908  0 
parport                40528  3 ppdev,parport_pc,lp
usb_storage            66304  0 
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
forcedeth              61292  0 
usbhid                 43968  0

---

### Post by chili555 on 2010-04-04
> boswell@boswell-desktop:~$ ndiswrapper -l
wg311v3 : driver installed
device (11AB:1FAA) presentThis is from post #2. Is this your current setting, or left over from yesterday? What does this tell us:```
dmesg | grep ndis
```

---

### Post by littlboz on 2010-04-04
I don't think that is possible because I deleated the partition and replaced it with the ubuntu I am using now.

When I typed in that code it did nothing

boswell@boswell-desktop:~$ dmesg | grep ndis
boswell@boswell-desktop:~$

Edit: I did install the wireless software and ndiswrapper already though.

---

### Post by chili555 on 2010-04-04
> I did install the wireless software and ndiswrapper already though.Your system doesn't think so. Did you encounter any errors or warnings as you went along? Can you please repeat from here forward to the end?> cd "WG311v3 V1.0/Driver/Windows 2000"
sudo ndiswrapper -i WG311v3.INF
installing wg311v3 ...Post any errors or warnings as you go along.

---

### Post by littlboz on 2010-04-04
boswell@boswell-desktop:~$ cd "WG311v3 V1.0/Driver/Windows 2000"
boswell@boswell-desktop:~/WG311v3 V1.0/Driver/Windows 2000$ sudo ndiswrapper -i WG311v3.INF
[sudo] password for boswell: 
driver wg311v3 is already installed
boswell@boswell-desktop:~/WG311v3 V1.0/Driver/Windows 2000$ ndiswrapper -l
wg311v3 : driver installed
    device (11AB:1FAA) present
boswell@boswell-desktop:~/WG311v3 V1.0/Driver/Windows 2000$ sudo modprobe ndiswrapper
boswell@boswell-desktop:~/WG311v3 V1.0/Driver/Windows 2000$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

boswell@boswell-desktop:~/WG311v3 V1.0/Driver/Windows 2000$ 




so, odd.

---

### Post by chili555 on 2010-04-04
> i reinstalled ubuntu because I wanted the 64 - bit version.
Did you read and follow this from the tutorial?> Getting driver files - AMD 64 architecture

If you are using 64 bit version of Ubuntu, *the above drivers will not work.* Instead, you need to get drivers for 64 bit architecture. These drivers are third party (i.e., not from the chipset manufacturer) but work fine. Instructions are in this thread on ubuntu forums; in particular, see this post. If not, I suggest you remove the driver you have and reinstall the reference 64-bit version.

---

### Post by littlboz on 2010-04-04
Right, sorry. My strategy was to go through the first process and see how it went. His link wasen't working for me but now it is. I forgot to go back to this step if the process didn't work. I'll let you know how it goes.

Edit: To remove the driver do I just delete the file?

---

### Post by chili555 on 2010-04-04
You should do:```
ndiswrapper -e wg311v3
```e is for 'erase.'

---

### Post by littlboz on 2010-04-04
boswell@boswell-desktop:~$ ndiswrapper -e wg311v3
couldn't delete /etc/ndiswrapper/wg311v3: No such file or directory

I guess that means I can install the new driver.

the directions for the 64 -bit driver ([http://www.computer-essence.com/Projects/wifi-1.html](http://www.computer-essence.com/Projects/wifi-1.html))
states the download the software from [http://www.jimbo7.com/wiki/files/good_WG311v3-driver.tgz](http://www.jimbo7.com/wiki/files/good_WG311v3-driver.tgz)

however I am a little lost on what to do at this website because it more acts like a search engine.

P.S. Thanks for still helping.

---

### Post by chili555 on 2010-04-04
The tutorial you referred us to in post #1 says to go here: [http://ubuntuforums.org/showpost.php?p=4026062&postcount=14](http://ubuntuforums.org/showpost.php?p=4026062&postcount=14)

It works for me.

Download the file to your desktop, right-click and select Extract Here. A folder will be created called 'wg311v3_ndis_amd64.' Open it and there is your 64-bit driver. Install it with:```
cd Desktop/wg311v3_ndis_amd64
ndiswrapper -i WG311v3.INF
```Then complete all the other steps on the tutorial. After you get past sudo modprobe ndiswrapper, see if it it correct with:```
ndiswrapper -l
iwconfig
```

---

### Post by littlboz on 2010-04-04
okay feel like I am close, I got the file, Then i tried your steps but I got this:

boswell@boswell-desktop:~$ cd Desktop/wg311v3_ndis_amd64
boswell@boswell-desktop:~/Desktop/wg311v3_ndis_amd64$ ndiswrapper -i WG311v3.INFcouldn't create /etc/ndiswrapper/wg311v3: Permission denied at /usr/sbin/ndiswrapper-1.9 line 194.
boswell@boswell-desktop:~/Desktop/wg311v3_ndis_amd64$

---

### Post by chili555 on 2010-04-04
'Permission denied' usually means only the supervisor is allowed to modify system files. You can temporarily gain supervisor privileges with 'sudo.'```
[COLOR="Red"]sudo[/COLOR] ndiswrapper -i WG311v3.INF
```

---

### Post by littlboz on 2010-04-04
[FONT=monospace]okay, I got the wireless to work,

I am going to reboot and see if stays 
[/FONT]

---

### Post by littlboz on 2010-04-04
okay I restarted but it dosen't want to connect again. It does recognize it however, here is a screenshot

---

### Post by chili555 on 2010-04-04
Did ndiswrapper get loaded on boot? Find out with:```
lsmod | grep ndis
```If it's not there, do:```
sudo modprobe ndiswrapper
```Now does it connect?

If so, see our thread yesterday for how to get it to load automagically on boot.

---

### Post by littlboz on 2010-04-04
okay I tried to get it to reconnect and it works. 

To get it to automatically connect i did the following:


boswell@boswell-desktop:~$ sudo ndiswrapper -m
module configuration already contains alias directive


Then I did boswell@boswell-desktop:~$ sudo gedit /etc/modules
it opened to a new termnal that stated the following:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc

---

### Post by chili555 on 2010-04-04
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc Unless you installed something I don't know about, I know of no module 'rtc.' I suggest you remove that and make the file look like:```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ndiswrapper 
```Proofread, save and close gedit. You should be all set.

---

### Post by littlboz on 2010-04-04
okay, all the wireless stuff works now.

I hope you have gained at least a fraction of the satisfaction that I  have now and that I will continue to have every time I boot my Ubuntu  Karmic Koala 9.10 64-bit now with fully operating wireless.

Thank you chili555

---

### Post by chili555 on 2010-04-04
I have indeed gained satisfaction. I hope you have gained knowledge. I hope you can install ndiswrapper correctly any time you need to. Thanks for your kind words.

---

