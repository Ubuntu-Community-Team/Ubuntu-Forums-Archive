---
title: "Upgraded from 9.04 to 9.10 and lost sound"
date: 2009-12-31
forum: Mythbuntu
---

### Post by jimmorton on 2009-12-31
Hi All, 
I just upgraded Mythbuntu from 9.04 / .021 to 9.10 / 0.22. I thought it  went rather smoothly but I have a few problems. 
First and most important I have no sound. I get a loud click from the  speakers and then silence. 

Both - 

Opening ALSA audio device 'default'. 
mixer unable to find control Master 1 

and 

WriteAudio: buffer underrun 
NVP(0): Forcing decode extra audio option on (Video method requires it). 
AFD: Opened codec 0x2f77630, id(MPEG2VIDEO) type(Video) 
AFD: codec AC3 has 6 channels 
AFD: Opened codec 0x56ec5e0, id(AC3) type(Audio) 
FilterManager: Failed to load filter 'colorspace', no such filter exists 
FilterManager: Failed to load filter 'colorspace', no such filter exists 

are here repeatedly. I'm not sure what they mean. Here is the frontend log. 

==> /var/log/mythtv/mythfrontend.log <== 
2009-12-31 13:38:24.275 Loading menu theme from  /usr/share/mythtv/themes/DVR//main_settings.xml 
2009-12-31 13:38:40.613 Received a remote 'Clear Cache' request 
2009-12-31 13:38:45.122 Received a remote 'Clear Cache' request 
2009-12-31 13:38:47.809 Loading menu theme from  /usr/share/mythtv/themes/DVR//tv_settings.xml 
2009-12-31 13:38:55.571 Received a remote 'Clear Cache' request 
2009-12-31 13:38:57.586 Received a remote 'Clear Cache' request 
2009-12-31 13:39:20.168 Received a remote 'Clear Cache' request 
2009-12-31 13:39:27.628 Loading menu theme from  /usr/share/mythtv/themes/DVR//tvmenu.xml 
2009-12-31 13:39:28.384 TV: Attempting to change from None to Watching  WatchingLiveTV 
2009-12-31 13:39:28.386 MythContext: Connecting to backend server:  192.168.1.8:6543 (try 1 of 1) 
2009-12-31 13:39:28.386 Using protocol version 50 
2009-12-31 13:39:28.388 Spawning LiveTV Recorder -- begin 
2009-12-31 13:39:28.418 Spawning LiveTV Recorder -- end 
2009-12-31 13:39:28.425 We have a  playbackURL(/video/livetv/1431_20091231133928.mpg) & cardtype(DUMMY) 
2009-12-31 13:39:28.426 We have a RingBuffer 
2009-12-31 13:39:28.476 TV: StartPlayer(0, Watching WatchingLiveTV,  main) -- begin 
2009-12-31 13:39:28.488 NVP(0): Disabling Audio, params(-1,2,44100) 
2009-12-31 13:39:28.766 FilterManager: Failed to load filter  'colorspace', no such filter exists 
2009-12-31 13:39:28.768 OSD Theme Dimensions W: 1280 H: 720 
2009-12-31 13:39:28.958 TV: StartPlayer(0, Watching WatchingLiveTV,  main) -- end ok 
2009-12-31 13:39:28.958 TV: Changing from None to Watching WatchingLiveTV 
2009-12-31 13:39:28.958 TV: State is LiveTV & mctx == ctx 
2009-12-31 13:39:28.958 New DB connection, total: 4 
2009-12-31 13:39:28.958 Connected to database 'mythconverg' at host:  localhost 
2009-12-31 13:39:28.960 Realtime priority would require SUID as root. 
2009-12-31 13:39:28.961 TV: UpdateOSDInput done 
2009-12-31 13:39:28.961 TV: UpdateLCD done 
2009-12-31 13:39:28.961 TV: ITVRestart done 
2009-12-31 13:39:28.963 OpenGLVideoSync() 
2009-12-31 13:39:28.986 ScreenSaverX11Private: DPMS Deactivated 1 
2009-12-31 13:39:28.997 Video timing method: SGI OpenGL 
2009-12-31 13:39:29.330 FilterManager: Failed to load filter  'colorspace', no such filter exists 
2009-12-31 13:39:30.917 NVP(0): Forcing decode extra audio option on  (Video method requires it). 
2009-12-31 13:39:31.002 FilterManager: Failed to load filter  'colorspace', no such filter exists 
2009-12-31 13:39:31.002 AFD: Opened codec 0x4511ef0, id(MPEG2VIDEO)  type(Video) 
2009-12-31 13:39:31.002 AFD: codec AC3 has 6 channels 
2009-12-31 13:39:31.003 AFD: Opened codec 0x90578a0, id(AC3) type(Audio) 
2009-12-31 13:39:31.037 Opening audio device 'default'. ch 2(2) sr 48000 
2009-12-31 13:39:31.037 Opening ALSA audio device 'default'. 
2009-12-31 13:39:31.177 mixer unable to find control Master 1 
2009-12-31 13:39:31.178 NVP(0): Enabling Audio 
2009-12-31 13:39:39.202 FilterManager: Failed to load filter  'colorspace', no such filter exists 
2009-12-31 13:39:39.963 FilterManager: Failed to load filter  'colorspace', no such filter exists 
2009-12-31 13:39:40.179 WriteAudio: buffer underrun 
2009-12-31 13:39:40.231 NVP(0): Forcing decode extra audio option on  (Video method requires it). 
2009-12-31 13:39:40.844 NVP(0): Prebuffer wait timed out 10 times. 
2009-12-31 13:39:41.490 NVP(0): Forcing decode extra audio option on  (Video method requires it). 
2009-12-31 13:39:41.579 FilterManager: Failed to load filter  'colorspace', no such filter exists 
2009-12-31 13:39:41.579 AFD: Opened codec 0x56ec5e0, id(MPEG2VIDEO)  type(Video) 
2009-12-31 13:39:41.579 AFD: codec AC3 has 6 channels 
2009-12-31 13:39:41.579 AFD: Opened codec 0x2f77630, id(AC3) type(Audio) 
2009-12-31 13:39:47.993 FilterManager: Failed to load filter  'colorspace', no such filter exists 
2009-12-31 13:39:48.996 FilterManager: Failed to load filter  'colorspace', no such filter exists 
2009-12-31 13:39:49.746 WriteAudio: buffer underrun 
2009-12-31 13:39:49.773 NVP(0): Forcing decode extra audio option on  (Video method requires it). 
2009-12-31 13:39:50.575 AFD: Opened codec 0x2f77630, id(MPEG2VIDEO)  type(Video) 
2009-12-31 13:39:50.575 AFD: codec AC3 has 6 channels 
2009-12-31 13:39:50.575 AFD: Opened codec 0x56ec5e0, id(AC3) type(Audio) 
2009-12-31 13:40:11.102 FilterManager: Failed to load filter  'colorspace', no such filter exists 
2009-12-31 13:40:11.815 FilterManager: Failed to load filter  'colorspace', no such filter exists 
2009-12-31 13:40:12.478 WriteAudio: buffer underrun 
2009-12-31 13:40:12.535 NVP(0): Forcing decode extra audio option on  (Video method requires it). 
2009-12-31 13:40:13.207 AFD: Opened codec 0x56ec5e0, id(MPEG2VIDEO)  type(Video) 
2009-12-31 13:40:13.207 AFD: codec AC3 has 6 channels 
2009-12-31 13:40:13.208 AFD: Opened codec 0x2f77630, id(AC3) type(Audio) 
2009-12-31 13:40:13.944 NVP(0): prebuffering pause 
2009-12-31 13:40:14.816 NVP(0): prebuffering pause 
2009-12-31 13:40:15.359 WriteAudio: buffer underrun 
2009-12-31 13:40:16.139 FilterManager: Failed to load filter  'colorspace', no such filter exists 
2009-12-31 13:40:16.758 FilterManager: Failed to load filter  'colorspace', no such filter exists 
2009-12-31 13:40:17.494 WriteAudio: buffer underrun 
2009-12-31 13:40:17.521 NVP(0): Forcing decode extra audio option on  (Video method requires it). 
2009-12-31 13:40:18.994 NVP(0): Prebuffer wait timed out 10 times. 
2009-12-31 13:40:20.375 AFD: Opened codec 0x4dd8480, id(MPEG2VIDEO)  type(Video) 
2009-12-31 13:40:20.375 AFD: codec AC3 has 6 channels 
2009-12-31 13:40:20.376 AFD: Opened codec 0x2f77630, id(AC3) type(Audio) 
2009-12-31 13:40:20.494 NVP(0): Prebuffer wait timed out 20 times. 
2009-12-31 13:40:27.921 TV: Attempting to change from Watching  WatchingLiveTV to None 
2009-12-31 13:40:27.955 ~OpenGLVideoSync() -- closing opengl vsync 
2009-12-31 13:40:28.162 TV: Changing from Watching WatchingLiveTV to None 
2009-12-31 13:40:28.163 ScreenSaverX11Private: DPMS Reactivated 1 
2009-12-31 13:40:39.018 Loading menu theme from  /usr/share/mythtv/themes/DVR//util_menu.xml 
2009-12-31 13:40:40.395 Loading window theme from  /usr/share/mythtv/themes/Terra/menu-ui.xml 
2009-12-31 13:40:40.463 Loading menu theme from  /usr/share/mythtv/musicmenu.xml 
2009-12-31 13:40:41.420 XMLParse: LoadTheme using  '/usr/share/mythtv/themes/default-wide/music-ui.xml' 
2009-12-31 13:40:42.011 Opening audio device 'default'. ch 2(2) sr 44100 
2009-12-31 13:40:42.012 Opening ALSA audio device 'default'. 
2009-12-31 13:40:42.156 mixer unable to find control Master 1 
2009-12-31 13:40:42.307 ScreenSaverX11Private: DPMS Deactivated 1 
MMX detected. Using fast method ! 
2009-12-31 13:40:55.226 ScreenSaverX11Private: DPMS Reactivated 1 
2009-12-31 13:42:54.475 XMLParse: LoadTheme using  '/usr/share/mythtv/themes/default-wide/music-ui.xml' 
2009-12-31 13:42:54.982 Opening audio device 'default'. ch 2(2) sr 44100 
2009-12-31 13:42:54.982 Opening ALSA audio device 'default'. 
2009-12-31 13:42:55.116 mixer unable to find control Master 1 
2009-12-31 13:42:55.128 ScreenSaverX11Private: DPMS Deactivated 1 
2009-12-31 13:43:09.162 ScreenSaverX11Private: DPMS Reactivated 1 
2009-12-31 13:43:13.762 AudioPulseUtil: Resume Success 
2009-12-31 13:43:13.769 Deleting UPnP client... 
Error in my_thread_global_end(): 2 threads didn't exit 

Any suggestions?

---

### Post by axelsvag on 2010-01-01
I have not myself dared to upgrade to 9.10 on my mythtv installation. But I have done it in my other computers. I am not at all certain that I can help you but there is some people that have had problem with this. One suggestion I have come from this blog [http://littlejohn.se/]("http://littlejohn.se/")it says there that it sometimes is problem with the kernels after an upgrade. The suggstions is basically this 
Check kernel version
```
sudo uname -r
```
if kernel version is below 2.6.31 do like this 
delete the file /boot/grub/menu.lst
then run this ```
sudo update-grub
```
check then on what partion you have your mbr 

and the run the this ```
sudo grub-install /dev/sdx 
``` change x and s to the right one for you.

---

### Post by jimmorton on 2010-01-01
I just got it fixed. I tried numerous suggestions that I turned up in various searches. The thing that finally did it or me was uninstalling PulseAudio.

Thanks fro your suggestions!

---

### Post by brundles on 2010-01-07
Possibly a stupid question, but did removing pulseaudio stop it playing back analog sound sources?

With pulseaudio running, XBMC currently refuses to play back digital streams (Dolby, DTS, etc)  but without it you can't have analogue streams (e.g. MP3).

Not to mention attemps to configure the sound setup via the preferences menu results in Ubuntu sitting there waiting for a response from the sound system :(.

---

