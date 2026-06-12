---
title: "Sound Crackling"
date: 2008-11-19
forum: Multimedia Software
---

### Post by happyhour on 2008-11-19
I turned on my computer today to find that the sound has stopped working correctly, all it does is crackle when playing any sound.

It was fine last night, and i don't think i have changed any settings.

I have used the sticky guide at the top of the page and it has not worked.

help

---

### Post by Tom.Servo on 2008-11-19
What do you have your audio config set to? Automatic, ALSA, etc?

---

### Post by happyhour on 2008-11-19
in system > preferences > sound
**sound events**
sound playback : autodetect

**Music and Movies**
sound playback : autodetect

**Audio Conferencing**
sound playback : autodetect
sound capture : ALSA

**Default Mixer Tracks**
Device : Playback: ALSA PCM on front: 0

---

### Post by Tom.Servo on 2008-11-19
Try and set it from autodetect to ALSA.

---

### Post by ljmoore on 2008-11-19
I have exactly the same problem (turned on computer to find sound was cracking), I have tried to change the settings to ALSA but that didn't work.
Any clues as to what might be going on? Thanks :)

---

### Post by psyke83 on 2008-11-19
Set the sound playback options back to Autodetect. Your problem is most likely because your PCM mixer's volume is muted/set to 0%. Check it via alsamixer:

```
$ alsamixer -Dhw
```

P.S. Searching the forum is always worthwhile. I've replied to similar threads at least half-a-dozen times in the past week.

---

### Post by c_riggan on 2008-11-19
> **psyke83 said:**
> Set the sound playback options back to Autodetect. Your problem is most likely because your PCM mixer's volume is muted/set to 0%. Check it via alsamixer:

```
$ alsamixer -Dhw
```

P.S. Searching the forum is always worthwhile. I've replied to similar threads at least half-a-dozen times in the past week.

I was having the same prob.. thanks alot.. search really helps huh.

---

### Post by equusaustralus on 2008-11-23
> **psyke83 said:**
> Set the sound playback options back to Autodetect. Your problem is most likely because your PCM mixer's volume is muted/set to 0%. Check it via alsamixer:

```
$ alsamixer -Dhw
```

P.S. Searching the forum is always worthwhile. I've replied to similar threads at least half-a-dozen times in the past week.
Psyke83, thanks for the post, increasing the PCM volume did the trick for me as well... strange bug!

---

### Post by ulster_con on 2009-01-16
> **psyke83 said:**
> Set the sound playback options back to Autodetect. Your problem is most likely because your PCM mixer's volume is muted/set to 0%. Check it via alsamixer:

```
$ alsamixer -Dhw
```

P.S. Searching the forum is always worthwhile. I've replied to similar threads at least half-a-dozen times in the past week.

thanks a mil, that worked for me :D

---

### Post by donmiguel on 2009-02-11
wonderful. not the first time this thread helps me =) hehe

---

### Post by DrewBoo on 2009-02-18
> **psyke83 said:**
> Set the sound playback options back to Autodetect. Your problem is most likely because your PCM mixer's volume is muted/set to 0%. Check it via alsamixer:

```
$ alsamixer -Dhw
```

P.S. Searching the forum is always worthwhile. I've replied to similar threads at least half-a-dozen times in the past week.

Thank you, psyke83.  Fixed.

---

### Post by dtr583 on 2009-02-18
> **psyke83 said:**
> Set the sound playback options back to Autodetect. Your problem is most likely because your PCM mixer's volume is muted/set to 0%. Check it via alsamixer:

```
$ alsamixer -Dhw
```

P.S. Searching the forum is always worthwhile. I've replied to similar threads at least half-a-dozen times in the past week.

After the latest system update I have crackling sound in flash and audacious.
I've checked my PCM mixer's volume and it's not muted.
Solution?

---

### Post by v1nsai on 2009-02-23
strangely, my pcm volume was all the way up, but decreasing it a little bit seems to have cleared it up.  I'm not asking questions and I'm just going to walk away while whistling....

---

### Post by johnkemp on 2009-03-14
> **psyke83 said:**
> Set the sound playback options back to Autodetect. Your problem is most likely because your PCM mixer's volume is muted/set to 0%. Check it via alsamixer:

```
$ alsamixer -Dhw
```

P.S. Searching the forum is always worthwhile. I've replied to similar threads at least half-a-dozen times in the past week.

This problem presented itself to me out of the blue last night and been driving me crazy.  This fix worked like a charm, thank you. :D

---

### Post by XopherH on 2009-04-02
> **psyke83 said:**
> 
```
$ alsamixer -Dhw
```


this is all that I needed.  so simple, i am slightly ashamed for reinstalling from synaptic first.

---

### Post by n1h0k3r on 2009-04-24
worked, creepy.

---

### Post by travm on 2009-04-26
best 4 line post ever.  Fixed my problem really quick.  Almost woke the house up though when i clicked test and it worked.  hella loud. :)

---

### Post by nem515 on 2009-04-27
> **psyke83 said:**
> Set the sound playback options back to Autodetect. Your problem is most likely because your PCM mixer's volume is muted/set to 0%. Check it via alsamixer:

```
$ alsamixer -Dhw
```

P.S. Searching the forum is always worthwhile. I've replied to similar threads at least half-a-dozen times in the past week.

That worked perfectly. Thank you :)

---

### Post by wimpelmeesje on 2009-04-28
This solution worked for me in 8.10 but I just upgraded to 9.04 and the crackling has come back, plus the solution doesn't work for me anymore. The crackling remains, whatever the position of the PCM slider.

---

### Post by mickey57 on 2009-05-20
[https://bugs.launchpad.net/ubuntu/+source/sdl-mixer1.2/+bug/66483]("https://bugs.launchpad.net/ubuntu/+source/sdl-mixer1.2/+bug/66483")
****************************
....I just did this:[http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html]("http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html")
...Got the sound to working great!...Screw Pulse Audio.

---

### Post by kedmond on 2009-09-03
> **psyke83 said:**
> Set the sound playback options back to Autodetect. Your problem is most likely because your PCM mixer's volume is muted/set to 0%. Check it via alsamixer:

```
$ alsamixer -Dhw
```

P.S. Searching the forum is always worthwhile. I've replied to similar threads at least half-a-dozen times in the past week.

Thanks!  You helped me out too!  :-)

-kedmond

---

### Post by Erszebet Lunah on 2009-09-09
Maybe not entirely the same problem but I thought I'd share it anyway:
I had crackling / popping sound when (and only when) playing audio cd's.
I'm using a Creative Audigy2 ZS soundcard with ALSA drivers (Kubuntu 9.04)
Solved it through Kmix->mixer window, selected the channel 'Audigy CD' and put the volume to 0.

---

### Post by Frenziefrenz on 2009-09-26
Thank you, raising the PCM volume solved my problem as well. Ubuntu 9.04 here. It happened some day after a restart and I have no idea why. I certainly hadn't been playing around with the PCM volume, or any volume at all for that matter. I don't recall if I noticed the PCM volume being down when the problem occurred, but probably not seeing how it wasn't even available in Ubuntu's volume mixer until just a moment ago when I upped it with the command line utility! If it had been in there, maybe I would have played with it at random... yet now that my problem's solved it's in there. I probably wouldn't have associated it with the problem either way since I still got that crackling sound, though.

---

### Post by Frenziefrenz on 2009-10-01
It happened again - turns out that it was somehow related to logging into KDE4 instead of Gnome. I don't know how to avoid this happening, though. :/

---

### Post by Ryazanov on 2009-10-04
> **psyke83 said:**
> Set the sound playback options back to Autodetect. Your problem is most likely because your PCM mixer's volume is muted/set to 0%. Check it via alsamixer:

```
$ alsamixer -Dhw
```P.S. Searching the forum is always worthwhile. I've replied to similar threads at least half-a-dozen times in the past week.

Thanks a lot! A had a bit different problem, playback was full of creeps, and using this command helped to resolve the issue, I had just reduced PCM down from red zone, and sound is just perfect at the moment! Thanks a lot! :D

---

### Post by suffer1989 on 2009-10-11
This command : > $ alsamixer -Dhw Doesnt work for me ... and all of a sudden im also getting cracking...

---

### Post by Albert Clarke on 2009-10-11
Don't use the onboard sound simply because its thin and tinny sounding and
completely inadequate for playing music and films.
 
I see you've avoided IRQ sharing which was a possible culprit.
Are you using the latest motherboard drivers from the manufacturer
and not just the ones in Windows? Same goes for your soundcard.
 
Your problem is most likely one of latency and some device trying to hog
resources.
Theres a utility called PCILatency
 [http://downloads.guru3d.com/download.php?det=951](http://downloads.guru3d.com/download.php?det=951)
that you can use to force devices to share the bandwidth equally.
For example graphics card sometimes get a latency of 200 or more and other
devices only get 32
- equalize the latency at 32 and all devices get an share.

---

### Post by m0rbidpercepti0ns on 2009-10-17
I have this same problem,and not only is my PCM turned all the way up *volume control>preferences>tell it to display PCM slider* but ive tinkered around to see if some obscure thing is causing an issue..and i cant find it. None of the sliders affect my sound at all besides PCM,Wave,and master volume. i tried running
$ alsamixer -Dhw 
But it didnt work and i got the error 
alsamixer: function snd_ctl_open failed for hw: No such device
Previously when i had no sound *for my card Digital output jack needs to be checked,unlike most cards" I know this command had brought up a graphical slider. Can anyone help? PS...sorry..i apparently cant figure out how to use the codebox:(

---

### Post by getmealive on 2010-03-05
hello
 
 I have installed Kubuntu 9.10 and have had problem with sounds cracks on my HP pavilion dv6618eo with HD nVidia audio. but I fixed this by installing the following packages:
 
 1. gedit: the official text editor of Gnome.
 2. gksude: installed this through Terminal
 
 after installion,I then entered the following code in terminal: 
 
 gksudo gedit /etc/modprobe.d/alsa-base.conf
 
 and then changed the following code in Alsa-config:
 
 options snd-hda-intel power_save=10 power_save_controller=N
 
 changed to: 
 options snd-hda-intel power_save=0 power_save_controller=N
 
 after all restarted the pc, and all was successfull, and the cracking sound fixed.
 
 in ubuntu, no need to install gksudo and gedit. just open terminal and paste in the following code:
 
 sudo gedit /etc/modprobe.d/alsa-base.conf
 
 or 
 gksudo gedit /etc/modprobe.d/alsa-base.conf
 
 then change the power save from 10 to 0.
 and restart pc.

---

### Post by ravalox on 2010-03-05
I installed 9.10 recently, and by installed 9.10 I mean installed mythbuntu 9.10, ubuntu 9.10, and xubuntu 9.10.  With every installation as soon as the sound comes online I'm greeted with an absurd amount of audio crackling.  It's relentless.  I have to leave my computer on mute because it sounds like some kind of static storm.  Any ideas as to what could be causing this nonsense?  I'm at my whits end, I've followed all the directions on this thread!

---

### Post by El Lance-O on 2010-05-06
I just purchased a Logitech N700 lapdesk with built-in speakers, and cracking is SEVERE on Lucid Lynx. It seems to be an encoding issue since some things cracking a lot than others, for example:

Crackling:
.avi playback
.divx playback
Streaming Shoutcast TV

No Crackling:
Flash video
.mp3 playback
Streaming radio (Pandora, Shoutcast)
.mp4 video playback (one file I tried worked fine)

But it's starting to be a file-by-file basis. Very irritating since it seems to be a direct problem with Pulseaudio, and we are pretty much forced to use Pulseaudio by default, and not easily presented with the option to change. Something needs to be developed differently there for sure.

---

### Post by El Lance-O on 2010-05-06
Tried removing Pulseaudio, and now I have no control over audio settings, including volume.

I've tried removing the .pulse folder, but it keeps being re-created, even after a reboot.

Any thoughts?

---

### Post by mickey57 on 2010-05-07
> **El Lance-O said:**
> Tried removing Pulseaudio, and now I have no control over audio settings, including volume.

I've tried removing the .pulse folder, but it keeps being re-created, even after a reboot.

Any thoughts?
.....*********......
[SIZE="3"]
.....I know the headache with Pulse-audio,I feel your pain.

.....I have gone back to running Pulse because it is so integrated within the system. I am running it on Fedora and Ubuntu,working fine now for me.

.....Here is what I would do:[COLOR="DarkRed"][SIZE="4"]sudo apt-get install pulseaudio[/SIZE][/COLOR]

....Re-boot and see if Pulse is working. If not then I would do this;

[COLOR="DarkRed"][http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8284273&postcount=4]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8284273&postcount=4")[/COLOR][/SIZE]

---

### Post by brooklynzoo81 on 2010-09-13
> **mickey57 said:**
> [https://bugs.launchpad.net/ubuntu/+source/sdl-mixer1.2/+bug/66483]("https://bugs.launchpad.net/ubuntu/+source/sdl-mixer1.2/+bug/66483")
****************************
....I just did this:[http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html]("http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html")
...Got the sound to working great!...Screw Pulse Audio.

I tried that link and it worked!  But my sound icon on the upper right is gone, and when i go to SYSTEM-->PREFERENCES and click on sound a pop up windows comes up and tells me "waiting for sound system to respond"  Any ideas? thanks.

---

### Post by stephen730 on 2011-06-21
For me, I had to turn my pcm volume DOWN, it was all the way up. Thanks for this though!

---

### Post by ebruzzone on 2012-05-06
I just wanted to confirm that 12 LTS has the same audio problem and this is the only working solution. After a succesful upgrade from previous Ubuntu versions I was going nuts about the crackling sound (and lost several days on google looking for a solution) that I did a clean up install... twice! Again, this is the only solution so thanks a lot. 

Si alguien esta buscando una solucion al audio entrecortado leer este post. Reinstalar Ubuntu no es la soluciòn. saludos

---

### Post by oldos2er on 2012-05-06
Old thread closed.

---

