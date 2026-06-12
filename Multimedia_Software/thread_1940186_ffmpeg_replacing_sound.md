---
title: "ffmpeg replacing sound"
date: 2012-03-13
forum: Multimedia Software
---

### Post by lf2 on 2012-03-13
Hi

i got a .mov file and i want to replace the audio with another file.. (aac or mp3)

the movie is like 20 seconds long and the audio file 2 minutes

when i replace it with this code: 

"ffmpeg -i audio.aac -i video.mov video_finale.mov"

i get the file but it extends the video file to 3 minutes (because of the long audio file) 

any suggestions how to fix this ?

---

### Post by sudodus on 2012-03-13
If you use a GUI video editing tool, it will be more intuitive to manage different lengths of the tracks. I suggest that you use OpenShot.
```
sudo apt-get install openshot
```

---

### Post by ron999 on 2012-03-13
> **lf2 said:**
> 
any suggestions how to fix this ?
Use a command like this:-
```
ffmpeg -i audio.aac -i video.mov -shortest video_finale.mov
```

---

### Post by lf2 on 2012-03-13
> **ron999 said:**
> Use a command like this:-
```
ffmpeg -i audio.aac -i video.mov -shortest video_finale.mov
```


hmm it keeps the video length but the last 2 seconds i dont hear anything.. (no sound)


another question... if i want to start the sound 10 seconds later..i have to use the -ss but it did not work... how do i use it correctly

---

### Post by ron999 on 2012-03-13
> **lf2 said:**
> hmm it keeps the video length but the last 2 seconds i dont hear anything.. (no sound)
Hi
Convert the soundtrack to wav:-

```
ffmpeg -i audio.aac audio.wav
```

Replace the sound:-

```
ffmpeg -i audio.wav -i video.mov -shortest video_finale.mkv
```

Convert sound back to aac:-

```
ffmpeg -i video_finale.mkv -vcodec copy -acodec aac -ab 128k -strict experimental video_finale.mov
```

---

### Post by lf2 on 2012-03-13
> **ron999 said:**
> Hi
Convert the soundtrack to wav:-

```
ffmpeg -i audio.aac audio.wav
```

Replace the sound:-

```
ffmpeg -i audio.wav -i video.mov -shortest video_finale.mkv
```

Convert sound back to aac:-

```
ffmpeg -i video_finale.mkv -vcodec copy -acodec aac -ab 128k -strict experimental video_finale.mov
```

hey 

tnx for your help...but still no sound last 2 seconds...

---

### Post by sudodus on 2012-03-14
> **lf2 said:**
> hey 

tnx for your help...but still no sound last 2 seconds...

This problem might be because the playback is out of sync: For example, by default ***mplayer*** plays the video at the correct speed or as fast as possible without frame-dropping, so the video might lag behind the audio.

I get this 'last and updating' line when playing 1080/50p with mplayer on this computer, which is not fast enough for it
```
A:  13.3 V:   5.5 [COLOR="Red"]A-V:  7.873[/COLOR] ct: -0.010 252/252 241%  8%  6.7% 249 0 
``` A-V: shows how much the video is lagging behind the audio, in this case 7.873 seconds.

So you can run the video clip with mplayer and check if A-V: indicates something close to zero or if the value grows.

---

### Post by lf2 on 2012-03-15
> **sudodus said:**
> This problem might be because the playback is out of sync: For example, by default ***mplayer*** plays the video at the correct speed or as fast as possible without frame-dropping, so the video might lag behind the audio.

I get this 'last and updating' line when playing 1080/50p with mplayer on this computer, which is not fast enough for it
```
A:  13.3 V:   5.5 [COLOR="Red"]A-V:  7.873[/COLOR] ct: -0.010 252/252 241%  8%  6.7% 249 0 
``` A-V: shows how much the video is lagging behind the audio, in this case 7.873 seconds.

So you can run the video clip with mplayer and check if A-V: indicates something close to zero or if the value grows.

i will check that now... 

i have another question...


a tough question i dont know if its possible..

is it possible to make the -ss dynamic..

i will try to explane what i am after...

the meta data video has a creation time : date 00:01:54+0100 
the meta data audio has a creation time: date 00:01:34+0100

(02:34 - 01:54 = 40 (thats the -ss i use)

is there a way to automaticly take the time off the video creation date and the audio creation date
nd use that as the -ss ?

is this possible ?

---

