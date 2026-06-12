---
title: "Error: ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card"
date: 2013-09-07
forum: Multimedia Software
---

### Post by ttsdinesh on 2013-09-07
I'm using Ubuntu 13.04 on my [COLOR=#000000]Samsung NP300V5A-S0CIN laptop. I tried executing a bash script to convert speech to text using google speech api. Here is my code:

[/COLOR]```
echo "Recording... Press Ctrl+C to Stop."
arecord -D "plughw:1,0" -q -f cd -t wav | ffmpeg -loglevel panic -y -i - -ar 16000 -acodec flac file.flac  > /dev/null 2>&1


echo "Processing..."
wget -q -U "Mozilla/5.0" --post-file file.flac --header "Content-Type: audio/x-flac; rate=16000" -O - "http://www.google.com/speech-api/v1/recognize?lang=en-us&client=chromium" | cut -d\" -f12  >stt.txt


echo -n "You Said: "
cat stt.txt


rm file.flac  > /dev/null 2>&1

```

I copied the code from [http://blog.oscarliang.net/raspberry-pi-voice-recognition-works-like-siri/](http://blog.oscarliang.net/raspberry-pi-voice-recognition-works-like-siri/)

When I executed the query I got an exception :

```
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
arecord: main:682: audio open error: No such file or directory

```

I think the issue is with my audio card. Do anybody knows how to fix it ?

Thanks in advance.

---

### Post by ttsdinesh on 2013-09-21
I figured out the issue. The following code works:

arecord -vv -t wav -d 3 | ffmpeg -loglevel panic -y -i - -ar 16000 -acodec flac file.fla

Though the above code does not record the audio very clearly, I'm able to get good response for audio clips less than 3 seconds.

---

