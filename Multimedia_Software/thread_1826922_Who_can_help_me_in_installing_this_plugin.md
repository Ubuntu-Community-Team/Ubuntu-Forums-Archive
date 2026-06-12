---
title: "Who can help me in installing this plugin?"
date: 2011-08-17
forum: Multimedia Software
---

### Post by Edoardo_P on 2011-08-17
Hello, I just don't know where to start with this.

It's an audio plugin that should work with ALSA and other stuff...

my terminal does not recognize the very first command, maybe because it's for another distro

download page:
[http://sourceforge.net/projects/bs2b/files/](http://sourceforge.net/projects/bs2b/files/)

tutorial and troubleshooting:
[http://www.rpgameplace.de/blog/index.php?/archives/21-Stereo-to-binaural-with-ALSA-using-bs2b-LADSPA-plug-in.html](http://www.rpgameplace.de/blog/index.php?/archives/21-Stereo-to-binaural-with-ALSA-using-bs2b-LADSPA-plug-in.html)

I'm using Ubuntu 10.10 32bit

thanks a lot for anyone who may help me

---

### Post by .... on 2011-08-17
Your terminal doesn't recognize the cd command because you're not putting in the right directory. Anyway, libbs2sb is already packaged for maverick here: [https://launchpad.net/~lazka/+archive/dumpingplace/+packages](https://launchpad.net/~lazka/+archive/dumpingplace/+packages)
Debian also keeps libbs2b in its repo: [http://packages.debian.org/source/sid/libbs2b](http://packages.debian.org/source/sid/libbs2b)

As far as configuring your install to use this system-wide, you would have to run it through pulseaudio (or remove pulseaudio). This thread might help: [http://ubuntuforums.org/showthread.php?t=1308838](http://ubuntuforums.org/showthread.php?t=1308838)

Personally, I just recompiled my music program (audacious) to use it. You can also get a gstreamer plugin in that PPA so gstreamer programs (rbox, exaile, guayadeque, totem, etc.) can use it.

---

### Post by Edoardo_P on 2011-08-17
forgive me I'm a complete beginner I would not know how to recompile anything... Can you help me in installing the maverick package? I've just downloaded it and looked for it in the ubuntu sw center and in the repositories but nothing works

---

### Post by Edoardo_P on 2011-08-17
P.S. I'm using an external USB 2.0 sound card from my laptop so maybe I need not to remove pulsaudio (?) I don't know I'm just guessing

P.P.S.:

as I try to open the maverick package with Ubuntu SW center, it says 

Dependency is not satisfiable: libbs2b0  

how shall I make it?

---

### Post by .... on 2011-08-17
```
sudo apt-add repository ppa:lazka/dumpingplace
sudo apt-get update
sudo apt-get install libbs2b-dev gstreamer0.10-bs2b
```

---

### Post by Edoardo_P on 2011-08-17
thanks but it does not work :confused:

the terminal's answer is weird... it says a command does not exist, it gives me many warnings and in the end it's unable to locate the package...

```
edoardo@edoardo-netbook:~$ sudo apt-add repository ppa:lazka/dumpingplace
**sudo: apt-add: command not found**

```then

```

edoardo@edoardo-netbook:~$ sudo apt-get update

...................
        
Fetched 1,214B in 9s (126B/s)                                                  
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG 61E091672E206FF0 Launchpad nautilus-elementary
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures were invalid: BADSIG A3CD88794B2C459E Launchpad PPA for aMule stable releases
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG B1ABFA423B17A4FD Launchpad RGBA Gtk
W: GPG error: http://it.archive.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead. 

```
```
edoardo@edoardo-netbook:~$ sudo apt-get install libbs2b-dev gstreamer0.10-bs2b
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libbs2b-dev
E: Unable to locate package gstreamer0.10-bs2b
E: Couldn't find any package by regex 'gstreamer0.10-bs2b'

```

quite challenging :confused:

---

### Post by Elfy on 2011-08-17
[https://help.ubuntu.com/community/add-apt-repository](https://help.ubuntu.com/community/add-apt-repository)

```
sudo add-apt-repository ppa:lazka/dumpingplace
```

then do the remaining commands from post #5

---

### Post by Edoardo_P on 2011-08-17
> **forestpiskie said:**
> [https://help.ubuntu.com/community/add-apt-repository](https://help.ubuntu.com/community/add-apt-repository)

```
sudo add-apt-repository ppa:lazka/dumpingplace
```then do the remaining commands from post #5

No way about the second command...
```

edoardo@edoardo-netbook:~$ sudo apt-get update

...........

Fetched 16.3kB in 9s (1,784B/s)                                                
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG 61E091672E206FF0 Launchpad nautilus-elementary
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures were invalid: BADSIG A3CD88794B2C459E Launchpad PPA for aMule stable releases
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG B1ABFA423B17A4FD Launchpad RGBA Gtk
W: GPG error: http://it.archive.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```but the latest seem to have worked anyway!

sudo apt-get install libbs2b-dev gstreamer0.10-bs2b
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libbs2b-dev is already the newest version.
gstreamer0.10-bs2b is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
edoardo@edoardo-netbook:~$ 




what next? :D because _**I don't find it among the exaile plugins anyway...**_ :(

the other players advised... I've just installed to see if any worked... but...

totem and rbox don't even appear among the apps... even after restarting everything... guayadeque crashes at start...

So... How shall I make it work now?

---

### Post by .... on 2011-08-17
What music player do you really want to use? Oh, and sorry about the typo in apt-add-repo command.

---

### Post by .... on 2011-08-17
For gstreamer programs
```
gst-bs2b
========

This uses the bs2b library, created by Boris Mikhaylov
http://bs2b.sourceforge.net/

Settings:
 - frequency cut (Hz) -> fcut=300..2000
 - feed level (db) -> feed=1.0..15.0

Presets:
 - DEFAULT: preset=0 <=> fcut=700 / feed=4.5 (This is the overal default)
 - CMOY: preset=1 <=> fcut=700 / feed=6.0
 - JMEIER: preset=2 <=> fcut=650 / feed=9.5

Example pipeline:
 gst-launch -v filesrc location=a.mp3 ! mad ! crossfeed preset=1 ! autoaudiosink
```so...
```
gconftool-2 --type string --set /system/gstreamer/0.10/default/audiosink "crossfeed preset=0 ! pulsesink"
gconftool-2 --type string --set /system/gstreamer/0.10/default/chataudiosink "crossfeed preset=0 ! pulsesink"
gconftool-2 --type string --set /system/gstreamer/0.10/default/musicaudiosink "crossfeed preset=0 ! pulsesink"
```

---

### Post by Edoardo_P on 2011-08-18
> **.... said:**
> For gstreamer programs
```
gst-bs2b
========

This uses the bs2b library, created by Boris Mikhaylov
http://bs2b.sourceforge.net/

Settings:
 - frequency cut (Hz) -> fcut=300..2000
 - feed level (db) -> feed=1.0..15.0

Presets:
 - DEFAULT: preset=0 <=> fcut=700 / feed=4.5 (This is the overal default)
 - CMOY: preset=1 <=> fcut=700 / feed=6.0
 - JMEIER: preset=2 <=> fcut=650 / feed=9.5

Example pipeline:
 gst-launch -v filesrc location=a.mp3 ! mad ! crossfeed preset=1 ! autoaudiosink
```so...
```
gconftool-2 --type string --set /system/gstreamer/0.10/default/audiosink "crossfeed preset=0 ! pulsesink"
gconftool-2 --type string --set /system/gstreamer/0.10/default/chataudiosink "crossfeed preset=0 ! pulsesink"
gconftool-2 --type string --set /system/gstreamer/0.10/default/musicaudiosink "crossfeed preset=0 ! pulsesink"
```

thank you again, don't worry for the mistake.

up to now I've used just rhythmbox, but I'm open to any other  alternative since I listen most on my music by headphones. I'm working  to listen by MPD and a client in the future. But I have to learn to use  the terminal before :smile: by the way, do you know any mpd client in which this plugin works?


I have copied ```
edoardo@edoardo-netbook:~$ gconftool-2 --type string --set /system/gstreamer/0.10/default/audiosink "crossfeed preset=0 ! pulsesink"
edoardo@edoardo-netbook:~$ gconftool-2 --type string --set /system/gstreamer/0.10/default/chataudiosink "crossfeed preset=0 ! pulsesink"
edoardo@edoardo-netbook:~$ gconftool-2 --type string --set /system/gstreamer/0.10/default/musicaudiosink "crossfeed preset=0 ! pulsesink"
edoardo@edoardo-netbook:~$ 
```and now it works on Rhythmbox, Banshee, anything.

Wow it works!!! THANKS A LOT GUYS!!! lots of love

[B][U]...now... how do I switch it on and off? 
[/U] 
[/B]:)

---

### Post by .... on 2011-08-18
Use the 3 commands above with only "pulsesink" to turn it off. You can make simple little bash scripts to save typing. That's beyond the scope of my help, though. ;)

---

### Post by Edoardo_P on 2011-08-18
> **.... said:**
> Use the 3 commands above with only "pulsesink" to turn it off. You can make simple little bash scripts to save typing. That's beyond the scope of my help, though. ;)

I've typed

```

edoardo@edoardo-netbook:~$ gconftool-2 --type string --set /system/gstreamer/0.10/default/audiosink "pulsesink"
edoardo@edoardo-netbook:~$ gconftool-2 --type string --set /system/gstreamer/0.10/default/chataudiosink "pulsesink"
edoardo@edoardo-netbook:~$ gconftool-2 --type string --set /system/gstreamer/0.10/default/musicaudiosink "pulsesink"
edoardo@edoardo-netbook:~$ 
```

and it switched!!

Wow! Problem solved! Thanks a lot guys

---

