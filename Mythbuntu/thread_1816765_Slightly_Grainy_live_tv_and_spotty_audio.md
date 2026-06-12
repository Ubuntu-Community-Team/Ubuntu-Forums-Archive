---
title: "Slightly Grainy live tv and spotty audio"
date: 2011-08-02
forum: Mythbuntu
---

### Post by grunge09 on 2011-08-02
1st my Rig:

Amd Quad Core 3.4GHz
1 GB Ram
1 TB Sata II HD
DVD Player Drive
Gigabit onboard
Using HDMI out of Nvidoa 210 Video Card to 32" LCD
I have Mythtv loaded on top of Ubuntu 11.04 64 bit.  
Hauppauge HVR-2250, using analog tuners only

Got it pretty much working (trial and error ya know), ripped a CD it plays, can play a DVD, Got Schedules Direct working.  

Initially had problems with IP Address not allowing frontend to work on same box as primary backend server.  Using DHCP to on Eth0 does not work.  Had to set static IP Address of same IP address and, mask, gateway & DNS and now that works.  

Had problems with setting a record and it not working, tuners were not setup right, deleted them and re-setup them as analog sizes only and now it works.  

NOW my 2 issues left are:

Live TV is a little grainy.  I changed out the TV Cable (I am using the new mythbox via a 2 way splitter with local cable co box) no help.  I swapped the one on the cable box and same thing.  Cable box is not grainy.

Also when live tv switches to commercials or I change channels I get white noise and stays on or stutters, until I go back to Live TV and chage channel again.  

The Audio is {SOLVED} Went thru FRONTEND SETUP and changed Audio to correct HDMI option.  That is fixed.  

In Myth TV Setup using ALSA:Default 

On Ubuntu I had to setup /etc/asound.conf to:

pcm.!default {
type hw
card 1
device 8
}

Seems Transcoding is not working now.  

My Mythtv log is:

2011-08-02 12:05:05.093 OSD: Scaling factors: 0.5625x0.8
2011-08-02 12:05:05.151 OSD: Base theme size: 1280x720
2011-08-02 12:05:05.151 OSD: Scaling factors: 0.5625x0.8
2011-08-02 12:05:05.154 Player(5): Video timing method: USleep with busy wait
2011-08-02 12:05:05.154 TV: Changing from None to WatchingLiveTV
2011-08-02 12:05:05.154 TV: State is LiveTV & mctx == ctx
2011-08-02 12:05:05.156 TV: UpdateOSDInput done
2011-08-02 12:05:05.156 TV: UpdateLCD done
2011-08-02 12:05:05.156 TV: ITVRestart done
2011-08-02 12:05:05.179 ScreenSaverX11Private: DPMS Deactivated 1
2011-08-02 12:05:05.250 VideoOutput: Created YV12 OSD.
2011-08-02 12:05:07.165 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2011-08-02 12:05:07.195 OSD: Base theme size: 1280x720
2011-08-02 12:05:07.195 OSD: Scaling factors: 0.5625x0.666667
2011-08-02 12:05:07.209 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-08-02 12:05:07.210 AFD: Opened codec 0x7f75a8833660, id(MPEG2VIDEO) type(Video)
2011-08-02 12:05:07.210 AFD: codec MP2 has 2 channels
2011-08-02 12:05:07.210 AFD: Opened codec 0x7f75a8832bc0, id(MP2) type(Audio)
2011-08-02 12:05:07.395 AO: Resampling from 48 kHz to 44 kHz with quality medium
2011-08-02 12:05:07.396 AO: Opening audio device 'PulseAudio:default' ch 2(2) sr 44100 sf 32 bit floating point reenc 0
2011-08-02 12:05:07.879 AudioPlayer: Enabling Audio
2011-08-02 12:05:07.933 AFD: Resetting byte context eof (livetv 1 was eof 0)
2011-08-02 12:05:08.066 VideoOutput: Created YV12 OSD.
2011-08-02 12:05:10.444 OSD: Base theme size: 1280x720
2011-08-02 12:05:10.444 OSD: Scaling factors: 0.5625x0.666667
2011-08-02 12:05:11.888 Preview: RemotePreviewRun() -- no reply..
2011-08-02 12:05:13.346 TV: OSDDialogEvent: result -2 text  action 0
2011-08-02 12:05:17.184 pause_active: 0
2011-08-02 12:05:44.415 [mp2 @ 0x7f75beae2580]incomplete frame
2011-08-02 12:05:44.415 AFD Error: Unknown audio decoding error
2011-08-02 12:05:44.442 PulseAudio Error: stream buffer under flow
2011-08-02 12:05:46.023 RingBuf(/var/lib/mythtv/livetv/1039_20110802120545.mpg) Warning: Not starting read ahead thread, already running
2011-08-02 12:05:46.034 Player(5): Waited 10ms for decoder lock
2011-08-02 12:05:46.088 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:05:46.088 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:05:46.088 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:05:46.088 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:05:46.088 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:05:46.088 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:05:46.088 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:05:46.088 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:05:46.088 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:05:46.089 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:05:46.094 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-08-02 12:05:46.094 AFD: Opened codec 0x7f75a8833660, id(MPEG2VIDEO) type(Video)
2011-08-02 12:05:46.094 AFD: codec MP2 has 2 channels
2011-08-02 12:05:46.094 AFD: Opened codec 0x7f75a851c830, id(MP2) type(Audio)
2011-08-02 12:05:46.100 AFD: Resetting byte context eof (livetv 1 was eof 0)
2011-08-02 12:05:46.224 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:05:46.224 AFD Error: Unknown decoding error
2011-08-02 12:05:46.224 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:05:46.224 AFD Error: Unknown decoding error
2011-08-02 12:05:46.225 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:05:46.225 AFD Error: Unknown decoding error
2011-08-02 12:05:46.225 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:05:46.225 AFD Error: Unknown decoding error
2011-08-02 12:05:46.225 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:05:46.225 AFD Error: Unknown decoding error
2011-08-02 12:05:46.225 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:05:46.225 AFD Error: Unknown decoding error
2011-08-02 12:05:46.225 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:05:46.225 AFD Error: Unknown decoding error
2011-08-02 12:05:46.226 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:05:46.226 AFD Error: Unknown decoding error
2011-08-02 12:05:46.226 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:05:46.226 AFD Error: Unknown decoding error
2011-08-02 12:05:46.226 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:05:46.226 AFD Error: Unknown decoding error
2011-08-02 12:05:46.324 Player(5): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAUUUuL
2011-08-02 12:05:46.333 Player(5): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAUUUuL
2011-08-02 12:05:46.342 Player(5): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAUUUuL
2011-08-02 12:05:46.347 Player(5): Waited 100ms for video buffers LAAAAAAAAAAAAAAAAAAAAAAAAAUUUUL
2011-08-02 12:05:56.820 TV: Attempting to change from WatchingLiveTV to None
2011-08-02 12:05:57.438 TV: Changing from WatchingLiveTV to None
2011-08-02 12:05:57.439 ScreenSaverX11Private: DPMS Reactivated 1
2011-08-02 12:05:58.624 TV: Attempting to change from None to WatchingLiveTV
2011-08-02 12:05:58.624 MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1 of 1)
2011-08-02 12:05:58.624 Using protocol version 63
2011-08-02 12:05:58.729 Spawning LiveTV Recorder -- begin
2011-08-02 12:05:59.147 Spawning LiveTV Recorder -- end
2011-08-02 12:05:59.154 We have a playbackURL(/var/lib/mythtv/livetv/1068_20110802120558.mpg) & cardtype(DUMMY)
2011-08-02 12:05:59.154 We have a RingBuffer
2011-08-02 12:05:59.186 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2011-08-02 12:05:59.212 OSD: Base theme size: 1280x720
2011-08-02 12:05:59.212 OSD: Scaling factors: 0.5625x0.8
2011-08-02 12:05:59.226 OSD: Base theme size: 1280x720
2011-08-02 12:05:59.226 OSD: Scaling factors: 0.5625x0.8
2011-08-02 12:05:59.229 Player(2): Video timing method: USleep with busy wait
2011-08-02 12:05:59.230 TV: Changing from None to WatchingLiveTV
2011-08-02 12:05:59.230 TV: State is LiveTV & mctx == ctx
2011-08-02 12:05:59.231 TV: UpdateOSDInput done
2011-08-02 12:05:59.231 TV: UpdateLCD done
2011-08-02 12:05:59.231 TV: ITVRestart done
2011-08-02 12:05:59.242 ScreenSaverX11Private: DPMS Deactivated 1
2011-08-02 12:05:59.310 VideoOutput: Created YV12 OSD.
2011-08-02 12:06:00.546 Player(2): Waited 10ms for decoder lock
2011-08-02 12:06:01.192 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2011-08-02 12:06:01.218 OSD: Base theme size: 1280x720
2011-08-02 12:06:01.218 OSD: Scaling factors: 0.5625x0.666667
2011-08-02 12:06:01.232 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-08-02 12:06:01.233 AFD: Opened codec 0x7f75a894a200, id(MPEG2VIDEO) type(Video)
2011-08-02 12:06:01.233 AFD: codec MP2 has 2 channels
2011-08-02 12:06:01.233 AFD: Opened codec 0x7f75a89361e0, id(MP2) type(Audio)
2011-08-02 12:06:01.294 AO: Resampling from 48 kHz to 44 kHz with quality medium
2011-08-02 12:06:01.294 AO: Opening audio device 'PulseAudio:default' ch 2(2) sr 44100 sf 32 bit floating point reenc 0
2011-08-02 12:06:01.298 AudioPlayer: Enabling Audio
2011-08-02 12:06:01.354 AFD: Resetting byte context eof (livetv 1 was eof 0)
2011-08-02 12:06:01.616 VideoOutput: Created YV12 OSD.
2011-08-02 12:06:05.699 PulseAudio Error: stream buffer under flow
2011-08-02 12:06:06.935 RingBuf(/var/lib/mythtv/livetv/1039_20110802120606.mpg) Warning: Not starting read ahead thread, already running
2011-08-02 12:06:06.975 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:06:06.976 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:06:06.976 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:06:06.976 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:06:06.982 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-08-02 12:06:06.982 AFD: Opened codec 0x7f75a894a200, id(MPEG2VIDEO) type(Video)
2011-08-02 12:06:06.982 AFD: codec MP2 has 2 channels
2011-08-02 12:06:06.982 AFD: Opened codec 0x7f75a8900f00, id(MP2) type(Audio)
2011-08-02 12:06:07.021 AFD: Resetting byte context eof (livetv 1 was eof 0)
2011-08-02 12:06:07.263 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:06:07.263 AFD Error: Unknown decoding error
2011-08-02 12:06:07.263 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:06:07.263 AFD Error: Unknown decoding error
2011-08-02 12:06:07.263 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:06:07.263 AFD Error: Unknown decoding error
2011-08-02 12:06:07.263 [mpeg2video @ 0x7f75beae2580]mpeg_decode_postinit() failure
2011-08-02 12:06:07.263 AFD Error: Unknown decoding error
2011-08-02 12:06:07.364 Player(2): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAUUUUUUUUuL
2011-08-02 12:06:07.373 Player(2): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAUUUUUUUUuL
2011-08-02 12:06:07.386 Player(2): Waited 100ms for video buffers UUuLAAAAAAAAAAAAAAAAAUUUUUUUUUU
2011-08-02 12:07:04.259 RingBuf(/var/lib/mythtv/livetv/1039_20110802120606.mpg): Waited 0.2 seconds for data 
			to become available... 26368 < 32768
2011-08-02 12:07:20.239 RingBuf(/var/lib/mythtv/livetv/1039_20110802120606.mpg): Waited 0.2 seconds for data 
			to become available... 27316 < 32768
2011-08-02 12:08:05.428 TV: Attempting to change from WatchingLiveTV to None
2011-08-02 12:08:05.902 TV: Changing from WatchingLiveTV to None
2011-08-02 12:08:05.903 ScreenSaverX11Private: DPMS Reactivated 1
2011-08-02 12:08:08.973 Pulse: Cleaning up PulseHandler
2011-08-02 12:08:08.973 Deleting UPnP client...
Error in my_thread_global_end(): 3 threads didn't exit

When I do "dmesg | grep saa"

[   11.555735] saa7164 driver loaded
[   11.560730] saa7164 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.561307] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   11.561312] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfe400000
[   11.561318] saa7164 0000:02:00.0: setting latency timer to 64
[   11.830032] saa7164_downloadfirmware() no first image
[   11.830041] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   12.053415] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   12.053418] saa7164_downloadfirmware() firmware loaded.
[   12.053424] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[   12.053429] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   12.053430] saa7164_downloadfirmware() BSLSize = 0x0
[   12.053431] saa7164_downloadfirmware() Reserved = 0x0
[   12.053432] saa7164_downloadfirmware() Version = 0x1661c00
[   19.170028] saa7164_downloadimage() Image downloaded, booting...
[   19.280018] saa7164_downloadimage() Image booted successfully.
[   21.620023] saa7164_downloadimage() Image downloaded, booting...
[   23.160027] saa7164_downloadimage() Image booted successfully.
[   23.210715] saa7164[0]: Hauppauge eeprom: model=88061
[   23.885968] DVB: registering new adapter (saa7164)
[   27.557900] DVB: registering new adapter (saa7164)
[   27.558251] saa7164[0]: registered device video0 [mpeg]
[   27.790649] saa7164[0]: registered device video1 [mpeg]
[   28.001935] saa7164[0]: registered device vbi0 [vbi]
[   28.001960] saa7164[0]: registered device vbi1 [vbi]

Anyone Got any ideas:

---

