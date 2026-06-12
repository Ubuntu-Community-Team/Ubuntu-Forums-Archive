---
title: "Problem with 5.1 surround - subwoofer"
date: 2009-12-07
forum: Multimedia Software
---

### Post by Hesediel on 2009-12-07
i have this situation


Up - left opened with ```
pavumeter
```  pulse settings with ```
padevchooser
```


Starting situatione:

[[img]http://s3.postimage.org/1WxWtr.jpg[/img]](http://www.postimage.org/image.php?v=Pq1WxWtr.jpg)


You can see that on Volume Meter the last line doesn't work, no signal. What i did: i'm gone on the left 'applet and checked
[b]
Configure Local Sound Server[/b]

Here i went on the last pannel:  ```
"Simultaneous Output"
```   so i checked
[b]
Aggiungere dispositivo virtuale per uscita contemporanea su tutte le schede locali.[/b] it will be like "Add virtual dispositive for contemporary exit on alls local cards

Doing this on "volume control" i can choose beetween two different thing

1**"Simoultaneous output to audio interno Analog Surround 5.1"** e 2**"Analog Surround 5.1"**

[[img]http://s3.postimage.org/1WAD59.jpg[/img]](http://www.postimage.org/image.php?v=Pq1WAD59)



I have the1 selezionato, if i select the 2 the subwoofer works! If i re-check the 1 the sub doesn't works Ho detto: 
Strange thing: if i check the 2 (so sub doesn't work)....and i come back on pulse audio preferences, "preferenze di pulse audio" e un-check [b]
Aggiungere dispositivo virtuale per uscita contemporanea su tutte le schede locali.[/b] So sub works even i have selected the 2. 

But in all cases if i restart, or i close the session, after re logging in the sub doesn't work and i have to make those manual steps for make it warks. Some one can help me?

---

### Post by geckon on 2010-01-09
Hi! I've tried to proceed according to your howto and I succeeded but only partially. Since I have changed "Simoultaneous output to ****** Analog Surround 5.1" to "Analog Surround 5.1" only for Rhythmbox, subwoofer turns off every time I e.g. play another song. Can anybody help?

---

### Post by geckon on 2010-01-09
Try change line
```
; enable-lfe-remixing = no
```

to
```
enable-lfe-remixing = yes
```

in file
```
/etc/pulse/daemon.conf
```

Worked for me -> my subwoofer plays ;-)

---

### Post by EagleDM on 2010-01-09
I think this is related to channel mapping.

Other users are experiencing the same problem,  it seems that the only correct channel mapping is 7.1 if your soundcard supports it.

There seems to be a problem when ALSA reports 7.1 and pulse tries to use 5.1 or any other config instead and you get no sound or garbled sound.


Give it a try.

---

### Post by geckon on 2010-01-10
My sound card supports 7.1, but I told PulseAudio to use 5.1 so this is not problem here.

---

### Post by Gone fishing on 2010-01-10
Thanks geckon

enable-lfe-remixing = yes

worked for me

---

### Post by geckon on 2010-01-10
> **Gone fishing said:**
> Thanks geckon


You are very welcome. I found it on some other forum so I want to help to someone else :-)

---

### Post by SR_ELPIRATA on 2010-03-08
I used this to fix my problem as well, thanks geckon!

However, I've noticed that the sub doenst always work, like in Rhythmbox, but whenever I watch movies with XBMC works great. No clue what it is.

PS: I forgot to reactivate the line again after the last install hehehe, its working great again.

ELP

---

