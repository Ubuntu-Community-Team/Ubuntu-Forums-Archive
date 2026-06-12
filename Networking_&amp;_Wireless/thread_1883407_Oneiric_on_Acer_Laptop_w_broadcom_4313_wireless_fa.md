---
title: "Oneiric on Acer Laptop w broadcom 4313 wireless fails (14e4:4727)"
date: 2011-11-19
forum: Networking &amp; Wireless
---

### Post by beaucoder on 2011-11-19
Hi Super-Sleuths!!

Oneiric 11.10 32-bit on Acer Aspire 5250 w 4313 (14e4:4727) wireless chipset. 

If no ethernet cable connected:  System locks up.
With ethernet cable connected: System will work, ethernet & wireless.

CANNOT DISCONNECT THE ETHERNET CABLE or machine locks up. Again NO wireless.

These DID NOT work:
   1. Activate / Deactivate Broadcom STA driver from Additional Drivers.
   2. bcmwl-kernel-source install via Synaptic.
   3. broadcom-sta-common / broadcom-sta-source via Synaptic
   4. firmware-b43-installer / b43-fwcutter install via Synaptic
   5. Download source code from broadcom and compile driver.
   6. Download older Natty deb pkg for b43 drivers and install.
   7. Various poke n' hope attempts from UbuntuForums and a few other places.

Any suggestions?  Laptop is brand new. As long as ethernet cable is connected we can connect.

As soon as the ethernet cable is disconnected: no wireless and lockup either while system is starting up or as soon an attempt to use the mouse is made. Locked up solid. 

Eager to hear and ready to test just about anything. Maybe even sacrifice a ram at the temple. 

Thanks,

Ken Wagner
Sugar Creek, Missouri
Where life is sweet...mostly, unless wireless matters.

---

### Post by chili555 on 2011-11-19
Let's have a look at the following terminal commands:```
lsmod | grep -e wl -e b4 -e ndis
dmesg | grep -e wl -e b4 -e ndis
ls /etc/modprobe.d
nm-tool
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Once we have gathered some additional information, we will be in a better position to proceed.

---

### Post by beaucoder on 2011-11-19
aThanks, Chili,


lsmod | grep -e wl -e b4 -e ndis gets nothing. 

dmesg | grep -e wl -e b4 -e ndis
[    0.448485] pnp 00:08: Plug and Play ACPI device, IDs SYN1b48 SYN1b00 SYN0002 PNP0f13 (active)
[   15.992219] ieee80211 phy0: wl_ops_config: change monitor mode: false (implement)
[   15.992232] ieee80211 phy0: wl_ops_config: change power-save mode: false (implement)
[   15.996358] ieee80211 phy0: wl_ops_bss_info_changed: qos enabled: false (implement)
[   15.996891] ADDRCONF(NETDEV_UP): wlan0: link is not ready

ls /etc/modprobe.d
alsa-base.conf          blacklist-cups-usblp.conf   blacklist-oss.conf
blacklist-ath_pci.conf  blacklist-firewire.conf     blacklist-rare-network.conf
blacklist.conf          blacklist-framebuffer.conf  blacklist-watchdog.conf
blacklist.conf~         blacklist-modem.conf

nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        B8:70:F4:FD:42:89

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         172.27.35.66
    Prefix:          24 (255.255.255.0)
    Gateway:         172.27.35.1

    DNS:             172.27.35.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        60:D8:19:65:03:B6

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    mollyglenn:      Infra, 00:23:69:BA:59:14, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    3104 6730:       Infra, 00:24:C8:64:69:10, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WEP
    Love2Workout1:   Infra, C0:3F:0E:25:1B:0A, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2

Happy to provide any other details.

           brcmsmac  -  This has me confused. Isn't this driver for the Mac?
  
Getting intrigued,

Ken

---

### Post by beaucoder on 2011-11-19
Full lsmod: 

lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55577  1 vfat
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_conexant    52418  1 
bcma                   19571  0 
arc4                   12473  2 
joydev                 17393  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
radeon                925020  3 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
brcmsmac              591864  0 
brcmutil               16885  1 brcmsmac
mac80211              272785  1 brcmsmac
psmouse                73673  0 
serio_raw              12990  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
cfg80211              172392  2 brcmsmac,mac80211
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    65224  1 radeon
crc_ccitt              12595  1 brcmsmac
drm_kms_helper         32889  1 radeon
k10temp                12990  0 
sp5100_tco             13495  0 
drm                   192226  5 radeon,ttm,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_piix4              13093  0 
binfmt_misc            17292  1 
i2c_algo_bit           13199  1 radeon
video                  18908  0 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
uas                    17699  0 
ahci                   21634  2 
libahci                25727  1 ahci
atl1c                  36638  0

---

### Post by chili555 on 2011-11-19
> brcmsmac - This has me confused. Isn't this driver for the Mac?It's the driver for your somewhat rare Broadcom wireless device. It requires somewhat rare firmware. Let's have a look at:```
ls /lib/firmware/brcm
```If there is no such file, then do:```
sudo apt-get install linux-firmware
sudo rmmod -f brcmsmac
sudo rmmod -f brcmutil
sudo modprobe brcmsmac
```Now is firmware no longer missing? Can you reboot without the ethernet cable?

---

### Post by beaucoder on 2011-11-19
There is code: 
ls /lib/firmware/brcm
bcm4329-fullmac-4.bin  bcm4329-fullmac-4.txt  bcm43xx-0.fw  bcm43xx_hdr-0.fw

P.S. Will be out the rest of the day. I expect to be online this evening again. 

Many thanks, Chili.

---

### Post by beaucoder on 2011-11-19
---------------------------------------------------------------------
Contents of bcm4329-fullmac-4.txt:   (In case it's helpful.)

# bcm94329sdagb board
# $Copyright (C) 2008 Broadcom Corporation$
# $id$

sromrev=3
vendid=0x14e4
devid=0x432e
# board type
boardtype=0x4ff

# board revision 1.1
boardrev=0x19

# boardflags
boardflags=0x1200

####### IMP ########
# Specify the xtalfreq if it is otherthan 38.4MHz
xtalfreq=38400

aa2g=1
aa5g=1

ag0=255

# 11g paparams
pa0b0=6003,6003,5112
pa0b1=64086,64086,64229
pa0b2=65195,65195,65081
pa0itssit=62
pa0maxpwr=66
opo=0
mcs2gpo0=0x2222
mcs2gpo1=0x2222

# sel = 1 : 20% evm  sel = 2 : 27% evm  sel = 3 : 16% evm
cckdigfilttype=0
ofdmdigfilttype=1

# 11a paparams lowband
pa1lob0=5662
pa1lob1=64130
pa1lob2=65156
# paparams midband
pa1b0=5724
pa1b1=64128
pa1b2=65167
#paparams high band
pa1hib0=5675
pa1hib1=64129
pa1hib2=65169
pa1itssit=62
pa1maxpwr=66
opo=0
mcs5gpo=0x22222222

# 11g rssi params
rssismf2g=0xa
rssismc2g=0xb
rssisav2g=0x3
bxa2g=0

# 11a rssi params
rssismf5g=0xa
rssismc5g=0xa
rssisav5g=0x3
bxa2g=0

# country code
ccode=X2
cctl=0x0

rxpo2g=1
rxpo5g=0
rxpo2gchnflg=0x1FFF

boardnum=2048
macaddr=00:90:4c:c5:34:23

#######
nocrc=1

#for mfgc
otpimagesize=182

# sdio extra configs
hwhdr=0x05ffff031030031003100000

#This generates empty F1, F2 and F3 tuple chains, and may be used if the host SDIO stack does not require the standard tuples.
RAW1=80 02 fe ff

#This includes the standard FUNCID and FUNCE tuples in the F1, F2, F3 and common CIS.
#RAW1=80 32 fe 21 02 0c 00 22 2a 01 01 00 00 c5 0 e6 00 00 00 00 00 40 00 00 ff ff 80 00 00 00 00 00 00 00 00 00 00 c8 00 00 00 00 00 00 00 00 00 00 00 00 00 ff 20 04 D0 2 29 43 21 02 0c 00 22 04 00 20 00 5A
nvramver=4.218.0.0

And now I really have to go!!!

---

### Post by chili555 on 2011-11-19
> **beaucoder said:**
> There is code: 
ls /lib/firmware/brcm
bcm4329-fullmac-4.bin  bcm4329-fullmac-4.txt  bcm43xx-0.fw  bcm43xx_hdr-0.fw

P.S. Will be out the rest of the day. I expect to be online this evening again. 

Many thanks, Chili.When you are able, please run and post:```
dmesg | grep brcm
```

---

### Post by beaucoder on 2011-11-20
Chili - Here it is. The laptop is going thru the huge post-install  update manager updates. Doing this because I tried the 64-bit Oneiric to  see if that would make a difference. It is actually a bit worse. Still  no usage unless hardwired to Internet via eth0.

dmesg | grep brcm
[   14.305837] brcmutil: module is from the staging directory, the quality is unknown, you have been warned.
[   14.307684] brcmsmac: module is from the staging directory, the quality is unknown, you have been warned.
[   14.353881] brcmsmac 0000:07:00.0: bus 7 slot 0 func 0 irq 11
[   14.353909] brcmsmac 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   14.353923] brcmsmac 0000:07:00.0: setting latency timer to 64

Ken

---

### Post by ts3 on 2011-11-25
> **chili555 said:**
> It's the driver for your somewhat rare Broadcom wireless device. It requires somewhat rare firmware.

I seem to have the same problem on my hp dm1 with Broadcom 4313 [14e4:4727].  Nothing I've tried has worked so far so I'm hoping that someone will post a solution to the OP that I can try as well.  Hope you don't mind :)

---

### Post by beaucoder on 2011-11-26
Not at all.

Ken

---

### Post by ts3 on 2011-11-26
I might have figured it out.  I'm not 100% sure because I don't actually have wireless at home but now I can see all the neighbours' wireless networks & they prompt me for a password when I click on one so at least there's some progress.  Will try to explain the steps & my reasoning below and if more experienced users can add to my post or correct me please do so.

I am running Ubuntu 11.10 64-bit on an hp dm1 4010us, single boot (ditched W7 out of the window promptly).  My wireless is Broadcom 4313 (14e4:4727), same as the OP's, and the results from the commands the OP ran were basically the same, the kernel device was brmsmac and I was showing status as either "disconnected" or "device not ready" depending on whether I'd messed with the STA drivers that come with the install or not.

From what I understand if one has Broadcom wireless then one can 1) use the b43 driver (can get them through Ubuntu Software Centre) or 2) use the Broadcom proprietary drivers.  Option 1) does not support BCM4313 so that's out.  Trying 2) by going through System Info &#8594; Additional Drivers and activating the default doesn't work, that's why we are here.  My guess is that trying that step installs the brcmsmac driver, which does not work and messes up the wireless; the Broadcom driver for 4313 4727(based on Broadcom's website) is called wl.   
 

 Broadcom has a good[FONT=Courier New] readme.txt[/FONT] on its website with the linux STA drivers ([http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)) that explains how to make the whole thing from scratch but I didn't feel quite up to this yet.  The [FONT=Courier New]readme.tx[/FONT]t also has a little subheading called [FONT=Courier New]Fresh Installation[/FONT] that explains how to remove conflicts with the b43 install and other artefacts that unfortunately do not work for us:[INDENT][FONT=Courier New]  Fresh installation: (from Broadcom's readme.txt) 
[/FONT][/INDENT][INDENT][FONT=Courier New]1: Remove any other drivers for the Broadcom wireless device.  There are several other drivers (besides this one) that can drive  Broadcom 802.11 chips such as b43, bcma and ssb. They will conflict with  this driver and need to be uninstalled before this driver can be installed. Any previous revisions of the wl driver also need to be removed.  

Note: On some systems such as Ubuntu 9.10, the ssb module may load during boot even though it is blacklisted (see note under Common Issues on how to resolve this. Nevertheless, ssb still must be removed (by hand or script) before wl is loaded. 

The wl driver will not function  properly if ssb the module is loaded.  

# lsmod  | grep "b43\|ssb\|bcma\|wl"  

If any of these are installed, remove them: 
# rmmod b43 
# rmmod ssb 
# rmmod bcma 
# rmmod wl  

To blacklist these drivers and prevent them from loading in the future: 
# echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf 
# echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf 
# echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf [/FONT]
[/INDENT]I did the [FONT=Courier New]lsmod[/FONT] and the [FONT=Courier New]rmmod[/FONT] commands but didn't start blacklisting through the terminal right away.   

 Instead I went to the [FONT=Courier New]/etc/modprobe.d/blacklist.conf[/FONT] file and looked around a bit, it's quite interesting.   Plus it's a read-only so one can't mess up too much by just opening.  It blacklists a BCM43xx b/c it has been replaced by b43 and ssb, something that's not true for people like us with BCM 4313.  There is also a file called[FONT=Courier New] blacklist-local.conf[/FONT] which blacklists wl.  I reckon that was created by my attempts to install b43.   
 
 I googled a bit more and found some helpful answers on the launchpad:
 
 [https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/174596](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/174596)

[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/178522](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/178522)
 
 Both strings explain how to resolve conflicts between bcma or brcmsmac and wl drivers: by blacklisting the conflicting drivers so that wl can run.  I figured I'd also have to un-blacklist the wl driver if I want it to work.

 I edited the files by opening them from the terminal (opening through the regular file manager does not work, the files are read-only for regular users so one needs sudo):
 
[FONT=Courier New]  gksudo gedit /etc/modprobe.d/blacklist.conf[/FONT]
 
which opens the text editor and added  

 [FONT=Courier New]blacklist bcma
 blacklist brmcsmac  
[/FONT]  
Then:
 
[FONT=Courier New]gksudo gedit /etc/modprobe.d/blacklist-local.conf[/FONT]
 
 and added a # in front of blacklist wl so the line became
 
[FONT=Courier New]# blacklist wl[/FONT]
 
 which from what I understand makes it a mere comment.
 
 I also went to System Info &#8594; Additional Drivers and removed the Broadcom STA driver, then went to Ubuntu Software Centre and removed the bcmwl-kernel-source.  At the end we want it to run but I thought I'd re-install after re-booting.  
 
 Then rebooted and reinstalled bcmwl-kernel-source and then broadcom-sta-source and broadcom-sta-common for good measure.  All those packages come up in the Ubuntu Software Centre if one types “bcm” in the search box. Then rebooted again & the neighbourhood wireless networks popped up like a charm.  Again, I don't know if I'll actually be able to connect – will drive to Starbucks tomorrow & give it a try.   At least I can see something and am using the right driver.
 
 One last thing – trying to fiddle with the Bluetooth settings messes the newly-hatched wireless up (sigh).  I'm keeping the Bluetooth off and will try to find a way to disable it permanently.
 
 Sorry for the long post: I am fairly new to Linux and had to work things out from scratch.  When someone writes “blacklist the driver” this is rather meaningless to me.  So I wrote out the steps with explanations hoping that it might help other new users with the same blasted driver.
 
 Again, if more experienced users want to correct or add to my post please do so.

To Ken: please let me know if you try this - I'd be chuffed to bits if it actually works for someone else.

---

### Post by beaucoder on 2011-11-27
Hi Guyz!!!

VERY GOOD NEWS, INDEED!!!   Problem is now fixed.

After all sorts of frustrations and aggravations, I came across a suggestion to set my Acer Aspire 5520 BIOS boot sequence to have the "net boot" as the first boot device entry. This is an Atheros selecton from the boot sequence selection menu for boot devices. 

As soon as I did this all the lockups, freezes and crazy mandatory Ethernet hard wire connection at all times went away. 

My heartfelt gratitude to the gang on Launchpad. Hooray!!!

Read all about it here: [https://answers.launchpad.net/ubuntu/+source/lightdm/+question/175874](https://answers.launchpad.net/ubuntu/+source/lightdm/+question/175874)

Ubuntu is (after much scrutiny, sweat, gritted teeth and wry asides) pretty awesome. Have always found a way to make it work. (So far.) 

Thanks for everyone's help.

Ken Wagner
Sugar Creek, Missouri
Where life is sweet....once again.:grin:

---

### Post by ts3 on 2011-11-28
Glad you fixed  your wireless :)  Mine works too, I am posting via wireless connection as we speak.  So it looks like completely different solutions to different problems with the same card/drive.  I might re-post my issue/solution as a separate post to make it easier to find for people with hp dm1 laptops, if you don't mind :)

Cheers,
TS

---

