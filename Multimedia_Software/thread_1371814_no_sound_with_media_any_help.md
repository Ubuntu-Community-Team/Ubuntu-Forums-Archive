---
title: "no sound with media? any help?"
date: 2010-01-03
forum: Multimedia Software
---

### Post by phawnex on 2010-01-03
i have no sound coming out of my imac running ubuntu 9.10, is there any remedy for this ?

i finally got my wireless up and running and couldnt be happier. i put in a cd and it shows that it is playing but there is no sound coming out.

any help would be greatly appreciated. thanks a lot.

---

### Post by phawnex on 2010-01-03
i tried opening the rhythmbox music player, tried playing the mp3's (searched and installed the three files i needed to play the mp3's) still no sound; but the computer would show it was playing the mps.  i went to test the radio on rhythmbox to make sure it just wasnt the mp3s, and it would play the radio but no sound still from streaming on the radio.

*shrugs

also i checked my sound preferences for hardware and it reads my internal audio from my imac. 

"internal audio; 1 output/1input; analog stereo duplex"

i experienced with some of the different profiles on the output and still no luck. and the mic i tested it reads the input and shows the levels when i tested the mic. but no sound.....

---

### Post by Yellow Pasque on 2010-01-03
Maybe this will give you some ideas: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/346170](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/346170)

What model imac do you have? WHat does this show?
```
aplay -l
```

---

### Post by phawnex on 2010-01-03
results :
> daniel@daniel-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

my imac i have had for about two year now, and its a 24 inch"  (model i dont know but i can find out in one second. )

also i peeped ur link for ideas.. i tested out the head phones (which are not my main concern cuz i am on desktop, if i can even get sound out of main audio then ill be one happy camper) but the headphones didnt have sound either

---

### Post by phawnex on 2010-01-03
imac model : 7,1.  (not 9,1 like the other guys...) my model is two years older.
24inch model

also in your link i read more indepth, it looks like liberalist is having the same issue (he has the same internal unit with the ALC889A...)....

so i dunno...

i may try the package out, but it wont mess up any thing else on the ubuntu os right?

---

### Post by Yellow Pasque on 2010-01-03
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Add line:
```
options snd-hda-intel model=imac24
```
Save. Quit. Reboot. Joy?

If that doesn't work, you can also try it with model=mb31 instead.

---

### Post by phawnex on 2010-01-03
where do i add the extra line. i put the gksu gegit..... command in terminal
and it produced another window with alsa-base.

do i put the extra line (the one u told me to add ) in the pop up window?  (and at which part of the coding in the alsa-base window?)

---

### Post by Yellow Pasque on 2010-01-03
Put the line at the end of the file.

---

### Post by phawnex on 2010-01-03
the window rhat popped up right?

(the alsa-base window)

---

### Post by Yellow Pasque on 2010-01-03
Yes.

---

### Post by phawnex on 2010-01-03
thanks man it worked. i got the sound out of it on the first shot.
ur a life saver.

major thanks.

---

