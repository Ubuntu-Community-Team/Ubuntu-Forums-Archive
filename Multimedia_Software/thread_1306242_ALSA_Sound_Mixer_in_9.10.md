---
title: "ALSA Sound Mixer in 9.10"
date: 2009-10-30
forum: Multimedia Software
---

### Post by stz_comp on 2009-10-30
Hi, 

I have a tiny little question about possibility of "downgrading" the new sound mixer in Ubuntu Karmic back the one, which was used in Jaunty. 

Here's the thing. I have 2 monitors, which one of them is an LCD TV switched on only occasionally. With the previous sound mixer, when I have checked "Mute" in the basic controller on the main panel, the wire connected to the TV was not attached. And also its volume was independent on the position of the main regulator. That was handy for me. Now the basic controller mutes all. Is there a way to redefine the regulated channel of this controller, or better replace whole new sound mixer with the older one?

Thanks

Zbynek

---

### Post by bezolaam on 2009-10-30
I also need this option. Old one was much better

---

### Post by TheodoreWard on 2009-11-03
> **stz_comp said:**
> Hi, 

I have a tiny little question about possibility of "downgrading" the new sound mixer in Ubuntu Karmic back the one, which was used in Jaunty. 

Here's the thing. I have 2 monitors, which one of them is an LCD TV switched on only occasionally. With the previous sound mixer, when I have checked "Mute" in the basic controller on the main panel, the wire connected to the TV was not attached. And also its volume was independent on the position of the main regulator. That was handy for me. Now the basic controller mutes all. Is there a way to redefine the regulated channel of this controller, or better replace whole new sound mixer with the older one?

Thanks

Zbynek

You can always start gnome-terminal and enter alsamixer which gives you a non-graphical mixer.

---

### Post by kempi29 on 2009-11-04
I think the old one was better. I can't set LFE in new mixer on my Soundblaster Audigy. 
](*,)

---

### Post by michy99 on 2009-11-04
Install gnome-alsamixer and it will be under Applications->Sound & Video.

---

### Post by dragonny on 2009-11-05
Really it would be great if somehow is possible to downgrade sound mixer in Karmic. Old one was much much better, and GNOME Alsa Mixer doesn't work good enough for me (keyboard shortcuts and panel icon).

---

### Post by abry on 2009-11-07
Agree, old mixer was much better. I have installed gnome-alsamixer and I can adjust sound there, but adjusting thingy at gnome-panel decreases sound at my m-audio revolution 5.1 but increases it just partially - so pcm stays at 20 percent and other channels get to full volume. Sometimes (when i move the adjusting thingy at gnome panel realy fast) it work how it is expected.

I am really regretting that I upgraded my computers to 9.10 (My another computer is MSI wind which is very problematic on karmic and yeah I didn read hidden warning at this pages before i did upgrade). I am with ubuntu for few years now ... maybe the time has come to look for other linux distribution.

Back to the topic ... why was working mixer replaced by new useless one? And is it possible to downgrade or get other mixer? (or at least working applet to gnome panel to adjust sound?)

---

### Post by Truckerpunk on 2009-11-07
This is not a solution. But I would like to launch my firefox with alsa. In 9.04 it was as simple as "aoss firefox" but in Karmic this doesn't work. The system monitor says that a firefox is indeed running, but nothing happens. The reason is that pulseaudio, won't let me have an java-app open and share the sound with any other application. Alsa allowed that. Are you guys able to launch firefox with the alsa-wrapper? ("aoss firefox"). Or able to have multiple audioplayback using another soundapp.?

---

### Post by armitage374 on 2009-11-19
THANK YOU!
Was getting seriously torqued about not getting any sound on my system after updating to Karmic Koala. Installed Gnome Alsa-mixer as last resort and managed to get my sound up and running after discovering that a channel I THOUGHT I unmuted on the systemsettings were still muted. 

In case anyone is wondering, I'm on an Nvidia/ASUS MB system with HDMI.

---

### Post by Russel_Winder on 2009-12-05
Sound control is clearly, well, crap (apologies for the strong language but strong language seems appropriate) in Karmic compared to Jaunty.  Whoever is responsible for the Ubuntu sound configuration is obviously making fascist decisions about what they think we want based on zero knowledge and are seemingly unlikely to be taking feedback.  This sort of situation really makes me contemplate ditching Ubuntu and going back to Debian.

What is really, really annoying is that rants like this may serve a cathartic purpose for the writer (in this case me :-) ) but they achieve absolutely nothing  since I doubt the people in charge of the Ubuntu configuration are involved in these fora.  Only by lobbying the actual people involved is it possible for anything to be done.

Clearly the Gnome ALSA mixer needs some work -- I get single volume and slider balance -- which I don't want and the button to select to separate sliders does nothing.

Does anyone know what the package for the sound control/mixer was in Jaunty -- another alternative is to forward port the package to Karmic and install it in replacement of the current totally useless and crap excuse for a sound control that has been foisted on an unsuspecting Ubuntu world.

Presumably it is all in the aim of dumbing down the system for whatever devious reason there might be.

---

### Post by ubtpenguin on 2009-12-05
Hey people I am from year 2012. 

I am here to witness that the great PulseAudio system completely obliterated Linux world as mayans predicted

---

### Post by phaedr_os on 2009-12-08
Yup the new default ubuntu gnome mixer really sucks
Installing the gnome alsa mixer does not really solve the problem since its settings are not remembered ie gone after restart

Fortunately the mixer in kbuntu, which i have now installed instead is still perfectly competant (xubuntu is ok too)

Audio is a very important part of the modern PC and any distro which can't handle it properly is hardly worth installing!

---

### Post by VertexPusher on 2009-12-08
> **Russel_Winder said:**
> Whoever is responsible for the Ubuntu sound configuration is obviously making fascist decisions about what they think we want based on zero knowledge and are seemingly unlikely to be taking feedback.
I agree 100%.

The reason why gnome-alsamixer has not seen an update since 2006 is because it was made redundant by Gnome's default mixer -- which is now gone and replaced by one that is crippled to the point that it won't even start up when PulseAudio isn't running. And of course the new mixer is unable to control ALSA volumes.

Someone at Canonical is asleep behind the wheel.

---

### Post by Yellow Pasque on 2009-12-08
You can grab the gnome-media and gnome-applets packages from here: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)
I reconfigured them to use the old gstreamer-based mixer. Don't install anything else (like gnome-settings-daemon or canberra stuff) from my PPA if you're still using PulseAudio though.

---

### Post by phaedr_os on 2009-12-08
>Install gnome-alsamixer and it will be under Applications->Sound & Video

u shouldn't have too, and anyway it doesn't remember the changes u make

>Sound control is clearly, well, crap

Clearly and well put. Why cripple their flagship distro in this way?

---

### Post by VertexPusher on 2009-12-09
> **phaedr_os said:**
> >Install gnome-alsamixer and it will be under Applications->Sound & Video

u shouldn't have too, and anyway it doesn't remember the changes u make
It does, but PulseAudio overwrites them.

If you look into /usr/share/pulseaudio/alsa-mixer, you'll find a lot of configuration files. Based on the content of these files, PulseAudio guesses the ideal default ALSA volume settings. No matter how you set ALSA volumes, on startup PulseAudio will reset them. In my case the master volume control will be muted, and the headphones jack will be switched off.

There is no configuration option to stop PulseAudio from doing so. I've looked for bug reports and found several describing the problem, but none of the developers seems to care.

Usually I run my system with a pure ALSA setup, but every once in a while I reinstall PulseAudio to remind myself how crappy it is. Then I remove it again. PulseAudio didn't work two years ago, it still doesn't work today, and it probably never will because its one-size-fits-all approach is fundamentally wrong.

> >Sound control is clearly, well, crap

Clearly and well put. Why cripple their flagship distro in this way?
They want Ubuntu to become the new Windows.

---

### Post by Yellow Pasque on 2009-12-09
VertexPusher, did you try my suggestion or are you just whining for the sake of whining? If you don't want to use the packages I reconfigured, at least install xfce4-mixer.

---

### Post by phaedr_os on 2009-12-09
>at least install xfce4-mixer

same as installing gnome alsa mixer - settings u give it are forgotten

---

### Post by markbuntu on 2009-12-11
If you would like the devs to make changes or if something does not seem to be working correctly then it is extremely important to file bug reports if you would care to have something done about it. 

The devs do not hang about in the forums but they do look at bug reports. The more people that file bug reports the sooner somthing will get to the top of the heap of things that need to be addressed.

For sure the gnome devs are reworking the new volume control. The one in Karmic is a sort of first look for the next gnome and they are wanting feedback about what else it should do, etc.

Of course if you just want to rant and rave that is all well and good but doesn't really help a whole lot with advancing the project.

---

### Post by Robbyx on 2009-12-12
I read elsewhere on the site that 

sudo alsactl store 0

Will save the alsamixer settings. 0 is the card number.

---

### Post by 5nak3 on 2009-12-13
Ok I'm also having this problem which I've looked away from for so long because the alsamixer command in terminal was good enough.

But each time I restart the settings are with headphone jack being set to 100% volume which as you can imagine is a huge problem if I forget to set the volume correctly before launching any audio through my headphones.

In any case I've not tried any solutions in this thread. I will give xfce4-mixer a go see how things go and see Temüjin's PPA.

But if anyone has a proper way to downgrade the system I'm very interested.


----EDIT----

Ok I just gave Temüjin's PPA a test and install gnome-media and gnome-applets via the 
"sudo apt-get install gnome-media gnome-applets" command in terminal. To an extent it works, I have better control of my devices more similar to Jaunty without the need of opening up Alsamixer in terminal.

While I'm not convinced that the system is a 100% replica of Jaunty's system, it works much better than the previous setup. I have lost control of individual application volume as was the norm in Karmic however that doesn't bother me as almost all programs I use that do with audio have their own in built controllers.


----EDIT 2----

Ok I just reset the computer and when I logged on my volume control applet was gone. I clicked on add applet, chose volume control, and out of curiosity right clicked the icon. I found a preference menu and I found I can me my volume keys control a specific channel (I chose the Master channel).

The volume for the headphones seems to have remained where I left it last. And now when I change volume instead of the silly notification in the top right corner I get a nice big square in the bottom half of my screen a la Jaunty!!!

Can't be happier :) Thanks a lot for the tip and indeed the ppa Temüjin!

---

### Post by Yellow Pasque on 2009-12-14
> Thanks a lot for the tip and indeed the ppa Temüjin!
You're welcome.

> per-application volume control...
That's actually one of the good things about PulseAudio, but as noted, most apps offer some form of volume control.

EDIT: One other note about running without PulseAudio - you'll want to right-click on the the GNOME menu(s) and select 'Edit Menu'. Under the System -> Preferences list, check 'Multimedia Systems Selector' (and you can uncheck the old Pulse-based 'Sound' option if you wish). This will allow you to control gstreamer apps.

---

### Post by repilce on 2009-12-14
Hello, New to Ubuntu here and novice-light moderate linux experience, i was having microphone issues to. using ubuntu 9.1 x64

I have a Sound Blaster Audigy ZS 2 card

I installed the media applets package from your links for AMD64 and had the new applet once installed, with the different controls and properties, but for some reason the same output on my card that was working before was not, so i rebooted, to find my applet gone, and WITHOUT an entry for volume control under the "add to panel" feature/menu.

Any suggestions?

---

### Post by Yellow Pasque on 2009-12-14
Did you uninstall PulseAudio?

And did you get the media-common and applets-data .debs as well?

---

### Post by travmon69 on 2009-12-15
Install  qamix  it   works   great  for me  ```
sudo apt-get install  qamix
```

---

### Post by phaedr_os on 2009-12-16
I think there are some good suggestions for including a decent mixer which is missing from the default install - xfce4-mixer is nice. And guidance  on how to switch away from pulse audio. But the other half of the problem is, that if u manage to adjust the various components of u'r sound system as u would like, the settings will be gone when the computer is switched off. This annoyance, ufortunately, remains.

---

### Post by Yellow Pasque on 2009-12-16
> **phaedr_os said:**
> I think there are some good suggestions for including a decent mixer which is missing from the default install - xfce4-mixer is nice. And guidance  on how to switch away from pulse audio. But the other half of the problem is, that if u manage to adjust the various components of u'r sound system as u would like, the settings will be gone when the computer is switched off. This annoyance, ufortunately, remains.
You experience this with packages from my PPA, or you can't figure out how to use it?

---

### Post by mgvbstar on 2009-12-18
Thanks Temüjin, your packages worked for me. I have a VT1708S and pulse on karmic was not working.

Is it possible to get my keyboard shortcuts for volume up/down/mute to work with alsa? They are set in the Keyboard Shortcuts tool but I assume that it is still trying to send my hotkey presses to pulse which is no longer installed.

---

### Post by Yellow Pasque on 2009-12-18
mgv: did you install the gnome-settings-daemon packages as well?

---

### Post by mgvbstar on 2009-12-18
no i had not, that fixed it for me. thanks again.

the only issue i have now is that muting via the keyboard shortcuts doesn't work. the keyboard shortcuts seem to control a channel called 'Front' and muting this channel doesn't turn off sound. can i change them to control a different channel? this is not really a big deal - i can live with it versus the dysfunctional pulse. i just wanted to report it for completeness.

thanks again! had your packages not gotten sound working properly for me i probably would've had to downgrade to 8.04

---

### Post by Yellow Pasque on 2009-12-19
You can either run:
```
gconf-editor
```
and look under /desktop/gnome/sound/
or, you can install the "classic" sound properties program: [http://launchpadlibrarian.net/33491183/soundproperties.tar.gz](http://launchpadlibrarian.net/33491183/soundproperties.tar.gz)

---

### Post by ancientrustic on 2009-12-26
I cannot mute my speakers when using headphones. I could do this in Jaunty, there were so many more options. Why take choice away? Is there a solution?

---

### Post by Yellow Pasque on 2009-12-26
> **ancientrustic said:**
> I cannot mute my speakers when using headphones. I could do this in Jaunty, there were so many more options. Why take choice away? Is there a solution?
Can you do it in alsamixer?

---

### Post by phaedr_os on 2010-03-20
So will there be a proper sound mixer in 10.04 or will the issue be ignored in favor of more gimmicks?

---

### Post by breadlord on 2010-03-31
If you've got the KDE libs installed I suggest installing kmix. It's the ugly, but functional equivalent of the old (per channel) gnome mixer.

---

### Post by jd4x4 on 2010-05-03
> **VertexPusher said:**
> 
...snip...
Usually I run my system with a pure ALSA setup, but every once in a while I reinstall PulseAudio to remind myself how crappy it is. Then I remove it again. PulseAudio didn't work two years ago, it still doesn't work today, and it probably never will because its one-size-fits-all approach is fundamentally wrong.

They want Ubuntu to become the new Windows.

This strikes me as pretty funny since my audio card & mixer work 1000% better in WinXP. 

Granted, I'm a reasonably new user but I've been trying to abandon M$ for about 3 years now and flipping between OS's & distros so I can't say I've tweaked Ubuntu as much as I have XP. I'm in the midst of archiving a bunch of reel to reel tapes, and because of the lack of ease in configuring my card inputs & outputs and the cheezy mixer control I'm either going back to XP for the project or maybe upgrade/downgrade to 64bit UbuntuStudio Karmic from my current i86 Ubuntu Lucid.

I just jumped from Jaunty to Lucid and I'm sorry I did because of the audio. After the Lucid upgrade I had to manually install my card (Gigabit on-board ALC883 not recognized) and after using the default mixer, I installed Temüjin's PPA (thanks!) and it helped a lot but the mixer still leaves a lot to be desired with my card.

---

