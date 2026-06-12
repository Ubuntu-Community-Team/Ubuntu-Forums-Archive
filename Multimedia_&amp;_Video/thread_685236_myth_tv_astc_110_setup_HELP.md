---
title: "myth tv astc 110 setup HELP"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by jordanubun on 2008-02-02
hi i am trying to set up my kworld astc 110 tuner with myth tv for ota atsc i have the dvb firmware but dont know how to instal it can anyone help me do this srry but i am a ubuntu newb

---

### Post by thecoolcat on 2008-02-06
Hi,  I use kworld atsc 115 which I believe is very similar to kworld atsc 110.

You can take a look at this thread that discusses this card's issues in detail and how it was solved:
[http://ubuntuforums.org/showthread.php?t=643415](http://ubuntuforums.org/showthread.php?t=643415)

You should place a copy of the firmware file (dvb-fe-nxt2004.fw) in your /lib/firmware/<linux kernel name>/. directory

If you just care about OTA ATSC, I'd suggest trying it first with mplayer (it will prove that your card works) before jumping on to mythtv.
See this post:
[http://ubuntuforums.org/showpost.php?p=3994301&postcount=7](http://ubuntuforums.org/showpost.php?p=3994301&postcount=7)

---

### Post by jordanubun on 2008-02-07
thax for your reply but when i put that comand in terminal it says " bash: .~/.mplayer/channels.conf: No such file or directory " i am new to this stuff so yea

---

### Post by jordanubun on 2008-02-07
that applies to testing my card with mplayer for atsc to install dvb utilities

---

### Post by jordanubun on 2008-02-07
installed dvb-utils then i went entered that info into terminal and since it siad that bash thing i then put in the directory of the dvb exampels channels.conf   and got this "  /usr/bin/scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > sudo /usr/share/doc/dvb-utils/examples/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy " what can i do

---

### Post by thecoolcat on 2008-02-08
In your dmesg output, do you see that nxt2004 is loaded?
When you hit dmesh, you should see something like this on the terminal:

```
[   38.416323] nxt200x: NXT2004 Detected
[   38.416391] DVB: registering new adapter (saa7133[0]).
[   38.416395] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   38.424290] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   38.454788] ieee80211_init: failed to initialize WME (err=-17)
[   38.467688] nxt2004: Waiting for firmware upload(2)...
.
.
.
[   40.167087] [COLOR="red"]nxt2004: Firmware upload complete[/COLOR]
[   41.994095] nxt200x: NXT2004 Detected
[   41.994127] DVB: registering new adapter (saa7133[1]).
[   41.994131] DVB: registering frontend 1 (Nextwave NXT200X VSB/QAM frontend)...
[   42.006105] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   42.008540] nxt2004: Waiting for firmware upload(2)...
[   43.708924][COLOR="Red"] nxt2004: Firmware upload complete[/COLOR]
```

And also make sure myth is not running while you scan.

---

### Post by jordanubun on 2008-02-09
in my dmesg out put this is what it says about my card


" [   32.199363] nxt200x: NXT2004 Detected
[   32.199425] DVB: registering new adapter (saa7133[0]).
[   32.199430] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   32.212019] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   32.246106] nxt2004: Waiting for firmware upload(2)...
[   32.246110] nxt2004: No firmware uploaded (timeout or file not found?) "

---

### Post by thecoolcat on 2008-02-11
Looks like you need to load the firmware. Can you take a look at this thread?

[http://ubuntuforums.org/showthread.php?t=647582](http://ubuntuforums.org/showthread.php?t=647582)

Try rebooting after polacing the firmware in the appropriate directory. Post back if you need more help.

---

### Post by cctvtech on 2008-02-27
So how do we get this get_dvb_firmware unzipped and get the firmware into the right directory.

I'm using Mythbuntu 7.10 and trying to install the Kworld 115 card.

There are tons of places pointing to the file but can't find how to use it, and yes I'm a linux n00b.

I'm logged in as root through Putty and the main file is on the desktop.

Thank you in advance!!!!!!

---

### Post by thecoolcat on 2008-02-27
Go to this website:
[https://help.ubuntu.com/community/MythTV_Feisty_hardware_list](https://help.ubuntu.com/community/MythTV_Feisty_hardware_list)
Under ATI cards, you should see a link to download the get_dvb_firmware script. Clink on this (or right click and save it as get_dvb_firmware).

Do the following from the directory where you have this script:
```
$ chmod +x get_dvb_firmware
$ ./get_dvb_firmware nxt2004
```
After this you should see dvb-fe-nxt2004.fw in the same dir.
Place a copy of the firmware file (dvb-fe-nxt2004.fw) in your /lib/firmware/<linux kernel name>/. directory
To do this, execute 
```
$ sudo cp dvb-fe-nxt2004.fw /lib/firmware/<linux kernal name>/.
```You can find out the correct valur of <linux kernal name> once you go to /lib/firmware/.

---

### Post by cctvtech on 2008-02-27
once I get to ./get_dvb_firmware nxt2004

It says: This firmware requires the unzip command

This is where I got stuck before

---

### Post by cctvtech on 2008-02-27
This is a stock setup, no one has had this problem?

---

### Post by thecoolcat on 2008-02-27
> **cctvtech said:**
> once I get to ./get_dvb_firmware nxt2004

It says: This firmware requires the unzip command

This is where I got stuck before

Ok. The script needs unzip command to be installed in your system. I don't know if unzip is preloaded in mythbuntu. You can check by executing the unzip command or executing "which unzip" on an xterm. If its not there, I believe you can add it easily using synaptic package manager.

---

### Post by cctvtech on 2008-02-27
THANKS!
I have ATSC TV Now :guitar:

---

