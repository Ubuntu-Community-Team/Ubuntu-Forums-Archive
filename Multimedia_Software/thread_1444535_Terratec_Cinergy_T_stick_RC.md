---
title: "Terratec Cinergy T stick RC"
date: 2010-04-01
forum: Multimedia Software
---

### Post by andlinux on 2010-04-01
Who can help me with this dvb-t stick ?
I thought it would work if I plugged it in but it doesn't. I searched the web to find some info but I get other types of the same brand.

if I do lsusb I get this:

```
Bus 002 Device 004: ID 0ccd:0097 TerraTec Electronic GmbH 
```

This is the latest part of dmesg when I plug in the usb stick:

```
[  315.990289] usb 2-6: new high speed USB device using ehci_hcd and address 5
[  316.147192] usb 2-6: configuration #1 chosen from 1 choice
[  316.154277] input: NEWMI USB2.0 DVB-T TV Stick as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.1/input/input11
[  316.154446] generic-usb 0003:0CCD:0097.0002: input,hidraw0: USB HID v1.01 Keyboard [NEWMI USB2.0 DVB-T TV Stick] on usb-0000:00:1d.7-6/input1

```

What can I do to make this work ?

---

### Post by andlinux on 2010-04-01
Forgot to mention, on the back of the stick is standing Cinergy T stick MKII

---

### Post by xc3RnbFO8P on 2010-04-01
Google this and translate:
> Probleme beim Installieren - Terratec Cinergy T-Stick
[http://forum.ubuntuusers.de/topic/probleme-beim-installieren-terratec-cinergy-t/3/#post-2361396]("http://forum.ubuntuusers.de/topic/probleme-beim-installieren-terratec-cinergy-t/3/#post-2361396")

---

### Post by andlinux on 2010-04-02
> **Ringi said:**
> Google this and translate:

[http://forum.ubuntuusers.de/topic/probleme-beim-installieren-terratec-cinergy-t/3/#post-2361396]("http://forum.ubuntuusers.de/topic/probleme-beim-installieren-terratec-cinergy-t/3/#post-2361396")Thanks, I'm gonna try that.

---

### Post by andlinux on 2010-04-02
Well I think it's installed correctly but how can I see or watch a channel ?

dmesg | grep -i dvb:

```
[    2.927056] input: NEWMI USB2.0 DVB-T TV Stick as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.1/input/input5
[    2.927162] generic-usb 0003:0CCD:0097.0001: input,hidraw0: USB HID v1.01 Keyboard [NEWMI USB2.0 DVB-T TV Stick] on usb-0000:00:1d.7-6/input1
[   22.859476] dvb-usb: found a 'TerraTec Cinergy T Stick RC' in cold state, will try to load a firmware
[   22.859483] usb 2-6: firmware: requesting dvb-usb-af9015.fw
[   23.347309] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
[   23.660218] dvb-usb: found a 'TerraTec Cinergy T Stick RC' in warm state.
[   23.660272] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   23.660825] DVB: registering new adapter (TerraTec Cinergy T Stick RC)
[   24.134967] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
[   24.164983] dvb-usb: TerraTec Cinergy T Stick RC successfully initialized and connected.
[   24.173257] usbcore: registered new interface driver dvb_usb_af9015

```

I have had another dvb-t stick (a very cheap one) and then I could do a scan with kaffeine to watch tv channels. It was very simple to watch tv with kaffeine. Now I'm lost...

---

### Post by xc3RnbFO8P on 2010-04-03
> **andlinux said:**
> Well I think it's installed correctly but how can I see or watch a channel ?

dmesg | grep -i dvb:

```
[    2.927056] input: NEWMI USB2.0 DVB-T TV Stick as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.1/input/input5
[    2.927162] generic-usb 0003:0CCD:0097.0001: input,hidraw0: USB HID v1.01 Keyboard [NEWMI USB2.0 DVB-T TV Stick] on usb-0000:00:1d.7-6/input1
[   22.859476] dvb-usb: found a 'TerraTec Cinergy T Stick RC' in cold state, will try to load a firmware
[   22.859483] usb 2-6: firmware: requesting dvb-usb-af9015.fw
[   23.347309] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
[   23.660218] dvb-usb: found a 'TerraTec Cinergy T Stick RC' in warm state.
[   23.660272] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   23.660825] DVB: registering new adapter (TerraTec Cinergy T Stick RC)
[   24.134967] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
[   24.164983] dvb-usb: TerraTec Cinergy T Stick RC successfully initialized and connected.
[   24.173257] usbcore: registered new interface driver dvb_usb_af9015

```

I have had another dvb-t stick (a very cheap one) and then I could do a scan with kaffeine to watch tv channels. It was very simple to watch tv with kaffeine. Now I'm lost...

Did you try to change Usb port?

---

### Post by andlinux on 2010-04-03
> **Ringi said:**
> Did you try to change Usb port?
I don't have that anymore, the dog played with it ;)

---

### Post by xc3RnbFO8P on 2010-04-03
> **andlinux said:**
> I don't have that anymore, the dog played with it ;)
Too bad
> I also had some weird problems with Kaffeine (Can't tune DVB). Then someone suggested that some USB ports might not be able to provide enough current (mA) for the USB stick. I connected my Cinergy T USB XS to a USB hub instead of the backside of the PC and all problems were gone.

---

### Post by andlinux on 2010-04-03
> **Ringi said:**
> Too bad
Indeed, that's strange. 
I think that the stick that I have now will work but I have no idea how I can make it work with a program. I have seen that you need a channels list with mplayer, vlc, etc.
So I started with w_scan but that's not generating a list :s

---

### Post by xc3RnbFO8P on 2010-04-03
Try:
> scan /usr/share/dvb/dvb-t/your location > /tmp/channels.conf

---

### Post by andlinux on 2010-04-04
> **Ringi said:**
> Try:
My country is listed but not my city.
So I took a random city.

But this is what I get:

```
scan /usr/share/dvb/dvb-t/be-Schoten > /tmp/channels.conf scanning /usr/share/dvb/dvb-t/be-Schoten
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 778000000 0 1 9 3 1 3 0
>>> tune to: 778000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_1_2:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 778000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_1_2:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```

I tried another city and it gives the same result.

---

### Post by andlinux on 2010-05-06
Well, now it's working. I did an upgrade to 10.04 and I used the tutorial on the [German]("http://forum.ubuntuusers.de/topic/probleme-beim-installieren-terratec-cinergy-t/4/") website.

Here is what I did:

- Upgrade to 10.04
```
sudo apt-get install mercurial linux-headers-$(uname -r) build-essential
```
```
hg clone -r 18b40811c3fd http://linuxtv.org/hg/v4l-dvb
```
```
cd v4l-dvb
```
```
mkdir cinergy
```
```
cd cinergy
```
```
wget http://media.ubuntuusers.de/forum/attachments/2361396/cinergy_t_stick_rc.tgz
```
```
tar xfvz cinergy_t_stick_rc.tgz
```
```
cp -r ./dvb-usb/* ~/v4l-dvb/linux/drivers/media/dvb/dvb-usb&&cp -r ./frontends/* ~/v4l-dvb/linux/drivers/media/dvb/frontends&&cp -r ./tuners/* ~/v4l-dvb/linux/drivers/media/common/tuners
```
```
cd ..
```
```
wget http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw
```
```
sudo cp dvb-usb-af9015.fw  /lib/firmware/
```
Note: If the compiling process stops with an error about M920X module and firedtv then do this first.
```
sed -i 's/CONFIG_DVB_FIREDTV=m/CONFIG_DVB_FIREDTV=n/' ./v4l/.config&&sed -i 's/CONFIG_DVB_USB_M920X=m/CONFIG_DVB_USB_M920X=n/' ./v4l/.config
```
Note: if you use a Dualcore CPU then do "make -j2" if you use a quadcore CPU "make -j4", single or unsure is "make"
```
make
```
```
sudo make install
```
```
sudo reboot
```
Note: to check if the module is loaded.
```
dmesg | grep -i dvb
```

If it works then you get something like this:
```
[    2.826468] input: NEWMI USB2.0 DVB-T TV Stick as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.1/input/input5
[    2.826566] generic-usb 0003:0CCD:0097.0001: input,hidraw0: USB HID v1.01 Keyboard [NEWMI USB2.0 DVB-T TV Stick] on usb-0000:00:1d.7-6/input1
[   21.991089] dvb-usb: found a 'TerraTec Cinergy T Stick RC' in cold state, will try to load a firmware
[   21.991095] usb 2-6: firmware: requesting dvb-usb-af9015.fw
[   22.490757] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
[   22.566723] dvb-usb: found a 'TerraTec Cinergy T Stick RC' in warm state.
[   22.566799] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   22.567131] DVB: registering new adapter (TerraTec Cinergy T Stick RC)
[   23.639842] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
[   23.746241] dvb-usb: TerraTec Cinergy T Stick RC successfully initialized and connected.
[   23.754359] usbcore: registered new interface driver dvb_usb_af9015
[ 1229.516190] dvb-usb: TerraTec Cinergy T Stick RC successfully deinitialized and disconnected.

```

---

### Post by staticx1 on 2010-05-09
Hi

I did all the procedure and it still not functioning.
all the process was smooth except the line;

```
dmesg | grep -i dvb
```which it seems like nothing is happening after that...

My stick is a WandTV USB2 stick 
lsusb gives me
Bus 001 Device 005: ID 15a4:1001 Afatech Technologies, Inc. **AF9015** DVB-T USB2.0 stick

but dmesg gives me
[ 1264.364116] usb 1-2: new high speed USB device using ehci_hcd and address 6
[ 1264.502751] usb 1-2: configuration #1 chosen from 1 choice
[ 1264.508032] input: Afa Technologies Inc. **AF9035A** USB Device as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.1/input/input13
[ 1264.508399] generic-usb 0003:15A4:1001.0005: input,hidraw0: USB HID v1.01 Keyboard [Afa Technologies Inc. AF9035A USB Device] on usb-0000:00:1d.7-2/input1


(My other system, which have WIn7 recognizes it as AF9035 BDA Device.
I'm using latest Ubuntu 10 with all updates.

Try to help me...
Thanks.:guitar:

---

### Post by andlinux on 2010-05-10
> **staticx1 said:**
> Hi

I did all the procedure and it still not functioning.
all the process was smooth except the line;

```
dmesg | grep -i dvb
```which it seems like nothing is happening after that...

My stick is a WandTV USB2 stick 
lsusb gives me
Bus 001 Device 005: ID 15a4:1001 Afatech Technologies, Inc. **AF9015** DVB-T USB2.0 stick

but dmesg gives me
[ 1264.364116] usb 1-2: new high speed USB device using ehci_hcd and address 6
[ 1264.502751] usb 1-2: configuration #1 chosen from 1 choice
[ 1264.508032] input: Afa Technologies Inc. **AF9035A** USB Device as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.1/input/input13
[ 1264.508399] generic-usb 0003:15A4:1001.0005: input,hidraw0: USB HID v1.01 Keyboard [Afa Technologies Inc. AF9035A USB Device] on usb-0000:00:1d.7-2/input1


(My other system, which have WIn7 recognizes it as AF9035 BDA Device.
I'm using latest Ubuntu 10 with all updates.

Try to help me...
Thanks.:guitar:

Did you take a look at this [link ]("http://ubuntuforums.org/showthread.php?t=1364396")?

---

### Post by staticx1 on 2010-05-11
yea, I followed the link but didn't find any clear solution. I'm trying to install it on x32 system, from what I read at the post, it can only work on older kernels.... is there a way to roll back to an older kernel?

I will be glad if you can provide me some clear solution, I'm not familiar  with Linux (Ubuntu) OS so if you can, please explain like you are trying to teach a monkey :)
thanks.

---

### Post by m2.g5ru6y7s on 2010-06-13
@andlinux: Many thanks for your post! I can confirm that it also works on Fedora 13 [perfectly]("http://img532.imageshack.us/img532/2159/schermafdrukw.png").

---

### Post by little_penguin on 2010-08-04
The Terratec Cinergy T stick RC is working here in Ubuntu Jaunty as well. I followed Eisheiliga's [German  instructions]("http://forum.ubuntuusers.de/topic/probleme-beim-installieren-terratec-cinergy-t/4/") (translated in this thread by andlinux), with one exception.

The original sed command resulted in compilation errors for me, so instead of the original code:

```
 sed -i 's/CONFIG_DVB_FIREDTV=m/CONFIG_DVB_FIREDTV=n/' ./v4l/.config&&sed -i 's/CONFIG_DVB_USB_M920X=m/CONFIG_DVB_USB_M920X=n/' ./v4l/.config 
```I had to use

```
sed -i 's/CONFIG_DVB_FIREDTV=m/CONFIG_DVB_FIREDTV=n/' ./v4l/.config
```It then compiled without any errors and after a reboot I had a working DVB-T stick :)

Regards,
LP

---

### Post by najgeetsrev on 2010-12-03
> **Ringi said:**
> Google this and translate:

[http://forum.ubuntuusers.de/topic/probleme-beim-installieren-terratec-cinergy-t/3/#post-2361396]("http://forum.ubuntuusers.de/topic/probleme-beim-installieren-terratec-cinergy-t/3/#post-2361396")

I made a english translation of the howto. You can find it [here](http://www.ditdomeinisvanmij.nl/2010/12/03/how-to-install/) at this link.


**Step 1**
Install mercurial, your Linux headers, build essentials and patch.

sudo apt-get install mercurial linux-headers-$(uname -r) build-essential patch

**Step 2**
Clone the video4linux-dvb driver source

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) 

**Step 3**
Download the path for the Terratec Cinergy T-Stick RC stick, unzip it and patch the source.

wget [http://media.cdn.ubuntu-de.org/fo.....cinergy-stick-rc.patch.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2489836/cinergy-stick-rc.patch.gz)
gunzip cinergy-stick-rc.patch.gz
patch -p0 <cinergy-stick-rc.patch

**Step 4**
Download the firmware and copy it to the firmware directory.

wget [http://www.otit.fi/~crope/v4l-dv......les/4.95.0/dvb-usb-af9015.fw](http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw)
sudo cp dvb-usb-af9015.fw  /lib/firmware/

**Step 5**
Compile the driver. Because of a bug it will crash the first time you will compile it. After the second time you can install the driver.

cd v4l-dvb
make -j2
sed -i 's/CONFIG_DVB_FIREDTV=m/CONFIG_DVB_FIREDTV=n/' ./v4l/.config
make -j2
sudo make install

**Step 6**
Always clean up after yourself.

cd ..
rm -r v4l-dvb
rm cinergy-stick-rc.patch
rm dvb-usb-af9015.fw

---

### Post by Ashrael on 2011-09-16
I bought this device:  0ccd:0097 TerraTec Electronic GmbH Cinergy T RC MKII

and I just want to say that it works out of the box in Natty (2.6.38-11-generic-pae).

Real nice picture quality and great reception (only 45% but it looks real nice)

So if you want to buy a dvb-t stick, I can say: buy this one!
It doesn't work with caffeine yet on my system, but with My-tv it works!

If anyone knows how to get the remote working? Would be nice.... :)
If I find a solution for the remote, I will post it here.


HTH!

---

### Post by Ashrael on 2012-04-26
Also works in 12.04 beta.

Although Me-tv has some problem, which I am confident will be solved soon, so I use Kaffeine now....
:popcorn:

---

