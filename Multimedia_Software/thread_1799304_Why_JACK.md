---
title: "Why JACK??"
date: 2011-07-07
forum: Multimedia Software
---

### Post by akhil2091 on 2011-07-07
Okay so here is my problem: Jack is working fine. This one program that I installed JACK for is also working fine. But I'm not getting sound from anything else (banshee etc).

I'd never heard of JACK until recently and although I've read a lot of threads on this forum and elsewhere I can't get any proper answer to this particular problem. I keep coming across terms like PulseAudio and alsa and I'm not really sure what they are or whether i need to install them 'cause i couldn't find any definitive answer anywhere. 

Also, what exactly does jack do apart from "handle low latency" audio? I read somewhere that it can route other audio through it but the problem is theres a lot of technical stuff that just goes over my head. 

I'd really appreciate if someone can explain it in simple terms. Thanks.

---

### Post by undeuxtrois on 2011-07-07
Hi there, 

JACK is a system that is mostly useful for having multiple programmes share the sound card and routing audio from one to another with very little noticeable audio delay (low latency).

PulseAudio is another system just like that, but I think that it's designed more for day to day stuff (programmes can beep while you are listening to some music, etc) and less for professional audio stuff.

Your problem comes from the fact that these systems take entire control over your sound card. So, when you start JACK, (through QJackCtl, for example) it disables PulseAudio and that makes any application that relies on PulseAudio (Banshee, for instance) unable to make sound.

The solution is to tell PulseAudio to send all it's audio through JACK while you are using it. There's one easy way to set this up in QJackCtl:

[https://wiki.archlinux.org/index.php?title=PulseAudio&oldid=181229#PulseAudio_through_JACK_the_new_way](https://wiki.archlinux.org/index.php?title=PulseAudio&oldid=181229#PulseAudio_through_JACK_the_new_way)

I hope it helps,

P.

---

### Post by akhil2091 on 2011-07-08
The guide says "setup these scripts" but does not specify where or how. Sorry I'm new to ubuntu so I might be missing something really obvious but I don't know if I'm supposed to create those scripts or run them in terminal (I tried this and it didn't work). 

Also, what if i want to connect all sound to JACK and not just the ones that run on PulseAudio? Should I connect ALSA into PulseAudio? I checked in Synaptic Package Manager that i already had some sort of programs installed for both PulseAudio and ALSA, i guess it came with ubuntu 11.4, so do I have to install some other software like alsa mixer and pulseaudio preferences etc? 

Thanks for your help.

---

### Post by undeuxtrois on 2011-07-08
Yeah, maybe the Arch Wiki isn't that clear after all. Here's what you need to do:

1- In a Terminal: sudo apt-get install pulseaudio-module-jack

This will install the PulseAudio module needed to have it use JACK.

2- Create 4 separate files containing the commands listed on the wiki and save them somewhere where you can forget about them (ex: Documents/scripts/, or something like that)

3- Make them executable. In the File Browser: Right-click -> Properties -> Permissions -> Allow executing file as program

4- In QJackCtl (which is listed as "JACK Control" here in Lucid): Setup -> Options, where you set up the scripts you have just created (Execute script on startup = pulse-jack-pre-start.sh, and so on)

5- Click OK and restart JACK by clicking Stop, then Start.

You should now see a PulseAudio JACK Sink (output) and PulseAudio JACK Source (input) and thus be able to run both JACK and PulseAudio apps without any problem.

For configuring ALSA to use PulseAudio, there is a section for that on the same wiki page:

[https://wiki.archlinux.org/index.php?title=PulseAudio&oldid=181229#Advanced_ALSA_Configuration](https://wiki.archlinux.org/index.php?title=PulseAudio&oldid=181229#Advanced_ALSA_Configuration)

but I have never tried it, since all the apps I use for making music are JACK-able.

Let me know if that works for you,

P.

---

### Post by akhil2091 on 2011-07-09
That worked! Thanks a lot for your help.

---

