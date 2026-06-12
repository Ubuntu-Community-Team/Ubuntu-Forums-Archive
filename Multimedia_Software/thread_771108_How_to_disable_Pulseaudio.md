---
title: "How to disable Pulseaudio?"
date: 2008-04-27
forum: Multimedia Software
---

### Post by picpak on 2008-04-27
Is there a way to remove Pulseaudio without uninstalling ubuntu-desktop? Audacity doesn't work with it, and I'd like to revert to ALSA. Thanks!

---

### Post by scragar on 2008-04-27
in 8.10 pusleausio unfortnatly)and atleast until it's fixed) is the only way to get sound working at all. once the bug related to this has been fixed I'm sure it will be disabled automaticaly with the update.

---

### Post by picpak on 2008-04-27
You mean 8.10 has already been started? I had no idea.

---

### Post by scragar on 2008-04-27
sorry, I meant 8.04 (I was talking to someone as I wrote that message, sorry).

sudenote: yeah, 8.10 development is underway, 8.10 meetings were planned before they finished adding finishing touches to hardy.

---

### Post by picpak on 2008-04-27
Soooo...does this mean we're left out in the dust? Seriously, what was the reasoning behind this?

Developer 1: "Wow, this Pulse Audio thing works great!"
Developer 2: "Yeah, but...Audacity is broken."
Developer 1: "So?"
Developer 2: "It's a SOUND EDITOR."
Developer 1: "Yeah....well...."

C'mon, I bet a lot of people use Audacity. I was actually trying to get someone to switch to Ubuntu and get accustomed to Audacity, but obviously that's not gonna happen. I don't understand why every 2 years or so there needs to be a drastic change to the sound system and the programs can't keep up. Why, just last week I was able to record from Firefox with Audacity. And I could play more than one sound at once. I could do basically whatever I wanted, and ALSA was maturing to become quite the useful sound system. Now this Pulse kid comes in town and reverses everything. It's so frustrating...

[/end rant]

---

### Post by scragar on 2008-04-27
I know what you mean, but it is filed as a bug(although I cannot find the report when I search I know it was there, too many unrealted results :P), so it will get fixed. if you absolutly require alsa then I'd recomend downgrading, if not then it may be wise to wait.

And pulse can play sound from more than 1 thing at once, just not more than one thing from the same program(EG totem, VLC and flash will work fine side by side, but another copy of totem or VLC will be silent)

---

### Post by loell on 2008-04-28
I thought I was the only one having problems with audacity, now i don't feel so worried :p

---

### Post by picpak on 2008-04-28
Well guys, getting it to work is actually really easy. You don't need to mess with PulseAudio or anything like that. Just uninstall jackd.

```
sudo apt-get remove jackd
```

...And you're done. Open up Audacity and all should work again. If not, try killing jackd and trying again.

```
killall jackd
```

Credit goes to [http://ubuntuforums.org/showpost.php?p=4812244&postcount=5](http://ubuntuforums.org/showpost.php?p=4812244&postcount=5) . Cheers!

---

### Post by Shachiel on 2008-04-28
I tried to remove jackd but I don't even have it installed. I tried the perfectsetup at pulseaudio's wiki, but everything is messy and whenever I open two apps that use pulseaudio they both crash, any ideas?

---

### Post by eye208 on 2008-04-29
> **scragar said:**
> And pulse can play sound from more than 1 thing at once
So can ALSA. It has been doing so for years.

Let's face it: Sound was fine in Ubuntu 7.10, and now PulseAudio has messed up everything. The prospect of having things working again in a few months is not exactly an incentive to upgrade. Pushing beta software into a LTS release is beyond stupid because everyone in the IT world will examine this release and conclude that Linux is not yet ready for the desktop.

---

### Post by peacewithall on 2008-04-29
I feel everyones frustration here, pulseaudio for me has been nothing but a failure, ok it works with a music and video player that comes with the initial ubuntu installation, but thats about it, can anyone honestly say 'pulseaudio' has solved sound problems for us?. As far as I see it, speaking as an 'average user', so far pulseaudio has given me crackly popping sound in some apps, an echo when it works well in some apps, or most of the time just plain don't work. The apps in question are littered all over the forums so, I won't go repeating.

I know it seems like a complaint, but seriously I want the choice to install esound again, why has our freedom to have ubuntu as we want it been taken away?, I know most will say Hardy Heron, is so heavily integrated with 'pulseaudio' its impossible to have that request. But surely these problems were encountered during testing?.

---

### Post by scragar on 2008-04-29
I was not defending the bug, but simply trying to explain facts. Someone above me said that pulse could not play more than 1 thing at once.

---

### Post by scragar on 2008-04-29
> **peacewithall said:**
> I feel everyones frustration here, pulseaudio for me has been nothing but a failure, ok it works with a music and video player that comes with the initial ubuntu installation, but thats about it, can anyone honestly say 'pulseaudio' has solved sound problems for us?. As far as I see it, speaking as an 'average user', so far pulseaudio has given me crackly popping sound in some apps, an echo when it works well in some apps, or most of the time just plain don't work. The apps in question are littered all over the forums so, I won't go repeating.

I know it seems like a complaint, but seriously I want the choice to install esound again, why has our freedom to have ubuntu as we want it been taken away?, I know most will say Hardy Heron, is so heavily integrated with 'pulseaudio' its impossible to have that request. But surely these problems were encountered during testing?.

I actualy think pusle was used as a temporary fix to the more serious problem of alsa not working, to point out flaws in pulse as a result is completely missing the point, pulse is a fix that is intended only to last until the alsa problem can be fixed.

---

### Post by eye208 on 2008-04-29
> **peacewithall said:**
> But surely these problems were encountered during testing?
Yes they were. See [this thread](http://ubuntuforums.org/showthread.php?t=754125).

I'm sure there is a way to disable or bypass PulseAudio, at least for applications that would otherwise use ALSA. At the core of the sound system there is still ALSA but it's configured to use the PulseAudio plugin for its default PCMs now. This should be reversible by changing the /etc/asound.conf file. Ubuntu 7.10 did not define this file at all, so ALSA's default settings were used which happened to work just fine.

---

### Post by peacewithall on 2008-04-29
> **eye208 said:**
> Yes they were. See [this thread](http://ubuntuforums.org/showthread.php?t=754125).

I'm sure there is a way to disable or bypass PulseAudio, at least for applications that would otherwise use ALSA. At the core of the sound system there is still ALSA but it's configured to use the PulseAudio plugin for its default PCMs now. This should be reversible by changing the /etc/asound.conf file. Ubuntu 7.10 did not define this file at all, so ALSA's default settings were used which happened to work just fine.

WOW !, well those opinions beat my pathetic rant, :). *whispers* And yes I agree with your post, I won't say which one specifically:).

---

### Post by XMAG on 2008-04-29
This pulse audio thing is filling my RAM and making the whole system slower when I'm listening to music. Whenever I do something (anything) while rythmbox is playing the sound will skip a couple of times. I uninstalled pulseaudio and the whole thing got fixed, but then I lost ubuntu-dekstop too...

The main question here is IS THERE A WAY OF REMOVING PULSEAUDIO (without remocing ubuntu-desktop package)?

---

### Post by Fred_E _krugar on 2008-04-30
An easy way to disable PulseAudio is to go into the system monitor and turn off PulseAudio Server. Alsa will then take over. You will have to turn it off each time you boot unless some one knows how to make a script to turn it off during boot. If so please post the script or IM me with it. 

I did this so I could play CSS and talk on Ventrilo and to also listen to music at the same time.

---

### Post by Melcar on 2008-04-30
Pulseaudio actually has been a boon for my system.  Gutsy would always revert to using the ATI sound passtrough chip on my HD2900XT even when I did all the necessary manual changes; this has not happened yet under Hardy.  All my apps. work fine (Audacity included), except for Mplayer under Kubuntu (I can't use the Pulseadio plugin).

---

### Post by brodae on 2008-04-30
Yeah, honestly, my PulseAudio experience has been wonderful. In all fairness, I haven't used Audacity yet... However, it made my system sounds, and Flash audio work. Both of which weren't working in my 7.10. Can't you just disable it by going to System -> Preferences -> Sound, and switching to something other then "PulseAudio Sound Server"? Or, does that not work? Or, does that only work temporarily? I don't know the answer to those questions. However, so far, I love PulseAudio.

---

### Post by Melcar on 2008-04-30
A problem with Pulseaudio that does annoy me, is that I can't get it to work with my custom kernels.  If I build a kernel against Hardy, no ALSA drivers are compiled, so I have to make sure I load them, but even then, my sound does not work. However, this is an "extracurricular activity" and in no way damaging to Hardy itself (it still drives me crazy thought).

---

### Post by atomicblue on 2008-05-04
This is only my opinion, mind you, but I question the decision to switch the sound system over to Pulseaudio for a LTS version.  I ask whether it would have been a better choice to tighten down the code from Gutsy and squish the bugs out of existence when switching everything over to a new anything usually brings up issues while everything is ironed out.  

Any thoughts / comments?   Or -- am I looking at this the wrong way?

---

### Post by MightyMag on 2008-05-04
> **Fred_E _krugar said:**
> An easy way to disable PulseAudio is to go into the system monitor and turn off PulseAudio Server. Alsa will then take over. You will have to turn it off each time you boot unless some one knows how to make a script to turn it off during boot. If so please post the script or IM me with it. 

I did this so I could play CSS and talk on Ventrilo and to also listen to music at the same time.

Yep, this worked for me. 
The only thing that worked previously was Audacious. Mplayer didn't work at all, VLC hade no sound. After I killed the Pulseaudio server everything worked like a charm. One might wonder why Pulseaudio is in 8.04 at all.

---

### Post by Artemis3 on 2008-05-07
I can not record anything from any source with any program. Audacity/arecord/jokosher/sound recorder either crash, freeze or do nothing.

The hardware is fine, i can listen to myself... correct mixer settings with proper capture chosen etc.

I guess ill uninstall pulseaudio to test, losing ubuntu-desktop is not the end of the world... Oh yes, vlc loses sync with audio when using pulseaudio; and what pulseaudio is supposed to do, say, an oss app and another alsa app playing sounds together doesn't work.

Teamspeak still takes over the sound card from wine, and everyone else's for that matter...

Ah well just did it and guess what? I can record again!... Hmm but just for some seconds, then it suddendly freezes and its like the device is not sending anything anymore... I suppose i need to properly remove pulseaudio or something.

---

### Post by nickko on 2008-05-07
> **Fred_E _krugar said:**
> An easy way to disable PulseAudio is to go into the system monitor and turn off PulseAudio Server. Alsa will then take over. You will have to turn it off each time you boot unless some one knows how to make a script to turn it off during boot. If so please post the script or IM me with it. 

I did this so I could play CSS and talk on Ventrilo and to also listen to music at the same time.
In order to automatically disable pulseaudio on startup, if you're under gnome, just go to System>Preferences>Sessions    and add a new startup command in the startup programs tab.   The command is simply "killall pulseaudio".

It worked perfectly for me, ALSA becoming the default sound application again.

---

### Post by notbitmonk on 2008-05-07
I recently upgraded to Hardy and had trouble with sound.  I have a Soundblaster Audigy ZS card and a 5.1 surround system that worked ok with 7.04 and 7.10.  With Hardy, the front and center speakers were ok but the rear speakers didn't have any sound.  By killing PulseAudio I can finally have sound again (Rythmbox, MPlayer, Totem) like I used to in 7.10.

---

### Post by strem on 2008-05-20
I do not like pulseaudio. It consumes RAM and making my desktop running slow, so I've completely removed 'pulseaudio' package and 'ubuntu-desktop' too.

The 'ubuntu-desktop' it's just a meta package it can be safely removed (it will appear again after next distributive upgrade)

---

### Post by omer_akhter on 2008-06-22
An easy way to disable PulseAudio here [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

### Post by gravometric on 2008-10-24
...and adding to the complaint list:  
Trying out 8.10.
When I've got my M-Audio Keystation plugged in and trying to play piano using Qsynth, the MIDI events keep getting delayed making random (but constant) latency.  Although a neat effect, I need to hear the notes as I'm playing them.  I can now "tune" Qjackctl all the way down to 64 Frames/Sec with 96000 sample rate without xruns (which is supposed to be only a 1.33 ms latency), but the notes do not register in Qsynth until almost a second late in some cases (chords played in rapid succession).  The same thing happens using Virtual Keyboard to a lesser extent (no virtual sustain pedal).

MIDI tracks already Composed in Rosegarden play correctly in time. I need to compose on my keyboard though (actually *playing* the piano), not through the notation editor in Rosegarden (point and click composition).

Pulseaudio seems to be one more wrapper for audio that's already running through enough wrappers as it is (HAL to Alsa to Pulse to Jack).

grav

---

### Post by markbuntu on 2008-10-24
Jack will not start if pulseaudio has grabbed the hardware so I doubt that pulse is causing your problem.

You seem to be misinformed about how jack works. Jack bypasses all sound servers and addresses the low level kernel drivers directly. When you use jack the connection is application-jack-drivers. 

Non-jack applications need to go through a sound server so their connection is application-sound server-alsa drivers. Alsa has drivers and a sound server layer. When you are using the alsa sound server the connection is application-alsa sound server-alsa drivers. Depending on how you have screwed around with your asoundconf file it can be as long as application-esd-alsa sound server-dmix-alsa drivers.

With pulseaudio it is application-pulseaudio-alsa drivers. Pulseaudio replaces the alsa sound server layer and esd and dmix and addresses the alsa drivers directly. 

Pulseaudio has been adopted by many distributions due to the ad-hoc nature of the alsa sound server and the increasingly messy and confusing manner in which it has grown along with the daunting prospect of simplifying current functionality while meeting demands for new functions. It is the same reasoning that led to alsa replacing oss. It is another transitional phase and we are the lucky people pushed to the bleeding edge.

Anyway, the problem you are having is most likely a priority issue with the kernel or a bug in the usb drivers.

You can try editing /etc/security/limits.conf and add or modify these lines

```

audio - memlock unlimited
audio - nice -10
audio - rtprio 99

```

This should get the kernel to give your audio stuff top priority.

---

### Post by Psy[H[] on 2008-11-04
Is there a way to disable pulseaudio _without removing it_?
I did 
```
sudo update-rc.d -f pulseaudio remove
``` to remove it from starting on boot.
Audio settings are switched to ALSA
I disabled pulseaudio in sessions. 
I removed pulseaudio-module-x11 package which contained /etc/xdg script
I even removed non-executable /etc/X11/Xsession.d/70pulseaudio


But still every time X starts I have pulseaudio process running! Damn! where is this autostart hidden???

---

### Post by markbuntu on 2008-11-04
If you have Enable software sound mixing (ESD) checked in System/Preferences/Sound/Sounds, pulseaudio will start since it has replaced ESD.

---

### Post by [censored] on 2008-12-11
For those of us who hate the fact that pulse-audio is automatically running by login, and would rather it weren't, I have found a solution on the web ......

[http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/#comment-35](http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/#comment-35)

Thanks to the blogger for providing it. My system is now nice and quick at bootup, and pulseaudio free (unless I choose to start it up myself!).

Can I say that I think it's really very lame of ubuntu to make it so hard for us to disable this feature.

---

