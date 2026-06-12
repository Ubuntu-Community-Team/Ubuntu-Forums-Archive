---
title: "Mythbuntu-Desktop on Ubuntu 15.04 No Channels Saved to DB"
date: 2015-09-25
forum: Mythbuntu
---

### Post by spyderdyne on 2015-09-25
Hello, 

I installed Ubuntu Desktop 15.04 64 bit.  I have a Hauppage 2250 dual tuner HD-PVR card installed and the drivers are good enough for Mythtv to identify the device and all the inputs.  I have set up each tuner in "Capture Cards" as a separate entry, set one of them to use Schedules Direct and my account is working there, and set the other one to pull EIT data from the air since you cant use the same SD schedule on both of them.

[IMG]http://spyderdyne.com/wp-content/uploads/2015/09/blog-myth-cards.png[/IMG]

[IMG]http://spyderdyne.com/wp-content/uploads/2015/09/blog-mythtv-video-sources.png[/IMG]

[IMG]http://spyderdyne.com/wp-content/uploads/2015/09/blog-mythtv-input-connections.png[/IMG]

Neither card has any channels.  The backend service is alive:

```
root@Ayana-Angel:~# netstat -untap | grep 6543
tcp        0      0 192.168.1.225:6543      0.0.0.0:*               LISTEN      4284/mythbackend
tcp        0      0 127.0.0.1:6543          0.0.0.0:*               LISTEN      4284/mythbackend
tcp        0      0 127.0.0.1:58200         127.0.0.1:6543          ESTABLISHED 4861/mythfrontend.r
tcp        0      0 127.0.0.1:6543          127.0.0.1:58200         ESTABLISHED 4284/mythbackend
tcp        0      0 127.0.0.1:6543          127.0.0.1:58199         ESTABLISHED 4284/mythbackend
tcp        0      0 127.0.0.1:58199         127.0.0.1:6543          ESTABLISHED 4861/mythfrontend.r
tcp6       0      0 ::1:6543                :::*                    LISTEN      4284/mythbackend

```

Running Mythfilldatabase is unable to connect for some reason:

```
2015-09-25 08:40:48.887193 I  Grab complete.  Actual data from 2015-10-08T00:00:00Z to 2015-10-09T00:00:00Z (UTC)
2015-09-25 08:40:48.887697 I  Main temp tables populated.
2015-09-25 08:40:48.888752 I  Did not find any new program data.
2015-09-25 08:40:48.889201 I  Source 2 configured to use only the broadcasted guide data. Skipping.
2015-09-25 08:40:48.890437 E  Failed to fetch some program info
2015-09-25 08:40:48.890451 I  Adjusting program database end times.
2015-09-25 08:40:48.890588 I      0 replacements made
2015-09-25 08:40:48.890591 I  Marking generic episodes.
2015-09-25 08:40:48.890799 I      Found 0
2015-09-25 08:40:48.890803 I  Extending non-unique programids with multiple parts.
2015-09-25 08:40:48.891066 I      Found 0
2015-09-25 08:40:48.891069 I  Fixing missing original airdates.
2015-09-25 08:40:48.891327 I      Found 0 with programids
2015-09-25 08:40:48.891656 I      Found 0 without programids
2015-09-25 08:40:48.891659 I  Marking repeats.
2015-09-25 08:40:48.892342 I      Found 0
2015-09-25 08:40:48.892346 I  Unmarking new episode rebroadcast repeats.
2015-09-25 08:40:48.892536 I      Found 0
2015-09-25 08:40:48.892682 I  Marking episode first showings.
2015-09-25 08:40:48.893492 I      Found 0
2015-09-25 08:40:48.893496 I  Marking episode last showings.
2015-09-25 08:40:48.894314 I      Found 0
2015-09-25 08:40:48.895440 I  DataDirect: Grabbing next suggested grabbing time
2015-09-25 08:40:49.296349 I  Suggested Time data: 613 bytes
2015-09-25 08:40:49.296763 I  DataDirect: BlockedTime is: 2015-09-25T13:40:49Z
2015-09-25 08:40:49.296917 I  DataDirect: nextSuggestedTime is: 2015-09-26T06:24:49Z
2015-09-25 08:40:49.298148 I  
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================

```

/root/.mythtv/config.xml, /home/spyderdyne/.mythtv/config.xml have the correct settings.  When I run "mythtv-setup", "mythtv-setup.real", "mythbackend", or "mythfrontend", they all list the 192.168.1.225 IP address, but for some reason some services are trying to access the DB from 127.0.0.1.  I have run mythtv-setup multiple times and it always has the correct settings already, I have run "dpkg-recoufigure mythtv-common" multiple times with the correct settings already populated as well. 


This should not be an issue because I am binding MySQL to 0.0.0.0, and have issued a grant for the mythtv user to access any interface:

```
GRANT ALL on mythconverg.* to 'mythtv'@'%' IDENTIFIED BY 'password';
```

As you can see from the netstat output it should have no issues connecting to either address on the backend either.  I am not allowed to scan for channels on either tuner, and am unable to use either tuner because there are no channels defined.  What am i missing here?  Any help would be appreciated.

Here are my tuner configs,

Tuner 0 Setup:

[IMG]http://spyderdyne.com/wp-content/uploads/2015/09/mythtv-video0-setup.png[/IMG]

[IMG]http://spyderdyne.com/wp-content/uploads/2015/09/mythtv-sd-antenna0-source.png[/IMG]

[IMG]http://spyderdyne.com/wp-content/uploads/2015/09/mythtv-sd-antenna0-input.png[/IMG]

Tuner 1 Setup:

[IMG]http://spyderdyne.com/wp-content/uploads/2015/09/eit-antenna1-source.png[/IMG]

[IMG]http://spyderdyne.com/wp-content/uploads/2015/09/mythtv-eit-antenna1-input.png[/IMG]


Thanks.

---

### Post by spyderdyne on 2015-09-25
Changing the Card Type to DVB... lets me scan for and input channels form SD, but not see video on the frontend.  This card has dual tuners, and dual mpeg-2 encoders.  Apparently everything is working as expected, and I just have no clue what to select in the MythTV menus to make it work properly.  I will continue to find someone who is using an HD tuner card with built in MGEP-2 encoders and see if I can determine what the settings are supposed to be, but after playing with the settings for about 3 hours I have still not stumbled upon a working set of MythTV config options.

Thanks.

---

### Post by aelfric55 on 2015-09-26
Beyond the driver have you got the correct firmware installed for this card? A link to it if necessary at [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2250](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2250)

If you are trying to receive over-the-air digital TV with this card, you have set up the wrong device node for digital. That is, the nodes /dev/video0 (1,2, etc.) are where an "MPEG2 encoder" or other encoder is set up to encode analog TV (nowadays mostly just signals from a cable box or satellite box in the US). An ATSC digital TV stream doesn't get encoded by the card at all when you receive it, MPEG2 or otherwise.  A DVB tuner for receiving over-the-air ATSC digital TV will be set up on a node that looks something like  /dev/dvb/adapter0/frontend0 (and /dev/dvb/adapter1/frontend0, etc.) These are the nodes my 2250 is set up on to do ATSC on the one machine I have that uses this card. You are correct that the card type should be set in mythtv-setup as "DVB-T/S/C, ATSC" 

If the 2250 is not being registered on two of the /dev/dvb/...  nodes at bootup (in addition to the /dev/videoX and /dev/vbiX analog tv nodes), this can be ascertained by looking at the output from ```
sudo dmesg | grep saa7164
``` The problem is usually missing firmware or firmware failing to load.

---

### Post by spyderdyne on 2015-09-27
Looks like the firmware is loading, but the DVB devices fail to register:

> root@Ayana-Angel:~# dmesg | grep saa7164
[    5.846533] saa7164 driver loaded
[    5.846628] CORE saa7164[0]: subsystem: 0070:f111, board: Hauppauge WinTV-HVR2250 [card=3,insmod option]
[    5.846632] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xf7800000
[    6.002632] saa7164_downloadfirmware() no first image
[    6.002702] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[    6.202784] saa7164_downloadfirmware() firmware read 4019072 bytes.
[    6.202787] saa7164_downloadfirmware() firmware loaded.
[    6.202791] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[    6.202796] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[    6.202797] saa7164_downloadfirmware() BSLSize = 0x0
[    6.202797] saa7164_downloadfirmware() Reserved = 0x0
[    6.202798] saa7164_downloadfirmware() Version = 0x1661c00
[   13.052457] saa7164_downloadimage() Image downloaded, booting...
[   13.156363] saa7164_downloadimage() Image booted successfully.
[   15.853984] saa7164_downloadimage() Image downloaded, booting...
[   17.620436] saa7164_downloadimage() Image booted successfully.
[   17.649364] saa7164_api_i2c_read() error, ret(2) = 0x13
[   17.717292] saa7164_dvb_register() Frontend initialization failed
[   17.717348] saa7164_initdev() Failed to register dvb adapters on porta
[   17.719514] saa7164_dvb_register() Frontend initialization failed
[   17.719569] saa7164_initdev() Failed to register dvb adapters on portb
[   17.719713] saa7164[0]: registered device video0 [mpeg]
[   17.956499] saa7164[0]: registered device video1 [mpeg]
[   18.172991] saa7164[0]: registered device vbi0 [vbi]
[   18.173079] saa7164[0]: registered device vbi1 [vbi]


I appear to have the correct firmware loaded [per the documentation]("http:..http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2250#Firmware"):

> 
root@Ayana-Angel:~# ls /lib/firmware/NXP*
/lib/firmware/NXP7164-2010-03-10.1.fw


Apparently the partially successful loading of the DVB portion does not create /dev/dvb/* devices because they are missing, although /dev/videoX and /dev/vbiX devices are being loaded successfully.  I did notice that there are 8 device options relating to different cards supplied by these drivers.  I am forcing [card=3,insmod option] in /etc/modprobe.d/options.conf as it is the first option for the 2250 card.  I will try forcing some different ones and see if one of those allows the DVB devices to load on reboot.

I have re-downloaded and re-extracted the drivers/firmware and have suppressed the card=3 option.  I will spend some time playing with it and see what happens.

Thanks for your help.

---

### Post by spyderdyne on 2015-09-27
Suppressing the card selection returns the options list:

```
root@Ayana-Angel:~# sudo dmesg | grep saa7164
[    6.577839] saa7164 driver loaded
[    6.577923] saa7164[0]: Your board isn't known (yet) to the driver.
saa7164[0]: Try to pick one of the existing card configs via
saa7164[0]: card=<n> insmod option.  Updating to the latest
saa7164[0]: version might help as well.
[    6.578005] saa7164[0]: Here are valid choices for the card=<n> insmod option:
[    6.578064] saa7164[0]:    card=0 -> Unknown
[    6.578115] saa7164[0]:    card=1 -> Generic Rev2
[    6.578173] saa7164[0]:    card=2 -> Generic Rev3
[    6.578226] saa7164[0]:    card=3 -> Hauppauge WinTV-HVR2250
[    6.578278] saa7164[0]:    card=4 -> Hauppauge WinTV-HVR2200
[    6.578330] saa7164[0]:    card=5 -> Hauppauge WinTV-HVR2200
[    6.578383] saa7164[0]:    card=6 -> Hauppauge WinTV-HVR2200
[    6.578435] saa7164[0]:    card=7 -> Hauppauge WinTV-HVR2250
[    6.578487] saa7164[0]:    card=8 -> Hauppauge WinTV-HVR2250
[    6.578539] saa7164[0]:    card=9 -> Hauppauge WinTV-HVR2200
[    6.578592] saa7164[0]:    card=10 -> Hauppauge WinTV-HVR2200
[    6.578665] CORE saa7164[0]: subsystem: 0070:f111, board: Unknown [card=0,autodetected]
[    6.578668] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xf7800000
[    6.578676] saa7164_initdev() Unsupported board detected, registering without firmware

```

Trying card=7 and card=8 produces the same issue with the DVB firmware:

```

root@Ayana-Angel:~# sudo dmesg | grep saa7164
[    6.671883] saa7164 driver loaded
[    6.671990] CORE saa7164[0]: subsystem: 0070:f111, board: Hauppauge WinTV-HVR2250 [card=8,insmod option]
[    6.671994] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xf7800000
[    6.829021] saa7164_downloadfirmware() no first image
[    6.829089] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[    6.968008] saa7164_downloadfirmware() firmware read 4019072 bytes.
[    6.968013] saa7164_downloadfirmware() firmware loaded.
[    6.968022] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[    6.968028] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[    6.968030] saa7164_downloadfirmware() BSLSize = 0x0
[    6.968031] saa7164_downloadfirmware() Reserved = 0x0
[    6.968033] saa7164_downloadfirmware() Version = 0x1661c00
[   13.814873] saa7164_downloadimage() Image downloaded, booting...
[   13.918778] saa7164_downloadimage() Image booted successfully.
[   16.512498] saa7164_downloadimage() Image downloaded, booting...
[   18.278945] saa7164_downloadimage() Image booted successfully.
[   18.323949] saa7164[0]: Warning: Unknown Hauppauge model #0
[   18.324002] saa7164[0]: Hauppauge eeprom: model=0
[   18.351829] saa7164_dvb_register() Frontend initialization failed
[   18.351884] saa7164_initdev() Failed to register dvb adapters on porta
[   18.354439] saa7164_api_i2c_read() error, ret(2) = 0x9
[   18.354545] saa7164_dvb_register() Frontend initialization failed
[   18.354598] saa7164_initdev() Failed to register dvb adapters on portb
[   18.354714] saa7164[0]: registered device video0 [mpeg]
[   18.590893] saa7164[0]: registered device video1 [mpeg]
[   18.806170] saa7164[0]: registered device vbi0 [vbi]
[   18.806235] saa7164[0]: registered device vbi1 [vbi]

```

Is it possible that I need a different driver/firmware or is this maybe the behavior I would expect if they sent me a 2255 card instead of the 2250 I purchased?

Thanks.

---

### Post by spyderdyne on 2015-09-27
It looks like i may be sending this thing back and getting something else.  Looks like they sold me a 2250 and sent me a 2255.

[http://ubuntuforums.org/showthread.php?t=2241753&highlight=2250+db](http://ubuntuforums.org/showthread.php?t=2241753&highlight=2250+db)

---

### Post by spyderdyne on 2015-09-28
Anyone know of a good dual tuner card that works and is available somewhere?  I have a pair of PCIe 1X slots internally, but would consider USB maybe.  Every one in the LinuxTV list is unavailable.

---

### Post by aelfric55 on 2015-09-28
Supposedly the 2255s are supported now, starting with kernel 4.2. At least the digital side is. Perhaps all you need is to get/compile a bleeding edge kernel and module load.

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2255](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2255)

---

### Post by spyderdyne on 2015-09-28
Nice.  I upgraded my kernel from these instructions:

```

# wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2-unstable/linux-headers-4.2.0-040200_4.2.0-040200.201508301530_all.deb
# wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2-unstable/linux-headers-4.2.0-040200-generic_4.2.0-040200.201508301530_amd64.deb
# wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2-unstable/linux-image-4.2.0-040200-generic_4.2.0-040200.201508301530_amd64.deb

dpkg -i linux-headers-4.2.0-*.deb linux-image-4.2.0-*.deb

sudo update-grub

```

After a reboot I confirmed my kernel version:

```

Linux Ayana-Angel 4.2.0-040200-generic #201508301530 SMP Sun Aug 30 19:31:40 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

Then I removed the old drivers:

```

rm -rf /lib/firmware/v4l-saa7164-1.0.*

```

Next, I removed my declaration setting which card type I am using:

```

# cat /etc/modprobe.d/options.conf

#options saa7164 card=8

```

After a reboot I got this:

```

root@Ayana-Angel:~# dmesg | grep saa7164
[    5.894366] saa7164 driver loaded
[    5.894455] CORE saa7164[0]: subsystem: 0070:f111, board: Hauppauge WinTV-HVR2255 [card=12,autodetected]
[    5.894459] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xf7800000
[    6.053463] saa7164_downloadfirmware() no first image
[    6.053546] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[    6.434416] saa7164_downloadfirmware() firmware read 4019072 bytes.
[    6.434421] saa7164_downloadfirmware() firmware loaded.
[    6.434430] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[    6.434436] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[    6.434438] saa7164_downloadfirmware() BSLSize = 0x0
[    6.434439] saa7164_downloadfirmware() Reserved = 0x0
[    6.434441] saa7164_downloadfirmware() Version = 0x1661c00
[   13.283126] saa7164_downloadimage() Image downloaded, booting...
[   13.387035] saa7164_downloadimage() Image booted successfully.
[   16.084660] saa7164_downloadimage() Image downloaded, booting...
[   17.851103] saa7164_downloadimage() Image booted successfully.
[   17.895651] saa7164[0]: Hauppauge eeprom: model=151061
[   18.020419] DVB: registering new adapter (saa7164)
[   18.020422] saa7164 0000:02:00.0: DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3306A VSB/QAM Frontend)...
[   18.058573] DVB: registering new adapter (saa7164)
[   18.058575] saa7164 0000:02:00.0: DVB: registering adapter 1 frontend 0 (LG Electronics LGDT3306A VSB/QAM Frontend)...
[   18.058991] saa7164[0]: registered device video0 [mpeg]
[   18.294717] saa7164[0]: registered device video1 [mpeg]
[   18.506863] saa7164[0]: registered device vbi0 [vbi]
[   18.506962] saa7164[0]: registered device vbi1 [vbi]

```

Checking my devices I see the DVB devices are alive now:

```

root@Ayana-Angel:~# ls /dev/dvb/adapter0/
demux0  dvr0  frontend0  net0
root@Ayana-Angel:~# ls /dev/dvb/adapter1/
demux0  dvr0  frontend0  net0

```

Configuring MythTV capture cards now.  Will let you know if it worked and I can cancel my RMA.

:popcorn:

---

### Post by spyderdyne on 2015-09-28
The proprietary NVidia drivers really don't like this kernel:

```

root@Ayana-Angel:~# sudo startx
xauth:  file /root/.Xauthority does not exist


X.Org X Server 1.17.1
Release Date: 2015-02-10
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.19.0-28-generic x86_64 Ubuntu
Current Operating System: Linux Ayana-Angel 4.2.0-040200-generic #201508301530 SMP Sun Aug 30 19:31:40 UTC 2015 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-040200-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash
Build Date: 11 September 2015  10:30:58AM
xorg-server 2:1.17.1-0ubuntu3.1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.32.6
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Mon Sep 28 09:59:03 2015
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
modprobe: ERROR: ../libkmod/libkmod-module.c:816 kmod_module_insert_module() could not find module by name='nvidia_340'
modprobe: ERROR: could not insert 'nvidia_340': Function not implemented
xinit: connection to X server lost

waiting for X server to shut down error setting MTRR (base = 0xf1000000, size = 0x00e00000, type = 1) Invalid argument (22)
(II) Server terminated successfully (0). Closing log file.

```

Updating to the latest driver also fails.  I located the latest driver:

```

root@Ayana-Angel:~# apt-cache search nvidia

nvidia-340 - NVIDIA binary driver - version 340.76
nvidia-340-dev - NVIDIA binary Xorg driver development files
nvidia-340-updates - NVIDIA binary driver - version 340.76
nvidia-340-updates-dev - NVIDIA binary Xorg driver development files
nvidia-340-updates-uvm - Transitional package for nvidia-340-updates
nvidia-340-uvm - Transitional package for nvidia-340
nvidia-346 - NVIDIA binary driver - version 346.59
nvidia-346-dev - NVIDIA binary Xorg driver development files
nvidia-346-updates - NVIDIA binary driver - version 346.59
nvidia-346-updates-dev - NVIDIA binary Xorg driver development files
nvidia-346-updates-uvm - Transitional package for nvidia-346-updates
nvidia-346-uvm - Transitional package for nvidia-346

```

...then installed it:

```

root@Ayana-Angel:~# apt-get install nvidia-346
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-28 linux-headers-3.19.0-28-generic
  linux-image-3.19.0-28-generic linux-image-extra-3.19.0-28-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libcuda1-346 nvidia-opencl-icd-346
The following packages will be REMOVED:
  libcuda1-340 nvidia-340 nvidia-opencl-icd-340
The following NEW packages will be installed:
  libcuda1-346 nvidia-346 nvidia-opencl-icd-346
0 upgraded, 3 newly installed, 3 to remove and 0 not upgraded.
Need to get 72.5 MB of archives.
After this operation, 9,661 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ vivid/restricted libcuda1-346 amd64 346.59-0ubuntu1 [7,742 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ vivid/restricted nvidia-346 amd64 346.59-0ubuntu1 [56.9 MB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ vivid/restricted nvidia-opencl-icd-346 amd64 346.59-0ubuntu1 [7,827 kB]
Fetched 72.5 MB in 7s (9,726 kB/s)                                             
(Reading database ... 247106 files and directories currently installed.)
Removing libcuda1-340 (340.76-0ubuntu2) ...
Removing nvidia-340 (340.76-0ubuntu2) ...
Stopping nvidia-persistenced
nvidia-persistenced: no process found
Done.
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/nvidia-340-prime/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-340-prime/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
INFO:Disable nvidia-340
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
update-initramfs: deferring update (trigger activated)
Removing nvidia-opencl-icd-340 (340.76-0ubuntu2) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for initramfs-tools (0.103ubuntu15) ...
update-initramfs: Generating /boot/initrd.img-4.2.0-040200-generic
Selecting previously unselected package libcuda1-346.
(Reading database ... 246815 files and directories currently installed.)
Preparing to unpack .../libcuda1-346_346.59-0ubuntu1_amd64.deb ...
Unpacking libcuda1-346 (346.59-0ubuntu1) ...
Selecting previously unselected package nvidia-346.
Preparing to unpack .../nvidia-346_346.59-0ubuntu1_amd64.deb ...
Unpacking nvidia-346 (346.59-0ubuntu1) ...
Selecting previously unselected package nvidia-opencl-icd-346.
Preparing to unpack .../nvidia-opencl-icd-346_346.59-0ubuntu1_amd64.deb ...
Unpacking nvidia-opencl-icd-346 (346.59-0ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.7.0.2-5) ...
Setting up libcuda1-346 (346.59-0ubuntu1) ...
Setting up nvidia-346 (346.59-0ubuntu1) ...
update-alternatives: using /usr/lib/nvidia-346/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-346/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/share/nvidia-346/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-346
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
Adding system user `nvidia-persistenced' (UID 124) ...
Adding new group `nvidia-persistenced' (GID 135) ...
Adding new user `nvidia-persistenced' (UID 124) with group `nvidia-persistenced' ...
Not creating home directory `/'.
Loading new nvidia-346-346.59 DKMS files...
First Installation: checking all kernels...
Building only for 4.2.0-040200-generic
Building for architecture x86_64
Building initial module for 4.2.0-040200-generic
ERROR (dkms apport): kernel package linux-headers-4.2.0-040200-generic is not supported
Error! Bad return status for module build on kernel: 4.2.0-040200-generic (x86_64)
Consult /var/lib/dkms/nvidia-346/346.59/build/make.log for more information.
Setting up nvidia-opencl-icd-346 (346.59-0ubuntu1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Processing triggers for initramfs-tools (0.103ubuntu15) ...
update-initramfs: Generating /boot/initrd.img-4.2.0-040200-generic

```

Still no worky.  Reverted to only the blessed Ubuntu Nouveau (defualt) drivers:

```

root@Ayana-Angel:~# apt-get remove nvidia-346
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-28 linux-headers-3.19.0-28-generic
  linux-image-3.19.0-28-generic linux-image-extra-3.19.0-28-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  nvidia-346
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 283 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 247132 files and directories currently installed.)
Removing nvidia-346 (346.59-0ubuntu1) ...
Stopping nvidia-persistenced
nvidia-persistenced: no process found
Done.
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/nvidia-346-prime/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-346-prime/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
INFO:Disable nvidia-346
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
update-initramfs: deferring update (trigger activated)
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for initramfs-tools (0.103ubuntu15) ...
update-initramfs: Generating /boot/initrd.img-4.2.0-040200-generic

```


```

root@Ayana-Angel:~# uname -a
Linux Ayana-Angel 4.2.0-040200-generic #201508301530 SMP Sun Aug 30 19:31:40 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

oot@Ayana-Angel:~# cat /etc/issue
Ubuntu 15.04 \n \l

```


It works!  Yay!  In fact, the Ubuntu default drivers HDMI sound actually works with the new kernel so apparently no need for proprietary ones now!

Winning!!!

---

### Post by spyderdyne on 2015-09-28
MythTV is unable to open/load the new card frontend even though it can see it.  Channel scans are failing, but at least it knows it's HD now...

Here is the new setup in MythTV


Capture cards:
[IMG]http://spyderdyne.com/wp-content/uploads/2015/09/2255-cards.png[/IMG]

[IMG]http://spyderdyne.com/wp-content/uploads/2015/09/2255-device0.png[/IMG]

[IMG]http://spyderdyne.com/wp-content/uploads/2015/09/2255-device1.png[/IMG]

I am reusing my old Antenna0 input from before with SD configured:

[IMG]http://spyderdyne.com/wp-content/uploads/2015/09/2255-input-adapter0.png[/IMG]

[IMG]http://spyderdyne.com/wp-content/uploads/2015/09/2255-inputs-interactions.png[/IMG]

Now we see that although the driver is loaded and the DVB devices are present for duty, MythTV doesnt seem to be able to use them:

[IMG]http://spyderdyne.com/wp-content/uploads/2015/09/2255-failtoopen.png[/IMG]

When we attempt a scan now, MythTV gets angry with us and tells us to check the console:

[IMG]http://spyderdyne.com/wp-content/uploads/2015/09/2255-scanning-error.png[/IMG]

But the console isn't telling us anything we didn't already know:

[IMG]http://spyderdyne.com/wp-content/uploads/2015/09/2255-console-unable2loaddvb.png[/IMG]

I have to assume that this massive jump in Kernel version and the 0.27 MythTV version do not play well together, and that 0.27 really doesn't like this driver.  I think the only thing left to try is to attempt to install 0.28 and see if that works, and if not I still need a different capture card.

---

### Post by aelfric55 on 2015-09-28
Well this is a surprise right before the goal line. I've had not many problems with mythtv 0.27 compiled on kernel 3.10 working on kernel 4.1.6, so I think the issue is more likely a bug in 0.27 that may not have even been addressed in yet 0.28. But who knows?

Just as a shot in the dark, are you running mythtv-setup as root? I've had occasional new installations where user/group assignments have gotten a little out-of-whack, and mythtv-setup only as root (and only on the machine itself, not through ssh login) could physically access the card.

Otherwise, good luck with the 0.28 installation.

---

### Post by spyderdyne on 2015-09-28
Since we are so far ahead of the stable kernel, I enabled the pre-release software updates option.  Hopefully this counteracts the wackiness I am seeing instead of adding to it.  Adding the MythTV 0.28 PPA repository and running upgrades:

```

# add-apt-repository ppa:mythbuntu/0.28 
# apt-get update
# apt-get upgrade
# apt-get dist-upgrade

```
 
Myth 0.28 installed successfully and I rebooted.  After reboot I opened MythTV Backend and was prompted to upgrade the database.  I upgraded it and navigated to inputs, and MythTV is still unable to open the frontend0 and frontend1 devices.

I am officially out of things to try.  If anyone has any suggestions before I send this card back and downgrade the kernel again please feel free to reach out to me.

Thanks.

---

### Post by spyderdyne on 2015-09-28
I prefer Nouveau if it works.  No reason to run a proprietary driver unless you have to.

;)

---

### Post by aelfric55 on 2015-09-28
I suspect that the Ubuntu 0.28 package was compiled against the same older 3.1x series kernels as the 0.27 package. I almost wish I had one of these cards on hand --I'd compile a  new installation of 0.27 on a 4.2 series kernel to establish whether or not the problem is a pure mythtv issue, which I believe it likely is.  But compiling software for Ubuntu leads to the use of strong language.

So returning the card is probably the correct course. As well as corresponding with the Mythtv devs over at Gossamer Threads to see whether they're aware of the issue.

All the best.

---

### Post by spyderdyne on 2015-09-28
I purchased the card from Newegg.com through a retailer named Humble Brothers ($111.38 + $11.50 shipping.)  After submitting an RMA they informed me that they would gladly refund the 2255 card or exchange it for an actual new bonafide 2250.  After searching through the LinuxTV approved functioning cards list for this I think I will do the latter and just use the older version with the older firmware.  I was unable to find any other supported cards that are available to purchase new that fit into a PCIe or PCIx 1X slot.  

At least now I know what to do to make it work when the correct hardware arrives.

I am not running MythTV as root b/c Ubuntu doesn't let me log in as root as a matter of course, which is best practice.  My thinking is it that if /dev/vbi and /dev/video are accessible to non-root users and loaded by the same driver, then /dev/dvb* should have the same perms.

Thanks everyone.

---

### Post by aelfric55 on 2015-09-28
I can attest that the "real" 2250s work very well with all kernels I've tried them on from 3.10 to 4.1, with no peculiarities of setup other than making sure the firmware is installed.  Setup in mythtv 0.27 is completely straightforward as well. You shouldn't have any problems.

---

### Post by spyderdyne on 2015-09-29
This card is one of the better options for sure.  Im excited to get the new one now.  I came into this without knowing anything about MythTV and am pretty confident with it having had these issues so this has been a good experience.  I also have a couple of LG televisions and the tuners are pretty sensetive so this is a good choice if you can get one that works.

---

### Post by spyderdyne on 2015-10-05
Apparently I know more about this issue than the seller.  They do not in fact have a new 2250 and it looks like I am going to have to pick up a used one since there do not seem to be any better options available that is approved by LinuxTV:

"----- From: <Humble Brothers LLC>  To: <James Scollard> -----

James,
So after your last email, I called the warehouse to verify and the parts we
received from Hauppauge are labeled 2250 on the box, but the cards are
actually 2255's. The model for the 2250 and 2255 is actually the same model
number which is 1229. I went around and called all the suppliers I could
find for the card and it looks like this is the same case with all the
suppliers. The 2250's I can find that are actual 2250's are used items. I
apologize but I am unable to find any 2250's. I followed up with Hauppage
and [B]they said they discontinued and recalled the 2250 due to a problem with
the chip[/B]. I apologize for all the confusion on this item. I will get an
immediate refund processed for you and If I can find an actual 2250 I will
send you an email with the information.

Thank you"

Is anyone ware of a defect with the 2250 chipsets?  People are still running these without issues so unless its a Windoze problem this is probably drek.

---

### Post by spyderdyne on 2015-10-05
Is this a legimitate option?

TBS 6704 ATSC / Clear QAM Quad Tuner

> [http://www.tbsdtv.com/products/tbs6704-atsc-or-clear-qam-quad-tuner-pcie-card.html](http://www.tbsdtv.com/products/tbs6704-atsc-or-clear-qam-quad-tuner-pcie-card.html)

I dont see it on the LinuxTV supported devices wiki, but this guy has a similar device and his works with MythTV:

> [http://ubuntuforums.org/showthread.php?t=2289090&p=13368072#post13368072](http://ubuntuforums.org/showthread.php?t=2289090&p=13368072#post13368072)

They also seem to stay current with Linux kernel versions and there are driver updates available to fix compatibility issues with kernels 4.1 and 4.2 already.  I think this is my new target device.

---

### Post by Jean-Marc_Vaillanc on 2015-10-13
> **spyderdyne said:**
> I purchased the card from Newegg.com through a retailer named Humble Brothers ($111.38 + $11.50 shipping.)  After submitting an RMA they informed me that they would gladly refund the 2255 card or exchange it for an actual new bonafide 2250.  After searching through the LinuxTV approved functioning cards list for this I think I will do the latter and just use the older version with the older firmware.  I was unable to find any other supported cards that are available to purchase new that fit into a PCIe or PCIx 1X slot.  

At least now I know what to do to make it work when the correct hardware arrives.

I am not running MythTV as root b/c Ubuntu doesn't let me log in as root as a matter of course, which is best practice.  My thinking is it that if /dev/vbi and /dev/video are accessible to non-root users and loaded by the same driver, then /dev/dvb* should have the same perms.

Thanks everyone.

How strange that you cannot make that card (presumably a 2225) work. I live in Canada and probably bought the same card a few weeks ago. The box says it is a new model, but still a 2250, not a 2225, but I don't believe it. I installed it on a fairly old computer with a small hard drive just to test it with Mythbuntu, before installing it on my real  (Gentoo) box, thinking that it would be easy, since the LinuxTV.org site says it works. Like you, I could not have the DVB part of the card initialized. After many hours of tries, search, and loading of firmware, I stumbled upon this very thread. 

I followed your instructions on how to install and switch to the 4.2 kernel (i386), and voilà, the card works! I used w_scan to detect the available channels, took one from the list, fired up VLC, chose "capture card", ATSC, input the frequency, and clicked on "play". To my great pleasure, I was now watching live TV, playing smoothly with sound in sync.

Thank you for the instructions, spyderdyne!

Did you try w_scan when you managed to have the card initialize completely?

Now for MythTV. I must admit that I have not been successful in using the card with MythTV, but I think this is due to some kind of server misconfiguration. Since I already have a working MythTV system, I configured my test box as a slave. What I managed to obtain is the main box seeing the adapter on the slave, but saying that it is not connected (when I check the tuner page in Mythweb). Last night, I finally found a page on MythTV's website were they explain [how to configure a slave and a master backend correctly]("https://www.mythtv.org/wiki/MythTV-HOWTO#Configuring_a_non-master_backend"), and realized that I have made some mistakes, like running a database and configuring the video source in mythtv-setup on the slave. So, if I can find some time this week, I will try a complete reinstall of Mythbuntu, a kernel upgrade, and a correct configuration of the slave to see if I can make all that work. 

I hope to come back with good news...

J-M

---

### Post by Jean-Marc_Vaillanc on 2015-10-17
Well, I have good news and less good news. The good news is that I succeeded in making the card work with MythTV (0.27, Mythbuntu) on my test computer. I was able to have the two tuners registered in the program, and have them scan for available channels. Not too many, because the computer and the (old style) TV antenna are in the basement, not even close to a window.

The less good news is that I can't configure the test box as a slave server to the main one, and I can't figure out why. The main server sees the tuners of the slave's adapter, but says that they are not connected. Why don't I just install the card in the main server? Well, this server has been on service since 2006. Three different computers, but still the same server, and I see it as a "production" server. The family uses it a lot. It runs on Gentoo, and that distribution is still only at stable kernel version 4.0.5, and i'm using 3.12 as of now. That did not prevent me to install the 4.2 kernel. I still have to configure it and try it before installing the card in the box and maybe recompile MythTV 0.27 against that new kernel, just in case.

Now, back to the test machine. What I did to make it work : I first did a clean install of Mythbuntu. Once installed, the only thing I configured in mythtv-setup was the IP address of the server to 127.0.0.1. That way, it would not try to connect to the main server. Then I immediately proceeded to upgrade to kernel 4.2, as per spyderdyne's instructions:

```

[COLOR=#000000][FONT=Ubuntu Mono]# wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2-unstable/linux-headers-4.2.0-040200_4.2.0-040200.201508301530_all.deb
[/FONT][/COLOR]# wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2-unstable/linux-headers-4.2.0-040200-generic_4.2.0-040200.201508301530_i386.deb
# wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2-unstable/linux-image-4.2.0-040200-generic_4.2.0-040200.201508301530_i386.deb

dpkg -i linux-headers-4.2.0-*.deb linux-image-4.2.0-*.deb

sudo update-grub  
```

After a reboot, I did

```
jmv@myth2:~$ uname -a
Linux myth2 4.2.0-040200-generic #201508301530 SMP Sun Aug 30 19:44:19 UTC 2015 i686 i686 i686 GNU/Linux 
```

to confirm that kernel 4.2 was running. So far, so good.
After that, I upgraded the system.

```
sudo apt-get update
sudo apt-get upgrade
```

I rebooted and then I proceeded to the [Hauppauge WinTV-HVR 2250 page]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2250") on LinuxTV.org website and downloaded only the NXP firmware ([http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw](http://www.steventoth.net/linux/hvr22xx/firmwares/4019072/NXP7164-2010-03-10.1.fw)), as the site says it should be sufficient, and copied it in /lib/firmware.

I then unloaded the saa7164 module and reloaded it

```
sudo modprobe -r saa7164
sudo modprobe saa7164 
```

It took 15-20 seconds for the command prompt to reappear. I guess it was the time needed to load the firmware and initialize the frontend (DVB)

```
jmv@myth2:~$ dmesg |grep saa71
[   11.399745] saa7164 driver loaded
[   11.400218] CORE saa7164[0]: subsystem: 0070:f111, board: Hauppauge WinTV-HVR2255 [card=12,autodetected]
[   11.400229] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 18, latency: 0, mmio: 0xfd400000
[   11.400238] saa7164_enable_msi() Failed to enable MSI interrupt. Falling back to a shared IRQ
[   11.560031] saa7164_downloadfirmware() no first image
[   11.560568] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   12.790069] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   12.790078] saa7164_downloadfirmware() firmware loaded.
[   12.790099] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[   12.790109] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   12.790112] saa7164_downloadfirmware() BSLSize = 0x0
[   12.790115] saa7164_downloadfirmware() Reserved = 0x0
[   12.790119] saa7164_downloadfirmware() Version = 0x1661c00
[   19.552039] saa7164_downloadimage() Image downloaded, booting...
[   19.656058] saa7164_downloadimage() Image booted successfully.
[   23.108029] saa7164_downloadimage() Image downloaded, booting...
[   24.980040] saa7164_downloadimage() Image booted successfully.
[   25.028724] saa7164[0]: Hauppauge eeprom: model=151061
[   25.322606] DVB: registering new adapter (saa7164)
[   25.322616] saa7164 0000:02:00.0: DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3306A VSB/QAM Frontend)...
[   25.365164] DVB: registering new adapter (saa7164)
[   25.365188] saa7164 0000:02:00.0: DVB: registering adapter 1 frontend 0 (LG Electronics LGDT3306A VSB/QAM Frontend)...
[   25.366473] saa7164[0]: registered device video0 [mpeg]
[   25.597418] saa7164[0]: registered device video1 [mpeg]
[   25.809848] saa7164[0]: registered device vbi0 [vbi]
[   25.810028] saa7164[0]: registered device vbi1 [vbi]
jmv@myth2:~$ 
```

Nice, we're making progress. I then installed the w-scan program and simply did

```
w_scan > channels.conf
```
without any argument and the card detected automagically that I was in Canada and that the format was ATSC. I reviewed the file, noted the name and frequency of the channel I wanted to watch, and gave VLC a try (see my previous post). It worked.

I fired up MythTV-setup again, chose the ATSC tuner that was already there in the "Capture Card" page, and did it for *BOTH* tuners. I then went in "Video Source" and configured it to Antenna, again for both tuners, and finally set up the connection to both tuners, using the antenna. In that same page, there is the "Scan for channels" option. Again, I did it for both tuners, even if there is only one connected to the antenna. Then I selected "Fetch channels from listings source" (not sure it was worth something), and closed mythtv-setup. The system asked me if I wanted to start mythtv-backend and I said yes. I also said yes to "Do you want to run mythfilldatabase?"

Now, I opened the frontend. I was a bit nervous because I had been working on that for the last few days and did not have much sleep. I chose Watch TV (the real test) and it worked! I was there, watching the channel from which I want to record shows. Even on a CRT monitor, the image was crisp and smooth. I scrambled to find earphones, as my test computer does not have speakers. The sound was good and in sync with the image. Perfect!

So tonight, I decided to record the news for testing. I scheduled it and left it there because I had other things to do. When I came back, the show was already recorded but the system was still transcoding it. It's a big file (7.6 Gig for one hour) and the computer is pretty old. I waited until it finished and I was happy to see that every thing had worked well. Smooth image, no stutter, no freeze, no pixelization, all was good, even the sound. And even my 12 year old daughter told me that the image was crisper than with the other MythTV box (analog cable).

Now if i can make it work as a slave server, all will be perfect.

Hope this helps somebody,

J-M
P.S Sorry for my english, it is not my first language

---

