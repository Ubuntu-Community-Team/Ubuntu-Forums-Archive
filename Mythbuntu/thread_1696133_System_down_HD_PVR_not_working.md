---
title: "System down HD PVR not working"
date: 2011-02-26
forum: Mythbuntu
---

### Post by phroman on 2011-02-26
Hello everybody, I unplugged my entire home theater system to move it, plugged it all back in, and my Hauppauge HD PVR is no longer working.  I cannot watch live TV, I cannot record any shows.  I've generally had a pretty hard time using this unit.  It's sort of been like, it might work, it might not.  The entire system worked fine before I unplugged everything.


Linux mythserver 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686 GNU/Linux
Mythfrontend version: fixes/0.24 (v0.24-190-gf169dd9)

My HD PVR unit version is 4903 and that matches my driver as shown in modprobe and lsusb below:

Here's modinfo:

```
user@mythserver:~/Desktop$ modinfo hdpvr
filename:       /lib/modules/2.6.35-25-generic/kernel/drivers/media/video/hdpvr/hdpvr.ko
description:    Hauppauge HD PVR driver
author:         Janne Grunau
license:        GPL
srcversion:     B50617E570904096DFD0CFF
alias:          usb:v2040p4982d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2040p4902d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2040p4901d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2040p4900d*dc*dsc*dp*ic*isc*ip*
depends:        videodev,v4l2-common
vermagic:       2.6.35-25-generic SMP mod_unload modversions 686 
parm:           video_nr:video device number (-1=Auto) (array of int)
parm:           hdpvr_debug:enable debugging output (int)
parm:           default_video_input:default video input: 0=Component / 1=S-Video / 2=Composite (uint)
parm:           default_audio_input:default audio input: 0=RCA back / 1=RCA front / 2=S/PDIF (uint)
parm:           boost_audio:boost the audio signal (bool)

```
Here's lsusb:

```
user@mythserver:~/Desktop$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 007 Device 002: ID 0c16:0001 Gyration, Inc. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0bc7:0008 X10 Wireless Technology, Inc. Wireless Transceiver (ACPI-compliant)
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 2040:4902 Hauppauge HD PVR
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
user@mythserver:~/Desktop$ 
```

user@mythserver:~/Desktop$ locate cx88-dvb.ko |grep `uname -r`
/lib/modules/2.6.35-25-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko

I updated the firmware from Hauppauge's website to HD PVR driver version 1.5.7.0

I can test the unit from the command line with:
cat /dev/video0 > test.ts
It creates a video file, so the unit seems to be in working order.  Power cycled the unit after that.

Here is my dmesg output:

```
user@mythserver:~/Desktop$ dmesg | grep pvr
[   15.092397] hdpvr 2-2:1.0: untested firmware version 0x15, the driver might not work
[   15.395558] hdpvr 2-2:1.0: device now attached to video0
[   15.395571] usbcore: registered new interface driver hdpvr
user@mythserver:~/Desktop$ 
```

Myth Backend Setup > Capture Cards:  My HD PVR is recognized fine.
Myth Backend Setup > Video Sources:  Shows one thing that is new.  I input my schedules direct info and without hitting the Retrieve Lineup button, the Data Direct Lineup: field shows: DITV803:-  After I hit the Retrieve Lineup button, the Data Direct Lineup: field shows:: DIRECTV Los Angeles-Satellite-Cable-myzipcode-DITV803:-

It will change back upon re-running Mythbackend.  That's probably not good.

Myth Backend Setup > Connect Source To Input: My channel change script is listed and executable, I cannot hit the Scan for Channels button, it's grayed out, but I can hit the Fetch channels from listings source button.  After doing that I set the Starting Channel to 2, a know working channel.  

I ran mythfilldatabase before attempting to go into 
Myth Backend Setup > Channel Editor.  

When I do get to Myth Backend Setup > Channel Editor: the Channels Scan button is grayed out.  Most of the times that I've seen this it's been when you put in the wrong type of capture card, or assign an incorrect/non-existent Starting Channel.  Seeing as my card was probed correctly and I know channel 2 is a working channel, I don't think that's it.  

There is a ringbuffer error which you can see in the logs below:

Here's my backend log:

```
2011-02-27 00:33:20.292 mythbackend version: fixes/0.24 [v0.24-190-gf169dd9] www.mythtv.org
2011-02-27 00:33:20.656 Using runtime prefix = /usr
2011-02-27 00:33:20.981 Using configuration directory = /home/mythtv/.mythtv
2011-02-27 00:33:21.552 Empty LocalHostName.
2011-02-27 00:33:21.763 Using localhost value of mythserver
2011-02-27 00:33:21.945 New DB connection, total: 1
2011-02-27 00:33:22.083 Connected to database 'mythconverg' at host: 127.0.0.1
2011-02-27 00:33:22.175 Closing DB connection named 'DBManager0'
2011-02-27 00:33:22.239 Connected to database 'mythconverg' at host: 127.0.0.1
2011-02-27 00:33:22.309 Current locale EN_US
2011-02-27 00:33:22.368 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-02-27 00:33:22.508 Current MythTV Schema Version (DBSchemaVer): 1264
2011-02-27 00:33:22.656 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-02-27 00:33:22.997 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2011-02-27 00:33:23.323 MythBackend: Starting up as the master server.
2011-02-27 00:33:23.786 New DB connection, total: 2
2011-02-27 00:33:24.119 Connected to database 'mythconverg' at host: 127.0.0.1
2011-02-27 00:33:24.794 New DB connection, total: 3
2011-02-27 00:33:25.089 Connected to database 'mythconverg' at host: 127.0.0.1
Usage: /usr/local/bin/directv.pl command ...
Commands:
  box_type RCA|RCA_OLD|D10-100|D10-200|D11|H20  - select set top box type
  delay number    - wait for number seconds. Floating point is valid 
  key string      - send remote key string.  See source for supported keys
  last_param      - execute last parameter on command line at current location
  number{-number} - change to specified channel-subchannel
  off             - turn box off
  on              - turn box on
  reboot          - hard reboot (reset)
  port string     - select port to send commands on, currently /dev/ttyS0
                    should be first on command line
  setup_channel number - send on, channel change command and OSD off command
                         retries if channel change not sucessful
  setup_channel_sd_hd number - setup_channel for SD only service with HD box
                         Use when you need channel up see SD channel when HD exists
  version         - display program version

  baudrate number      - select serial port baudrate, currently 115200
  channel_change_type key|command - select channel change method
  get_channel          - print current channel
  get_datetime         - print date and time
  get_signal           - print signal strength
  hide                 - hide text, will also prevent info button from working
  show                 - show text, will also allow info button to work
  retries number       - set maximum number of retries on error
  set_system_datetime  - set PC clock from box.  ntp is more accurate
  text string          - display string on screen, "" to clear
  verbose|quiet        - select how much information printed

Mythtv command for normal RCA box: directv.pl setup_channel
Complex Mythtv command for D10-200 box doing same as setup_channel:
   directv.pl box_type D10-200 on last_param delay .2 key exit
Mythtv adds channel number at end of command

Command /dev/ttyS0 not found
2011-02-27 00:33:30.103 New DB scheduler connection
2011-02-27 00:33:30.146 Connected to database 'mythconverg' at host: 127.0.0.1
2011-02-27 00:33:30.214 Main::Registering HttpStatus Extension
2011-02-27 00:33:30.321 Enabled verbose msgs:  important general
2011-02-27 00:33:30.405 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-02-27 00:33:33.260 Reschedule requested for id -1.
2011-02-27 00:33:34.059 Scheduled 166 items in 0.8 = 0.18 match + 0.62 place
2011-02-27 00:33:34.102 Seem to be woken up by USER
2011-02-27 00:33:35.005 MainServer::ANN Monitor
2011-02-27 00:33:35.053 adding: mythserver as a client (events: 0)
2011-02-27 00:33:37.913 MainServer::ANN Monitor
2011-02-27 00:33:38.022 adding: mythserver as a client (events: 0)
2011-02-27 00:33:38.064 MainServer::ANN Monitor
2011-02-27 00:33:38.105 adding: mythserver as a client (events: 1)
2011-02-27 00:33:38.165 MainServer::ANN Playback
2011-02-27 00:33:38.206 adding: mythserver as a client (events: 0)
2011-02-27 00:33:38.251 TVRec(1): Changing from None to WatchingLiveTV
2011-02-27 00:33:38.292 TVRec(1): HW Tuner: 1->1
2011-02-27 00:33:38.465 LoadFromScheduler(): Error, called from backend.
2011-02-27 00:33:38.466 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
Usage: /usr/local/bin/directv.pl command ...
Commands:
  box_type RCA|RCA_OLD|D10-100|D10-200|D11|H20  - select set top box type
  delay number    - wait for number seconds. Floating point is valid 
  key string      - send remote key string.  See source for supported keys
  last_param      - execute last parameter on command line at current location
  number{-number} - change to specified channel-subchannel
  off             - turn box off
  on              - turn box on
  reboot          - hard reboot (reset)
  port string     - select port to send commands on, currently /dev/ttyS0
                    should be first on command line
  setup_channel number - send on, channel change command and OSD off command
                         retries if channel change not sucessful
  setup_channel_sd_hd number - setup_channel for SD only service with HD box
                         Use when you need channel up see SD channel when HD exists
  version         - display program version

  baudrate number      - select serial port baudrate, currently 115200
  channel_change_type key|command - select channel change method
  get_channel          - print current channel
  get_datetime         - print date and time
  get_signal           - print signal strength
  hide                 - hide text, will also prevent info button from working
  show                 - show text, will also allow info button to work
  retries number       - set maximum number of retries on error
  set_system_datetime  - set PC clock from box.  ntp is more accurate
  text string          - display string on screen, "" to clear
  verbose|quiet        - select how much information printed

Mythtv command for normal RCA box: directv.pl setup_channel
Complex Mythtv command for D10-200 box doing same as setup_channel:
   directv.pl box_type D10-200 on last_param delay .2 key exit
Mythtv adds channel number at end of command

Command /dev/ttyS0 not found
2011-02-27 00:33:40.621 SignalMonitor: channel change failed
2011-02-27 00:33:40.707 SignalMonitor: channel change failed
2011-02-27 00:33:40.799 SignalMonitor: channel change failed
2011-02-27 00:33:40.891 SignalMonitor: channel change failed
2011-02-27 00:33:40.983 SignalMonitor: channel change failed
2011-02-27 00:33:41.075 SignalMonitor: channel change failed
2011-02-27 00:33:49.750 TVRec(1): Changing from WatchingLiveTV to None
2011-02-27 00:34:50.216 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
```


Here's my frontend log: 

```
Starting mythfrontend.real..
2011-02-27 00:33:23.454 mythfrontend version: fixes/0.24 [v0.24-190-gf169dd9] www.mythtv.org
2011-02-27 00:33:23.454 Using runtime prefix = /usr
2011-02-27 00:33:23.454 Using configuration directory = /home/joe/.mythtv
2011-02-27 00:33:23.454 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-02-27 00:33:24.059 Empty LocalHostName.
2011-02-27 00:33:24.059 Using localhost value of mythserver
2011-02-27 00:33:24.066 New DB connection, total: 1
2011-02-27 00:33:24.068 Connected to database 'mythconverg' at host: 127.0.0.1
2011-02-27 00:33:24.071 Closing DB connection named 'DBManager0'
2011-02-27 00:33:24.072 Connected to database 'mythconverg' at host: 127.0.0.1
2011-02-27 00:33:24.072 Current locale EN_US
2011-02-27 00:33:24.072 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-02-27 00:33:24.278 ScreenSaverX11Private: XScreenSaver support enabled
2011-02-27 00:33:24.419 DPMS is disabled.
2011-02-27 00:33:24.431 Desktop video mode: 1920x1080 60.000 Hz
2011-02-27 00:33:24.957 Enabled verbose msgs:  important general
2011-02-27 00:33:24.959 Loading en_us translation for module mythfrontend
2011-02-27 00:33:25.241 LIRC: Successfully initialized '/dev/lircd' using '/home/joe/.mythtv/lircrc' config
2011-02-27 00:33:25.241 JoystickMenuThread: Joystick disabled - Failed to read /home/joe/.mythtv/joystickmenurc
2011-02-27 00:33:25.314 Using Frameless Window
2011-02-27 00:33:25.470 Using Full Screen Window
2011-02-27 00:33:25.807 Using the Qt painter
2011-02-27 00:33:26.031 New DB connection, total: 2
2011-02-27 00:33:26.163 New DB connection, total: 3
2011-02-27 00:33:26.163 Current MythTV Schema Version (DBSchemaVer): 1264
2011-02-27 00:33:26.170 Connected to database 'mythconverg' at host: 127.0.0.1
2011-02-27 00:33:26.171 Connected to database 'mythconverg' at host: 127.0.0.1
2011-02-27 00:33:28.883 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-02-27 00:33:28.883 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-02-27 00:33:28.894 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-02-27 00:33:28.894 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-02-27 00:33:29.119 Registering Internal as a media playback plugin.
2011-02-27 00:33:29.138 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-27 00:33:29.138 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-27 00:33:29.139 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-27 00:33:29.139 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-02-27 00:33:29.139 Loading en_us translation for module mythgallery
2011-02-27 00:33:29.159 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-02-27 00:33:29.181 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-02-27 00:33:29.186 Loading en_us translation for module mythmusic
2011-02-27 00:33:29.193 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-02-27 00:33:29.235 Loading en_us translation for module mythvideo
2011-02-27 00:33:29.263 Loading en_us translation for module mythweather
2011-02-27 00:33:29.706 Found mainmenu.xml for theme 'Mythbuntu'
2011-02-27 00:33:29.834 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-02-27 00:33:29.835 Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

2011-02-27 00:33:29.835 Unable to determine master backend time zone settings.  If those settings differ from local settings, some functionality will fail.
2011-02-27 00:33:37.912 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-02-27 00:33:37.913 Using protocol version 63
2011-02-27 00:33:38.165 TV: Attempting to change from None to WatchingLiveTV
2011-02-27 00:33:38.165 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-02-27 00:33:38.165 Using protocol version 63
2011-02-27 00:33:38.251 Spawning LiveTV Recorder -- begin
2011-02-27 00:33:38.766 Spawning LiveTV Recorder -- end
2011-02-27 00:33:38.769 We have a playbackURL(/var/lib/mythtv/livetv/1202_20110227003338.mpg) & cardtype(DUMMY)
2011-02-27 00:33:38.769 We have a RingBuffer
2011-02-27 00:33:39.008 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2011-02-27 00:33:39.033 OSD: Base theme size: 1280x720
2011-02-27 00:33:39.033 OSD: Scaling factors: 0.5625x0.8
2011-02-27 00:33:39.127 OSD: Base theme size: 1280x720
2011-02-27 00:33:39.127 OSD: Scaling factors: 0.5625x0.8
2011-02-27 00:33:39.130 Player(0): Video timing method: USleep with busy wait
2011-02-27 00:33:39.130 TV: Changing from None to WatchingLiveTV
2011-02-27 00:33:39.130 TV: State is LiveTV & mctx == ctx
2011-02-27 00:33:39.133 TV: UpdateOSDInput done
2011-02-27 00:33:39.133 TV: UpdateLCD done
2011-02-27 00:33:39.133 TV: ITVRestart done
2011-02-27 00:33:39.268 VideoOutput: Created YV12 OSD.
2011-02-27 00:33:48.645 OSD: Base theme size: 1280x720
2011-02-27 00:33:48.645 OSD: Scaling factors: 0.5625x0.8
2011-02-27 00:33:48.651 MythUIHelper, Error: LoadScaleImage(uparrow_alt.png)Unable to find image file
2011-02-27 00:33:48.651 MythUIHelper, Error: LoadScaleImage(downarrow_alt.png)Unable to find image file
2011-02-27 00:33:49.702 TV: OSDDialogEvent: result 0 text Exit Live TV action DIALOG_VIDEOEXIT_JUSTEXIT_0
2011-02-27 00:33:49.745 TV: Attempting to change from WatchingLiveTV to None
2011-02-27 00:33:49.799 TV: Changing from WatchingLiveTV to None
2011-02-27 00:33:51.499 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit
```


This renders my whole system dead, any help on this is surely appreciated.  Thanks!

---

### Post by phroman on 2011-02-27
UPDATE:  Looks like a channel change script issue.  I get the feeling anything at all wrong with the channel change scripts causes live tv not to work.  I use a serial/usb cable to control my set top box, a Direct TV H20 receiver only.  The script is owner:mythtv group:mythtv others:read-only Executable.

 If I set the channel change script in Mythbuntu > Backend Setup > Input Connections to: /usr/true, I can watch live tv.  

In mythbackend.log, I got an error "could not find device /dev/ttyS0  

It seems like a syntax error in how I'm entering the channel change script on the line in the backend.  I've always had it as:
/usr/local/bin/directv.pl /dev/ttyS0 box_type=H20

I get different errors in mythbackendlog, depending on what I place first on the line.

Two changes I made to the channel change script itself were setting the baud rate to 115200 for my receiver, and setting the serial port to /dev/ttyS0. 

Looking at the errors in the backend log, I can't tell if I'm supposed to enter all of those parameters/commands like the box_type, etc..  Or which ones are mandatory or what.


Here's a snippet:

```
Usage: /usr/local/bin/directv.pl command ...
Commands:
  box_type RCA|RCA_OLD|D10-100|D10-200|D11|H20  - select set top box type
  delay number    - wait for number seconds. Floating point is valid 
  key string      - send remote key string.  See source for supported keys
  last_param      - execute last parameter on command line at current location
  number{-number} - change to specified channel-subchannel
  off             - turn box off
  on              - turn box on
  reboot          - hard reboot (reset)
  port string     - select port to send commands on, currently /dev/ttyS0
                    should be first on command line
  setup_channel number - send on, channel change command and OSD off command
                         retries if channel change not sucessful
  setup_channel_sd_hd number - setup_channel for SD only service with HD box
                         Use when you need channel up see SD channel when HD exists
  version         - display program version

  baudrate number      - select serial port baudrate, currently 115200
  channel_change_type key|command - select channel change method
  get_channel          - print current channel
  get_datetime         - print date and time
  get_signal           - print signal strength
  hide                 - hide text, will also prevent info button from working
  show                 - show text, will also allow info button to work
  retries number       - set maximum number of retries on error
  set_system_datetime  - set PC clock from box.  ntp is more accurate
  text string          - display string on screen, "" to clear
  verbose|quiet        - select how much information printed

Mythtv command for normal RCA box: directv.pl setup_channel
Complex Mythtv command for D10-200 box doing same as setup_channel:
   directv.pl box_type D10-200 on last_param delay .2 key exit
Mythtv adds channel number at end of command

Command /dev/ttyS0 not found
```


user@mythserver:~/Desktop$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[    0.265466] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.265780] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
user@mythserver:~/Desktop$ 

Can't think of what else to do.

---

### Post by tgm4883 on 2011-02-27
Stick /usr/true in the backend setup, fire up live tv, ssh into the box from another machine then try your channel change command you were using with a valid channel tacked onto the end. See if it successfully changes the channel or not. If not, then it isn't a mythtv issue, as your command may be wrong. Judging by the error message, sounds like it may not be at /dev/ttyS0 anymore

---

### Post by phroman on 2011-02-27
Hi tgm4883, thanks for replying.

I resized the frontend to a small window so I could see it on my tv/desktop, put /bin/true in the backend and called the script from the command line.  It responded with: Error excessive retries

It does tune to live tv though with /bin/true.

 Here's the backend log:

```

2011-02-27 10:05:29.937 mythbackend version: fixes/0.24 [v0.24-190-gf169dd9] www.mythtv.org
2011-02-27 10:05:30.021 Using runtime prefix = /usr
2011-02-27 10:05:30.071 Using configuration directory = /home/mythtv/.mythtv
2011-02-27 10:05:30.113 Empty LocalHostName.
2011-02-27 10:05:30.155 Using localhost value of mythserver
2011-02-27 10:05:30.203 New DB connection, total: 1
2011-02-27 10:05:30.249 Connected to database 'mythconverg' at host: 127.0.0.1
2011-02-27 10:05:30.292 Closing DB connection named 'DBManager0'
2011-02-27 10:05:30.331 Connected to database 'mythconverg' at host: 127.0.0.1
2011-02-27 10:05:30.373 Current locale EN_US
2011-02-27 10:05:30.415 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-02-27 10:05:30.460 Current MythTV Schema Version (DBSchemaVer): 1264
2011-02-27 10:05:30.501 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-02-27 10:05:30.543 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2011-02-27 10:05:30.582 MythBackend: Starting up as the master server.
2011-02-27 10:05:30.628 New DB connection, total: 2
2011-02-27 10:05:30.674 Connected to database 'mythconverg' at host: 127.0.0.1
2011-02-27 10:05:30.717 New DB connection, total: 3
2011-02-27 10:05:30.758 Connected to database 'mythconverg' at host: 127.0.0.1
2011-02-27 10:05:31.200 New DB scheduler connection
2011-02-27 10:05:31.241 Connected to database 'mythconverg' at host: 127.0.0.1
2011-02-27 10:05:31.284 Main::Registering HttpStatus Extension
2011-02-27 10:05:31.325 Enabled verbose msgs:  important general
2011-02-27 10:05:31.378 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-02-27 10:05:34.285 Reschedule requested for id -1.
2011-02-27 10:05:34.544 Scheduled 174 items in 0.3 = 0.05 match + 0.21 place
2011-02-27 10:05:34.596 Seem to be woken up by USER
2011-02-27 10:05:59.838 MainServer::ANN Monitor
2011-02-27 10:05:59.895 adding: mythserver as a client (events: 0)
2011-02-27 10:05:59.938 MainServer::ANN Monitor
2011-02-27 10:05:59.979 adding: mythserver as a client (events: 1)
2011-02-27 10:06:51.286 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-02-27 10:07:05.457 MainServer::ANN Playback
2011-02-27 10:07:05.490 adding: mythserver as a client (events: 0)
2011-02-27 10:07:05.536 TVRec(1): Changing from None to WatchingLiveTV
2011-02-27 10:07:05.576 TVRec(1): HW Tuner: 1->1
2011-02-27 10:07:05.753 LoadFromScheduler(): Error, called from backend.
2011-02-27 10:07:05.754 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2011-02-27 10:07:12.091 Finished recording Fareed Zakaria GPS: channel 1202
2011-02-27 10:07:12.155 LoadFromScheduler(): Error, called from backend.
2011-02-27 10:07:12.156 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2011-02-27 10:07:12.209 Finished recording Fareed Zakaria GPS: channel 1202
2011-02-27 10:07:14.553 RecBase(1:/dev/video0): GetKeyframePositions(1,9223372036854775807,#0) out of 1
2011-02-27 10:07:14.702 RecBase(1:/dev/video0): GetKeyframePositions(1,9223372036854775807,#0) out of 1
2011-02-27 10:08:51.413 Expiring 0 MB for 1202 at 2011-02-27T10:07:05 => "Fareed Zakaria GPS"

```

Frontendlog with all sorts of crazy errors..

```

Starting mythfrontend.real..
2011-02-27 10:05:58.167 mythfrontend version: fixes/0.24 [v0.24-190-gf169dd9] www.mythtv.org
2011-02-27 10:05:58.167 Using runtime prefix = /usr
2011-02-27 10:05:58.167 Using configuration directory = /home/joe/.mythtv
2011-02-27 10:05:58.168 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-02-27 10:05:58.841 Empty LocalHostName.
2011-02-27 10:05:58.841 Using localhost value of mythserver
2011-02-27 10:05:58.850 New DB connection, total: 1
2011-02-27 10:05:58.852 Connected to database 'mythconverg' at host: 127.0.0.1
2011-02-27 10:05:58.856 Closing DB connection named 'DBManager0'
2011-02-27 10:05:58.856 Connected to database 'mythconverg' at host: 127.0.0.1
2011-02-27 10:05:58.857 Current locale EN_US
2011-02-27 10:05:58.857 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-02-27 10:05:59.061 ScreenSaverX11Private: XScreenSaver support enabled
2011-02-27 10:05:59.062 DPMS is disabled.
2011-02-27 10:05:59.072 Desktop video mode: 1920x1080 60.000 Hz
2011-02-27 10:05:59.082 Enabled verbose msgs:  important general
2011-02-27 10:05:59.085 Loading en_us translation for module mythfrontend
2011-02-27 10:05:59.090 LIRC: Successfully initialized '/dev/lircd' using '/home/joe/.mythtv/lircrc' config
2011-02-27 10:05:59.090 JoystickMenuThread: Joystick disabled - Failed to read /home/joe/.mythtv/joystickmenurc
2011-02-27 10:05:59.210 Using the Qt painter
2011-02-27 10:05:59.303 New DB connection, total: 2
2011-02-27 10:05:59.303 Connected to database 'mythconverg' at host: 127.0.0.1
2011-02-27 10:05:59.304 Current MythTV Schema Version (DBSchemaVer): 1264
2011-02-27 10:05:59.365 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-02-27 10:05:59.365 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-02-27 10:05:59.367 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-02-27 10:05:59.367 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-02-27 10:05:59.574 Registering Internal as a media playback plugin.
2011-02-27 10:05:59.600 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-27 10:05:59.600 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-27 10:05:59.600 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-27 10:05:59.601 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-02-27 10:05:59.601 Loading en_us translation for module mythgallery
2011-02-27 10:05:59.626 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-02-27 10:05:59.649 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-02-27 10:05:59.653 Loading en_us translation for module mythmusic
2011-02-27 10:05:59.664 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-02-27 10:05:59.677 Loading en_us translation for module mythvideo
2011-02-27 10:05:59.683 Loading en_us translation for module mythweather
2011-02-27 10:05:59.781 Found mainmenu.xml for theme 'Mythbuntu'
2011-02-27 10:05:59.837 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-02-27 10:05:59.838 Using protocol version 63
2011-02-27 10:07:05.456 TV: Attempting to change from None to WatchingLiveTV
2011-02-27 10:07:05.456 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-02-27 10:07:05.457 Using protocol version 63
2011-02-27 10:07:05.536 Spawning LiveTV Recorder -- begin
2011-02-27 10:07:05.847 Spawning LiveTV Recorder -- end
2011-02-27 10:07:05.850 We have a playbackURL(/var/lib/mythtv/livetv/1202_20110227100705.mpg) & cardtype(DUMMY)
2011-02-27 10:07:05.850 We have a RingBuffer
2011-02-27 10:07:05.928 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2011-02-27 10:07:05.957 OSD: Base theme size: 1280x720
2011-02-27 10:07:05.957 OSD: Scaling factors: 0.5625x0.8
2011-02-27 10:07:05.982 OSD: Base theme size: 1280x720
2011-02-27 10:07:05.982 OSD: Scaling factors: 0.5625x0.8
2011-02-27 10:07:05.985 Player(0): Video timing method: USleep with busy wait
2011-02-27 10:07:05.985 TV: Changing from None to WatchingLiveTV
2011-02-27 10:07:05.985 TV: State is LiveTV & mctx == ctx
2011-02-27 10:07:05.988 TV: UpdateOSDInput done
2011-02-27 10:07:05.988 TV: UpdateLCD done
2011-02-27 10:07:05.988 TV: ITVRestart done
2011-02-27 10:07:06.067 VideoOutput: Created YV12 OSD.
2011-02-27 10:07:12.941 Player(0): DecoderGetFrame() called with NULL decoder.
2011-02-27 10:07:13.252 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.252 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.252 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.252 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.253 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.253 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.253 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.253 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.253 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.253 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.253 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.253 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.253 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.253 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.253 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.253 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.253 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.254 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.254 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.254 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.254 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.254 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.254 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.254 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.254 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.254 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.254 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.254 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.254 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.254 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.254 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.255 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.255 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.255 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.255 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.255 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.255 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.255 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.255 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.255 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.255 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.255 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.255 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.255 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.255 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.255 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.256 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.256 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.256 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.256 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.256 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.256 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.256 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.256 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.256 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.256 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.256 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.256 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.256 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.257 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.257 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.257 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.257 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.257 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.257 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.257 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.257 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.257 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.257 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.257 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.257 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.257 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.258 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.258 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.258 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.258 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.258 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.258 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.258 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.258 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.258 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.258 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.258 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.258 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.259 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.259 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.259 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.259 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.259 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.259 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.259 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.259 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.259 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.259 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.259 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.259 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.259 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.259 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.259 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.260 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.260 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.260 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.260 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.260 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.260 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.260 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.260 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.260 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.260 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.260 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.260 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.260 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.260 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.260 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.260 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.261 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.261 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.261 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.261 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.261 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.261 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.261 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.261 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.261 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.261 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.261 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.261 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.261 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.262 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.262 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.262 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.262 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.262 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.262 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.262 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.262 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.317 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.317 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.317 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.317 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.317 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.317 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.317 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.317 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.317 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.317 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.317 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.317 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.317 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.317 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.317 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.318 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.318 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.318 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.318 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.318 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.318 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.318 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.318 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.318 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.318 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.318 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.318 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.318 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.318 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.318 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.318 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.318 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.318 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.318 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.319 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.319 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.319 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.319 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.319 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.319 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.319 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.319 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.319 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.319 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.319 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.319 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.319 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.319 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.442 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.442 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.442 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.442 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.443 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.443 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.443 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.443 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.443 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.443 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.443 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.443 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.443 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.443 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.443 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.443 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.444 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.444 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.444 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.444 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.444 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.444 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.444 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.444 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.444 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.444 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.444 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.444 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.445 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.445 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.445 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.445 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.445 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.445 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.445 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.445 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.445 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.445 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.445 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.445 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.445 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.445 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.445 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.446 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.446 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.446 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.446 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.446 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.446 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.446 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.446 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.446 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.446 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.446 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.446 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.446 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.446 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.446 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.446 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.447 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.447 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.447 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.447 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.447 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.628 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.628 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.628 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.628 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.628 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.628 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.628 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.628 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.628 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.628 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.628 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.629 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.629 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.629 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.629 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.629 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.629 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.629 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.629 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.629 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.629 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.629 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.630 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.630 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.630 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.630 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.630 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.630 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.630 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.630 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.630 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.630 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.630 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.630 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.630 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.630 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.630 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.630 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.631 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.631 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.631 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.631 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.631 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.631 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.631 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.631 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.631 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.631 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.631 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.631 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.631 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.631 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.631 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.631 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.632 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.632 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.632 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.632 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.632 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.632 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.632 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.632 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.632 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.632 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.693 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.693 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.693 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.693 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.693 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.693 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.693 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.693 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.693 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.694 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.694 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.694 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.694 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.694 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.694 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.694 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.758 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.758 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.758 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.759 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.759 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.759 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.759 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.759 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.759 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.759 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.759 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.759 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.759 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.759 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.759 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.759 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.759 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.760 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.760 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.760 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.760 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.760 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.760 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.760 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.760 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.760 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.760 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.760 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.760 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.760 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.760 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.760 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.761 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.761 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.761 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.761 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.761 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.761 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.761 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.761 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.761 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.761 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.761 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.761 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.761 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.761 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.761 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.761 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.884 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.884 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.884 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.884 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.884 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.884 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.884 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.884 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.884 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.884 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.884 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.884 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.884 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.885 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.885 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.885 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.885 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.885 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.885 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.885 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.885 [h264 @ 0x5df3ae0]non-existing SPS 15 referenced in buffering period
2011-02-27 10:07:13.885 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.885 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.885 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.885 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.886 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.886 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.886 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.886 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.886 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.886 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.886 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.886 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.886 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.886 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.886 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.886 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.886 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.886 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.886 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.886 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.887 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.887 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.887 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.887 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.887 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.887 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.887 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.887 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.887 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.887 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.887 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.887 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.887 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.887 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.887 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:13.888 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.888 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.888 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:13.888 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:13.888 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:13.888 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:13.888 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:13.888 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:14.074 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:14.074 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:14.074 [h264 @ 0x5df3ae0]non-existing PPS referenced
2011-02-27 10:07:14.075 [h264 @ 0x5df3ae0]sps_id out of range
2011-02-27 10:07:14.075 [h264 @ 0x5df3ae0]non-existing SPS 32 referenced in buffering period
2011-02-27 10:07:14.075 [h264 @ 0x5df3ae0]non-existing PPS 0 referenced
2011-02-27 10:07:14.075 [h264 @ 0x5df3ae0]decode_slice_header error
2011-02-27 10:07:14.075 [h264 @ 0x5df3ae0]no frame!
2011-02-27 10:07:14.126 [h264 @ 0x5df3ae0]mmco: unref short failure
2011-02-27 10:07:14.339 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2011-02-27 10:07:14.439 OSD: Base theme size: 1280x720
2011-02-27 10:07:14.439 OSD: Scaling factors: 1.5x1.5
2011-02-27 10:07:14.465 AFD: Opened codec 0xaa95b850, id(H264) type(Video)
2011-02-27 10:07:14.465 AFD: codec AAC has 2 channels
2011-02-27 10:07:14.466 AFD: Opened codec 0xaa968270, id(AAC) type(Audio)
2011-02-27 10:07:14.520 AO: Opening audio device 'spdif' ch 2(2) sr 48000 sf signed 32 bit reenc 0
2011-02-27 10:07:14.552 AudioPlayer: Enabling Audio
2011-02-27 10:07:14.606 AFD: Resetting byte context eof (livetv 1 was eof 0)
2011-02-27 10:07:14.782 [h264 @ 0x5df3ae0]mmco: unref short failure
2011-02-27 10:07:14.838 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAuLLLL
2011-02-27 10:07:14.847 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAuLLLL
2011-02-27 10:07:14.850 [h264 @ 0x5df3ae0]mmco: unref short failure
2011-02-27 10:07:14.856 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAuLLLL
2011-02-27 10:07:14.864 Player(0): Waited 100ms for video buffers LAAAAAAAAAAAAAAAAAAAAAAAAAuLLAL
2011-02-27 10:07:14.968 Player(0): Waited 100ms for video buffers UUULULAAAAAAAAAAAAAAAAAAAAULLAu
2011-02-27 10:07:14.977 Player(0): Waited 100ms for video buffers UUULUULAAAAAAAAAAAAAAAAAAAULLAu
2011-02-27 10:07:14.990 Player(0): Waited 100ms for video buffers UUULUUULAAAAAAAAAAAAAAAAAAULLAu
2011-02-27 10:07:15.123 VideoOutput: Created YV12 OSD.

```

The wiki where it mentions tracking the HD PVR,  [http://www.mythtv.org/wiki/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/Hauppauge_HD-PVR)  it talks about patches for the HD PVR but I have no idea how to apply them, and they looked to be for .23 anyway.  Here's a link to them:
Patch 6719: 
[http://code.mythtv.org/trac/ticket/6719](http://code.mythtv.org/trac/ticket/6719)

Patch 6611: 
[http://code.mythtv.org/trac/ticket/6611](http://code.mythtv.org/trac/ticket/6611)

Thanks bud!

---

### Post by phroman on 2011-02-27
SOLVED:  It was the baud rate in the channel change script.  I had it set to 115200 like in my old setup.  For some reason it only works being set to 9600 now.

It does seem to be even slower than it used to, and that was bad enough, but its working!

---

