---
title: "ZynAddSubFX freezing Dapper"
date: 2006-05-27
forum: Multimedia &amp; Video
---

### Post by ronlybonly on 2006-05-27
I just grabbed Nasca O. Paul's synthesizer, ZynAddSubFX, from the Dapper Universe repo., but whenever I try to run it, the computer freezes and i have to reboot. Has anybody else experienced this problem?

---

### Post by bwanab on 2006-05-30
I use it all the time and it works perfectly under Dapper. Are you sure you're running jackd before you run zynaddsubfx?

---

### Post by ronlybonly on 2006-05-31
[QUOTE=bwanab]I use it all the time and it works perfectly under Dapper. Are you sure you're running jackd before you run zynaddsubfx?[/QUOTE]

Isn't ZynAddSubFX supposed to be able to run w/ ALSA or OSS without JACK?

---

### Post by slugkilla on 2006-05-31
You need to download JACK Control from the repo and have it running while you launch zyn.

---

### Post by bwanab on 2006-05-31
[QUOTE=ronlybonly]Isn't ZynAddSubFX supposed to be able to run w/ ALSA or OSS without JACK?[/QUOTE]
You're right - and it still works fine for me. Have you been able to run any other audio out applications?

---

### Post by samoht on 2006-06-01
Zynaddsubfx doesn't freeze the OS, but randomly crashes a lot here (dapper, amd64). :-(

---

### Post by slugkilla on 2006-06-01
could you at least try running jack control before running zyn? It worked for me.

---

### Post by tenzin on 2006-06-08
[QUOTE=slugkilla]You need to download JACK Control from the repo and have it running while you launch zyn.[/QUOTE]

got the same problem....


hmm...what do you mean with "download JACK Control"?
Whats that for a package? Cant find it in the Rep.

do you mean qjackctl? then it work not anyway

...would be great if anybody can give a exactly workaround

thx
tenzin

---

### Post by ronlybonly on 2006-06-09
Yeah, the JACK Control app is qjackctl. Is this not working for you?

---

### Post by tenzin on 2006-06-10
[QUOTE=ronlybonly]Yeah, the JACK Control app is qjackctl. Is this not working for you?[/QUOTE]

no, I allways tried it with qjackctl....it just freezes...

do I need special configuration on jack to work nice with zyn?



and has midi to be enable (cause right now it does not work)

greetings

---

### Post by tenzin on 2006-06-12
...has midi to be enabled/activated?

---

### Post by zettberlin on 2006-06-12
[QUOTE=tenzin]...has midi to be enabled/activated?[/QUOTE]

yes - if alsa-seq is not running Zynadd will crash (and eventually freeze the Desktop) to start alsa-seq do like this:

1. ) open a console-window / teminal an become root

zettberlin@zettubudapper:~$ sudo bash

2.) enter the following commands, that i learned from Dana Olson of ubuntustudio:


#sudo bash
#modprobe snd-seq
#echo snd-seq >> /etc/modules
#exit


now Zynadd should start OK, if you really want to use Linux for audio, fetch a jackit-environment including at least:

jackit
qjackctl
muse
ardour


find out, how to set it up here:

[http://ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation](http://ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation)

it is much easyer, than it looks like ;-)
Plus: for me it works just perfectly WITHOUT hacking PAM or lsm. Use the standardkernel for dapper and everything should be fine for Latencies as loww as 4-5 ms :-)

p.s.: Zynadd and jackd should run the same Samplerate, as should alsa as well ...

---

### Post by tenzin on 2006-06-13
thx zettberlin...you are great.

works pretty well....

now all app work that I need :KS 



regards

---

### Post by dolson on 2006-06-13
FWIW, that step is definitely in the wiki... [http://www.ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation#ALSA_Sequencer](http://www.ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation#ALSA_Sequencer)

---

### Post by zettberlin on 2006-06-14
yeah - the script in the wiki will work as well - yet it is mor complicated - it does more or less the same..

BTW: i really made the best experiences with the stockkernel without any hacking of PAM or lsm - as i added the mentioned lines to limits.conf i get a crossfire of xruns and a destructive loss of my envy-chips  internal sync, producing most unwanted distortioneffects.

Right now i run muse with 3 synthplugins synced with H2 without any glitches at 5.8 ms latency. The maximum was ;-)0.33ms (16 frames/period 96000 Hz):-) with seq24 playing a complex basspatch in ams stable enough to use  the sliders of the included moog-filtermodule.

---

### Post by The_Archdude on 2006-06-15
i have a probleme with snd-seq :

# modprobe snd-seq
FATAL: Module snd_seq not found.
FATAL: Error running install command for snd_seq

here's my modules related to seq :
/lib/modules/2.6.15.7-rt21/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.15.7-rt21/kernel/sound/core/seq/instr/snd-ainstr-iw.ko
/lib/modules/2.6.15.7-rt21/kernel/sound/core/seq/instr/snd-ainstr-gf1.ko
/lib/modules/2.6.15.7-rt21/kernel/sound/core/seq/instr/snd-ainstr-simple.ko
/lib/modules/2.6.15.7-rt21/kernel/sound/core/seq/snd-seq-dummy.ko

i compiled my kernel with rlimits as you can see, but i had no other alsa setting concerning seq : i checked them all during make menuconfig

---

### Post by zettberlin on 2006-06-15
OK - what if you ask for snd-seq-virmidi like this:

# modprobe snd-seq-virmidi

??

Plus: How did your System work with the Stockkernel (where this should be no issue :-) )?

---

### Post by dolson on 2006-06-15
The "script" in the wiki wasn't my idea, someone else modified that to make a backup of your modules file before you go off and echo things into it. And that's a good idea, in my opinion. Besides that, it also only modifies it if the alsa-seq module is not listed already.

It might look complex, but so does other sections of the wiki. But the thing is, you can copy and paste that stuff, and it will work.

If I should dumb down everything so it doesn't protect users from typos even more than it already doesn't, then let me know, and I will do it gladly.

---

### Post by zettberlin on 2006-06-19
To be "complicated" does not mean "not good" - of course it is better, if there is a backup before one changes something in an important system-file.
Though I would suggest to have some comments for beginners like this:

#get root-privileges
sudo su
#insert the module for the sequencer
modprobe snd-seq
#find out, if the seqencer is already in the file that makes modules loaded at bootup and inform the user about the results
if grep -q -x snd-seq /etc/modules; \
  then echo && echo "NOTE: snd-seq is already in /etc/modules, no changes needed"; \
#if the sequencer is not in the file make a backup named by the recent date and attach the command to load the module to the end of the file
  else cp /etc/modules /etc/modules_backup_`date +%Y%m%d%H%M` && echo snd-seq >> /etc/modules; \
fi
exit

AND: Would it not be better to have the sequencer enabeled by default if one installs a Program that needs it to run (Zynadd, qjackctl, Muse etc etc etc)?

Maybe we could ask the responsible people in the project to have have it like this...

---

### Post by dolson on 2006-06-19
TBH, I don't see why the sequencer isn't automatically loaded, period.

---

### Post by kellogs on 2006-06-27
i found zynadd pretty picky... sometimes it works for hours, and sometimes it just drops from jack...

The best settings I found for working quite well are the ones on the wiki... but with periods/buffer 4. less than 4 and it will drop from jack after sometime.

Other Synths/plugins do work quite stable... hydrogen for example is rock solid and Qsynth is stable as rock too (it loads big soundfonts in less than a second lol!!!!). So the problem could be zynadd...... 

I use the stock kernel and rosegarden4. I got about 5 ms , and sync is perfect. If you put the same buffers/periods as in jack in the program you use, you get less drops from jack. for example rosegarden and jacks work quite stable if I use the same settings on both.

---

### Post by dolson on 2006-06-28
kellogs, ZynAddSubFX is not very realtime-friendly. If you click around in the GUI enough, you're going to get Xruns and/or disconnects. That's just how it is right now... I don't know if the developer plans on fixing it or what.

---

### Post by zettberlin on 2006-06-28
[QUOTE=dolson]kellogs, ZynAddSubFX is not very realtime-friendly. If you click around in the GUI enough, you're going to get Xruns and/or disconnects. That's just how it is right now... I don't know if the developer plans on fixing it or what.[/QUOTE]

Yeah, Zynadd is challenging and you can easily click patches in it that order maths from it that will overload any System below an Movie-Studio renderfarm.

At the other hand it offers al lot and for an application as complex as it is it is astoundingly flawless and stable.

---

