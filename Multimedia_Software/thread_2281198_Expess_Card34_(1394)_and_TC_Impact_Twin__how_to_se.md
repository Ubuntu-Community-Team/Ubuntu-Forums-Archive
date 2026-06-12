---
title: "Expess Card/34 (1394) and TC Impact Twin : how to set up with Ubuntu"
date: 2015-06-05
forum: Multimedia Software
---

### Post by Vamer on 2015-06-05
Hello,

I've just migrated from Windows to Ubuntu 15.04 (64-bit) and I want to set-up my audio interface (TC Electronics : Impact Twin) and the Firewire 1394a Express Card/34 (Unibrain : Firecard 400-e, this has a Texas Instruments chipset) that I have to connect it to my laptop.

In the process I want to learn how these all work in Ubuntu so I'm looking for the right articles/guides that can help me build a type of "know-how" in this area.

My current requirement is to use my set-up for audio playback (FLAC files), in the future I might record vocals (I own a mic which connects to Impact Twin).

1. Should I stick with Ubuntu Desktop of go for Ubuntu Studio?

2. Which is the most valid/up-to-date guide for my case (setting up the h/w finding the right s/w)? I've googled a bit 

UbuntuHelp 
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

Drivers? Is this the right place to look for?
[http://ffado.org/](http://ffado.org/)


Thanks in advance for setting me on the right path.

---

### Post by Bucky Ball on 2015-06-05
Welcome. I can't help you with a lot of this, but have you tried plugging the external devices in and seeing if they 'just work'? Unlike Windows, the majority of device drivers are already in the kernel, you don't need to install them from a third-party. For the drivers that aren't there, there is possibly a workaround or Linux drivers available from a third-party. Hope someone with similar devices can help you. I have an old Mbox that never worked in 10.04 LTS, worked with a workaround in 12.04 and works 'out of the box' with 14.04 LTS as the drivers are now included in the kernel. If your hardware didn't just hit the market yesterday, you might be lucky.

As for replacing Ubuntu with Ubuntu Studio, not really any need by the sounds of what you intentions for the machine are. You can install 'ubuntustudio-audio' from the repositories (Software Centre or Synaptics or via a terminal) and that will add all the UStudio audio stuff. If you wanted to replace, you can install 'ubuntustudio-desktop' and that will install EVERYTHING that needs to be from Ubuntu Studio on top of your already installed Ubuntu. This is not a good idea and may cause unforeseen issues (and bloat).

PS: Firewire card so you can plug Firewire devices in? Not an issue. Just install it and reboot. Generic stuff like that is rarely a problem. The TC might be.

Hope that helps in some way.

UPDATE: As for the Impact Twin, looks like it works. See the last post [here]("http://forum.tcelectronic.com/topic/16527/impact-twin-and-linux/"). You're right in that there is not a lot online about it and Ubuntu, and that is generally a very good sign. Hopefully means people aren't having issues.

---

### Post by Vamer on 2015-06-05
Thanks Bucky Ball,

I had a major set-back (did some totally inappropriate package purging and I ended up performing a clean install of 15.04), so back to the start (after having read quite a lot).
Currently, I've installed nothing other than the 15.04 had (or prompted for the update of some packages) and I've plugged in the Express Card and turned on the Audio Interface.

I think that the status is not bad:

Kernel:

```
uname -r
3.19.0-18-generic
```

pci output:

```
lspci | grep -E -i "1394|firewire"
07:00.0 FireWire (IEEE 1394): Texas Instruments XIO2200A IEEE-1394a-2000 Controller (PHY/Link) (rev 01)
```

dmesg:

```
dmesg | grep -E -i "1394|firewire"
...
[  576.624035] firewire_ohci 0000:07:00.0: added OHCI v1.10 device as card 3, 4 IR + 8 IT contexts, quirks 0x2
[  577.124914] firewire_core 0000:07:00.0: created device fw0: GUID 08144376000001a3, S400
...
[  686.099204] firewire_core 0000:07:00.0: created device fw1: GUID 0001660409c025c5, S400
[  880.250160] firewire_core 0000:07:00.0: rediscovered device fw0
```

devices:

```
ls -lap /dev/fw*
crw------- 1 root root 248, 0 &#921;&#959;&#973;&#957;  5 18:16 /dev/fw0
crw------- 1 root root 248, 1 &#921;&#959;&#973;&#957;  5 18:22 /dev/fw1

```

Driver:

```
lsmod | grep -E -i "1394|firewire"
snd_firewire_lib       32768  1 snd_dice
firewire_ohci          45056  0 
firewire_core          69632  3 snd_firewire_lib,firewire_ohci,snd_dice
crc_itu_t              16384  1 firewire_core
snd_pcm               106496  6 snd_firewire_lib,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_dice
snd_rawmidi            32768  3 snd_firewire_lib,snd_dice,snd_seq_midi
```


I can now see the Impact Twin under Settings -> Sound -> XIO2200A IEEE-1394a-2000 Controller (PHY/Link) (DC-1394 PCIe) Multichannel.
It does not work of course.

I am thinking of going straing to setting and cofiguring FFADO and Jack, while skipping anything in between (I want to go for a minimum config just to avoid breaking something again).
[B][https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
FireWire sound cards (IEEE 1394, FFADO)[/B]

 Do you agree with this approach?

Thanks in advance.

Question: is there a way to see the presence and status of the firewire devices? Apart from using commands like lspci and dmesg?

---

### Post by Vamer on 2015-06-05
Hi,

I've installed ffado, jackd2, and the gui qjackctl in order to configure the audio interface for jack.
I also set the irq prios for firewire as explained here [https://help.ubuntu.com/community/FireWire/DigitalAudio](https://help.ubuntu.com/community/FireWire/DigitalAudio)

I verified that I'm using the latest firewire stack (firewire_ohci) and that the "blacklisting" in /etc/modprobe.d/blacklist-firewire.conf is done right.

When I start the QjackCtl application (and having configured it as suggested in these articles) the Jack Server cannot even be started, so I must be doing something terribly wrong.

Output from the log. Can you propose any kind of trouble-shooting?


Fri Jun  5 19:56:45 2015: Starting jack server...
Fri Jun  5 19:56:45 2015: JACK server starting in realtime mode with priority 10
Fri Jun  5 19:56:45 2015: self-connect-mode is "Don't restrict self connect requests"
Fri Jun  5 19:56:45 2015: ERROR: Cannot lock down 82274202 byte memory area (Cannot allocate memory)
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Fri Jun  5 19:56:45 2015: ERROR: firewire ERR: FFADO: Error creating virtual device
Fri Jun  5 19:56:45 2015: ERROR: Cannot attach audio driver
Fri Jun  5 19:56:45 2015: ERROR: JackServer::Open failed with -1
Fri Jun  5 19:56:45 2015: ERROR: Failed to open server

I based my actions on the following:

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)
[https://help.ubuntu.com/community/FireWire/DigitalAudio](https://help.ubuntu.com/community/FireWire/DigitalAudio)
[https://help.ubuntu.com/community/FireWire/oldPages/Firewire03](https://help.ubuntu.com/community/FireWire/oldPages/Firewire03)

---

### Post by Bucky Ball on 2015-06-05
Post #8 [here]("http://ubuntuforums.org/showthread.php?t=1637399&p=10199399&viewfull=1#post10199399") might be a little dated, but you never know. Things may have changed a bit. 

I haven't used Jack in a while and when I did it worked so your issues are a bit outside my experience. Try searching for 'Cannot lock down byte memory area jack' which is what I did to turn up the above link (I used that as it is the first error in your output and possibly causing the ones that follow). Hopefully a Jack aficionado can join us sometime soon.

You've done really well to get this far as a novice and great the firewire card 'just works'. It looks like the audio interface is not far away either. ;)

---

### Post by Vamer on 2015-06-06
Hello Bucky Ball,

I've gone to great lengths in getting jackd (jack-deamon) to work but...
I'm concluding that the TC Impact Twin is not working properly with the ffado driver (regardless of what the admin in the TC support wrote).


1. I fixed my device's name value in qJackCtl to hw:Twin so that the "slot" in which the card is discovered by Linux each time is irrelevant.

```
cat /proc/asound/cards
1 [Twin           ]: DICE - Impact Twin
                      TC Electronic ImpactTwin (serial 9669) at fw1.0, S400
```


2. fixed memory (locked) problem:

```
ulimit -r -l
real-time priority              (-r) 95
max locked memory       (kbytes, -l) unlimited
```

3. Installed low-latency kernel (I should have not however, since the original did not cause any problem):

```
uname -r
3.19.0-18-lowlatency
```

Now my set-up looks like this (pic attached).

[ATTACH=CONFIG]262466[/ATTACH]


And when I start the jack:

 [COLOR=#999999]21:37:05.374 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]21:37:05.386 Statistics reset.[/COLOR]
 [COLOR=#cccc99]21:37:05.396 ALSA connection change.[/COLOR]
 [COLOR=#999999]21:37:05.477 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]21:37:05.513 ALSA connection graph change.[/COLOR]
 [COLOR=#ff0000]21:37:18.812 D-BUS: JACK server could not be started. Sorry[/COLOR]
 [COLOR=#66cc99]Cannot connect to server socket err = No such file or directory[/COLOR]
 [COLOR=#66cc99]Cannot connect to server request channel[/COLOR]
 [COLOR=#66cc99]jack server is not running or cannot be started[/COLOR]
 [COLOR=#66cc99]Sat Jun  6 21:37:18 2015: Starting jack server...[/COLOR]
 [COLOR=#66cc99]Sat Jun  6 21:37:18 2015: JACK server starting in realtime mode with priority 10[/COLOR]
 [COLOR=#66cc99]Sat Jun  6 21:37:18 2015: self-connect-mode is "Don't restrict self connect requests"[/COLOR]
 [COLOR=#66cc99]Sat Jun  6 21:37:18 2015: ERROR: firewire ERR: Could not prepare streaming device![/COLOR]
 [COLOR=#66cc99]Sat Jun  6 21:37:18 2015: ERROR: Cannot attach audio driver[/COLOR]
 [COLOR=#66cc99]Sat Jun  6 21:37:18 2015: ERROR: JackServer::Open failed with -1[/COLOR]
 [COLOR=#66cc99]Sat Jun  6 21:37:18 2015: ERROR: Failed to open server

[/COLOR]
Followed by a segmentation fault (dump follows):

 
[COLOR=#66cc99]Sat Jun  6 21:37:18 2015: ERROR: Segmentation Fault![/COLOR]
 [COLOR=#66cc99]Sat Jun  6 21:37:18 2015: ERROR: Segmentation Fault![/COLOR]
 [COLOR=#66cc99]Sat Jun  6 21:37:18 2015: ERROR: info.si_signo = 11[/COLOR]
 [COLOR=#66cc99]Sat Jun  6 21:37:18 2015: ERROR: info.si_signo = 11[/COLOR]
 [COLOR=#66cc99]Sat Jun  6 21:37:18 2015: ERROR: info.si_errno = 0[/COLOR]
 [COLOR=#66cc99]Sat Jun  6 21:37:18 2015: ERROR: info.si_code  = 1 (SEGV_MAPERR)[/COLOR]
 [COLOR=#66cc99]Sat Jun  6 21:37:18 2015: ERROR: info.si_addr  = 0x7fad5f35d7c6
...
[/COLOR]

I googled for "firewire err - could not open streaming device" and the picks I found where not promising; I understand that it's probably that the ffado does not support my sound card.

[http://linuxmusicians.com/viewtopic.php?f=47&t=12522](http://linuxmusicians.com/viewtopic.php?f=47&t=12522)

Should I ask for help at more specialised on Linux audio forum (so that I could have another shot)? Do I have any other options?

Thanks in advance!

PS I've installed both jack and jack2 but in the qJackCtl jack is used (I read about their differences, supposedly I'm ok with either of the two).


```
dpkg -l jack*


ii  jack-capture                   0.9.71-1             amd64                program for recording soundfiles with jack
un  jack-daemon                    <none>               <none>               (no description available)
ii  jack-keyboard                  2.7.1-1              amd64                Virtual MIDI keyboard for JACK MIDI
ii  jack-rack                      1.4.8~rc1-2          amd64                LADSPA effects "rack" for JACK
un  jack-tools                     <none>               <none>               (no description available)
ii  jackd                          5                    all                  JACK Audio Connection Kit (default server package)
un  jackd-firewire                 <none>               <none>               (no description available)
un  jackd1                         <none>               <none>               (no description available)
un  jackd1-firewire                <none>               <none>               (no description available)
ii  jackd2                         1.9.10+20140719git3e amd64                JACK Audio Connection Kit (server and example clients)
ii  jackd2-firewire                1.9.10+20140719git3e amd64                JACK Audio Connection Kit (FFADO and FreeBoB backends)
```


```
dpkg -l alsa*

un  alsa                           <none>               <none>               (no description available)
ii  alsa-base                      1.0.25+dfsg-0ubuntu4 all                  ALSA driver configuration files
un  alsa-oss                       <none>               <none>               (no description available)
ii  alsa-tools                     1.0.28-1             amd64                Console based ALSA utilities for specific hardware
ii  alsa-tools-gui                 1.0.28-1             amd64                GUI based ALSA utilities for specific hardware
ii  alsa-utils                     1.0.28-1ubuntu2      amd64                Utilities for configuring and using ALSA

```


[COLOR=#66cc99]

[/COLOR]

---

### Post by Bucky Ball on 2015-06-06
In your screenshot of your setup, what do you have in 'Channels I/O' to the lower right of the GUI? Can you change the selection to the Twin there also? It appears you might not have the I/O set correctly by this:

> socket err = No such file or directory

... your first error.

Also, this may have nothing to do with it, but just to note that you should have all other audio apps off when starting jack. Start jack first, if you can, then launch your audio app. That is probably what you're already doing, but doesn't hurt to mention. :)

To be honest, I've never had to do any of this with jack, so not really sure what is going wrong, but following my nose at the instigation of the errors in your output. :-k

---

### Post by Vamer on 2015-06-06
I've just noticed that some env vars are not defined in my system, eg $JACK_START_SERVER.
Also I cannot locate the jackdrc file where these are supposed to be included.
I don't think however that this relates to the first problem with the firewire dev.

[http://manpages.ubuntu.com/manpages/lucid/man1/jackd.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/jackd.1.html)

echo $JACK_START_SERVER
returns nothing.

---

### Post by Bucky Ball on 2015-06-06
Not sure if you read my last post, #8. Have a look there. Go ahead and try a jack specific forum, but concerning this one, you might have more luck if I move the thread to ***Multimedia*** as ***Ubuntu Studio*** is for UStudio support specifically so a move might increase your audience a bit.

*Thread moved to **Multimedia**.*

Lots of non-Ubuntu Studio users also use jack. ;)

---

### Post by Vamer on 2015-06-06
I've just noticed that some env vars are not defined in my system, eg $JACK_START_SERVER.
Also I cannot locate the jackdrc file where these are supposed to be included.
I don't think however that this relates to the first problem with the firewire dev.

[http://manpages.ubuntu.com/manpages/lucid/man1/jackd.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/jackd.1.html)

echo $JACK_START_SERVER
returns nothing.

---

### Post by Vamer on 2015-06-06
[FONT=arial black][/FONT]Hello Bucky Ball,

thanks for relocating the thread to a more "visible" area to be hosted.

Yes, I've checked #8:

In a previous topic of mine I'd posted:

ulimit -r -l
real-time priority              (-r) 95
max locked memory       (kbytes, -l) unlimited

there's no problem with the locking of the memory.

---

### Post by Bucky Ball on 2015-06-06
No, but there could be with the 'Channel I/O'. 

In jack 'Settings' (I think) set them to the channels on the Twin, if you can. The setting is bottom right of that GUI. See if you can start jack.

---

### Post by dawiba2 on 2015-06-07
@Vamer

Installing jackd2-firewire, ffado-mixer-qt4 and qjackctl (and the other packages they pull in) should be enough to get firewire audio devices working. I think you should be fine with what you installed.

In Ubuntu, you have to add your user to the audio group if you want to use jack via qjackctl to control your firewire device.

Check if you are in the audio group

```
groups
```

If 'audio' doesn't appear, than add yourself to that group

```
sudo adduser <yourusernamehere> audio
```

You will have to log out/log in or reboot for that change to take effect.

When you installed the jack software, you should have had a pop-up message asking if you wanted to enable real-time priorities. If you chose 'yes', then you want your qjackctl setup window to match the attached screenshot. If you chose 'no', then make sure the 'realtime' checkbox is unchecked.

With those things done, you should be able to start jack and access your firewire audio card.

Rtirq priorities are an optional extra if you are having audio issues where your audio card is sharing an irq with another device. From your description of what you intend to do, it might not be necessary. I record and playback audio and midi on a couple of old laptops without problems without rtirq being installed. I have installed the low latency kernel though, which helps with this. These things can be very hardware dependent, so in your case, you might need it. Trial and error is the way forward with that.

Hope this helps

---

### Post by Vamer on 2015-06-07
Hello dawiba2,

1. my user-name belongs to group "audio".

2. about rt enabling I believe I'm ok (meaning that I have it enabled):

ulimit -r -l 
real-time priority              (-r) 95
max locked memory       (kbytes, -l) unlimited

3. I'd also set the Rtirq priorities as suggested in various articles.

My problem is very basic, Jackd won't start at all, so either I've configured wronly something fundamental (which I doubt) or the Impact Twin is just "not visible" in Ubuntu (at least given my Texas Instrument firewire controler).

I appreciate the help (I think I'll have to revert to Windows in the end however).

---

### Post by Vamer on 2015-06-07
PS Is there a way to explicitly set the jackd2 as the server of choice? In qJackCtl I set the path /usr/bin/jackd however when I grep for jackd2* I can't find anything in my system. 
I was thinking of giving it a try with jack2...

---

### Post by Kim_Ake on 2015-10-01
How did it go, did you ever get this to work?

I have an Impact Twin, and have the same problems. The crazy thing is, that I managed to get Jack to start a few times randomly when I played with the settings, and even made a 45 minute recording without glitches in Bitwig Studio. But that was only once, I even bought a firewire controller with a Texas Instruments chip, same symptoms. 

Also, if I choose ALSA as the driver in qjackctl, Jack starts, and applications like Renoise and Audacity work. But Bitwig won't, and I can't start Jack with the firewire drivers selected.

I was also wondering about jack2, how it relates to qjackctl. It seems to be installed (jack_control) with Ubuntu Studio, but it gives me the errors too. 

Anyway, Impact Twin does indeed work, there is just something very funky going on with FFADO, or something else...

---

### Post by Vamer on 2015-10-03
No, I'd given up then. It's good to know though that somebody has made some progress (even if you're not enjoying an "error free steady state").
I'd think twice however before making another attempt with Ubuntu and my Impact Twin.

---

### Post by Kim_Ake on 2015-10-09
I installed KXStudio instead, everything is running fine straight out of the box. So there must be just something configured very wrong in Ubuntu by default. But I can attest that the Impact Twin works fine with FFADO :)

---

### Post by Vamer on 2016-09-20
Hello,

I've just performed a clean install of Ubuntu 16.04 LTS (64-bit). Impact Twin seems to work, meaning that audio playback is available, however there are glitches.
I've yet to proceed with any finetunings (I must re-check all the posts, it's been a while), so this behaviour is based on the "default" audio settings. The audio interface is indeed recognised however in the System Settings -> Audio as Impact Twin.

---

### Post by Bucky Ball on 2016-09-21
*Thread closed*. 

Please mark this as solved and start a new thread. It will greatly improve your chances of support. Resurrecting an old, dead, long thread to post about a different release? You do yourself no favours. This case is closed, a new one has opened ...

Feel free to link back to this thread in the new one if you want to provide some background. Thanks.

---

