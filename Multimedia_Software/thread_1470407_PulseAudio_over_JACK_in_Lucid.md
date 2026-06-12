---
title: "PulseAudio over JACK in Lucid"
date: 2010-05-02
forum: Multimedia Software
---

### Post by Emblem Parade on 2010-05-02
Why do this? Two reasons:

1) Many of us use JACK for low-latency audio work, but it's annoying to have to turn it on or off to have to allow regular Ubuntu applications to work. It's even more annoying that both can't normally work together -- either JACK or PulseAudio must take control of the sound control. This method allow JACK to do, and PulseAudio just routes to JACK.

2) JACK is kinda super awesome. By routing PulseAudio through it, your regular Ubuntu sound application suddenly get super powers. :)

Pretty easy to do! (Well, we count our blessings in Linux...)

**1. DYNAMICALLY**

You need the PulseAudio utilities and JACK sink:

```
sudo aptitude install pulseaudio-utils pulseaudio-module-jack
```

And then run this to get PulseAudio connected to JACK:

```
pactl load-module module-jack-sink
pactl load-module module-jack-source
```

Now, go to Ubuntu's sound preferences, and you'll see "Jack sink" in the output tab. :)

If you use JACK Control, you can create a script for the above and have it set up in "Execute script after Startup". Then, PulseAudio will automatically load the JACK sink when you start JACK.

**2. BY DEFAULT**

Edit /etc/pulse/default.pa, and add these lines:

```
load-module module-jack-source
load-module module-jack-sink
```

You can test it without rebooting by restarting PulseAudio. In Ubuntu, PulseAudio is started in the user session, not as a system daemon. To restart it:

```
pulseaudio --kill
pulseaudio --start
```

---

### Post by indelible on 2010-05-03
Thanks for starting this thread, been trying to figure out the mysterious nature of pulseaudio/alsa/jack and why none of them see to play nice ever since I started trying to switch to Ubuntu.  I installed the two packages fine on 10.04 AMD64 here, but when I try to enable with the pactl commands I get the oh so helpful error: 

**Failure: Module initalization failed**

syslog says: 

pulseaudio[4284]: module-jack-sink.c: jack_client_open() failed.
pulseaudio[4284]: module.c: Failed to load  module "module-jack-sink" (argument: ""): initialization failed.

I have installed the jackd package but perhaps there is some voodoo required to make it start up that I'm unaware of?

---

### Post by Emblem Parade on 2010-05-03
@indelible, you must actually start JACK first for the JACK sink to connect to it.

I recommend the software JACK Control (package: qjackctl) as a GUI, instead of using the command line.

If you're using JACK, I'd also strongly recommend you switch to the preempt kernel, which is available for 10.04 AMD64 (but not i386, for some reason). It's source identical to Ubuntu's general kernel, just compiled with a slightly different configuration to make it more aggressive for realtime applications like JACK. That means less chance of xruns!

```
sudo aptitude install linux-preempt linux-preempt-headers
```

You're lucky to start working with this on Ubuntu 10.04. Getting JACK to do realtime before was a pain in the ***... Kudos to the Ubuntu team for making this so much easier.

By the way, I can't say PulseAudio-over-JACK has been very stable for me. Sometimes PulseAudio's JACK sink fails for no apparent reason. Restarting JACK usually solves the problem. I've tried to increase latency (bad!) on JACK and it seems to have helped.

---

### Post by indelible on 2010-05-03
I had actually installed the preemtive kernel earlier, and I am running AMD64, and after much head scratching I came upon this thread which helped me get jackd running: 

[http://ohioloco.ubuntuforums.org/showthread.php?t=806730](http://ohioloco.ubuntuforums.org/showthread.php?t=806730)

I'm now able to get audio through pulseaudio to jack to the hardware in gnome-mplayer, but the main app I want to have realtime and Jack for is still remaining silent. Renoise is a closed source app though, and sadly they only release an x86 version for Linux which now I'm told means I need to use a 32-bit version of Jack to be able to use, although it also supports Alsa but even when I shut down pulseaudio and jackd and nothing is using the alsa device, Renoise just outputs silence with no errors, although maybe that's a 32bit/64bit snafu as well???  Starting to think I should have just installed 32-bit Ubuntu but then you're saying perhaps I wouldn't get preemt support.. and yeah basically this is why I say I've been "trying" to switch to Ubuntu for years.. haha.. unfortunately I didn't start trying to do this with the new "easy" way in 10.04...  ](*,)

---

### Post by indelible on 2010-05-03
What's really puzzling me is that Renoise shows up in Jack as connected, and when I play something in it the DSP load increases, but there's just no sound whatsoever, whereas it works fine in pulseaudio based apps.   Would that be the normal behavior for a 32bit app, to "seem" connected to Jack, and increase DSP load, but just not produce any output and not report any error? Seems kind of bizarre to me.  I would have expected it to be more along the lines of not connecting to Jack at all, or at least producing some kind of error.

---

### Post by Emblem Parade on 2010-05-03
> **indelible said:**
> What's really puzzling me is that Renoise shows up in Jack as connected, and when I play something in it the DSP load increases, but there's just no sound whatsoever, whereas it works fine in pulseaudio based apps.   Would that be the normal behavior for a 32bit app, to "seem" connected to Jack, and increase DSP load, but just not produce any output and not report any error? Seems kind of bizarre to me.  I would have expected it to be more along the lines of not connecting to Jack at all, or at least producing some kind of error.

This is beyond the topic of this thread...

I have no experience with Renoise, but I do think you should try to make 100% sure that you have JACK working first. I like to use Hydrogen (drum machine) to test it, but anything can work. (Audacious, a music player, also comes with a JACK output that you can use to test JACK.) Everything in my tutorial already assumes that you have JACK working well.

If Renoise doesn't work for you, I strongly recommend Ardour, which is an excellent DAW. Another good one is Qtractor.

A really dead simple one (which doesn't even use JACK, just plain ALSA!) is Jokosher.

Welcome to the world of linux audio. There are some very good things about it, but in general usability it's about 10 years behind the rest. :/

[Here's]("http://emblemparade.net/Main/Sound-production-using-free-software") an intro to this world I wrote a while ago (and sadly still relevant).

---

### Post by indelible on 2010-05-03
Yeah, Jack was definitely working in other apps.  I got fed up with 10.04 and decided to try debian and it's the same situation even with only the minimum requirements to get Renoise running installed, it's dead silent even in ALSA while other apps work flawlessly.. so it's something screwy in Renoise.. anyway I realise it's offtopic for this thread, I'll try to get help from the Renoise guys.  Thanks for the suggestions of other linux audio software anyway though.

---

### Post by mike jones on 2010-05-11
My pulseaudio to jack configuration was broken by upgrading from Karmic to Lucid.
I post this as others may experience this, and for review.

I was moded up to studio level on Karmic as in:-
[https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu)
And further patched for pulseaudio to jack as in:-
[http://sync-signal.com/2009/12/configuring-jack-and-pulseaudio-on-ubuntu-9-10/](http://sync-signal.com/2009/12/configuring-jack-and-pulseaudio-on-ubuntu-9-10/)

But after upgrading to Lucid qjackctl then failed because of these mods.

This is how I fixed it.

I executed the scripts as above:- 
sudo aptitude install pulseaudio-utils pulseaudio-module-jackdid 
then replaced the scripts in qjackctl:-
qjackctl | Setup  | Options

Execute script on Startup:    [Disabled]
Execute script after Startup:  pactl load-module module-jack-sink;pactl load-module module-jack-source
Execute script on Shutdown:    pulseaudio -k
Execute scruipt after Shutdown:start-pulseaudio-x11

(This ignores the jackpulse.conf file used before)

I also commented out with a ';' in:-  ~/.pulse/client.conf   "; autospawn = no"
(NOT /etc/pulse/client.conf)  I not sure if this is was problematical.

I have not yet found how to automate required output selection:-
SYSTEM|PREFERENCES|SOUND| OUTPUT pulesadio-jack-

Also note a qjackctl timeout of 9999 helped me to get it all working on Kamic.
cat ~/jackdrc is:- /usr/bin/jackd -t9999 -dalsa -dhw:0 -r44100 -p256 -n3

The Lucid upgrade also removed the soundfount from Qsynth Setup | Soundfounts:-
eg "/usr/share/sounds/sf2/FluidR3_GM.sf2"

This all seams to work now, I am however still frustrated by audacity crashing with jack loaded.

---

### Post by Emblem Parade on 2010-05-11
The sad truth is that even on Lucid, PulseAudio is not stable over JACK. It crashes on me for no apparent reason (AMD64).

Even though I wrote this guide, I do not recommend using it right now, at least not the PulseAudio packages available in Lucid.

---

### Post by Adriano ML on 2010-08-12
I also have some problems with pulseaudio over jack. Most programs keeps opening and closing the jack sink for no apparent reason. 

Similar to this already patched bug:
[https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/503174](https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/503174)

---

### Post by maghoxfr on 2010-08-12
Hello, I'm really interested in having this working. Sadly, I don't know much about developing but I've found something, even though is quite old. 

[This]("http://danielnouri.org/notes/2009/6/9/pulseaudio-through-jack-on-jaunty") is a script, that I don't really know how to use.

I'm sure you came across with it but I'm just posting to see if it's possible to have Pulseaudio through jack run a rt kernel in Lucid.

Thanks

---

### Post by pazuzuzu on 2010-11-06
I'm running Lucid Lynx (10.04) here as well and had problems.

I had problems getting PulseAudio routed to JACK as well. I installed pulseaudio-module-jack, edited /etc/pulse/default.pa, made sure JACK was running and that it was the default sink for PulseAudio.

Unfortunately, pulseAudio would then seg fault with this error:

```
W: module-jack-sink.c: JACK error >zombified - calling shutdown handler< 
```

It turns out there's a known issue with the versions of PulseAudio and JACK (and/or the pulseaudio-module-jack) which were causing a seg fault.  To fix this, I installed JACK2 from source and now run the JACK2.  All is going well.  

If you'd like that broken down step by step, I did a writeup on my blog, here: [http://jmyers-gnu.blogspot.com/2010/11/pulseaudio-jack2-on-ubuntu-1004.html](http://jmyers-gnu.blogspot.com/2010/11/pulseaudio-jack2-on-ubuntu-1004.html)

---

### Post by maghoxfr on 2010-11-06
I installed the pulse-jack package from synaptic and it runs fine.

---

### Post by dajjyhuaca on 2011-08-05
I am about to try this out (pulse audio over jack) but I thought it wise to ask the following questions before I proceed:

1. Will surround sound continue working as before once on jack, for example 4.1?
2. Has anyone tried this on 11.04 Natty?

Thanks a mil!

---

