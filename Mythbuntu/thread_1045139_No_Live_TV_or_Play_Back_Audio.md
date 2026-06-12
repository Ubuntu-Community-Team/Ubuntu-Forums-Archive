---
title: "No Live TV or Play Back Audio"
date: 2009-01-20
forum: Mythbuntu
---

### Post by RonPDX on 2009-01-20
Hello everyone, 

Earlier this evening while I setting up the digital portion of my card I lost audio for Analog Live TV and Playback (audio works for digital tv), I had this happen once before and I ended up doing a fresh install, however I don't want to do another fresh install since I have all of my setting where I want them. Audio everywhere else is working just as it should.

After battling this for 4 hours I am hoping that someone can point me in the right direction to trouble shoot this issue before I literally pull all of my hair out.  My settings, hardware and log can found below.

**Update**
I finally broke down and did a fresh install with a couple minor tweaks that solved my audio problem.

Mythbuntu 8.10 v0.21
Pinnacle 800i

Audio Output: dev/dsp
Pass Through: Default
Audio Channels: 5.1
Upmix: Passive
Use internal volume control: true (checked)
Mixer Device: dev/mixer
Mixer Control: PCM

Software Encoders
Default, Live TV, High Quality, Low Quality all have the same settings
MP3
Sample: 48000
Quality: 9
Volume: 90

Sound (Preferences Menu)
Sound Effects
Playback: Auto

Music & Movies
Sound Playback: Auto

Audio Conference 
Sound Playback: Auto
Sound Device: Alsa...

Device 
Intel 82801D8 -ICH4 (Alsa Mixer)

Capture Card Audio Device: dev/dsp

All of my ALSA Mixer settings are unmuted and capture option is set to record. On the lower portion the only option that is selected is video. 

```
==> /var/log/mythtv/mythbackend.log <==
2009-01-20 01:20:28.880 Expiring 8 MBytes for 10955 @ Tue Jan 20 01:00:00 2009 => Man vs. Wild "Belize"
2009-01-20 01:26:21.850 MainServer::HandleAnnounce Monitor
2009-01-20 01:26:21.909 adding: homeoffice as a client (events: 0)
2009-01-20 01:26:21.918 MainServer::HandleAnnounce Monitor
2009-01-20 01:26:21.926 adding: homeoffice as a client (events: 1)
2009-01-20 01:26:21.944 MainServer::HandleAnnounce Playback
2009-01-20 01:26:21.957 adding: homeoffice as a client (events: 0)
2009-01-20 01:26:21.966 TVRec(25): Changing from None to WatchingLiveTV
2009-01-20 01:26:21.978 TVRec(25): HW Tuner: 25->25
2009-01-20 01:26:27.437 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
strange error flushing buffer ... 
2009-01-20 01:27:15.191 TVRec(25): HW Tuner: 25->25
2009-01-20 01:27:19.485 Finished recording Man vs. Wild "Belize": channel 10955
2009-01-20 01:27:20.676 Finished recording Man vs. Wild "Belize": channel 10955
2009-01-20 01:27:20.965 TVRec(25): RingBufferChanged()
2009-01-20 01:27:21.021 Finished recording Man vs. Wild "Belize": channel 10955
2009-01-20 01:27:21.052 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-20 01:27:22.896 Using runtime prefix = /usr
2009-01-20 01:27:23.302 Empty LocalHostName.
2009-01-20 01:27:23.504 Using localhost value of homeoffice
2009-01-20 01:27:23.723 New DB connection, total: 1
2009-01-20 01:27:23.826 Connected to database 'mythconverg' at host: localhost
2009-01-20 01:27:23.937 Closing DB connection named 'DBManager0'
2009-01-20 01:27:24.061 Connected to database 'mythconverg' at host: localhost
2009-01-20 01:27:24.172 New DB connection, total: 2
2009-01-20 01:27:24.231 Connected to database 'mythconverg' at host: localhost
2009-01-20 01:27:24.240 Current Schema Version: 1214
2009-01-20 01:27:25.392 Preview: Grabbed preview '/var/lib/mythtv/recordings/10955_20090120012626.nuv' 480x480@64s
2009-01-20 01:27:40.721 TVRec(25): HW Tuner: 25->25
2009-01-20 01:27:45.190 Finished recording Late Night With Conan O'Brien: channel 10956
2009-01-20 01:27:46.428 Finished recording Late Night With Conan O'Brien: channel 10956
2009-01-20 01:27:46.712 TVRec(25): RingBufferChanged()
2009-01-20 01:27:46.751 Finished recording Late Night With Conan O'Brien: channel 10956
2009-01-20 01:27:46.769 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-01-20 01:27:48.296 Using runtime prefix = /usr
2009-01-20 01:27:48.400 Empty LocalHostName.
2009-01-20 01:27:48.485 Using localhost value of homeoffice
2009-01-20 01:27:48.668 New DB connection, total: 1
2009-01-20 01:27:48.817 Connected to database 'mythconverg' at host: localhost
2009-01-20 01:27:48.932 Closing DB connection named 'DBManager0'
2009-01-20 01:27:48.964 Connected to database 'mythconverg' at host: localhost
2009-01-20 01:27:48.999 New DB connection, total: 2
2009-01-20 01:27:49.028 Connected to database 'mythconverg' at host: localhost
2009-01-20 01:27:49.043 Current Schema Version: 1214
2009-01-20 01:27:49.941 Preview: Grabbed preview '/var/lib/mythtv/recordings/10956_20090120012719.nuv' 480x480@64s
2009-01-20 01:27:50.872 TVRec(25): Changing from WatchingLiveTV to None
2009-01-20 01:27:51.464 Finished recording Scrubs "My Fruit Cups": channel 10960
2009-01-20 01:28:28.969 Expiring 33 MBytes for 10955 @ Tue Jan 20 01:00:00 2009 => Man vs. Wild "Belize"
2009-01-20 01:30:29.030 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 01:30:29.039 Expiring 18 MBytes for 10956 @ Tue Jan 20 00:37:00 2009 => Late Night With Conan O'Brien
2009-01-20 01:30:29.054 Expiring 1 MBytes for 10960 @ Tue Jan 20 01:00:00 2009 => Scrubs "My Fruit Cups"
2009-01-20 01:36:12.279 Reschedule requested for id 0.
2009-01-20 01:36:12.469 Scheduled 27 items in 0.2 = 0.00 match + 0.18 place
2009-01-20 01:38:43.315 Reloading backend settings
2009-01-20 01:46:28.280 Using runtime prefix = /usr
2009-01-20 01:46:28.342 Empty LocalHostName.
2009-01-20 01:46:28.349 Using localhost value of homeoffice
2009-01-20 01:46:28.374 New DB connection, total: 1
2009-01-20 01:46:28.385 Connected to database 'mythconverg' at host: localhost
2009-01-20 01:46:28.389 Closing DB connection named 'DBManager0'
2009-01-20 01:46:28.394 Connected to database 'mythconverg' at host: localhost
2009-01-20 01:46:28.400 New DB connection, total: 2
2009-01-20 01:46:28.403 Connected to database 'mythconverg' at host: localhost
2009-01-20 01:46:28.410 Current Schema Version: 1214
Starting up as the master server.
2009-01-20 01:46:28.548 New DB connection, total: 3
2009-01-20 01:46:28.553 Connected to database 'mythconverg' at host: localhost
2009-01-20 01:46:34.980 New DB scheduler connection
2009-01-20 01:46:34.995 Connected to database 'mythconverg' at host: localhost
Digital is defined, but isn't attached to a cardinput.
2009-01-20 01:46:35.170 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-01-20 01:46:35.174 Main::Registering HttpStatus Extension
2009-01-20 01:46:35.176 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-01-20 01:46:35.178 Enabled verbose msgs:  important general
2009-01-20 01:46:35.184 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 01:46:37.778 MainServer::HandleAnnounce Monitor
2009-01-20 01:46:37.788 adding: homeoffice as a client (events: 0)
2009-01-20 01:46:37.791 MainServer::HandleAnnounce Monitor
2009-01-20 01:46:37.794 adding: homeoffice as a client (events: 1)
2009-01-20 01:46:37.807 MainServer::HandleAnnounce Playback
2009-01-20 01:46:37.810 adding: homeoffice as a client (events: 0)
2009-01-20 01:46:37.815 TVRec(25): Changing from None to WatchingLiveTV
2009-01-20 01:46:37.827 TVRec(25): HW Tuner: 25->25
2009-01-20 01:46:38.053 Reschedule requested for id -1.
2009-01-20 01:46:38.201 Scheduled 27 items in 0.1 = 0.05 match + 0.09 place
2009-01-20 01:46:38.218 Seem to be woken up by USER
2009-01-20 01:46:43.340 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
strange error flushing buffer ... 
2009-01-20 01:46:58.213 TFW, Error: Write() -- IOBOUND begin cnt(28582) free(14976)
2009-01-20 01:46:59.291 TFW, Error: Write() -- IOBOUND end
2009-01-20 01:47:32.822 TVRec(25): Changing from WatchingLiveTV to None
2009-01-20 01:47:33.241 Finished recording Scrubs "My Buddy's Booty": channel 10960
2009-01-20 01:47:55.048 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-20 01:50:57.413 Expiring 41 MBytes for 10960 @ Tue Jan 20 01:30:00 2009 => Scrubs "My Buddy's Booty"
2009-01-20 01:52:41.723 MainServer::HandleAnnounce Monitor
2009-01-20 01:52:43.728 adding: homeoffice as a client (events: 0)
2009-01-20 01:52:43.842 MainServer::HandleAnnounce Monitor
2009-01-20 01:52:43.849 adding: homeoffice as a client (events: 1)
2009-01-20 01:52:43.876 Reschedule requested for id -1.
2009-01-20 01:52:44.363 Scheduled 27 items in 0.5 = 0.10 match + 0.37 place

==> /var/log/mythtv/mythfrontend.log <==
2009-01-20 01:46:33.161 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-20 01:46:33.335 MythMusic adding CD-Writer: 1,0,0 -- CD-RW  CRX320EE 
2009-01-20 01:46:33.336 MythMusic adding CD-Writer: 1,1,0 -- LTN486S 48x Max 
2009-01-20 01:46:33.468 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.0.5:5060 NAT address 192.168.0.5
SIP: Cannot register; proxy, username or password not set
2009-01-20 01:46:33.865 NetworkControl: Listening for remote connections on port 6546
2009-01-20 01:46:33.869 No theme dir: /home/stiles/.mythtv/themes/Mythbuntu-8.04
2009-01-20 01:46:37.774 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-20 01:46:37.778 Using protocol version 40
2009-01-20 01:46:37.804 TV: Attempting to change from None to WatchingLiveTV
2009-01-20 01:46:37.806 Using protocol version 40
2009-01-20 01:46:43.478 DPMS Deactivated 
2009-01-20 01:46:43.498 New DB connection, total: 3
2009-01-20 01:46:43.499 New DB connection, total: 4
2009-01-20 01:46:43.501 Connected to database 'mythconverg' at host: localhost
2009-01-20 01:46:43.505 Connected to database 'mythconverg' at host: localhost
2009-01-20 01:46:43.658 Opening audio device '/dev/dsp'. ch 6(2) sr 48000
2009-01-20 01:46:43.660 Opening OSS audio device '/dev/dsp'.
2009-01-20 01:46:52.688 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Video Overlay'
2009-01-20 01:46:53.146 OSD Theme Dimensions W: 640 H: 480
2009-01-20 01:46:58.662 TV: Changing from None to WatchingLiveTV
2009-01-20 01:46:58.674 Realtime priority would require SUID as root.
2009-01-20 01:46:59.005 Video timing method: USleep with busy wait
2009-01-20 01:47:11.803 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.852 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.856 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.858 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.860 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.861 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.863 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.867 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.869 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.873 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.877 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.882 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.885 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.886 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.887 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.889 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.891 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.896 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.898 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.900 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.906 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.910 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.912 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.914 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.915 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.918 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.924 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.951 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.962 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.963 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.965 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.966 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.968 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.973 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.978 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.982 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.983 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.985 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.988 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.990 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.993 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.994 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:11.996 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.005 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.010 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.014 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.085 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.102 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.116 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.148 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.161 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.179 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.204 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.211 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.239 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.253 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.280 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.282 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.305 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.330 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.346 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.348 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.378 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.404 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.418 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.436 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.454 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.481 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.497 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.514 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:12.566 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2009-01-20 01:47:32.798 TV: Attempting to change from WatchingLiveTV to None
2009-01-20 01:47:33.324 TV: Changing from WatchingLiveTV to None
2009-01-20 01:47:33.415 DPMS Reactivated.
Destroying SipFsm object 
2009-01-20 01:47:38.752 Deleting UPnP client...
```

---

### Post by PsyberS on 2009-02-09
I have recently run into a similar problem.  You say you had to do a fresh install to fix it, but with 'tweaks' to the audio.  What did you have to do special to fix this problem?

As an aside, I have found I can get audio back on my PVR-150, but not on the analog input of my HVR-1600.  Audio on the digital input of the HVR-1600 works fine no matter what.

For me, if I set max channels to 2 (as opposed to 5.1) it fixes the PVR-150's audio.  Alternatively, I can change from ALSA to OSS (and leave max channels at 5.1) and it also fixes the PVR-150.  With ALSA+2ch, I get similar audio buffer overflow messages in my frontend log, but with OSS+5.1 I don't get any messages, just no audio.

Any insights would be greatly appreciated, as I really hope to avoid a Windows fix (aka, re-install)! :-)

**Update**
After further investigation, I realized the computer rebooted today and since it's last boot it had updated kernels.  My problem was the cx18 driver for my HVR-1600 needed re-installed for the new kernel.  Once I installed for the new kernel, problem solved!  Not sure if that was your problem but hopefully this helps someone!

---

