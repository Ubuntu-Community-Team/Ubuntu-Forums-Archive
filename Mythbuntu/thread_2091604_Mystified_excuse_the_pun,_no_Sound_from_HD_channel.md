---
title: "Mystified? excuse the pun, no Sound from HD channels"
date: 2012-12-05
forum: Mythbuntu
---

### Post by drifting on 2012-12-05
Hi chaps.

I am a little confused. I am in the UK and have a number of HD channels that are received via DVB-S2, and a number of other channels from the same card are in Standard Def.

The odd thing is that the Sound from HD is working on the server itself, via the frontend I use for testing. All my slave machines (Acer revo) will give sound on standard channels, but none on HD?
The revo's are connected via HDMI to the TV's. 

This all worked fine till I bit the bullet and went from 11.04 to 12.04 and from .24 to .26 have passed briefly through .25 of Myth.

Suggestions?

Regards Paul.

---

### Post by jksj on 2012-12-06
HD broadcasts in the UK are MPEG-4 H.264/AVC where SD broadcasts are MPEG-2.
Freesat broadcasts both standards, so your DVB-S2 card is passing both stream types to myth for decoding.
To make matters more interesting the HD audio stream can switch dynamically between stereo and surround sound signals. There are also multiple audio streams within the HD signal. See [http://www.freeview.co.uk/Resolutions/About-Freeview-HD/Can-I-get-5.1-surround-sound-with-Freeview-HD](http://www.freeview.co.uk/Resolutions/About-Freeview-HD/Can-I-get-5.1-surround-sound-with-Freeview-HD).

So when watching SD broadcasts a simple stereo signal is sent out. For HD the decoder has to deal with a more complex stream.
The problem should be resolvable by re-scanning the audio hardware in mythfrontend audio setup and using the test facility to check the interface is working. If I remember correctly, mythtv cannot automatically determine the audio parameters of the ion 1 chip on the Acer Revo so you may have to try out the various combinations manually.
Are you using HDMI or analogue out?

---

### Post by drifting on 2012-12-06
Thanks for the reply.

I am using HDMI. Did not think of re scanning, just set it to what it was on previous versions, worked ok up till now. But thanks for the advice.

Just really threw me that analogue playback machines were fine, those with HDMI worked fine except for any HD channels, then just got cracking audio.

Regards Paul

---

### Post by jksj on 2012-12-06
I  used to have an Acer Revo but have recently moved to an Ion 2 based system. I remember that I had to set -    	 	 	 	in advanced audio settings - Stereo PCM only. Otherwise the HDMI interface did not work properly. Note this does not stop surround sound working it just overcomes a problem in the Ion HDMI interface.
Hope this is of some use - best of luck.

---

### Post by drifting on 2012-12-07
Thanks for all the advice.
I have found a setting that gives audio in both standard and high def, however unlike how it used to be set, which had the work HDMI in it, this time it just says hware? Also noticed that the audio level is much quieter on tv than via mythmusic, or mythvideo. I did not need the PCM option set, seemed to make little difference. Hopefully I will have time this weekend to mess with all options.

Regards Paul

---

### Post by BicyclerBoy on 2012-12-08
The ION (& earlier) HDMI HDA audio do not support ELD audio capability reporting & alsa assumes full capability in the receiver (8x192KHz & DTS-MA etc).

I'm not sure how but it is possible to fake the ELD info for alsa but it is easier to limit MythTV audio output to channels/codec formats/sample rates that your receiver/TV/display can handle.

Might find forcing 48KHz sample rate (MythTV audio/advanced audio settings?) allows it to work..

You are using nVidia proprietary driver ?

---

### Post by drifting on 2012-12-12
Bicyclerboy

Yes I am using Mythbuntu with the Nvidia proprietary driver. 
As I say, I seem to have it working, but the audio level difference is quite large between mythmusic / TV / and especially HD recordings, the HD being the quietest of them all. Will try your suggestion, but wished I had made a note as to what they were set previously.

---

### Post by BicyclerBoy on 2012-12-12
I find that PCM stereo is louder than AC3 5.1 audio (all digital out & decoded in HT amp) by about 3dB. I get more variation channel to channel.

The industry std recording levels on CDs are too high, I believe this occurred for marketing reasons.

My "Videos" are mostly cut TV recordings & play exactly same as original.

Can't face mythmusic..it does not even play an album in the right order.
It is a lot to ask to compete with the likes of Clementine but there are many good music player UIs to copy/compare.

---

### Post by jksj on 2012-12-13
HD audio has a higher dynamic range than SD.  Which makes SD generally sound louder although the max volume will be the same in both cases. This is pretty irritating when changing channels but is worth living with due to the improved quality in HD. If it really annoys most amplifiers will compress the range down, on my Onkyo receiver it is called a 'Late Night Function'.
[http://en.wikipedia.org/wiki/Dynamic_range_compression](http://en.wikipedia.org/wiki/Dynamic_range_compression)

---

### Post by BicyclerBoy on 2012-12-13
DTS music soundtracks can be even quieter..they are meant to be original concert equivalent volume at 0dB.

@jksj
Did you get AC3 & DTS to bitstream to amp over S/PDIF or HDMI ?

The OP might be using stereo PCM out for multi-channel & then the volume levels are effected by the MythTV down-mix weighting matrix.

The down-mix has to be setup to prevent clipping when "summing" 5.1 into 2 channels.

So on same channel with AC3-5.1 & AAC stereo a news programme, with mostly FR FL, AC3 sounds quieter than stereo track.

A minor points: 
HD OTA TV broadcasts are not HDA.
AC3-5.1 is not HD audio. OTA bitrate is 1/2 1/3 of max supported by AC3.
AAC at a higher enough bitrate etc could be near HDA but it is not used that way.
mpeg2 audio is better than mp3 except for compression.

---

### Post by drifting on 2012-12-15
Thanks for the very informative post, I knew none of that. Going to go so far as to print this out and mess around with the settings. Sadly until I sort out the picture size (Overscan, I think?) Some of the options are hidden. Should not complain, was using .23 on 4 tv's without an issue for quite a few years.
Thanks again Bicyclerboy.

Regards Paul

---

### Post by BicyclerBoy on 2012-12-15
If you have overscan issues & just need to see all the buttons & tickboxes can start mythfrontend with:
mythfrontend --geometry 1440x900
launch on 2nd X display:
mythfrontend -display :0.1 --geometry 1440x900
[http://www.mythtv.org/wiki/Override_settings](http://www.mythtv.org/wiki/Override_settings)

The FE has a setting that allows GUI & video playback to be diff video modes or diff size (great for old CRTs).

With DFP TVs the ideal setup is direct pixel mapping.

The nVidia driver release from 310 (?) has temporarily removed the GUI overscan compensation gadget form nvidia-settings.
You have to use viewportin viewportout..
Does this help?
[http://ubuntuforums.org/showthread.php?t=2090914](http://ubuntuforums.org/showthread.php?t=2090914)

The GUI interface is planned to have this feature returned..

---

