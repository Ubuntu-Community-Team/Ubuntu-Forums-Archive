---
title: "Youtube rejects libx264 coded video?"
date: 2010-04-24
forum: Multimedia Software
---

### Post by Dimitree on 2010-04-24
Hello, everything that i try to encode with libx264 is being rejected by youtube with "fail to convert" error.
It doesn't matter if i use OpenShot or PiTiVi or any other app.
As long as the codec is libx264 youtube rejects the file.
Is there a way to fix this?

---

### Post by Dimitree on 2010-04-24
Is there anyone who uploads HD videos to youtube?
Please tell me which program do you use and what presets?

---

### Post by FrankVdb on 2010-04-24
Same question here... I use OpenShot to convert my drumming videos to Youtube-HD and it doesn't work...

---

### Post by Dimitree on 2010-04-24
Well i have made some progress :/ but there's no audio.
Youtube will accept .h264 and avi Video Formats but there is no audio :(
I'm testing all the audio codecs to find anything that will work with it.
And to be honest i'm starting to think that it's an audio encoder issue since youtube accepts the clips when audio is not working.
Someone help please :)

---

### Post by Dimitree on 2010-04-24
All audio codecs combinations with .avi container and libx264 failed.:(

---

### Post by tgalati4 on 2010-04-24
It is my understanding that h264 (MPEG4 AVC--Advanced Video Codec) uses AAC as the primary audio codec.

Not sure what youtubeHD specifications are.

---

### Post by Dimitree on 2010-04-24
The problem is with Ubuntu Lucid libraries for libavformat :/

Unless someone explains how to install the Karmic version of libavformat-unstripped under Lucid there is no other solution which i know for now :/

Or i guess installing Karmic is the other option :/
Hope someone can help with installing libavformat for Karmic under Lucid.

I tested the libs with Karmic live usb stick and everything works there.
The problem is only under Lucid and Lucid libs :/

---

### Post by Dimitree on 2010-04-24
Unbelievable ...
The problem was actually the Opera web browser ...
The reason everything worked on my Live 9.10 usb stick is because i was using Firefox to upload the movies.
Now after installing 9.10 and using Opera, the same problems appeared like under Lucid where i used Opera as well.

So if you are using Opera 10.10 and you get youtube errors Failed unable to convert file when uploading your videos, try using Firefox although youtube reports that the file was successfully uploaded with Opera, it's not.

I love you Opera <3 Q_Q

---

