---
title: "How to get Philips SPC 200NC working?"
date: 2005-12-24
forum: Multimedia &amp; Video
---

### Post by Get on 2005-12-24
Hi all!


I have tried to get my Philips SPC 200NC webcam working, but I haven't succed. I have tried to install the pwc drivers, but I don't get any /dev/video. Is it the wrong driver or is anything else maybe wrong?

The dmesg output:
```

[4296463.163000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[4296684.495000] Linux video capture interface: v1.00
[4296684.500000] pwc Philips webcam module version 10.0.9rc1-unofficial loaded.
[4296684.500000] pwc Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
[4296684.500000] pwc Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
[4296684.500000] pwc the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
[4296684.500000] pwc Trace options: 0x00a1
[4296684.503000] usbcore: registered new driver Philips webcam
[4296888.601000] usb 3-1: USB disconnect, address 2
[4296893.163000] usb 3-1: new full speed USB device using uhci_hcd and address 3

```

Best regards,
Get

---

### Post by spacetime on 2005-12-28
I have the SPC 300NC (next model up) and also have not (yet) been able to get it working under Linux... From what I have read, this is because Philips only provides hardware specs under NDAs and come down heavily on reverse-engineering (read: C&D and/or lawsuit) so unless they provide one it seems like we won't have any Linux drivers for them :(

---

### Post by Get on 2006-01-04
[QUOTE=spacetime]I have the SPC 300NC (next model up) and also have not (yet) been able to get it working under Linux... From what I have read, this is because Philips only provides hardware specs under NDAs and come down heavily on reverse-engineering (read: C&D and/or lawsuit) so unless they provide one it seems like we won't have any Linux drivers for them :([/QUOTE]
:( :( :( 

Well, thanks for the information

---

### Post by isaric on 2006-01-19
I have also this webcam and there is a French post here :
[http://forum.ubuntu-fr.org/viewtopic.php?pid=173759#p173759]("http://forum.ubuntu-fr.org/viewtopic.php?pid=173759#p173759")
 One says to me
[quote=Isaric]Mark McClelland me dit  :

```
I believe the main chip is ZC0302, supported by this driver: http://mxhaard.free.fr/

The sensor chip is either HV7131, PAS202, or PAS106 (I don't know which).
The driver will need to be modified to detect the specific chips in your camera.
```[/quote]
 but I cannot what make some?

---

### Post by isaric on 2006-01-20
extract : 
[http://forum.ubuntu-fr.org/viewtopic.php?id=23086]("http://forum.ubuntu-fr.org/viewtopic.php?id=23086")
```
Philips SPC200NC is just supported by spca5xx chipset Vimicro VC0305 smile
 On the other hand the pilot is in release candidate (very experimental) either you await or you a little tests has your risks and dangers smile http://mxhaard.free.fr/spca50x/Doc/allinone/ to take the rc4 it is necessary to test with spcaview and the following order:
 spcaview - D /dev/video0 - F jpg - S 352x288

```

an expert to test ?

---

### Post by IdoMcFly on 2006-02-04
[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

new version with SPC200NC support

---

### Post by isaric on 2006-02-05
How to do 
i have 

isaric@acer:~$ dmesg
```
(translated set 2, code 0xaa on isa0060/serio0).
[4299061.146000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299061.340000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299061.340000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299061.572000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299061.572000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299061.707000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299061.707000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299061.791000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299061.791000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299061.867000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299061.867000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299068.403000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299068.403000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299068.567000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299068.567000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299110.558000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299110.558000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299110.694000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299110.694000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299110.778000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299110.778000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299110.913000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299110.913000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299110.967000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299110.967000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299111.103000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299111.103000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299182.405000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299182.405000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299182.628000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299182.628000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299182.830000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299182.830000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299182.966000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299182.966000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299232.306000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299232.306000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299232.471000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299232.471000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299232.555000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299232.555000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299232.660000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299232.660000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299268.556000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299268.556000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299268.693000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299268.693000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299348.919000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299348.919000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299349.054000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299349.054000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299349.109000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299349.109000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299349.214000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299349.214000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299349.298000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299349.298000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299349.374000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299349.374000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299349.458000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299349.458000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299349.564000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299349.564000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299349.618000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299349.618000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299349.724000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299349.724000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299349.867000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299349.867000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299350.061000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299350.061000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299352.742000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299352.742000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299352.847000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299352.847000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299353.138000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299353.138000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299353.303000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299353.303000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299354.313000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299354.313000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299354.448000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299354.448000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299354.532000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299354.532000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299354.694000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299354.694000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299356.871000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299356.871000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299356.977000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299356.977000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299357.272000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299357.272000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299357.436000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299357.436000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299358.962000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299358.962000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299359.672000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299359.672000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299360.178000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299360.178000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299360.343000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299360.343000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299361.120000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299361.120000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299361.285000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299361.285000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299366.453000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299366.453000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299366.639000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299366.639000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299730.613000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299730.613000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299730.719000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299730.719000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299735.619000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299735.619000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299735.724000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299735.724000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299737.550000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299737.550000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299738.483000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299738.483000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299738.686000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299738.686000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299738.792000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299738.792000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299738.851000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299738.851000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299738.956000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299738.956000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299738.985000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299738.985000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299739.121000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299739.121000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299744.951000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299744.951000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299745.057000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299745.057000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299746.904000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299746.904000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299747.010000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299747.010000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299809.613000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299809.613000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299809.748000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299809.748000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299837.654000] usbcore: deregistering driver spca5xx
[4299837.657000] drivers/usb/media/spca5xx/spca5xx-core.c: driver spca5xx deregistered
[4299838.283000] spca5xx: no version magic, tainting kernel.
[4299838.292000] usbcore: registered new driver spca5xx
[4299838.292000] drivers/usb/media/spca5xx/spca5xx-core.c: spca5xx driver 00.57.02 registered
[4300200.905000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300200.905000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300201.008000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4300201.008000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300392.530000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300392.530000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300392.724000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4300392.724000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300393.616000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300393.616000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300393.811000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4300393.811000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300537.093000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300537.093000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300537.288000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4300537.288000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300543.753000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300543.753000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300544.124000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4300544.124000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300544.208000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300544.208000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300544.314000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4300544.314000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300544.398000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300544.398000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300544.504000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4300544.504000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300544.558000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300544.558000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300544.693000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4300544.693000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
```

And with camora
```
could not connect to video device (/dev/video0). Please check connection.
```

---

### Post by Choup's on 2006-02-10
This webcam is now working for me !!
 
The driver you have to use is : [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

How to proceed ?

First, you have to create the device:
sudo mknod /dev/video0 c 81 0
sudo mknod /dev/video1 c 81 1
sudo chmod a+rw /dev/video0
sudo ln -s /dev/video0 /dev/video

Then all you have to do is to compile and install the module:
tar -xvzf spca5xx-20060202.tar.gz
cd spca5xx-20060202
export CC=gcc-3.4 (or CC=gcc-3.4 if it doesn't work)
make
sudo make install

Note: you have to use the gcc release that was used to compile your kernel. Enter cat /proc/version to verify.

And finally:
cd /lib/modules/2.6.12-10-686-smp/kernel/drivers/usb/media/spca5xx/
sudo mv spca5xx.ko spca5xx.ko.sav
sudo cp xxx/spca5xx-20060202/spca5xx.ko .

And now: 
- you plug the cam
- and it should be working (I used camorama without any parameter)

You may have to restart camorama, otherwise you may have a blank screen (I don't what is this pb...?).

---

### Post by golovan on 2006-02-23
[QUOTE=Choup's]This webcam is now working for me !!
 
[/QUOTE]
Hi!
I've purchased the 300nc-version. Has anyone got it work? 
I tried Choup's howto but well, I get "could not connect to video device (/dev/video0). Please check connection." so I guess it doesn't work for me...

---

### Post by Choup's on 2006-03-03
There is an automated tool that give an help to install the driver for the SPC X00NC webcams.

Just modify your source.list:
```
sudo gedit /etc/apt/sources.list
```

And add the following lines at the end of the file:
```
## Easycam pour webcam
deb http://blognux.free.fr/debian unstable main
```

Don't forget to update the database:
```
sudo apt-get update
```

Then, using Synaptic, install easycam2 package.
It should be installed in -->System-->Administration-->Easycam2 (or something like that)

I hope you have some basics in french as this is a french software. ;) 
This software is quite intuitive, but if you have any trouble with the language, ask and I'll translate (or look in the dictionnary :-D ) .

---

### Post by golovan on 2006-03-03
[QUOTE=Choup's]There is an automated tool that give an help to install the driver for the SPC X00NC webcams.

Just modify your source.list:
```
sudo gedit /etc/apt/sources.list
```

And add the following lines at the end of the file:
```
## Easycam pour webcam
deb http://blognux.free.fr/debian unstable main
```

Don't forget to update the database:
```
sudo apt-get update
```

Then, using Synaptic, install easycam2 package.
It should be installed in -->System-->Administration-->Easycam2 (or something like that)

I hope you have some basics in french as this is a french software. ;) 
This software is quite intuitive, but if you have any trouble with the language, ask and I'll translate (or look in the dictionnary :-D ) .[/QUOTE]

Thank's for the tip, but unfortunately it doesn't work...
It says "No camera, or no compatible camera found". I've also downloaded the latest spca from mxhaard.free.fr, which claims to support the camera, and almost got it to work, blue light and everything, but when I try to launch it, everything freezes and hangs and I have to power-button-off the computer...

---

### Post by Choup's on 2006-03-03
[QUOTE=golovan]and almost got it to work, blue light and everything, but when I try to launch it, everything freezes and hangs and I have to power-button-off the computer...[/QUOTE]

This is a good start... It is the same for me, it depends on what software I am using.
With spcaview (from mxhaard.free.fr), no problem. 
And with amsn, it works also as long as I am not clicking too fast on the configuration toolbox.:???: 
With camorama I have a lot of freezes and I also need to power-button-off the computer

It seems, actually, that the driver from mxhaard.free.fr still has some few bugs. Maybe on a later release...
Anyway, it is the only one that supports this type of webcam...

---

### Post by golovan on 2006-03-04
Wohoo!
It works! I now have it working in aMSN!
I used the spca on mxhaard.free.fr. 
Easycam and easyspca diddn't do it for me (guess it uses an older version of the driver)
I haven't succeeded in installing spcaview though.. (that's right I'm a noob:) )

But: 
[QUOTE=Choup's]
It seems, actually, that the driver from mxhaard.free.fr still has some few bugs. Maybe on a later release...
Anyway, it is the only one that supports this type of webcam...[/QUOTE]

A small bug I've run into is that the picture is upside down. So yeah, maybe it will be corrected in the next version.

---

### Post by Anbreizh on 2006-03-04
Hi ! 

I have add the last version of Spca5xx in EasyCam2 today.
If you want, you can try ;)

Ps : I don't update EasyCam1 (easycam in synaptic) and EasySpca because i only dev EasyCam2 :)

---

### Post by isaric on 2006-03-05
Extract of
[Centralisation Probleme Webcam+EasyCam]("http://forum.ubuntu-fr.org/viewtopic.php?id=16670&p=48")

 [http://mxhaard.free.fr]("http://mxhaard.free.fr") Michel Xhaard tel me :
[QUOTE=Michel Xhaard]Without the webcam difficult to better do, has less to have quality of extra clairvoyance smile what is not my case. There is no more until only one generous giver has to wait appears, because I cannot buy all the webcams market and provide the work of development gracefully[/QUOTE]

---

### Post by golovan on 2006-03-06
[QUOTE=Anbreizh]Hi ! 

I have add the last version of Spca5xx in EasyCam2 today.
If you want, you can try ;)
[/QUOTE]

Hi!
I tried it, and now it found my camera (the former version did not), installed the driver and then said I should configure it in Tools->Webcam or something. I couldn't find those Tools, so I tried to launch it in aMSN. Unfortunately that didn't work. It froze and I had to use the power-button-off to wake the pc up again. Then I reinstalled the driver form mxhaard.free.fr, and it works (still upside down, but hey..it works;) )

---

### Post by golovan on 2006-03-08
hi again.
since aMSN looks kinda ugly, I followed this thread: [http://www.ubuntuforums.org/showthread.php?t=87001&highlight=amsn]("http://www.ubuntuforums.org/showthread.php?t=87001&highlight=amsn")
 to de-uglify it. It worked like a charm, but now my camera is not working again.. It freezes up everything and also, at least I think that's why, gives me an I/O error on my fat-drive (windows share). I've tried to completely remove everything that's related to spca and reinstall, but I don't know if I have managed to remove all of it, and either way, reinstalling the driver doesn't change the freeze situation. Does anyone know how to remove every trace of it so that I can try a fresh install?

---

### Post by Dr.Fix on 2006-05-07
I've inatalled easycam2 and it finds my camera, Philips SPC600NC.
It installs driver and creates /dev/video0 and link /dev/video.
modules spca5xx and videodev are loaded (lsmod proves that) but I get 
"Could not connect to video device (/dev/video0)" opening camorama or any other software... why?

---

### Post by kayrune on 2006-06-03
I have a SPC200 webcam and trying to get it to work.

the spca5xx module included in 6.06 does not work. The one from easycam2 however does somewhat work. Out of 3 tries I have experienced computer hardlock 2 times, and a crappy upside down image 1 time. ](*,) 

Is there any future for this webcam ?

---

### Post by kayrune on 2006-07-21
I just tried the 0.6 version of the spca5xx driver, and it seems to work every time with spcaviewer, however when I started Camorama the computer hard locked!

(this is on dapper)

Edit, I also tried Ekiga, and during setup it passed "test 0" for the webcam, then during the next test the computer hard locked.

---

### Post by mock on 2006-07-22
I have a Philips SPC700NC, but i haven't figure out if 

sudo mknod /etc/video0 c 81 0
sudo mknod /etc/video1 c 81 1

i the previos post will work, i tried to figure out what "81" stands for (is that from [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) (vedor id or product id?)

please help i feel i'm like almost there to make it work!  
(Can i use the same adresss as the previos post?)

---

### Post by raules on 2006-10-31
Edgy Eft 6.10

1) System- Administration- Software Sources
                        check _Community maintaned (universe)_ 


2) sudo apt-get install module-assistant
   sudo module-assistant 
   PREPARE
   SELECT
   select module _spca5xx_
   and
   GET
   BUILD
   INSTALL

Philips SPC 300NC

---

### Post by st14n on 2006-12-21
> **raules said:**
> Edgy Eft 6.10

1) System- Administration- Software Sources
                        check _Community maintaned (universe)_ 


2) sudo apt-get install module-assistant
   sudo module-assistant 
   PREPARE
   SELECT
   select module _spca5xx_
   and
   GET
   BUILD
   INSTALL

Philips SPC 300NC

Worked like a charm for my Philips SPC 700NC. Thanks.

---

### Post by Lord Xadar on 2007-01-23
Well, tried 2 cams this evening using the latest drivers from mxhaard...

First experience - Philips SPC 200NC
I get an image that is:
-blueish or like it's only the blue channel (camorama's controls do not resolve the issue);
-upside down (but mxhaard knows about this, just put the webcam cilinder upside down to solve);
-only a quarter, what I mean is that by standin right in front of the cam I see only half of my face both horizontaly and verticaly (just my left eye, or was it the right one?);

Second experience - MicroSoft VX1000
-full picture (YAY);
-blueish picture on camorama;
-yellowish picture on ekiga;
-very dark picture in both cases (in a room with only  a standard 80-100 W equivalent fluorescent light... or something like that... well I see myself very well through my own eyes ^_^);

I'll have to try the second cam when there is some natural light (which is bad, since I chat with my girlfriend only in the evening...);

That's all folk!

---

### Post by golovan on 2007-02-06
Hi
I still haven't succeeded with my philips spc300. When I plug it in and fire up amsn. It is detected. Blue light gets lit, I choose device and channel. But then the computer freezes. Nothing works and I have to power off the hard way. Do I have to blacklist anything?

---

### Post by golovan on 2007-02-06
kind of got it to work following this thread [http://ubuntuforums.org/showthread.php?t=75284](http://ubuntuforums.org/showthread.php?t=75284).

it's upsides down, and I can't change video settings but hey, I've got a picture:)

---

### Post by OffHand on 2007-02-06
> **golovan said:**
> Hi
I still haven't succeeded with my philips spc300. When I plug it in and fire up amsn. It is detected. Blue light gets lit, I choose device and channel. But then the computer freezes. Nothing works and I have to power off the hard way. Do I have to blacklist anything?

Might wanna give my howto a try:


[http://www.ubuntuforums.org/showthread.php?t=282748](http://www.ubuntuforums.org/showthread.php?t=282748)

---

### Post by grisou on 2007-05-25
Hi,
I have a Philips SPC700NC. I installed gspcav1-20070508 using the instructions posted on:
[http://ubuntuforums.org/showthread.php?t=303330&page=7](http://ubuntuforums.org/showthread.php?t=303330&page=7)

Ekiga shows a dark picture (see attached image, I have light skin and holding a medecine bottle). The Ekiga video adjustments don't fix it. I had the same effect when I previously used spca5xx. (I then made a clean install of Ubuntu 6.10 because 7.04 messed up my system.)

Any ideas how to make the picture look normal will be appreciated. Thank you.

---

### Post by grisou on 2007-05-25
Solved! :D

I tried it with the day light, and the picture is good now. Unlike with the windows driver, the LED light of the webcam is not sufficient to get a good picture. I just need an additional and better light source for night operation. Thanks to everybody in this forum and the developers of Linux drivers.

(Philips SPC700NC, gspcav1-20070508)

---

### Post by bulwork_30 on 2007-09-25
> **raules said:**
> Edgy Eft 6.10

1) System- Administration- Software Sources
                        check _Community maintaned (universe)_ 


2) sudo apt-get install module-assistant
   sudo module-assistant 
   PREPARE
   SELECT
   select module _spca5xx_
   and
   GET
   BUILD
   INSTALL

Philips SPC 300NC

I've done that but I've problem with <include linux.h>....
While building it stops and says:............. 
  | make[3]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'      
 &#9474;   CC [M]  /usr/src/modules/spca5xx/drivers/usb/spca5xx.o                   
 &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c:39:26: error:               
 &#9474; linux/config.h: No such file or directory                                  
 &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c: In function                
 &#9474; ‘spca50x_init_isoc’:                                                       
 &#9474; /usr/src/modules/spca5xx/drivers/usb/spca5xx.c:1681: warning: assignment   
 &#9474; from incompatible pointer type                                             
 &#9474; make[4]: *** [/usr/src/modules/spca5xx/drivers/usb/spca5xx.o] Error 1     
 &#9474; make[3]: *** [_module_/usr/src/modules/spca5xx] Error 2   
  |  make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'     
 &#9474; make[2]: *** [default] Error 2                                            
 &#9474; make[2]: Leaving directory `/usr/src/modules/spca5xx'                     
 &#9474; make[1]: *** [binary-modules] Error 2                                     
 &#9474; make[1]: Leaving directory `/usr/src/modules/spca5xx'                      
 &#9474; make: *** [kdist_build] Error 2 

I tried to comment (/*<include linux.h>*/) but....i have "no permission" to save the changed file ....
Please...HELP!

---

### Post by threeisles on 2007-09-25
Hi there,

I am a real Linux newbie, I'm afraid. I have installed Xubuntu on my wife's laptop, and am trying to connect the SPC 300NC to it. I tried to follow the advice above, but the program seemed not to find the resources it needed. Also the set up seemed different (I went in through Terminal and wrote the commands in there) but I was chucked out before I could finish. 

Also is it a problem that the software is for spc5xx when mine is the spc 300nc?

If anyone knows (or can guess ) the instructions I need to follow to get this installed on Xubuntu, I''d be very thankful.

ThreeIsles

---

