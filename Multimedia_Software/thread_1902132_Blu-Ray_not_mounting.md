---
title: "Blu-Ray not mounting"
date: 2011-12-30
forum: Multimedia Software
---

### Post by Chrus on 2011-12-30
Im trying to get Mythbuntu to play Blu-Ray movies, but the discs wont even mount. Running Mythbuntu 10.10.

I've got a LG CH12LS328 Blu-Ray drive. I wasnt expecting blu-ray to just work out of the box, but I was thinking they would at least mount.

Is there something I need to do to get it working?

As usual... happy to provide any further info if needed.

Thanks

---

### Post by Chrus on 2012-01-04
bump

---

### Post by BicyclerBoy on 2012-01-04
BDs mount fine on 10.04.3 with the standard up-to-date kernel.

As I understand the BD filesystem is not the problem.

Could be you have something wrong with auto-mount or gvfs..

udisks --show-info /dev/sr0
udisks --show-info /dev/sr1

Some good debugging ideas here:
[http://askubuntu.com/questions/76860/cd-dvd-drive-not-mounted-when-inserted-with-disc-of-any-kind](http://askubuntu.com/questions/76860/cd-dvd-drive-not-mounted-when-inserted-with-disc-of-any-kind)

MythTV requires 0.24+fixes & launching mythavtest from terminal
mythavtest bd://media/APOCALYPSE_NOW_DISC1/

obviously edit the disk label, use <tab><tab> to help auto complete.
Some BDs require you to navigate to different title (i.e. not title 1.)

---

### Post by rubylaser on 2012-01-05
The disk should mount for you at a minimum.  Playback is another story, but still not difficult.

I use XBMC as my playback device on Ubuntu.  For Bluray playback, I use MakeMKVs Bluray streaming capabilities to mount and auto connect to the stream like [this]("http://forum.xbmc.org/showthread.php?t=67420").  It appears that's [Myth's method]("http://www.mythtv.org/wiki/High_Definition_Disk_Formats") of reading the disks as well.

---

### Post by BicyclerBoy on 2012-01-05
You do not need to use makeMKV to play BDs (directly of the disk) in MythTV. So that is not the myth method.

But it is re-assuring to know that MakeMKV is an option..

---

### Post by Chrus on 2012-01-06
Thanks for the info BicyclerBoy and Rubylaser.

It would appear I am a bit of an idiot on this one. Looks like the disk has been mounting the whole time. Stupid me was expecting to see an icon appear on the desktop like when a dvd/cd is inserted. Checking /media and /mnt should of been my first step. *slaps forehead*

Anyway... The output from udisk and mythavtest are below. Im assuming mythavtest is meant to play the BD? All im getting is a "Please wait" message before being dumped back to command line.

Cheers

udisk --show-info /dev/sr0
```

Showing information for /org/freedesktop/UDisks/devices/sr0
  native-path:                 /sys/devices/pci0000:00/0000:00:11.0/host4/target4:0:0/4:0:0:0/block/sr0
  device:                      11:0
  device-file:                 /dev/sr0
    presentation:              /dev/sr0
    by-path:                   /dev/disk/by-path/pci-0000:00:11.0-scsi-2:0:0:0
  detected at:                 Fri 06 Jan 2012 03:40:45 PM EST
  system internal:             0
  removable:                   1
  has media:                   1 (detected at Fri 06 Jan 2012 04:02:28 PM EST)
    detects change:            1
    detection by polling:      1
    detection inhibitable:     1
    detection inhibited:       0
  is read only:                0
  is mounted:                  1
  mount paths:             /media/THE_PHANTOM_MENACE
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  size:                        49121787904
  block size:                  2048
  job underway:                no
  usage:                       filesystem
  type:                        udf
  version:                     
  uuid:                        
  label:                       THE_PHANTOM_MENACE
  optical disc:
    blank:                     0
    appendable:                0
    closed:                    1
    num tracks:                1
    num audio tracks:          0
    num sessions:              1
  drive:
    vendor:                    HL-DT-ST
    model:                     BDDVDRW CH12LS28
    revision:                  1.00
    serial:                    
    WWN:                       
    detachable:                0
    can spindown:              0
    rotational media:          Yes, unknown rate
    write-cache:               unknown
    ejectable:                 1
    adapter:                   /org/freedesktop/UDisks/adapters/0000_3a00_3a11_2e0
    ports:
      /org/freedesktop/UDisks/adapters/0000_3a00_3a11_2e0/host4
    similar devices:
    media:                     optical_bd
      compat:                  optical_bd optical_cd optical_cd_r optical_cd_rw optical_dvd optical_dvd_plus_r optical_dvd_plus_r_dl optical_dvd_plus_rw optical_dvd_r optical_dvd_ram optical_dvd_rw optical_mrw optical_mrw_w
    interface:                 scsi
    if speed:                  (unknown)
    ATA SMART:                 not available


```

mythavtest db://media/THE_PHANTOM_MENACE/
```

2012-01-06 16:17:21.557 Using runtime prefix = /usr
2012-01-06 16:17:21.558 Using configuration directory = /home/chrus/.mythtv
2012-01-06 16:17:21.559 Empty LocalHostName.
2012-01-06 16:17:21.559 Using localhost value of Mythbuntu
2012-01-06 16:17:21.569 New DB connection, total: 1
2012-01-06 16:17:21.578 Connected to database 'mythconverg' at host: localhost
2012-01-06 16:17:21.578 Closing DB connection named 'DBManager0'
2012-01-06 16:17:21.623 ScreenSaverX11Private: XScreenSaver support enabled
2012-01-06 16:17:21.625 DPMS is disabled.
2012-01-06 16:17:21.685 Primary screen: 0.
2012-01-06 16:17:21.686 Connected to database 'mythconverg' at host: localhost
2012-01-06 16:17:21.687 Using screen 0, 1360x768 at 0,0
2012-01-06 16:17:21.737 Desktop video mode: 1360x768 60.0168 Hz
2012-01-06 16:17:21.804 The NV-CONTROL X extension is not available on screen 0 of ':0.0'.
2012-01-06 16:17:21.805 max_width: 1920 max_height: 1200
2012-01-06 16:17:21.807 MythUI Image Cache size set to 20971520 bytes
2012-01-06 16:17:21.812 Primary screen: 0.
2012-01-06 16:17:21.813 Using screen 0, 1360x768 at 0,0
2012-01-06 16:17:21.815 Using theme base resolution of 1280x720
2012-01-06 16:17:21.865 AudioPulseUtil: Suspend Success
2012-01-06 16:17:21.868 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2012-01-06 16:17:21.868 JoystickMenuThread Error: Joystick disabled - Failed to read /home/chrus/.mythtv/joystickmenurc
2012-01-06 16:17:21.929 Using Frameless Window
2012-01-06 16:17:21.929 Using Full Screen Window
2012-01-06 16:17:22.255 Using the Qt painter
2012-01-06 16:17:22.435 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2012-01-06 16:17:22.446 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2012-01-06 16:17:22.457 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2012-01-06 16:17:22.458 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2012-01-06 16:17:22.566 Current MythTV Schema Version (DBSchemaVer): 1254
2012-01-06 16:17:22.566 TV: ctor -- begin
2012-01-06 16:17:22.578 TV: ctor -- end
2012-01-06 16:17:22.578 TV: Init -- begin
2012-01-06 16:17:22.580 TV: Init -- end channel groups
2012-01-06 16:17:22.598 TV: DrawUnusedRects() -- begin
2012-01-06 16:17:22.598 TV: DrawUnusedRects() -- end
2012-01-06 16:17:22.609 TV: DrawUnusedRects() -- begin
2012-01-06 16:17:22.609 TV: DrawUnusedRects() -- end
2012-01-06 16:17:22.728 TV: DrawUnusedRects() -- begin
2012-01-06 16:17:22.728 TV: DrawUnusedRects() -- end
2012-01-06 16:17:22.731 TV: Init -- end
2012-01-06 16:17:22.733 TV: StartTV() -- begin
2012-01-06 16:17:22.733 TV: ctor -- begin
2012-01-06 16:17:22.735 TV: ctor -- end
2012-01-06 16:17:22.735 TV: Init -- begin
2012-01-06 16:17:22.736 TV: Init -- end channel groups
2012-01-06 16:17:22.737 TV: DrawUnusedRects() -- begin
2012-01-06 16:17:22.738 TV: DrawUnusedRects() -- end
2012-01-06 16:17:22.738 TV: DrawUnusedRects() -- begin
2012-01-06 16:17:22.738 TV: DrawUnusedRects() -- end
2012-01-06 16:17:22.738 TV: DrawUnusedRects() -- begin
2012-01-06 16:17:22.738 TV: DrawUnusedRects() -- end
2012-01-06 16:17:22.738 TV: DrawUnusedRects() -- begin
2012-01-06 16:17:22.738 TV: DrawUnusedRects() -- end
2012-01-06 16:17:22.794 TV: DrawUnusedRects() -- begin
2012-01-06 16:17:22.794 TV: DrawUnusedRects() -- end
2012-01-06 16:17:22.794 TV: DrawUnusedRects() -- begin
2012-01-06 16:17:22.794 TV: DrawUnusedRects() -- end
2012-01-06 16:17:22.812 TV: Init -- end
2012-01-06 16:17:22.820 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2012-01-06 16:17:22.821 Using protocol version 23056
2012-01-06 16:17:22.829 TV: tv->Playback() -- begin
2012-01-06 16:17:22.834 TV: tv->Playback() -- end
2012-01-06 16:17:22.834 TV: StartTV -- process events begin
2012-01-06 16:17:22.856 TV: HandleStateChange(0) -- begin
2012-01-06 16:17:22.856 TV: Attempting to change from None to WatchingVideo
2012-01-06 16:17:22.857 RingBuf(/home/chrus/db://media/THE_PHANTOM_MENACE/): OpenFile(/home/chrus/db://media/THE_PHANTOM_MENACE/, 12)
2012-01-06 16:17:29.358 RingBuf(/home/chrus/db://media/THE_PHANTOM_MENACE/): Could not open /home/chrus/db://media/THE_PHANTOM_MENACE/.
2012-01-06 16:17:29.359 RingBuf(/home/chrus/db://media/THE_PHANTOM_MENACE/): CalcReadAheadThresh(0 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2012-01-06 16:17:29.361 TV: HandleStateChange(0) -- end
2012-01-06 16:17:29.362 TV: StartTV -- process events end
2012-01-06 16:17:29.362 TV: StartTV -- process events 2 begin
2012-01-06 16:17:29.370 TV: DrawUnusedRects() -- begin
2012-01-06 16:17:29.370 TV: DrawUnusedRects() -- end
2012-01-06 16:17:29.370 TV: DrawUnusedRects() -- begin
2012-01-06 16:17:29.370 TV: DrawUnusedRects() -- end
2012-01-06 16:17:29.370 TV: DrawUnusedRects() -- begin
2012-01-06 16:17:29.370 TV: DrawUnusedRects() -- end
2012-01-06 16:17:29.370 TV: DrawUnusedRects() -- begin
2012-01-06 16:17:29.371 TV: DrawUnusedRects() -- end
2012-01-06 16:17:29.373 TV: StartTV -- process events 2 end
2012-01-06 16:17:29.376 TV::~TV() -- begin
2012-01-06 16:17:29.427 TV::~TV() -- lock
2012-01-06 16:17:29.429 TV::~TV() -- end
2012-01-06 16:17:29.430 TV: StartTV -- end
2012-01-06 16:17:29.435 AudioPulseUtil: Resume Success

```

---

### Post by BicyclerBoy on 2012-01-06
The cmd has "...bd://media/.." not "..db://.."

The 10.04.3 gnome desktop does mount BD & displays an icon.
Mythbuntu uses Xfce so it may not.

For the purpose of watching BD disks you own & have the right to watch..
So no ripping/dumping/streaming...
For direct BD playback:
- have to be using MythTV 0.24+fixes (i.e. close to trunk)
- compiled/installed libAACS
- invoke with mythavtest (terminal)
- have BD disk VUK etc in KEYDB.cfg file (dumpHD helps here)

doom9 is a great resource.
Note the 2 different formats of KEYDB.cfg file.
MythTV has its own copy..& I just copy over the VUKs as required..

For the purpose of watching BD disks you own & have the right to watch without ripping/dumping etc ..
So the process is:
1. Get new BD
2. in tray run ./dumphd.sh
3. disk key VUK in existing (aacskeys) key database ? yes/no
4. no: enter disk name/label (gets saved to KEYDB.cfg)
5. exit dumpHD..
6. copy over (& edit format) key entry into mythtv copy of KEYDB.cfg 
7. invoke mythavtest...

Obviously you can do steps 1.-6. quite efficiently for a number of disks..

---

