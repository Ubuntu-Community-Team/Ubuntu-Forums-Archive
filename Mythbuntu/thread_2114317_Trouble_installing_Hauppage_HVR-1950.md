---
title: "Trouble installing Hauppage HVR-1950"
date: 2013-02-09
forum: Mythbuntu
---

### Post by RoatanMitch on 2013-02-09
I'm fairly new to Ubuntu and MythTV but do have a long and varied list of experience in other systems. I installed the latest version of Mythbuntu about a week ago and have been unable to get the HVR-1950 recognized by the system. I've tried all that I can think of. I even installed version 10.04 (which recognized the 1950!) to make sure that I wasn't dealing with a hardware problem.

I started from scratch again today.

[LIST=1]
[*]I did a clean install of Mythbuntu 12.04.1 64-bit
[*]I installed all the updates via the Update Manager
[*]I installed git
[*]I loaded the v4l drivers
[*]git clone git://linuxtv.org/media_build.git
[*]cd media_build
[*]./build
[*]make install
[/LIST]

All seems to go fine until the make install. I get the following errors and the make fails.

[COLOR="Blue"]make[2]: Entering directory `/home/mitch/Downloads/media_build/v4l/firmware'
Installing firmwares at /lib/firmware: vicam/firmware.fw dabusb/firmware.fw cp: cannot stat `dabusb/firmware.fw': No such file or directory
dabusb/bitstream.bin cp: cannot stat `dabusb/bitstream.bin': No such file or directory
ttusb-budget/dspbootcode.bin cpia2/stv0672_vp4.bin av7110/bootcode.bin dvb-fe-bcm3510-01.fw dvb-fe-or51132-qam.fw dvb-fe-or51132-vsb.fw dvb-fe-or51211.fw dvb-fe-xc5000-1.6.114.fw dvb-ttpci-01.fw-261a dvb-ttpci-01.fw-261b dvb-ttpci-01.fw-261c dvb-ttpci-01.fw-261d dvb-ttpci-01.fw-261f dvb-ttpci-01.fw-2622 dvb-usb-avertv-a800-02.fw dvb-usb-bluebird-01.fw dvb-usb-dib0700-1.20.fw dvb-usb-dibusb-5.0.0.11.fw dvb-usb-dibusb-6.0.0.8.fw dvb-usb-dtt200u-01.fw dvb-usb-terratec-h5-drxk.fw dvb-usb-terratec-h7-az6007.fw dvb-usb-terratec-h7-drxk.fw dvb-usb-umt-010-02.fw dvb-usb-vp702x-01.fw dvb-usb-vp7045-01.fw dvb-usb-wt220u-01.fw dvb-usb-wt220u-02.fw v4l-cx231xx-avcore-01.fw v4l-cx23418-apu.fw v4l-cx23418-cpu.fw v4l-cx23418-dig.fw v4l-cx23885-avcore-01.fw v4l-cx23885-enc.fw v4l-cx25840.fw 
make[2]: Leaving directory `/home/mitch/Downloads/media_build/v4l/firmware'
make[1]: Leaving directory `/home/mitch/Downloads/media_build/v4l'[/COLOR]

When I tried this on Mythbuntu 10.04 version I had no problems. Everything seemed to work and I could see the 1950 as a device. Is there a problem with the 12.04.1 and the HVR-1950? I've googled everything I can find about this and have not found a solution.

Mitch - a bit exasperated at this moment!

---

### Post by sanderj on 2013-02-09
Did you google 

"Installing firmwares at /lib/firmware: vicam/firmware.fw dabusb/firmware.fw cp: cannot stat `dabusb/firmware.fw'"

Explanation: your firmware is missing.

In older Ubuntus, you would get the "network hardware" icon in the upper right corner to install proprieatry stuff. No so in Ubuntu 12.10 ... :-(

Have you installed "linux-firmware"? Maybe that helps?

---

