---
title: "Fusion Remote MCE"
date: 2006-02-15
forum: Multimedia &amp; Video
---

### Post by Cosmic_Crusader on 2006-02-15
I've been trying to get the "Fusion Remote MCE" which comes with the "DViCO FusionHDTV DVB-T Dual Digital" card working (with the end goal to use the remote to control MythTV).

I'd really appreciate any insight people have on how to get this to work.

My environment is AMD64, and running the stock Ubuntu kernel (2.6.12-10-amd64-k8-smp).

I have downloaded, compiled and installed the latest source from the V4L Mercurial repository (as detailed: [http://linuxtv.org/repo/)]("http://linuxtv.org/repo/%29").  From this I have fully working DVB support inside MythTV, just not the infrared remote receiver.

I've also compiled my own lirc 0.7.0.1 from Ubuntu deb sources with the patch applied for the card (from [http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/)]("http://www.itee.uq.edu.au/%7Echrisp/Linux-DVB/DVICO/%29").
A summary of how I did that: > INSTALL Automake-1.6
apt-get install automake-1.6
sudo update-alternatives --set automake /usr/bin/automake-1.6

apt-get source lirc
cd lirc-0.7.0.1
patch -p1 < lirc-0.7.0-dvico.diff
## edit debian/rules -> --with-driver=dvico
dpkg-buildpackage -rfakeroot -uc -b Then as instructed on that website I have modifed "/etc/lirc/hardware.conf" to have > LIRCD_ARGS="--driver=dvico --device=/dev/usb/hiddev0" 
However, there is no /dev/usb directory, and no /dev/hiddev* files either.

After all this lirc just segfaults when I run irw to test the remote (understandable as there is no device file).

As further information, I get the following in dmesg: > [   51.526302] cx88[0]/2: found at 0000:04:08.2, rev: 5, irq: 17, latency: 64, mmio: 0xf9000000
[   51.526310] cx88[0]/2: cx2388x based dvb card
[   51.528135] DVB: registering new adapter (cx88[0]).
[   51.528145] DVB: registering frontend 0 (Zarlink MT352 DVB-T)...
[   51.597031] cx2388x blackbird driver version 0.0.5 loaded
[   52.340768] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000677164]
[   52.761988] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual USB' in warm state.[   52.761999] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   52.763609] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual USB).
[   54.776376] dvb-usb: recv bulk message failed: -110
[   54.777623] DVB: registering frontend 1 (Zarlink MT352 DVB-T)...
[   54.780249] dvb-usb: schedule remote query interval to 150 msecs.
[   54.785340] dvb-usb: DViCO FusionHDTV DVB-T Dual USB successfully initialized and connected.
[   54.785351] usbcore: registered new driver dvb_usb_cxusb 

Anyone else have any success?
Or possibly some suggestions?

I would prefer not to use the kernel from Dapper and just stick with the standard 5.10 kernel, just to keep things as close as possible to the standard Ubuntu 5.10 system.

---

### Post by Cosmic_Crusader on 2006-02-28
Managed to get this working using Ubuntu version of lirc with "dev/input" driver.

In short, I compiled the latest stable kernel (2.6.15.4): > make-kpkg -initrd --revision=dvico2 kernel_image 
I then compiled and installed the latest V4L from their Mercurial source control.  Details at [http://www.linuxtv.org/repo/]("http://www.linuxtv.org/repo/")

Then I modified "/etc/lirc/hardware.conf": > DRIVER="dev/input"
DEVICE="/dev/input/event2"
MODULES="evdev" 
The rest is just a normal dev/input setup, as the remote works like a normal keboard.  When pressing keys on the remote they appears on the console.

All I need to figure out now is how to stop the remote beign used as the console keyboard.

---

### Post by chaumurky on 2006-04-18
I'm following your success and trying it myself now. I had to make a link to aci.h for the v4l-dvb compile to complete:
 
> sudo ln -s /usr/src/linux-source-2.6.15/sound/oss/aci.h /usr/src/linux-headers-2.6.15-20-686/sound/oss/
 
I'm doing it remotely from work *cough* so I'll try the remote when I get home. Thanks for the tips.

---

