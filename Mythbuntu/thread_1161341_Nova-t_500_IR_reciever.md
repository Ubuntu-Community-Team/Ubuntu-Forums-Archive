---
title: "Nova-t 500 IR reciever"
date: 2009-05-16
forum: Mythbuntu
---

### Post by wildbillkelso on 2009-05-16
Hi all.

I got a Nova-T 500 the other day. I have been pulling what little hair I have  out, trying to get the remote to work over the last few days. I have looked high and low and googled lots. I realise that the remote configuration is covered extensively here and else where but I think this is something diferent. I discovered that on the mythtv wiki there is a setup guide, and from this I have established that the IR receiver is not being recognised.

I do dmesg | grep -i dvb
and I get

$ dmesg | grep -i dvb
[    9.952971] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
[    9.952989] usb 2-1: firmware: requesting dvb-usb-dib0700-1.20.fw
[   11.342850] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   12.068026] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
[   12.068188] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   12.068645] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   12.296784] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[   12.476968] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   12.477344] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   12.628730] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
[   12.808147] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
[   12.808317] usbcore: registered new interface driver dvb_usb_dib0700


Now, according to the wiki I should have something in there like

[   24.787147] input: IR-receiver inside an USB DVB receiver as /class/input/input4

Obviously there is no point in going through the remote setup if the IR receiver is present though I have tried out of desperation!

I have checked out and tried several methods I have found with no results.
I am using jaunty and have a clean install.
Any ideas greatfully recieved.

Many thanks

---

### Post by wildbillkelso on 2009-05-17
Updated driver from Linux TV. Sorted now.

---

### Post by tony.morse on 2009-07-23
Can you say more?

I have the same card in my Myth setup and I can't get the IR remote control working either.  I do get the line saying... 

[ 24.787147] input: IR-receiver inside an USB DVB receiver as /class/input/input4

except the location is different, so my remote should be working right? except it doesn't, I get no response from anything I've tried to date.

---

### Post by yogaman69 on 2009-08-09
Like Tony.morse, I would be interested in more details, can you epand a bit please?

---

### Post by uMuppet on 2009-10-09
Any progress on this?  I would love to find the firmware to make this device work on 9.04.  I cant get dmesg to find it at all.

---

### Post by tonycollinet on 2009-10-10
You'll see a number of threads of mine regarding the novatd500 IR. I finally got it to work by first installing the latest v4l drivers

[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers) 

(Involved, but just follow it step by step)

Then following
[http://ubuntuforums.org/showthread.php?t=1140411&highlight=nova+t+500+remote](http://ubuntuforums.org/showthread.php?t=1140411&highlight=nova+t+500+remote)

again step by step.

HOWEVER - my remote device line in hardware.conf is:
REMOTE_DEVICE="/dev/input/event5"

You need to find the "event5" from 
sudo cat /proc/bus/input/devices


Sorry - but far from an expert - I have pretty much muddled through, and don't really understand what is going on. But it IS possible to make it work.

---

### Post by igoddard on 2009-10-10
> **tonycollinet said:**
> You'll see a number of threads of mine regarding the novatd500 IR. I finally got it to work by first installing the latest v4l drivers

[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers) 

(Involved, but just follow it step by step)

Then following
[http://ubuntuforums.org/showthread.php?t=1140411&highlight=nova+t+500+remote](http://ubuntuforums.org/showthread.php?t=1140411&highlight=nova+t+500+remote)

again step by step.

HOWEVER - my remote device line in hardware.conf is:
REMOTE_DEVICE="/dev/input/event5"

You need to find the "event5" from 
sudo cat /proc/bus/input/devices


Sorry - but far from an expert - I have pretty much muddled through, and don't really understand what is going on. But it IS possible to make it work.

If you follow the instructions in [http://ubuntuforums.org/showthread.php?t=1140411](http://ubuntuforums.org/showthread.php?t=1140411) about setting up a udev rule you will have the remote device at /dev/input/irremote rather than /dev/input/event5.  The reason for doing it that way is that the event number could change if, for instance, you booted up with something plugged into a USB port.

---

### Post by tonycollinet on 2009-10-10
Thanks - will give that a try.

---

