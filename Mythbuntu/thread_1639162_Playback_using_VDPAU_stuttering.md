---
title: "Playback using VDPAU stuttering"
date: 2010-12-06
forum: Mythbuntu
---

### Post by Nikas on 2010-12-06
Mythbuntu 10.04.
MythTV 0.24.
2 x Nova T-500
Sweden DVB-T
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 220] (rev a2)

**Some** of my channels are unwatchable using VDPAU. If i change to something else it works great. Sound stuttering and picture broken up like when having bad reception. But as i said, only for some channels. A friend of mine is having the same problem. CPU usage at playback: 3 - 5% and it's SD-tv.

My frontend log fills with this:
> 2010-12-06 19:39:35.868 We have a RingBuffer
2010-12-06 19:39:36.025 Clearing OpenGL painter cache.
2010-12-06 19:39:36.100 VDPAU: Created 2 output surfaces.
2010-12-06 19:39:36.100 VDPAU: Created VDPAU render device 1920x1080
2010-12-06 19:39:36.196 Player(1): Video timing method: USleep with busy wait
2010-12-06 19:39:36.196 TV: Changing from None to WatchingLiveTV
2010-12-06 19:39:36.196 TV: State is LiveTV & mctx == ctx
2010-12-06 19:39:36.198 TV: UpdateOSDInput done
2010-12-06 19:39:36.198 TV: UpdateLCD done
2010-12-06 19:39:36.198 TV: ITVRestart done
2010-12-06 19:39:36.281 VDPAU: Added 2 output surfaces (total 4, max 4)
2010-12-06 19:39:39.848 Player(1): DecoderGetFrame() called with NULL decoder.
2010-12-06 19:39:40.921 RingBuf(/var/lib/mythtv/recordings/1021_20101206193939.mpg): Waited 1.0 seconds for data
                        to become available... 2520 < 32768
2010-12-06 19:39:40.921 Checking to see if there's a new livetv program to switch to..
2010-12-06 19:39:41.923 RingBuf(/var/lib/mythtv/recordings/1021_20101206193939.mpg): Waited 2.0 seconds for data
                        to become available... 2520 < 32768
2010-12-06 19:39:41.923 Checking to see if there's a new livetv program to switch to..
2010-12-06 19:39:46.136 VDPAU Painter: Clearing VDPAU painter cache.
2010-12-06 19:39:46.139 MythPainter: 3 images not yet de-allocated.
2010-12-06 19:39:46.160 Clearing OpenGL painter cache.
2010-12-06 19:39:46.233 VDPAU: Created 2 output surfaces.
2010-12-06 19:39:46.233 VDPAU: Created VDPAU render device 1920x1080
2010-12-06 19:39:46.282 Player(1): Forcing decode extra audio option on (Video method requires it).
2010-12-06 19:39:46.282 AFD: Opened codec 0x9c4a080, id(MPEG2VIDEO) type(Video)
2010-12-06 19:39:46.283 AFD: codec MP2 has 2 channels
2010-12-06 19:39:46.283 AFD: Opened codec 0x9e65660, id(MP2) type(Audio)
2010-12-06 19:39:46.623 AO: Opening audio device 'hw:0,7' ch 2(2) sr 48000 sf signed 32 bit reenc 0
2010-12-06 19:39:46.753 AudioPlayer: Enabling Audio
2010-12-06 19:39:46.825 VDPAU: Added 2 output surfaces (total 4, max 4)
2010-12-06 19:39:47.160 ALSA, Error: WriteAudio: buffer underrun
2010-12-06 19:39:47.679 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAADDDLL
2010-12-06 19:39:47.816 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAADDDLL
2010-12-06 19:39:47.952 Player(1): Waited 100ms for video buffers LAAAAAAAAAAAAAAAAAAAAAAAAAADDDaL
2010-12-06 19:39:47.958 Player(1): Waited 100ms for video buffers LAAAAAAAAAAAAAAAAAAAAAAAAAADDDaL
2010-12-06 19:39:48.094 Player(1): Waited 100ms for video buffers LAAAAAAAAAAAAAAAAAAAAAAAAAADDDaL
2010-12-06 19:39:48.316 Player(1): Waited 100ms for video buffers DLLAAAAAAAAAAAAAAAAAAAAAAAAAADAd
2010-12-06 19:39:48.326 Player(1): Waited 100ms for video buffers DLLAAAAAAAAAAAAAAAAAAAAAAAAAADAd
2010-12-06 19:39:48.468 Player(1): Waited 100ms for video buffers DLLAAAAAAAAAAAAAAAAAAAAAAAAAADAd
2010-12-06 19:39:48.763 ALSA, Error: WriteAudio: buffer underrun
2010-12-06 19:39:49.760 ALSA, Error: WriteAudio: buffer underrun
2010-12-06 19:39:50.751 ALSA, Error: WriteAudio: buffer underrun
2010-12-06 19:39:51.170 Player(1): Waited 100ms for video buffers AAAAAAAAADAADLDLAAAAAAAAAAAAAAAA
2010-12-06 19:39:51.175 Player(1): Waited 100ms for video buffers AAAAAAAAADAADLDLAAAAAAAAAAAAAAAA
2010-12-06 19:39:51.506 ALSA, Error: WriteAudio: buffer underrun
2010-12-06 19:39:52.303 ALSA, Error: WriteAudio: buffer underrun
2010-12-06 19:39:52.412 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAADDADLALAAAAAAAAAA
2010-12-06 19:39:52.639 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAADAADdALLAAAAAAAAA
2010-12-06 19:39:52.645 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAADAADdALLAAAAAAAAA
2010-12-06 19:39:52.907 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAADDALDLAAAAAAAA
2010-12-06 19:39:52.912 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAADDALDLAAAAAAAA
2010-12-06 19:39:53.761 ALSA, Error: WriteAudio: buffer underrun
2010-12-06 19:39:54.508 ALSA, Error: WriteAudio: buffer underrun
2010-12-06 19:39:54.721 Player(1): Waited 100ms for video buffers AAADDAAAALDLAAAAAAAAAAAAAAAAAAAA
2010-12-06 19:39:54.900 Player(1): Waited 100ms for video buffers AAAADAAAALDdLAAAAAAAAAAAAAAAAAAA
2010-12-06 19:39:54.906 Player(1): Waited 100ms for video buffers AAAADAAAALDdLAAAAAAAAAAAAAAAAAAA
2010-12-06 19:39:55.260 ALSA, Error: WriteAudio: buffer underrun
2010-12-06 19:39:56.265 ALSA, Error: WriteAudio: buffer underrun
2010-12-06 19:39:57.259 ALSA, Error: WriteAudio: buffer underrun
2010-12-06 19:39:57.763 ALSA, Error: WriteAudio: buffer underrun
2010-12-06 19:39:57.956 Player(1): Waited 100ms for video buffers LAAAAAAAAAAAAAAAAAAAAAAAAADDDaAL
2010-12-06 19:39:57.962 Player(1): Waited 100ms for video buffers LAAAAAAAAAAAAAAAAAAAAAAAAADDDaAL


My /etc/modprobe.d/dvb-usb-dib0700.conf
> options dvb-usb-dib0700 force_lna_activation=1
options dvb_usb disable-rc-polling=1
options usbcore autosuspend=-1


Where do i start?

Edit: I have looked here and it's to no help for me.
[http://www.mythtv.org/wiki/VDPAU#Troubleshooting](http://www.mythtv.org/wiki/VDPAU#Troubleshooting)

Edit 2: Sweden did some changes to one mux and i think the problems started after that:
"Mode change mux 5 from short mode to mode 24M (FEC 2/3, Guard 1/32)."
They have not changed anything on the other muxes but i'm having problems with channels at mux 4 AND 5.
I have removed and rescanned channels and transports.

Keep in mind, this problems show when using VDPAU. No stuttering or bad picture when using another playback profile like CPU++...

---

### Post by byronmyth on 2010-12-07
This may sound overly simplistic, but have you tried the other antenna socket on the Nova-T? Seems to make a big difference to mine, but that was signal strength related (too much).

---

### Post by Nikas on 2010-12-07
> **byronmyth said:**
> This may sound overly simplistic, but have you tried the other antenna socket on the Nova-T? Seems to make a big difference to mine, but that was signal strength related (too much).

I have the "old" Nova-T card with one input for both tuners. Not diversity in other words.
No artifacts when i play the file using my computer or another playback profile. Only having problems with VDPAU.

---

### Post by jlazkano on 2011-03-06
Hello, I am having same problem on a Debian Squeeze, I have a ION board with one DVB-S2 and two DVB-T.

Any solution?

Best regards.

---

### Post by LowSky on 2011-03-06
Use a different VDPAU setting.

I really think the main issue is signal strength

---

### Post by Nikas on 2011-03-06
> **LowSky said:**
> Use a different VDPAU setting.

I really think the main issue is signal strength

Same problem with another setting.
VDPAU = problems
Not using VDPAU (same recording) = no problems.

---

### Post by jyavenard on 2011-03-07
> **Nikas said:**
> Same problem with another setting.
VDPAU = problems
Not using VDPAU (same recording) = no problems.

VDPAU is far more picky as to what it can actually decode as opposed to the software decoder.

There are limitations related to the size of the video being played, the encoding profile used etc...

The other issues could be with the amount of vdpau buffer you have allocated : currently this is not something mythtv will automatically set. Try raising the number of vdpau buffers used:
[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

The default for vdpaubuffersize is 17. Try raising it to 32 (you add a filter in the playback profile and enter vdpaubuffersize=32)

If your processor is fast enough, you could also try using a custom playback profile that uses ffmpeg for decoding but VDPAU for the rendering and deinterlacing.

That way you get the best of both world.

---

### Post by Nikas on 2011-03-07
> **jyavenard said:**
> VDPAU is far more picky as to what it can actually decode as opposed to the software decoder.

There are limitations related to the size of the video being played, the encoding profile used etc...

The other issues could be with the amount of vdpau buffer you have allocated : currently this is not something mythtv will automatically set. Try raising the number of vdpau buffers used:
[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

The default for vdpaubuffersize is 17. Try raising it to 32 (you add a filter in the playback profile and enter vdpaubuffersize=32)

If your processor is fast enough, you could also try using a custom playback profile that uses ffmpeg for decoding but VDPAU for the rendering and deinterlacing.

That way you get the best of both world.

vdpaubuffersize does nothing for me.
It's just recordings from some channels. Seems like they use another bitrate or something that vdpau cant handle right.

I have a ION second generation with Intel(R) Atom(TM) CPU D510   @ 1.66GHz (DualCore).

---

### Post by jlazkano on 2011-03-07
> **Nikas said:**
> vdpaubuffersize does nothing for me.
It's just recordings from some channels. Seems like they use another bitrate or something that vdpau cant handle right.

I have a ION second generation with Intel(R) Atom(TM) CPU D510   @ 1.66GHz (DualCore).

Same problem here, I try with vdpaubuffersize but nothing. I am using Nvidia ION with Atom 330 processor.

I have no problem with 1080p MKV videos. How can I check the DVB-T and DVB-S2 bitrate/codec?

Thanks for all your and best regards.

---

### Post by baffle on 2011-12-02
I have the same hardware and problems as described here; Did anyone eventually find a solution to this?

---

### Post by dibuntux on 2011-12-06
Many people have this problem (see this [http://ubuntuforums.org/showthread.php?t=1780984](http://ubuntuforums.org/showthread.php?t=1780984)), but with the latest update it seems solved. At least for SD stuff, on HD still some problems do arise.
I'm on 0.24 with the latest PPA updated, but I have the latest nVidia driver (290), which I think solve the problem. Check what driver you have (if its 185, as per 10.04 standard) and look for how to get the latest using x-squad nvidia latest.
Hope it helps.


Mythbuntu 10.04 AMD64
Gigabyte GA-M720
Athlon X2 4800+
Nvidia 9400GT 1GB
WD Sata2 CaviarGreen X 2
Skystar 2 DVB-s
Nova T-500 dual DVB-T
Denon AVR 1610 connected with SPDIF
Optoma HD700x on DVI

---

### Post by jlazkano on 2011-12-06
Thanks dibuntux.

I am using the latest version from this repository:

```

deb http://ppa.launchpad.net/mythbuntu/0.24/ubuntu oneiric main
deb-src http://ppa.launchpad.net/mythbuntu/0.24/ubuntu oneiric main

```

I have 280.13 version of Nvidia driver, could I install the latest driver manually? Any updated repository to Oneiric?

I have ION board FE/BE with dual boot, Mythbuntu (Oneiric) and Debian (Squeeze) with same problem on both systems.

This problem will be related with ION, VDPAU and HD channels.

Thanks for your help.

---

### Post by nickrout on 2011-12-06
> look for how to get the latest using x-squad nvidia latest

I think he actually means x-swat

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by jlazkano on 2011-12-07
> **nickrout said:**
> I think he actually means x-swat

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Thanks!

---

### Post by BicyclerBoy on 2011-12-08
There is a possibility that the recorded data is corrupt.

Should try s/w decode on same recordings (just try VLC) to eliminate corrupt recordings.

Recently been forced (10.04.3 myth024+fixes) to add this to /etc/modprobe.d/dvb-options.conf:

# jittery reception nova-t-500 Aust 7MHz & Denmark
options dib3000mc buggy_sfn_workaround=1
options dib7000p buggy_sfn_workaround=1 

check the options are applied (after update-initramfs -u & reboot) with:
cat /sys/module/dvb_usb_dib0700/parameters/force_lna_activation
cat /sys/module/dib3000mc/parameters/buggy_sfn_workaround 

Recent kernel changes seems to require underscores only in the module names/labels/options, previously all "-" minus chars where parsed to underscores.

Not all multiplexes are/where affected & single frequency networks are not used here for dvb-t.

---

