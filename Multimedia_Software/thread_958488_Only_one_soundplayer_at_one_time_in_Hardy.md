---
title: "Only one soundplayer at one time in Hardy?"
date: 2008-10-25
forum: Multimedia Software
---

### Post by Azyx on 2008-10-25
Hey
I have make a new installation of Hardy (8.04).

I have installed Flashplayer so I can look at Youtube. My problem is that if i listen to musik or movies in Rhytmbox or Totem and pause to listen/look at Youtube, there is no sound. I have to close Rhytmbox/Totem completly. The same thing is nessesary if I listen on Youtube and want to play mp3 och movies. No sound untill I completly shout down Firefox/Youtube. Sometime firefox don't close down completly, so I need to kill firefox thrue Top or System Monitor.

My hardware is a follows:

Azyx@datorn:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 0 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:07.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
01:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
01:0a.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
01:0a.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
01:0a.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
01:0a.3 FireWire (IEEE 1394): NEC Corporation IEEE 1394 Host Controller (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)


My soundcard is the following:

Azyx@datorn:~$ cat /proc/asound/cards
 0 [CMI8738        ]: CMI8738-MC6 - C-Media CMI8738
                      C-Media CMI8738 (model 55) at 0xd000, irq 22

I have an AMD XP3000+.

I Think the problem beguin then Ubuntu start use Pulsaudio, or maybee then the start using ALSA-mixer.
Another or maybe simular problem is that there are drop-out in the sound, if I for instanse open a new windor, or use the computer to something else. I have tried to get the music-player another NICE-value. 

Cheers Azyx

---

### Post by edyeeh on 2008-10-25
I had the same problem here. Using amarok, only one can play when loaded simultaneously with youtube.

I tried an experiment and loaded Youtube first then opening Amarok. Then I got an error saying that "xine was unable to initialize any audio drivers"

I looked at the preferences on amarok. Seeing that amarok only has the 'xine engine' option, I changed another option in output plugin from 'alsa' to 'autodetect'. It worked, it could play simultaneously. So your guess with the problem sourcing from the use of alsa or pulse was right.

Maybe tinkering with the options of rhythm could do something.

---

### Post by CyberCod on 2009-01-18
having the same problem here.  It doesn't make sense that this is a setting problem in one single program.  Because it goes both ways.  If I start a movie in VLC, it has sound, but then any youtube videos played while that movie is playing cannot be heard.  And vice versa... if a youtube video is played, VLC will produce no sound.  I am using the same exact sound card.

I thought I had something configured wrong, but I'm guessing its just something with this card.  Thankfully I have a bunch of other sound cards laying around.  This can be an annoying bug.  But thats what it is... a bug.  Not something you did wrong.  

If I change all the settings in the Sound settings application (gnome-sound-properties)to Alsa, then Totem and Firefox can both still play sound, but VLC cannot.  So until I switch the sound card, I'll be using totem.

---

### Post by tegnoto89 on 2009-01-18
I realize I have a thread on this up, but I've gotta bump - I think this more accurately describes the problem.

Anyone have suggestions?

---

### Post by HavocXphere on 2009-01-18
It's an alsa issue. Something about it taking full control of the sound card. Not sure what the fix is, but I've heard talk of something involving dmix solving the problem.

Not a pulseaudio issue - I've got the same thing on kubuntu...which doesn't use Pulse.

In for solution.

---

### Post by tegnoto89 on 2009-01-18
SOLVED (for me at least)

Simply got rid of pulseaudio and installed esound!

[http://ubuntuforums.org/showthread.php?t=963914&highlight=remove+pulseaudio](http://ubuntuforums.org/showthread.php?t=963914&highlight=remove+pulseaudio)

---

### Post by Azyx on 2009-01-18
But what do Kubuntu use? u can't get rid of pulsaudio, if it does not exist in Kunbuntu ;)

> **tegnoto89 said:**
> SOLVED (for me at least)

Simply got rid of pulseaudio and installed esound!

[http://ubuntuforums.org/showthread.php?t=963914&highlight=remove+pulseaudio](http://ubuntuforums.org/showthread.php?t=963914&highlight=remove+pulseaudio)

---

### Post by HavocXphere on 2009-01-18
arts seems to be the esound equivalent for kubuntu users. Neither is working for me though.:(

I find it somewhat annoying that kubuntu and ubuntu went in different directions with the sound thing (Pulse vs Phonon).

---

### Post by markbuntu on 2009-01-18
I am using KDE4 in Intrepid with pulseaudio and do not have these problems. Phonon and pulseaudio do not seem to be causing any conflicts. I installed KDE4 after I installed Intrepid gnome so your results may be different.

I also do not have these problems in my hardy installs. Rather than remove pulseaudio it is better to get it working properly. You can do that by following this guide

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If you need more extensive help you can go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

