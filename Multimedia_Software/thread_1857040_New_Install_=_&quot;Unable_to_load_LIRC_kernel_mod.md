---
title: "New Install = &quot;Unable to load LIRC kernel modules.&quot;"
date: 2011-10-09
forum: Multimedia Software
---

### Post by fullmoonguru on 2011-10-09
I have a new install of 10.04 with MythTV.  I load LIRC with the Mythbuntu LIRC Generator & get this error when it finishes:

Loading LIRC modules                                                  [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

It's a Harmony remote set up to act as an mce remote, with an mce blaster.  Only the directional arrows work on the remote.  I have the same combo on another partition working fine.  Even if I move my hardware.conf, lircd.conf, & lircrc files to the new install, it's the same.  There must be something going on with a newer LIRC package.  Anyone know what's going on?

---

### Post by fullmoonguru on 2011-10-10
Anyone?

---

### Post by tasticorp on 2011-10-10
What kernel modules are you trying to load in /etc/lirc/hardware.conf? You could try running modprobe against each in turn to see which one won't load

---

### Post by fullmoonguru on 2011-10-10
This is what my hardware.conf file looks like:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev lirc_mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Scientific Atlanta Cable box"
TRANSMITTER_MODULES="lirc_dev lirc_mceusb2"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="scientificatlanta/general.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```I did these:

```
sudo modprobe lirc_dev lirc_mceusb
sudo modprobe lirc_dev lirc_mceusb2
```and didn't get errors.  Was that right?  I did notice that there is no lirc1 in /dev.

---

### Post by fullmoonguru on 2011-10-11
I re-posted this in the Mythbuntu forum.  

[http://ubuntuforums.org/showthread.php?p=11332691#post11332691](http://ubuntuforums.org/showthread.php?p=11332691#post11332691)

I would have moved it but it looks like I don't have that ability.

---

### Post by tasticorp on 2011-10-13
I think mceusb is gone. Try lsmod | grep mceusb Unless both lirc_mceusb* modules are listed, there was a problem.

If it isn't gone on Maverick. I'm pretty sure Natty is finished with it. I'm using a hauppauge remote and having my own troubles but I think it involves loading the ir_kbd_i2c module (may not apply to mceusb) and using devinput as a driver for lirc in hardware.conf to get your .lircrc up and running [http://forum.xbmc.org/archive/index.php/t-101151.html](http://forum.xbmc.org/archive/index.php/t-101151.html)

It might be worth trying modprobe ir_kbd_i2c debug=1; on my setup dmesg picks up remote presses but I have to map them to actual events now

Also, devices are mapped to /dev/input/event* now cat /proc/bus/input/devices should show you which event number you need to be connecting  to which you should add to hardware.conf

---

### Post by fullmoonguru on 2011-10-17
Here is what happened:  I followed the new wiki instructions [here]("http://www.mythtv.org/wiki/Hauppauge_HD-PVR") for compiling the v4l driver for my Hauppauge HD-PVR.  The new instructions are updated so I don't have to go in & edit files with the model number of my recorder.  The problem is that they make these modules all disappear:

  	 	 	 	 	```
kernel/sound/pci/trident/snd-trident.ko 
 kernel/sound/pci/ymfpci/snd-ymfpci.ko  
 kernel/sound/pci/vx222/snd-vx222.ko  
 kernel/sound/synth/snd-util-mem.ko  
 kernel/sound/synth/emux/snd-emux-synth.ko 
 kernel/sound/usb/snd-usb-audio.ko  
 kernel/sound/usb/snd-usb-lib.ko  
 kernel/sound/usb/usx2y/snd-usb-usx2y.ko 
 kernel/sound/usb/usx2y/snd-usb-us122l.ko 
 kernel/sound/usb/caiaq/snd-usb-caiaq.ko 
 kernel/sound/pcmcia/vx/snd-vxpocket.ko  
 kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko 
 kernel/sound/soc/snd-soc-core.ko  
 kernel/sound/soc/codecs/snd-soc-ad1836.ko 
 kernel/sound/soc/codecs/snd-soc-ad1938.ko 
 kernel/sound/soc/codecs/snd-soc-ad73311.ko 
 kernel/sound/soc/codecs/snd-soc-ak4104.ko 
 kernel/sound/soc/codecs/snd-soc-ak4535.ko 
 kernel/sound/soc/codecs/snd-soc-ak4642.ko 
 kernel/sound/soc/codecs/snd-soc-cs4270.ko 
 kernel/sound/soc/codecs/snd-soc-l3.ko  
 kernel/sound/soc/codecs/snd-soc-pcm3008.ko 
 kernel/sound/soc/codecs/snd-soc-spdif.ko 
 kernel/sound/soc/codecs/snd-soc-ssm2602.ko 
 kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko 
 kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko 
 kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko 
 kernel/sound/soc/codecs/snd-soc-twl4030.ko 
 kernel/sound/soc/codecs/snd-soc-uda134x.ko 
 kernel/sound/soc/codecs/snd-soc-uda1380.ko 
 kernel/sound/soc/codecs/snd-soc-wm8350.ko 
 kernel/sound/soc/codecs/snd-soc-wm8400.ko 
 kernel/sound/soc/codecs/snd-soc-wm8510.ko 
 kernel/sound/soc/codecs/snd-soc-wm8523.ko 
 kernel/sound/soc/codecs/snd-soc-wm8580.ko 
 kernel/sound/soc/codecs/snd-soc-wm8728.ko 
 kernel/sound/soc/codecs/snd-soc-wm8731.ko 
 kernel/sound/soc/codecs/snd-soc-wm8750.ko 
 kernel/sound/soc/codecs/snd-soc-wm8753.ko 
 kernel/sound/soc/codecs/snd-soc-wm8776.ko 
 kernel/sound/soc/codecs/snd-soc-wm8900.ko 
 kernel/sound/soc/codecs/snd-soc-wm8903.ko 
 kernel/sound/soc/codecs/snd-soc-wm8971.ko 
 kernel/sound/soc/codecs/snd-soc-wm8974.ko 
 kernel/sound/soc/codecs/snd-soc-wm8940.ko 
 kernel/sound/soc/codecs/snd-soc-wm8960.ko 
 kernel/sound/soc/codecs/snd-soc-wm8961.ko 
 kernel/sound/soc/codecs/snd-soc-wm8988.ko 
 kernel/sound/soc/codecs/snd-soc-wm8990.ko 
 kernel/sound/soc/codecs/snd-soc-wm8993.ko 
 kernel/sound/soc/codecs/snd-soc-wm9081.ko 
 kernel/sound/soc/codecs/snd-soc-wm-hubs.ko 
 kernel/sound/soc/codecs/snd-soc-max9877.ko 
 kernel/sound/ac97_bus.ko  
 kernel/ubuntu/aufs/aufs.ko  
 kernel/ubuntu/compcache/ramzswap.ko  
 kernel/ubuntu/compcache/xvmalloc.ko  
 kernel/ubuntu/dm-raid4-5/dm-raid45.ko  
 kernel/ubuntu/fsam7400/fsam7400.ko  
 kernel/ubuntu/iscsitarget/iscsi_trgt.ko 
 kernel/ubuntu/lirc/lirc_dev/lirc_dev.ko 
 kernel/ubuntu/lirc/lirc_atiusb/lirc_atiusb.ko 
 kernel/ubuntu/lirc/lirc_bt829/lirc_bt829.ko 
 kernel/ubuntu/lirc/lirc_ene0100/lirc_ene0100.ko 
 kernel/ubuntu/lirc/lirc_i2c/lirc_i2c.ko 
 kernel/ubuntu/lirc/lirc_igorplugusb/lirc_igorplugusb.ko 
 kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko 
 kernel/ubuntu/lirc/lirc_it87/lirc_it87.ko 
 kernel/ubuntu/lirc/lirc_ite8709/lirc_ite8709.ko 
 kernel/ubuntu/lirc/lirc_mceusb/lirc_mceusb.ko 
 kernel/ubuntu/lirc/lirc_sasem/lirc_sasem.ko 
 kernel/ubuntu/lirc/lirc_serial/lirc_serial.ko 
 kernel/ubuntu/lirc/lirc_sir/lirc_sir.ko 
 kernel/ubuntu/lirc/lirc_streamzap/lirc_streamzap.ko 
 kernel/ubuntu/lirc/lirc_ttusbir/lirc_ttusbir.ko 
 kernel/ubuntu/ndiswrapper/ndiswrapper.ko 
 kernel/ubuntu/omnibook/omnibook.ko  
 kernel/ubuntu/rtl8192se/r8192se_pci.ko  
 kernel/ubuntu/rfkill/av5100.ko  
 kernel/ubuntu/rfkill/pbe5.ko  
 kernel/arch/x86/oprofile/oprofile.ko  
 kernel/net/core/pktgen.ko  
 kernel/net/llc/llc2.ko  
 kernel/net/802/p8023.ko  
 kernel/net/802/stp.ko  
 kernel/net/802/garp.ko  
 kernel/net/sched/act_police.ko  
 kernel/net/sched/act_gact.ko  
 kernel/net/sched/act_mirred.ko  
 kernel/net/sched/act_ipt.ko  
 kernel/net/sched/act_nat.ko  
 kernel/net/sched/act_pedit.ko  
 kernel/net/sched/act_simple.ko  
 kernel/net/sched/act_skbedit.ko  
 kernel/net/sched/sch_cbq.ko  
 kernel/net/sched/sch_htb.ko  
 kernel/net/sched/sch_hfsc.ko  
 kernel/net/sched/sch_red.ko  
 kernel/net/sched/sch_gred.ko  
 kernel/net/sched/sch_ingress.ko  
 kernel/net/sched/sch_dsmark.ko  
 kernel/net/sched/sch_sfq.ko  
 kernel/net/sched/sch_tbf.ko  
 kernel/net/sched/sch_teql.ko  
 kernel/net/sched/sch_prio.ko  
 kernel/net/sched/sch_multiq.ko  
 kernel/net/sched/sch_atm.ko  
 kernel/net/sched/sch_netem.ko  
 
```

So then the LIRC install doesn't work.

I then tried the older instructions linked from that page & they didn't work either.  So I restored my old instructions (having stupidly deleted them after using the new ones but before getting LIRC to work), and it works fine.  I want to let them know about this problem, but didn't see anywhere to comment.  I'll look into contributing to the wiki & figure that out.  This is enough of a PITA even when it's working right...  

Anyway, if you have a 10.04 install with the HD-PVR box, here's what works:

  	 	 	 	 	```
sudo apt-get install build-essential mercurial linux-headers-`uname -r` 

  cd v4l-dvb
  make clean
  make
sudo make install
sudo reboot

```

You have to modify the hdpvr.h, the hdpvr-core.c, and the .config file as described in the wiki.  One more caveat: Changing all lines except "CONFIG_VIDEO_HDPVR in the .config file to "n" to save time, as it says in the wiki, caused problems for me.  When I just changed the one line needed it worked fine.

---

### Post by fullmoonguru on 2011-10-18
Arrggh!  Just realized that it's not recording.  Outside of Myth I can can a test.ts file that plays jerky with no audio.  Inside Myth it just fails.

So at this point, with  the new HDPVR-v4l instructions the recording works (I think that's what I remember), but LIRC doesn't & there seems to be other strange behavior, presumably from all those missing madules.  With my old instructions the modules are all there and LIRC works, but recording isn't happening.

I've really had enough of this.  Especially since I've done it all before and it's always worked. 

Anybody got anything for me?

---

