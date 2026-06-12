---
title: "Picard MP3 Support"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by fordp on 2007-08-12
[SIZE=4][SIZE=3]I just had a problem getting picard to recognise MP3s.

After a lot of head scratching and Web Searching I found that 

"[/SIZE][/SIZE]libtunepimp" is needed for mp3 support.
[SIZE=4]I installed that using Synaptic and now it seems to be working!

I hope this helps somebody!
[/SIZE]

---

### Post by caecus314 on 2007-08-16
Thanks!  That did help.

---

### Post by Somatik on 2007-08-18
thanks!

---

### Post by digilink on 2007-08-19
You bet it helped, thanks a mil!!!! Working perfectly, I love this app.....

---

### Post by Band B on 2007-08-24
In Feisty the complete package name is:
libtunepimp5-mp3

---

### Post by Maczimus on 2007-11-06
Thank you.....Found via Google!

---

### Post by zombie_monkey on 2007-11-07
Thanks a lot, I had almost given up :)

---

### Post by Yoooder on 2007-11-09
I've gotten Picard to recognize mp3's in Gutsy, however when I drag an mp3 from the file list into the main pane Picard hangs and doesn't ever come back.

Anybody else experience this?

---

### Post by Somatik on 2007-11-09
> **Yoooder said:**
> I've gotten Picard to recognize mp3's in Gutsy, however when I drag an mp3 from the file list into the main pane Picard hangs and doesn't ever come back.

Anybody else experience this?

I never got it to work properly, but it might have been me missing something...

---

### Post by ypcs on 2007-12-21
> **Yoooder said:**
> I've gotten Picard to recognize mp3's in Gutsy, however when I drag an mp3 from the file list into the main pane Picard hangs and doesn't ever come back.

Anybody else experience this?

You need to install libtunepimp5-mp3

```
sudo apt-get install libtunepimp5-mp3
```

---

### Post by Band B on 2007-12-22
> **ypcs said:**
> You need to install libtunepimp5-mp3

```
sudo apt-get install libtunepimp5-mp3
```

I suggest you submit this as a bug first (but look  if someone else submited it yet). Beacues it shouldn't hang when facing an mp3. It should (in the best case) give an error, or just do nothing.

---

### Post by clubsoda on 2007-12-27
I found some debian packages for the latest version here:-
[https://launchpad.net/~luks/+archive](https://launchpad.net/~luks/+archive)

Strangely, the first CD I tried isn't found by Picard 0.7.2 or 0.9.0.  The **CD Lookup** function brings up an empty list.  Clicking **Manual Search** takes me to a Firefox page saying *"MusicBrainz doesn't currently have any release which have this TOC:"*.  Manually searching the website by artist & track finds similar songs but from different albums.  Finally, the **Scan** or **Analyze** functions calculate the fingerprints but come back with nothing.

Now here's the bizarre part... Plugging the same CD into Sound Juicer comes back straight away with a full track listing!  I checked the net traffic and saw that SoundJuicer accesses the MusicBrainz database.  How weird is that?

---

### Post by clubsoda on 2007-12-27
Hmm, does one have to be logged into MusicBrainz to use Picard in search mode?

---

### Post by marlboro05 on 2008-02-19
sudo apt-get install libtunepimp5-mp3
worked for me too thanks!

---

