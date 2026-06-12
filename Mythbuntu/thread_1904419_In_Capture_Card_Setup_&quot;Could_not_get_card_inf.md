---
title: "In Capture Card Setup &quot;Could not get card info&quot; error"
date: 2012-01-04
forum: Mythbuntu
---

### Post by gunsmoke on 2012-01-04
Hello, 

**My hardware info:**
ASUS M3N78-VM
2GB RAM
AMD Athlon II x3 455
Happauge HVR 2200 DVB-T capture card.

**OS:**
Ubuntu 11.10
Kernel 3.0.0-14-generic-pae
GNOME 3.2.1
Mythbuntu set for updates on 0.24.x

**Background:**
I had a system working on 10.04 for 6-7 month's. I recently upgraded from 10.04 to 11.10, and have since failed to get myth to recognize my HVR2200.

In my hunt to get things working again I have updated to the new capture card firmware:

NXP7164-2010-03-10.1.fw

from the instructions made by LowSky here; [http://ubuntuforums.org/showthread.php?t=942403]("http://ubuntuforums.org/showthread.php?t=942403") and installed the latest v4l drivers from here; [http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers]("http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers"). Also installed latest FFmpeg and x264 from user FakeOutdoorsman here; [http://ubuntuforums.org/showthread.php?t=786095]("http://ubuntuforums.org/showthread.php?t=786095").


On the Permission/user side I have tried the following:

```
sudo chmod 755 /dev/dvb
```

```
sudo useradd -G video mythtv
```

```
sudo chown -R myth:video /dev/dvb
```

```
sudo chown -R root:mythtv /dev/dvb
```

```
sudo chown -R myth:myth /dev/dvb
```

```
 sudo adduser mythtv video
```

```
sudo chmod a+rwx /dev/dvb
```

```
sudo chown -R mythtv:mythtv /dev/dvb
```



**Problem:**
Myth is not able to install/use the capture card. Following error is displayed in the "Capture Card Setup" dialog in the master backend configuration:

> Could not get card info for card /dev/dvb/adapter0/frontend0 Subtype: Unknown error


**What's working:**
However, I am able to use scan and make a channel.conf:

```
scan /usr/share/dvb/dvb-t/no-Stavanger_Bokn | tee channels.conf

```

And also play all my media on the backend, in my frontend; Watch Recordings/Videos/DVD, Play Music etc.



**Here is some outputs:**

```
myth@M3N78:~$ dmesg|grep saa7164
[   13.566383] saa7164 driver loaded
[   13.566436] saa7164 0000:04:00.0: PCI INT A -> Link[LN2A] -> GSI 18 (level, low) -> IRQ 18
[   13.567125] CORE saa7164[0]: subsystem: 0070:8940, board: Hauppauge WinTV-HVR2200 [card=4,insmod option]
[   13.567128] saa7164[0]/0: found at 0000:04:00.0, rev: 129, irq: 18, latency: 0, mmio: 0xfe800000
[   13.567134] saa7164 0000:04:00.0: setting latency timer to 64
[   13.724746] saa7164_downloadfirmware() no first image
[   13.724755] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   14.126788] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   14.126790] saa7164_downloadfirmware() firmware loaded.
[   14.126797] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[   14.126803] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   14.126804] saa7164_downloadfirmware() BSLSize = 0x0
[   14.126805] saa7164_downloadfirmware() Reserved = 0x0
[   14.126806] saa7164_downloadfirmware() Version = 0x1661c00
[   20.988038] saa7164_downloadimage() Image downloaded, booting...
[   21.092030] saa7164_downloadimage() Image booted successfully.
[   23.212034] saa7164_downloadimage() Image downloaded, booting...
[   24.876033] saa7164_downloadimage() Image booted successfully.
[   24.920487] saa7164[0]: Hauppauge eeprom: model=89619
[   25.229346] DVB: registering new adapter (saa7164)
[   27.862040] DVB: registering new adapter (saa7164)
[   27.862348] saa7164[0]: registered device video0 [mpeg]
[   28.091793] saa7164[0]: registered device video1 [mpeg]
[   28.302699] saa7164[0]: registered device vbi0 [vbi]
[   28.302719] saa7164[0]: registered device vbi1 [vbi]

```

```
myth@M3N78:~$ ls /dev/dvb/ -o
totalt 0
drwxr-xr-x 2 root 120 2012-01-04 21:02 adapter0
drwxr-xr-x 2 root 120 2012-01-04 21:02 adapter1
```

```
myth@M3N78:~$ ls /dev/vi* -l
crw-rw----+ 1 root video 81, 0 2012-01-04 21:02 /dev/video0
crw-rw----+ 1 root video 81, 1 2012-01-04 21:02 /dev/video1

```

```
myth@M3N78:~$ sudo cat /etc/group | grep video
[sudo] password for myth: 
video:x:44:mythtv,myth

```

```
myth@M3N78:~$ ls -l /dev/dvb/adapter*
/dev/dvb/adapter0:
totalt 0
crw-rw----+ 1 root video 212, 1 2012-01-04 21:02 demux0
crw-rw----+ 1 root video 212, 2 2012-01-04 21:02 dvr0
crw-rw----+ 1 root video 212, 0 2012-01-04 21:02 frontend0
crw-rw----+ 1 root video 212, 3 2012-01-04 21:02 net0

/dev/dvb/adapter1:
totalt 0
crw-rw----+ 1 root video 212, 5 2012-01-04 21:02 demux0
crw-rw----+ 1 root video 212, 6 2012-01-04 21:02 dvr0
crw-rw----+ 1 root video 212, 4 2012-01-04 21:02 frontend0
crw-rw----+ 1 root video 212, 7 2012-01-04 21:02 net0

```

Log:
```
myth@M3N78:~$ tail -f /var/log/mythtv/mythfrontend.log
2012-01-04 21:59:49.755 OSD: Scaling factors: 0.55x0.6
2012-01-04 21:59:49.870 OSD: Base theme size: 1280x720
2012-01-04 21:59:49.870 OSD: Scaling factors: 0.55x0.6
2012-01-04 21:59:49.879 Player(0): Video timing method: USleep with busy wait
2012-01-04 21:59:49.880 TV: Changing from None to WatchingVideo
2012-01-04 21:59:51.959 ScreenSaverX11Private: DPMS Deactivated 1
2012-01-04 21:59:51.994 VideoOutput: Created YV12 OSD.
2012-01-04 22:00:09.190 TV: Attempting to change from WatchingVideo to None
2012-01-04 22:00:09.290 TV: Changing from WatchingVideo to None
2012-01-04 22:00:09.291 ScreenSaverX11Private: DPMS Reactivated 1

```



Please if anyone have some tips on how to make this work again, do tell me. In advance thanks):P

---

### Post by gunsmoke on 2012-01-05
Somehow I got it working again. :D

After updating the MPlayer iaw the tutor from andrew.46 here: [http://ubuntuforums.org/showthread.php?t=1542240&highlight=mplayer]("http://ubuntuforums.org/showthread.php?t=1542240&highlight=mplayer"), I restarted and deleted all cards and video sources in the backend setup. Then I did a new setup, and just ignored the "Could not get card info" error, and used the channels.conf file from the scan command, and volla!! it's working again:KS


Anyone who will explaine way I get the "Could not get card info" error?

---

