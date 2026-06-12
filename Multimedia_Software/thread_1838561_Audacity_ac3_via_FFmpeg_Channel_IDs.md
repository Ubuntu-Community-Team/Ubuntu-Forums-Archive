---
title: "Audacity ac3 via FFmpeg Channel IDs"
date: 2011-09-03
forum: Multimedia Software
---

### Post by olivero1 on 2011-09-03
I have searched for help on how Audacity with FFmpeg Channel's are mapped for ac3. So I created a sample ac3 file just to find out what it is. What follows are my notes (screen-shots) of what I have discovered, and how to set it up (future reference):)

First you must have Audacity installed with the FFmpeg codecs. I am not going into detail on this because all you have to do is search this forum for directions.

Once you have Audacity installed you must enable "Advanced Mixing Options":
**Edit/Preferences/Import/Export** *(refer to Screenshot.png)*

Using Audacity, create a recording with 6 MONO tracks. Label each as highlighted in the *Screenshot-Audacity.png* image. Of course you can use any name you wish, but I have found that having the Channel ID then the speaker ID useful for debugging the audio when something goes wrong.

Once you are finished with the audio and the desired recording is ready to complete. Export the file [File/Export]. *See screenshot-Export File.png* and select ac3 from the selection box. Be sure to include a filename for the audio!

Then assign the audio tracks to the proper channels. *See Screenshot-Advanced Mixing Options.png*. Once you have the connections established, click OK.

Now test it with VLC or your player of choice (assuming you have 5.1 playback on your PC) and verify that the audio is good and presented in the way you want it.

If everything is good, then utilize the ac3 file for whatever you want.

Enjoy!:popcorn:

Let me know how it works out and if I have made any errors.

Here is the Channel ID in text form:

> Channel 1 = Left
Channel 2 = Center
Channel 3 = Right
Channel 4 = Left Surround
Channel 5 = Right Surround
Channel 6 = LFE

And as a BONUS :P Dolby Channel Identification & Common Amp color schemes:
> 0 = Center/Green
1 = Front Left/White
2 = Front Right/Red
3 = Surround Left/Blue
4 = Surround Right/Grey
5 = LFE/Purple
6 = Surround Back Left/Brown
7 = Surround Back Right/Khaki

---

### Post by BicyclerBoy on 2011-09-04
A good test track
www_lynnemusic_com_surround_test.ac3
You can play direct to amp to check (VLC)

The A52/AC3 channel order from ffmpeg
 ac3tab.h
```

00054 enum CustomChannelMapLocation{
00055     AC3_CHMAP_L=        1<<(15-0),
00056     AC3_CHMAP_C=        1<<(15-1),
00057     AC3_CHMAP_R=        1<<(15-2),
00058     AC3_CHMAP_L_SUR=    1<<(15-3),
00059     AC3_CHMAP_R_SUR =   1<<(15-4),
00060     AC3_CHMAP_C_SUR=    1<<(15-7),
00061     AC3_CHMAP_LFE =     1<<(15-15)

```
This order is SMPTE.

Hopefully the Audacity folks have this sorted..there are many posts on various websites about the incorrect order of transcoded AC3 audio.

If I use ffmpeg directly to encode AC3, first the channel order must be corrected.

This should be invisible to the user but FYI.
The ffmpeg AC3 encoder has channel order options as a input parameter.
The best I can determine the internal order inside ffmpeg is non-std e.g.5.1 ch order
L, R, C, Ls, Rs, LFE

Alsa is non-std
L, R, Ls, Rs, Centre, LFE

---

### Post by abitks on 2012-03-29
First of all. Big thanks for this guide. It gave me hope that (greeeeat tool) Audacity  can export directly into ChannelMix. This is more than expected for me because it fully supports codecpack and libavcodecs library (which includes ac3dec), but i just didnt know where to check that radio button. (imh toobad that Audacity default is export to single mono)

Second and most important. If I'm remap channel as you list them in you post i'll get strange clipping because most of current decoders (ex.LAVFilter) andtheir decoding matrix require channel ordered as below. I refer to proper channel order that could be easily checked in MPC-HC->(right button menu) Filters->LAV Audio Decoder->[Status] tab (L R C LFE BL BR - -)

```
Channel 1 = Left
Channel 2 = Right
Channel 3 = Center
Channel 4 = LFE
Channel 5 = Left Surround
Channel 6 = Right Surround
```

You might wonder why the heck i use this detour when i have readily available *eac3to* tool with *libAften* support. Well, it's because libAften introduces some nasty lowpass filter opposing to *libav* which is somewhat slower (4x-6x) but doing proper job without anykind of filtering. And doesnt require 2pass when clipping is occurred (in fact there's no clipping just the fact that libAften-eac3to is devoted to get the job done in its own manner).

---

