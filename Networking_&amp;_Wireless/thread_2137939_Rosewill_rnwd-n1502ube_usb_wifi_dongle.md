---
title: "Rosewill rnwd-n1502ube usb wifi dongle"
date: 2013-04-22
forum: Networking &amp; Wireless
---

### Post by Nukester on 2013-04-22
I recently bought a usb wifi dongle from Rosewill, model number RNWD-N1502UBE. Says it should P&P with linux but it doesn't seem to work. It uses Ralink RT5370 chipset. I type 'lsusb' in terminal and I get: 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13d3:5108 IMC Networks 
Bus 001 Device 007: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter

Any Ideas on what I can use?

Using Xubuntu 11.10.

---

### Post by marvselby on 2013-04-22
Linux sees the adapter.  That is good.  Now type "lsmod" and post the output.  That will show if the kernel module for it is loaded.  I would expect to see something like rt73usb or some such name in there.  By the way, what version of Ubuntu are you running?

---

### Post by Nukester on 2013-04-23
> **marvselby said:**
> Linux sees the adapter.  That is good.  Now type "lsmod" and post the output.  That will show if the kernel module for it is loaded.  I would expect to see something like rt73usb or some such name in there.  By the way, what version of Ubuntu are you running?

Running Xubuntu 11.10

Can't figure out how to post the output from the terminal without it being jumbled up when I post it. But I don't see anything on the output thats similar to rt73usb.

---

### Post by Nukester on 2013-04-23
Here's the output from 'lsmod':


```

Module                  Size  Used by
joydev                 17393  0 
eeepc_wmi              12949  0 
asus_wmi               19624  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
snd_hda_codec_realtek   174055  1 
arc4                   12473  2 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
ath9k                 117425  0 
rfcomm                 38139  4 
bnep                   17830  2 
mac80211              436455  1 ath9k
psmouse                87140  0 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
serio_raw              13027  0 
ppdev                  12849  0 
ath9k_common           13781  1 ath9k
ath9k_hw              391523  2 ath9k,ath9k_common
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
cfg80211              178679  3 ath9k,mac80211,ath
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
binfmt_misc            17292  1 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  414568  2 
drm_kms_helper         45466  1 i915
drm                   197692  3 i915,drm_kms_helper
snd                    62064  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
i2c_algo_bit           13199  1 i915
wmi                    18744  1 asus_wmi
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
atl1c                  36718  0 

```

---

### Post by marvselby on 2013-04-23
YIKES!  Your adapter says it has a Ralink chipset but the kernel has loaded an Atheros at9k driver.  Do you have a wireless card installed?  Please post the output of "lspci" which will tell.  Did the dongle come with a driver disk?  What version Ubuntu are you running?

---

### Post by Nukester on 2013-04-24
> **marvselby said:**
> YIKES!  Your adapter says it has a Ralink chipset but the kernel has loaded an Atheros at9k driver.  Do you have a wireless card installed?  Please post the output of "lspci" which will tell.  Did the dongle come with a driver disk?  What version Ubuntu are you running?

Yeah I'm using the onboard wifi on my netbook, I'm trying to get this rosewill adapter working on another PC that doesn't have built in wifi.

Is there anyway to change it where it uses the rosewill adapter instead of the built in one? The adapter came with linux drivers but it came with these weird complicated insttructions:

```

Build Instructions:  
====================


1> $tar -xvzf DPB_RT2870_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2870_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
     define the linux kernel source include file path LINUX_SRC
     modify to meet your need.


3> In os/linux/config.mk 
    define the GCC and LD of the target machine
    define the compiler flags CFLAGS
    modify to meet your need.
    ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
       => #>cd wpa_supplicant-x.x
       => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
    ** Build for being controlled by WpaSupplicant with Ralink Driver
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
       => #>cd wpa_supplicant-0.5.7
       => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d


4> $make
    # compile driver source code
    # To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
      => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c


5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
    
6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt2870sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up


7> unload driver    
    $/sbin/ifconfig ra0 down
    $/sbin/rmmod rt2870sta
    
```

---

### Post by marvselby on 2013-04-25
Okay, that explains the Atheros driver.  What you're gonna have to do is install the driver on the machine you intend to use the dongle on.  I'm not sure about this, but I think there's a "quick and dirty" way to get it installed.  If you connect the dongle and do an installation, I am thinking that the appropriate drivers will be loaded.  You could check this notion by booting a live CD and checking to see if you have an internet connection.  If I were doing it, I think I would use 12.04 LTS.  Of course, you would want to back up your data before doing an installation.  :D

I recently switched from a dongle to a PCI adapter because I was having a problem with disconnection and reconnection since my machine runs 24/7.  That  solved my problem.  If you're just going to use the machine sporadically, the dongle will probably be okay and hopefully, the disconnection issue has been solved, especially in the newer versions of Ubuntu.

What you're gonna have to do is screw your courage to the sticking point and build the module.  (That's the weird instructions.)  It really isn't that hard.  Here's a link that should help you.  [http://ubuntuforums.org/showthread.php?t=1800178]("http://ubuntuforums.org/showthread.php?t=1800178")

So why do we build modules?  Well, Linux has a great deal of flexibility.  What you're doing when you build a module is to tailor it specifically to your operating system.  You need one batch of code and it will work on just about any version of Linux.  Unlike Windows, you don't need a driver for a specific operating system.  Of course, the tradeoff is that you don't get to click a button; you have to use the feared prompt in a terminal window and edit some files.

Before you do anything, you have to install build-essential and linux-headers-generic.  Hopefully, you can get a wired internet connection to do that.  You can use a package manager like Synaptic or use the handy-dandy prompt to type "sudo apt-get install build-essential" and then "sudo apt-get install linux-headers-generic".

Copy the file DPB_RT2870_Linux_STA_x.x.x.x.tgz from the CD (I assume) to your desktop.  Double-click the file and allow it to extract to the desktop.  Rename the folder created with something easy to remember.  RT5370 would be a good name for it.  Open a terminal window.  You should be in your home directory so type "cd /Desktop/RT5370"  (Case is important.)  Now is a good  time to change to superuser.  ("sudo su")  Open the makefile with an editor (like gedit) "gedit Makefile".  The file probably will not need any changes but check the MODE and TARGET entries.  If you make changes, you will need to save them when you close gedit.  Then "gedit /home/(your home directory)/Desktop/RT5370/os/linux/config.mk"  In that file I think the only thing you have to changes is: 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.  Then save the file.

Now the fun.  You should still be in the RT5370 directory so all you have to do is type "make".  If you can read 4,000 words a minute, you can read what scrolls by.  Hopefully there will be no errors indicated and then you can type "make install".  Now load the module with "modprobe rt5370sta" and your wireless should be working  You can close the terminal and go have a beer.  This should work but it will not continue to work through a reboot.  You'll have to reload the driver (sudo modprobe rt5370sta) each time.  Take heart, though, there are ways to reload the driver automatically each time and carry the configuration through a kernel upgrade.

I went back to reread the instructions because I remembered a step I had to do with my module.  You need to copy the file containing the firmware for the dongle to a configuration file.  While still superuser, type "cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat".  I also noticed that they had named the module rt2870sta, so if the module doesn't load the original way, try using modprobe rt2870sta.

---

