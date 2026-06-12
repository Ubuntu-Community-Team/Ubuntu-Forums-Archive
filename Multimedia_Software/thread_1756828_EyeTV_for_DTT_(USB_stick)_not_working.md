---
title: "EyeTV for DTT (USB stick) not working"
date: 2011-05-12
forum: Multimedia Software
---

### Post by perevera on 2011-05-12
I just bought a new USB DVB-T receiver: Elgato EyeTV for DTT.

In the following chart:

[http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices](http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices)

it is listed as supported out of the box, which is not the case.

When I connect the stick, the only message I get is the following:

May 13 00:15:26 micasa kernel: [16969.930122] usb 2-2: new high speed USB device using ehci_hcd and address 4

So I guess I will need to mess up with patches, kernel modules, firmware files, etc.

Please, is anybody using this receiver or the Hauppauge WinTV-NOVA-T (which is said to be a clone)?

Or, can anybody give me a clue?

Thanks in advance.

---

### Post by fieccle01 on 2011-05-14
I have the same problem and would also appreciate some help. I am very new to Linux so could you please explain as if i were a five year old. 
Thanks

---

### Post by perevera on 2011-05-17
I finally figured out how to make it work, mainly thanks to some Italian colleagues:

[http://forum.ubuntu-it.org/index.php?topic=437622.0;prev_next=prev](http://forum.ubuntu-it.org/index.php?topic=437622.0;prev_next=prev)

I explain here in detail what worked for me. The main trick is to patch, compile and install the driver Video4Linux.

Keep in mind my system is a Ubuntu 10.10 (64 bits) and my current kernel version is:  2.6.35-28-generic.

Ok, when you launch 'lsusb' you see something like this:

Bus 002 Device 004: ID 0fd9:003f
  
This is the rev. 3 of this USB stick, not still supported, but it has actually the same chip as the previous revisions, actually supported by the V4L driver.

You have to install the proper firmware, as said in the table it is: dvb-usb-dib0700-1.20.fw.

You can get it from: [http://www.linuxtv.org/downloads/firmware/](http://www.linuxtv.org/downloads/firmware/), you have to copy it to /lib/firmware/2.6.35-28-generic (or whatever directory is in your case, find it out with 'uname -r').

You need also to install the kernel headers:

$ sudo apt-get install linux-headers-`uname -r`

Then download the source code of the V4L driver. There are several ways, this one worked for me:

$ git clone git://linuxtv.org/media_build.git

(You may need to install 'git' previously).

Now, let's go to the patch: edit the file media_build/linux/drivers/media/dvb/dvb-usb/dvb-usb-ids.h and change this value to fit the one for the actual USB stick:

#define USB_PID_ELGATO_EYETV_DTT                        0x0021     0x003f

Compile the driver with:

$ make

Install it with:

$ sudo make install

Restart the system, then check if the tuner is already supported:

$ lsmod | grep dvb

The output should be something like this:

[   15.408405] dvb-usb: found a 'Elgato EyeTV DTT' in cold state, will try to load a firmware

[   15.438852] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'

[   15.750073] Registered IR keymap rc-dntv-live-dvb-t

[   15.795351] cx88/2: cx2388x dvb driver version 0.0.8 loaded

[   15.795353] cx88/2: registering cx8802 driver, type: dvb access: shared

[   16.149584] dvb-usb: found a 'Elgato EyeTV DTT' in warm state.

[   16.149615] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.

[   16.894508] dvb-usb: schedule remote query interval to 50 msecs.

[   16.894510] dvb-usb: Elgato EyeTV DTT successfully initialized and connected.

[   16.894653] usbcore: registered new interface driver dvb_usb_dib0700

And this is it, you should have now a new /dev/dvb/adapter0 or similar mapped to the device.

---

### Post by uncleted on 2011-05-24
Just to clear this up, after the git clone, you should run the following commands.

```
cd media_build 
./build.sh
```

The build.sh will grab the latest tarball for the v4l source and patch it, if you don't do this you'll end up with an empty looking directory.

Info from [here]("http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers").

---

### Post by TypeXXI on 2011-11-20
> **perevera said:**
> 

Now, let's go to the patch: edit the file media_build/linux/drivers/media/dvb/dvb-usb/dvb-usb-ids.h and change this value to fit the one for the actual USB stick:

#define USB_PID_ELGATO_EYETV_DTT                        0x0021     0x003f



I realised that for DDT stick the value has to be
#define USB_PID_ELGATO_EYETV_DTT                        0x003f

Don't write 0x0021 anywhere.

---

### Post by perevera on 2011-12-07
> **TypeXXI said:**
> I realised that for DDT stick the value has to be
#define USB_PID_ELGATO_EYETV_DTT                        0x003f

Don't write 0x0021 anywhere.

Yes, my mistake!

---

