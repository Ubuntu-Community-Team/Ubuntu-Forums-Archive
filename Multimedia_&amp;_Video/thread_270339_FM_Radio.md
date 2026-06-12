---
title: "FM Radio"
date: 2006-10-03
forum: Multimedia &amp; Video
---

### Post by confusimo on 2006-10-03
I need a new tv tuner.  

1.  Is BT 848 supported or only 878.

2.  IF I get one like Hauppauge and it has FM feature builtin.  Will I be able to use the FM feature.  Listen to FM or record it for personal use only.  Or no FM software exists for linux.  And I'm beter with just a plain PCI tuner.

If the FM is not supported then I don't have to waste extra on that.  Or I have this USB device but probably not linux compadible.

Thanks,
Confusimo

---

### Post by confusimo on 2006-10-04
Nobody uses FM?

---

### Post by confusimo on 2006-10-05
Nobody?

---

### Post by Titus A Duxass on 2006-10-06
There is a partially developed FM radio in MythTV, check out the mythtv pages.

---

### Post by confusimo on 2006-10-06
I will thanks.  I finally decided on BT8787 so let cross our fingers.

---

### Post by confusimo on 2006-10-09
That's too complicated so I found thius instead.  If it works I'll let you know.  It installed OK but the card hasn't arrived yet.  When it does I'll reply again.

[http://www.wh-hms.uni-ulm.de/~mfcn/gnomeradio/](http://www.wh-hms.uni-ulm.de/~mfcn/gnomeradio/)

Thanks,
Confusimo

---

### Post by Shane10101 on 2006-10-12
I haven't been able to get GnomeRadio to work with my pvr350 card yet, but then I really don't know what I'm doing ;)

I think the problem is simply a matter of pointing the program to the correct device.  Currently, it's looking to "/dev/radio0", but I'm not able to tune in a station, despite the fact that I know there are several strong signals in range. (My setup works under the Hauppage-supplied software running on WinXP.)  

My guess is that, since the tuner is on the same card as the video device, that perhaps it's not a "/dev/radioX" device I'm looking for, but a "/dev/videoX" device instead.  Anyone with a more-educated guess for me??

I'll let y'a know how it goes.

Shane

---

### Post by Shane10101 on 2006-10-12
Okay, that part worked -- pointing it to the video device instead...

...now I can "tune" the stations in, and receive feedback about the signal (stereo/mono/...), but I still don't have any sound to the speakers.  

Any suggestions??

Shane

---

### Post by Shane10101 on 2006-10-12
Hmm.  This isn't looking too terribly hopeful:

[http://ubuntuforums.org/showthread.php?p=1608928]("http://ubuntuforums.org/showthread.php?p=1608928")

---

### Post by confusimo on 2006-10-12
Works for me as /dev/radio0.  If I use /dev/video0 nothing happens.  It only gives 1 station for now.  But that may just be the card.

Thanks,
Confusimo

---

### Post by mister_p_1998 on 2007-02-14
> **Shane10101 said:**
> Okay, that part worked -- pointing it to the video device instead...

...now I can "tune" the stations in, and receive feedback about the signal (stereo/mono/...), but I still don't have any sound to the speakers.  

Any suggestions??

Shane

Hi Shane,
you need to run a cable from the audio out on the TV card into the audio in ( Mic?) on your sound card

---

