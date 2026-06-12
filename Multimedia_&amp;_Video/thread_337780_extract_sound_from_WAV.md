---
title: "extract sound from WAV"
date: 2007-01-13
forum: Multimedia &amp; Video
---

### Post by sn0m on 2007-01-13
does anybody knows any good program to extract video from wav files. There are a few shows that i like to listen to them in my car stereo.
thanks
koli

---

### Post by kebes on 2007-01-13
You said "extract video from wav" but I'm guessing what you are asking is "how do I extract the audio track from a video, and save it as a WAV file?"...

If that's your question, you can use the GUI program "avidemux" to extract audio and video separately, and transform them into other formats.

---

### Post by sn0m on 2007-01-13
Sorry i got it wrong. I meant extract audio from WMV file.
thanks for you suggestion, i'll have a go at avidemux.
thanks
koli

---

### Post by kebes on 2007-01-13
Trying to extract from WMV might be a problem. I don't know if avidemux can do that (but it's worth a try!). If it doesn't support it, you may need to use transcode or mencoder to convert to a more Linux-friendly format first!

---

### Post by majoridiot on 2007-01-13
```
ffmpeg -i <inputfile> -vn -ab 16 -ac 2 -ar 44100 <outputfile.wav>
```

(convert <inputfile> to <outputfile> using: vn=no video, -ab=16 bit audio, -ac=2 audio channels, -ar=44100Hz)

---

### Post by sn0m on 2007-01-18
I must be doing sth stupid as i still can't get it work.
this is the otput

sn0m@sn0m-laptop:~$ ffmpeg -i <inputfile> -vn -ab 16 -ac 2 -ar 44100 <outputfile.wav>
bash: syntax error near unexpected token `newline'
sn0m@sn0m-laptop:~$ cd /home/sn0m/Desktop
sn0m@sn0m-laptop:~/Desktop$ ls
aulona dental clinic 005.jpg  MUM'S%20WEBSITE.html   topstory21dhjetor.wmv
aulona dental clinic 014.jpg  new file~              topstory28dhjetor.wmv
interfacesut~                 topstory14dhjetor.wmv
sn0m@sn0m-laptop:~/Desktop$ ffmpeg -i <inputfile> -vn -ab 16 -ac 2 -ar 44100 <outputfile.wav>
bash: syntax error near unexpected token `newline'
sn0m@sn0m-laptop:~/Desktop$ ffmpeg -i <topstory21dhjetor.wmv> -vn -ab 16 -ac 2 -ar 44100 <topstory21dhjetor.wav>
bash: syntax error near unexpected token `newline'
sn0m@sn0m-laptop:~/Desktop$ ffmpeg -i <inputfile> -vn -ab 16 -ac 2 -ar 44100 <outputfile.wav>
bash: syntax error near unexpected token `newline'
sn0m@sn0m-laptop:~/Desktop$ what am I doing wrong here????????????
bash: what: command not found
sn0m@sn0m-laptop:~/Desktop$ 

thanks
Koli

---

### Post by kko1 on 2007-01-18
Drop the < and >. ;-)

Hope this helps,
kko

... just dropped in here to wonder if I'd post a question myself and saw this thread at the top...

> sn0m@sn0m-laptop:~/Desktop$ what am I doing wrong here????????????
bash: what: command not found

:-)

---

### Post by sn0m on 2007-01-18
thanks buddy, it works fine.
Thanks a million
koli:D

---

