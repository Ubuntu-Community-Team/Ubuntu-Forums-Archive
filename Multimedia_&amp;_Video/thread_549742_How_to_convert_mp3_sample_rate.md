---
title: "How to convert mp3 sample rate?"
date: 2007-09-13
forum: Multimedia &amp; Video
---

### Post by ELMIT on 2007-09-13
I got the bible as mp3 files, like:

Audiobible Old Testament - 17 Esther - Old_17_Esther_05.mp3
Audiobible Old Testament - 17 Esther - Old_17_Esther_06.mp3
Audiobible Old Testament - 17 Esther - Old_17_Esther_07.mp3

(note the spaces within the names)

I tried for testing:
sox "bible-22050/Audiobible New Testament - 01 Matthew - New_01_Matt_01.mp3" -r44100 "bible-44100/Audiobible New Testament - 01 Matthew - New_01_Matt_01.mp3"
sox: Failed writing bible-44100/Audiobible New Testament - 01 Matthew - New_01_Matt_01.mp3: Sorry, no MP3 encoding support

ronald@ronald-cs-laptop:~/temp$ sox --help
sox: Version 12.18.2
....
Supported file formats: aiff al alsa au auto avr cdr cvs dat vms gsm hcom la lu maud mp3 nul ossdsp prc raw sb sf sl smp sndt sph 8svx sw txw ub ul uw voc vorbis vox wav wve 

Supported effects: avg band bandpass bandreject chorus compand copy dcshift deemph earwax echo echos fade filter flanger highp highpass lowp lowpass mask mcompand noiseprof noisered pan phaser pick pitch polyphase rate repeat resample reverb reverse silence speed stat stretch swap synth trim vibro vol 

effopts: depends on effect



Questions:
1. why it says it does not support mp3, while sox --help says it does? Or is it a syntax error in my command?
2. how can I convert all 1161 mp3 files? (there are spaces in the name)


Thanks for your help!

bye

Ronald

---

### Post by jnorthr on 2007-09-13
Is it possible you are missing a codec for mp3 files ? start here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)

Here is another link i found about sox - it may help but dunno : [http://www.extremetech.com/article2/0,1697,2126264,00.asp](http://www.extremetech.com/article2/0,1697,2126264,00.asp)

don't know much about sox myself except that the "White Sox extended manager Ozzie Guillen's contract through 2012 on Tuesday even though the team is tied for the worst record in the major leagues." [http://www.freep.com/apps/pbcs.dll/article?AID=/20070912/SPORTS12/709120362/1050/SPORTS02](http://www.freep.com/apps/pbcs.dll/article?AID=/20070912/SPORTS12/709120362/1050/SPORTS02)
:)

---

### Post by ELMIT on 2008-05-24
mp3 is installed, ... otherwise I could not play any mp3. I can use them. I need to convert them to another sample rate, because the sc_streaming program can not use 22050 bit rate.

---

