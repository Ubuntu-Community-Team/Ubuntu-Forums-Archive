---
title: "Wirelesss not working"
date: 2011-09-19
forum: Networking &amp; Wireless
---

### Post by btophek on 2011-09-19
I purchased a Toshiba net book model N505.  It came with Windows 7 starter.  Disliking Microsoft products,  I installed Ubuntu net book I think it's version is 10.04.  I can't get the wireless to work.  I'm thinking Ubuntu doesn't have the correct drivers installed.  Where would I go to find them and what do I need?  Wireless comes preinstalled.  The controller I believe is Realtek according to the installed hardware that Ubuntu found in the computer.

Bob

---

### Post by mikewhatever on 2011-09-19
There is no such thing a the wifi driver for Toshiba netbooks. Any notebook or netbook can have a variety of wifi devices from Intel, Atheros, Broadcom, etc. Would it be too much to ask that you tell us which one is yours?

---

### Post by btophek on 2011-09-19
I believe it is an Intel.  The owners manual doesn't provide too many specifics.  I went online to do a search for the hardware inside the computer.  Realtek is the network controller.  I don't know if this helps?  There are a few Intel hardware devices inside the computer.

---

### Post by wildmanne39 on 2011-09-19
Hi, welcome to the forum! please open a terminal by hitting ctrl+alt+t then paste these commands into it, then post the results here from each command:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by btophek on 2011-09-23
```

```p { margin-bottom: 0.08in; }  DISTRIB_ID=Ubuntu  
 DISTRIB_RELEASE=10.04  
 DISTRIB_CODENAME=lucid  
 DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"  
 Linux btophek-toshiba 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux 





   	 	 	 	p { margin-bottom: 0.08in; }  btophek@btophek-toshiba:~$ sudo lshw -C network  
 [sudo] password for btophek:  
   *-network UNCLAIMED      
        description: Network controller  
        product: Realtek Semiconductor Co., Ltd.  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:07:00.0  
        version: 01  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list  
        configuration: latency=0  
        resources: ioport:2000(size=256) memory:f0100000-f0103fff  
   *-network  
        description: Ethernet interface  
        product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:09:00.0  
        logical name: eth0  
        version: 05  
        serial: b8:70:f4:60:f9:d1  
        size: 100MB/s  
        capacity: 100MB/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s  
        resources: irq:27 ioport:3000(size=256) memory:f050c000-f050cfff(prefetchable) memory:f0508000-f050bfff(prefetchable)  
 btophek@btophek-toshiba:~$ 





   	 	 	 	p { margin-bottom: 0.08in; }  btophek@btophek-toshiba:~$ lspci -nm | grep -e0280 -e 0200  
 07:00.0 "0280" "10ec" "8176" -r01 "10ec" "8184"  
 09:00.0 "0200" "10ec" "8136" -r05 "1179" "fdc0"  
 btophek@btophek-toshiba:~$ 





   	 	 	 	p { margin-bottom: 0.08in; }  btophek@btophek-toshiba:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions. 





   	 	 	 	p { margin-bottom: 0.08in; }  btophek@btophek-toshiba:~$ rfkill list all  
 btophek@btophek-toshiba:~$ 





   	 	 	 	p { margin-bottom: 0.08in; }  btophek@btophek-toshiba:~$ lsmod  
 Module                  Size  Used by  
 nls_iso8859_1           3249  1  
 nls_cp437               4919  1  
 vfat                    8901  1  
 fat                    47767  1 vfat  
 binfmt_misc             6587  1  
 ppdev                   5259  0  
 snd_hda_codec_realtek   203168  1  
 snd_hda_intel          21877  2  
 snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel  
 fbcon                  35102  71  
 snd_hwdep               5412  1 snd_hda_codec  
 tileblit                2031  1 fbcon  
 font                    7557  1 fbcon  
 bitblit                 4707  1 fbcon  
 snd_pcm_oss            35308  0  
 snd_mixer_oss          13746  1 snd_pcm_oss  
 snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss  
 softcursor              1189  1 bitblit 
 snd_seq_dummy           1338  0  
 snd_seq_oss            26726  0  
 vga16fb                11385  0  
 vgastate                8961  1 vga16fb 
 snd_seq_midi            4557  0  
 snd_rawmidi            19056  1 snd_seq_midi  
 snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi  
 joydev                  8708  0  
 i915                  282354  4  
 snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event  
 snd_timer              19098  2 snd_pcm,snd_seq  
 drm_kms_helper         29297  1 i915  
 snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq  
 snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 drm                   162471  5 i915,drm_kms_helper  
 soundcore               6620  1 snd  
 snd_page_alloc          7076  2 snd_hda_intel,snd_pcm  
 i2c_algo_bit            5028  1 i915  
 intel_agp              24177  2 i915  
 video                  17375  1 i915  
 agpgart                31724  2 drm,intel_agp  
 uvcvideo               56990  0  
 output                  1871  1 video  
 videodev               34361  1 uvcvideo  
 psmouse                63245  0  
 v4l1_compat            13251  2 uvcvideo,videodev  
 serio_raw               3978  0  
 lp                      7028  0  
 parport                32635  2 ppdev,lp  
 usb_storage            39425  1  
 ahci                   32008  2  
 r8169                  33884  0  
 mii                     4381  1 r8169  
 btophek@btophek-toshiba:~$ lsmod

---

### Post by garvinrick4 on 2011-09-23
This has been fix for toshiba mini with realtek card.
8176.
Open a terminal with wired pluged in and run these one at a time.
unplug and reboot.

```
sudo add-apt-repository ppa:lexical/hwe-wireless
```
```
sudo apt-get update
```
```
sudo apt-get install rtl8192ce-dkms
```

---

### Post by garvinrick4 on 2011-09-23
@wildmanne39
Good morning wildmanne39 was on  line at 3 AM pacific time last night and first time you were not
on line in darn near 3 weeks did you pass out at keyboard? Enjoy your day Sir.

---

### Post by wildmanne39 on 2011-09-23
Hi, I have been away from my computer most of the day and last night it crashed after I got it going, I turned it off.

Thank you for posting the solution to his issue, that should get him fixed up.

---

### Post by btophek on 2011-09-24
Thanks for all your help I appreciate it very much.  I performed the updates and of course through the wired connection I received all the new updates  for 10.04 netbook. so everything is current.  Unfortunately the wireless still does not work.  I can take the computer right to the wireless access point and it doesn't lock on.  Perhaps there is a configuration process I'm unaware of?

---

### Post by wildmanne39 on 2011-09-24
Hi, please run these commands:
```
lsmod
```
```
dmesg | grep -e wlan -e 8192
```
Thank you

---

### Post by btophek on 2011-09-24
[btophek@btophek-toshiba:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203376  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
fbcon                  35102  71 
tileblit                1999  1 fbcon
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
vga16fb                11385  0 
snd_rawmidi            19056  1 snd_seq_midi
vgastate                8961  1 vga16fb
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
joydev                  8740  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  288611  4 
drm_kms_helper         29329  1 i915
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162377  5 i915,drm_kms_helper
soundcore               6620  1 snd
i2c_algo_bit            5028  1 i915
uvcvideo               57374  0 
video                  17375  1 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
videodev               34361  1 uvcvideo
output                  1871  1 video
intel_agp              24375  2 i915
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63677  0 
serio_raw               3978  0 
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            39841  0 
r8169                  34140  0 
ahci                   32360  2 
mii                     4381  1 r8169
btophek@btophek-toshiba:~$ dmesg | grep -e wlan -e 8192
[    7.394098] r8192ce_pci: disagrees about version of symbol module_layout
btophek@btophek-toshiba:~$ 
]

---

### Post by btophek on 2011-09-25
[btophek@btophek-toshiba:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203376  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
fbcon                  35102  71 
tileblit                1999  1 fbcon
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
vga16fb                11385  0 
snd_rawmidi            19056  1 snd_seq_midi
vgastate                8961  1 vga16fb
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
joydev                  8740  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  288611  4 
drm_kms_helper         29329  1 i915
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162377  5 i915,drm_kms_helper
soundcore               6620  1 snd
i2c_algo_bit            5028  1 i915
uvcvideo               57374  0 
video                  17375  1 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
videodev               34361  1 uvcvideo
output                  1871  1 video
intel_agp              24375  2 i915
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63677  0 
serio_raw               3978  0 
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            39841  0 
r8169                  34140  0 
ahci                   32360  2 
mii                     4381  1 r8169
btophek@btophek-toshiba:~$ dmesg | grep -e wlan -e 8192
[    7.394098] r8192ce_pci: disagrees about version of symbol module_layout
btophek@btophek-toshiba:~$ 
]

---

### Post by wildmanne39 on 2011-09-25
Hi for some reason the driver is not loaded.

Did you restart your computer after you installed it?

Did you watch the terminal was there any errors?

Disconnect your wired connection then try this please:
```
sudo modprobe rtl8192ce
```
give it a few seconds to see of it comes alive, if not install the drivers again using the directions in post 6 and watch for errors it might not have installed correctly.
Thank you

---

### Post by btophek on 2011-09-25
Well the driver loaded fine with no errors.  No, I didn't restart the computer after the driver was loaded.  I had an update manager icon come up and the computer updated then I restarted the computer.  When I look for installed software I see the driver come up and it says it's installed.  I tried reinstalling it under step 6 but the terminal came back and said that it already was there and installed.  What is the code to uninstall the driver?  I'll try uninstalling it and then reinstall it to see if it works?

---

### Post by wildmanne39 on 2011-09-25
Hi, I see the problem the driver was compiled against the wrong kernel version, use software center and remove it please. 

I am not sure this may have been caused by updating after you compiled it before you restarted.

After you remove it restart your computer then try the install again in post 6 then disconnect your wired connection and restart.
Thank you

---

### Post by btophek on 2011-09-25
[btophek@btophek-toshiba:~$ sudo add-apt-repository ppa:lexical/hwe-wireless
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 88B3CE2CE934D5F973CC26C80C5CE27EA088FF1E
gpg: requesting key A088FF1E from hkp server keyserver.ubuntu.com
gpg: key A088FF1E: "Launchpad Keng-Yu's PAA" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
btophek@btophek-toshiba:~$ sudo apt-get update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                      
Ign [http://ppa.launchpad.net/lexical/hwe-wireless/ubuntu/](http://ppa.launchpad.net/lexical/hwe-wireless/ubuntu/) lucid/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Reading package lists... Done
btophek@btophek-toshiba:~$ sudo apt-get install rtl8192ce-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rtl8192ce-dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
btophek@btophek-toshiba:~$ 
]

---

### Post by btophek on 2011-09-25
Where in software center would this program be listed under?

---

### Post by btophek on 2011-09-26
I found the software and deleted it. Then restarted the computer.  I reinstalled the software as in post 6.  Then restarted the computer without the wired connection.  I went to the the wireless source, antenna, and it still doesn't work.  I'm just going to format the hard drive and start over.  Something is probably conflicting  somewhere.  Thanks for your help.  If after the reinstall and updating it still doesn't work.  I'll be back to let you know either way.

---

### Post by btophek on 2011-09-27
Hi,

Problem solved.  Thanks for all of your help.  I ended up formatting the hard drive and reloaded 10.04 netbook.  I entered in the code from post 6 and everything compiled correctly.  I can now use wireless.  Everything works great.  Thanks again.

---

### Post by wildmanne39 on 2011-09-27
Hi, I am glad it is working, if I was helpful would you please show your support for me becoming an ubuntu member by clicking on the red link in my signature and post to my thread? also would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

