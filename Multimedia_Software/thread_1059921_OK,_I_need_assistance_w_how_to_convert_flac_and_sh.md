---
title: "OK, I need assistance w/ how to convert flac and shn"
date: 2009-02-04
forum: Multimedia Software
---

### Post by missbliss on 2009-02-04
Even though I've read through some tutorials, I can not seem to figure out how to convert my flac's and shn's to something burnable like mp3 or wav.

Any help?

I just tried this tutorial:

[http://www.simplehelp.net/2008/12/11/how-to-convert-flac-files-to-mp3-using-ubuntu-linux/](http://www.simplehelp.net/2008/12/11/how-to-convert-flac-files-to-mp3-using-ubuntu-linux/)

But, when I place the files in the converter it crashes before converting anything.

---

### Post by cozmicharlie on 2009-02-04
shn files are not well supported anymore because it is an older codec but there are a few apps that can convert shn.  Both rely on installing the shn codec.  Two options I like for converting in linux are PACPL and SoundKonverter (with a k not a c - this is a kde program but it works fine in gnome).  

shn codec:  Install the shn codec.  Follow the instructions:

Open a terminal
At the prompt type or cut and paste the following commands

Download the shn codec to your home folder:
```
$ wget http://www.etree.org/shnutils/shorten/dist/src/shorten-3.6.1.tar.gz
```

untar the package
```
$ tar xvf shorten-3.6.1.tar.gz
```

Change to the directory you just untarred
$ ```
cd shorten-3.6.1
```

Install - write each command one line at a time 
```
$ ./configure 
$ make
# sudo make install
```

Now the shn codec should be installed

To convert you have a few options.  I like PACPL but Soundkonverter also works good and has a GUI interface so chose which one you like (if you search the forums you will also find methods using ffmpeg).

PACPL is a command line app but it is easy - follow the instructions here to install:  [http://ubuntuforums.org/showthread.php?t=712064](http://ubuntuforums.org/showthread.php?t=712064) 

Once you install PACPL, you use it from the command line.  So for example if I have a music file named mymusic.shn and I want to convert it to mp3:

Open a terminal

At the prompt type:
```
$ pacpl --to mp3 /home/music/mymusic.shn
```

Thats it.  PACLP has many features.  To get a list of all available options type:
```
$ pacpl --longhelp 
```

Install the flac codec from Synpaptic.  Search for flac and install.  

SoundKonverter: Install from Synaptic. 

To play shn you only have a few options.  I like xmms - follow this tutorial:
[http://ubuntuforums.org/showthread.php?t=833164](http://ubuntuforums.org/showthread.php?t=833164)

Post back if you need further help

Enjoy

---

### Post by amy s on 2010-03-01
Ok. First of all, thank you for these directions. But I'm having a problem with PACPL.  When I try to convert, it says "could not find suitable application to decode :shn"

What can I do about this? I've tried converting shn files to FLAC with shntool, but kept getting permission errors, and now with PACPL, I keep getting this error. 

Please help!

---

### Post by Yellow Pasque on 2010-03-01
Permission errors? Do you have permissions to the file/directory? Did you try to prefix the commmand with sudo? Terminal output would be useful..

---

### Post by cozmicharlie on 2010-03-01
> **Temüjin said:**
> Permission errors? Do you have permissions to the file/directory? Did you try to prefix the commmand with sudo? Terminal output would be useful..

Yes it sounds like the permissions on the audio file (the flac or shn files).  If you follow his instructions and it works when you sudo then the owner of the files is root and they need be changed to user.  Also, go to /usr/local/bin - do you see shorten bin file?  Can you play the shn or flac files from an audio player?

---

