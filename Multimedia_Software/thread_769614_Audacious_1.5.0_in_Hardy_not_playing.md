---
title: "Audacious 1.5.0 in Hardy not playing"
date: 2008-04-26
forum: Multimedia Software
---

### Post by evolipel on 2008-04-26
After installing Audacious from the official Hardy repos on a fresh Hardy install, it doesn't seem to play. It just stops at 00:00 and doesn't advance on anything that I try. Internet radio, local files (of various formats), a CD -- all of it is just at 00:00.

I've tried fiddling with the output plugins (both the PulseAudio and the ALSA outputs do the same thing) to no avail. I've also tried random other options like the sampling rate converter, bit depth, and such -- didn't help.

Running it from a console doesn't give any pertinent errors or warnings or notifications or anything, even with the -N option.

Audacious 1.2.something from the official Gutsy repos and Audacious 1.4.2 from getdeb both ran perfectly well under Gusty.

All the other sound/multimedia programs work just fine under Hardy. Once again, this was a clean format/install; I think upgrading is too messy.

Also (not sure if this is relevant), it used to segfault anytime I tried to open it because I also installed audacious-crossfade. Apparently there's a bug in audacious-crossfade that caused that; I uninstalled it, and at least it now opens.

Finally, if I click "Reload Plugins" from Preferences, it segfaults (doesn't say anything useful, though). Also not sure if this is related.

---

### Post by rhauff on 2008-05-08
Sorry I can't help, but I've got similar problems and tried switching to alsa as you did(among many other things) to no avail.  Mine will play MP3 and AAC streams and local files, but Ogg .m3u's (playlists) delay about 30 seconds before playing and when skipping through.  Ogg files play fine however.

I've got this problem on two systems:
1. Xubuntu 7.10 w/ Audacious 1.45
2. Xubuntu 8.04 w/ Audacious 1.50

---

### Post by rhauff on 2008-05-08
I just confirmed this problem on my kid's PC running Kubuntu 7.10 also, with Audacious 1.4.5

---

### Post by lancern on 2008-05-08
same here on xubuntu 8.04..I cant do anything with the thing..it keeps crashing..not that I care about using it,,I just read about it here in a thread and tried it out a few days ago..It must still be in alpha testing are something..You can use other players for inet radio.xmms still works..saw a .deb on here somewhere for it..

---

### Post by cikson on 2008-05-13
I have same problem
> **evolipel said:**
> 
Running it from a console doesn't give any pertinent errors or warnings or notifications or anything, even with the -N option.

All the other sound/multimedia programs work just fine under Hardy. Once again, this was a clean format/install; I think upgrading is too messy.

but my output is:
```
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

```
I hope this can help.

---

### Post by Major_Kong on 2008-05-13
Err... you have to change the output plugin to pulseaudio. Open the preferences window, and in the Audio options, choose PulseAudio Output Plugin, as the current output plugin.

It's more of a packaging bug, than a audacious bug.

---

### Post by javaguru on 2008-06-19
> **Major_Kong said:**
> Err... you have to change the output plugin to pulseaudio. Open the preferences window, and in the Audio options, choose PulseAudio Output Plugin, as the current output plugin.

It's more of a packaging bug, than a audacious bug.

Wrong, this doesn't solve anything. It's just as dead as before. I get:

```
adyhasch@jenna:~/Desktop/mp3$ audacious 
Failed to load plugin (/usr/lib/audacious/Input/amidi-plug.so): /usr/lib/audacious/Input/amidi-plug.so: undefined symbol: audacious_drct_get_playing
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

``` in Audacious 1.5.1
Everything works fine when executed by root.

---

### Post by javaguru on 2008-06-19
actually you just need to :
1. Uninstall audacious
2. Remove the old configuration directories which reside in your home dir
3. Reinstall audacious

> 
adyhasch@jenna:~$ apt-get remove audacious
adyhasch@jenna:~$ rm -r .audacious/ /home/adyhasch/.config/audacious /home/adyhasch/.cache/audacious  home/adyhasch/.local/share/audacious /home/adyhasch/.local/share/applications/audacious-usercustom-usercustom-1.desktop
adyhasch@jenna:~$ apt-get install audacious


now you've hopefully wiped all traces of audacious, and got a clean install.

---

### Post by JPorter on 2008-06-22
I've found (on my system at least) that it is a problem with the [FONT="Courier New"] [COLOR="DimGray"]audacious-plugins-extra[/COLOR] [/FONT] package.  I uninstalled that one (left the regular [FONT="Courier New"] [COLOR="DimGray"]audacious-plugins[/COLOR] [/FONT]) and everything seems to work perfectly.

---

### Post by Odrodzona-Sarmacja on 2008-06-22
> **javaguru said:**
> actually you just need to :
1. Uninstall audacious
2. Remove the old configuration directories which reside in your home dir
3. Reinstall audacious

now you've hopefully wiped all traces of audacious, and got a clean install.

It won't work for segfault. You need
1. Totally Uninstall audacious with configuration files too
2. Reboot computer
3. Install audacious.

Actually this will work with every application on Ubuntu, which doesn't want to work because of "segfault". The only exception is synaptic manager, there you instead need remove just two files from its cash to make it work again.

Ps. And audacious tends to play for hours without problem... You just need to push "play" few times in beginning when it "mysteriously" stops.

---

### Post by kuric on 2008-08-23
I had this problem after installing LiVES (the video editor, wich also brings XMMS).

Is there any incompatibility between XMMS and Audacious? I guess Audacious has to be installed (or reinstalled) after XMMS/LiVES. Someone has an explanation for this? :?

The solution above worked with me. I have uninstalled Audacious and manually deleted: 
/home/%username%/.cache/audacious
/home/%username%/.config/audacious
/home/%username%/.local/share/audacious
Then reboot... and finally install Audacious again. That's it. 
But I don't know yet if this will be a permanent solution.

---

### Post by dreadmeat on 2008-09-03
similar issues here
> audacious 1.5.0
xubuntu 8.04.1
mp3 files

the thing will just stop playing mid song
the audacious forums look like a waste of time.
maybe the developer is too busy?
this post here illustrates what happens here

[http://boards.nenolod.net/viewtopic.php?f=4&t=39](http://boards.nenolod.net/viewtopic.php?f=4&t=39)

---

### Post by dreadmeat on 2008-09-05
aaaw man, it just stopped again.
played about 4 albums then stopped midway through the 30th track.


edit, and again just now.
i'm not doing anything cpu or network intensive.

---

### Post by coskierken on 2008-09-06
Had, repeat had tried everything and enough hair gone, the problem.  Finally found it.  According to the xmms error, it could not find the correct audio output.  So, I found the config file and it was defaulted to pulse audio.  I changed it to ALSA.so and all is well.  But, looked in preferences in Audacious and you are able to change it there.  I did not try this to see what happens.  Hope this help!

---

### Post by dreadmeat on 2008-09-06
> **coskierken said:**
> Had, repeat had tried everything and enough hair gone, the problem.  Finally found it.  According to the xmms error, it could not find the correct audio output.  So, I found **the config file** and it was defaulted to pulse audio.  I changed it to ALSA.so and all is well.  But, looked in preferences in Audacious and you are able to change it there.  I did not try this to see what happens.  Hope this help!which 'config file' did you change?

---

### Post by linuxchemist on 2008-10-11
I had the same problem and solved it with the following steps:

1) Uninstall audacious and remove all relative settings and directories:
sudo apt-get remove --purge audacious
rm -r .audacious/ /home/%username%/.config/audacious /home/%username%/.cache/audacious home/%username%/.local/share/audacious /home/%username%/.local/share/applications/audacious

2) Install PulseAudio
Go to the Add-Remove programs and install
PulseAudio Device Chooser
PulseAudio Volume Control
PulseAudio Volume Meter (Playback)
PulseAudio Volume Meter (Capture)
PulseAudio Manager

3) Install audacious again
sudo apt-get install audacious

4) Run "Appcliations"-> "Multimedia" -> "PulseAudio Device Chooser"
or type on terminal padevchooser and run
On tray icon will appear PulseAudio applet

5) Now run audacious and in preferences in Audio Output choose PulseAudio Output Plugin
Now open some mp3 song with audacious and while it plays without sound make left click on tray icon of PulseAudio Applet and choose Volume Control. on card "Playback" choose your device and sound will appear immediately. Good luck!

---

### Post by dreadmeat on 2008-10-11
heh, i just switched to OSS output :p

---

### Post by spooner on 2008-10-15
I had this error and I solved using the removeal and reinstallation. I don't think it was an output problem as audacious was still playing flac files fine just not ogg or mp3... I hate this type of bug!

---

### Post by SjoerdC on 2008-10-18
> **kuric said:**
> I had this problem after installing LiVES (the video editor, wich also brings XMMS).

Is there any incompatibility between XMMS and Audacious? I guess Audacious has to be installed (or reinstalled) after XMMS/LiVES. Someone has an explanation for this? :?

The solution above worked with me. I have uninstalled Audacious and manually deleted: 
/home/%username%/.cache/audacious
/home/%username%/.config/audacious
/home/%username%/.local/share/audacious
Then reboot... and finally install Audacious again. That's it. 
But I don't know yet if this will be a permanent solution.

that worked for me!

---

### Post by Artemis3 on 2008-10-18
I suggest you remove audacious 1.5.0 and install the newer 1.5.1 version from [getdeb](http://www.getdeb.net/).

---

