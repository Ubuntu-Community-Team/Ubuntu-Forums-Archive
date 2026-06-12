---
title: "No-lag TV capture card viewer"
date: 2008-10-02
forum: Multimedia Software
---

### Post by Eric_Allard on 2008-10-02
Hi all,

I'm looking for a program that will allow me to view the input from my TV tuner card without lag. Anyone know if such a thing exists?

I've been using a program called DScaler with my Hauppauge WinTV-PVR-150 capture card to connect my Playstation 2 to my computer (I don't own a TV). The results are quite good with respect to both image quality and lag, but I'd rather avoid dual-booting for something as trivial as that (I'd like to take the plunge and do away with my Windows boot altogether).

The capture card is correctly detected by Ubuntu, but the programs I've tried such as MythTV have a delay of approximately 2 seconds. Needless to say that this makes gaming impossible.

Any suggestions would be greatly appreciated.

Eric

---

### Post by wolfen69 on 2008-10-02
I have a Hauppauge pvr150 card running on my hardy box, and I get  tv by: 

```
sudo apt-get install ivtv-utils 
```

open VLC player

File -> Open Capture Device -> PVR -> OK

then you can do (in terminal)

```
ivtv-tune -c25
``` (25 is channel number)

which changes the channel.

```
ivtv-tune -h
```

to see the options which control the card. 


for a cool desktop tv remote,(so you dont have to use terminal to change channels) go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

remember to have java installed first. then you can right click: open with java.

to record tv:

```
cat /dev/video0 > /tmp/name_of_file.mpg
```

it will record whatever channel you are on. then ctrl-c to stop.

---

### Post by Eric_Allard on 2008-10-03
Thanks for the reply.

Unfortunately, it seems that the IVTV drivers cause that lag as well. I think that IVTV and V4L drive most software out there so I think that I am out of luck unless the driver can be configured to avoid the lag.

Any other suggestions?

Thanks again

---

### Post by jzalomon on 2009-08-05
hi...i was reading about your problem with the sound lag....lag is actually coming from the second input sound...let me clear it up for you...turn on the game or whatever you are trying to watch through the tuner card...and open up volume control and on playback...turn down the volume on line-in.... your sound lag should go away...the problem is that is getting two different sound lines... so you should use only one...the line-in or the wave..hope it helps...keep me posted!!

good luck
:D

---

### Post by jzalomon on 2009-08-05
sorry...forgot to suggest to use tvtime...have you tried it?
simple and very nice...cya

---

