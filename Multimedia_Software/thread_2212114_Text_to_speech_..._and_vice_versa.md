---
title: "Text to speech ... and vice versa"
date: 2014-03-19
forum: Multimedia Software
---

### Post by Langstracht on 2014-03-19
It looks like there was some buzz about Festival a couple of years ago.  And little or nothing since.

I just gave it a try.  And it "works" albeit not very well.

Is there any other software that someone can recommend that does "work"?

I'd also like to get a speech-to-text programme.  Have looked and found nothing.

Again can someone recommend a programme?

TIA

---

### Post by FakeOutdoorsman on 2014-03-20
[size=5]text-to-speech[/size]
You can use the flite filter in ffmpeg. You'll have to compile it:

```
sudo apt-get install build-essential flite1-dev
wget http://ffmpeg.org/releases/ffmpeg-snapshot.tar.bz2
tar xjvf ffmpeg-snapshot.tar.bz2
cd ffmpeg
./configure --enable-libflite --enable-gpl
make -j4
```

Now run your new ffmpeg binary (notice the **./** before the ffmpeg):
```
cd ~/ffmpeg
./ffmpeg -f lavfi -i flite=textfile=speech.txt output.wav
```
or enter the text in your command instead of using speech.txt:
```
cd ~/ffmpeg
./ffmpeg -f lavfi -i flite=text='Corn? When did I eat corn?' output.wav
```

I haven't actually tested these commands so take a look at the docs too.

Also see:
[list]
[*][FFmpeg flite filter documentation](http://ffmpeg.org/ffmpeg-filters.html#flite)
[*][How To Compile FFmpeg and x264 on Ubuntu](https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide)
[/list]

---

### Post by Langstracht on 2014-03-21
I'll give that/them a try.  Thanks for the info.

---

