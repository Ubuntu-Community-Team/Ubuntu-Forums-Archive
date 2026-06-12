---
title: "Video driver for Xine / DVB-T"
date: 2009-05-15
forum: Multimedia Software
---

### Post by kilgore9 on 2009-05-15
Hello All,
After several hours of googling I was finally able to get my Terratec Cingergy T (DVB-T stick) to be recognized by Ubuntu 8.04.  The problem is that no matter what program I tried to use (VLC, MPlayer, MeTV, Kaffeine) the system would crash when trying to watch digital TV via the Stick.  I had this problem generally with video until I learned how to switch the video driver/module to "X11" on all the programs.  I was able to change it in VLC as well and now I can watch using VLC.  

The problem is that VLC is pretty much crappy for digital TV.  I would really like to use Kaffeine or MeTV, both running on the Xine engine.  But I can't figure out which video driver to use to keep it from crashing.  X11 is not listed as an option in Kaffeine or Xine.

Does anyone know which videodriver to use in Kaffeine/Xine to fix this glitch?

---

### Post by xc3RnbFO8P on 2009-05-15
In Terminal show the output of:
> lsusb
and
> dmesg

---

### Post by kilgore9 on 2009-05-15
Hello Ringi, here is my output

lsusb

Bus 008 Device 003: ID 0ccd:0069 TerraTec Electronic GmbH 
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 045e:007d Microsoft Corp. Notebook Optical Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

dmesg (this one is long, so I only post the DVB related info)

[  475.028754] dvb-usb: found a 'TerraTec Cinergy T USB XE' in cold state, will try to load a firmware
[  475.076260] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
[  475.125654] dvb-usb: found a 'TerraTec Cinergy T USB XE' in warm state.
[  475.125710] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  475.125995] DVB: registering new adapter (TerraTec Cinergy T USB XE)
[  475.421463] af9013: firmware version:4.95.0
[  475.424633] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
[  475.452231] mc44s803: successfully identified (ID = 14)
[  475.452800] dvb-usb: TerraTec Cinergy T USB XE successfully initialized and connected.




Like I said, the stick works, I can watch TV fine through VLC.  It just crashes in everything else... thanks for the help!

---

### Post by xc3RnbFO8P on 2009-05-15
Try:
Kaffeine> Settings> xine Engine Parameters> Video> driver, change from auto to **xshm**

---

### Post by kilgore9 on 2009-05-15
omg it works!  Thanks so much!

Would you mind telling me how you knew it had to be xshm?

---

### Post by xc3RnbFO8P on 2009-05-15
I found it here:
[https://bugs.launchpad.net/ubuntu/+source/kaffeine/+bug/366549]("https://bugs.launchpad.net/ubuntu/+source/kaffeine/+bug/366549")

---

