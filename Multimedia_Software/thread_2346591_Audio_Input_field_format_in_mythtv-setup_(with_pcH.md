---
title: "Audio Input field format in mythtv-setup (with pcHDTV HD-5500 S-video input)"
date: 2016-12-16
forum: Multimedia Software
---

### Post by noscgag on 2016-12-16
Background: I have a DirectTV receiver that has an S-video output (not HD) that I hooked up to an HVR-1950. For audio I use RCA cables from the STB to the HVR-1950. I also record HD over-the-air with this tuner. Additionally, I have a pcHDTV HD-5500 for OTA HD. I could record OTA HD programs on either the HVR-1950 or the HD-5500 (simultaneously), or standard video from the satellite using the HVR-1950.

This setup was working fine until a couple days ago when the HVR-1950 stopped working. I decided fine, I'll remove the HVR-1950 and use the S-video input on the HD-5500. I went into mythtv-setup, removed the HVR-1950 capture card, installed the HD-5500 as an Analog V4L card on /dev/video0, put it in the same recording group as the DVB part of the HD-5500 (so it wouldn't try to use the card to record to shows at the same time), and set the Audio Input to "ALSA:default".

The good news is the HD part of the HD-5500 still works (audio and video), and the video from the analog part of the HD-5500 works fine. The bad news is the audio from the satellite doesn't come through.

I've tried several different setups and looked any many posts dealing with this issue, but haven't been able to figure out why mine doesn't work.

The first setup was to plug the audio output from the STB into the audio jack of the HD-5500. This was done through a cable that converts the RCA connectors from the STB to the 1/8" plug required by the HD-5500. With this setup, and the Audio Input on the Input Connections screen of mythtv-setup set to "ALSA:default" I get white noise audio. I checked the mythbackend.log and it shows no errors.

Looking at some other posts ([https://beckustech.wordpress.com/2012/02/27/setting-up-a-home-server-with-ubuntu-11-10-part-2-mythtv/](https://beckustech.wordpress.com/2012/02/27/setting-up-a-home-server-with-ubuntu-11-10-part-2-mythtv/) and [https://www.mythtv.org/wiki/PCI_TV_audio](https://www.mythtv.org/wiki/PCI_TV_audio)), it looks like the audio input should be set to something like "ALSA:hw:1,0", or possibly "ALSA:plughw:1,0" (sorry about the smiley, I could figure out how to get rid of it, that should be A-L-S-A-:-p-l-u-g-h-w). These both result in no audio at all, and an error in the backend log like "(AlsaBad) AudioInALSA(plughw:1,0): pcm open failed: Device or resource busy".

So, I thought I'd try using the line-in jack on my regular sound card instead of the one on the HD-5500, using "hw:0,0", but that also results in a "pcm open failed" message in the backend.

I wanted to make sure this would work outside of mythtv so I used mplayer to display the video and audio using this command line (with the audio going to the line-in jack rather than the HD-5500):

```
sudo mplayer tv:// -tv driver=v4l2:device=/dev/video0:input=2:alsa=1:adevice=plughw.0,0:amode=2:audiorate=48000:forceaudio:immediatemode=0
```

This works: I see the video and I get the corresponding audio. So it seems like using the main soundcard's line-in jack should work.

I wanted to see if I could get mplayer to use the audio input on the HD-5500. so I substituted "1,0" for "0,0" in the above line, switched the audio plug from the STB to the jack on the HD-5500, and mplayer complains that it's not a pcm device (sorry, don't have the actual text").

I have seen several posts that say you have to set the audio sample rate to 48000 in the "Recording Options" section as well as in the playback groups (I think this is what it's called, it's in one the mythtv-setup groups). I have also checked the "Open DVB card on demand&#8221; and unchecked the &#8220;Use DVB card for active EIT scan&#8221; for the DVB part of the HD-5500 (while these settings are needed, I don't think they're relevant for the problem I'm having).

My system details:
mythbackend version: fixes/0.27 [v0.27-193-g8ee257c] [http://www.mythtv.org]("http://www.mythtv.org/")

Output from "arecord -l" to list all the sound recording devices:
```
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC888 Alt Analog [ALC888 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CX8801 [Conexant CX8801], device 0: CX88 Digital [CX88 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
Similar output from "cat /proc/asound/cards":
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd2120000 irq 30
 1 [CX8801         ]: CX88x - Conexant CX8801
                      Conexant CX8801 at 0xd5000000
```
Relevant portions of the mythbackend.log:
```
Dec 16 05:31:56 mythtv mythbackend: mythbackend[11330]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange) TVRec[13]: Changing from None to WatchingLiveTV
Dec 16 05:31:56 mythtv mythbackend: mythbackend[11330]: I TVRecEvent tv_rec.cpp:3602 (TuningCheckForHWChange) TVRec[13]: HW Tuner: 13->13
Dec 16 05:31:56 mythtv mythbackend: mythbackend[11330]: I TVRecEvent recorders/v4lchannel.cpp:558 (SetInputAndFormat) V4LChannel[13](/dev/video0): SetInputAndFormat(8, NTSC) (v4l v2) input_switch: 0 mode_switch: 1
Dec 16 05:31:56 mythtv mythbackend: mythbackend[11330]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
Dec 16 05:31:59 mythtv mythbackend: mythbackend[11330]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
Dec 16 05:31:59 mythtv mythbackend: mythbackend[11330]: E TVRecEvent recorders/audioinputalsa.cpp:336 (AlsaBad) AudioInALSA(plughw:0,0): pcm open failed: Device or resource busy
Dec 16 05:31:59 mythtv mythbackend: mythbackend[11330]: E TVRecEvent recorders/NuppelVideoRecorder.cpp:771 (AudioInit) NVR(/dev/video0): Failed to open audio device ALSA:plughw:0,0
Dec 16 05:31:59 mythtv mythbackend: mythbackend[11330]: E TVRecEvent recorders/NuppelVideoRecorder.cpp:699 (Initialize) NVR(/dev/video0): Failed to init audio input device
Dec 16 05:32:00 mythtv mythbackend: mythbackend[11330]: E NVRAudio recorders/audioinputalsa.cpp:336 (AlsaBad) AudioInALSA(plughw:0,0): pcm open failed: Device or resource busy
Dec 16 05:32:00 mythtv mythbackend: mythbackend[11330]: E NVRAudio recorders/NuppelVideoRecorder.cpp:2387 (doAudioThread) NVR(/dev/video0): Failed to open audio device ALSA:plughw:0,0
Dec 16 05:32:23 mythtv mythbackend: mythbackend[11330]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange) TVRec[13]: Changing from WatchingLiveTV to None
```
I think my main problem is that I'm not entering the "ALSA" information correctly in mythtv-setup, but I can't find a definitive reference for the format. The frontend setup also has an audio section (for output, not input), and the format there seems to be different (e.g. ALSA:CARD=CX8801,DEV=0), though I have tried that too and it says it can't open that either.

Any help would be much appreciated.

---

### Post by noscgag on 2016-12-17
Solved!

I was unable to use the analog input from the HD-5500. From what alsamixer shows me, it has an "Analog-TV" "Playback" (output), an "Audio-Out" toggle (on/off), and an "Analog-TV" "Capture" (input). If I connect the audio output from my STB to the input jack on the HD-5500, then connect the 3.5mm plug from the HD-5500 cable to the computer's regular Line-In jack, I either (a) get the STB audio mixed with noise, or (b) get just the STB audio. To get rid of the noise I used alsamixer to mute the "Audio-Out" setting by typing 'm'. There didn't seem to be any reason to try piping the audio from the STB through the HD-5500 to the Line-In jack, since all it did was pass it through or add noise.

I also tried getting the audio directly from the HD-5500 by connecting the STB to the HD-5500's input jack and setting the "Audio device" setting in mythtv-setup's Capture card to "ALSA:hw:1,0", but this either resulted in white noise or no sound, depending on whether I had muted the "Audio-Out" setting in alsamixer. 

So I gave up on the HD-5500 for getting audio. This meant I had to capture audio from the STB with the regular sound card. For me, this is an Intel HDA, which has the ALC888 hardware. I thought this would just be a matter of plugging the STB output into in the the computer's Line-In jack on the back and setting the "Audio device" for the capture card in mythtv-setup to the correct device.

The first roadblock was that the sound from the STB was *always* coming out of the TV's speakers, which would be really annoying unless you were watching live TV. I eventually discovered the "Loopback Mix" setting in alsamixer. My terminal screen wasn't wide enough to display it and I didn't realize if you kept hitting the right-arrow key that the display would scroll sideways to reveal more controls. Once I found Loopback Mix on the far right side of the display and disabled it, that prevented the Line-In audio from always playing on the TV speakers.

The next problem was that the only audio input I could get to record was the default, which for my system is hw:0,0. From my previous post you can see that this is card 0 (Intel), device 0. I was able to record audio from the STB using the command:
```
arecord -d 10 -f dat -t wav -v -v -D hw:0,0 a.wav
```
This records 10 seconds (-d 10) of audio at a sample rate of 48000 (-f dat) in the WAV format (-t wav), showing PCM details and a VU meter (-v -v), from the PCM card 0 device 0 (hw:0,0), outputting to the "a.wav" file. The VU meter was nice because I could immediately tell whether I was recording audio or not.

So I went back to "mythtv-setup --> Capture cards --> [V4L:/dev/video0] --> Audio device" and set it to "ALSA:hw:0,0". Unfortunately, when I tried to Watch TV in mythtv, the mythbackend log reported "Failed to open audio device ALSA:hw:0,0". Changing "hw" to "plughw" didn't help. My guess is that the myth frontend already has this device open for audio output that prevents the backend from opening it for audio input. At one point I tried running the arecord command above while running the frontend and it failed until I exited the frontend (but I can't replicate that now, so I'm not sure).

So, since hw:0,0 didn't work, I needed to find a different device. Referring back to the output from "arecord -l" you can see that the Intel card has a second device, 2, called "ALC888 Alt Analog" (device 0 is called "ALC888 Analog"). So, going back to the "Audio device" setting in mythtv-setup I changed it to "ALSA:hw:0,2", restarted the backend and frontend and tried to Watch TV. As usual, I got video but no audio, but this time the backend log did NOT say it failed to open audio device (it didn't indicate success either), so, now if I could just figure out how to get audio to device 2 I might have something that works.

I could not find *any* information on "Alt Analog"; not in Intel's docs on the HDA, not in Realtek's ALC888 datasheet, not even on the Internet. However, I eventually ran across [https://www.alsa-project.org/main/index.php/Help_To_Debug_Intel_HDA](https://www.alsa-project.org/main/index.php/Help_To_Debug_Intel_HDA) , which says "On the "Capture" tab, you can change the capture source setting using the spacebar" (referring to alsamixer). So, back to alsamixer, switching to the "Capture" view I see two bars, one labeled "Capture" and the other labeled "Capture 1". I see that the "Capture" bar has the text "CAPTURE" right below the bar graph and that "Capture 1" just has "-------". So I move the selection over to the "Capture 1" bar and hit the SPACE bar, and now "CAPTURE" shows up for the "Capture 1" bar.

I now use the command
```
arecord -d 10 -f dat -t wav -v -v -D hw:0,2 a.wav
```
Nothing. No sound. So I go back to alsamixer again, and I see two more settings to the right of the "Capture 1" bar: "Input Source" and "Input Source 1". The former has the text "Line" above it while the latter has the text "Rear Mic". So, I use the up/down arrow keys to set this to "Line" for "Input Source 1".

I execute the arecord command again and the VU meter moves! I play the file and I have real audio! So, back to mythtv-setup and the Audio device setting, set it back to "ALSA:hw:0,2", exit, start the frontend, Watch TV, and....SOUND!

This took *so* much longer than I thought it would, but I am very happy to have finally figured it out.

---

