---
title: "No Success with WinFF - already installed  libavcodec-extra-52"
date: 2010-01-30
forum: Multimedia Software
---

### Post by DiegoDeEscocia on 2010-01-30
Hey all.

I'm having no success converting several files I wished to with WinFF. I'm on 9.10 Karmic Koala, all latest updates, and I've installed ffmpeg, WinFF, and libavcodec-extra-52....

I've been using the gui but elected to have it show the response from the terminal commands:

```
#!/bin/sh
echo -n "\033]0; Convirtiendo Death Note_ Episodio 27, Secuestro (parte 1_3) Castellano.m4v (1/1)\007"
/usr/bin/ffmpeg -threads 2 -i "/media/windows/Documents and Settings/Iain/dwhelper/Death Note_ Episodio 27, Secuestro (parte 1_3) Castellano.m4v" -acodec libmp3lame -ab 160kb -ac 2 -ar 44100 "/home/diego/Death Note_ Episodio 27, Secuestro (parte 1_3) Castellano.mp3"
read -p "Pulse Entrar para continuar." dumbyvar
rm "/home/diego/.winff/ff100131005346.sh"
```Here is one. I tried to simply extract the audio to MP3. 


Here is another conversion I was trying to do to an ipod classic optimised video format:

```
#!/bin/sh
echo -n "\033]0; Convirtiendo Bleach 011 El Legendario quincy.avi (1/1)\007"
/usr/bin/ffmpeg -threads 2 -i "/home/diego/Descargas/Bleach 011 El Legendario quincy.avi" -r 29.97 -vcodec libx264 -flags +loop -cmp +chroma -deblockalpha 0 -deblockbeta 0 -crf 21 -bt 256k -refs 1 -coder 0 -me_method full -me_range 16 -subq 5 -partitions +parti4x4+parti8x8+partp8x8 -g 250 -keyint_min 25 -level 30 -trellis 2 -sc_threshold 40 -i_qfactor 0.71 -s 320x240 -aspect 4:3 -acodec libfaac -ab 112kb -ar 48000 -ac 2 "/home/diego/Bleach 011 El Legendario quincy.m4v"
read -p "Pulse Entrar para continuar." dumbyvar
rm "/home/diego/.winff/ff100131005543.sh"
```
Appologies for the spanish line - that's the language Ubuntu is currently running in (I can change it to English if need be).

Convirtiendo Bleach 011 - means converting Bleach 011 etc....

and 'Pulse Entrar para continuar' means - 'press enter to continue'


Any help would be much appreciated folks.....

---

### Post by LuridCinema on 2010-01-30
I had some issues w/ getting a good quality result w/ Winff. I have had bettter results using ffmpeg alone. With ffmpeg I have had to experiment. I have had good results using the " -sameq "  switch and keeping the other parameters minimal. Some times I have had to use several settings ( swithces ) to get good results. i have a text document and have kept notes on the results.

However , I have had luck in using Audacity to open the audio from video files and convert to any formay supported. I   just did a test of an .avi file and was able to open in Audacity and save as .mp3, so give that a try 1

Good Luck o Buena Suerte !!!

---

### Post by DiegoDeEscocia on 2010-01-31
Thanks for the suggestion I'll give audacity a try for that! I used to do it for FLV's though it seemed to be quite a slow way of going about it. I'd forgotten about it completely though.

The most useful function for me of WinFF has to be the presets, as I often want to optimise the files for playing on an ipod classic screen, or my PSP or something like that.

If I were getting something meaningful out the other side of the process it would at least be better than having no reaction when I ask WinFF to convert.

Is there a way to figure out the command I need to enter in terminal by using WinFF but enter it manually so that I can take advantage of the pre-settings?

I assume it's part of that massive text I posted up earlier on?

I'd much rather get the gui working - as I get lazy when wanting to set up a batch of them to convert when I go to bed ;-) but if it comes down to it I'm happy to go oldschool with the commandline (it's the settings I'll need to optimise for various devices that are intimidating!)

---

### Post by FakeOutdoorsman on 2010-01-31
You were on the correct path by installing **libavcodec-extra-52**, but the version of this package from the official Ubuntu repository does not support encoding to AAC audio.  This is the audio format that your iPod classic preset uses.

The good new is that Medibuntu offers a version of **libavcodec-extra-52** that does support AAC (and AMR audio as well).  Installing this should allow your iPod preset to work.  See Option C in:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by DiegoDeEscocia on 2010-02-12
Thanks for your help (and sorry for the late reply! I had exams!). I've followed option c but still can't get WinFF to behave any differently....????

I would rather get the Gui working....

but if not does anyone know what the command line entry I'd have to use is to convert whatever a video happens to be in to a video format optimised for the ipod classic screen size? Because all of this codec stuff can be so confusing!

Thanks again for your help!

---

### Post by DiegoDeEscocia on 2010-02-13
Ok I tried taking the command output from winff pasted above:

/usr/bin/ffmpeg -threads 2 -i "/home/diego/Descargas/Bleach 011 El Legendario quincy.avi" -r 29.97 -vcodec libx264 -flags +loop -cmp +chroma -deblockalpha 0 -deblockbeta 0 -crf 21 -bt 256k -refs 1 -coder 0 -me_method full -me_range 16 -subq 5 -partitions +parti4x4+parti8x8+partp8x8 -g 250 -keyint_min 25 -level 30 -trellis 2 -sc_threshold 40 -i_qfactor 0.71 -s 320x240 -aspect 4:3 -acodec libfaac -ab 112kb -ar 48000 -ac 2 "/home/diego/Bleach 011 El Legendario quincy.m4v"
read -p "Pulse Entrar para continuar." dumbyvar
rm "/home/diego/.winff/ff100131005543.sh"

And deleting out:

"Pulse Entrar para continuar." dumbyvar
rm "/home/diego/.winff/ff100131005543.sh" 

(I actually also changed it to a different file which wasn't working with WinFF either....)

I made the remaining text a script with nano, entered it 'sudo chmod a+x' to give it executable powers and ran it....

It seems to be presently converting that one video....

So far so good.

But why won't WinFF work? I've got massive batches of files to convert so I'd really value not having to enter them all manually! :-/

Anyone got any ideas/suggestions?

---

### Post by DiegoDeEscocia on 2010-02-18
Help pretty pretty please :-)!

Thanks all! ;-)

At least I can sort of convert them now...albeit in a longhanded laboreous way...

---

