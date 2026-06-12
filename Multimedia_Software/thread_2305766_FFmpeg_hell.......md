---
title: "FFmpeg hell......"
date: 2015-12-09
forum: Multimedia Software
---

### Post by dave_anderson2 on 2015-12-09
Trying implement a "tee" option in ffmpeg to do what should be a simple thing. I need to run a screen capture and feed it to two identical files, output.mpg and output2.mpg ( which are actually going to separate remote machines via network, I just called them such for simplicity)

```
[FONT=monospace][COLOR=#000000]$ ffmpeg -f alsa -i pulse -f x11grab -s 1920x1080 -i :0.0+1920,0 -target ntsc-dvd -aspect 16:9 -f tee "output.mpg|output2.mpg"[/COLOR]
[/FONT]
```

I get this:   ```
[FONT=monospace][COLOR=#FF5454]**Output file #0 does not contain any stream**[/COLOR]
[/FONT]
```

So I read till my eyes bleed and try various attempts at using  -map:

```
[FONT=monospace][COLOR=#000000]ffmpeg -f alsa -i pulse -f x11grab -s 1920x1080 -i :0.0+1920,0 -target ntsc-dvd -aspect 16:9 -f tee -map 0:v -map 0:a "output.mpg|output2.mpg" [/COLOR]
[/FONT]
```

Which yields this:\
```
[FONT=monospace][COLOR=#000000]Input #0, alsa, from 'pulse':[/COLOR][COLOR=#B26818]                                                                                                                                                                                                                                        [/COLOR][COLOR=#000000] [/COLOR]
  Duration: N/A, start: 1449638618.125236, bitrate: 1536 kb/s
    Stream #0:0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
Input #1, x11grab, from ':0.0+0,0':
  Duration: N/A, start: 1449638618.159890, bitrate: N/A
    Stream #1:0: Video: rawvideo (BGR[0] / 0x524742), bgr0, 1920x1080, 29.97 fps, 29.97 tbr, 1000k tbn, 29.97 tbc
[COLOR=#B21818]Stream map '0:v' matches no streams.[/COLOR]
[COLOR=#000000][/COLOR]
[/FONT]
```

I don't know if it's just a syntax issue or what but I'm not seeing it. I tried using -c copy (pipieline) but ffmpeg doesn't recognize -c: command.

Running Kubuntu 15.10.

---

### Post by coldraven on 2015-12-09
Would this work?
```
[FONT=monospace][COLOR=#000000]$ ffmpeg -f alsa -i pulse -f x11grab -s 1920x1080 -i :0.0+1920,0 -target ntsc-dvd -aspect 16:9 -f output.mpg && cp output.mpg output2.mpg[/COLOR][/FONT]
```

This should copy the output.mpg if ffmpeg succeeds.
> More precisely, && will evaluate the second expression **if the first expression returns 0**.  It's good to remember that not all commands use return value to  indicate success/failure — GNU diff, for example, returns 1 if two files  differ and 0 if they don't differ.
From here:
[http://stackoverflow.com/questions/4510640/command-line-what-is-the-purpose-of](http://stackoverflow.com/questions/4510640/command-line-what-is-the-purpose-of)

---

### Post by dave_anderson2 on 2015-12-10
That does work, however due to the way the system works, the files need to appear on the respective machines as simultaneously  as possible. I currently run 2 instances of the command at the same time, but I'm trying to conserve CPU. Also looking at a third output as an .mp4 @ 1080 for web upload .

---

### Post by coldraven on 2015-12-10
According to this link multiple outputs should be possible so I'm not sure what's going wrong unless you are using an old version of ffmpeg.
[https://trac.ffmpeg.org/wiki/Creating%20multiple%20outputs](https://trac.ffmpeg.org/wiki/Creating%20multiple%20outputs)

We shall have to wait for Fakeoutdoorsman to join the thread. He's the ffmpeg guru, for an example see here: [http://ubuntuforums.org/showthread.php?t=2299129&highlight=ffmpeg](http://ubuntuforums.org/showthread.php?t=2299129&highlight=ffmpeg)

---

### Post by sudodus on 2015-12-10
I agree that we should wait for Fakeoutdoorsman.

But I think there is an error with the tee command, that can be fixed without his help.

If you have two terminal windows you can test the following:

In one window you start the following command

```
tail -f ~/.bash_history|tee 1fil > 2fil
```

and in the other terminal window (run both windows in the same directory, for example your home directory) you can run various commands, for example

```
echo 'Hello World'
free
uname -a
echo 'Ready to inspect the result?'
cat 1fil
cat 2fil

```

You should see how the commands are added to the tail (end) of .bash_history which is copied/shown in the two output files "1fil" and "2fil". Try something similar with ffmpeg :-)

```
ffmpeg ... | tee "output.mpg" > "output2.mpg"
```

---

### Post by viewera on 2015-12-10
try this

```
ffmpeg -f alsa -i pulse -f x11grab -s 1920x1080 -i :0.0+1920,0 -target ntsc-dvd -aspect 16:9 -f tee -map 1:v -map 0:a "output.mpg|output2.mpg"
```

---

### Post by dave_anderson2 on 2015-12-10
Thanks much for the help, coldraven and sudodus,  I tried reading and assembling various commands to meet with one failure after another, and couldn't figure out why tee wasn't working. 

Then viewera comes along, changes a "0" to "1" and the thing works......go figure..... THANK YOU!!!  (I'll buy you a virtual beer!!):D

Amazing how one digit can make or break things...:lolflag:

FFmpeg is a powerful critter but you have to know how to feed it.

---

