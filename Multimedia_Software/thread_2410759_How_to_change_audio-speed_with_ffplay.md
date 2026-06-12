---
title: "How to change audio-speed with ffplay:"
date: 2019-01-20
forum: Multimedia Software
---

### Post by rosika on 2019-01-20
Hi altogether,


if I have longer texts to read I like to have them read to me with the following script from [https://wiki.ubuntuusers.de/Sprachausgabe/#SVOX-pico2wave](https://wiki.ubuntuusers.de/Sprachausgabe/#SVOX-pico2wave) .


```
1  #!/bin/bash
2  pico2wave -l=de-DE -w=/tmp/test.wav "$(cat ${1})"
3  avplay -f wav -loglevel 0 >/dev/null -x 100 -y 50  -vn -autoexit /tmp/test.wav
4  rm /tmp/test.wav



```Save the script as **svox.sh** in */usr/local/bin* and start it with


```
svox.sh TEXTFILE.txt



```That works really well with English texts (with "**pico2wave -l=en-GB [...]**" in line 2 of course) but the audio-speed in German is a bit slow.


What I´ve tried so far is replacing line 3 with


```
avplay -f wav -loglevel 0 >/dev/null -x 100 -y 50  -vn -autoexit -filter:a "atempo=2.0" /tmp/test.wav 



```yet that didn´t work. In order to find out why that is I tried typing the following command in the terminal:


```
avplay -f wav -x 100 -y 50  -vn -autoexit -filter:a "atempo=2.0" test.wav



```I got the following error-message:


```
[...]
Failed to set value 'atempo=2.0' for option 'filter:a': Option not found

```

So it seems that either the syntax isn´t correct or the option isn´t supported.
Does anyone know of a way to speed up the audio output?


Thanks a lot in advance.
Greetings
Rosika  :(


P.S.:


my system: Linux/Lubuntu 16.04.5 LTS, 64 bit

---

### Post by mc4man on 2019-01-20
Use this instead
```
-af atempo=2
```

---

### Post by rosika on 2019-01-20
Hi   mc4man,

thanks a lot for your suggestion. Alas I couldn´t get it to work. I get the following error-mages:

```
avplay -f wav -x 100 -y 50  -vn -autoexit -af atempo=2 kgw_Pause.wav

[...]
Input #0, wav, from 'kgw_Pause.wav':KB vq=    0KB sq=    0B f=0/0   
  Duration: 00:00:09.10, bitrate: 1411 kb/s
    Stream #0:0: Audio: pcm_s16le ([1][0][0][0] / 0x0001), 44100 Hz, 2 channels, s16, 1411 kb/s
[auto-inserted resampler 0 @ 0x7f8a1004c6c0] Cannot select channel layout for the link between filters auto-inserted resampler 0 and Parsed_atempo_0.
[auto-inserted resampler 0 @ 0x7f8a1004c6c0] Unknown channel layouts not supported, try specifying a channel layout using 'aformat=channel_layouts=something'.
Failed to open file 'kgw_Pause.wav' or configure filtergraph
```

---

### Post by mc4man on 2019-01-20
Trying your script with proper filter syntax works fine here (though 2 is much too fast and distorts..
Also trying that last posted command works fine, the command could be shortened, i.e as example
ffplay  -x 100 -y 50  -af atempo=1.1 /home/doug/Music/03.Summertime.wav

The file you are showing latest error on is not from pico2wave.. so likely error is from the file, not the command. (pico2wave produces a mono track.

---

### Post by rosika on 2019-01-21
Hi mc4man,

thanks for your reply.
Alas the command you gave me doesn´t work. I really don´t know why. I always get the stated error-mesage.

Yet with the following script I managed to produce a workaround:


```
#!/bin/bash


pico2wave -l=de-DE -w=/tmp/test.wav "$(cat ${1})"
ffmpeg -i /tmp/test.wav -filter:a "atempo=1.2" -vn /tmp/test2.wav  # increase speed by a factor of 1.2
firejail --net=none avplay -f wav -loglevel 0 >/dev/null -x 100 -y 50  -vn -autoexit /tmp/test2.wav  # play sound in a sandbox
rm /tmp/test.wav
rm /tmp/test2.wav

```

Just out of curiosity:
In your example you used ***atempo=1.1 ***.
So am I right in assuming that the *atempo filter *can be in-/decreased in 0.1-steps and not just 0.5-steps?

Greetings
Rosika

---

### Post by slickymaster on 2019-01-21
*Thread moved to **Multimedia Software**.*

---

### Post by rosika on 2019-01-21
Hi again,

seems like I found an answer to my latest question ( [https://www.systutorials.com/docs/linux/packages/ffmpeg/ffplay-all.html#atempo](https://www.systutorials.com/docs/linux/packages/ffmpeg/ffplay-all.html#atempo) ):

> **25.19 atempo[#]("https://www.systutorials.com/docs/linux/packages/ffmpeg/ffplay-all.html#atempo") [TOC]("https://www.systutorials.com/docs/linux/packages/ffmpeg/ffplay-all.html#toc-atempo")**

[COLOR=#333333][FONT=arial]Adjust audio tempo.[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]The filter accepts exactly one parameter, the audio tempo. If not specified then the filter will assume nominal 1.0 tempo. Tempo must be in the [0.5, 2.0] range.[/FONT][/COLOR]
**25.19.1 Examples[#]("https://www.systutorials.com/docs/linux/packages/ffmpeg/ffplay-all.html#Examples-20") [TOC]("https://www.systutorials.com/docs/linux/packages/ffmpeg/ffplay-all.html#toc-Examples-20")**


[LIST]
[*]Slow down audio to 80% tempo:atempo=0.8
[*]To speed up audio to 125% tempo:atempo=1.25
[/LIST]

So it seems any incremental steps are possible.

Thanks again for your help.

Greetings
Rosika  ;)

---

