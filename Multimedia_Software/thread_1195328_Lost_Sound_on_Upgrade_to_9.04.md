---
title: "Lost Sound on Upgrade to 9.04"
date: 2009-06-23
forum: Multimedia Software
---

### Post by kopolee11 on 2009-06-23
I recently upgraded my laptop to Ubuntu 9.04 Jaunty (yes I know I'm slow to the uptake) and everything went smoothly... except for the lost of sound. At first I tried restarting the computer, but that didn't work. 

Then I checked the Help documents and found a lot of good info. ([https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) if people are curious) However I still need help. Particularly at the part where I need find the correct codec for my soundcard. I'm not very adept at these things so instead I must appeal to you guys, the Ubuntu community. Thanks a lot. 

Here's some of my info just so you guys know. 

The output to ```
aplay -l
``` was ```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And my sound system info can be found [here]("http://www.alsa-project.org/db/?f=aaca27f4b78d6b618e43c29a8abdfd17303f657e"). Thanks a lot, and if you need any more information please let me know.

---

### Post by Aesculaius on 2009-06-23
ahhh you have that intel card.. I recently built a pc and Ubuntu reads it as the same.. if you go to ALSA's website and download the most current Driver, Util, and.. theres one other pkg you need to download.. compile them and install them from source.. after that you just need to run alsa to adjust your sound levels and it shooooooooould work... if you dont know how to compile from source...

```
sudo tar xjf nameofpkggoeshere
 cd nameofpkg (not including extension
 sudo ./configure
 sudo make
 sudo make install
```

assuming you get no errors during ./configure and make processes you should be in good shape.. ./configure will let u know if your missing anything you may need like for example if you need an updated gcc

---

### Post by raboofje on 2009-06-23
> **kopolee11 said:**
> However I still need help. Particularly at the part where I need find the correct codec for my soundcard. (...) my sound system info can be found [here]("http://www.alsa-project.org/db/?f=aaca27f4b78d6b618e43c29a8abdfd17303f657e")

That page mentions 'Codec: LSI ID 1040' and 'Codec: IDT 92HD71B8X'... I find neither of those in /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz though...

I assume you did check with (gnome-)alsamixer that the output channels are unmuted?

---

### Post by kopolee11 on 2009-06-24
Aesculaius: Thanks. I installed the latest driver, lib, and firmware with no problem. However, I got several errors for the Util during the "Make" stage. Specifically the output was: ```
Making all in include
make[1]: Entering directory `/home/kopolee11/Programs/Alsa_Codec_Crap/alsa-utils-1.0.20/include'
make  all-am
make[2]: Entering directory `/home/kopolee11/Programs/Alsa_Codec_Crap/alsa-utils-1.0.20/include'
make[2]: Leaving directory `/home/kopolee11/Programs/Alsa_Codec_Crap/alsa-utils-1.0.20/include'
make[1]: Leaving directory `/home/kopolee11/Programs/Alsa_Codec_Crap/alsa-utils-1.0.20/include'
Making all in alsactl
make[1]: Entering directory `/home/kopolee11/Programs/Alsa_Codec_Crap/alsa-utils-1.0.20/alsactl'
Making all in init
make[2]: Entering directory `/home/kopolee11/Programs/Alsa_Codec_Crap/alsa-utils-1.0.20/alsactl/init'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/kopolee11/Programs/Alsa_Codec_Crap/alsa-utils-1.0.20/alsactl/init'
make[2]: Entering directory `/home/kopolee11/Programs/Alsa_Codec_Crap/alsa-utils-1.0.20/alsactl'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT alsactl.o -MD -MP -MF ".deps/alsactl.Tpo" -c -o alsactl.o alsactl.c; \
	then mv -f ".deps/alsactl.Tpo" ".deps/alsactl.Po"; else rm -f ".deps/alsactl.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT state.o -MD -MP -MF ".deps/state.Tpo" -c -o state.o state.c; \
	then mv -f ".deps/state.Tpo" ".deps/state.Po"; else rm -f ".deps/state.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT utils.o -MD -MP -MF ".deps/utils.Tpo" -c -o utils.o utils.c; \
	then mv -f ".deps/utils.Tpo" ".deps/utils.Po"; else rm -f ".deps/utils.Tpo"; exit 1; fi
utils.c: In function ‘initfailed’:
utils.c:92: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
utils.c:93: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
utils.c:94: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
utils.c:95: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT init_parse.o -MD -MP -MF ".deps/init_parse.Tpo" -c -o init_parse.o init_parse.c; \
	then mv -f ".deps/init_parse.Tpo" ".deps/init_parse.Po"; else rm -f ".deps/init_parse.Tpo"; exit 1; fi
gcc  -g -O2   -o alsactl  alsactl.o state.o utils.o init_parse.o  -lasound -lm -ldl -lpthread
xmlto man alsactl_init.xml
/bin/bash: xmlto: command not found
make[2]: *** [alsactl_init.7] Error 127
make[2]: Leaving directory `/home/kopolee11/Programs/Alsa_Codec_Crap/alsa-utils-1.0.20/alsactl'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kopolee11/Programs/Alsa_Codec_Crap/alsa-utils-1.0.20/alsactl'
make: *** [all-recursive] Error 1

```

And this was after getting no error messages from the ./configure. So I'm not sure what I need. Any idea what the problem is?  

raboofje: Yeah I didn't find the codec in the ALSA-Configuration text either. That's what made me originally get help from the form. And yes I did make sure all the audio streams are unmuted, which they are according to alsamixer. Any other ideas?

Thanks a lot to you both. I really appreciate it.

---

### Post by Aesculaius on 2009-06-24
see that line that says /bin/bash: xmlto: command not found?
that means you need xmlto.. i think i saw it in the debian repo so if u cant apt-get it just download the .deb pkg and install it... i didnt have that problem however i used this fix with Super OS and not ubuntu.. Super OS is a modded ubuntu so maye i already had xmlto... im surprised ./configure didnt complain.. download that xmlto package then run make again.. maybe itl spit out new code to help debug it... also remember to run.. 
```
sudo make clean 
``` to undo everything you did for the utils build

---

### Post by Yellow Pasque on 2009-06-24
There's a script to build ALSA from source: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by Aesculaius on 2009-06-25
Pfft whats the fun in using a script? Building from source is fun!

---

### Post by AsianSpanker on 2009-07-05
Now what percent of the people in the world know how to build from source? And of those, what percent think it is fun to spend days trying to figure out why Ubuntu looses sound, or can't perform the smae task today, that it did yesterday? I like Ubuntu because it is a sturdy OS that doesn't change every time I boot up, like the evil empire OS.
I bought a Dell Inspiron 1525 with Ubuntu installed. It worked well. I liked it. I felt I was contributing to something I believed in. But every up-date has made the system less stable. I loose the sound. Update. Works for awhile. Then I loose the sound again, right after some update.
I don't think the Ubuntu community only wants computer geeks to be able to use the system, but also wants regular guys who have families, jobs, responsibilities to be able to use it also?
But after wiping my system 2 times to get it to work right, I am beginning to wonder.
I don't know too many people who want a fresh install every month. Most people I know just want to turn on their computer and get things done.

---

### Post by rtalcott on 2009-07-05
I ran the script and still have no sound....I am sure I still need to do something else...I have un-muted the digital outputs using alsamixer.
rt

iec958:CARD=SB,DEV=0
    HDA ATI SB, STAC92xx Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

---

