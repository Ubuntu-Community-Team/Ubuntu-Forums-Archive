---
title: "Converting a video into SECAM norm?"
date: 2008-02-13
forum: Multimedia Production
---

### Post by bouligab on 2008-02-13
Hi, I need to convert a video (.avi, even if this doesn't mean anything) from its NTSC format to a SECAM format.

Does anyone know of a mean to do that?

I guess it would be possible with mencoder or vlc, in command-line, but as I have yet to learn the bases of the command-line internal logic, I'm not able to find how by myself.

---

### Post by theacoustician on 2008-02-13
I'm fairly certain you can do this in Avidemux.  However, I have to ask ... why?  The only reason I can think would be to burn the file to DVD for playback.  Otherwise, if you're only going to be watching this file on a PC, there's no need for format conversion.

---

### Post by Creative2 on 2008-02-13
secam as ntsc is only a combination of parameter for example 

ntsc support max  frame for second 30
 and 720 for 480 o someting like that

so for ntsc you should do this :

mencoder INPUT -ofps 30 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000 -vf scale -zoom -xy 720  -xvidencopts fixed_quant=4  -o OUTPUT

**for secam it [COLOR="Red"]SHOULD BE THIS [/COLOR]** I AM NOT SURE
*at the end of this there is a table *
[http://en.wikipedia.org/wiki/Secam#References](http://en.wikipedia.org/wiki/Secam#References)

i think with avidemux is very easy...you must only resize and set frame for second to 25, anyway with mencoder you could try with this 

```
mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000 -vf scale -zoom -xy 720  -xvidencopts fixed_quant=4  -o OUTPU
```

OR 
```

mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000 -vf scale  720:576  -xvidencopts fixed_quant=4  -o OUTPUT
```


if you know audio codec is mp3 you should try to leave audio without re-encoding so (to check i use ffmpeg -i  'INPUTFILE.AVI' 2>&1 |grep Stream )

```
mencoder INPUT -ofps 25 -ovc xvid -oac copy  -vf scale -zoom -xy 720  -xvidencopts fixed_quant=4  -o OUTPU
```

so as you can see is like PAL  i think  :)

---

### Post by bouligab on 2008-02-13
Great thanks! You made me understand a lot of points that were ambiguous in my little brain...

And yes, the purpose of the conversion is to grave a DVD!

I'm going to experiment with avidemux, and still, great thanks!

---

