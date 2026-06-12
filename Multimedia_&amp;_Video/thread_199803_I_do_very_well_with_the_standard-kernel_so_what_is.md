---
title: "I do very well with the standard-kernel so what is RT-patching good for..."
date: 2006-06-19
forum: Multimedia &amp; Video
---

### Post by zettberlin on 2006-06-19
Hello !

I have mentioned this a few times here and in other forums:

On the day i switched from Suse 9.3 to ubuntu dapper drake all my jackd-trouble was gone. WHITHOUT any hacking expect switching on the alsa-sequencer.

I use the standard-kernel:
zettberlin@zettubudapper:~$ uname -a
Linux zettubudapper 2.6.15-25-386 #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006 i6
86 GNU/Linux

on a PIV 2,6 GHz PC with 1024 RAM, 2 IDE-HDD and a Terratec EWX24/96 with envy24-chipset for audio.
My jackd-settings for everyday-use (not audio only but Web, Office and the like also at the same time under XFCE):

/usr/bin/jackd -R -p256 -t1000 -u -dalsa -dhw:0 -r44100 -p128 -n2 -s -zr

if i work with audio only i can have ardour recording/mixing and H2 and ams plus seq24 well and stable at settings for 5.8 ms Latency, To run a single Synth played by seq24 and recording its output with qarecord i switch to this:

/usr/bin/jackd -R -p32 -t1000 -u -dalsa -dhw:0 -r96000 -p128 -n2 -s -zr

that is: 0.66 ms nominal latency: not so bad ehhh ;-)

At the normal settings (for 11 - 5.8 ms latency) i do not see xruns with normal operation, if they occur as i start up big programs like Muse while  Ardour is running - they seam to not break anything. No scratches - no dropouts - nothing.
The only severe problem i still fight with is, that alsa seams to run out of sync with the envy-chip at massive datatransport or some other operations that extremely affect the memory-system. The same applies to some VST-dlls loaded via DSSI in Rosegarden. But the majority of the audioapps works just flawless - I never see or hear bad behaviour with Ardour, Zynaddsubfx, ams, seq24, specimen, H2, mhwaveedit and some 6-7 others i dayly use.

So i repeat: i got this results whithout any hacking with lsm or PAM let alone with kernel-sources : i just run the standardkernel as installed by the dapper-CD.

What will be improved on my system, if I build my own patched kernel and hack PAM ?

---

### Post by rbalfour on 2006-06-19
> 
PIV 2,6 GHz PC


You may want to try the 686 kernel.

$ sudo apt-get install linux-686

some features are left out of the standard kernel build, in MOST cases, you never need to rebuild or hack the kernel. If it works great for you now, no need to kernel-hack.

---

### Post by pellgarlic on 2006-06-19
the fact that you have a fairly decent processor, and a decent amount of ram will probably help, but i agree, your results are pretty good! i have a similar setup - P IV 3.0 GHz, 1 GB RAM, M-Audio Audiophile 2496 (ICE1712-based), and i don't get as good results as you seem to... perhaps it's cause i'm still only at the shallow end of the lurning curve here - defected to linux only a few months ago, after having flirted with it a few times over the last couple of years.

can you explain what the command-line options that you are using for jack mean?  some are obvious (44100 and 96000 are obviously the sample rates) but as i use qjackctl, i'm not sure how your options relate to the options i use.

i have actually been considering trying making a custom-compiled kernel with the realtime pre-emption patch, to achieve the "roughly 95% preemption, as compared to about 50% preemption without the patch" as claimed on ubuntustudio.com: [http://ubuntustudio.com/wiki/index.php/Dapper:Vanilla_Kernel_With_Realtime_Preemption](http://ubuntustudio.com/wiki/index.php/Dapper:Vanilla_Kernel_With_Realtime_Preemption), as jack shows a number of xruns when i start it. however, i have tried alternative window managers - minimalist ones like fluxbox, openbox and icewm, with some success - the reduction in resource-usage achieved by not loading gnome seems to help substantially.

if you are getting good results, don't sweat it - you seem to be one of the lucky few. i guess the preemptive patch will help some people more than others - as ubuntu specifically, and linux in general, is philosophically inclined to striving for usability on *any* hardware, including older computers (which might not have as fast a processor or as much ram as you or i have), some people will find the extra leeway invaluable. of course, i could also be talking out of my *** here - latency may have nothing to do with processor speed or amount of ram, but i guess faster and more can't hurt, can it?

but yeah, good results - as i said at the start, could you explain those options a little for me? i want to experiment with jack and see if i can match your results... :)

---

### Post by metasymbol on 2006-06-19
Nearly same results here, just played "hogand" a  old fashioned organ with 96000khz / 32samples - only 16 xruns in 5 minutes (with a funny sound because the pattern automatic plays double fast like d'n'b) - With this kernel ubuntu is the first end user distribution with a working jack "out of the box". 

But like zettberlin I use a envy24 based audiochip, which is optimized by design for fast audio, but on an old amd thunderbird 2200 with 1GB ram.

---

### Post by zettberlin on 2006-06-19
[QUOTE=pellgarlic]

can you explain what the command-line options that you are using for jack mean?  
[/QUOTE]

/usr/bin/jackd -R  # start jackd in realtimemode

-p256 -t1000 # let it have 256  Frames per Period and wait one second before a nonresponding client is disconnected

 -u #unlock libraries GTK+, QT, FLTK, Wine - this is important on my system for zynaddsubfx shows quite nasty habits when saving a patch if this is unchecked

-dalsa -dhw:0 -r44100 -p128  # alsa is the driver, hw0 the interface, 44.1 khz the samplerate 128 ports may suffice for now (very big scenarios could need more)

-n2 # 2 periods/buffer affects the latency, is the smallest allowed number - on some boards it can help to workaround interrupt-trouble to set more here

-s   # softmode is something like relic from my older systems on witch i checked this by default - it makes jackd Ignore xruns reported by the ALSA driver , should not be needed on a realtimesystem but does not hurt anyway :-) 

-zr #dither the signal rectangular - this eliminates unwanted artefacts if converting Samplerates.


[QUOTE=pellgarlic]
guess faster and more can't hurt, can it?

[/QUOTE]

of course not :-) but at the other hand: your system should run like hell as is -
 i guess my motherboard (Asus P4P800SE) is quite Okayish. Plus i have tuned it using its BIOS like this:

1.) disabeling every device that is not absolutely vital (Parallelport, 2nd USB, both serial ports, joystick and of course: the Onboardsoundchip)

2.) setting the slot that holds my Audiocard to an exclusive Interrupt 

thats it, no big deal...

What setting do you use and what results can you achieve?

---

### Post by dolson on 2006-06-19
If the default kernel works good for you, then great.

With dapper, you do NOT hack PAM. All you have to do is enable the audio group access to realtime priveleges, which is simply a config file setting. This is in the wik, and someone told me it was done by default even, but I can't confirm this from a fresh install as I have not done a fresh install.

With a truly pre-emptible kernel, you can do a LOT better than a standard kernel. Just FYI, on my old system, I can compile a new kernel, download files on BitTorrent, chat on Gaim, surf in Epiphany, run burnk7 3 times simultaneously, all in GNOME, all the while be recording XMMS output through JACK into Ardour with 0 Xruns, at 1.33ms latency JACK settings. I have never had the same success with a standard kernel. If you have, then great for you! Don't change it; enjoy it, and start making some music.

---

### Post by zettberlin on 2006-06-20
[QUOTE=dolson]

With a truly pre-emptible kernel, you can do a LOT better than a standard kernel. Just FYI, on my old system, I can compile a new kernel, download files on BitTorrent, chat on Gaim, surf in Epiphany, run burnk7 3 times simultaneously, all in GNOME, all the while be recording XMMS output through JACK into Ardour with 0 Xruns, at 1.33ms latency JACK settings.[/QUOTE]

Puhhh... now that is in fact some more than I can do :-) :-) 
I got very good results but not *that* good, the same stability (with all the mentioned extra-systemload) i can only have with about 6 ms Latency.

so I will try it on the new PC I have ordered, this one will not need any special hardwaresupport beyond audio so a custom kernel should do OK.

---

### Post by pellgarlic on 2006-06-20
@zettberlin: thanks for providing the info about those command-line options - i think i'll try out those settings on my setup (but entering them in qjackctl) and see how i get on...

[QUOTE=zettberlin]What setting do you use and what results can you achieve?[/QUOTE]

i didn't have much luck changing from the defaults at all (frames/period=1024, periods/buffer=4,timeout=500ms), which provide latency of about 42 milliseconds - if i reduced the frames/period or period/buffer settings, i started getting some xruns immediately (although not lots, there were too many, and a lot of "red" ones, which were over 1 ms i think, and a few were 7 ms or even 40 ms!), and going a few "notches" down on either ( to approach the latency values you report of a few milliseconds or so), i got streams of xruns.

however, my luck changed when i tried selecting the "realtime" option in qjackctl (as i saw it in your command-line options - i should really have clocked this from the beginning, don't know how i missed it... :) ) and i got much better results:

periods/buffer=2, frames/period=128, latency=2.67ms, for every 5 or so lines of "load=..." i get in qjackctl's "messages" window, i get an "xrun of at least 0.08ms (or so). this seems pretty acceptable to me :)

periods/buffer=2, frames/period=64, latency=1.33ms, for every 2 or 3 lines of "load=..." i get an "xrun of at least 0.8ms (or so). not quite as usable as the previous, but still pretty good for using the stock kernel.

as a side note - i also can't seem to change a couple of the other settings:
the "jackrealtime" server path doesn't work - i get a "Could not start JACK. sorry" error message when i click on the "start" button. i might hazard a guess that my system just isn't capable of using that because i don't have the preemptive kernel? but then, the "realtime" parameter itself seems to work ok... (if you are unfamiliar with the gui of qjackctl, look at the second screenshot on this page: [http://qjackctl.sourceforge.net/qjackctl-ss1.html](http://qjackctl.sourceforge.net/qjackctl-ss1.html) there is a "server path" drop-down, which contains the options "jackd", "jack-realtime", and "jackstart". wonder what these do?)

also, i have to leave the "input channels" and "output channels" set to "0", otherwise jack won't work... i get a "could not connect to Jack server as client. Please check the messages window for more info" error. (see attached txt file) this does not seem to hinder my recording or playback abilities though...

also, i meant to ask in my last post, but forgot - in your original post, you mentioned "switching on the alsa-sequencer". can i ask how you did that? any time i open jack, i get a "could not connect to midi sequencer" (or something like that) message, and i can't run certain other audio programs, because they can't find /dev/seq. my sound-card has midi inputs, soi i'm pretty sure it should be capable of providing this functionality, i just don;t know how to get it working... how did you do it?

---

### Post by zettberlin on 2006-06-20
> **pellgarlic]

periods/buffer=2, frames/period=128, latency=2.67ms, for every 5 or so lines of "load=..." i get in qjackctl's "messages" window, i get an "xrun of at least 0.08ms (or so). this seems pretty acceptable to me :)
[/QUOTE]

well, to be honest - there should´nt be any xruns at all at these settings exept those caused by extreme Systemload and/or buggy programs

[QUOTE=pellgarlic]
periods/buffer=2, frames/period=64, latency=1.33ms, for every 2 or 3 lines of "load=..." i get an "xrun of at least 0.8ms (or so). not quite as usable as the previous, but still pretty good for using the stock kernel.
[/QUOTE]

i have got such settings running right now for benchmarking - no xruns either...


[QUOTE=pellgarlic]
 "server path" drop-down, which contains the options "jackd", "jack-realtime", and "jackstart". wonder what these do?)
[/QUOTE]

jackstart was made for getting realtime with 2.4 kernels, "jack-realtime" is special also (i do not exactly know, what it means  said:**
> 
you mentioned "switching on the alsa-sequencer". can i ask how you did that? 

this you find at the ubuntustudio-wiki:

[http://www.ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation#ALSA_Sequencer](http://www.ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation#ALSA_Sequencer)

the sequencer is a kernel-module, a virtual device made out of software. To provide the same things you would get from a "real" Hardwaremididevice you have to make your system load it into RAM at startup. The script does this and some useful extrastuff, especially copying the existing moduleconfig-file to a backupfile namend by the recent date and checking if the module is already in there (which would mean, that something else is wrong, very unlikely though...)

---

### Post by pellgarlic on 2006-06-20
[QUOTE=zettberlin]there should´nt be any xruns at all at these settings exept those caused by extreme Systemload and/or buggy programs[/QUOTE]

hmm... maybe i need to modify some other settings, as these results are with  just jack and ardour running.

[QUOTE=zettberlin]
this you find at the ubuntustudio-wiki:

[http://www.ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation#ALSA_Sequencer](http://www.ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation#ALSA_Sequencer)
[/QUOTE]

holy crap!  i swear i must have tried "sudo modprobe snd-seq" a hundred times before, and it never worked (always got a "device not exist" error), but i thought i'd try it again, on your advice to follow the instructions on the page you linked to, and it damn well worked! :) sweet!

ok, looking at the section before the "ALSA sequencer" section at the one called "Real-time support" - do i have to do that? did you do that zettberlin? if you did, that may be the crucial difference here. if not, i guess i'll just keep looking...

---

### Post by zettberlin on 2006-06-20
[QUOTE=pellgarlic]
ok, looking at the section before the "ALSA sequencer" section at the one called "Real-time support" - do i have to do that? did you do that zettberlin? [/QUOTE]

I did but it did not give any improvement and some apps/scenarios produced more xruns than before so i commented the lines out again - dolson said in this thread, that tweaking PAM is not usefull in standard Dapper.

So try it, maybe it helps but i suspect that your Audiocard may feel not comfortable in its slot - so revisit the BIOS could be more of a success-bringer.

---

### Post by pellgarlic on 2006-06-21
[QUOTE=zettberlin]i suspect that your Audiocard may feel not comfortable in its slot - so revisit the BIOS could be more of a success-bringer.[/QUOTE]

that's sound advice, i'll look into that first. cheers :)

---

### Post by dolson on 2006-06-21
[QUOTE=zettberlin]I did but it did not give any improvement and some apps/scenarios produced more xruns than before so i commented the lines out again - dolson said in this thread, that tweaking PAM is not usefull in standard Dapper.

So try it, maybe it helps but i suspect that your Audiocard may feel not comfortable in its slot - so revisit the BIOS could be more of a success-bringer.[/QUOTE]

I did not say this. I said you do not have to HACK PAM in Dapper (unlike Breezy), because the patches are already incorporated.

If you do not follow those steps, and do not use the realtime-lsm (which you should not as it is deprecated), then your apps will not have the ability to run in realtime.

Every step on that wiki page is there for a reason.

---

### Post by zettberlin on 2006-06-21
[QUOTE=dolson]I did not say this. I said you do not have to HACK PAM in Dapper (unlike Breezy), because the patches are already incorporated.[/QUOTE]

OK - this is understood : i meant to "HACK" PAM means to change anything about it per hand... I am somewhat confused sometimes about all this stuff...

[QUOTE=dolson]
If you do not follow those steps, and do not use the realtime-lsm (which you should not as it is deprecated), then your apps will not have the ability to run in realtime.
[/QUOTE]

But they do on my system! I did follow the wiki and get less stability than whithout changing anything in /etc/security/limits.conf so i commented the lines out and now the situation is as described before: 
stable running applications (Ardour, seq24, Zynadd, ams and some 12-15 more) at about 5,8 ms (in XFCE, with Mozilla, Open Office etc running at the same time)
Yesterday i tried to run a scenario as described by you with seq24 playing something with specimen and recording it with ardour with 1.45 ms nominal latency - it worked for 2 houres or so without an xrun, then i started to experiment with fst and ran into trouble quite fast. 

But if we do not speak about experiments but working with stable, welldesigned software such as ardour or zynaddsubfx - i still see lots of risks and work and sweat and little improvement with the rt-kernel.

---

### Post by pellgarlic on 2006-06-21
@dolson - regarding the steps in the  "Real-Time Support" section:

```
sudo -i
echo @audio - rtprio 99 >> /etc/security/limits.conf
echo @audio - memlock 250000 >> /etc/security/limits.conf
echo @audio - nice -10 >> /etc/security/limits.conf
exit
```

are these necessary and/or useful if you are *not* using the realtime kernel? do they have any effect (be it positive or negative) on the default dapper kernel?

---

### Post by dolson on 2006-06-23
Those are for PAM, and have nothing to do with the kernel version you are using.

OK, not entirely true; you must be using 2.6.12 or newer (which you are, as your profile says you are using Ubuntu 6.06). This is the only requirement.

As described on the wiki, there are two separate issues here.

1) Your applications need to be able to request realtime privileges from the kernel. To do this, there are four methods: a) use a recent PAM combined with kernel 2.6.12+, b) use set_rlimits combined with kernel 2.6.12+, c) use realtime_lsm, which is now deprecated, or d) run everything as root, which is highly insecure and very much not recommended.

and

2) Pre-emptible kernel. As outlined on the wiki, the default Dapper kernel gets about 50% pre-emption. With Ingo's patch, you will get about 99% pre-emption. People with sufficiently fast systems may never notice a difference (although it would have to be a very fast system I would think), nor will people who set their buffers/periods insanely high (which results in higher latencies).

These two are independant of each other.

I don't see how PAM would make a system unstable. I have been using a hacked PAM on Breezy, and this pre-hacked PAM on Dapper for many months now, with no issues of stability.

The realtime kernel (poor name, really, as it's likely the source of confusion) DOES cause some stability issues, but I haven't noticed any on 2.6.16-rt26 yet.

---

### Post by pellgarlic on 2006-06-23
so i should notice an improvement in performance if i apply those "realtime" changes to limits.conf, even if though i am not using the realtime-preemption kernel? 

i am indeed using 6.06, with kernel 2.6.15-23-686. i believe dapper's kernel has PAM included, so apart from the description "real-time support" above the commands to edit limits.conf, everything else seems in place. i'm just unsure about the "realtime" bit, i guess.

it sounds like you're saying that audio applications can "request realtime privileges" even though you don't have a "realtime" kernel installed. is that right?

---

### Post by dolson on 2006-06-24
Yes, that is what I said, you are correct.

This has always been possible by running things as root, and the temporary solution was realtime_lsm. But now that the kernel has the hooks in place by default, all you need is a properly configured recent PAM to take advantage of this.

PAM is not part of the kernel.

I am not sure how I could lay it out more clearly than my last post, so try giving it another read. If it's still confusing, you might want to ask on the linux-audio-users mailing list.

---

### Post by metasymbol on 2006-06-28
[QUOTE=dolson]IThis is in the wik, and someone told me it was done by default even, but I can't confirm this from a fresh install as I have not done a fresh install.
[/QUOTE]

Yes, yesterday I've done a fresh install of dapper: The only thing to do to play music  with realtime ist to switch on the realtime checkbox in qjackctl. The only "ubuntustudio" optimization I've done is the "modprobe alsa-seq".

But later I will build a "real" realtime kernel (based on vanilla 2.6.17) - a clone (zcat /proc/config.gz > .config) of the dapper kernel with included module alsa-seq, molnars rt-patch and rt-lsm and check it out. 

PAM is no go for me because of the bad documentation and some graphical probs and at least, PAM is stopping my performance when I use more than 99% cpu.

---

### Post by SoftGround on 2006-06-28
With Rosegarden on the Dapper Kernel I am getting the warning about the clock resolution being too low.

I note that when you build the real time kernel you set the clock resolution to High: 1000ns.  

Do I have to re-build the Dapper Kernel to incorporate this.

Regards

SG

---

### Post by zettberlin on 2006-06-28
metasymbol handed me a benchmark for Zynaddsubfx that finally convinced me of the Need for the RT-Patches.

I really never ran into Trouble with the stock-kernel but the test with 6 instrumentpatches at the same time showed me the limits of the stockkernel.

Ubuntu 6.06 "out of the universe" Zynaddsubfx
Playing 4 Notes-Chords
Presets: (All on MidiChan 1)

Layer 1 -Sequence2
Layer 2 -Impossible Dream1
Layer 3 -Analogpad1 
Layer 4 -StringsPad1 
Layer 5 -Wind 


I need to run this with 256/44100 to make it run without crackle etc.

So i found out, what RT-patching is good for...:-)

---

### Post by dolson on 2006-06-28
[QUOTE=SoftGround]With Rosegarden on the Dapper Kernel I am getting the warning about the clock resolution being too low.

I note that when you build the real time kernel you set the clock resolution to High: 1000ns.  

Do I have to re-build the Dapper Kernel to incorporate this.

Regards

SG[/QUOTE]

That would be the only solution I know of at this time.

Of course, if you're going to rebuild anyway, you may wish to try using a vanilla kernel and the -RT patch.

---

### Post by SoftGround on 2006-06-29
Thanks Dana, I was sort of coming to that conclusion myself.
Here is the current state of play:

PC with Conexant modem and no broadband.  Fast connection at work.
On board sound + Teratec DMX 6Fire 24/96

Dapper installed and upgraded, added Ubuntu Plus CD for media.

Installed Linuxant Free model support but not fast enough for updating.
Open source conecant drivers probably conflict with onboard sound chip.

Downloaded Frode's Rosegarden 1.2.3 and dependencies + Qjackctl, Lilypond and Notedit using Live CD at work, made a local repository using dpkg-scanpackages.  Installed ok.  Had to add Kghostscript to get lilypond preview working.

I have dowloaded the 2.6.17 kernel and the 2.6.17-rt3 patch.

Do I still need the EVMS and claim bd patches on this kernel?

---

### Post by cycle on 2006-06-29
[QUOTE=SoftGround]
I have dowloaded the 2.6.17 kernel and the 2.6.16-rt3 patch.
[/QUOTE]

well theres a problem already, for 2.6.17 kernel the current rt patch is - patch-2.6.17-rt1

:wink:

---

### Post by SoftGround on 2006-06-29
Well spotted cycle, but fortunately its a typo, will edit to avoid further embaressment.

The current patch (as I edit) is  2.6.17-rt4, so I am downloading that now.

---

