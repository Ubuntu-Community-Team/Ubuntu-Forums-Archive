---
title: "Setup Streaming video server"
date: 2009-07-02
forum: Multimedia Software
---

### Post by NateMan on 2009-07-02
I've been attempting to setup a streaming video server using the guide shown here:  [http://www.linuxjournal.com/article/6720](http://www.linuxjournal.com/article/6720)

It seems to be an interesting way for me to watch videos from my home server at any location, however I can't seem to get ffmpeg to extract raw pcm output. 
I'm attempting to use this piece of code:
```

ffmpeg -i <input_file> -vn <output_file>

```
This only works if I name the file .whatever-the-audio-is (.wav .mp3 .aac), when I really want it to come out as a .pcm file (or at least I think so). I believe this is what I need to get the next faac command to work, since it doesn't work with .wav, .mp3, or .aac files. If anyone has any advice on command line only ways to complete the same task, please let me know. I'd like to script this so that I can run it automatically on .avi files. Thanks in advance. I know its a rather old article.

---

