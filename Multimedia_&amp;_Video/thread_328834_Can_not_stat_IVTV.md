---
title: "Can not stat IVTV"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by jlr4u on 2006-12-31
Can not initialize IVTV.
I am using Ubuntu 2.6.17-10  wih Hauppauge PVR-500.
Can anyone point me in the right direction from the following cod? 

jlr@JLR-PVR:~$ dmesg |grep ivtv
```
[17179587.488000] ivtv:  ==================== START INIT IVTV ====================
[17179587.488000] ivtv:  version 0.7.0 (tagged release) loading
[17179587.488000] ivtv:  Linux version: 2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
[17179587.488000] ivtv:  In case of problems please include the debug info between
[17179587.488000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179587.488000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17179587.488000] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[17179587.488000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17179587.532000] ivtv0: This is the first unit of a PVR500
[17179587.712000] tuner 2-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[17179587.712000] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[17179587.876000] tda9887 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[17179588.068000] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[17179588.212000] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17179588.876000]**[COLOR="Red"] ivtv0: unable to open firmware v4l-cx2341x-enc.fw[/COLOR]**
[17179588.876000] ivtv0: did you put the firmware in the hotplug firmware directory?
[17179588.876000] ivtv0 warning: failed loading encoder firmware
[17179588.876000] ivtv0 warning: Error loading firmware -3!
[17179588.876000] ivtv0: Error -3 initializing firmware.
[17179588.876000] ivtv0: Error -12 on initialization
[17179588.876000] ivtv: probe of 0000:02:08.0 failed with error -12
[17179588.876000] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[17179588.876000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17179588.920000] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[17179589.072000] tda9887 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[17179589.084000] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[17179589.196000] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17179589.244000] ivtv0: This is the second unit of a PVR500
[17179589.244000] ivtv0: Correcting tveeprom data: no radio present on second unit
[17179589.920000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[17179589.920000] ivtv0: did you put the firmware in the hotplug firmware directory?
[17179589.920000] ivtv0 warning: failed loading encoder firmware
[17179589.920000] ivtv0 warning: Error loading firmware -3!
[17179589.920000] ivtv0: Error -3 initializing firmware.
[17179589.920000] ivtv0: Error -12 on initialization
[17179589.920000] ivtv: probe of 0000:02:09.0 failed with error -12
[17179589.920000] ivtv:  ===
```=================  END INIT IVTV  ================== 

jlr@JLR-PVR:~$ cd /lib/firmware
jlr@JLR-PVR:/lib/firmware$ md5sum v4l-*
```
305dba74bbe5905447add8883f3ecb68  v4l-cx2341x-dec.fw
d85cb08382395390dc95ac6ebc2205f9  v4l-cx2341x-enc.fw
0661f8b2693fe3123e6234557353eacc  v4l-cx2341x-init-mpeg.bin
0661f8b2693fe3123e6234557353eacc  v4l-cx2341x-init.mpg
99836e41ccb28c7b373e87686f93712a  v4l-cx25840.fw
jerry@Jerry-PVR:/lib/firmware$
```

Thank You!

---

### Post by superm1 on 2007-01-01
> **jlr4u said:**
> Can not initialize IVTV.
I am using Ubuntu 2.6.17-10  wih Hauppauge PVR-500.
Can anyone point me in the right direction from the following cod? 

jlr@JLR-PVR:~$ dmesg |grep ivtv
```
[17179587.488000] ivtv:  ==================== START INIT IVTV ====================
[17179587.488000] ivtv:  version 0.7.0 (tagged release) loading
[17179587.488000] ivtv:  Linux version: 2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
[17179587.488000] ivtv:  In case of problems please include the debug info between
[17179587.488000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179587.488000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17179587.488000] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[17179587.488000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17179587.532000] ivtv0: This is the first unit of a PVR500
[17179587.712000] tuner 2-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[17179587.712000] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[17179587.876000] tda9887 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[17179588.068000] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[17179588.212000] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17179588.876000]**[COLOR=Red] ivtv0: unable to open firmware v4l-cx2341x-enc.fw[/COLOR]**
[17179588.876000] ivtv0: did you put the firmware in the hotplug firmware directory?
[17179588.876000] ivtv0 warning: failed loading encoder firmware
[17179588.876000] ivtv0 warning: Error loading firmware -3!
[17179588.876000] ivtv0: Error -3 initializing firmware.
[17179588.876000] ivtv0: Error -12 on initialization
[17179588.876000] ivtv: probe of 0000:02:08.0 failed with error -12
[17179588.876000] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[17179588.876000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17179588.920000] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[17179589.072000] tda9887 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[17179589.084000] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[17179589.196000] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17179589.244000] ivtv0: This is the second unit of a PVR500
[17179589.244000] ivtv0: Correcting tveeprom data: no radio present on second unit
[17179589.920000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[17179589.920000] ivtv0: did you put the firmware in the hotplug firmware directory?
[17179589.920000] ivtv0 warning: failed loading encoder firmware
[17179589.920000] ivtv0 warning: Error loading firmware -3!
[17179589.920000] ivtv0: Error -3 initializing firmware.
[17179589.920000] ivtv0: Error -12 on initialization
[17179589.920000] ivtv: probe of 0000:02:09.0 failed with error -12
[17179589.920000] ivtv:  ===
```=================  END INIT IVTV  ================== 

jlr@JLR-PVR:~$ cd /lib/firmware
jlr@JLR-PVR:/lib/firmware$ md5sum v4l-*
```
305dba74bbe5905447add8883f3ecb68  v4l-cx2341x-dec.fw
d85cb08382395390dc95ac6ebc2205f9  v4l-cx2341x-enc.fw
0661f8b2693fe3123e6234557353eacc  v4l-cx2341x-init-mpeg.bin
0661f8b2693fe3123e6234557353eacc  v4l-cx2341x-init.mpg
99836e41ccb28c7b373e87686f93712a  v4l-cx25840.fw
jerry@Jerry-PVR:/lib/firmware$
```Thank You!
The md5sums for all of those files look correct, let me ask did you build from ubuntu source packages or from the .tar.gz at ivtvdriver.org?

---

### Post by jlr4u on 2007-01-02
I am just getting back to answering --  After doing a cold boot,  everything came back fine and I was able to test out the card by recording and playing back from the terminal mode.

I am not sure why the cold boot worked?  I had restarted (warm boot) several times.

Thank you!

---

### Post by superm1 on 2007-01-02
> **jlr4u said:**
> I am just getting back to answering --  After doing a cold boot,  everything came back fine and I was able to test out the card by recording and playing back from the terminal mode.

I am not sure why the cold boot worked?  I had restarted (warm boot) several times.

Thank you!

Well a possible explanation was that the firmware wasn't properly loaded into the card the first time around.  A warm boot won't necessarily reload the firmware.  A cold boot clears the firmware from the card and then on the next module load, it will load from scratch.

Glad that worked :) - I've added this bit about a cold boot to the wiki page.

---

