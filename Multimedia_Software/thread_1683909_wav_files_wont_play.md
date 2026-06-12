---
title: "wav files wont play"
date: 2011-02-08
forum: Multimedia Software
---

### Post by compactbrain on 2011-02-08
hi all,
I have FL Studio 9 installed but some of the wav files wont play.
When i try play them i get an error "Could not decode stream".
Ive tried several players and rezound will play the files but when i save it again no matter what format it wont play.
Any help greatly appreciated

---

### Post by compactbrain on 2011-02-08
figured it out (someone else did actually) the wav files are encoded with ogg vorbis and the FL studio doesn't set it up right in wine,
just need to enter a command t the terminal to fix it

```
sed -i 's/\[drivers32\]/\[drivers32\]\nMSACM.vorbis=vorbis.acm/' ~/.wine/drive_c/windows/system.ini
```

---

