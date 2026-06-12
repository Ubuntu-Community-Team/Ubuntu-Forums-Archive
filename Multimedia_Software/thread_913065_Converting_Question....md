---
title: "Converting Question..."
date: 2008-09-07
forum: Multimedia Software
---

### Post by robelliott2125 on 2008-09-07
Hey guys & gals,

I'm needing some advice...

Does anyone know of a good program which can convert MP3s to AAC / M4A format?  I use this for my SE K800i mobile phone, since it allows more albums on the card I have, than MP3.

Also, on the same note, does anyone convert avi's to some format the same phone can read?  Since I'd love the new Slipknot Video (Psychosocial) on my phone as a videotone?

I know its two questions in one, but since they are both about converting, I figured I'd ask away...

Nobody in the IRC channel answered / helped on this matter, so hoping to get some suggestions from you guys.

The tracks don't need to be read within Ubuntu, since they are only for the phone, so pc playback isn't a necessity.

Thank you,

---

### Post by SuperSonic4 on 2008-09-07
perl audio converter will convert your audio files. It comes with a mod-install-kubuntu.sh which you run in terminal to satisfy dependencies

soundkonverter would probably be easier on ubuntu due to the former being integrated in Konqueror, Amarok and Dolphin (all kde apps)

```
sudo apt-get install soundkonverter
```

---

### Post by robelliott2125 on 2008-09-07
> **SuperSonic4 said:**
> perl audio converter will convert your audio files. It comes with a mod-install-kubuntu.sh which you run in terminal to satisfy dependencies

soundkonverter would probably be easier on ubuntu due to the former being integrated in Konqueror, Amarok and Dolphin (all kde apps)

```
sudo apt-get install soundkonverter
```

If perl is good, and is stable on Ubuntu, I don't mind trying it, since I already use a lot of K programs (I love Amarok!).

Next reinstall, will no-doubt be KDE.

Thanks again for the advice.  Any suggestion to the video conversion?

Thanks,

---

### Post by listener on 2008-09-07
You need not reinstall - it will all install on Ubuntu fine.

good luck

---

### Post by robelliott2125 on 2008-09-07
> **listener said:**
> You need not reinstall - it will all install on Ubuntu fine.

good luck

I didn't say I was reinstalling tonight, just to have KDE apps, just meaning when I next have to do a reinstall, it'll be to KDE not GDE.

---

### Post by robelliott2125 on 2008-09-12
Just wondering if anyone else could help on this matter.

I've installed SoundKonverter, but it doesn't seem to convert MP3s to AAC / M4A.

Still wanting to somehow convert an Avi to 3gp (which I think my phone allows and only accepts).

Thanks guys and gals!

---

### Post by unoodles on 2008-09-12
I think you'll need ffmpeg from medibuntu.

AFAIK (correct me if I'm wrong), aac encoder can't be in the repo's because it violates pantents.

---

### Post by robelliott2125 on 2008-09-12
> **unoodles said:**
> I think you'll need ffmpeg from medibuntu.

AFAIK (correct me if I'm wrong), aac encoder can't be in the repo's because it violates pantents.

Damnit, if it is a patented format.  I haven't a clue tbh.  I use it for my phone, and thats me happy.

I think this is becoming a dead end for me, and will have to continue using winblows for itunes.  Both being crap.  lol

Thanks anyway guys!

---

### Post by FakeOutdoorsman on 2008-09-12
Get ffmpeg from the Medibuntu repository.  It supports restricted formats.  If you like a gui with presets, then try WinFF.  Basic usage:
```
ffmpeg -i input.mp3 -vn -ab 128k output.mp4
```
In this example, "-vn" tells ffmpeg to ignore the video and "-ab 128k" is the audio bitrate.  If no bitrate is supplied then it will use the default value of 64k.

---

