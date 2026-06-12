---
title: "TinyTwin (Afatech DVB-T 2) - LIRC remote"
date: 2009-09-01
forum: Multimedia Software
---

### Post by siren09 on 2009-09-01
I have a DigitalNow TinyTwin USB tuner card, which comes with a remote control.  I'd like to get this working under MythTV.

The remote was connected and listed under lshal, and button presses at the console were interpreted as keyboard strokes.  Good start, I thought.  Unfortunately, a single button press resulted in a continuous stream of characters, so something is not seeing the button release.  

Anyway, I thought I'd look at getting the remote supported under LIRC, and have searched for a configuration, but I don't think one exists yet.  So, being brave and foolhardy, I would like to try to generate one. 

The first step was to remove the HAL configuration by adding lines to the /usr/share/hal/fdi/preprobe/20thirdparty/remote.fdi (and also to lirc.fdi in the same directory):

          <device>
     <match key="info.product" string="Afatech DVB-T 2">
         <merge key="info.ignore" type="bool">true</merge>
     </match>
 </device>
 

 This info was gleaned from the lshal command.  On reboot, the remote control no longer spits keys to the command line.  Ok, good start.

Next, I understand I needed to configure LIRC.  I edited my /etc/lirc/hardware.conf file as follows:[INDENT]REMOTE_DRIVER="dev/input" 
REMOTE_DEVICE="/dev/input/by-id/usb-Afatech_DVB-T_2_010101010600001-event-ir"

...
START_LIRCD=true    
...

# Receiver settings required by gnome-lirc-properties 
RECEIVER_MODEL="Afatech DVB-T 2" 
RECEIVER_VENDOR="Linux Input Device" 

# Remote settings required by gnome-lirc-properties 
REMOTE_MODEL="Linux Input Layer compatible Remote" 
REMOTE_VENDOR="Generic"
[/INDENT]I am pretty sure that this is correct so far.  So I tried to run irw on the command line to test the remote control (note I do not have a lircd.conf in /etc yet).  irw ran ok but absolutely nothing was received on pressing buttons.

lircd was running, so I stopped it using: sudo /etc/init.d/lirc stop, and then ran from the command line: sudo lircd -n --device= /dev/input/by-id/usb-Afatech_DVB-T_2_010101010600001-event-ir --driver=dev/input .  This gave the following output:[INDENT]lircd-0.8.4a[14085]: error in configfile line 1
lircd-0.8.4a[14085]: reading of file '/dev/input/by-id/usb-Afatech_DVB-T_2_010101010600001-event-ir' failed
lircd-0.8.4a[14085]: reading of config file failed
lircd-0.8.4a[14085]: lircd(devinput) ready
[/INDENT]The /dev/input/by... file does exist.  dmesg | grep lirc does not return any results.  I am running 6.2.30 kernel.  This suggests to me that something is not right with lircd.  How do I check if the relevant kernel modules are running ok (starting the daemon from init.rc on the command line gives no errors).  I did also consider compiling lirc from source, given my kernel version, ut the configuration tool setup.sh seems to require me to select a remote control, and of course mine is not listed...

If someone could give me pointers as to where to go next, I'd be grateful.  

Thanks.

---

### Post by cunneen on 2010-07-06
Thanks for posting this siren09. Did you manage to get the remote working in the end? If so, how?

My experience is a little different from yours: it looks like my remote is not detected at all (lshal doesn't list it) and pressing the remote keys with irw running does nothing.

Any info you could give me would be appreciated.

---

### Post by koan on 2010-07-08
I am using tinytwin, with kernel 2.6.34, and everything is recognised:

```

[    9.740066] DVB: registering new adapter (DigitalNow TinyTwin DVB-T Receiver)
[    9.950888] af9013: found a 'Afatech AF9013 DVB-T' in warm state.
[    9.953517] af9013: firmware version:4.95.0
[    9.964894] DVB: registering adapter 3 frontend 0 (Afatech AF9013 DVB-T)...
[    9.965037] MXL5005S: Attached at address 0xc6
[    9.965147] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:06.1/usb2/2-2/input/input7
[    9.965208] dvb-usb: schedule remote query interval to 150 msecs.
[    9.965210] dvb-usb: DigitalNow TinyTwin DVB-T Receiver successfully initialized and connected.
[   10.058307] usbcore: registered new interface driver dvb_usb_af9015

```

So input7 is the IR, and lshal shows that is bound to event7:

```

$ sudo lshal | grep input7
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:06.1/usb2/2-2/input/input7/event7'  

```

If I 'cat /dev/event7' while sending remote signals to the tinytwin, I get nothing.

I think this is still not working.  I know someone else using tinytwin official drivers (downloaded) and didn't get the IR working.

My hardware is 1b80:e402 btw.

---

### Post by cunneen on 2010-07-09
I'm still trying to get my TinyTwin remote working too, under mythbuntu 9.10 .
 
For what it's worth, the remote appears to be a Yaocoo SRC-0149U
 
[http://www.yaocoo.com/2009/0319/zNMDAwMDAwMDIzNQ.html](http://www.yaocoo.com/2009/0319/zNMDAwMDAwMDIzNQ.html)
 
Is that what your remotes look like, siren09 and koan? Mine is the same except silver and without the branding.
 
[IMG]http://www1.dealextreme.com/productimages/sku_6202_1.jpg[/IMG]
 
It looks like the manufacturer ships it with a receiver as well, but of course the tinytwin has one built in so it doesn't come with the receiver.

---

### Post by koan on 2010-07-09
Yeah - I have a remote that looks like this, so I guess it must be the one that came with the tinytwin.

Note that under normal circumstances, the remote isn't that relevant to the process.  Any IR signals should be picked up through the infrared.  LIRC via irecord is able to work out the pulse and gap lengths for any remote that it gets a signal for.

This is why I am not entirely sure which remote is which - once you have a working lircd.conf you can use it with almost any IR receiver.

---

### Post by cunneen on 2010-07-12
I'm trying to make sense of [this thread]("http://forums.whirlpool.net.au/forum-replies.cfm?t=1238107") on the whirlpool forums, which looks very promising.

---

### Post by koan on 2010-07-14
> **cunneen said:**
> I'm trying to make sense of [this thread]("http://forums.whirlpool.net.au/forum-replies.cfm?t=1238107") on the whirlpool forums, which looks very promising.

Unfortunately, I think that is for a previous revision of the Tinytwin.  

Nothing shows up in the event device as far as I can see for this revision.

---

