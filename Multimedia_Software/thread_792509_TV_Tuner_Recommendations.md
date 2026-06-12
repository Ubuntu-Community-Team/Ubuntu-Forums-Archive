---
title: "TV Tuner Recommendations"
date: 2008-05-13
forum: Multimedia Software
---

### Post by MikeCheck on 2008-05-13
I am planning on buying a TV tuner card, but I have noticed quite a few problems posted on the forums.  Does anyone have any recommendations on which tuner cards work the best/easiest?
Also, what do I need to do to get it running properly?
I am running Hardy and I have an Nvidia graphics card.
Thanks.

---

### Post by sammiam on 2008-05-13
I too am looking for a TV  Tuner.  I see that it looks like Kworld Global TV terminator works, but am looking for recommendations...

---

### Post by hermes0710 on 2008-05-13
Pinnacle 310i was not that cool for both windows/linux. Their software sucks. Too slow and full of bugs... I still regret those stupid euros.

After installing hardy i have the card working fine (not checked dvb though) but i suggest you skip this model at least...

---

### Post by MeKino on 2008-05-13
I have successfully installed the Hauppauge pvr 150 tuner. For details follow this link...

[http://ubuntuforums.org/showthread.p...ighlight=wintv](http://ubuntuforums.org/showthread.p...ighlight=wintv)

---

### Post by MikeCheck on 2008-05-16
Also, will the remotes work as well?

---

### Post by MikeCheck on 2008-05-16
> **MeKino said:**
> I have successfully installed the Hauppauge pvr 150 tuner. For details follow this link...

[http://ubuntuforums.org/showthread.p...ighlight=wintv](http://ubuntuforums.org/showthread.p...ighlight=wintv)

That link doesn't work for me

---

### Post by MeKino on 2008-05-16
Sorry about the link - this one should be ok.


[http://ubuntuforums.org/showthread.php?t=758845](http://ubuntuforums.org/showthread.php?t=758845)

---

### Post by GhettoYhetti on 2008-05-17
Wow . . . no new words of wisdom since early last year?  

I am looking to get a TUNER and this doesn't look to be very promising.  Are you saying that the PVR150 works well with just the cable box?  Or does it do the "Cable Ready" magic?

---

### Post by MeKino on 2008-05-18
The PVR150 works just as well with any input - it just so happens that I use it this way. I don't know what "Cable Ready" magic is.

---

### Post by PJSingh5000 on 2008-05-30
I have not tried this myself, but at another forum, someone suggested that Hauppauge cards are supported well.  They said that the bt848/bt878 chipset based cards work the best.

---

### Post by wolfen69 on 2008-05-30
i use the Hauppauge pvr150 without problems. copy the following if you decide to get one.

I get  tv by: 

sudo apt-get install ivtv-utils 

open VLC player

File -> Open Capture Device -> PVR -> OK

then you can do (in terminal)

ivtv-tune -c25 (25 is channel number)

which changes the channel.

ivtv-tune -h

to see the options which control the card. 


for a cool desktop tv remote,(so you dont have to use terminal to change channels) go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

remember to have java installed first. then you can right click: open with java.

to record tv:

cat /dev/video0 > /tmp/name_of_file.mpg

it will record whatever channel you are on. then ctrl-c to stop.

---

### Post by Porpoise on 2008-07-06
Alternatively, you can use v4l2 to control the card (I use these methods personally):

The device setting (usually) for Hauppauge PVR-150:  /dev/video0:
```

v4l2-ctl --device=/dev/video0

```Then the standard (I'm in europe-west/PAL):
```

v4l2-ctl --set-standard=pal

```To select inputs:
```

v4l2-ctl --set-input=0    #for Tuner 1
v4l2-ctl --set-input=1    #S-Video 1
v4l2-ctl --set-input=2    #Composite 1
v4l2-ctl --set-input=3    #S-Video 2
v4l2-ctl --set-input=4    #Composite 2

```If using the Tuner as input, then to select channels:
```

v4l2-ctl -f 711.250    #Frequency: 11380 (711.250000 MHz) (BBC 1)
v4l2-ctl -f 655.250    #Frequency: 10484 (655.250000 MHz) (BBC 2)
v4l2-ctl -f 631.250    #Frequency: 10100 (631.250000 MHz) (ITV 1)
v4l2-ctl -f 679.250    #Frequency: 10868 (679.250000 MHz) (CHA 4)

```This method requires your default (PAL, SECAM, NTSC) and region settings to have previously been set (for which you can also use ivtv-tune as previously mentioned).
Further information and the various switches for v4l2-ctl can be found here: [http://ivtvdriver.org/index.php/V4l2-ctl](http://ivtvdriver.org/index.php/V4l2-ctl)

Obviously, if you are in a different location/using a different system, you will need to use the relevant frequencies.

Then, the VLC command-line to record:
```

vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1 --sout '#duplicate{dst=std{access=file,mux=ts,dst="/home/steve/Desktop/raid-partition/DVCR/filename.mpg"}}'

```Or, if you wish to view the stream whilst recording:
```

vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1 --sout '#duplicate{dst=display,dst=std{access=file,mux=ts,dst="/home/steve/Desktop/raid-partition/DVCR/filename.mpg"}}'

```
This method allows you to use the same command for capture irrespective of input/channel settings - you can set the input/channel individually without having to mess about editing the VLC command-line each time.

There is also a utility called TV-Viewer available which gives you a GUI for TV Channel switching

Hope this might be of help to someone.

---

