---
title: "Stream sound from Windows to Linux (PulseAudio?)"
date: 2009-04-10
forum: Multimedia Software
---

### Post by Zorael on 2009-04-10
My mother is quite fond of her iTunes library and the music she can access via Spotify, but her computer is located in a room separate from the beefier speakers in the livingroom.

I'm looking for a way to set up streaming from that Windows desktop to an Ubuntu machine that I'd connect to the stereo, and then set up a vnc session so she can - from that Ubuntu machine - set up and play her music *from* her desktop *via* that machine *to* the stereo. I realize PulseAudio would be awesome for this, and it'd be quite easy to set up were the desktop machine running Ubuntu as well. Unfortunately, it isn't.

Is there a way to set up the Windows machine to be a source, then the Ubuntu machine to play its stream to the stereo sink? Basically, what would be needed for Windows to stream sound to Pulse? Googling turns up information from ages forgotten.
> **Is there a Win32/Windows driver that act like a PulseAudio client?**

    Not exactly, but there use to be a ESoundD driver like that, and PulseAudio can connect to a ESoundD client.
    This project is WinESD at [WinESD](http://www.clingman.org/winesd/). This software was developped for NT4 and Windows 2000. It has been reported to work under Windows XP connected to a PulseAudio server (One computer under Microsoft Windows XP using WinESD, connected to another computer under Microsoft Windows XP using PulseAudio). This project looks unmaintained and last version was "pre-alpha". It still works, but with restrictions :

    * Sometimes, the sound is "broken". It look like it's when two processes try to emit sounds in the same time. Perhaps it's different from one computer to another.
    * There is no easy installers as for July 2007, neither for WinESD nor PulseAudio for Win32/Windows. It's a "Let's play with configuration by hands" installation.
    * You need to unactivate your sound card if you already have one on the computer running WinESD. This will need a reboot. This is undocumented on the [WinESD site](http://www.clingman.org/winesd/).
    * Switching from one driver to another will need to play with Activate/Unactivate drivers, which will cause reboot. 
[Source](http://pulseaudio.org/wiki/FAQ#IsthereaWin32WindowsdriverthatactlikeaPulseAudioclient). Something aimed for NT4 and 2000 doesn't bode well for her machine, which is luckily running XP and not Vista, but that's still ancientware. Not to mention it specifically says it's buggy and alpha, and in the testimony both the source and the server seems to have been XP machines.


Any alternative solution? VLC doesn't cut it; I need the output from both Spotify and iTunes. I'm not limited to PulseAudio, I just know it's easy to configure.

edit: Latency is also a non-issue; even if sound is delayed 5 seconds, as long as it plays consistently on the sink, she's happy.

---

### Post by markbuntu on 2009-04-10
Set up a shoutcast server and aim it at the ubuntu machine. The pulse windows project is lanquishing due to lack of any developer willing to write and maintain the code. Lennart is always looking for volunteers.

---

### Post by merlinn31 on 2009-07-01
Did you ever figure out how to stream audio from a Windows machine to a Linux machine?  My laptop speakers suck, and I'd like to forward audio to my media center.  You mentioned "VLC won't cut it".  I'm not even sure how I'd get that to stream sound.

---

### Post by 0xdeadc0de on 2009-09-08
I know this is a little late, but check out liveincode. Download it, put it somewhere. then get ssh for windows (I installed openssh, then added C:\Program Files\OpenSSH\bin to the windows system path (right click my computer, go to properties, then advanced/environment variables, scroll down on the bottom list until you find Path, edit it, add ;C:\Program Files\OpenSSH\bin to the end)
then run this little batch script in the liveincode folder (Or add liveincode to your system path too to run the batch script from anywhere)

linco.exe --flag-files -B 16 -C 2 -R 44100 | ssh.exe -p15200 LinuxUsername@192.168.10.75 "cat - | pacat --server 127.0.0.1 --playback"

---Notes---
replace LinuxUsername with a username setup on the linux machine, 
replace 192.168.10.75 with the ip of the linux machine
I run ssh on port 15200 instead of the standard 22, so you can remove the -p15200 as well

You may want to look into setting up pre-shared ssh keys as well so a password doesn't need to be typed every time

ssh ftw! :popcorn:

Also, you need to open your volume controls in windows, go to the recording section(options/properties/input), and make sure "Wave Out Mix" is checked as the selected recording device. liveincode is designed to pipe the recording device (Which by default is the microphone) to another application, in this case, ssh.

There will be a few seconds delay so not for watching movies on windows with stereo sound, but excellent for your case. \\:D/
----------

---

### Post by paulmcq on 2010-10-13
This post is rather old by now, so it may help someone to know that it works fine for TTS from WinXP SP3 to Ubuntu Lucid 10.4.

Thank you very much, 0xDeadC0de. On my first try, I failed to follow your "Wave Out Mix" instructions. After that, perfect.
FWIW, my exact batch file is:
<code>
linco.exe -B 16 -C 2 -R 44100 | \bin\plink.exe PASERVER "cat - | pacat --playback"
</code>
Of course, that is all on one line. Take care with the quotes. Assumes passwordless SSH has been set up.

---

### Post by fivestones on 2011-07-21
Just wanted to say that this still works even with the 7-year-old liveincode, streaming all the audio from my Windows 7 machine to my Lucid Ubuntu machine beautifully. Finally.

(I had been looking for something to do this and send it to airplay (I have shairport on Ubuntu making it look like an airport server), but couldn't find anything other than the pay-for airfoil.)

Thanks for the help previous posters. I wouldn't have thought to string together the output from lineincode with pacat on a different computer across the network using plink. Brilliant.


My specific command is:
linco -B 16 -C 2 -R 44100 | plink SERVERIP -l USERNAME -pw PASSWORD "cat - | pacat --playback"

(Note that the way I'm doing this, it's sending an unencrypted password over the network and is very unsecure, but you can set up plink to do this securely with a key; this worked for me for testing purposes.)

---

### Post by mikecariotoglou on 2011-09-02
I had exactly the same requirement as the poster of this thread, and the same topology. I spent three days looking for a solution, went down the same paths you folks did, and finally set up a very similar solution like the one described here,with some twists :

*. The concept is the same : you get the audio from the windows machine,and pipe it to the Linux machine (you can also pipe it to multiple machines, by duplicating the source streaming commands

*. using netcat on the SOURCE machine is something you cannot avoid. However, using netcat on the Linux (destination) machine, should be avoided, because the netcat | pacat chain adds a latency of 3-4 seconds, with or without ssh. Fortunately, this can be avoided by streaming directly to the pulseuadio server!

Here is how to do it : (Ubuntu 10.04) :
edit /etc/pulse/default.pa (and system.pa, if you are running pulse as system instance).
add at the end :

load-module module-simple-protocol-tcp port=5000 #choose your port here.

restart your session or system to reload pulse. it will now listen to the port you specified, and play any raw audio (format 44100/16/stereo) you stream to that port.

this works like a charm, with less than 1 sec latency. some previous posts seemed to believe that there was a problem with starting/stopping the stream. I can confirm that this is not an issue anymore, with the pulse shipped with 10.04 (0.9.21).

make sure pulse is running, 
(ps aux | grep pulse)

and do the following in the windows machine:

linco -B 16 -C 2 -R 44100 | nc <Linux IP> 5000

Hint: if, like me, you did not want to hear the audio in the source (windows) machine, and/or you don't have a "what you hear" input, you can use a virtual audio card simulator, send the output of your music player (mediaMonkey in my case) to the virtual card output, and pick it up via linco on the virtual card's simulated input. this is how I am set up, and it works really great.

I found two such emulators for windows :

1. Virtual Audio Cable (commercial, around 25 euros)
[http://software.muzychenko.net/eng/vac.htm](http://software.muzychenko.net/eng/vac.htm)

2. VaCard (freeware)
[http://www.barix.com/downloads/Software_tools/221/](http://www.barix.com/downloads/Software_tools/221/)

I am using (2), which is rather basic, but works fine.

so, finally the chain is :

mediaMonkey -> vacard -> linco -> netcat ---->pulseAudio-simple-tcp

Remember to set your default INPUT device to vacard in control panel, because linco reads the default input only.

Hope this helps someone...

---

### Post by Helios423 on 2011-09-11
I tried Vacard from your link, but... if you installed Vacard, why even bother with linco/netcat? Vacard comes with a streamer, which can be used to stream either mp3 (up to 48khz/320kbit) or raw pcm.

In my case I streamed it to my network's broardcast (i.e. rtp://192.168.0.255:4444) and had a VLC on my linux-box listen to rtp://@:4444. Although 48khz pcm didn't seem to work, the rest of the options work just as well as any of the other Linco-solutions mentioned here. I'm guessing if you'd stream tcp to your server, similar to your netcast command, you could use pcm over pureaudio directly. I didn't even select an alternative device, it could just hook up to the default windows recording device similar to what linco does.
It has some other options for streaming as well, but I didn't bother to explore those.

So you should be able to reduce your chain to:
mediaMonkey -> vacard streamer ---->pulseAudio-simple-tcp

or  to my variant:
mediaMonkey -> vacard streamer ----> vlc/other streaming client

---

### Post by bug67 on 2011-09-11
I use [Airfoil]("http://www.rogueamoeba.com/airfoil/"). Airfoil runs on your computer (Mac or PC) and is able to stream *any* audio source from the computer running it to *any* device running [Airfoil Speakers]("http://www.rogueamoeba.com/airfoil/speakers.php").

I'm using Airfoil to stream audio from my Windows 7 PC to my living room stereo via AirPort Express and then to my Linux machine in the kitchen via Airfoil Speakers for Linux.  I had to [add some .dll files to make Airfoil Speakers for Linux to work]("http://kevin.colyar.net/2009/12/fixing-airfoil-speakers-for-ubuntu/") but, there was easily available info on line on how to do that.  However, since you would be streaming from a Mac, that may not even be necessary.
__________________
Dell XPS 400 Linux Mint 10 (Julia)

---

