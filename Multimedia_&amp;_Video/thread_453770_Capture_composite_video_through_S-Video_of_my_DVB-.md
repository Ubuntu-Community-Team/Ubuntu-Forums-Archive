---
title: "Capture composite video through S-Video of my DVB-T card"
date: 2007-05-24
forum: Multimedia &amp; Video
---

### Post by agatha on 2007-05-24
Hi

I have converted from WinXP to Ubuntu (now Feisty) in the last 6 months and am still struggling with Linux.
I have a DVICO Fusion HDTV Plus DVB-T card with an analog/composit input socket (S-Video)

The TV side of the card works OK with Kaffeine, but I want my system to capture video through the S-Video socket.

There are two major problems:
1. I can't find software with a 'capture' option. Kino captures only via Firewire port, which is OK for my digicam. I have tried to use VLC, but can't configure it, because

2. I don't understand how to set it up to capture rather than record the tuner output.


All suggestions are extremely welcome.

Thanks in advance
Franz
PS: THis was all very simple in WinXP, because the DVICO software provided the capture option, sadly the DVICO software will not run under Linux, including wine.

---

### Post by R%&amp;92GH&amp; on 2007-06-24
I have exactly the same problem, I can see the tv using kaffeine under feisty, but I don't know how to make the composite and S-video ports working. My tv card is an AVerTV DVB-T 777.

I also tried xawtv and tvtime, with no success.

any suggestions?

thnx

---

### Post by david_2001 on 2007-06-24
Firstly, do you know what video device is assigned to your card?  If you only have one video card then it should be /dev/video0.  If so and you have tvtime installed then connect a video source to the S-Video input of the card and start tvtime as follows:
```
tvtime -d /dev/video0 -b /dev/vbi0
```
If the card is not attached to /dev/video0  then substitute the correct video device and matching vbi device.  If tvtime just comes up with a black screen then right click in the tvtime window, select "Input configuration" from the menu and then click on "Change video source" to switch between the possible inputs.

If the above worked, i.e. you got video (with no sound, of course, because these cards mostly don't have a sound input), then install xawtv.  The xawtv package includes v4lctl, which can be used to switch between card inputs.  Just to check that v4lctl works, confirm the inputs that are available with:
```
v4lctl -c /dev/video0 list
```
The output is going to be something like the following, though far neater because I've never found a way to get fixed space fonts to work in this forum:
> attribute  | type   | current | default | comment
-----------+--------+---------+---------+-------------------------------------
norm       | choice | PAL-BG  | NTSC-M  | NTSC-M NTSC-JP PAL-BG PAL-DK PAL-I PAL-M PAL-N PAL-Nc PAL-60 SECAM-L SECAM-DK
input      | choice | S-Video | Composi | Composite1 S-Video
audio mode | choice | mono    | mono    | mono stereo lang1 lang2
bright     | int    |     127 |     127 | range is 0 => 255
contrast   | int    |      63 |      63 | range is 0 => 255
color      | int    |     127 |     127 | range is 0 => 255
hue        | int    |     127 |     127 | range is 0 => 255
volume     | int    |      63 |      63 | range is 0 => 63
Balance    | int    |      64 |      64 | range is 0 => 127
mute       | bool   | on      | on
To set the video input to S-Video use:
```
v4lctl -c /dev/video0 setinput S-Video
```
All you need to do then is pick your capture software.  Mencoder and transcode are two possible options.  I prefer transcode because it never seems to have problems with audio/video synchronisation, unlike mencoder.  The command line that I use to capture video from vhs tapes to mjpeg format for editing/transcoding is:
```
transcode \
  -u 256,2 \
  -x v4l2=resync_margin=1:resync_interval=250:overrun_guard=1,v4l2 \
  -g 720x576 \
  --import_asr 2 \
  -i /dev/video0 \
  -H 0 \
  -p /dev/dsp2 \
  -e 32000,16,2 \
  -E 48000,16,2 \
  -N 0x2000 \
  -b 192 \
  -J resample,smartyuv,mask=lefttop=0x6:rightbot=720x564,hqdn3d=luma=4:chroma=3:
luma_strength=6:chroma_strength=4,pv=cache=30 \
  -y ffmpeg \
  -F mjpeg \
  -o outfile.avi

```

---

