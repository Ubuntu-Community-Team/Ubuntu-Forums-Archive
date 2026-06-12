---
title: "Can't hear sound but can see on playback monitor"
date: 2009-10-01
forum: Multimedia Software
---

### Post by siddhant3s on 2009-10-01
I know that there are already a lots of thread pointing towards sound problem. I searched the forums/web, tried my best not to ask help ( I never had a problem in which was not resolved after rigorous searching the web, but this one ), but now I am up. Sorry folks, but here it goes:

I installed Jaunty from its CD, everything was fine until I downloaded and installed the updates from the update manager. The sound stoped playing. Mind you that my hardware is perfectly fine as I am able to play sound on other OSs(namely the Vista that came installed with this HP Pavilion 1161Tx Laptop) (even on Ubuntu LiveCD, sound works ).
So there is definitely some problem with configuration of drivers,

I followed few guides on the web and installed padevchooser (or something like that) and found an interesting behaviour.

But first thing first:
```
siddhant3s@x10n:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


siddhant3s@x10n:~$ lspci -v | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
 
```Now, I play a music file and click on the PulseAudioApplet and choose "Volume Meter (Playback)". When I do so, I am able to see the meter telling me that the sound is there. It goes up and down (Image attached).

Please Help.
Thank You.

EDIT:Forgot to mention that I even installed Timidity for Tux Guitar. It also used to work fine, but now as there is no sound, I can't here anything from TuxGuitar.

---

### Post by scragar on 2009-10-01
```
lsmod|grep '^snd' | column -t
```
Check if your sound modules(and hence drivers) are loaded, could you post the output please?

---

### Post by siddhant3s on 2009-10-01
Here it is
```
siddhant3s@x10n:~$ lsmod|grep '^snd' | column -t
snd_hda_intel       435252  2
snd_pcm_oss         46336   0
snd_mixer_oss       22656   1   snd_pcm_oss
snd_seq_dummy       10756   0
snd_pcm             83076   2   snd_hda_intel,snd_pcm_oss
snd_seq_oss         37760   0
snd_seq_midi        14336   0
snd_rawmidi         29696   1   snd_seq_midi
snd_seq_midi_event  15104   2   snd_seq_oss,snd_seq_midi
snd_seq             56880   7   snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer           29704   2   snd_pcm,snd_seq
snd_seq_device      14988   5   snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                 62756   14  snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc      16904   2   snd_hda_intel,snd_pcm

```

Forgot to mention that I even installed Timidity for Tux Guitar. It also used to work fine, but now as there is no sound, I can't here anything from TuxGuitar.

---

### Post by scragar on 2009-10-01
OK, well your sound modules are loaded, try:
```
alsamixer
```And adjust your volume and unmute everything, failing that being the issue you might also want to try running these two:
```
# first a simple line to select your sound card from a drop down
sudo apt-get install asoundconf-gtk && asoundconf-gtk

# next forcing the reloading of alsa
sudo /sbin/alsa force-reload
```
You may also want to check your user is a part of the audio group.

---

### Post by siddhant3s on 2009-10-01
All my slider in alsamixer were up to 100.
I did asoundconfgtk and chose pulse.
And then I did the force-reload.

Logged out, Logged in. Still same.

I also checked the group permission. Pulse group has my username.

Hey, but after doing what you said,  all my slider in the alsamixer are gone, just one is left. Previosly there were about 4 sliders. All gone.

---

### Post by scragar on 2009-10-01
Don't set your sound card to pulse, change it to your other option, the one for your sound card(I personally hate pulse, but that's because of early issues when pulse was still not working with flash or multiple sound channels)

---

### Post by siddhant3s on 2009-10-01
Ok So I put asounconfgtk on to Intel. I got my alsamixer with similar (not same) kind of sliders.
But still no sound. I tried logging out.

---

### Post by scragar on 2009-10-01
OK, you shouldn't need to log out though unless you change your groups, don't worry too much about that.

Could you try killing off pulse, might be responsible:
```
killall pulseaudio
```
If that doesn't work I'm running short of ideas other than to downgrade alsa or manually update it.

---

### Post by delix on 2009-10-01
I have the exact same problem, i have visited all the other pages, and i get the same, pulseaudio shows the sound levels but i get no sound, did everything you said in this traid and many others, still no sound, my sound card is an intergated intel, on an asus laptop

---

### Post by delix on 2009-10-02
i even tried with oss not with alsa, and still the same, the mixer shows the leves but no sound
heeeeeeeeeeeeeeeeeeeeeeeelp

---

### Post by eastavin on 2009-10-02
seems that you are not alone.   I had sound too until switching to Ubuntu from Windows xp.  Have you opened a trouble ticket?  I see a lot of compaq/HP users surfing these forums and other sites looking for solutions but very few trouble tickets.

---

### Post by delix on 2009-10-02
a ticket with ubuntu or my manufacturer

---

### Post by siddhant3s on 2009-10-02
> **eastavin said:**
> seems that you are not alone.   I had sound too until switching to Ubuntu from Windows xp.  Have you opened a trouble ticket?  I see a lot of compaq/HP users surfing these forums and other sites looking for solutions but very few trouble tickets.
So, how should I open a trouble ticket?
And by the way, does anyone here know how to downdate( opposite of update) Ubuntu, i.e. how to uninstall whatever updates Ubuntu did?

---

### Post by siddhant3s on 2009-10-05
Well, I ultimately found out the fix. I can't say if it is the 'right' way, but definitely this is not the wrong way.

I observed that after the update, in my grub boot-up menu, there was an additional updated Linux Kernel which used to get booted up. So, I booted the other one, i.e. the older one, and ultimately, my sound worked. Then I configured my grub boot list and made that particular kernel the default one.

---

### Post by MasterOfTheHat on 2009-10-05
The same thing happened with my setup. I booted it up this morning after not having it powered on since Friday, and there was no sound. Even the mute button on the laptop was amber, (it has worked before, but the light never changed, i.e. It was always white, even when the sound was muted).

After reading siddhat3s' post, I rebooted and had grub boot 2.6.28-14-generic instead of 2.6.28-15-generic, and the sound works now. 

That new kernel was just installed on Friday. What are we missing?

---

### Post by mailvatsy on 2009-10-05
hi ! I am new here. I use a HP 1242. Ubuntu will not play sounds. I tried reading a few posts and making good. No avail. on Win it says IDT high def codec. How can i enable sounds ?

---

### Post by delix on 2009-10-05
i found a way searching by my laptop model, it is easy, it's here [http://ubuntuforums.org/showthread.php?t=1191356&highlight=HDA+Intel+VT1708S](http://ubuntuforums.org/showthread.php?t=1191356&highlight=HDA+Intel+VT1708S), down by the end of the page it goes something like this

Well, this pretty much solved it for me!

Install alsa 1.0.20 as described here;
[http://monespaceperso.org/blog-en/20...tu-jaunty-904/]("http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/")

And tweak the hda-verb thingy described in following post;
[http://georgia.ubuntuforums.org/show....php?p=7564125]("http://georgia.ubuntuforums.org/showthread.php?p=7564125")


 	Quote:
 	 	 		 			 				 	Code:
 	sudo -s
wget [ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/misc/hda-verb/hda-verb-0.3.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/misc/hda-verb/hda-verb-0.3.tar.gz)
tar xf hda-verb-0.3.tar.gz
cd hda-verb-0.3
make
cp hda-verb /usr/bin
gedit /etc/rc.local 
And add this line before "exit 0"
 	Code:
 	hda-verb /dev/snd/hwC0D0 0x1c SET_EAPD_BTLENABLE PCM

---

### Post by linuxnewbie1 on 2009-10-05
Hello -

new to Ubuntu, tried it a couple years back but couldn't get any audio to work and therefore switched to a different flavor, Xandros and then Zenwalk. My computer died and got one as a hand-me-down. It came with Ubuntu 9.04 already installed on it but alas, no sound. Tried finding a fix for it but there are so many different pages out there and I am not real familiar with Ubuntu so I was hoping someone might tell me where to start and how to try and get sound. :(

Please help, desperate as I would really like to try Ubuntu out but I just can't for the life of me figure out this audio thing.

Yes, am a noob when it comes to Ubuntu,

Thanks in advance for any help offered!!

---

### Post by delix on 2009-10-06
what computer do you have, your sound card, try searching the forums for your sound card specifically that's how i fixed mine, if there is none then i suggest you try this

[http://monespaceperso.org/blog-en/20...tu-jaunty-904/](http://monespaceperso.org/blog-en/20...tu-jaunty-904/)
it should update your alsa driver, 
if after the update you still have no sound then i suggest looking through this
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
or this
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
but read through them carefully, most of the users get their sound fixed right after upgrading alsa, turning their levels in the mixer to maximum or additionaly after the alsa upgrade install the pulseaudio sound server
post back after you've tried

---

### Post by delix on 2009-10-06
what computer do you have, your sound card, try searching the forums for your sound card specifically that's how i fixed mine, if there is none then i suggest you try this

[http://monespaceperso.org/blog-en/20...tu-jaunty-904/](http://monespaceperso.org/blog-en/20...tu-jaunty-904/)
it should update your alsa driver, 
if after the update you still have no sound then i suggest looking through this
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
or this
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
but read through them carefully, most of the users get their sound fixed right after upgrading alsa, turning their levels in the mixer to maximum or additionaly after the alsa upgrade install the pulseaudio sound server
post back after you've tried

---

### Post by BAiHAX on 2009-10-06
> **scragar said:**
> OK, well your sound modules are loaded, try:
```
alsamixer
```And adjust your volume and unmute everything, failing that being the issue you might also want to try running these two:
```
# first a simple line to select your sound card from a drop down
sudo apt-get install asoundconf-gtk && asoundconf-gtk

# next forcing the reloading of alsa
sudo /sbin/alsa force-reload
```You may also want to check your user is a part of the audio group.

Thank you! The sound have appeared.

---

### Post by linuxnewbie1 on 2009-10-06
> **delix said:**
> what computer do you have, your sound card, try searching the forums for your sound card specifically that's how i fixed mine, if there is none then i suggest you try this

[http://monespaceperso.org/blog-en/20...tu-jaunty-904/](http://monespaceperso.org/blog-en/20...tu-jaunty-904/)
it should update your alsa driver, 

I tried looking through that article but it isn't really written for someone that has little idea as to what they are doing.Do I just open a terminal and start typing everything that it says in the quotes sections of his article? It isn't really "self explanatory" as to what one does as he presumes it is. Sorry to sound like such a newbie but that is why I posted in this section. On other versions I tried the audio just worked, I didn't need to do anything else.

As for the computer, I got it from someone else and all that it says on the tower is Micron Client pro and Pentium III.

---

### Post by delix on 2009-10-06
as for the link the words in the blocks (the blue ones are commands) you type them in your terminal, 
every new line is a command, 
except in the first blue block the second line, 
all the others blocks have commands only in them, 
you can copy one line at a time and paste it in the terminal with ctrl+shift+v

---

### Post by kcox5342 on 2009-10-06
Edit, whoops, wrong thread...

---

### Post by kcox5342 on 2009-10-06
OK, maybe I'm confused in all the excitement about getting my sound working.  Scragar - that post about asoundconf-gtk has fixed my lack of sound on my mythtv backend.  Thanks!!

---

### Post by nirax on 2009-10-07
updated to 9.10 and have the same problem..
unfortunately trying to hear sound and applying your tips runs in:

> asoundconf-gtk sh: /usr/bin/asoundconf: not found
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!


i also have all snd loaded:

> lsmod|grep '^snd' | column -t
snd_seq_dummy       2656    0
snd_seq_oss         28576   0
snd_seq_midi        6432    0
snd_seq_midi_event  6940    2   snd_seq_oss,snd_seq_midi
snd_seq             50224   6   snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm_oss         37920   0
snd_mixer_oss       16028   1   snd_pcm_oss
snd_ice1724         95932   3
snd_ice17xx_ak4xxx  3420    1   snd_ice1724
snd_ac97_codec      101216  1   snd_ice1724
snd_ak4xxx_adda     8028    2   snd_ice1724,snd_ice17xx_ak4xxx
snd_ak4114          8892    1   snd_ice1724
snd_pcm             75296   5   snd_pcm_oss,snd_ice1724,snd_ac97_codec,snd_ak4114
snd_page_alloc      9156    1   snd_pcm
snd_pt2258          3580    1   snd_ice1724
snd_i2c             5148    2   snd_ice1724,snd_pt2258
snd_rawmidi         22208   2   snd_seq_midi,snd_ice1724
snd_timer           22276   2   snd_seq,snd_pcm
snd_seq_device      6920    5   snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                 59204   19  snd_seq_oss,snd_seq,snd_pcm_oss,snd_mixer_oss,snd_ice1724,snd_ac97_codec,snd_ak4xxx_adda,snd_ak4114,snd_pcm,snd_pt2258,snd_i2c,snd_rawmidi,snd_timer,snd_seq_device


one strange thing is:
the gnome sound applet (the loudspeaker symbol in the top right) offers only []mute and sound preferences on a right click, and a main volume bar on a left click. double clicking it has no effect (not as previous a mixer will appear)

sound preference ahrdware is Env24PT driver..

would be glad if someone has an idea.. it really sux wihtout sound. :(

ps. i already unmuted everything with alsamixer, or tried to restart alsa, or delete the .pulse... and even reinstalled alsa

>   521  rm -r /home/nirax/.pulse
  522  killall pulseaudio
  524  sudo /etc/init.d/pulseaudio restart


aplay recognizes the snd card

> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SN25P [Shuttle SN25P], device 0: ICE1724 [ICE1724]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SN25P [Shuttle SN25P], device 1: ICE1724 IEC958 [ICE1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SN25P [Shuttle SN25P], device 2: ICE1724 Surrounds [ICE1724 Surround PCM]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1


kernel info
> 
 uname -a
Linux nirax-desktop 2.6.31-12-generic #39-Ubuntu SMP Mon Oct 5 22:08:01 UTC 2009 i686 GNU/Linu

---

### Post by MasterOfTheHat on 2009-10-07
I ended up having to reinstall ALSA to get it to even acknowledge my sound card existed after the upgrade. 

See [post here]("http://ubuntuforums.org/showpost.php?p=8062409&postcount=6").

---

### Post by nirax on 2009-10-07
ok, seems it was a 9.10 bug.
since the last aptitude upgrade some minutes ago, where the kernel got installed again ( 2.6.31-12-generic Oct 7 release) possibly with some driver fixes and some alsa parts aswell my sound is back working. pheeeWW!! :-) thanks@dev

---

### Post by delix on 2009-10-07
so it's recommended to update aptitude and the kernel. hm, i tried the beta and yes the sound was a problem too, but also it had a problem with the ntfs partitions it couldn't grant me permission, i treid a fix i found online but it didn't work, maybe this fixes that too

---

### Post by nirax on 2009-10-07
no upgrade of aptitude is required. with aptitude upgrade i meant what you may possibly do with synaptic. (synaptic is AFAIK the gtk frontend for aptitude). neverless: short said: 

[LIST]
[*]i checked for updates with my favored comand line package manager
[*]the upgrade to the new packages fixed the problem ;)
[/LIST] 

may possibly fix your problems as well if it started with 9.10

---

### Post by djtarki on 2009-11-01
> **scragar said:**
> OK, well your sound modules are loaded, try:
```
alsamixer
```And adjust your volume and unmute everything, failing that being the issue you might also want to try running these two:
```
# first a simple line to select your sound card from a drop down
sudo apt-get install asoundconf-gtk && asoundconf-gtk

# next forcing the reloading of alsa
sudo /sbin/alsa force-reload
```You may also want to check your user is a part of the audio group.


It worked for me . Thank you!

---

### Post by kforum on 2010-03-14
using sudo /sbin/alsa force-reload
 worked for me, and it seems works for a lot of people, THIS THREAD NEEDS TO BE STICKIED ASAP. its the essential solution to upgrade sound problems on 9.10.


cheers

edit: the sad part is having to do this every time...

---

