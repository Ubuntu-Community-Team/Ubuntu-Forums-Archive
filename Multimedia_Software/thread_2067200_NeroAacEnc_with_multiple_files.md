---
title: "NeroAacEnc with multiple files"
date: 2012-05-11
forum: Multimedia Software
---

### Post by Morty-L on 2012-05-11
It should be possible to use Asunder and NeroAACEnc as encoder, but I have not been able to figure out where to put the contents of the zip-file from Nero.

Any pointers?

Error message:
'neroAacEnc' was not found in your path.  Asunder requires it to produce MP4 files.  All AAC functionality is disabled.

---

### Post by shantiq on 2012-05-11
Place your neroAacEnc    in /usr/bin    Morty


it seems it needs to be there

also needs to be made executable    i tried to run it and good it went but no tagging in Asunder for me...


you may know this already:KS:KS


```
sudo cp neroAacEnc /usr/bin  

```
```
cd /usr/bin  

```
```
sudo chmod +x neroAacEnc 
```




Anyway another route available to you to is [**Rubyripper**]("http://linuxappfinder.com/package/rubyripper") **and it will tag**

with this line of code in the "other" box


> neroAacEnc -q 1 -if %i -of %o.m4a && neroAacTag %o.m4a -meta:artist=%a -meta:album=%b -meta:genre=%g -meta:year=%y -meta:track=%n -meta:title=%t


For this you will need [**neroAacTag** ]("http://www.nero.com/eng/downloads-nerodigital-nero-aac-codec.php")and also place it in /usr/bin and make executable


Thanx to Mc4man for showing me all this a while back :KS

---

### Post by Morty-L on 2012-05-13
Thanks a lot, Shantiq!  Didn't know this.

---

### Post by Morty-L on 2012-09-16
[COLOR=Blue]Hi again,

I still have a problem.  I now have placed the files in /usr/bin as instructed.

I get this error in the asunder.log:[/COLOR]
sigchld completed 
Encoding track 12 to "/media/Sea1TBB/Musikk/Silje Nergaard - Port Of  Call/12 - Silje Nergaard - Don't Explain.m4a" 
8059 started: neroAacEnc -q 0.60 -if /media/Sea1TBB/Musikk/Silje  Nergaard - Port Of Call/12 - Silje Nergaard - Don't Explain.wav -of  /media/Sea1TBB/Musikk/Silje Nergaard - Port Of Call/12 - Silje Nergaard  - Don't Explain.m4a 
w11 (8059) 
sigchld for 8059 (know about wav 0, mp3 0, ogg 0, flac 0, wv 0, ape 0,  mpc 0, m4a 8059 
8059 exited with 32512: **exited, status=127 **
sigchld completed 
Saving configuration  
[COLOR=Blue]
The cd is ripped to .wav and .flac format, but there are no .m4a files.

I have looked for a solution for a long time, but it looks as if I am the only one with this problem.  I am thinking that I might have the wrong version of the neroaacenc file?[/COLOR]

---

### Post by Morty-L on 2012-10-06
I found a solution to this problem:
installed 
lib32stdc++6

That fixed the problem, and I can now rip to three (or more) different formats at the same time using Asunder in my 64-bit version of Ubuntu: .wav, .flac, and .m4a

Thanks to Andrew Smith for helping me!

---

### Post by andrew.46 on 2012-11-30
Those interested in NeroAacEnc may be interested to know that I am working on a patch to submit upstream to enable aac encoding with NeroAacEnc for the commandline ripper abcde. Should help breathe even more life into this great ripper hopefully :).

---

### Post by cottfcfan on 2013-01-01
Thanks Shantiq. Works perfect with Rubyripper.

---

