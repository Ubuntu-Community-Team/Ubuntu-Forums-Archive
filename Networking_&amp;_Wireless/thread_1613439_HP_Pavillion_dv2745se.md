---
title: "HP Pavillion dv2745se"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by Axcelon on 2010-11-04
I have an HP Pavillion dv2745se and I cannot get the wifi adapter to work.

Here are the data points as per the network issue instructions:

2)

 [FONT=&quot]04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)[/FONT]  
  3)

   [FONT=&quot]~$ iwconfig[/FONT]
  
  [FONT=&quot]lo        no wireless extensions.[/FONT]
  
  
  
  [FONT=&quot]eth0      no wireless extensions.[/FONT]
  
  
  
  [FONT=&quot]eth1      IEEE 802.11  Access Point: Not-Associated   [/FONT]
  
  [FONT=&quot]          Link Quality:5  Signal level:0  Noise level:0[/FONT]
  
  [FONT=&quot]          Rx invalid nwid:0  invalid crypt:0  invalid misc:0[/FONT]
  
  
4)

   [FONT=&quot]~$ lsmod[/FONT]
  
  [FONT=&quot]Module                  Size  Used by[/FONT]
  
  [FONT=&quot]parport_pc             26058  0 [/FONT]
  
  [FONT=&quot]ppdev                   5556  0 [/FONT]
  
  [FONT=&quot]binfmt_misc             6599  1 [/FONT]
  
  [FONT=&quot]snd_hda_codec_conexant    29736  1 [/FONT]
  
  [FONT=&quot]joydev                  8735  0 [/FONT]
  
  [FONT=&quot]nouveau               516971  2 [/FONT]
  
  [FONT=&quot]snd_hda_intel          22107  2 [/FONT]
  
  [FONT=&quot]snd_hda_codec          87552  2 snd_hda_codec_conexant,snd_hda_intel[/FONT]
  
  [FONT=&quot]snd_hwdep               5040  1 snd_hda_codec[/FONT]
  
  [FONT=&quot]snd_pcm                71475  2 snd_hda_intel,snd_hda_codec[/FONT]
  
  [FONT=&quot]ttm                    56633  1 nouveau[/FONT]
  
  [FONT=&quot]drm_kms_helper         30200  1 nouveau[/FONT]
  
  [FONT=&quot]snd_seq_midi            4588  0 [/FONT]
  
  [FONT=&quot]snd_rawmidi            17783  1 snd_seq_midi[/FONT]
  
  [FONT=&quot]lib80211_crypt_tkip     7736  0 [/FONT]
  
  [FONT=&quot]snd_seq_midi_event      6047  1 snd_seq_midi[/FONT]
  
  [FONT=&quot]snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event[/FONT]
  
  [FONT=&quot]drm                   168054  4 nouveau,ttm,drm_kms_helper[/FONT]
  
  [FONT=&quot]snd_timer              19067  2 snd_pcm,snd_seq[/FONT]
  
  [FONT=&quot]r852                    9536  0 [/FONT]
  
  [FONT=&quot]sm_common               3285  1 r852[/FONT]
  
  [FONT=&quot]snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq[/FONT]
  
  [FONT=&quot]hp_wmi                  5191  0 [/FONT]
  
  [FONT=&quot]uvcvideo               55847  0 [/FONT]
  
  [FONT=&quot]nand                   34905  2 r852,sm_common[/FONT]
  
  [FONT=&quot]wl                   1959533  0 [/FONT]
  
  [FONT=&quot]videodev               43098  1 uvcvideo[/FONT]
  
  [FONT=&quot]v4l1_compat            13359  2 uvcvideo,videodev[/FONT]
  
  [FONT=&quot]snd                    49006  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/FONT]
  
  [FONT=&quot]nand_ids                2903  1 nand[/FONT]
  
  [FONT=&quot]nand_ecc                3938  1 nand[/FONT]
  
  [FONT=&quot]mtd                    18877  2 sm_common,nand[/FONT]
  
  [FONT=&quot]psmouse                59033  0 [/FONT]
  
  [FONT=&quot]agpgart                32011  2 ttm,drm[/FONT]
  
  [FONT=&quot]soundcore                880  1 snd[/FONT]
  
  [FONT=&quot]lib80211                5058  2 lib80211_crypt_tkip,wl[/FONT]
  
  [FONT=&quot]serio_raw               4022  0 [/FONT]
  
  [FONT=&quot]i2c_algo_bit            5168  1 nouveau[/FONT]
  
  [FONT=&quot]k8temp                  3132  0 [/FONT]
  
  [FONT=&quot]snd_page_alloc          7120  2 snd_hda_intel,snd_pcm[/FONT]
  
  [FONT=&quot]i2c_nforce2             5179  0 [/FONT]
  
  [FONT=&quot]video                  18712  0 [/FONT]
  
  [FONT=&quot]output                  1883  1 video[/FONT]
  
  [FONT=&quot]lp                      7342  0 [/FONT]
  
  [FONT=&quot]parport                31492  3 parport_pc,ppdev,lp[/FONT]
  
  [FONT=&quot]firewire_ohci          21106  0 [/FONT]
  
  [FONT=&quot]firewire_core          46643  1 firewire_ohci[/FONT]
  
  [FONT=&quot]sdhci_pci               6339  0 [/FONT]
  
  [FONT=&quot]sdhci                  15890  1 sdhci_pci[/FONT]
  
  [FONT=&quot]crc_itu_t               1383  1 firewire_core[/FONT]
  
  [FONT=&quot]led_class               2633  1 sdhci[/FONT]
  
  [FONT=&quot]forcedeth              49433  0 [/FONT]
  
  [FONT=&quot]ahci                   19013  0 [/FONT]
  
  [FONT=&quot]libahci                21667  3 ahci[/FONT]
  
  [FONT=&quot]pata_amd                8746  0 [/FONT]
  
  5)

This command did not return any data.

6)

   [FONT=&quot]~$ sudo lshw -C network[/FONT]
  
  [FONT=&quot]  *-network               [/FONT]
  
  [FONT=&quot]       description: Ethernet interface[/FONT]
  
  [FONT=&quot]       product: MCP67 Ethernet[/FONT]
  
  [FONT=&quot]       vendor: nVidia Corporation[/FONT]
  
  [FONT=&quot]       physical id: a[/FONT]
  
  [FONT=&quot]       bus info: pci@0000:00:0a.0[/FONT]
  
  [FONT=&quot]       logical name: eth0[/FONT]
  
  [FONT=&quot]       version: a2[/FONT]
  
  [FONT=&quot]       serial: 00:1d:72:46:0a:a7[/FONT]
  
  [FONT=&quot]       capacity: 100MB/s[/FONT]
  
  [FONT=&quot]       width: 32 bits[/FONT]
  
  [FONT=&quot]       clock: 66MHz[/FONT]
  
  [FONT=&quot]       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/FONT]
  
  [FONT=&quot]       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII[/FONT]
  
  [FONT=&quot]       resources: irq:42 memory:fc488000-fc488fff ioport:30f8(size=8) memory:fc489c00-fc489cff memory:fc489800-fc48980f[/FONT]
  
  [FONT=&quot]  *-network DISABLED[/FONT]
  
  [FONT=&quot]       description: Wireless interface[/FONT]
  
  [FONT=&quot]       product: BCM4312 802.11b/g LP-PHY[/FONT]
  
  [FONT=&quot]       vendor: Broadcom Corporation[/FONT]
  
  [FONT=&quot]       physical id: 0[/FONT]
  
  [FONT=&quot]       bus info: pci@0000:04:00.0[/FONT]
  
  [FONT=&quot]       logical name: eth1[/FONT]
  
  [FONT=&quot]       version: 01[/FONT]
  
  [FONT=&quot]       serial: 00:1a:73:e6:1a:2f[/FONT]
  
  [FONT=&quot]       width: 64 bits[/FONT]
  
  [FONT=&quot]       clock: 33MHz[/FONT]
  
  [FONT=&quot]       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless[/FONT]
  
  [FONT=&quot]       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg[/FONT]
  
  [FONT=&quot]       resources: irq:21 memory:fc000000-fc003fff[/FONT]  
      [FONT=&quot]7)[/FONT]
  
  [FONT=&quot]~$ iwlist scan[/FONT]
  
  [FONT=&quot]lo        Interface doesn't support scanning.[/FONT]
  
  
  
  [FONT=&quot]eth0      Interface doesn't support scanning.[/FONT]
  
  
  
  [FONT=&quot]eth1      Interface doesn't support scanning.[/FONT]
  
  
  
  [FONT=&quot]8)[/FONT]
  
  [FONT=&quot]~$ lsb_release -d[/FONT]
  
  [FONT=&quot]Description:      Ubuntu 10.10[/FONT]
  
  
  [FONT=&quot]9)[/FONT]
  
  [FONT=&quot]~$ uname -mr[/FONT]
  
  [FONT=&quot]2.6.35-22-generic i686[/FONT]
  
  
  [FONT=&quot]10)[/FONT]
  
  [FONT=&quot]~$ sudo /etc/init.d/networking restart[/FONT]
  
  [FONT=&quot][sudo] password for dave: [/FONT]
  
  [FONT=&quot] * Reconfiguring network interfaces...                                   [ OK ][/FONT]
  

Help!  I installed Ubuntu 10.10 because I am an audiophile and the output to USB via livesession rhythmbox was noticeably better than Windows Vista using Foobar even with the Kernel streaming plugin enabled.  But I cannot get the wifi adapter to work, and so I cannot really use Ubuntu.

The live session activated the Broadcom STA driver, but said it needed to restart to use it.  I figured ok, let's install Ubuntu onto my hard drive and then the driver will work because a restart would accept config changes.

I installed it and now the "Additional Drivers" window comes up blank!

Help!

---

### Post by jdkchem on 2010-11-04
You need to activate the Broadcom STA driver.  You will need a network connection other than the wireless.  You should have seen a warning about haing a network connection during the install.

---

### Post by Axcelon on 2010-11-04
Okay, that's fine, it said that it was recommended . . . anyway, that is not an option for me.

How are you supposed to have an internet connection when no ethernet connections are available and your wifi driver isn't working?

Is there any other solution?

---

### Post by bkratz on 2010-11-04
> **Axcelon said:**
> Okay, that's fine, it said that it was recommended . . . anyway, that is not an option for me.

How are you supposed to have an internet connection when no ethernet connections are available and your wifi driver isn't working?

Is there any other solution?

Look in the section labeled "sta -no internet access"

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Axcelon on 2010-11-06
I have tried everything listed, exactly following the steps, step-by-step, and still get nothing.

My install will not recognize anything.

No STA driver, no nVidia drivers . . .

The Live Session CD (but not when booted via USB) would activate the wifi driver, but it claimed it needed to restart, which a live session can never do--if I understand correctly.

So far I can't do any of the things I wanted to do with Ubuntu.  No Apple Lossless support, I can't play any mpeg or avi files, . . . and none of the drivers for anything work.

---

### Post by bkratz on 2010-11-06
No, it is just saying that the drivers can be installed from the live CD, not to run from it. Bring it up normally and 

" Systems installed from CDROM can simply add the install CD as a package source and install bcmwl-kernel-source, automatically installing the required dependencies. "  Go to System>>administration>> software sources and put a check  mark in "installable from CD Rom" and " [COLOR="DarkRed"]and install bcmwl-kernel-source, automatically installing the required dependencies[/COLOR] ".

---

