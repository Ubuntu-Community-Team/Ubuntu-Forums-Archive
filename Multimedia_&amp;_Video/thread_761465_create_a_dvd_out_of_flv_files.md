---
title: "create a dvd out of flv files"
date: 2008-04-21
forum: Multimedia &amp; Video
---

### Post by Circus-Killer on 2008-04-21
i currently have lots and lots of flv files, which i would like to make a full dvd, along with a dvd menu if possible.

my problem is i dont know where to start or what programs i need.

i would like someone to tell me what packages i will need, along with basic instructions on how i can get my flv files to dvd. i do not want to keep the files as flv. i want them to be converted to .vob files (or whatever files dvds use).

basically, i want to create a dvd out of those flv files that will work on most dvd players.

---

### Post by Circus-Killer on 2008-04-22
*bump*

---

### Post by Circus-Killer on 2008-04-22
*last attempt bump*

---

### Post by Prefader on 2008-04-22
I'd say your first step would be to convert all those flv files into mpegs.  I usually use ffmpeg for this sort of thing:
```
ffmpeg -i filename.flv -target ntsc-dvd filename.mpg
```
Use -target pal-dvd if that's appropriate for your location.

###EDIT###
I just noticed that flash video created with the vp6 codec doesn't appear to work with ffmpeg.  Try using mencoder, with this command:
```
mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -vf scale=720:480,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:vstrict=0:acodec=ac3:abitrate=192:aspect=16/9 -ofps 30000/1001 -o filename.mpg filename.flv
```
Make sure you change the "aspect=16/9" section to match your source clip - usually 4/3.
###EDIT #2###
Just noticed you're located in S. Africa, so here's the code for a PAL conversion:
```
mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -vf scale=720:576,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=15:vstrict=0:acodec=ac3:abitrate=192:aspect=16/9 -ofps 25 -o filename.mpg filename.flv
```
Then, try using something like qdvdauthor or devede (both available via apt - make sure you've got multiverse enabled).  I haven't used either one in a long time, but they should work for you.

---

### Post by Circus-Killer on 2008-04-23
thanks so much, will give it a bash and report back. ;)

---

### Post by Circus-Killer on 2008-04-23
alright, i tried the suggestion but there was a problem when converting from flv to mpg.

the video on the mpg comes out fine. however, the audio is full of static and noise. you can barely hear the actual audio over all the noise. wondering how i might stop this?

---

### Post by Prefader on 2008-04-24
Can you post the output of this command, using one of the original .flv files?
```
mplayer -vo null -ao null -frames 0 -identify filename.flv
```
Also, which program did you end up using to convert the file - ffmpeg, or mencoder?

---

### Post by Circus-Killer on 2008-04-30
okay, when i retried mencoder in hardy, there were no sound problems in the conversion. ;)

---

### Post by Prefader on 2008-04-30
Glad to hear it worked!

---

### Post by akadruid on 2008-05-17
> **Prefader said:**
> 
here's the code for a PAL conversion:
```
mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -vf scale=720:576,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=15:vstrict=0:acodec=ac3:abitrate=192:aspect=16/9 -ofps 25 -o filename.mpg filename.flv
```
Then, try using something like qdvdauthor or devede (both available via apt - make sure you've got multiverse enabled).
Thank you for posting this, I'm trying to to do the same thing and the conversion worked fine for me.  The output .mpg file was almost 1GB for a 175mb .flv, not a problem for me but worth noting.

Turning it into a DVD has proved much harder though:
[LIST]qdvdauthor 1.0 from the repository did not work for me using Hardy x64, it just segfaults on startup. I was able to download the .deb for 1.20 from [http://www.getdeb.net/app/QDVDAuthor](http://www.getdeb.net/app/QDVDAuthor), which worked OK.
[/LIST]
[LIST]I did not find qdvdauthor all that easy to use, but after some fiddling I was able to generate an iso image. Unfortunately it won't burn, just gives this error:
```
BraseroGrowisofs stderr: /dev/hda: engaging DVD-R DAO upon user request...
BraseroGrowisofs stderr: :-[ PERFORM OPC failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 133
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record burn.c:2273)
``` It plays in VLC if you loopback mount the iso though. 
[/LIST]
[LIST]I also tried KMediaPlayer, which looked nice at first, but I spent quite a lot of time with it and could not get a burnable file from it. 
[/LIST]
[LIST]I installed tovid and todiscgui but I admit I could not figure out the interface and gave up.
[/LIST]

I'm given up on this project for now, I plan to revisit it when I have more time.

Does anyone know of a more idiot-proof tool? Or least with a smaller learning curve?

(To my mind, an ideal tool would be more like audio CD burning tools - i.e. where the default is just a way of adding files plus a burn button. Presumably the tool would have to create a basic menu for you - just a list of the files plus a 'play all' button - but that doesn't sound like rocket science?)

---

