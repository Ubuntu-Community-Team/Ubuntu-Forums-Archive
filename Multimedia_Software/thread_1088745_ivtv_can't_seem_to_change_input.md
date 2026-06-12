---
title: "ivtv can't seem to change input"
date: 2009-03-06
forum: Multimedia Software
---

### Post by klein de usa on 2009-03-06
hi 
i have installed ivtv on ubuntu 8.10 from the package manager, and all seems fine except i can change the input to s-video or composite.

klein@klein-810:~$ dmesg |grep Initialized
[   12.465080] ivtv0: Initialized card #0: WinTV PVR 500 (unit #1)
[   12.583515] ivtv1: Initialized card #1: WinTV PVR 500 (unit #2)
[   27.413986] [drm] Initialized drm 1.1.0 20060810
[   27.445117] [drm] Initialized i915 1.6.0 20060119 on minor 0


klein@klein-810:~$ v4l2-ctl --get-input
Video input : 0 (Tuner 1)
klein@klein-810:~$ v4l2-ctl --set-input=2
klein@klein-810:~$ v4l2-ctl --get-input
Video input : 0 (Tuner 1)
klein@klein-810:~$ v4l2-ctl --set-input=1
klein@klein-810:~$ v4l2-ctl --get-input
Video input : 0 (Tuner 1)

the card works fine when you use the coax connector, picture is not as good as i hoped.


i just can't figure out what i'm doing wrong?

---

### Post by wolfen69 on 2009-03-06
i'm not sure i understand. when you say you installed ivtv, do you mean ivtv-utils? if you don't have it, install it.

then you can do 
```
ivtv-tune -h
```
to see which options you have.

to change input, you would need to do
```
ivtv-tune -d(device_name)
```

what app are you using to watch tv with?

---

### Post by klein de usa on 2009-03-06
hi 
i'm using the card to record old 8mm cassettes home movies of the kids, on the coax connection /dev/video0 i can record video but i'm hopping s-video or composit is better, i'v been using mplayer to watch the video's.



i was using the help in terminal v4l2-ctl --h for help 

i'm a little confused i'v been doing a lot of reading and i think i'm lost

---

### Post by klein de usa on 2009-03-06
hi 
and i did install ivtv-utils

---

### Post by klein de usa on 2009-03-06
ivtv-tune -d Composite 1


it is still on the coax connector 

klein@klein-810:~$ v4l2-ctl --get-input
Video input : 0 (Tuner 1)

---

### Post by wolfen69 on 2009-03-06
the official [documentation]("http://ivtvdriver.org/index.php/Documentation") may be of some help.

---

### Post by klein de usa on 2009-03-06
i rebooted and it changed to input2 right off the bat lol it will record the video using  cat /dev/video0 > test.mpg  but i can't get mplayer to play the video coming form the card maybe on input2 it doesn't?

---

### Post by saedelaere on 2009-03-08
You could have a look at this piece of software [here]("http://home.arcor.de/saedelaere/index_eng.html") to watch and record TV. But I have to admit only one of your two tuners will be supported.

Regards

---

### Post by klein de usa on 2009-03-08
thanks guys

---

### Post by megamanexent on 2009-06-06
I know you got it some what solved, but i noticed that  v4l2-ctl cannot change to an input as long the tuner is in use. Next time try to change to composite when the tuner is not in use. i.e the card is not playing video through VLC, MPlayer, etc

Edit: i should have looked at the date 2006, it 2009 thats a long time to wait for a reply.. LOL

---

