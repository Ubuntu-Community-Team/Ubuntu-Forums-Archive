---
title: "Recording Skype makes it complain"
date: 2013-04-19
forum: Multimedia Software
---

### Post by pokepal101 on 2013-04-19
Okay. I'm trying to record a Skype call (screen, microphone and 'stereo mix') by using avconv (ffmpeg) and arecord.

The commands I am using are: (in a script, of course)
```
avconv -v panic -f x11grab -s 1600x900 -i :0.0 -r 30 -vcodec libx264 -crf 0 video.mkv &
arecord -D pulse -f dat audio1.wav &
arecord -D pulse -f dat audio2.wav &
```
PulseAudio is configured correctly to make the first arecord record the microphone and the second record the 'stereo mix'.

If I run the program on Firefox, while I'm playing a YouTube video, everything works properly.

If I run the program, then initiate a Skype call, Skype complains about a 'Problem with Audio Playback'.
If I initiate a Skype call, then run the program, I get about 3 seconds of audio on each of the files, before they abruptly end. No error messages are printed to the console.

Can someone help me?
Thanks in advance.

---

### Post by uzumakifahim on 2013-04-19
There is very good skype call recorder out there. It works great for me. check out [this link]("https://help.ubuntu.com/community/SkypeRecordingHowto") for more details. Not only that, if you want to download the package directly you can [click here]("http://atdot.ch/scr/download/").

Hope this solution will works for you.

---

### Post by pokepal101 on 2013-04-19
> **uzumakifahim said:**
> There is very good skype call recorder out there. It works great for me. check out [this link]("https://help.ubuntu.com/community/SkypeRecordingHowto") for more details.

Thanks for that link, it might come in handy one day, but it doesn't quite solve my problem.
If I've interpreted that page correctly, it would record my Skype call, but nothing else.

I want to record my Skype call, as well as the system audio, so I could, say, record me playing a game while talking with my friend.

---

