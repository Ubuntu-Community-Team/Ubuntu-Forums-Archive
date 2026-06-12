---
title: "sound not working after upgrade to 9.04"
date: 2009-04-25
forum: Multimedia Software
---

### Post by bhavikpatel on 2009-04-25
Hi All, 

I was successfully using ubuntu 8.10 till yesterday evening, and my mind gone bad and I decided to upgrade it to 9.04. After upgrade, everything was perfect, and sound was working perfectly. I watched a movie yesterday night, and I slept after that.  

Now I wakeup today morning, and "bang"! The sound is not working in ubuntu!
I really like ubuntu for it's speed and effieciency, but the problem like this forces me to use Vista even though I hate it!!

Now coming to my problem, can anyone tell me what the heck is going on in my PC? 

I have tried following steps mentioned in past threads in this forum, but nothing working. 

Here's the output of some of the commands: 

$ cat /proc/asound/modules 
  0 snd_hda_intel

$ cat /proc/asound/cards 
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf6480000 irq 21

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Please help me to solve this problem. I can give more info about my hardware, but you have to tell me which command I have to run, because I don't know the commands at the moment. 

Thanks for the help.

---

### Post by TheSlipstream on 2009-04-25
Sorry man, lots of us are having the same problem. I've tried heaps of things and nothing seems to fix it. Lets hope Canonical fixes this very fast.

---

### Post by blurt on 2009-04-25
Me too; upgraded to 9.04, and no sound! Tried uninstalling/reinstalling
drivers, etc., no dice. This forced me to install RealPlayer11GOLD.exe
on windows XP, even though this installer requires an internet connection.
Normally, I don't allow windows onto the internet, because of the sneaky
aspects of Microsoft's design, so I had to install the nic driver to XP
long enough to do the install, then quickly uninstall the windows nic
driver, since windows is a virus-magnet. Ugh! I also hope they fix this
sound problem fast.--blurt.](*,)](*,)

---

### Post by drrampgi on 2009-04-25
same problem for me in compaq presario CQ40.

---

### Post by wh276348 on 2009-04-25
No sound.  HP DV7 1260us sound working perfectly in Kubuntu 8.10.  After upgrade to Kubuntu 9.04 sound stopped working.

---

### Post by roemchine on 2009-04-25
It also stopped working on my HP HDX9480EG Laptop since I updated Ubuntu:confused:

The model of my sound card is:
> romana@romana-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: SigmaTel STAC9271D

I tried to install the lates driver, but it does not work:
[http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

Please help me [-o<

---

### Post by g.a. on 2009-04-25
well, here is another, from 8.10 to 9.04 I lost the sound on a Dell Precision M2400 with:

uname -r
2.6.28-11-generic

cat /proc/asound/modules
 0 snd_hda_intel

cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf6fdc000 irq 21

I tried a lot fo stuff with Kmix, PulseAudio e system Settings, posted on kubuntuforums.net, here, etc.

Any suggestion?

thanks
g.

---

### Post by edm1 on 2009-04-25
I know this sounds extremely patronising and probably not the cause but alot of people go a couple of days without sound after an upgrade before realising something has become muted in gnome volume control.

---

### Post by 4thfloorstudios on 2009-04-25
Having the same problem. Is there some bugreport one could post information to?

---

### Post by dave r on 2009-04-25
:confused: Same here, upgraded to 9.04 yesterday and no sound in Amarok, Rhythm player still working normally. Spent most of last night on this Forum trying fixes but nothing has worked.

---

### Post by markitoxs on 2009-04-25
Have you guys tried returning to the previous kernel?

---

### Post by gkgarg24 on 2009-04-25
Hey Guys, 

I was also having same problem after upgrade to ubuntu 9.04. I am running it on Dell Inspiron 1420n. I did the following steps after searching through forums. 

1>Run the following commmand
 [INDENT]sudo gedit /etc/modprobe.d/alsa-base [/INDENT]
2>Add the following text to it.  
[INDENT]options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes[/INDENT]
3>Save the file.
4>Rune the following commend : 
 [INDENT] sudo /etc/init.d/alsa-utils restart [/INDENT]
5>If this does not work try rebooting machine. Sound should be back again.


Hope this helps!

Regards

---

### Post by mrkeef on 2009-04-25
Didn't work for me :(

I had this problem following  aprevious upgrade. I can't remember what I did though.

---

### Post by mrkeef on 2009-04-25
Fixed the problem on my computer! 

Go to System-Preferences-Sound.

Change all the settings from ALSA to OSS. (Run the Test sound first- if it works go through the others and change them all)

---

### Post by Wistful on 2009-04-25
I have Realtek ALC889 and had problems with my sound in Ubuntu 9.04 and after applying these steps my sound is back!

Steps posted by [COLOR="Red"]gkgarg24[/COLOR]

---

### Post by 4thfloorstudios on 2009-04-25
Ok, found out what is working to at least hear anything :)

- Boot with kernel 2.6.27-11
- Set all audio devices to "OSS"

Seems, that my alsa-base package is at version 1.0.17 so maybe just wait for 1.0.19 to be in the updates.

---

### Post by gfxcoder on 2009-04-25
has anyone been able to get sound on an hp dv7t-2000?  i've tried adding the "usual" to sound.conf (options options snd-hda-intel model=...) with several variations of parameters, restarting alsa each time.  thanks!

---

### Post by SeanBlader on 2009-04-25
> **gkgarg24 said:**
> 
[INDENT]options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes[/INDENT]


Didn't help. All 5 volume sliders are at the max. I've tried 15 or so different model's in the alsa-base.conf file, I've tried irqpoll in grub, nothing makes sound work on my Adamo.

```

:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Lexda on 2009-04-26
Ok, so here's an interesting situation. Just upgraded to 9.04 on an Asus G50VT laptop. Internal sound system (the laptop speakers) works fine. However, there is no sound being sent through the audio port. Neither speakers nor earbuds work, and I know they're making a connection because I get mild feedback when I twist the plugin in the port (which is normal for my speakers).

The sound preferences thing didn't work. Anybody have a clue what would be causing that?

---

### Post by bhavikpatel on 2009-04-26
Hi All, 


I finally found a workaround for the sound problem. 
Run the alsamixer in the terminal, and see if you have any muted channels in that. If a channel is muted, it shows MM for that channel. 

Select a channel with lef or right arrow keys, and press M to unmute the channel. 

For me, the Master channel is muted every time I restart the PC. 
So I have to unmute it manually every time I boot the PC. 

But I am highly dissatisfied with the updates in 9.04 release. 

For example, I was using Ekiga's paid VoIP service, and it was working perfectly in 8.10. Not Ekiga is updated to 3.2.0 in ubuntu 9.04, and it's one bloody f***ing hell of a quality!!! I virtually have to shout in my headset, and still I can not be heard clearly. They have changed some codecs, and I don't know why they need to change a perfectly working codec, and replace it with some junk codec!!!

I mostly use my PC for watching movies, listening to music, and talking to my family on Ekiga VoIP. So ubuntu 9.04 is a huge disappointment for me!!!

---

### Post by g.a. on 2009-04-26
I tried what suggested by gkgarg24 but it did not work.

Also, some is suggesting to switch from "alsa" to "oss", I'm not sure of what it means, in attach please find a snapshot from 

system settings -> multimedia

as you can see the only available operation is test and change the order between the two (?) devices.

thanks in advance for any help. it is quite frustrating to spent almost one full day in try to fix what should be very basic in an o.s.

g.

---

### Post by roemchine on 2009-04-26
I downloaded the 2.6.27 kernel (mainline) and I can hear everything:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.27/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.27/)

---

### Post by g.a. on 2009-04-26
it is necessary to modify the kernel for a sound issue?

I'm surprised, compiz, plasmoid, all of them are nice features but if one has to spend days to recover basic functionalities I wonder if the robustness was forgot when sketching the ambicious roadmap...

best
g.

---

### Post by HardWaters on 2009-04-26
I had the same problem in **Compaq CQ40** intel.. 

it should be** solved** by doing the following:

open the alsa config file by:

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```at the end of the file just paste the following lines:

```
options snd-pcsp index=-2
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1
```

---

### Post by g.a. on 2009-04-26
thanks for the suggestion but it did not work
g.

---

### Post by zarthon on 2009-04-26
In this code what parts would be dependent on hardware?

I have some audio programs that I use infrequently for sound recording,mixing , and rythm generation and was wondering if these or dependencies could be complicating my situation?

As for the ones I do use when I pay a song in Quode Libet I get no sound but in pulse volume control i get meter on the sound and it looks like it's Mono! (ick) My quad core workstation degenerated into a broken Victrola.

When I run GNU Solfege I get the message in a dialog: "No module named oss_sequencer2". I am guessing I may need to muck with alternatives / soft links in addition to this fix. 

I going to try this fix. If it works we need to band together and advocate to push it upstream. The OSS solution is a ridiculously backward workaround but at least I can get this squared away. 

Does anyone else want to get audio working using pulseaudio and then mix local sound with sound from other network sources? 

Audio problems in the distro are leading me think about jump to another distro. Why did they break the OS? What is so complex. Why can other distros get it right but not Ubuntu? I am going to research fundamentals when I have the time. 

Someone was talking about having to shout. This problem is almost certainly audio gain control / mic boost being off rather than on. ( I imagine someone has already mentioned this but I thought I would throw it in.)


> **HardWaters said:**
> I had the same problem in **Compaq CQ40** intel.. 

it should be** solved** by doing the following:

open the alsa config file by:

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```at the end of the file just paste the following lines:

```
options snd-pcsp index=-2
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1
```

---

### Post by zarthon on 2009-04-26
In GNOME select "configure local sound server" using the pulseauido applet.
This may be installed for me because I had mucked with pulse in 8.10.

In pulseaudio preferences dialog

Go to "Multicast/RTP" tab and check to enable it, select radio button "create a separate device", then check "loopback to local speakers"

I believe my troubles could have been that I was creating a separate device and not looping back!

A serendipitous fix for me so far !  And so quick After my long blah blah blah. LOL !

---

### Post by Lexda on 2009-04-26
Alright, so none of the stuff here has worked. However, here's something interesting: I can get partial output if I only plug the headphones or speakers in part way. The laptop speakers continue sounding along with maybe 1/3 volume in the headphones/speakers. When the plug is put all the way in, then, all sound ceases.

AlsaMixer has my card being "HDA Intel," with the chip as "Generic 10de ID 5." All bars look normal, except for the "Headphones" bar, which has no number or colored bar above it. I would assume my problem is that, but I can't find a way to activate its volume. Any ideas?

---

### Post by markbuntu on 2009-04-26
There are a lot of issues with the alsa snd-hda-intel driver which is in the kernel. There are some patches on the way so expect updates. The vast majority of sound problems with laptops have to do with this driver and it is not an especially easy thing to parse since autoprobing can only get so far. There are a huge pile of modprobe options available for specific machines and the alsa docs I can find are very sketchy about that. If anyone can find a definitive list, please provide a link.

---

### Post by RangerX_308 on 2009-04-27
> **gfxcoder said:**
> has anyone been able to get sound on an hp dv7t-2000?  i've tried adding the "usual" to sound.conf (options options snd-hda-intel model=...) with several variations of parameters, restarting alsa each time.  thanks!

I have dv7t-2000, this is what I did to get sound *mostly* working (see below).

-Add the following to etc/modprob.d/alsa-base.conf
options snd-hda-intel model=hp-m4 enable=1 index=0
options snd-hda-intel enable_msi=1
-Upgrade ALSA to 1.0.19 per [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

This got the speakers working, and I have tested Rhythmbox, but not much else.  The problem I now have is that sound only comes out of speakers, not headphones.  Plugging in headphones seems to do nothing to speaker output.

If anyone has any thoughts on this system & fixing headphones, it would be greatly appreciated.

---

### Post by burstyouth88 on 2009-04-27
hey, im having the same prob as well.
but mine has goten worse i have null output 
alsa mixex has dissapeared

---

### Post by babusar on 2009-04-27
I had this same problem when upgrading from 8.04 to 8.10 on my laptop and the same thing has happened again when upgrading to 9.04. I've found a work around that has worked for both these upgrades. This is taken from Bug #286610:

you can fix it easily yourself by adding

options snd-hda-intel model=laptop enable=1 index=0

to the file /etc/modprobe.d/options. If you don't know how: Press Alt+F2, type for example

gksu gedit /etc/modprobe.d/options

press enter, write the options line above in it, save, reboot and everything should be fine.

It's worked fine for me on my HP 6735s laptop. Hope it helps.
Michael

---

### Post by davidfdr on 2009-04-27
> **babusar said:**
> 
...

options snd-hda-intel model=laptop enable=1 index=0

...


On my GATEWAY P-6831-FX i´ve tested
options snd-hda-intel model=laptop enable=1 index=0 
and
options snd-hda-intel model=stac92xxenable=1 index=0

both options with options snd-hda-intel enable_msi=1

And is working. But the sound plays with a very low sound playback level.

---

### Post by emanrique on 2009-04-27
I have the same problems, i was googling out and i find this link:

[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)

i install these packages as i read on the link

sudo apt-get install asoundconf-gtk alsa-oss libasound2 libasound2-plugins padevchooser gstreamer0.10-pulseaudio ubuntu-restricted-extras

And then everything was perfect as always, try it....

---

### Post by gfxcoder on 2009-04-28
> **RangerX_308 said:**
> I have dv7t-2000, this is what I did to get sound *mostly* working (see below).

-Add the following to etc/modprob.d/alsa-base.conf
options snd-hda-intel model=hp-m4 enable=1 index=0
options snd-hda-intel enable_msi=1
-Upgrade ALSA to 1.0.19 per [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

This got the speakers working, and I have tested Rhythmbox, but not much else.  The problem I now have is that sound only comes out of speakers, not headphones.  Plugging in headphones seems to do nothing to speaker output.

If anyone has any thoughts on this system & fixing headphones, it would be greatly appreciated.

it works!  i have sound!  thanks!  i believe i've seen something for the headphones somewhere, but i cannot seem to find it.

just as a recap, my dv7t-2000 has sound out of front speakers, but not headphones. i have not tried the mic.  here is my alsa-base.conf
```
options snd-hda-intel model=hp-m4 enable=1 index=0
options snd-hda-intel enable_msi=1
```

now if i can only get the suspend to ram working properly...

---

### Post by teutontom on 2009-04-28
> **bhavikpatel said:**
> Hi All, 


I finally found a workaround for the sound problem. 
Run the alsamixer in the terminal, and see if you have any muted channels in that. If a channel is muted, it shows MM for that channel. 

Select a channel with lef or right arrow keys, and press M to unmute the channel. 

For me, the Master channel is muted every time I restart the PC. 
So I have to unmute it manually every time I boot the PC. 

But I am highly dissatisfied with the updates in 9.04 release. 

For example, I was using Ekiga's paid VoIP service, and it was working perfectly in 8.10. Not Ekiga is updated to 3.2.0 in ubuntu 9.04, and it's one bloody f***ing hell of a quality!!! I virtually have to shout in my headset, and still I can not be heard clearly. They have changed some codecs, and I don't know why they need to change a perfectly working codec, and replace it with some junk codec!!!

I mostly use my PC for watching movies, listening to music, and talking to my family on Ekiga VoIP. So ubuntu 9.04 is a huge disappointment for me!!!

Thank you! I've been all over the forums trying different fixes and workarounds nothing worked. Your simple solution solved the problem.
Gracias danke thank you.:popcorn:

---

### Post by Convert on 2009-04-28
> **g.a. said:**
> I tried what suggested by gkgarg24 but it did not work.

Also, some is suggesting to switch from "alsa" to "oss", I'm not sure of what it means, in attach please find a snapshot from 

g.

For the OSS thing, in the Sound control panel (find this in menu System : Preferences: Sound), you will see on the devices tab your selections are probably autodetect for sound playback (three locations on the tab).  Go to these drop down menus and select "OSS - Open Sound System".  Then you have to restart your computer to ensure the change takes effect.  This will set your sound driver to the OSS driver.

I had a different sound problem with the ALSA driver - the volume was extremely low even with the sound settings turned all the way up.  The OSS driver sound works much better with plenty of volume.

---

### Post by palash on 2009-04-29
Thanks a lot emanrique. I did it and it is working fine for my HP dv6448 laptop. Great job.

Palash

---

### Post by homanhtruong on 2009-04-29
> **HardWaters said:**
> I had the same problem in **Compaq CQ40** intel.. 

it should be** solved** by doing the following:

open the alsa config file by:

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```at the end of the file just paste the following lines:

```
options snd-pcsp index=-2
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1
```

Thanks HardWaters very much. I solved the problem. God Bless for You!!!!!!!!!

---

### Post by RangerX_308 on 2009-04-29
I have the same functionality with OSS as with ALSA.  Sound comes from speakers, but not headphones.

I have found quite by accident that the only sound that comes through the headphones is the system beep.  It also comes through the speakers at the same time.

---

### Post by OchoHa on 2009-04-30
I have this problem too, and tried all of the various model settings with no luck. Finally I've just given up and downgraded my kernel to 2.6.27-8.  I suppose I could spend some more time trying to understand all of the various params, but I'm kind of busy right now.

---

### Post by skotos on 2009-04-30
> **gkgarg24 said:**
> Hey Guys, 

I was also having same problem after upgrade to ubuntu 9.04. I am running it on Dell Inspiron 1420n. I did the following steps after searching through forums. 

1>Run the following commmand[INDENT]sudo gedit /etc/modprobe.d/alsa-base [/INDENT]2>Add the following text to it.[INDENT]options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes[/INDENT]3>Save the file.
4>Rune the following commend :[INDENT] sudo /etc/init.d/alsa-utils restart [/INDENT]5>If this does not work try rebooting machine. Sound should be back again.


Hope this helps!

Regards
I have edited */etc/modprobe.d/alsa-base**.conf*** instead of */etc/modprobe.d/alsa-base* that was not present in the */etc/modprobe.d* directory and just changed these two lines
[php]options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=acer-aspire position_fix=1 enable=yes
[/php]The first line was not present and I have added it from the scratch, the second one was previously set like this[php]options snd-hda-intel model=acer-aspire
[/php]because I am working on an Acer Aspire 9815WKMi.

Thanks to **gkgarg24** and his quick fix _**amarok**_ works like a charm again! Thanks a lot!

---

### Post by jrullan on 2009-05-01
Me too. HP DV3-1075us. Used Wubi install, everything working ok except for sound!

---

### Post by salimanfé on 2009-05-02
same problem after upgrading to 9.04
Amarok, no sound, rhythmbox, yes sound works, it crashes a lot..
with movie player its scratchy sometimes for both video and sound, similarly for flash..
I hv this problem with Pulseaudio: when running the command pulseaudio --check
output: 
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
WHAT DOES IT MEAN? WHAT TO DO? thanks :KS

---

### Post by tdashroy on 2009-05-02
So going to System --> Preferences --> Sound  and changing everything to OSS, my sound works again. But, what is the difference between OSS and ALSA? Isn't OSS worse in quality?

---

### Post by peter_babeone on 2009-05-03
try this:

```
sudo gedit /etc/modprobe.d/alsa-base.conf

options snd-hda-intel model=model=hp-m4
```

then restart your X-server with CTRL-ALT-Backspace.

This works for many people so far ! :)

---

### Post by tdashroy on 2009-05-03
Thanks for the response! Unfortunately, this did not work...is the model in the command supposed to refer to a certain sound card or something? Whenever I log in my sound does not work, and if I go to Applications --> Sound & Video --> PulseAudio Volume Control  and then go to the Output Devices tab, it shows Null Output. Now, if I do

```
killall pulseaudio
```

the Output Devices tab changes to HDA Intel - STAC92xx Analog. Is there any way I can get this tab to always say the latter of the two, other than running this command on start up?

---

### Post by benjoseph on 2009-05-03
I have been trying several things, this worked for me.

Sound In: HDA NVIDIA (hw:Nvidia, 4)
Sound Out: HDA NVIDIDA (hw:Nvidia,0)
Ringing: HDA NVIDIA (hw:Nvidia,0)

Sound Effects- Sound Playback: AUTODETECT

MUSIC MUVIES: Sound Playback AUTODETECT

AUDIO CONFERENCING: 
Sound Playback:   AUTODETECT
Sound Capture: Alsa Advance Linux Sound Architecture

DEFAULT MIXER TRACS
Device: USB Device 0x46d:0x8da (Alsa Mixer)
Microphone

Good luck :-)

---

### Post by tdashroy on 2009-05-03
This actually seems to be working for the time being

```
sudo adduser <username> audio
```

Even though there was no audio group before.

Got the suggestion from here:
[http://ubuntuforums.org/showthread.php?t=1012636&page=2](http://ubuntuforums.org/showthread.php?t=1012636&page=2)

---

### Post by maddix on 2009-05-04
Hello.

I am following this branch because I've got almost same problems like everybody here, but almost is key word for me :).

I have laptop HP DV7 1135nr.
Alsa used module snd-hda-intel
Sound works fine for me, except one thing I have built in microphone which does not works, I've noticed same problems on 8.10 in December (I was trying different versions, before I finally choose 8.4 like most working out the box). But now I am trying utilize all nice features from 9.04 and once I've update to 8.10 and everything works so far, I thought that probably I can successfully update to 9.04 but ... microphone not working so far, and "Volume control" don't remember my changes on "Recording" tabsheet. That seems very strange for me I don't wanna back to 8.04, but it looks like most stable and working system for my laptop :(

Thanks everybody who post different solutions here, I've tried everything from this branch but nothing work for me so far.

---

### Post by ryecomp on 2009-05-04
Same problem here. 

It started when upgraded to ubuntu 8.10. Then, solution was 
1) kill all pulseaudio related process
2) sudo alsa force-reload 
3) set all sound related setting to ALSA
and 1,2 step must be done every booting time.

But this time (upgraded to ubuntu 9.04), previous solution 
did not work. So, after searching 
1) add following lines to end of /etc/modprobe.d/alsa-base.conf
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel enable_msi=1
2) set all sound related setting to ALSA
3) execute volume control/alsamixer/gnome-alsamixer uncheck all the mute. 
4) reboot

This procedure works!!

---

### Post by tdashroy on 2009-05-04
So ummm...what I said worked for me previously, no longer works for me. Any suggestions?

---

### Post by skotos on 2009-05-04
> **skotos said:**
> I have edited */etc/modprobe.d/alsa-base**.conf*** instead of */etc/modprobe.d/alsa-base* that was not present in the */etc/modprobe.d* directory and just changed these two lines
[php]options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=acer-aspire position_fix=1 enable=yes
[/php]The first line was not present and I have added it from the scratch, the second one was previously set like this[php]options snd-hda-intel model=acer-aspire
[/php]because I am working on an Acer Aspire 9815WKMi.

Thanks to **gkgarg24** and his quick fix _**amarok**_ works like a charm again! Thanks a lot!

I want to specify what I have realized since I posted the above message: **the sound system is still broken: _LESS!!_**** than before, _BUT STILL BROKEN_.**

If I run amarok as my first audio app, amarok plays fine: I can move the current track handle forward and backwards and there are no problems (it goes on playing with no hassles from where I have dropped it), but if I run amarok after launching a totem instance, amarok will be muted. 

Thus follows that *amarok has to be run first*, or - simply - that

[LIST=1]
[*]you have to close (or simply stop) all the other audio apps
[*]run amarok
[*]run the previously running audio apps
[/LIST]
but this is not the only problem.
Totem cannot play well after this procedure. after a while, in fact, the audio track played by Totem can be listened well while - at the same time - **the video frames go slowly and suddenly as quick as possible**.
It is not easy to have it playing smoothly again: it is a matter of luck when you stop the current movie, restart it, close and rerun it.

From my point of view, it is not a video plugin issue but still an audio related issue since the audio apps still have some conflict / misconfiguration / quirk that need to be solved or discovered to let me (us) start each audio app in a random order.

---

### Post by g.a. on 2009-05-04
Hi all,

I have the same sound problem in upgrading to 9.04.

I was playing with the config files and make it work. Now I messed everything and the sound is not working anymore. I'm pretty shure that it is related to the

> /etc/modprobe.d/alsa.conf

file. In particular the last lines:

> options snd-pcsp index=-2
options snd slots=snd-hda-intel
options snd-hda-intel model=dell-m4-2
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1

does anyone sees any error in those lines? (dell-m4-2 was the correct parameter for my pc).

thanks in advance.
g.

ps I have booted with the former kernel (2.6.27-11-generic ) and with this configuration file it works. can it be a bug?

---

### Post by chris-at on 2009-05-04
> **mrkeef said:**
> Fixed the problem on my computer! 

Go to System-Preferences-Sound.

Change all the settings from ALSA to OSS. (Run the Test sound first- if it works go through the others and change them all)

I'm using KDE - can anyone tell me how I can do the change there? Multimedia in "System Settings" doesn't offer OSS as an option.

---

### Post by lorebett on 2009-05-04
> **chris-at said:**
> I'm using KDE - can anyone tell me how I can do the change there? Multimedia in "System Settings" doesn't offer OSS as an option.

me too, I didn't find any option in kde.

the sound seems to work fine, but for amarok (e.g., rhythmbox works)

---

### Post by Gleen Globes on 2009-05-04
I had to downgrade my NVidia driver from Jaunty´s recommended version 180 to version 173 to get my audio to work on my Mythbuntu set up. Other´s mileage may vary.

---

### Post by lorebett on 2009-05-04
> **Gleen Globes said:**
> I had to downgrade my NVidia driver from Jaunty´s recommended version 180 to version 173 to get my audio to work on my Mythbuntu set up. Other´s mileage may vary.

you mean nvidia graphic card?
because my sound card is an nvidia...

---

### Post by Anthalion on 2009-05-04
Same **** here.

I run Xubuntu; on live version, everything runs OK, but when I install Xubuntu on my desktop, I cannot make sound.
I cannot even select ALSA drivers, and I tried EVERYTHING concerning them.

Its frustrating.

I also tried EVERYTHING in the sticky topic related to ALSA drivers, however, nothing worked out.

```
david@david-desktop:~$  
david@david-desktop:~$ mkdir src cd src
mkdir: ne mogu napraviti direktorij `src': Datoteka postoji
david@david-desktop:~$       
david@david-desktop:~$ mkdir alsa
david@david-desktop:~$       
david@david-desktop:~$ cd alsa
david@david-desktop:~/alsa$       
david@david-desktop:~/alsa$ sudo apt-get install build-essential linux-headers-$(uname -r)
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.28-11-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
david@david-desktop:~/alsa$ alsamixer
ALSA lib conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default

alsamixer: function snd_ctl_open failed for default: No such file or directory
david@david-desktop:~/alsa$ sudo gedit /etc/modprobe.d/alsa-base 
[sudo] password for david: 
sudo: gedit: command not found
david@david-desktop:~/alsa$ sudo mousepad /etc/modprobe.d/alsa-base 
david@david-desktop:~/alsa$ alsamixer
ALSA lib conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default

alsamixer: function snd_ctl_open failed for default: No such file or directory
david@david-desktop:~/alsa$ 
```

I am switching back to Xubuntu 8.10 till they fix this.

And I dont understand at all why people use Ubuntu or Kubuntu. Xubuntu is FAR FASTER then any other Ubuntu. Xfce ftw.

I even think that I plan to switch myself to Openbox manager, which is even faster then Xfce.
Basically, for me, Xubuntu is like 10x better Ubuntu. Everything is the same; some graphic is different. Thats it.

---

### Post by skotos on 2009-05-04
> **skotos said:**
> ...
From my point of view, it is not a video plugin issue but still an audio related issue since the audio apps still have some conflict / misconfiguration / quirk that need to be solved or discovered to let me (us) start each audio app in a random order.
Ok, now the sound system of my notebook seems to be working fine.
Here it is what I have done: as I have discovered in this post - [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012) - there is a **new PulseAudio!** - version **0.9.15** - at [https://launchpad.net/~themuso/+archive/ppa]("https://launchpad.net/%7Ethemuso/+archive/ppa")

I installed it with all the other updates that come with it and - voilà! - any further sound issue has definitely gone!

HTH. Good luck


FYI Updates are available for Jaunty, Intrepid, Hardy, Gutsy & Feisty

---

### Post by g.a. on 2009-05-06
hi skotos,

does it mean that it might be the case to wait unitl next official update? I spent already a lot of time playing around with the parameters and would not like to waste additional hours in that...

thanks
g.

---

### Post by Buntuyang on 2009-05-08
Try this , it worked for me.
---------------------------------

Ubuntu sound no sound speakers

In 8.04, double click on the volume control, click on Edit/Preferences, then check External amplifier to be visible. The switches tab then appears. Uncheck External amplifier in that tab. Worked for me anyway."
This really worked for me, I just installed ubuntu today and it took me 6 hours to get sound work.

---

### Post by freakrz on 2009-05-08
> **HardWaters said:**
> I had the same problem in **Compaq CQ40** intel.. 

it should be** solved** by doing the following:

open the alsa config file by:

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```at the end of the file just paste the following lines:

```
options snd-pcsp index=-2
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1
```

I have a HP HDX 16t and the above solution worked for me...!

---

### Post by wyth on 2009-05-08
For what it's worth, I had this problem with an HDA Intel card (Realtek ALC888), and went through all kinds of hoops before I got it working.  I posted what I did [in this thread]("http://ubuntuforums.org/showthread.php?t=1153133").

It uses Luke Yelavich's repository with the latest ALSA and PulseAudio

---

### Post by MacroLand on 2009-05-10
i have sound when I switch to OSS however that does not work firefox. Interesting part is after upgrade to 9.04 the sound in my system was working. Then I reboot my laptop and sound is gone. Instead now it is a cracking noise.

---

### Post by skotos on 2009-05-12
> **g.a. said:**
> hi skotos,

does it mean that it might be the case to wait unitl next official update? I spent already a lot of time playing around with the parameters and would not like to waste additional hours in that...

thanks
g.
Sorry for this delay, g.a.
I came here just to look for a way to cancel - with some tags I cannot find! - my comment in which I reported I was successful.
In fact, I definitely was successful after an installation from scratch I have run in the mean time. BTW, not to mess up with amarok 1.4/2.0 I have not installed them and everything works currently fine: no more system unreliability, sound and video issues.

I still lack amarok, but I cannot be involved (I have not so much time) in this gnome-kde-pulseaudio amarok stuff. I thus decided to go on with rythmbox and retry in the future. Unfortunately, amarok is really an awsome app that has no competitor on gnome and its integration should be better evaluated in the event of a release upgrade.

The latest pulseaudio packages available on launchpad are not needed if you give up messing with gnome-kde-amarok and - consequently - pulseaudio issues.
Currently, I would suggest you to uninstall amarok and - like me - wait for a few updates to come.

---

### Post by g.a. on 2009-05-12
thanks for your reply.

I got almost sound working in a not-so-rational way:

[http://kubuntuforums.net/forums/index.php?topic=3103412.msg180302#msg180302](http://kubuntuforums.net/forums/index.php?topic=3103412.msg180302#msg180302)

but the microphone still is not working. I'm currently oversear and really sad, frustrating not being able to skype with my family but only to mimic a video-call...

I'll see what to do.

best,
g.

---

### Post by lorebett on 2009-05-13
have you tried with static-oss? it solved my problem under gnome (you also need to set oss in the sound configuration dialog of gnome), but not under kde actually

---

### Post by cryptoguru on 2009-05-20
I had the same problem with my upgrade.

I fixed it by opening the volume control app and choosing pulseaudio mixer as the device.

It seems that 9.04 has fully moved over to pulseaudio now, whereas 8.10 used a strange combination of alsa and pulseaudio.

If this works on your system, post back here so we know it's not just me :-)

---

### Post by frcsyk on 2009-05-20
Thanks for all the helpful info.  Unfortunately for me I am still having problems.  I've been working at this for about a week now and have had no success at all.  

I've tried all the guides on the forum and I've also tried updating to the latest version of pulse/alsa from Luke's repository.  If I open up Pulseaudio I can see the audio streaming but no sound.  I've tried the disabling the external amplifier but still no luck.  I would really love to hear some thoughts on fixing this issue.  Thanks in advance~

I am using Ubuntu 9.04 on a Thinkpad X41 which uses the ICH6 audio chipset (AC'97)

From aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

From lspci - v 

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
    Subsystem: IBM Device 0581
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at 1c00 [size=256]
    I/O ports at 18c0 [size=64]
    Memory at a0040800 (32-bit, non-prefetchable) [size=512]
    Memory at a0040400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

---

### Post by brianmrowe on 2009-05-26
I have sound, but no mic.  That's better than nothing, but I would not have upgraded if I knew - my killer app is skype.. no skype it messes up my work.. ouch... I've had to use skype on windows....
I did install the pulse audio and check the volume to get sound working, but that did not fix the mic.

---

### Post by Josey on 2009-05-26
For some reason my sound is muted after every reboot in 9.04.  Alsa seems muted by default in 9.04 as this was the case when I ran the update and did a fresh install.

I have to run gnome-volume-control every time now after reboot.  Why does it not save?

Check to see if volume is simply muted...

---

### Post by petersfreeman on 2009-06-01
I have upgraded to Ubunto 9.04 running on my four machines, two desktops and two laptops.  Sound is working fine on three out of the four machines, but not on my Toshiba Satellite A300-02W.  Using aplay -l I get:

[FONT="Courier New"]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/FONT]
and with lspci -v I get:

[FONT="Courier New"]...
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff1e
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d6800000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
...
[/FONT]

I have yet to find a solution to this problem and it is not encouraging based on other posts.

---

### Post by jenkinbr on 2009-06-02
> **gkgarg24 said:**
> Hey Guys, 

I was also having same problem after upgrade to ubuntu 9.04. I am running it on Dell Inspiron 1420n. I did the following steps after searching through forums. 

1>Run the following commmand
 [INDENT]sudo gedit /etc/modprobe.d/alsa-base [/INDENT]
2>Add the following text to it.  
[INDENT]options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes[/INDENT]
3>Save the file.
4>Rune the following commend : 
 [INDENT] sudo /etc/init.d/alsa-utils restart [/INDENT]
5>If this does not work try rebooting machine. Sound should be back again.


Hope this helps!

Regards
No luck.
> **mrkeef said:**
> Fixed the problem on my computer! 

Go to System-Preferences-Sound.

Change all the settings from ALSA to OSS. (Run the Test sound first- if it works go through the others and change them all)
Still nothing...
> **emanrique said:**
> I have the same problems, i was googling out and i find this link:

[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)

i install these packages as i read on the link

sudo apt-get install asoundconf-gtk alsa-oss libasound2 libasound2-plugins padevchooser gstreamer0.10-pulseaudio ubuntu-restricted-extras

And then everything was perfect as always, try it....
nope....
> **cryptoguru said:**
> I had the same problem with my upgrade.

I fixed it by opening the volume control app and choosing pulseaudio mixer as the device.

It seems that 9.04 has fully moved over to pulseaudio now, whereas 8.10 used a strange combination of alsa and pulseaudio.

If this works on your system, post back here so we know it's not just me :-)
still no....



I also get this when I try to play the test sound:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused
```

---

### Post by cmoua on 2009-06-03
What the heck!  Spent hours trying to fix this dumb updated release and why release such updates with bugs or unknown issues.  

I have a Lenovo T43 - system, sound, everything was working great - after the update, some of my apps don't work right, sound, etc.

Is there a way to revert back a few days or does the update overwrites everything?  So frustrating, if all fails, might look to get rid of Ubuntu altogether...


Thanks.

---

### Post by kaoshavoc on 2009-06-03
Ok, I had the same sound issue, I tried 4 different step by step fixes, nothing worked. Now, I am not sure if it was really broke and one of the steps fixed it but I clicked on my little speaker on the upper right, went to "Open Volume Control" and found that the new drivers that had been installed on the upgrade must have muted everything but the master. I just uncklicked all the mutes and it works just fine. I hope this advice helps someone. It just seems too simple of a solution to a problem everyone seems to be having, but sometimes simple things are easy to over look.

---

### Post by jenkinbr on 2009-06-03
Some have found [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) to be helpful.  I haven't (yet), but I think I'm gonna post there as well...

---

### Post by zarthon on 2009-06-04
Jenkinbr what is your 
```
grep pulse /etc/group
```  
?
```
mine looks like this:
audio:x:29:pulse,johndoe
pulse:x:116:root,johndoe
pulse-access:x:117:root,johndoe
pulse-rt:x:118:johndoe,root
```

{{edited}} Jenkinbr I was tired last night and missed that you have an [Inspiron1420]("https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron1420") Others that are having trouble this information would be very useful in suggesting specific solutions to your problem.
 What generally is your audio setup ? For example mine is:
[COLOR="Navy"]Computer: Desktop
Audio Adapter 1:  onboard surround adapter (Intel HD Audio ICH9) on Mother board from Gigabyte
Audio Adapter 2: possible audio on TV tuner card 
Speakers: Altec Lansing VS2421 Stereo speaker system with subwoofer[/COLOR]

You wrote in your other thread:
> I've had no problems like this in 7.04, 7.10, and 8.10; some minor issues in 8.04.
If you boot from an old live CD, does audio still work with older Ubuntu releases?

I had problems with (Intel HDA ICH9) and  solved them all using a guide to fixing problems with pulse by psyke83. Thanks!  

I quit when I solved my problem. I lovee Pulse audio now that I have it up and working !!!! After moving to a new house my problems were back again. I thought something was not permanently saved.
I solved it by installing and using gnome alsa mixer which allowed me to discover that i was plugged into the side surround plug instead of the front channels and the side channels were unmuted but at volume 0. 
Bone headed move on my part :rolleyes: but to my defense the color of my speaker plug looked much like the color of the ring around the side channel audio jack! ugh
My natural inclination is to guess that there are problems with pulseaudio but the only problem with pulse in this regard is that the pulse mixer does not pickup and translate on a low level all the channels of the surround audio to its interface so you must go into the ALSA mixer to change some settings.

---

### Post by zarthon on 2009-06-04
Has anyone tried a USB audio adapter to quickly solve the problem and get decent basic audio? They are selling for $20 on newegg someone got the first one I browsed to work at least with some linux.
[http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16829128002](http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16829128002) 

I thought of this because my telex usb microphone comes right up and with a bit of fiddling with audio sources in pulse volume control I could use it.

---

### Post by darioman on 2009-06-04
Same here,  I think that it's back to a windows machine :(

---

### Post by zarthon on 2009-06-04
> **darioman said:**
> Same here,  I think that it's back to a windows machine :(
What sound card to you have ? Is it a desktop or laptop? is it surround or stereo? What speaker system do you have?


With 1-3 hours effort or $20 you can probably solve this problem and you will save this effort or expense fairly quickly.

With Ubuntu there is not a need to regularly reinstall the operating system, then reboot at least 3 times installing updates upon updates and then piece together all your applications like there is in windows. 
Ubuntu Linux is not just an Operating System with Internet security built in, it is a well tuned software distribution system that integrates thousands of general use and specialized programs for free. Programs in a distribution version are integrated and tested to work together and are all upgraded when you upgraded as a whole when you preform a distribution upgrade.

---

### Post by jenkinbr on 2009-06-05
> **zarthon said:**
> Jenkinbr what is your 
```
grep pulse /etc/group
```  
?
```
mine looks like this:
audio:x:29:pulse,johndoe
pulse:x:116:root,johndoe
pulse-access:x:117:root,johndoe
pulse-rt:x:118:johndoe,root
```


```
jenkinbr@jenkinbr:~$ grep pulse /etc/group
audio:x:29:pulse:jenkinbr:root
pulse:x:118:jenkinbr
pulse-access:x:119:jenkinbr
pulse-rt:x:120:jenkinbr

```
Should I add root as a user in the pulse-rt group
```
sudo adduser root pulse-rt
```

> **zarthon said:**
> {{edited}} Jenkinbr I was tired last night and missed that you have an [Inspiron1420]("https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron1420") Others that are having trouble this information would be very useful in suggesting specific solutions to your problem.
I don't have an inspiron.  Not sure where you found that out at, but my system is a custom-build from a local computer shop. It was actually built about 7 or 8 years ago for a local business.  I got the machine when the business upgraded their hardware.
> **zarthon said:**
>  What generally is your audio setup ? For example mine is:
[COLOR="Navy"]Computer: Desktop
Audio Adapter 1:  onboard surround adapter (Intel HD Audio ICH9) on Mother board from Gigabyte
Audio Adapter 2: possible audio on TV tuner card 
Speakers: Altec Lansing VS2421 Stereo speaker system with subwoofer[/COLOR]

[COLOR="Navy"]Computer: Desktop, Pentium 4 w/ 512 mb Ram
Audio 1: Onboard audio (Intel 82801BA-ICH2) on Intel motherboard
Speakers: Phillips MMS171 (38W stereo speakers w/ sub) (uses standard 3.5mm plug)[/COLOR]

> **zarthon said:**
> If you boot from an old live CD, does audio still work with older Ubuntu releases?

Yes, all of them have sound (even the Jaunty live CD has sound)

> **zarthon said:**
> I had problems with (Intel HDA ICH9) and  solved them all using a guide to fixing problems with pulse by psyke83. Thanks!  
I've been trying out that guide.  The test sound now SAYS it is playing, but the speaker output says otherwise...
> **zarthon said:**
> 
I quit when I solved my problem. I lovee Pulse audio now that I have it up and working !!!! After moving to a new house my problems were back again. I thought something was not permanently saved.
I solved it by installing and using gnome alsa mixer which allowed me to discover that i was plugged into the side surround plug instead of the front channels and the side channels were unmuted but at volume 0. 
Bone headed move on my part :rolleyes: but to my defense the color of my speaker plug looked much like the color of the ring around the side channel audio jack! ugh
My natural inclination is to guess that there are problems with pulseaudio but the only problem with pulse in this regard is that the pulse mixer does not pickup and translate on a low level all the channels of the surround audio to its interface so you must go into the ALSA mixer to change some settings.

My card is relatively old, but it still functions.  I though the card was shot, but then realized that I had audio in windows. (that actually scared the crap out of me because I wasn't expecting it).

---

### Post by RangerX_308 on 2009-06-15
Break out the duct tape....

This "fix" works for my HP DV7-2000 with hda-intel, you mileage may vary.

This gives you headphones and/or speakers. All code below is for setting one OR the other. Check links at bottom for more info and possible speaker/headphone combination variations.


[LIST=1]
[*]   Upgrade ALSA to 1.0.20 per [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)
[*]Reboot. Sound should be working from speakers at this point.
[*]Create a folder in your Home directory with a name like .audiofix
[*]In terminal browse to your new directory
[*]Download & install hda-verb:```
wget -c ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz
tar xvzf hda-verb-0.3.tar.gz
cd hda-verb-0.3
sudo apt-get update
sudo apt-get install build-essential
make

```
[*]Move the file to your .audiofix directory
[*]```
cp hda-verb ~/.audiofix
```
[*]You can now delete the remaining hda-verb-0.3 files & directory if you wish
[*]You now need to "activate" your headphones with the following command. ```
sudo ~/.audiofix/hda-verb /dev/snd/hwC0D0 0x0f SET_CONNECT_SEL 1
``` You should now have sound out of speakers AND headphones.
[*]Now to create your scripts to switch between headphones & speakers.
[*]Using GEdit, create 2 new text files, one called Headphones.sh & one called Speakers.sh.
[*]For Headphones script, enter this code:```
gksudo ~/.audiofix/hda-verb /dev/snd/hwC0D0 0x0f SET_CONNECT_SEL 1
gksudo ~/.audiofix/hda-verb /dev/snd/hwC0D0 0x0f SET_PIN_WIDGET_CONTROL 0x40
gksudo ~/.audiofix/hda-verb /dev/snd/hwC0D0 0x0d SET_PIN_WIDGET_CONTROL 0
``` **Note:**  the first line of this script is a repeat of the Headphone "activiation" code.  This code needsto be run every time you reboot your system, so I put it in here.
[*]For Speakers script, enter this code:```
gksudo ~/.audiofix/hda-verb /dev/snd/hwC0D0 0x0f SET_PIN_WIDGET_CONTROL 0
gksudo ~/.audiofix/hda-verb /dev/snd/hwC0D0 0x0d SET_PIN_WIDGET_CONTROL 0x40
```
[*]Now create some application launchers for your scripts & you are all set.
[/LIST]
Info for this "fix" found here-
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363870](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363870)
[http://ubuntuforums.org/showthread.php?t=984081&page=2](http://ubuntuforums.org/showthread.php?t=984081&page=2)

While this workaround gives me headphones, I still can't figure out how to get the line out on my docking station to work.  If anyone figures that out, please reply to this thread.

Edit-

after upgrading to Kernel 2.6.28-13 (see [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/389538](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/389538) for details) sound breaks.  Rerun step 1 and all should work

---

### Post by thavionhawk on 2009-06-17
I installed Ubuntu 9.04, then I downloaded and installed the ALC850 driver off Asus's site(I have a A8N32 Sli Deluxe board) I installed that and set all the Gnome sound settings to OSS and things work grate. I played some moves with VLC and my sound system showed DTS or Dolby pasthrough output(I use S/PDIF to a JVC 5.1 Reseaver). Now the system shows Dolby all the time on the Reseaver and I am geting no sound outpuite at all from any app. I tested the Reseaver with my PS3 and every thing checked out so somthing has gone wronge with my sound system. any ideas?

---

### Post by Gleen Globes on 2009-06-18
After MUCH Googling I now have audio working via ALSA in my Mythbuntu 9.04. I output all audio via S/PDIF to my Logitech 5.1 system. YMMV on other *buntu!

First I checked alsamixer via Terminal and made sure all volumes were maxed and that outputs were all un-muted using M on keyboard. Some people have said they need to drop levels back to 90% to stop popping sound when audio sent to speakers but doesn´t seem to stop this happening on my system.
```
alsamixer
```Next I added Luke Yelavich´s Launchpad PPA which contains updates for ALSA and Pulse Audio. I let Update Manager install whatever it reckoned it wanted.
[https://launchpad.net/~themuso/+archive/ppa]("https://launchpad.net/%7Ethemuso/+archive/ppa")

Next I found Soundcheck´s ALSA Upgrade script and followed instructions to get latest version of ALSA (1.0.20 from Ubuntu installed 1.018b)
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

Because it was MythTV that I couldn´t get sound out of I then checked settings using MythTV´s wiki entry
[http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto#Set_Myth_up_for_digital_sound](http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto#Set_Myth_up_for_digital_sound)

---

### Post by goog64 on 2009-06-29
> **Buntuyang said:**
> Try this , it worked for me.
---------------------------------

Ubuntu sound no sound speakers

In 8.04, double click on the volume control, click on Edit/Preferences, then check External amplifier to be visible. The switches tab then appears. Uncheck External amplifier in that tab. Worked for me anyway."
This really worked for me, I just installed ubuntu today and it took me 6 hours to get sound work.


I am so happy I could cry. I want to kiss you!!! 30 hours I have poured over all the sound problem posts at this site. (I have about 15 extra lines in my alsa-base.conf file).
I have seen the External Amplifier solution before but I DIDN'T REALISE I HAD TO CHECK IT TO GET THE SWITCHES TAB TO APPEAR. I thought because external amplifier was unchecked that it was OK.
Thankyou for your clear explanation Buntuyang.

---

### Post by jenkinbr on 2009-06-29
> **Buntuyang said:**
> Try this , it worked for me.
---------------------------------

Ubuntu sound no sound speakers

In 8.04, double click on the volume control, click on Edit/Preferences, then check External amplifier to be visible. The switches tab then appears. Uncheck External amplifier in that tab. Worked for me anyway."
This really worked for me, I just installed ubuntu today and it took me 6 hours to get sound work.

*Gives it a try*
*Wonders Why I didn't see this earlier*

> **goog64 said:**
> I am so happy I could cry. I want to kiss you!!! 30 hours I have poured over all the sound problem posts at this site. (I have about 15 extra lines in my alsa-base.conf file).
I have seen the External Amplifier solution before but I DIDN'T REALISE I HAD TO CHECK IT TO GET THE SWITCHES TAB TO APPEAR. I thought because external amplifier was unchecked that it was OK.
Thankyou for your clear explanation Buntuyang.

+1

Hours googleing, half a dozen subscribed threads on the subject, $30 to walmart for a USB sound dongle.

In all, I've probably spent 35-40 hours looking for a solution, eventually settling with a USB dongle that only preformed substandard due to my dependancy on USB devices (WIFI, USB HDD, Thumb drives, Keyboard, Mouse, SD card reader, etc.  Audio and WIFI demanded too much out of the system.

I am SOLVED!!!

*Hunts down other sound threads I've posted in to make known this solution*

---

### Post by Eroll on 2009-07-24
My issue seems to be that I have sound according to the Pulse Volume Meter, yet I hear no sound where I should.  What I mean is that if I plug my speakers into one of the surround channels on my ALC883 then I have sound. The front channel on the card is not pushing any sound out. Any ideas? I've unmuted everything in the alsamixer and have compiled the newest drivers from RealTek and Alsa. As well as reinstalled the pulseaudio system.

---

### Post by JonnyV on 2009-08-05
I gotta say I followed bhavikpatel advice in post #20 and it worked for me.
Thanks,

---

### Post by Rowdy358116 on 2009-08-05
I also have no sound and I have wasted enough time trying to fix it. How do I remove ubuntu from my desktop?
Thankyou

---

### Post by jpt266 on 2009-08-06
I finally got my sound to work. I do not know what I did that actually fixed it. I searched, read, and tried everything that looked plausible. And I too was just ready to give it up. I loaded Win7 then back to Ubuntu 9.04 and I had sound.

Don't ask me what happened. Life is a learning process.

---

### Post by sandwormblues on 2009-08-06
I downgraded to hardy and the sound is still funky!  Sound worked just fine in Gutsy, I recall.  What the heck happened?  Maybe Ubuntu needs to slow down their release schedule.

---

### Post by gragle on 2009-08-27
> **gkgarg24 said:**
> Hey Guys, 

I was also having same problem after upgrade to ubuntu 9.04. I am running it on Dell Inspiron 1420n. I did the following steps after searching through forums. 

1>Run the following commmand
 [INDENT]sudo gedit /etc/modprobe.d/alsa-base [/INDENT]
2>Add the following text to it.  
[INDENT]options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes[/INDENT]
3>Save the file.
4>Rune the following commend : 
 [INDENT] sudo /etc/init.d/alsa-utils restart [/INDENT]
5>If this does not work try rebooting machine. Sound should be back again.


Hope this helps!

Regards

[COLOR="Magenta"]Brillzo! This worked perfectly for me after days of trying to fix this.[/COLOR]

---

### Post by johnnyallstar on 2009-08-30
I didn't upgrade from 8.10, I put a fresh install of 9.04 onto an HP DV-7 2040 with an intel quad 2.0, and I am getting no sound whatsoever, from either internal or headphone jack.  I have tried a dozen different solutions, but still have nothing.

Help : (

---

### Post by RangerX_308 on 2009-08-31
> **johnnyallstar said:**
> I didn't upgrade from 8.10, I put a fresh install of 9.04 onto an HP DV-7 2040 with an intel quad 2.0, and I am getting no sound whatsoever, from either internal or headphone jack.  I have tried a dozen different solutions, but still have nothing.

Help : (

Try following these instructions:

[http://ubuntuforums.org/showpost.php?p=7462566&postcount=83](http://ubuntuforums.org/showpost.php?p=7462566&postcount=83)

I have the DV7-2000.  Should be the same sound card.  I pulled the Vista install of and did a fresh install of 9.04.  Did a lot of digging and this is what works for me.  There is another fix I implemented to be able to switch between Headphones & Speakers, which I will try to post another time.  

Quad core huh?  Nice. :mrgreen:

---

### Post by ambersdarkfox on 2009-09-11
same here i have a dv3-1075us and i got no sound and my grapics card aint working right tho i got ati crap i tryed all the sound fixes even ones tryed in the terminal no go still not working with either 9.04 or mint 7 tryed both and my grapics card is a pain i cant run second life it says i dont meet requirements but i have abot 4 times the requirements i tryed the ati propertary driver for linux and that no work either will ati support ever get better because of this i am stuck dual running windows and linux and i would rather use all linux hell wine covers me for the games i would want to play x3 and it gets better to ^^ and i hope it will run alan wake when it comes out XD if anyone can help me or just want to talk about linux or whatever you can add this sweet fur X3 yes i am a furry =P and if you just want to add me to throw stones because of furry phobia or just genral stupidity because you fail to actualy try to understand anything other then yourself please dont waste my time i am smart enough to know how to block you X3 but if you not and you genral know how to help my problem or just like going on about linux like i do XD *** me to yim [email]ambersdarkfox@yahoo.com[/email] or if you have another messenger email me i have 2 more hehe next time i get a computer i make sure it is more linux freindly XD

---

### Post by mysoccerballz on 2009-10-03
> **Wistful said:**
> I have Realtek ALC889 and had problems with my sound in Ubuntu 9.04 and after applying these steps my sound is back! Thanks!

Steps posted by [COLOR=Red]gkgarg24[/COLOR]
Oh my god, i've been going crazy trying to figure this out, and after following these steps, it works! I can't even explain how happy i was to hear the drums and start up music when i re-booted, i had to make a username just to come on here and thank you for your help.

---

### Post by littleghost76 on 2009-10-18
I tried several things that were posted in this forum... I rebooted and o.O it wouldn't reboot, prolly broke something by mistake heh. I went into recovery mode, and just used the 'repair broken packages' option... rebooted and voila. both ubuntu and my sound were back... not sure how it happened, but I do know i need to say thanks to the people that posted here, sooo thanks!

---

### Post by RangerX_308 on 2009-11-06
Has anyone tried Karmic yet?  do these issues still exist?

---

### Post by waltclay on 2009-11-06
Yes, or it's a new set of issues with similar results. Paraphrasing Mark Twain: ubuntu does not repeat itself, but it does rhyme.

---

### Post by jenkinbr on 2009-11-07
I've found no problems ... yet...

(listening to a youtube vid now...)

---

### Post by RangerX_308 on 2009-11-07
> **jenkinbr said:**
> I've found no problems ... yet...

(listening to a youtube vid now...)

What hardware are you running on?  I'm hoping to solve this speaker/headphone issue without duct tape.

---

### Post by dcoins on 2010-01-19
> **emanrique said:**
> I have the same problems, i was googling out and i find this link:
 
[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)
 
i install these packages as i read on the link
 
sudo apt-get install asoundconf-gtk alsa-oss libasound2 libasound2-plugins padevchooser gstreamer0.10-pulseaudio ubuntu-restricted-extras
 
And then everything was perfect as always, try it....
 
[FONT=Arial][SIZE=2]Thank you! Thank you!, I’ve been searching for days for a fix and yours is the only one that worked![/SIZE][/FONT]
[FONT=Arial][SIZE=2]Thank you again!![/SIZE][/FONT]

---

