---
title: "no sound with realtek high definition audio card"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by mrxtambourineman on 2008-01-12
I just recently installed ubuntu 7.1 and ubuntu is unable to recognize my video card. I have a toshiba a215 series laptop with ati mobo (i think). In windows my sound card was called a realtek high definition. Now, I have tried to update with the realtek drivers from their page. I used the automatic install. However, this did not fix the problem. Perhaps I did something wrong? At the end it said something like alsaconfig or alsamixer not found. When I do sudo lshw -class sound, this is what i get:

  *-multimedia            
       description: Audio device
       product: SBx00 Azalia
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel

Does anyone have any suggestions? I would greatly appreciate any feedback received.

edit: also tried doing the manual install, but got errors. I successfully configured and installed the new 1.0.15 libraries, but when I tried to ./configure alsa-utils 1.0.15 i get an error saying it requires curses libraries. Does anyone know how to fix this?

Edit: Got past the configure, but when i try make install I get: 

make[2]: Leaving directory `/home/eric/Desktop/alsa-utils-1.0.15/alsactl'
make[1]: Leaving directory `/home/eric/Desktop/alsa-utils-1.0.15/alsactl'
Making install in alsaconf
make[1]: Entering directory `/home/eric/Desktop/alsa-utils-1.0.15/alsaconf'
Making install in po
make[2]: Entering directory `/home/eric/Desktop/alsa-utils-1.0.15/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/home/eric/Desktop/alsa-utils-1.0.15/alsaconf/po'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/eric/Desktop/alsa-utils-1.0.15/alsaconf'
make: *** [install-recursive] Error 1

Fixed the above problems. Got to the alsa sound config window when autointalled and everything,but still unable to get sound

---

### Post by c0met on 2008-01-12
Hi,

I'm very much not an expert in this stuff, but I have a couple of suggestions below that might or might not help. 

Open the[COLOR="DarkRed"]** Synaptic Package Manager**[/COLOR]  (System >> Administration). Do a search for Alsa and see if (a)  [COLOR="Purple"]**Alsa-base**[/COLOR] and (b) [COLOR="Purple"]**Alsa-utils**[/COLOR] are installed. If these are installed, try [COLOR="DarkRed"]**System >> Preferences >> Sound**[/COLOR] and see what devices are listed as being used for the various events. You could try changing to driver that has (Alsa) in its name and see if that makes a difference.

---

### Post by c0met on 2008-01-12
Also, the below link was written for an earlier version of Ubuntu, but it might be useful.

[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by mrxtambourineman on 2008-01-12
Tried your suggested website. Tried the command: cat /proc/asound/card0/codec\#* but it told me:
eric@portablevegan:~$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory
eric@portablevegan:~$ 
eric@portablevegan:~$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory
eric@portablevegan:~$ 
eric@portablevegan:~$ cat /proc/asound/card0/codec\#*
cat: /proc/asound/card0/codec#*: No such file or directory
eric@portablevegan:~

---

