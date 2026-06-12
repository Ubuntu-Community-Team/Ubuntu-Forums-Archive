---
title: "Using SPDIF for system sound output (How?)"
date: 2005-11-09
forum: Multimedia &amp; Video
---

### Post by unzari on 2005-11-09
I've set up Breezy on a system plugged into my flat panel display to be used for watching movies with "mplayer".  The sound is plugged into my home cinema system, and I know it all works, because "mplayer" can play through the SPDIF (using "-ac hwac3") with no problems.

My question is "How can I enable SPDIF output for all system sounds?".  In Windows, there is an option in the volume control application labelled "Use SPDIF", and when selecting it, all sound goes via this channel.

Anybody know?

Thanks in advance...
u*

---

### Post by MetalMusicAddict on 2005-11-24
I would also love to know this. :)

---

### Post by installer on 2005-11-25
[QUOTE=MetalMusicAddict]I would also love to know this. :)[/QUOTE]

So would I..........

---

### Post by AndyC_772 on 2005-12-19
[QUOTE=installer]So would I..........[/QUOTE]

Try opening a terminal window and running 'alsamixer', then scroll right (arrow key) until 'IEC958' is highlighted. Push 'M' to enable SPDIF and then Escape to exit.

Works for me... listening to a Shoutcast stream through my AV amp right now :D

ps. also ensure that the next bar 'IEC958 Playback AC97-SPSA' is at 0 - don't ask me why!

---

### Post by anarchist_hippy on 2005-12-19
I think it doesn't work :( [I tried, but nothing changed... There's options in IEC958: PCM, analog or IEC958 . M doesn't works :(  

Any other ideas?

---

### Post by PsyberOneZero on 2005-12-19
Here's a series of screenshots of gnome-volume-mixer for setting up nForce onboard sound
[http://ubuntuforums.org/showpost.php?p=553082&postcount=5](http://ubuntuforums.org/showpost.php?p=553082&postcount=5)

I've seen this several times in the forum, I'll put a HOWTO together in the next few days, but this will work for now.

---

### Post by polt on 2005-12-20
I would like to be able to do this on an Intel 945 board. The system sets up beautifully with Breezy Badger -- including analog audio, but no digital output. My S/PDIF is optical, but that doesn;t matter, does it?

---

### Post by nt_bert on 2006-01-24
Simpler than I thought. 

Here is the URL that led me to the solution:
[http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php?module=Generic](http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php?module=Generic)

Warning, these instructions are for a nForce 2 integrated motherboard, so YMMV. (Your SPDIF device may not be an IEC958.  8)

Here is basically what you do : 

Open a terminal.
type : aplay -l
(You can get the same information from Device Manager, but this way is quicker)


on the second grouping you will have a device called an IEC958 . Take note of the number directly after card and device.

type : vim ~/.asoundrc 
hit i

type :

 pcm.!default {
	type hw
	card <x>
        device <y>
	}

	ctl.!default {
	type hw           
	card <x>
        device <y>
        }

After both card and device you need to put the numbers that you retrieved from aplay -l . (number that was after card in aplay -l in place of <x> and the number that was after device in place of <y>).

Tap your escape key twice. type the colon ":" key once.
type "wq"

Now any thing that plays through alsa should go over your spdif.

Have fun !

Sean P, MCSE. 

[QUOTE=unzari]I've set up Breezy on a system plugged into my flat panel display to be used for watching movies with "mplayer".  The sound is plugged into my home cinema system, and I know it all works, because "mplayer" can play through the SPDIF (using "-ac hwac3") with no problems.

My question is "How can I enable SPDIF output for all system sounds?".  In Windows, there is an option in the volume control application labelled "Use SPDIF", and when selecting it, all sound goes via this channel.

Anybody know?

Thanks in advance...
u*[/QUOTE]

---

### Post by OlineSixtyOne on 2006-01-24
That didn't work for me. I got no audio output on analog or SPDIF, and Mplayer gave an error whenever I tried to play something. Stuff in Rhythmbox plays at about 3x speed (no audio output though). Is there any way to modify that so it will work?

---

### Post by OlineSixtyOne on 2006-01-25
Keep it on page 1 :p

---

### Post by jazzgossen on 2006-01-26
nt_bert's solution works great for me! Hooray!

Edit: not so great.
The system sounds now go over SPDIF, but using for example XMMS is problematic. It works once. If I close it, do something that makes a system sound (clicks something on the panel), and then run XMMS again, it complains that it can't open the soundcard. Then I have to go to the preferences, change output plugin (I'm not sure what helps, but changing between the ALSA and the crossfader plugin seems to work), and then it works again.

Strange, huh?

---

### Post by OlineSixtyOne on 2006-01-26
While trying to compile Mplayer and get ALSA output I installedan ALSA dev package with Synaptic and my SPDIF all of a sudden started working. No .asoundrc or anything, it just works now. Thats quite odd. 

On a sidenote, the repositories Mplayer build doesn't playback H.264 correctly. I had to build it myself from CVS to get it to work :(.

---

### Post by nt_bert on 2006-01-31
ARGH!

Okay, the above instructions work kinda of. I went and reinstalled my system (It is the equivelant of a thin client this day and age , 20gb drive, 1gb mem. I use the system as a front end to play video, music and do my office and internet stuff). Anyways, when I found that I had SPDIF working, I tried to replicate the success. Foolish me, I get my generalized systems sounds going out of my amplifier. I get VLC (Not Totem which I was utilizing before) and amaroK out of my amplifier. Everything else I try, I get these awful clicking noises if I do pass-through audio. 

I think there is something else that I am missing in making ALSA the primary sound driver on my system. I wonder if I have to set the foolish thing up as the system default sound device using the default sound resource file or something else equally foolish.

For those who are wondering:

AMD Athlon 3200 XP running Ubuntu 5.10 
1 GB RAM.
Shuttle Dusk or Dawn system. (41G I think).
nVidia 5500 w/ three outs. (DVI,S-Video and VGA)
 - DVI to HDMI convertor running a 36" Sony WEGA TV in 640x480 (I just can't get any lovin outta X on this one. Any help would be appreciated. I have the nVidia 7667 drivers installed and have made my X unusable trying to get more on the resolution. The dang TV is a Trinitron Tube and should be capable of at least 1024x768....grrrrrr....Of course I had to tell X that it was DFP in order to get projection onto the TV...).
- an older HP vx74 on the VGA out.
20 GB HDD w/ 13.5 GB free.
DVD +/- RW

NFS server is  running Kubuntu 5.10
AMD Athlon 1800 XP
512 MB RAM
White Box - Antec Full Tower Chasis
nForce2 Motherboard w/ 3 PATA channels (6 devices) and 2 SATA Channels
4 x 200GB drives, 1x 13 GB system drive, 1 CD-RW, 1 DVD-ROM
Geforce 3 video w/S-Video and VGA (Flat Panel connected to the VGA)

Anyways, I will blog my trials to this particular thread and see what comes of it.

Sean P., MCSE.

---

### Post by nt_bert on 2006-02-01
Snoopy Dance ! Snoopy Dance ! 

Xine now works, so I should be able to download Totem-xine and it should work (perhaps I will end up having to recompile the sucker, but no big deal). 

Anyways, what I did was that I apt-get/synaptic the alsa headers, downloaded the source for Xine and did a sudo ./configure, sudo make, sudo install (Really a simple and clean compile - GOOD JOB XINE CREW). For some reason, if I did a ./configure, I got an error, but NBD.  I also compiled and installed xine-ui off of the xine site.Then I set my audio out to 5.1 surrond as it was using my pcm out and I set my sound drivers to ALSA and everything just worked ! One down, now if Totem-Xine works I will sitting pretty. I really like the simple UI of Totem. (I am now watching new BSG miniseries movie, <plug> Great show, BUY the DVDs and support them.</plug>  on my TV, from my computer, with the sound through my amp.)

I do not know why the default version of Xine through synaptic with various additional repositories would not work, but it did not. Hopefully I will not have to do this for all of the packages that claim ALSA compatibility but just don't work.

Sean P., MCSE.

---

### Post by nt_bert on 2006-02-01
Snoopy Dance Again !

I was able to download Totem-Xine from Synaptic and it just worked. One problem is that it does not understand ogg as I forgot to get those plugins before I compiled the xine library, but once I figure that piece out (I am just doing that piece for completeness.) I will be done and can start to remove applications from my system (Like VLC and Xine-UI). I will have to go back and reread the Xine docs to see if Xine is capable of dumping an raw mpg out. If so, I will not have a use for mplayer either and can remove this also.

\\:D/       \\:D/     \\:D/      \\:D/      \\:D/      \\:D/      \\:D/      \\:D/

---

### Post by jazzgossen on 2006-02-01
[QUOTE=OlineSixtyOne]While trying to compile Mplayer and get ALSA output I installed an ALSA dev package with Synaptic and my SPDIF all of a sudden started working. No .asoundrc or anything, it just works now. Thats quite odd. 
[/QUOTE]

Which ALSA dev package was that?

---

### Post by nt_bert on 2006-02-02
[QUOTE=jazzgossen]Which ALSA dev package was that?[/QUOTE]
I am assuming that the dev package that he used was the same that I did.It is alsa-source for the version of the Ubuntu you are using. At least that is the appropriate search for synaptic.

Sean P, MCSE.

---

### Post by nt_bert on 2006-02-03
Found that I will still need mplayer for dumping streams from DVDs. Finding that the chapters are highly non relevant for moving through a movie. The other application that I am finding is a must have is lsdvd. Thoggen is not quite ready and I am finding that dvd::rip, while very nice, is not reliable in the amount of time it takes. 

Still fighting the good fight on moving everything through spdif. Although tonight I was busy earning my paycheck versus doing any more research into what else I need to move. However, has anyone reading this thread been able to get Doom3 or NWN to work over SPDIF ?  I can get NWN to work over the headphones, but not through spdif. Doom3 just does not work at all over my audio. The video runs great at 1024 x 768 on my crt and the installer works fine.

Thanks.

Sean P, MCSE.

---

### Post by nt_bert on 2006-02-06
Big freakin' disappointment. I found the specification for video over HDMI. I do not know if I should be disappointed or not. Seems that I may have a HDMI 1.0 device and am stuck at 640x480 @60hz (31.5).  :{ WAAAAAAAAAAA! Okay, enough of that. Here are the specs for the rest of you. Depending on what you have for HDMI (1.0,1.1 or 1.2), that will determine the resolutions that yoiu can get through a HDMI-DVI convertor. 

You should always have 
   640x480 . Some of you (SNIFF! ME! SNIFF!) will only have this one.
The other possible resolutions are :
   720x480
   720x576
   1280x720
   1920x1080i. 

Good Luck to you!

Sean P, MCSE.

---

### Post by nt_bert on 2006-02-14
Now I am utterly FLUMOXed and disappointed. I could use anyones experience and help.

I installed XP on my system so now I am dual booting and a couple of things happened.
1) My HDMI to DVI cable picked up and ran with all the resolutions that I could ever want (BIG HINT to you videophiles trying to get HDTV to work with Linux). 
2) My SPDIF went digital with XP.....

I don't get it.

I did catch an article on /. about HDMI and the new Blue Ray being liscenced technology at 15K a month plus a device fee. Anyone have any feedback on this ? How else can I help to make this work under Ubuntu ?

On another note, what is up with the source tree ? I installed Build-essentials, the i386 kernel sources to the 2.6.12 (I think) and tried to install 8183 nVidia drivers manually. I compiled but they would not load as my source claimed to be a different version than my kernel. Yet on synaptic, it claimed the same variation. Any insight, any one ?

Under Mandriva Free 2006 the drivers install and compile just fine, so I know it is not the drivers, it is the distro on this one.

---

