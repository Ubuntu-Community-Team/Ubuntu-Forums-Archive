---
title: "Audacity very strange problem"
date: 2007-04-12
forum: Multimedia &amp; Video
---

### Post by f3ua on 2007-04-12
Hi all

I've got a very big problem with audacity. I'm a dj and i like record my mixes from my consolle. So i've connected the rec out of the consolle to the line in connector on my sound card and started recording.

I can heat the sound, but there is a "metallic" noise under it. I watched all settings, alsa mixer ecc and i can't eliminate it. BUT the very strange thing is that if i record with the gnome tool the registration is PERFECT so it isn't an audio problem.

Please give me some ideas. Thanks.

---

### Post by bananabob on 2007-04-13
Is the line in volume too high in audacity?

---

### Post by f3ua on 2007-04-13
> **bananabob said:**
> Is the line in volume too high in audacity?

I think not because I've set up it from the audacity's volume bar and from gnome alsa mixer both.

I've analyzed the file recorded and there are some frequencies that create this "metallic noise" *only* on certain sounds. In other sounds the registration is correct.

I repeat that with gnome recorder the registration is perfect, and the my soundcard works fine also with games.

Here are my lspci about the soundcard.
```

00:0d.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

```

---

### Post by bananabob on 2007-04-13
This is indeed very strange. If the sound is there in Audacity, you would expect Gnome recorder would pick it up as well.

Unless --- Is Gnome recorder using OSS, instead of ALSA, or is AUdacity that is using OSS instead of ALSA, maybe??????

---

### Post by f3ua on 2007-04-14
From the preferences -> audio I/O screen i can select only:

/dev/dsp

And from channel i've selected 2 (Stereo).

How can i know if audacity is using oss instead alsa or viceversa?

Thanks.

---

### Post by bananabob on 2007-04-14
go to System>Prefences>Sound and you will see a selection panel

---

### Post by f3ua on 2007-04-15
I've got autodetect in all boxes. I can select
ALSA
OSS
ESD
NVIDIA CK804 - IEC958
NVIDIA CK804
Autodetect

What's the best choice?

---

### Post by bananabob on 2007-04-15
ALSA - is supposed to be the best choice, and I would assume that you are using it with Autodetect. What I would do is change them to each choice and give it a try and see (or rather hear) the results.

---

### Post by JingleBells on 2007-04-19
Hi all

I'm facing the same problem using Audacity (the 'metallic' noise) and it's driving me crazy!

I went to System>Preferences>Sound>Devices and there Audio Capture is ALSA while rest are *Autodetect*. 
Funny thing is, the Sound Recorder Program (Applications>Sound and Video>Sound Recorder) is working perfectly under these settings, but the metallic noise is appearing there if I select OSS as my Audio Capture method!:mad: 

Please help me get around this problem!!

---

### Post by f3ua on 2007-04-21
You have the same problem!!

But if you set ALSA as recording device, Audacity works correctly?

Thanks.

---

### Post by backdoc on 2007-06-24
I had the same problem.  Since I was able to resolve it, I wanted to post my experience here for others.

I believe the problem is associated with the OSS drivers.  I guess some would suggest using the alsa-oss wrapper to work around it.  I find that unacceptable because I don't want to add another layer.  However, my understanding is  that Audacity doesn't have support for Alsa in the most recent release.  So, you will need to use that if you stick with the latest version Audacity in the Ubuntu repositories.  But, alsa is supported in Audacity in the beta version.  I guess it is supported via the portaudioV19 code.  I wanted some of the features in the beta anyway, so I chose to compile it from source.

I didn't have too much trouble compiling it.  But, I did have a good bit of trouble getting alsa to work.  I could get Audacity to show the OSS drivers as an option for the input and output devices.  But, I couldn't get alsa to show up.  I thought I didn't have alsa working, but I was able to rule that out by removing the OSS modules with rmmod and then playing some music with another audio application.

Rather than to continue going into more detail here, I have already posted my experience in great detail on the Audacity forums.  So, I will just [link to it]("http://audacityteam.org/forum/thread/5110").  Hopefully, this will save someone else the same trouble.  [This link]("http://audacityteam.org/wiki/index.php?title=Linux_Issues#OSS_vs_ALSA") came in real helpful for me, too.

The links aren't showing up in the preview.  So, I will post them here:
[LIST]
[*][http://audacityteam.org/forum/thread/5110](http://audacityteam.org/forum/thread/5110)
[*][http://audacityteam.org/wiki/index.php?title=Linux_Issues#OSS_vs_ALSA](http://audacityteam.org/wiki/index.php?title=Linux_Issues#OSS_vs_ALSA)
[/LIST]

---

### Post by f3ua on 2007-06-25
Huge thanks for this explanation. I saw that ubuntu studio has very interesting features, may it solve also this problem without any alsa/oss wrapper? Now I can't try it because I've no time.

Thanks again.

---

