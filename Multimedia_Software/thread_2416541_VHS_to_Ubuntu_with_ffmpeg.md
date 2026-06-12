---
title: "VHS to Ubuntu with ffmpeg"
date: 2019-04-11
forum: Multimedia Software
---

### Post by shantiq on 2019-04-11
====================[SIZE=1]*much of this info came from [here]("https://gordonlesti.com/digitize-a-vhs-tape-with-ffmpeg-and-easycap-on-linux/")*[/SIZE]===================

Always thought that digitizing VHS would be an expensive business
Turns out if you have a VCR in working order and £6/$8 or thereabouts for leads it is within anyone's reach
I also thought you probably needed complicated software
Turns out ffmpeg will do that for you with one click once you have entered the command

```
ffmpeg -f v4l2 -standard PAL -thread_queue_size 1024 -i /dev/video0 -f alsa -thread_queue_size 1024 -i hw:2,0  -c:v libx264  -s 720x576 -b:v 3000k -r 25 -aspect 4:3 -c:a flac -channels 2 -ar 48000 outfile.mkv
```

All you need to verify first is which audio stream [where it says hw:1,0] to enter in your commandline

You can find that out easily by running: 
```
cat /proc/asound/cards
```

in my case i get

```
 cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xdf220000 irq 130
 1 [Alpha          ]: USB-Audio - Lexicon Alpha
                      Lexicon Lexicon Alpha at usb-0000:00:14.0-5, full speed
 2 [CAMERA         ]: USB-Audio - USB2.0 PC CAMERA
                      ARKMICRO USB2.0 PC CAMERA at usb-0000:00:14.0-8.3, high speed
```
                      
                      
 So I pick hw:1,0   because I want the full PCM stream to go to flac
 
 If you want to use the usb converter sound [USB-Audio - USB2.0 PC CAMERA][it only goes to 320k] here you would pick hw:2,0   
 
 
 
**[SIZE=1]*  So If you have old tapes you would like on your computer; invest  £6/$8 and enjoy this old into reanimated experience  ...  *[/SIZE]**
 
 LEADS NEEDED ARE THESE  [you link &#10122; to &#10123; and plug usb into your computer]
 -----------------
 
&#10122;  1.5m Scart to 3 x Phono Cable IN OUT Switchable Triple RCA Composite Lead Switch 

Set to Out obviously  

&#10123; USB 2.0 Audio VHS to DVD Converter Capture Recorder Analog Video to Digital

see pix below :

[[IMG]https://i.postimg.cc/vxtSz9Px/IMG-5772.jpg[/IMG]]("https://postimg.cc/vxtSz9Px")[[IMG]https://i.postimg.cc/r0JPGxZ0/IMG-5775.jpg[/IMG]]("https://postimg.cc/r0JPGxZ0")[[IMG]https://i.postimg.cc/HjYKYvjQ/IMG-5774.jpg[/IMG] ]("https://postimg.cc/HjYKYvjQ")
[[IMG]https://i.postimg.cc/jCRVWd3n/IMG-5773.jpg[/IMG]]("https://postimg.cc/jCRVWd3n")



PS :: Once you have ripped the file were you to encounter an av sync problem use this as post-processing  [very good advice here]("http://ffmpeg -i originalfile.mkv -itsoffset 0.3 -i original.mkv -map 0:0 -map 1:1-acodec copy -vcodec copy synced.mkv")


```
 ffmpeg -i originalfile.mkv -itsoffset 0.3 -i original.mkv -map 0:0 -map 1:1  -acodec copy -vcodec copy synced.mkv
```

0.3 here stands for 0.3/s

PS2 :: If whilst doing tests at first you find the saturation is too high you can add this to original line

```
ffmpeg -f v4l2 -standard PAL -thread_queue_size 1024 -i /dev/video0 -f alsa -thread_queue_size 1024 -i hw:1,0  -c:v libx264  -s 720x576 -b:v 2400k [COLOR=#800000]*-vf eq=saturation=0.5*[/COLOR] -r 25 -aspect 4:3 -c:a flac -channels 2 -ar 48000   outfile.mkv
```

1.0 being full saturation

---

