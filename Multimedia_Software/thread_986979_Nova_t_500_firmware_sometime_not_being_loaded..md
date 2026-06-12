---
title: "Nova t 500 firmware sometime not being loaded."
date: 2008-11-19
forum: Multimedia Software
---

### Post by nedwards on 2008-11-19
Hi,

I have a Nova t 500 in my AMD 64 system using 8.10.

I have however been having a problem which is that sometimes the firmware fails to load. When it fails I get:

[   15.249775] dib0700: loaded with support for 7 different device-types
[   15.250241] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   15.250246] firmware: requesting dvb-usb-dib0700-1.10.fw
[   15.314324] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   15.586763] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   17.298289] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   18.344056] dib0700: firmware download failed at 7420 with -110

When it works I get:

[   15.201737] dib0700: loaded with support for 7 different device-types
[   15.202170] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   15.202174] firmware: requesting dvb-usb-dib0700-1.10.fw
[   15.312553] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   15.571226] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   17.313255] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   17.527620] dib0700: firmware started successfully.
[   18.028020] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   18.030275] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   18.030554] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   18.149098] DVB: registering frontend 0 (DiBcom 3000MC/P)...
[   18.209728] MT2060: successfully identified (IF1 = 1236)
[   18.687285] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   18.687489] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   18.696184] DVB: registering frontend 1 (DiBcom 3000MC/P)...
[   18.701426] MT2060: successfully identified (IF1 = 1231)
[   19.263690] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:14.4/0000:03:0a.2/usb4/4-1/input/input6
[   19.295757] dvb-usb: schedule remote query interval to 150 msecs.
[   19.295765] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   19.296055] usbcore: registered new interface driver dvb_usb_dib0700

Also when in warm state it works:

[   19.882614] dib0700: loaded with support for 7 different device-types
[   19.883338] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   19.883463] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   19.883732] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   19.900384] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   19.999273] DVB: registering frontend 0 (DiBcom 3000MC/P)...
[   20.170692] MT2060: successfully identified (IF1 = 1236)
[   20.259644] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   20.663783] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   20.664039] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   20.671122] DVB: registering frontend 1 (DiBcom 3000MC/P)...
[   20.676667] MT2060: successfully identified (IF1 = 1231)
[   21.238389] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:14.4/0000:03:0a.2/usb4/4-1/input/input6
[   21.268292] dvb-usb: schedule remote query interval to 150 msecs.
[   21.268302] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   21.268560] usbcore: registered new interface driver dvb_usb_dib0700

This seems to happen just in cold state and when the computer has been off for more that a minute or two.

Please can someone help here and yes the correct firmware is there:

-rw-r--r-- 1 root root 34306 2008-10-27 05:33 /lib/firmware/dvb-usb-dib0700-1.10.fw

Thanks very much.

Nick

---

### Post by watkin5 on 2008-12-05
> **nedwards said:**
> Hi,

I have a Nova t 500 in my AMD 64 system using 8.10.

I have however been having a problem which is that sometimes the firmware fails to load. When it fails I get:

[   15.249775] dib0700: loaded with support for 7 different device-types
[   15.250241] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   15.250246] firmware: requesting dvb-usb-dib0700-1.10.fw
[   15.314324] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   15.586763] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   17.298289] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   18.344056] dib0700: firmware download failed at 7420 with -110



I'm having the same problem with all the 8.10 kernels. All the kernels in Hardy work reasonably well.

I've started a bug report
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/303667](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/303667)

Did you fix the problem with your Nova T 500?
I'm also see lots of i2c error with 8.10.

Any advice would be greatly appreciated.

---

### Post by nedwards on 2008-12-05
Hi,

I have not fixed the problem, what I did to to get around it for now was added the following to the end of /etc/rc.local:

# deal with dib0700 firmware not being loaded properly
return=$(dmesg | grep 'dib0700: firmware download failed at');
if [ $? = "0" ];
then
        rmmod dvb_usb_dib0700
        modprobe dvb_usb_dib0700
        /etc/init.d/lirc restart
        /etc/init.d/gdm restart
fi

exit 0

I did this with the linuxtv drivers from a couple of weeks back and things seemed to work better for a while. However I have just updated the drivers from linuxtv and I am now getting the following errors again and things are not working:

Dec  5 21:23:29 media kernel: [12748.012160] mt2060 I2C read failed

By the way something went wrong with your link its: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/303667/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/303667/)

Regards,

Nick

---

### Post by watkin5 on 2008-12-10
Which version of the card have you got?

lsusb shows mine as
   ID 2040:9950 Hauppauge

Thanks for the rc.local script. The firmware always loads the second time, although,when the second tuner starts up, I then get 
   [  230.456120] dvb-usb: error while enabling fifo.


Regards,
Robert Watkins

---

### Post by nedwards on 2008-12-10
Hi Robert,

I have the same device as you:

Bus 004 Device 002: ID 2040:9950 Hauppauge

I have seen that error before as is shown below:

Dec 10 19:21:12 media kernel: [  152.156250] dvb-usb: error while enabling fifo.
Dec 10 19:23:32 media ntpd[4225]: synchronized to 91.189.94.4, stratum 2
Dec 10 19:23:32 media ntpd[4225]: kernel time sync status change 0001
Dec 10 19:28:44 media kernel: [  603.208141] mt2060 I2C write failed (len=2)
Dec 10 19:28:49 media kernel: [  608.208185] mt2060 I2C write failed (len=6)
Dec 10 19:28:54 media kernel: [  613.208107] mt2060 I2C read failed
Dec 10 19:28:59 media kernel: [  618.216166] mt2060 I2C read failed
Dec 10 19:29:04 media kernel: [  623.224093] mt2060 I2C read failed
Dec 10 19:29:09 media kernel: [  628.232142] mt2060 I2C read failed

Now when the card is in this state, when I think go to watch tv it says that the 'master backend server has gone away for some reason'.

Now I had it all up and running well yesterday for the first time in ages! However today it's broken again. Also I have disabled one of the tuners to see if that helps, however it doesn't appear to.

One other side not, I have also had an issue with mythtv saying that my tuner is unavailable so I have added '/etc/init.d/mythtv-backend restart' to the end of /etc/rc.local. 

I have had EIT switched on so I will switch off again and see what happens.

Best regards,

Nick

---

