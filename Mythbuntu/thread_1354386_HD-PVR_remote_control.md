---
title: "HD-PVR remote control"
date: 2009-12-13
forum: Mythbuntu
---

### Post by jmlott on 2009-12-13
I am running mythbuntu 9.10 on an Asrock ION 330HT (2nd gen) with a Hauppauge 1212 HD-PVR (rev E1). I have everything set up perfectly except the remote control.

I have done extensive research on the topic over the past week and it seems that certain select people have gotten it to work. All of the instructions I have found have been segmented across multiple sites, forums and mailing lists. I have yet to see a definitive list of steps to take to make this work, and I hope someone can help me with that.

I would like to get both the receiver and blaster working, but at this point, I would settle for one or the other.

Currently, I am having trouble getting the lirc modules to create a device at /dev/lirc0. I have gotten it to work with one of the methods I tried a couple of days ago, but have since lost it and cant get it back. I have patched both lirc and the hdpvr driver with the instructions from Jarod Wilson's posts to the mythtv-users list. When I modprobe lirc_zilog, it should create /dev/lirc0, but it does nothing. All I get is this output in the syslog:

```
Dec 13 20:04:54 mythbox kernel: [18281.082167] lirc_dev: IR Remote Control driver registered, major 61
Dec 13 20:04:54 mythbox kernel: [18281.084653] lirc_zilog: Zilog/Hauppauge IR driver initializing
Dec 13 20:04:54 mythbox kernel: [18281.088501] lirc_zilog: initialization complete
```

```
ls /dev/lirc*
/dev/lircd
```

```
lsmod|grep lirc
lirc_zilog             15504  0
lirc_dev               10804  1 lirc_zilog
```

Is there anyone who has gotten this working and can help?

---

### Post by Jumping_jackas on 2009-12-13
I will be watching for an answer here as well. I am interested in what you set in your backend for PVR-1212 as I can not even get video on my frontend.

---

### Post by jmlott on 2009-12-14
As far as video is concerned, it worked out of the box with very little trouble in Karmic. At least after I put it on a Windoze box to update the firmware. If you havent tried that, I would suggest it. Other than that, just make sure you have loaded the driver with 
```
sudo modprobe hdpvr
```

Make sure you have followed these guidelines from the mythwiki as well:
**Important Note:** You must set a channel change script for the HD-PVR to work properly. If you don't care about channel changes, you can set it to /bin/true, but there absolutely must be a channel change script defined. 
**Important Note 2:** You must leave Preset tuner to channel empty or LiveTV and channel changes will not work

---

### Post by jmlott on 2009-12-16
Ok, so after trying every single method described on the entirety of the webz, I am convinced either I have faulty hardware or everyone that has claimed to have it working is a liar [I kid ;)]. I even tried a Fedora Core 12 live cd that people claimed works out of the box with no avail. It gave me more info in the logs when loading the lirc_zilog driver, but still wouldnt create a /dev/lirc*.

I have admitted defeat for now, until an actual working driver is included in a kernel.

I still have a dire need for a working remote and IR blaster. Can anyone offer a suggestion for a good usb solution that includes both? My box has no external serial port or room for expansion cards, so usb is my only option. If I have to get a separate receiver/blaster, that's fine, but I would prefer an all-in-one.

---

### Post by killrmantis on 2009-12-17
Don't exist eh?  :-)  My HD-PVR begs to differ!  I have an HD-PVR running Mythbuntu 9.10 with patched drivers.  So far it's been great!

Boot FC12 with the HD-PVR connected and modprobe lirc_zilog.  What do you get from dmesg? ```
dmesg |grep zilog
```

---

### Post by jmlott on 2009-12-18
Well, then.... so apparently, I didnt spend quite enough time snopping around in FC12 to see why it didnt work last time. If I had actually checked the logs instead of quitting after loading the driver didnt create /dev/lirc0, I would have seen the error msg about the firmware being missing. (I can be dumb and impatient at times)

```
[root@localhost Downloads]# cp haup-ir-blaster.bin /lib/firmware
[root@localhost Downloads]# modprobe lirc_zilog
root@localhost Downloads]# lsmod|grep lirc
lirc_zilog             14212  0 
lirc_dev               10772  1 lirc_zilog
i2c_core               23120  8 lirc_zilog,hdpvr,v4l2_common,videodev,i2c_nforce2,nouveau,drm,i2c_algo_bit
[root@localhost Downloads]# ls /dev/lirc*
/dev/lirc0
[root@localhost Downloads]# dmesg|grep lirc
lirc_dev: IR Remote Control driver registered, major 249 
lirc_zilog: Zilog/Hauppauge IR driver initializing
lirc_zilog: chip found with RX and TX
lirc_dev: lirc_register_driver: sample_rate: 0
lirc_zilog: Zilog/Hauppauge IR blaster firmware version 2.1.0 loaded
lirc_zilog: initialization complete
```


Well, thankyou for getting me headed back in the right direction. At least I know now that the hardware is fine.

irw isn't capturing any keypresses in FC12 right now, but that could be because I dont have lirc set up properly. I cant remember if it needs all of the config files to run irw or not. Either way, I am certainly miles ahead of where I was a few days ago.

You didn't happen to write down the steps you tool to make it work under mythbuntu, did you? I could definitely use more help on that side of things. In all of the segmented instructions I read for patching the drivers, I probably did something wrong. 

Thanks for helping!

Matt

---

### Post by Jumping_jackas on 2009-12-18
As a complete DOLT i eagerly await the successful conclusion to the IR blaster from the PVR-1212 to control the DCT-6200 Motorola STB. I would love to see a step by step procedure for setting up my Mythbuntu 9.10 backend.

PLEASE PLEASE PLEASE

---

### Post by killrmantis on 2009-12-28
Hopefully this helps!  I'm an amateur wiki contributor so keep comments constructive please.  I sure would appreciate everyone's feedback regarding potential errors or rough spots in the guide.

[http://www.mythtv.org/wiki/Hauppauge_HD-PVR#IR_Transmitter_Support](http://www.mythtv.org/wiki/Hauppauge_HD-PVR#IR_Transmitter_Support)

This wiki section includes all the links someone needs to take something like Mythbuntu 9.10 from install to configuring full HD-PVR IR blaster support.

#edit
You'll also need a channel changer script (example below.)

 > #!/bin/bash
   
  irsend="irsend"
  SEND_ONCE="SEND_ONCE"
  remote="blaster"
  keyprefix="0_125_KEY_"
   
  for ((i=0 ; i<${#1} ; i++)); do
   echo $irsend $SEND_ONCE $remote $keyprefix${1:i:1}
   $irsend $SEND_ONCE $remote $keyprefix${1:i:1}
  done
  

---

### Post by jmlott on 2009-12-29
Hey man, I **really** appreciate you updating the wiki with that info. That is awesome of you!

I am at work right now, so I cant do any testing until I get home tonight, but I am already ssh'd into my box compiling the modules. The guide seems pretty clear so far. I'll update with my progress later.

Thanks again!!

---

### Post by jmlott on 2009-12-29
The hdpvr and zilog drivers compiled like a champ and everything appears to be working (though I cant see if I have a blinking LED or not yet since Im not home).

I did run into one problem though...

I have an mceusb remote that I need to compile in as well. Your instructions were fairly vague on where to find a source that will compile cleanly into the new lirc_dev. Clearly the one I am using is not compatible. I modified the Makefile to compile lirc_mceusb and copied over lirc_mceusb.c (I even pulled some of the iclude paths from lirc_zilog.c into it), but make errors out on me.

Do you know of a good place to get a working source file from?

Error from make:

```
make
make CONFIG_LIRC_MCEUSB=m -C /lib/modules/2.6.31-16-generic-pae/build M=/home/mythbox/lirc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic-pae'
  CC [M]  /home/mythbox/lirc/lirc_dev.o
  CC [M]  /home/mythbox/lirc/lirc_mceusb.o
/home/mythbox/lirc/lirc_mceusb.c:290: error: expected specifier-qualifier-list before ‘lirc_t’
/home/mythbox/lirc/lirc_mceusb.c: In function ‘mceusb_dev_printdata’:
/home/mythbox/lirc/lirc_mceusb.c:340: error: ‘struct mceusb_dev’ has no member named ‘flags’
/home/mythbox/lirc/lirc_mceusb.c: In function ‘request_packet_async’:
/home/mythbox/lirc/lirc_mceusb.c:410: error: ‘URB_ASYNC_UNLINK’ undeclared (first use in this function)
/home/mythbox/lirc/lirc_mceusb.c:410: error: (Each undeclared identifier is reported only once
/home/mythbox/lirc/lirc_mceusb.c:410: error: for each function it appears in.)
/home/mythbox/lirc/lirc_mceusb.c:414: error: ‘struct mceusb_dev’ has no member named ‘send_flags’
/home/mythbox/lirc/lirc_mceusb.c: In function ‘mceusb_ir_open’:
/home/mythbox/lirc/lirc_mceusb.c:486: error: ‘MOD_INC_USE_COUNT’ undeclared (first use in this function)
/home/mythbox/lirc/lirc_mceusb.c:487: error: ‘struct mceusb_dev’ has no member named ‘flags’
/home/mythbox/lirc/lirc_mceusb.c:490: error: ‘struct mceusb_dev’ has no member named ‘flags’
/home/mythbox/lirc/lirc_mceusb.c: In function ‘mceusb_ir_close’:
/home/mythbox/lirc/lirc_mceusb.c:507: error: ‘struct mceusb_dev’ has no member named ‘flags’
/home/mythbox/lirc/lirc_mceusb.c:508: error: ‘struct mceusb_dev’ has no member named ‘lock’
/home/mythbox/lirc/lirc_mceusb.c:509: error: ‘struct mceusb_dev’ has no member named ‘flags’
/home/mythbox/lirc/lirc_mceusb.c:510: error: ‘struct mceusb_dev’ has no member named ‘lock’
/home/mythbox/lirc/lirc_mceusb.c:512: error: ‘MOD_DEC_USE_COUNT’ undeclared (first use in this function)
/home/mythbox/lirc/lirc_mceusb.c: In function ‘send_packet_to_lirc’:
/home/mythbox/lirc/lirc_mceusb.c:517: error: ‘struct mceusb_dev’ has no member named ‘lircdata’
/home/mythbox/lirc/lirc_mceusb.c:519: error: ‘struct mceusb_dev’ has no member named ‘lircdata’
/home/mythbox/lirc/lirc_mceusb.c:521: error: ‘struct mceusb_dev’ has no member named ‘lircdata’
/home/mythbox/lirc/lirc_mceusb.c: In function ‘mceusb_process_ir_data’:
/home/mythbox/lirc/lirc_mceusb.c:532: error: ‘struct mceusb_dev’ has no member named ‘flags’
/home/mythbox/lirc/lirc_mceusb.c:539: error: ‘struct mceusb_dev’ has no member named ‘is_pulse’
/home/mythbox/lirc/lirc_mceusb.c:541: error: ‘struct mceusb_dev’ has no member named ‘is_pulse’
/home/mythbox/lirc/lirc_mceusb.c:545: error: ‘struct mceusb_dev’ has no member named ‘lircdata’
/home/mythbox/lirc/lirc_mceusb.c:547: error: ‘struct mceusb_dev’ has no member named ‘lircdata’
/home/mythbox/lirc/lirc_mceusb.c:547: error: ‘struct mceusb_dev’ has no member named ‘is_pulse’
/home/mythbox/lirc/lirc_mceusb.c:561: error: ‘struct mceusb_dev’ has no member named ‘is_pulse’
/home/mythbox/lirc/lirc_mceusb.c:564: error: ‘struct mceusb_dev’ has no member named ‘is_pulse’
/home/mythbox/lirc/lirc_mceusb.c:570: error: ‘struct mceusb_dev’ has no member named ‘lircdata’
/home/mythbox/lirc/lirc_mceusb.c:573: error: ‘struct mceusb_dev’ has no member named ‘lircdata’
/home/mythbox/lirc/lirc_mceusb.c:573: error: ‘struct mceusb_dev’ has no member named ‘is_pulse’
/home/mythbox/lirc/lirc_mceusb.c: In function ‘mceusb_dev_recv’:
/home/mythbox/lirc/lirc_mceusb.c:620: error: ‘URB_ASYNC_UNLINK’ undeclared (first use in this function)
/home/mythbox/lirc/lirc_mceusb.c:630: error: ‘struct mceusb_dev’ has no member named ‘send_flags’
/home/mythbox/lirc/lirc_mceusb.c:631: error: ‘struct mceusb_dev’ has no member named ‘send_flags’
/home/mythbox/lirc/lirc_mceusb.c: In function ‘mceusb_transmit_ir’:
/home/mythbox/lirc/lirc_mceusb.c:663: error: ‘lirc_t’ undeclared (first use in this function)
/home/mythbox/lirc/lirc_mceusb.c:663: error: expected ‘;’ before ‘wbuf’
/home/mythbox/lirc/lirc_mceusb.c:664: warning: ISO C90 forbids mixed declarations and code
/home/mythbox/lirc/lirc_mceusb.c:682: error: ‘wbuf’ undeclared (first use in this function)
/home/mythbox/lirc/lirc_mceusb.c:688: error: ‘struct mceusb_dev’ has no member named ‘transmitter_mask’
/home/mythbox/lirc/lirc_mceusb.c: In function ‘set_transmitter_mask’:
/home/mythbox/lirc/lirc_mceusb.c:748: error: ‘struct mceusb_dev’ has no member named ‘flags’
/home/mythbox/lirc/lirc_mceusb.c:753: error: ‘struct mceusb_dev’ has no member named ‘transmitter_mask’
/home/mythbox/lirc/lirc_mceusb.c:756: error: ‘struct mceusb_dev’ has no member named ‘transmitter_mask’
/home/mythbox/lirc/lirc_mceusb.c: In function ‘set_send_carrier’:
/home/mythbox/lirc/lirc_mceusb.c:768: error: ‘struct mceusb_dev’ has no member named ‘carrier_freq’
/home/mythbox/lirc/lirc_mceusb.c:771: error: ‘struct mceusb_dev’ has no member named ‘carrier_freq’
/home/mythbox/lirc/lirc_mceusb.c:783: error: ‘struct mceusb_dev’ has no member named ‘carrier_freq’
/home/mythbox/lirc/lirc_mceusb.c: In function ‘mceusb_gen1_init’:
/home/mythbox/lirc/lirc_mceusb.c:899: error: ‘struct mceusb_dev’ has no member named ‘is_pulse’
/home/mythbox/lirc/lirc_mceusb.c: In function ‘mceusb_dev_probe’:
/home/mythbox/lirc/lirc_mceusb.c:1058: error: ‘lirc_t’ undeclared (first use in this function)
/home/mythbox/lirc/lirc_mceusb.c:1090: error: ‘struct mceusb_dev’ has no member named ‘lock’
/home/mythbox/lirc/lirc_mceusb.c:1091: error: ‘struct mceusb_dev’ has no member named ‘wait_out’
/home/mythbox/lirc/lirc_mceusb.c:1124: error: ‘struct mceusb_dev’ has no member named ‘flags’
/home/mythbox/lirc/lirc_mceusb.c:1125: error: ‘struct mceusb_dev’ has no member named ‘flags’
/home/mythbox/lirc/lirc_mceusb.c:1126: error: ‘struct mceusb_dev’ has no member named ‘flags’
/home/mythbox/lirc/lirc_mceusb.c:1127: error: ‘struct mceusb_dev’ has no member named ‘flags’
/home/mythbox/lirc/lirc_mceusb.c:1130: error: ‘struct mceusb_dev’ has no member named ‘lircdata’
/home/mythbox/lirc/lirc_mceusb.c:1131: error: ‘struct mceusb_dev’ has no member named ‘is_pulse’
/home/mythbox/lirc/lirc_mceusb.c:1158: error: ‘struct mceusb_dev’ has no member named ‘flags’
/home/mythbox/lirc/lirc_mceusb.c:1187: error: ‘struct mceusb_dev’ has no member named ‘flags’
/home/mythbox/lirc/lirc_mceusb.c: In function ‘mceusb_dev_disconnect’:
/home/mythbox/lirc/lirc_mceusb.c:1228: error: ‘struct mceusb_dev’ has no member named ‘wait_out’
/home/mythbox/lirc/lirc_mceusb.c:1230: error: ‘struct mceusb_dev’ has no member named ‘lock’
/home/mythbox/lirc/lirc_mceusb.c:1234: error: ‘struct mceusb_dev’ has no member named ‘lock’
/home/mythbox/lirc/lirc_mceusb.c: At top level:
/home/mythbox/lirc/lirc_mceusb.c:1259: error: implicit declaration of function ‘LIRC_THIS_MODULE’
/home/mythbox/lirc/lirc_mceusb.c:1259: error: expected expression before ‘.’ token
/home/mythbox/lirc/lirc_mceusb.c:1260: error: request for member ‘name’ in something not a structure or union
/home/mythbox/lirc/lirc_mceusb.c:1308: warning: data definition has no type or storage class
/home/mythbox/lirc/lirc_mceusb.c:1308: warning: type defaults to ‘int’ in declaration of ‘EXPORT_NO_SYMBOLS’
make[2]: *** [/home/mythbox/lirc/lirc_mceusb.o] Error 1
make[1]: *** [_module_/home/mythbox/lirc] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic-pae'
make: *** [all] Error 2
```

Makefile:

```
# Makefile for the lirc drivers.
#

# Each configuration option enables a list of files.

obj-$(CONFIG_LIRC_DEV)          += lirc_dev.o
# obj-$(CONFIG_LIRC_BT829)      += lirc_bt829.o
# obj-$(CONFIG_LIRC_ENE0100)    += lirc_ene0100.o
# obj-$(CONFIG_LIRC_I2C)                += lirc_i2c.o
# obj-$(CONFIG_LIRC_IGORPLUGUSB)        += lirc_igorplugusb.o
# obj-$(CONFIG_LIRC_IMON)               += lirc_imon.o
# obj-$(CONFIG_LIRC_IT87)               += lirc_it87.o
# obj-$(CONFIG_LIRC_ITE8709)    += lirc_ite8709.o
obj-$(CONFIG_LIRC_MCEUSB)       += lirc_mceusb.o
# obj-$(CONFIG_LIRC_PARALLEL)   += lirc_parallel.o
# obj-$(CONFIG_LIRC_SASEM)      += lirc_sasem.o
# obj-$(CONFIG_LIRC_SERIAL)     += lirc_serial.o
# obj-$(CONFIG_LIRC_SIR)                += lirc_sir.o
# obj-$(CONFIG_LIRC_STREAMZAP)  += lirc_streamzap.o
# obj-$(CONFIG_LIRC_TTUSBIR)    += lirc_ttusbir.o
#obj-$(CONFIG_LIRC_ZILOG)       += lirc_zilog.o

all:
        make CONFIG_LIRC_MCEUSB=m -C /lib/modules/$(shell uname -r)/build M=$(shell pwd) modules

clean:
        make -C /lib/modules/$(shell uname -r)/build M=$(shell pwd) clean
```

lirc_mceusb.c attached

---

### Post by killrmantis on 2009-12-29
I've attached the lirc drivers that come with Fedora.  They should be compatible.

Yea that part of the guide is vague because it's only theory.  I don't have my rig setup like that so I didn't have a real world example to speak of.  I have a friend that's working on a setup exactly like yours.  He's struggling to get LIRC to tell the difference between the remote and the HD-PVR.  Definitely still a WIP in that regard.

---

### Post by jmlott on 2009-12-30
Thanks for the complete set of drivers. Copying over lirc_mceusb.c from there worked like a charm. I now have my remote working again anyway. I still have yet to see the LED blink on the blaster though. I cant figure out why, unless it's bad hardware. Correct me if I'm wrong, but it should blink regardless of what codes it is sending, right? In other words, if I have hardware.conf set up just like your example and have the lircd.conf you linked to in place and can run irsend with no errors, I should see a blinking LED on the blaster.

If there's a chance it may still be software, I can post whatever files I need to in order for you to get a better idea of where I'm going wrong.

Thanks again for all your help!

---

### Post by killrmantis on 2009-12-30
It blinks when it sends something.  You're limited to a fixed codeset so as long as you've sent something it understands to the correct port it will blink.

Having a system with remote and blaster is a little trickier.  I have a friend that's still trying to iron out the kinks.  He hasn't quite got it yet.

You should be getting an error from irsend and/or dmesg if it's not sending.  You might try it without the remote configured.  (Changing hardware.conf and lircd.conf.)

---

### Post by joshuad156 on 2009-12-31
Hi there, killrmantis has been helping me get my HDPVR working with lirc.  However, it appears getting both the blaster and the remote working together is a struggle, to put it gently. :)

As killrmantis has said, I think I have the same setup as you so you may be experiencing my problem.  The root of which is caused by an Ubuntu/LIRC bug.

[https://bugs.launchpad.net/mythbuntu/+bug/477988](https://bugs.launchpad.net/mythbuntu/+bug/477988)

To get around this I did the following:

In /etc/lirc/hardware.conf, change the following:
> TRANSMITTER_SOCKET=""to
> TRANSMITTER_SOCKET="/var/run/lirc/lircd1"and then in your channel script change the following:
> irsend="irsend"to 
> irsend="irsend --device=/var/run/lirc/lircd11"(that's not a typo, it looks like eleven and not one, thanks to the above linked bug)

After that, restart lirc
> sudo /etc/init.d/lirc restartIf you still get no blinking LED on your blaster, then maybe you have a bad transmitter???  Like killrmantis says, if you run, for example, the channel changing script he provided, you should get some kind of message back.  I was getting 'transmission failed' before I fixed the above problem when I ran my change script.

---

### Post by jmlott on 2009-12-31
Well, I certainly appreciate all the help. It appears my transmitter is bad, though. Nothing I do will produce a blinking LED. I have taken everything relating to the remote out and just have the transmitter stuff left in. I am getting no error messages at all. Everything seems to be running fine, just no transmit.

I might try plugging it in to my gf's laptop since it is the only Windows PC in the house and see if I get anything there. That should be the ultimate test.

Oh well, thanks anyway.

---

### Post by grygub on 2010-10-31
This thread has been dead for awhile now but seems to be the best place for this question. I am running 10.10 and trying to get the blaster working on the hd-pvr. I am using the the guide at the [mythtv wiki]("http://www.mythtv.org/wiki/Hauppauge_HD-PVR#IR_Transmitter_Support")
when i attempt to use the make command i get the following errors
```
grygub@myth-livingroom:~/Downloads/hdpvr-blaster-drivers/hdpvr$ sudo make
make -C /lib/modules/2.6.35-22-generic/build M=/home/grygub/Downloads/hdpvr-blaster-drivers/hdpvr modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/grygub/Downloads/hdpvr-blaster-drivers/hdpvr/hdpvr-video.o
/home/grygub/Downloads/hdpvr-blaster-drivers/hdpvr/hdpvr-video.c: In function ‘hdpvr_free_queue’:
/home/grygub/Downloads/hdpvr-blaster-drivers/hdpvr/hdpvr-video.c:95: error: implicit declaration of function ‘usb_buffer_free’
/home/grygub/Downloads/hdpvr-blaster-drivers/hdpvr/hdpvr-video.c: In function ‘hdpvr_alloc_buffers’:
/home/grygub/Downloads/hdpvr-blaster-drivers/hdpvr/hdpvr-video.c:146: error: implicit declaration of function ‘usb_buffer_alloc’
/home/grygub/Downloads/hdpvr-blaster-drivers/hdpvr/hdpvr-video.c:147: warning: assignment makes pointer from integer without a cast
/home/grygub/Downloads/hdpvr-blaster-drivers/hdpvr/hdpvr-video.c: In function ‘hdpvr_poll’:
/home/grygub/Downloads/hdpvr-blaster-drivers/hdpvr/hdpvr-video.c:522: error: implicit declaration of function ‘video_is_unregistered’
make[2]: *** [/home/grygub/Downloads/hdpvr-blaster-drivers/hdpvr/hdpvr-video.o] Error 1
make[1]: *** [_module_/home/grygub/Downloads/hdpvr-blaster-drivers/hdpvr] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [all] Error 2

```

Does anyone know what this means and what i can do about it?
thanks

---

### Post by killrmantis on 2010-11-01
Where did you get that source from?

Those are compiler errors which means it's defective code (unlikely) or somehow you got one piece that doesn't match another piece.

---

### Post by grygub on 2010-11-03
The mythtv wiki for the hd-pvr ([http://www.mythtv.org/wiki/Hauppauge_HD-PVR#IR_Transmitter_Support]("http://www.mythtv.org/wiki/Hauppauge_HD-PVR#IR_Transmitter_Support")) has instructions on how to get the ir transmitter working. One step has a link labeled [patched hd-pvr and lirc drivers]("http://www.themainlan.com/mythtv/hdpvr-blaster-drivers.tar.gzv"). Thank you I appreciate your help.

---

### Post by killrmantis on 2010-11-04
Ok, I just wanted to make sure you weren't using something weird.  :-)

I did some testing and some research and I think I found the issue.

It looks like those methods were renamed in 2.6.34.  (_[Change history here]("http://www.linuxhq.com/kernel/v2.6/34-rc6-git1/include/linux/usb.h")_)  From the looks of things only the method name changed.  You should be able to change usb_buffer_alloc() to usb_alloc_coherent() and usb_buffer_free() to usb_free_coherent().

I originally pulled those drivers out of FC12 (because it's the only distro in which the blaster works.)  If I get time I'll go back and see if I can get an updated version from FC.  I've been out of the HDPVR drivers loop for sometime.  It's possible someone else on the other side of the world has a better solution.

Also, FWIW, you don't have to be root to run make.  It's actually safer that you not be root.

---

### Post by grygub on 2010-11-05
Thanks alot for your help. Making those changes in addition to changing video_is_unregistered() to video_is_registered() made it compile.

---

### Post by thakk on 2010-11-11
I ran thru this thread and I was able to get it to compile, but now I am unable to view live tv even with /bin/true in the change channel script.

I'm wondering if something broke during the compile?

I have a HDPVR with mythbuntu 10.10.

Any ideas?

---

### Post by grygub on 2010-11-14
Did you just compile it or did you also load the driver with modprobe? I gave up in trying to make the lirc driver compile and never got to the load driver step. Just compiling the driver did not break my system but I couldn't say what loading it would do. I am going to wait until someone pulls the driver from fedora core 14 which should compile with our kernel version.

---

### Post by prmckinney on 2010-11-16
I just went through the process of getting this working on Ubuntu 10.10 as well.  Be sure when you changed video_is_unregistered to video_is_registered you inverted the conditional as well.  Before I realized my mistake it was working fine via cat /dev/video0, but Myth wouldn't generate video files at all.  After I corrected the logic it seems to be working fine.

---

### Post by stong98 on 2010-11-25
> **prmckinney said:**
> I just went through the process of getting this working on Ubuntu 10.10 as well.  Be sure when you changed video_is_unregistered to video_is_registered you inverted the conditional as well.  Before I realized my mistake it was working fine via cat /dev/video0, but Myth wouldn't generate video files at all.  After I corrected the logic it seems to be working fine.

Can you help me out with this step?  I believe I've followed along so far by making the changes mentioned to the hdpvr/hdpvr-video.c file as noted below, but I'm not sure I understand what you mean by inverting the conditional.  Do I need to change "dev->video_dev" to "dev<-video_dev" or is it "video_dev->dev" or am I way off base?

These are the changes I made to hdpvr/hdpvr-video.c: 
[LIST]
[*]change usb_buffer_alloc() to usb_alloc_coherent()
[*]change usb_buffer_free() to usb_free_coherent()
[*]change video_is_unregistered() to video_is_registered()
[/LIST]

Also, please let me know if what I've noted above is not correct or complete.

Thanks for your help.

---

### Post by stong98 on 2010-11-25
I found more instances of the usb_buffer_alloc and usb_buffer_free in the lirc folder.  I've tried changing those and running make in the lirc folder but it will not run.  I've also tried running make without any edits in the lirc folder, so i'm not sure what I'm doing wrong there.  Here is the output from running make in the lirc folder (I get the same output with edited files and stock files):

```
ryan@mythbuntu01:~/Documents/hdpvr_lirc/hdpvr-blaster-drivers/lirc$ make
make CONFIG_LIRC_ZILOG=m -C /lib/modules/2.6.35-23-generic/build M=/home/ryan/Documents/hdpvr_lirc/hdpvr-blaster-drivers/lirc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic'
  CC [M]  /home/ryan/Documents/hdpvr_lirc/hdpvr-blaster-drivers/lirc/lirc_zilog.o
In file included from /home/ryan/Documents/hdpvr_lirc/hdpvr-blaster-drivers/lirc/lirc_zilog.c:60:
/home/ryan/Documents/hdpvr_lirc/hdpvr-blaster-drivers/lirc/lirc_dev.h: In function âlirc_buffer_initâ:
/home/ryan/Documents/hdpvr_lirc/hdpvr-blaster-drivers/lirc/lirc_dev.h:47: warning: passing argument 1 of âkfifo_allocâ makes pointer from integer without a cast
include/linux/kfifo.h:108: note: expected âstruct kfifo *â but argument is of type âunsigned intâ
/home/ryan/Documents/hdpvr_lirc/hdpvr-blaster-drivers/lirc/lirc_dev.h:47: warning: passing argument 3 of âkfifo_allocâ makes integer from pointer without a cast
include/linux/kfifo.h:108: note: expected âgfp_tâ but argument is of type âstruct spinlock_t *â
/home/ryan/Documents/hdpvr_lirc/hdpvr-blaster-drivers/lirc/lirc_dev.h:47: warning: assignment makes pointer from integer without a cast
/home/ryan/Documents/hdpvr_lirc/hdpvr-blaster-drivers/lirc/lirc_dev.h: In function âlirc_buffer_readâ:
/home/ryan/Documents/hdpvr_lirc/hdpvr-blaster-drivers/lirc/lirc_dev.h:76: error: implicit declaration of function âkfifo_getâ
/home/ryan/Documents/hdpvr_lirc/hdpvr-blaster-drivers/lirc/lirc_dev.h: In function âlirc_buffer_writeâ:
/home/ryan/Documents/hdpvr_lirc/hdpvr-blaster-drivers/lirc/lirc_dev.h:81: error: implicit declaration of function âkfifo_putâ
make[2]: *** [/home/ryan/Documents/hdpvr_lirc/hdpvr-blaster-drivers/lirc/lirc_zilog.o] Error 1
make[1]: *** [_module_/home/ryan/Documents/hdpvr_lirc/hdpvr-blaster-drivers/lirc] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
make: *** [all] Error 2

```

I also tried running make after editing each of these files in the same way as the previous post:

1. Modify lirc/lirc_igorplugusb.c as follows:
[INDENT]a. change usb_buffer_alloc() to usb_alloc_coherent()
b. (2 edits) change usb_buffer_free() to usb_free_coherent()[/INDENT]
2. Modify lirc/lirc_mceusb.c as follows:
[INDENT]a. change usb_buffer_alloc() to usb_alloc_coherent()
b. (2 edits) change usb_buffer_free() to usb_free_coherent()[/INDENT]
3. Modify lirc/lirc_streamzap.c as follows:
[INDENT]a. change usb_buffer_alloc() to usb_alloc_coherent()
b. (2 edits) change usb_buffer_free() to usb_free_coherent()
[/INDENT]

Any help is much appreciated.

---

### Post by jayman8547 on 2010-11-25
Got an hdpvr a few weeks ago and I am having a hard time setting it up. I know it works but I want to use the IR blaster on it.  I have it plugged into a stand alone backend.  Other tuners on the backend are a HD homerun and a Dvico RT5 gold.  I went through the wiki page and got the hdpvr driver to compile but I am having make errors with the lirc one.  Also, what remote do I set in mcc?  Do I set a blaster in mcc?  Been all over the web and can't find much which means it's pretty straightforward or no one else is doing this...

---

### Post by stong98 on 2010-11-26
I think I have made some progress here, but am still having one problem.  I've been able to get the IR working for both transmit and receive, but now can't get the video to work.  I'm guessing it has to do with editing the hdpvr-video.c file and "inverting the conditional" as that's the only part I haven't been able to understand.  

Based on this post in the mythtv-users thread ([http://www.gossamer-threads.com/lists/mythtv/users/457534#457534]("http://www.gossamer-threads.com/lists/mythtv/users/457534#457534")) Mythbuntu 10.10 comes with a patched version of LIRC that will work.  So that takes care of the problem of being unable to run "make" in the lirc folder.  

Using the information in this thread ([http://www.gossamer-threads.com/lists/mythtv/users/419225]("http://www.gossamer-threads.com/lists/mythtv/users/419225")) I've set up my hardware.conf file with all of the information under the first "remote" section, and nothing in the "transmitter" section.  Here is what the top of my hardware.conf file looks like now:

```
#Chosen Remote Control
REMOTE="HD-PVR"
REMOTE_MODULES="lirc_zilog"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

```

So with the modified hdpvr.ko in place and LIRC configured as above, I've successfully gotten my HD-PVR to change the channel on my STB.  Unfortunately as soon as it does so, something crashes and no video plays.  At some point this morning I had video playing successfully (without channel changes), but I have not been able to get back to that setup since working on the LIRC side of things.  As I mentioned previously, I'm fairly certain the problem has to do with my lack of understanding of inverting the conditional, so I'm hoping someone can shed some light there and we can all get this working.

Note: I am running mythbuntu 10.10 fully updated with .24 and running on kernel 2.6.35-23 if that makes any difference.

---

### Post by stong98 on 2010-11-26
> **jayman8547 said:**
> Got an hdpvr a few weeks ago and I am having a hard time setting it up. I know it works but I want to use the IR blaster on it.  I have it plugged into a stand alone backend.  Other tuners on the backend are a HD homerun and a Dvico RT5 gold.  I went through the wiki page and got the hdpvr driver to compile but I am having make errors with the lirc one.  Also, what remote do I set in mcc?  Do I set a blaster in mcc?  Been all over the web and can't find much which means it's pretty straightforward or no one else is doing this...

I did specify a remote using MCC when I first set up MythTV, but when opening MCC now, it still shows the same thing I set up originally even though I have manually made config changes.  I'm pretty sure that the MCC is only editing the hardware.conf and lircd.conf files for you using predefined remote configurations, so once we make manual edits to those I would not touch the LIRC settings in MCC as it will overwrite your edits.  I am not certain about this behavior, but that is what I believe is happening so I have left it alone since I started manually editing it.

---

### Post by jayman8547 on 2010-11-27
I think I am close...

My HDPVR works great with live tv.  I compiled the hdpr drivers but skipped over the LIRC ones (running 10.10) and went on to "Steps to Enable IR Transmitter".  Did all those but still the channel change script in the backend set to /bin/true.  Now I want to test the channel changing capabilities.  What script should i use?  the directv.pl?  Another?  When I change the channel watching live tv, the pvr blinks for a bit, waiting for the channel change, but then goes back to the same channel.  Obviously because of /bin/true.

If I can get the channel change script to work, then all I did was compile the HDPV driver and all the steps in "Steps to Enable IR Transmitter"...

---

### Post by stong98 on 2010-11-27
> **jayman8547 said:**
> Did all those but still the channel change script in the backend set to /bin/true.  Now I want to test the channel changing capabilities.  What script should i use?  the directv.pl?  Another?  When I change the channel watching live tv, the pvr blinks for a bit, waiting for the channel change, but then goes back to the same channel.  Obviously because of /bin/true.

I think the script you use depends on the STB you are controlling, but I've pasted the script that I'm using below.  Note that my STB requires me to push Enter before giving it commands to wake it up, so there is an extra line in the script to accommodate that.  I'm not sure where this script came from because I believe I downloaded it a long time ago and just keep it around for when I'm able to get it working, but I do keep it in /usr/local/bin.

```

#!/usr/bin/perl

# make sure to set this string to
# the corresponding remote in /etc/lircd.conf
$remote_name = "Motorola_VIP_1200";

# Let's assume you don't need to press enter after you punch in a
# channel number. Change this to 1 if your cable box expects you press
# enter after each command
$needs_enter = 0;

# Change this to point to your rc executable
$rc_command = "/usr/bin/irsend";

# This subroutine actually sends the signal to the cable box
sub change_SIGNAL {
    my($SIGNAL) = @_;
    system ("$rc_command SEND_ONCE $remote_name ENTER");
    system ("$rc_command SEND_ONCE $remote_name $SIGNAL");
}

$SIGNAL=$ARGV[0];
open F, ">> /var/log/channel.log";
print F "channel changing $SIGNAL\n";
close F;
print "channel changing $SIGNAL\n";

# Checks if $SIGNAL begins with a digit
# If it detects that the string is made up of digits, then it puts
# spaces between the digits.  Ex. 1234 becomes 1 2 3 4
if ( $SIGNAL =~ /^\d+$/ )
{
    my $length = length($SIGNAL);
    my $counter = 0;
    my $temp;

    while( $counter < $length )
    {
        $temp .= substr($SIGNAL,$counter,1) ." ";
        $counter++;
    }

    change_SIGNAL($temp);
}
else
{
    # argument we passed was not made up of digits, so it must be a
    # command that does something other than channel changing on the
    # cable box
    change_SIGNAL($SIGNAL);
}

# Do we need to send enter
if ( $needs_enter )
{
    system ("$rc_command SEND_ONCE $remote_name ENTER");
}


```


> **jayman8547 said:**
> If I can get the channel change script to work, then all I did was compile the HDPV driver and all the steps in "Steps to Enable IR Transmitter"...

When you say that all you did was compile the hdpvr, you mean you didn't make any of the changes identified in this thread?  It won't compile on my system if I don't make the changes noted.  What kernel version do you have?  If you did make the changes noted, how did you change the "video_is_unregistered" line?

---

### Post by jayman8547 on 2010-11-28
> **stong98 said:**
> When you say that all you did was compile the hdpvr, you mean you didn't make any of the changes identified in this thread?  It won't compile on my system if I don't make the changes noted.  What kernel version do you have?  If you did make the changes noted, how did you change the "video_is_unregistered" line?

I made the changes up to modifying anything with the lirc drivers since there was an updated version in 10.10.  I did not touch the "video_is_unregistered" line.

Also, tried the directv.pl script as well as your channel change script to no avail.

At this point I've been screwing around with this thing for a few weeks so I'm gonna look at some other options for channel changing...

---

