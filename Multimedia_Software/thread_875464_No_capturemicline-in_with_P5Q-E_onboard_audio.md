---
title: "No capture/mic/line-in with P5Q-E onboard audio?"
date: 2008-07-30
forum: Multimedia Software
---

### Post by johann_p on 2008-07-30
I am extremely disappointed with the audio support in Ubuntu (or Linux in general?).

I had a lot of trouble to get audio capture/monitoring to work on my old Intel DG965WH board under Gutsy  -- I had to download and compile the alsa drivers myself.

Now I have exchanged the motherboard -- I have now an ASUS P5Q-E and I have done a complete new install of Hardy.

The situation is now worse. No input works with the onboard audio -- not the microphone and not line-in.  Audacity does not record anything, I cannot hear anything. Playing sound files does work though.

alsamixer shows three Views: Playback (with Master and PCM sliders), Capture (with a single slider called "Digital") and All.

If I go to System->Preferences->Sound the testing works for playback, but not for  sound capture. I get the following options for capture:
  HDA Generic
  ALSA
  OSS
  PulseAudio
  Test Sound
  Silence
Even Test Sound does not work correctly though I hear *something* -- with interrupts and in bad quality though. All other options produce silence even though the mic is connected and line-in is connected to a live audio source.

There seems to be no way to make line-in and mic usable??????

:(

---

### Post by johann_p on 2008-07-31
I am totally frustrated and disappointed -- audio did not work fully on three different computers/motherboards I tried, all the problems I got I googled and I found dozens/hundreds of posts of other people having similar problems, but no solutions.

Is there a list of recommended Audio cards that are certified or known to work with Ubuntu? I am willing to shell out extra money just to get rid of these endless problems.

---

### Post by koala454 on 2008-09-01
I have the same problem. The on-board output sound works ok but no mic. I went to use skype and wouldn't work. Did you ever find a solution to this for the P5Q-E on 32bit Hardy?

Thanks

---

### Post by johann_p on 2008-09-02
No solution so far. 
I have given up on this for now :(

---

### Post by genernic on 2008-09-03
This is slightly off topic, but I have got the same motherboard you do, the P5Q-E and I can not seem to get 8.04 to install. Have you done any trics to get it to work?

I have tried both 32 and 64 bit live cds and 32 bit alternative cd but they all freeze during install, at about 51% after diskpartitioning and file copying.

I originally ran Fedora 9, but changed to Ubuntu because my IDE dvd rom did not work under fedora(it does not support the marvell IDE controller I think).

---

### Post by johann_p on 2008-09-03
> **genernic said:**
> This is slightly off topic, but I have got the same motherboard you do, the P5Q-E and I can not seem to get 8.04 to install. Have you done any trics to get it to work?

I have tried both 32 and 64 bit live cds and 32 bit alternative cd but they all freeze during install, at about 51% after diskpartitioning and file copying.

I originally ran Fedora 9, but changed to Ubuntu because my IDE dvd rom did not work under fedora(it does not support the marvell IDE controller I think).
I have had no problem installing Ubuntu 8.04 32 on that system from a live CD.

I have had problems installing a previous version on a different computer from an IDE drive though.
This time, I installed from the SATA CDROM drive as far as I remember.

---

### Post by Farfouille78 on 2008-09-03
Hi,

How I understand you Jonathan !

I've spent 2 days trying to make the microphone working but no way.

I've tried on 2 computers both running updated Hardy :

1st is based on a GA-EP45T-DS3R (The same P45 chipset as you). I've tried with both with the onboard sound card (82801JI/Azalia/ALC882 stuff) and an Audigy SE card. Nothing.

2st is based on an old AsRock Athlon Socket A CM with a Fortissimo II (Cirrus Logic SoundFusion CS4624 chip). Nothing.

When I say nothing, it means that I can hear sound (rythmbox, aplay, even World Of Warcraft is fine), but the mic. doesn't work : no echo, no recording with arecord or the gnome recorder. 

I've also followed dozen of posts. Nothing at all.

I've also checked my mic/headphone with the last Windows XP computer I've got. It is okay.

So my request is simple, if your mic. is working fine, can you post your configuration (Motherboard/Soundcard) and your settings in "System/Preferences/Sounds" and in "Volume Control".

Thank you in advance

---

### Post by johann_p on 2008-09-03
Who is Jonathan?

Farfouille78, no one here has achieved to make the mic work -- i just answered a different question about installing Ubuntu 8.04 on this system.

Personally I am sick and tired of browsing through countless instructions that wont help, reading countless webpages about the same problem but with no solution etc.

When I really need the mic (I am too busy now anyways) I will just go out and buy a cheap soundblaster card and hope that that one works.

---

### Post by Farfouille78 on 2008-09-03
> **johann_p said:**
> Who is Jonathan?

Oups ! :oops:  Sorry for misinterpreting your name (need some rest after spending nights on that problem).

By the way, from my sad experience, a cheap SB card is not a garantee to have the microphone working...

That's why I invite users with working microphone to post their settings.

---

### Post by johann_p on 2008-09-03
> **Farfouille78 said:**
> Oups ! :oops:  Sorry for misinterpreting your name (need some rest after spending nights on that problem).

By the way, from my sad experience, a cheap SB card is not a garantee to have the microphone working...

That's why I invite users with working microphone to post their settings.

OK -- I just wanted to make sure because I thought there must be a misunderstanding :)

In any case, I have been using Linux (mainly Suse and Ubuntu) on half a dozen computers by now and soun has always been a problem.

So I would really love to hear about some not too expensive soundcard that JUST WORKS under Linux/Ubuntu and is easy to find on the market. I simply do not want to spend so much more time on this.

---

### Post by raspewtin on 2008-09-06
Hi there,

Has anyone had any joy with this?

My ASUS P5Q play audio ok under Ubuntu 8.04 - however, only one of the audio outputs works. And none of the audio inputs works. It sounds like the same problem.

I think there must be a generic driver that Ubuntu uses by default that doesn't support very much.

The ASUS P5Q installation CD comes with alsa audio drivers, but the installation instructions are a little intimidating for me. It says you have to recompile the kernel with the new drivers. I'm a bit worried it'll screw up my system.

Can anyone advise on this? Or if anyone has succeeded at this, could they restate the instructions in language that mere mortals can understand? :)

I've attached the instructions from the CD in case anyone is interested.

Thanks

---

### Post by hippolyte on 2008-09-12
First I would run alsamixer and check if the microphone is not muted by default (I've seen that already). This is a console application. So you have to type 'alsamixer' in a terminal. On Ubuntu (where most users don't even enabled a root account), you might have to type 'sudo alsamixer'. In any case, this is not an Ubuntu and even not a Linux issue. This is alsa !

If the onboard soundchip is not or half supported, a cheap PCI sound card should do it. I cannot tell in details since I'm working on a Unix Box right know ... but I usually solve the problem with a $30  C-Media Electronics CMI8738, either on Unix ( which doesn't use alsa at all) or in Linux (alsa with all distros). I don't do a lot with sound but I did already used Skype on Debian with such a soundcard. So it will work on Ubuntu as well.

You should disable onboard sound in the Bios while using a PCI soundcard. Linux doesn't like when it finds two sound devices (Unix doesn't care). 

Let me know if running alsamixer solved the problem. I have to pick up a mainboard for an Ubuntu system, and I won't take a P5Q-E if the soundchip is not fully supported. I'm always prepared to add a soundcard, but I don't do it if I can avoid it. Notice that the soudchip on the P5Q-E is different from the one in most other P5Q based boards ! You should'nt probably had problem with the Realtek ALC1200 on the P5Q Pro.

I have a question too for you guys: How is Compiz doing on your systems ? Does it often freeze/crash X and if not ... what graphic card are you using? Also does anyone have experience with the onboard Intel graphic chipsed on the P5Q-VM ?

cheers,

hippo

---

### Post by markbuntu on 2008-09-13
Is the sound chip on that mobo HDA?
If so, this thread might help to get it set up properly:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

I also use c-media cards, they are very good cards for such a low price and they work out of the box.

---

### Post by Dan Thompson on 2008-10-01
I'm experiencing a similar problem with the onboard Realtek ALC889A sound. I actually get no sound at all.

Fresh install of 64bit hardy. Doesn't even detect soundcard.

Motherboard - GA-EP45T-DS3R

Any leads?

---

### Post by markbuntu on 2008-10-01
If you are looking for a one stop shop to troubleshoot your sound problems, you can look in my 100,000 page guide to sound troubleshooting. 

I have linked in as many sites and threads as I can find that offer real solutions to sound problems. It starts with the very basic basics and if you go all the way through it and read all the links, and the links in the links you will be a Ubuntu (hardy) sound expert (should only take a week or two):

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by johann_p on 2008-10-20
> **hippolyte said:**
> F
Let me know if running alsamixer solved the problem.

No - alsamixer does not even show a slider for the mic - the only "caputure" slider shown is labeled "Digital" is turned up fully and does nothing.
I am aware that this is not the kernel but alsa, but for the end user who simply expects a mundane part of his system to "just work" it does not really matter :)

I find it a bit disappointing that this has not changed by some update either -- the mixer controls and alsamixer still shows the same stripped-down interface that essentially just lets me control output volume and nothing else.
> 
I have a question too for you guys: How is Compiz doing on your systems ? Does it often freeze/crash X and if not ... what graphic card are you using? 
It works just fine - I am using a NVIDIA graphics card on my system. However I usually have compiz turned off because I do not see an advantage and I hate one thing about it: when compiz is enabled, the desktop switcher applet does not show windows in the mini-desktops.

---

### Post by markbuntu on 2008-10-20
> **johann_p said:**
> No - alsamixer does not even show a slider for the mic - the only "caputure" slider shown is labeled "Digital" is turned up fully and does nothing.
I am aware that this is not the kernel but alsa, but for the end user who simply expects a mundane part of his system to "just work" it does not really matter :)

I find it a bit disappointing that this has not changed by some update either -- the mixer controls and alsamixer still shows the same stripped-down interface that essentially just lets me control output volume and nothing else.
...

For some sound chips having the digital on disables the analog. This is especially common when digital inputs are enabled. Try disabling the digital capture and reboot and then see if a mic is available.

---

### Post by johann_p on 2008-10-20
> **markbuntu said:**
> For some sound chips having the digital on disables the analog. This is especially common when digital inputs are enabled. Try disabling the digital capture and reboot and then see if a mic is available.
There seems to be no way to do disable this (what key should I press - M or space does not have any effect) ... setting it to level 0 does not change anything.

---

### Post by markbuntu on 2008-10-20
You might want to get gnome-alsamixer. It is far easier to use and understand that the alsamixer.

---

### Post by johann_p on 2008-10-20
> **markbuntu said:**
> You might want to get gnome-alsamixer. It is far easier to use and understand that the alsamixer.
I tried it -- it has essentially the same interface, if anything, a bit more spartanic even.
There is no obvious way to "disable" digital either. 
I dont think my problem is that i do not understand alsa-mixer -- the problem seems to be that the device is simply supported by alsa only in an extremely basic manner. :(

---

### Post by markbuntu on 2008-10-20
If that is the case, you might want to try ALSA 1.0.18 or 1.0.17 which may have better support:


[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

You also might want to start here to find out what sort of support is actually available for your card from ALSA:


[http://alsa.opensrc.org/index.php/Main_Page](http://alsa.opensrc.org/index.php/Main_Page)

---

### Post by johann_p on 2008-10-21
I have installed the newest ALSA (1.0.18RC3) but that did not help either -- no way to capture anything, microsoft or line-in.

I finally gave up and used an old SB card which does seem to work. Unfortunately I had to remove a different PCI card to make this possible and have now an unusable and unused on-board sound thats good for nothing :(

Rather frustrating, all that.

---

### Post by markbuntu on 2008-10-21
Have you filed a bug report on this at Launchpad or with the alsa devs?
They really need to hear about things like this so they can fix them.

---

### Post by Psyphre on 2009-05-20
Hi, Im considering getting this P5Q-E motherboard, was wondering how all of you have got on since your last posts? You were all using Hardy(i think) and now Jaunty has been released, so hoping alot has improved since.

Hope to hear from you.
Thanks.

---

### Post by stillious on 2009-06-04
> **Psyphre said:**
> Hi, Im considering getting this P5Q-E motherboard, was wondering how all of you have got on since your last posts? You were all using Hardy(i think) and now Jaunty has been released, so hoping alot has improved since.

Hope to hear from you.
Thanks.

I am running a fresh install of Jaunty (x86) and still cannot get anything from my mic input :(

---

### Post by Psyphre on 2009-06-04
ah shame. I bought it in the end and luckily I have a sound card which works great in linux, so im using that for my sound.

---

### Post by xboxmods3077 on 2010-08-01
YES!!!!!, I used alsamixer and fixed my problem!!! 

I have a Biostar TA790GX 128m mobo with the ALC888 Realtek chipset and I am running Lucid 64-bit, for the record.

I could not hear any audio from my line-in source (I play my xbox on a PC monitor and run the Xbox audio to PC's line-in). 

   So I loaded up alsamixer in the terminal and checked it out. I had to stretch the terminal window so it would show ALL of my chipset's channels, but when I found the line input channel, it was muted. I used the arrow key to select the channel and then hit the "M" key and presto!! It unmuted and I heard sound.

Thanks folks. One less reason for me to reboot into Windows 7. :popcorn:

---

