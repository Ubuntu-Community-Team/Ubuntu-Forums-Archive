---
title: "VDR and Ubuntu"
date: 2008-11-26
forum: Multimedia Software
---

### Post by segalion on 2008-11-26
I have been searching documentation about VDR and ubuntu and it is very poor, so I decided to initiate a quickly guide.

Actually it is in progress. 

[SIZE="4"]What is? 
[/SIZE]Probably the best linux digital video program, used even in comercial hardware solutions.

It work as a server (vdr-kbd) with multiple plugins, reading dvb mpeg from devices installed on the machine. And clients (vdr-sxfe) -can be more than one kind (xine, mplayer, vlc ...) and runing in diferent computers- that output the stream (TV or radio channel). In this example, server and client run on same machine.
The main plugin is vdr-xineplugin, but there are other . i.e a webserver (to control vdr remotely, program record timer, see epg...), weather, games (as modern tv-sets), and almost what you can imagine to see on a tv).


See the oficcial screenshots at [http://www.cadsoft.de/vdr/software.htm](http://www.cadsoft.de/vdr/software.htm)

**More doc**
[wiki]("http://www.linuxtv.org/vdrwiki/index.php/Main_Page")
[URL="http://www.linuxtv.org/vdrwiki/index.php/UBUNTU/Installation"]VDR&Ubuntu


[/URL][SIZE="4"]Mini howto[/SIZE] (in progress)
Requirements:
- Have a DVB card properly supported by video4linux kernel.

**Install:**
From ubuntu repositories:
sudo apt-get install vdr libxine1-xvdr vdr-plugin-xineliboutput libxineliboutput-sxfe xineliboutput-sxfe

**Configure:**
Need to configure:
0. ?
```
sudo nano /etc/default/vdr
```
```
ENABLED=1
OPTIONS="-w 60"
USER=your_user_name
VIDEO_DIR=/your_prefered_dir

```
1. plugin to have video output:

```
sudo nano /etc/vdr/plugins/plugin.xineliboutput.conf

```
and put inside
```
--local=none
--primary
--remote=37890

```

2. have the proper channel list. In my example I use the satellite transponder list from kaffeine files, but you can search others (dvb-s, dvb-t, etc.).
You can use *scan* from [dvb-utils]("http://packages.ubuntu.com/intrepid/i386/dvb-utils/filelist") package (sudo apt-get install dvb-utils)
```
scan -o vdr -e 6 /usr/share/dvb/dvb-s/Astra-19.2E > /var/lib/vdr/channels.conf
```
With dvb-apps installed, you have more scan files at /usr/share/dvb/dvb-t/ and /usr/share/dvb/dvb-c/
I.e, you can scan channels for terrestrial digital tv at Madrid-Spain with scan -o vdr -e 6 /usr/share/dvb/dvb-t/es-Madrid > /var/lib/vdr/channels.conf

3. Some permisons stuff (probably is not best solution) on the config and cache dirs used by vdr:
/var/lib/vdr
the main files are:
     channels.conf ( channel-list with the format [http://www.linuxtv.org/vdrwiki/index.php/Syntax_of_channels.conf](http://www.linuxtv.org/vdrwiki/index.php/Syntax_of_channels.conf) )
     remote.conf ( key and lirc definitions to control the vdr. The main are arrow-keys, ok=enter, menu, colors (red,green,yellow,blue) and numbers...
     setup.conf ( vdr config options modified easily with osd info later...)
/var/cache/vdr (the epg info).

i.e.

```
sudo chmod 777 /var/lib/vdr
sudo chmod 666 /var/lib/vdr/*

```

**Run:**
Start the server (it start automagically when ubuntu start)
```
sudo /etc/init.d/vdr start
```

Start the client to see the TV...
```
vdr-sxfe xvdr+udp://localhost
```

To be completed...

---

