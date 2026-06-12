---
title: "Audio over HDMI issues"
date: 2012-12-02
forum: Mythbuntu
---

### Post by splg on 2012-12-02
Hello!

I hope someone here will be able to help! I'm having a problem with audio over HDMI with mythbuntu 12.04 64bit and only stereo sound works. I decided to build a new machine so I've only been working with this a few days and this is all new to me.

My Setup:
* MSI z77ma-g45 mobo with: HDMI out, core i3 cpu with integrated HD4000 graphics, and realtek ALC892 sound on board. (no add-on cards)
* updated my bios as another thread suggested with no change
* HTPC connected via HDMI to my AV Receiver then to my HDtv
* HDhomerun Prime tuner
* mythbuntu 12.04 installed, then selected the update repos as well as repos for mythtv 0.26 since I read that was the latest stable.(completed all updates)
* AV Receiver supporting up to 7.1 and Dolby TrueHD

Playing/ recording off the prime works however my receiver always says "Stereo" even when it's live tv and it says that it's 5.1. I also know the Receiver can do 5.1 since DVDs play fine.

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


```
$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default:CARD=PCH
    HDA Intel PCH, ALC892 Analog
    Default Audio Device
sysdefault:CARD=PCH
    HDA Intel PCH, ALC892 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=PCH,DEV=0
    HDA Intel PCH, HDMI 0
    HDMI Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Hardware device with all software conversions
```


Alsamixer has everything unmuted.

Bios has no options for integrated sound except on/ off. (I read some where to try to switch it to off but that make nothing work)

In the mythtv audio setup, there's a long list of devices however all the ones that include 5.1/7.1 say they are "invalid or not usable". 

If anyone has advice or tests to run, please let me know as I'm anxious to get this working fully!

Thanks in advance

---

### Post by BicyclerBoy on 2012-12-02
In the mythtv audio scanner, pick one that is most like "hw:CARD=PCH,DEV=3".

Later mythtv (0.26?) can directly read the ELD data for connected HDMI devices (*).

As a starting point:
- Untick up-mixing
- untick software volume/dmix
- select AC3 & DTS as supported by amp (* might not exist anymore).

As you are using new iCPU it is possible that later kernels & intel driver are required..

Are you using VA-API (vainfo) ?

---

### Post by splg on 2012-12-03
Hello BicyclerBoy,

In the audio setup, I have alsa:hw:CARD=PCH,DEV3 (Direct hardware without conversion) selected. After you posted I was playing with the audio setup and realized that when I switch it to 5.1 (my current setup is only 5.1 with a 7.1 receiver) it errors out and says I can't use it. However if I just leave it at 7.1, the audio test works and the 2 side speaker locations play through the rear. This seemed good however when I went to watch live tv that was in 5.1, the receiver still shows stereo.

I have everything selected AC3/DTS/TrueHD/etc on that screen. No upmixing and no dmix. Another interesting point you mentioned was 
vainfo. I googled and saw I *should* be using it so I've installed that now but not sure where to go from here:

```
# vainfo 
libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Intel i965 driver - 1.0.15
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileH264Baseline           :	VAEntrypointVLD
      VAProfileH264Baseline           :	VAEntrypointEncSlice
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointEncSlice
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointEncSlice
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

```

I also installed libbluray1 but that is where I stopped. Not to tackle two issues at once, but the video is pretty choppy randomly and especially during fast motions. For a 3.3ghz i3 it seems very strange. I bumped up the hd4000 memory in the bios to 256mb and maxed it out but I'm thinking that is a driver issue.

Again, any direction with either issue would be very appreciated! Sorry for bring up all these issues at once.

---

### Post by BicyclerBoy on 2012-12-04
Do your DVDs play with AC3/DTS audio in MythTV ?

The intel driver gets better in later kernels..I would add/use xorg-edgers ppa. There has been a lot of work done on HD3000/4000 Cedarview etc.
That effects HDMI audio & VA-API.

So the audio prolbems could all disappear with the VA-API problems..

There are 2 ways your system can output multi-channel audio over HDMI:
- matrix encoded AC3 (a52) DTS(-MA) &/or AAC etc
- discrete 6/8 channels LPCM

Post the ELD file from:
/proc/asound/card0/eld#0.0
(check all/any eld#x.y files found for contents)

To start testing I would set the speaker config to 2 ch stereo with amp capabilities set to AC3/DTS.
- try a DVD (with AC3/DTS).

I think MythTV can test HDMI multi-channel audio over AC3 & as discrete multi-ch.

BD playback works very well (no BD menus) & better than DVDs, sometimes have to select diff title from the OSD GUI. There is a bit of tinkering under the hood required.
There is good info on mythtv.org wiki..

---

### Post by rDwyP44y on 2012-12-04
The audio problems should  disappear with the VA-API problems (once you solve them that is)..

---

### Post by splg on 2012-12-05
I'm actually still waiting for my optical drive to be delivered. Earlier when I said DVD's play fine, I should have specified I was using a stand alone player though the AVR. 

I do however have files that on my windows computer that register as 5.1 however the same files don't on my mythbuntu box. I know that isn't the same and maybe I'll have to revisit this whole issue when I can properly troubleshoot. If it helps, this is the output of the eld file:

```

# cat /proc/asound/card0/eld#3.0 
monitor_present		1
eld_valid		1
monitor_name		DENON-AVAMP
connection_type		HDMI
eld_version		[0x2] CEA-861D or below
edid_version		[0x3] CEA-861-B, C or D
manufacture_id		0xee11
product_id		0x1c
port_id			0x0
support_hdcp		0
support_ai		1
audio_sync_delay	0
speakers		[0x5f] FL/FR LFE FC RL/RR RC RLC/RRC
sad_count		7
sad0_coding_type	[0x1] LPCM
sad0_channels		8
sad0_rates		[0x1ee0] 32000 44100 48000 88200 96000 176400 192000
sad0_bits		[0xe0000] 16 20 24
sad1_coding_type	[0x7] DTS
sad1_channels		6
sad1_rates		[0x6c0] 44100 48000 88200 96000
sad1_max_bitrate	1536000
sad2_coding_type	[0x2] AC-3
sad2_channels		6
sad2_rates		[0xe0] 32000 44100 48000
sad2_max_bitrate	640000
sad3_coding_type	[0xb] DTS-HD
sad3_channels		8
sad3_rates		[0x1ec0] 44100 48000 88200 96000 176400 192000
sad4_coding_type	[0xa] E-AC-3/DD+ (Dolby Digital Plus)
sad4_channels		8
sad4_rates		[0xc0] 44100 48000
sad5_coding_type	[0xc] MLP (Dolby TrueHD)
sad5_channels		6
sad5_rates		[0x1ec0] 44100 48000 88200 96000 176400 192000
sad6_coding_type	[0xc] MLP (Dolby TrueHD)
sad6_channels		8
sad6_rates		[0x6c0] 44100 48000 88200 96000

```

I'm not sure when the drive arrives if I can specify how the audio will be "seen" by the AVR. Usually if it's 5.1, it will just display it as such.

Lastly, I added the xorg-edgers PPA and while it did find about 50 updates, it doesn't appear to have changed much (both in getting surround or in video performance). I've been testing further and noticed that while the video of live tv can be choppy, the recordings are not when they are played back. 

Again, I'm at a loss unless there are more packages I'm missing.

Thanks!

---

### Post by nickrout on 2012-12-05
Save yourself a world of pain and get a nVidia card that supports vdpau.

---

### Post by splg on 2012-12-06
So does basically everyone have a dedicated video card that's attached to a receiver? I don't want to give up and I think my blu-ray drive will be here tomorrow or Saturday. I'll have to see if I can make any headway after that.

---

### Post by nickrout on 2012-12-06
> **splg said:**
> So does basically everyone have a dedicated video card that's attached to a receiver? I don't want to give up and I think my blu-ray drive will be here tomorrow or Saturday. I'll have to see if I can make any headway after that.Well it's just that nVidia cards are much better supported for linux than any others, hence my suggestion.

Unfortunately there don't seem to be many motherboards with onboard nvidia graphics chipsets anymore, leading to a need for discrete cards.

A suitable card can be had pretty cheap though.

---

### Post by BicyclerBoy on 2012-12-07
These intel GPU show lots of promise..
-best CPU power efficiency
-low power operating modes
-open source drivers
-common & small mobos

The post-processing shader operations are still way behind nVidia driver & that does not matter for film judder BD 24p.

Try in terminal:
speaker-test -l 2 -c 8 -r 192000 -D hw:0,3

The ELD filename is curious, I expected it to be called eld#0.0, was that file obtained after xorg-edgers update & **reboot**?

You could try starting mythfrontend with extra verbose logging "-v audio" & then use the audio scan & test tool..Then there should be lots of useful info in the stdout, possibly too much to buffer so may need to re-direct to file.

---

### Post by splg on 2012-12-09
It is very strange. I put in a DVD in my xbox and it plays as 5.1 and the receiver recognizes it instantly as dolby digital, however after installing the dvdrom in my myth box, that same dvd shows up as stereo or Multi In.

With the terminal speaker test for the 8 channels, all (5.1 worked) the extra two played in their respective speakers unless I used -c 6. It looks (at least to me) that the computer can do 5.1 however during the test it said "Multi In".

The ELD filename output IIRC was after the update and reboot. There is no other Eld file listed at this point.

I did starting mythfrontend with verbose logging however I wasn't sure about the "-v audio" part. I have a few lines where it said "echo 384 | sudo tee /proc/asound/card0/pcm3p/sub0/prealloc" which I did with no change. One line said to echo in 3008 but again, nothing different happened.

Should I just be getting an inexpensive Nvidia card at this point? Should I get one with HDMI on the back or since my mobo has HDMI, would I be using that port? Since it's only video output (I assume) and I do not have an optical port how would I get sound? Sorry for the turn in the thread. I just don't get what is going on with the current situation, especially when a DVD doesn't even play directly from the DVDrom :confused::confused:

---

### Post by BicyclerBoy on 2012-12-11
Sorry couldn't login yesterday..
I wouldn't give up on intel soln just for audio reasons..

With discete PCIe video card you would used the card HDMI.
The mobo HDMI video output would not be driven by discrete card.
The mobo HDMI jack could be driven by mobo/iGFX only if BIOS & chipset allow.
Intel "H" chipset does not.

All the recent model video cards output audio over HDMI.
Note the GTX200 series did not, GT200 series did with diff capability.
Some very old mobo graphics did.

speaker-test can only test discrete channel audio (no AC3 5.1 etc), so stereo or "multi" is correct.

mythfrontend -v help
- to see all options
mythfrontend -v audio
- verbose audio logging & exercising the audio testing tools generates lots of useful info..(maybe audio is not an option??)

The amp indicating "multi" suggests MythTV is outputting multi-ch LPCM over HDMI rather than bit-streaming the "raw" AC3/DTS/DTS-MA.
This is arguably the highest possible quality audio output but requires the software decoder to be better than the HTamp's decoder & that is a concern.
i.e. (multi) myth is decoding AC3 (etc) & outputting discrete audio channels.

I'm (fairly) sure you can set MythTV to bitstream all "matrix encoded" audio streams. For this to work you must have unticked up-mixing & unticked software volume control.
Is there an "enable pass-through" setting?

---

### Post by drewdin on 2012-12-11
@bicyclerboy, I have the Intel H67bl, from your last post I take it that the HDMI output will not work properly?

I was unable to get it working in 11.10 fixes and I was told when 12.04 comes out it will work, I was going to update but if it still does not work I might just wait.

---

### Post by BicyclerBoy on 2012-12-12
My intel GFX is not used as HTPC..

The H chipsets do not support onboard (iCPU/iGfx) & discrete PCIe to be active together, Just one or the other.
The H chipsets should be capable of HDMI HDA audio.

From what I have read & feedback from others..there is a lot to gain & only a little risk in using xorg-edgers ppa.
There was a lot of intel HD3000/4000/cedarview graphics & HDMI commits in kernel 3.5.

If you wait for 12.04 distro to get to 3.5 you'll be waiting for a long time maybe forever.

---

### Post by splg on 2012-12-12
So I have a bit of (hopefully) funny news. I was scratching my head playing with VLC and my testing with my DVD that has 5.1. For the life of me I couldn't (and can't) get it to play in surround. I got VLC to show Dolby Digital in the drop down and selected it but it stayed as stereo regardless. 

Fast forward a few hours.......

Then I decided to try combinations from the frontend (I tried mythfrontend -v audio). It gave a slew of info in verbose mode but nothing that stood out to me. I continued different combinations of options in the audio setup until I found to my surprise that even though we said originally I should use: alsa:hw:CARD=PCH,DEV3 (Direct hardware without conversion), if I use: ALSA:hdmi:CARD=PCH,DEV=0 (HDA Intel PCH, HDMI0 HDMI Audio Output (AVR connected to HDMI) I get 5.1 on live/recorded TV! Further DEV0 shows up correctly on my AVR display. 

After reading your post (and the Direct Hardware description) I definitely thought that was the correct one to use. I'm not sure what the difference is with DEV0 vs DEV3 but so far it is working. 

VLC on the other hand even with that DEV0 selected, refuses to work right. It is far less of a concern since I will only be playing DVDs/other files a smaller percent of the time. I'd like to know what to do to fix it but again, not a huge concern. 

And it pains me to revisit since the purpose was to be as green as possible, but what video card would help my video performance/clarity without being "too much"? I have a Picture in picture feature and the second window is unwatchable. My assumption is that I need more video processing. I was looking at the nvidia GT630 with 2GB of ram but I'm not sure if it's shear core mhz or shader speed I need or amount of RAM for HTCP stuff. I think that card is cheap enough but has decent specs.

---

### Post by BicyclerBoy on 2012-12-13
Great stuff..
Maybe the "hdmi:..DEV=0" device has a different set of audio capabilities even tho it is essentially the same device as hw:..DEV=3.

MythTV plays DVDs fine here..was a recent menu stutter patch. this also seem to have cured an odd screen focus problem.

Are you now using xorg-edgers ppa for kernel & intel drivers ?
Are you using VA-API ?
Did you try the built-in video playback method tester?

AFAICT the GT630 should be the best choice ATM. VDPAU had 512MB was minimum, sometimes the models with more RAM have a lower/slower shader performance.
DDR3 is better than DDR2.

A kepler based card a bit faster shader than GT430 would be perfect (630 is a rebadged 500 model possibly slightly re-jigged).
The fermi & kepler cards can decode 2 HD streams for stereoscopic. The driver does not enable this?

It is quite difficult to find hard facts about these HTPC cards without buying them..

---

### Post by splg on 2012-12-14
I first install vainfo from the "regular" repos and it may have pulled in vaapi with it. After that installed, I started using the xorg-edgers PPA and grabbed all the updates. I'm not sure if maybe I should reinstall them now or if it would have grabbed updates and applied them after the fact.

The built in tests for HD content from the wizard plays fine. I have more an issue with live TV (recorded is good as well). I have three tuners so doing picture in picture is a no-go at the moment. I'm assuming that is video card related (but maybe it just doesn't work right?)

---

### Post by BicyclerBoy on 2012-12-14
MythTV won't use va-api unless it is set in FE/setup/TV settings/playback/video-profiles.

Note you have to use openGL painter with va-api.

You have no shortage of CPU processing power for decoding additional stream, I don't know if MythTV can do pic-in-pic with VA-API.
But if you are using openGL decode now then pic-in-pic should be working.

---

### Post by splg on 2012-12-17
When I try to select VAAPI from the setup wizard I get an error that it can't use it (the test SD and HD video clips also fail to play)

I have made sure I installed:
libdrm-intel1
libva1
libva-intel-vaapi-driver
gstreamer0.10-vaapi
vainfo

Not sure why but maybe if I could use VAAPI, my performance would be better. Is there another package I should install? Currently the display wizard is set to "Normal".

---

### Post by BicyclerBoy on 2012-12-18
Run in a terminal:
glxinfo | grep -i opengl
vainfo

---

### Post by splg on 2012-12-18
I needed to install mesa-utils (since glxinfo wasn't there either) I restarted after doing the install and all updates but VAAPI setting in the wizard still didn't work but I'm using OpenGL High quality as a fallback. (The error was something like failed to initialize video)

```

# glxinfo |grep -i opengl
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Desktop 
OpenGL version string: 3.0 Mesa 9.1-devel
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:


# vainfo 
libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Intel i965 driver - 1.0.15
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileH264Baseline           :	VAEntrypointVLD
      VAProfileH264Baseline           :	VAEntrypointEncSlice
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointEncSlice
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointEncSlice
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

```

---

### Post by nickrout on 2012-12-18
> **splg said:**
> (The error was something like failed to initialize video)

Precise answers and analysis require precise questions. Please post the EXACT error. It is easy enough to cut and paste from the log file.

---

### Post by BicyclerBoy on 2012-12-18
It might be better to test VA-API with VLC or mplayer..but start them from a terminal so we see some logging.

---

### Post by splg on 2012-12-19
Sorry for the lack of error. This is what I get when trying to use VLC with an mpeg file:

```
VLC media player 2.0.3 Twoflower (revision 2.0.2-93-g77aa89e)
[0xfbc108] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvbpsi error (PSI decoder): TS discontinuity (received 7, expected 0) for PID 0
libdvbpsi error (PSI decoder): TS discontinuity (received 1, expected 0) for PID 49
QGtkStyle was unable to detect the current GTK+ theme.
libdvbpsi error (PSI decoder): TS discontinuity (received 7, expected 0) for PID 0
libdvbpsi error (PSI decoder): TS discontinuity (received 1, expected 0) for PID 49
libdvbpsi error (PSI decoder): TS discontinuity (received 6, expected 2) for PID 49
libdvbpsi error (PSI decoder): TS discontinuity (received 14, expected 8) for PID 0
libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva: va_openDriver() returns 0
[0x7fa254c955b8] avcodec decoder: Using VA API version 0.32 for hardware decoding.

```


This is the mythfrontend output when running the wizard and selecting vaapi and choosing the HD test video
```
libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva: va_openDriver() returns 0
2012-12-19 18:35:49.268504 I  VAAPI: Version: 0.32
2012-12-19 18:35:49.268509 I  VAAPI: Driver : Intel i965 driver - 1.0.15
2012-12-19 18:35:49.268525 I  VAAPI: Profile: MPEG2Simple Entrypoints: VLD 
2012-12-19 18:35:49.268528 I  VAAPI: Profile: MPEG2Main Entrypoints: VLD 
2012-12-19 18:35:49.268532 I  VAAPI: Profile: H264Base Entrypoints: VLD EncSlice (UNSUPPORTED) 
2012-12-19 18:35:49.268535 I  VAAPI: Profile: H264Main Entrypoints: VLD EncSlice (UNSUPPORTED) 
2012-12-19 18:35:49.268537 I  VAAPI: Profile: H264High Entrypoints: VLD EncSlice (UNSUPPORTED) 
2012-12-19 18:35:49.268540 I  VAAPI: Profile: VC1Simple Entrypoints: VLD 
2012-12-19 18:35:49.268542 I  VAAPI: Profile: VC1Main Entrypoints: VLD 
2012-12-19 18:35:49.268544 I  VAAPI: Profile: VC1Advanced Entrypoints: VLD 
2012-12-19 18:35:49.268552 I  VideoOutput: CalcHueBase(Intel i965 driver - 1.0.15): Unknown adaptor, hue may be wrong.
2012-12-19 18:35:49.268554 I  VideoOutput: Please open a ticket if you need to adjust the hue.
2012-12-19 18:35:49.268866 I  AFD: Opened codec 0x5689460, id(H264) type(Video)
2012-12-19 18:35:49.268872 I  AFD: codec AAC has 2 channels
2012-12-19 18:35:49.269552 I  AFD: Opened codec 0x5689880, id(AAC) type(Audio)
2012-12-19 18:35:49.269564 I  AFD: codec AC3 has 6 channels
2012-12-19 18:35:49.269715 I  AFD: Opened codec 0x5697f80, id(AC3) type(Audio)
2012-12-19 18:35:49.273246 I  AO: Opening audio device 'hdmi:CARD=PCH,DEV=0' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2012-12-19 18:35:49.274161 E  ALSA: Requested 500000us got 341333 buffer time
2012-12-19 18:35:49.274225 E  ALSA: Try to manually increase audio buffer with: echo 128 | sudo tee /proc/asound/card0/pcm3p/sub0/prealloc
2012-12-19 18:35:49.329151 W  OpenGL: Could not determine whether Sync to VBlank is enabled.
2012-12-19 18:35:49.866378 I  OpenGL1: Fragment program support available
2012-12-19 18:35:49.866429 I  OpenGL: OpenGL vendor  : Intel Open Source Technology Center
2012-12-19 18:35:49.866436 I  OpenGL: OpenGL renderer: Mesa DRI Intel(R) Ivybridge Desktop 
2012-12-19 18:35:49.866439 I  OpenGL: OpenGL version : 3.0 Mesa 9.1-devel
2012-12-19 18:35:49.866444 I  OpenGL: Max texture size: 8192 x 8192
2012-12-19 18:35:49.866447 I  OpenGL: Max texture units: 8
2012-12-19 18:35:49.866457 I  OpenGL: Direct rendering: Yes
2012-12-19 18:35:49.866459 I  OpenGL: PixelBufferObject support available
2012-12-19 18:35:49.866461 I  OpenGL: Initialised MythRenderOpenGL
2012-12-19 18:35:49.866485 I  VidOutGL: Created MythRenderOpenGL device.
2012-12-19 18:35:49.945208 I  OpenGL painter using existing OpenGL context.
2012-12-19 18:35:49.945214 I  OpenGL painter using existing QGLWidget.
2012-12-19 18:35:49.989419 I  GLVid: Using raw RGBA input textures.
2012-12-19 18:35:49.990544 E  VAAPI: Invalid display
2012-12-19 18:35:49.990548 E  VidOutGLVAAPI: Failed to create VAAPI context.
2012-12-19 18:35:49.992835 I  Clearing OpenGL painter cache.
2012-12-19 18:35:49.992861 I  OpenGL1: Deleting OpenGL Resources
2012-12-19 18:35:49.992872 I  OpenGL: Deleting OpenGL Resources
2012-12-19 18:35:49.993702 E  VideoOutput: Not compiled with any useable video output method.
2012-12-19 18:35:49.993715 E  Player(0): Couldn't create VideoOutput instance. Exiting..
2012-12-19 18:35:50.011576 E  Player(0): Unable to initialize video.
2012-12-19 18:36:10.055982 E  playCtx: StartPlaying() Failed to start player
2012-12-19 18:36:10.057254 I  TV: Main UI disabled.
2012-12-19 18:36:10.057270 I  TV: Entering main playback loop.
2012-12-19 18:36:10.059104 I  TV: Exiting main playback loop.
2012-12-19 18:36:10.086246 N  Resuming idle timer
```

---

### Post by BicyclerBoy on 2012-12-20
If the VLC (with vaapi) playback test was successful then the problem must be with mythtv.

I'm not sure if the mythtv errors means that mythtv is:
- complied without VAAPI support
- incompatible with later intel driver.

Do you compile mythtv from source ?
Can you determine the build options ?

From freedesktop.org 5th Oct 2012: 

"VA-API was bumped to 0.33.0, while libva still supports VA drivers
compiled for 0.32.x API."

This is just speculation but the above quote does not imply that the opposite is true..
Shame that xorg-edgers does not provide libva for all distro releases..

---

### Post by splg on 2013-01-19
Hello all, 

After a long break due to the holidays, a mess up somewhere within my mythtv setup and the integrated video issues, I've had to format and start over. For some reason my live tv broke and refused to work. 

As such, I took that time to step back, buy an nvidia 630GT card and install mythbuntu 12.04.1. I've done all the updates and upgraded to Mythtv 0.26. Now playing TV or DVD's from this newly reconfigured machine, Stereo sound is working. The really sad part is that my surround 5.1 audio is still not working. I was really hoping that the 630GT would solve the issues but I was wrong. 

So far I installed nvidia-current-updates and nvidia settings via aptitude. aplay -L shows:

```

null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default:CARD=PCH
    HDA Intel PCH, ALC892 Analog
    Default Audio Device
sysdefault:CARD=PCH
    HDA Intel PCH, ALC892 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Hardware device with all software conversions

```

I've tested with my AVR via command line and this works with 5.1:
 speaker-test -l 4 -c 6 -r 48000 -D hw:1,7

When the machine isn't playing media, the AVR shows "PLII C" but when I run the above speaker test it does show "Multi In". 

I've tried to change everything possible in VLC (the version that came with mythbuntu) and even DVD's that the XBOX shows as "Dolby" only play as stereo. VLC seems very flaky and when I change a setting and save it, I exit and restart it to ensure that it was applied. I've changed the setting for Dolby surround to ON, Use S/PDIF when available, and under ALSA set Audio Output channels to 5.1. To make matters stranger, forcing certain settings like all the Surround options, makes a quick chirping/static noise that is very loud. Further testing shows that if I keep all the force Dolby stuff on in VLC but disable the Use S/PDIF checkbox and play a DVD, the menu of the DVD with audio plays (as stereo) but when I choose the first chapter, the audio cuts out (no chirping). No matter how high the volume, there is no audio. If I skip to a few minutes forward or back, the AVR goes from PLII C, to Multi In for a brief second and I hear audio. But one second later, it cuts out and shows PLII C again but with no audio. 

I'm not sure what is missing here and how the Xbox will say it's a normal Dolby 5.1 DVD but when the Mythtv box plays it, will only show as stereo. (Even the Multi In mode, isn't good since that is some sort of upmixing from stereo to play the same stuff in all the speakers) 

I know there is a lot of information here but if you have any pointers now that I have additional hardware and have done the format/reinstall please let me know. Hope everyone had a good holiday.

---

### Post by BicyclerBoy on 2013-01-19
Sad you gave up on intel vaapi..
Just other day I tried an old i3 ironlake vaapi xorg-edgers & mythtv 0.26+fixes..
Played OTA TV at exactly half frame rate..
The unity desktop was much faster than old nvidia 9400GT.

Did you rescan audio devices (FE audio settings)?

Tick the audio codecs supported by your amp?
This might not be necessary because MythTV can now read/parse the EDID audio data.

"Multi-in" means discrete multi-channel PCM (over HDMI).
MythTV (& VLC XBMC) can output AC3/DTS 5.1 as bitstream (not decoded) or decoded as discrete multichannel (HDMI only).

I think I trust a good HT amp AVR decoders more than ffmpeg..mind you ffmpeg does not cost "an arm & a leg"..

You can can configure MythTV to output AC3/DTS/DTS-MA/E-AC3 directly to your amp..

---

### Post by splg on 2013-01-21
Yeah, I did give up (in hopes of making things easier) but really I'm right back where I started! I went through the FE audio setup again and ticked all the boxes since my AVR supports them all, hit rescan, did the speaker test on all of them and think the most appropriate choice is:

hw:CARD=NVidia,DEV=7

I ran the test from CLI with: speaker-test -Dhw:CARD=NVidia,DEV=7 -c6 and got the normal 5.1 output and the AVR showed the "Multi In". Everything seems good but TV recordings that show they should be 5.1 only come through as 2.0. That is why I was testing with VLC and a DVD as previously suggested and can confirm that that doesn't work either. (Of course, if I skip ahead in VLC, the AVR mode switches for a second to Multi In, I hear the audio from all channels and then POOF, the mode on the AVR switches and audio is lost)

Since I started fresh and have a new install, what packages would you recommend to ensure all the proper drivers/software is loaded? Again I'm using mythbuntu 12.04.1 with latest updates. I feel as though there is some setting in mythbuntu itself I'm missing. Clearly the audio can come through, just seems like it's misconfigured at this point. Thanks so far for the help, I know this one is very strange.

---

### Post by BicyclerBoy on 2013-01-22
AFAIK MythTV 0.26 (&0.25) enumerates the nVidia pin codecs 3,7-9 as [0 - 3]..

So your correct device could/should be labelled:

"ALSA:hdmi:CARD=NVidia,DEV=1"

(it does on my lucid 10.04 mythtv 0.26+fixes alsa 1.0.26)

What is your speaker configuration set to ?

Maybe your HT amp is reporting the amp & TV/display audio ELD in a less common format that is confusing alsa/mythv. Onkyo was one brand causing problems.

---

### Post by splg on 2013-01-22
I've changed the audio device as you have stated above and was successful when running the audio test from the wizard. It didn't change the issues am having though. I was wondering about the updated ALSA version you have. I show my version is at 1.0.24. 

I've also played around with the HDMI setting on the AVR but that too doesn't change anything. It seems as though the proper signal is sent out for a brief second but then changes back. I'd assume it was an issue with the AVR except I've got a few different types of devices, media players, etc attached and they all work without a problem. And since I can't get VLC to work either, it seems very much a mythbuntu/ubuntu issue rather than a MythTV problem.

Anything else I should be checking?

---

### Post by BicyclerBoy on 2013-01-23
The mythtv dev who implemented the HDA HDMI audio stuff did recommend alsa 1.0.25 (from git only at the time).
I believe the ELD reporting only works properly from 1.0.25.
Hard to say if this has any impact on your issue.

I'm using alsa 1.0.26 (but not the kernel module) because problems with couple of alsa-plugins.
Updating the user space code is actually quite straightforward.
A very useful trick was finding a one-line patch to avoid the 1GB xml bloatware dependency.

*buntu 12.04 has been using alsa 1.0.25 since Feb 2012 (before release)..don't know why mythbuntu 12.04 should indicate alsa 1.0.24..

A easy kernel module upgrade (dkms) that does not break with kernel updates is:
[https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages)

VLC (old version) & AC3 output:
Use advanced settings..
Set "Use S/PDIF when available"
Don't set "Force detection of dolby surround"..this is just fake prologic nonsense.
Set the alsa Device name to " HDA NVidia HDMI (hw:1,7)"

Play a DVD & then select "Audio Track" to be AC3 or DTS.

Don't set audio output device to be "alsa surround5.1", the default setting of this is an discrete analogue output.

---

### Post by splg on 2013-01-29
I'm not sure how or what I did (I was trying so many different things) from settings in mythtv, playing with the receiver and installing/uninstalling nvidia* drivers, something finally worked. I think I'm currently using the experimental 310 drivers. I kept trying different things and rebooting until my surround was working!

I wanted to thank you BicyclerBoy and the rest of the people who helped me here! Without the advise here, I wouldn't have gotten this working!!

---

### Post by daone on 2013-02-16
Curious if you have tried this hard ware with an other operating system? Wondering if this is a Mythtv problem or just an driver problem why you can't get audio from HDMI. Have found the Audio setup in Mythtv 0.25 Front End to be very helpful in selecting correct audio device. Can only ask if you have tried the obvious in Audio setup and selected scan for hardware and tried the audio channel test on every single device detected by mythtv? 

Also, have you chosen the audio test on the stereo setting? Or have you tried the test on 5.1 channels. I experienced the problem of the no audio if I tried the channel test on the wrong number speakers on my television speakers. My 60" Panasonic television will only output stereo, so if I tried the mythtv audio channel test in 5.1, I would get no sound.

---

