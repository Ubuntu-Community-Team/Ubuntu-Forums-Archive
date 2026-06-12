---
title: "Jack refuses to start after I upgraded to 13.04 64bit"
date: 2013-05-26
forum: Multimedia Software
---

### Post by redaxe90 on 2013-05-26
A few days ago I upgraded my 64bit system to 13.04, in the belief that I could continue recording my own music without any biggish problems. Then I had no real use for Jack for a few days, but today I've hit a wall face first. The first indication of problems came when I opened up the Message pane of Jack
```
 [COLOR=#999999]17:13:31.061 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]17:13:31.075 Statistics reset.[/COLOR]
 [COLOR=#cccc99]17:13:31.182 ALSA connection change.[/COLOR]
 [COLOR=#999999]17:14:21.236 D-BUS: Service not available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot read socket fd = 15 err = Success
 CheckRes error
 JackSocketClientChannel read fail
 Cannot open qjackctl client
 Registered event listener change listener:  true 
 QSpiAccessible::accessibleEvent not handled:  "6"  obj:  QMenu(0x24a5f20) "" 


```
Now I have no idea why this has happened, but I decided to go into the setup, to make sure everything was checked as before and nothing had changed. Note that I've always used this to record music via my Lexicon Omega USB soundcard, which has never failed me until now.

After checking that the setup was as I left it last time, I pressed the Start button, causing Jack to freeze temporarily. Until it gave me an error message in the message pane
```
 QSpiAccessible::accessibleEvent not handled:  "7"  obj:  QMenu(0x24a5f20) "" 
 FIXME: handle dialog start. 
 QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QObject(0x0)  " invalid interface!" 
 QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QObject(0x0)  " invalid interface!" 
 QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QObject(0x0)  " invalid interface!" 
 QSpiAccessible::accessibleEvent not handled:  "8008"  obj:  QObject(0x0)  " invalid interface!" 
 FIXME: handle dialog end. 
 [COLOR=#999999]17:19:47.875 JACK is starting...[/COLOR]
 [COLOR=#990099]17:19:47.879 /usr/bin/jackd -p128 -t2000 -dalsa -dhw:1 -r44100 -p256 -n2[/COLOR]
 [COLOR=#990099]Cannot read socket fd = 15 err = Success[/COLOR]
 [COLOR=#990099]CheckRes error[/COLOR]
 [COLOR=#990099]JackSocketClientChannel read fail[/COLOR]
 [COLOR=#990099]Cannot open qjackctl client[/COLOR]
 [COLOR=#999999]17:19:47.906 JACK was started with PID=2893.[/COLOR]
 [COLOR=#999999]Cannot create thread 1 Operation not permitted[/COLOR]
 [COLOR=#999999]Cannot create thread 1 Operation not permitted[/COLOR]
 [COLOR=#999999]Cannot create thread 1 Operation not permitted[/COLOR]
 [COLOR=#999999]`default' server already active[/COLOR]
 [COLOR=#999999]Failed to open server[/COLOR]
 [COLOR=#999999]jackdmp 1.9.10[/COLOR]
 [COLOR=#999999]Copyright 2001-2005 Paul Davis and others.[/COLOR]
 [COLOR=#999999]Copyright 2004-2013 Grame.[/COLOR]
 [COLOR=#999999]jackdmp comes with ABSOLUTELY NO WARRANTY[/COLOR]
 [COLOR=#999999]This is free software, and you are welcome to redistribute it[/COLOR]
 [COLOR=#999999]under certain conditions; see the file COPYING for details[/COLOR]
 [COLOR=#999999]17:19:47.966 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#ff0000]17:19:55.102 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 [COLOR=#ff0000]Cannot read socket fd = 16 err = Success[/COLOR]
 [COLOR=#ff0000]CheckRes error[/COLOR]
 [COLOR=#ff0000]JackSocketClientChannel read fail[/COLOR]
 [COLOR=#ff0000]Cannot open qjackctl client[/COLOR]
 [COLOR=#ff0000]QSpiAccessible::accessibleEvent not handled:  "2"  obj:  QMessageBox(0x7fff9397e650) "" [/COLOR]
 [COLOR=#ff0000]FIXME: handle dialog start. [/COLOR]
 [COLOR=#ff0000]FIXME: handle dialog end. [/COLOR]
 [COLOR=#ff0000]QSpiAccessible::accessibleEvent not handled:  "6"  obj:  QMenu(0x2410620) "" [/COLOR]


```

Now I'm completely stumped. I have no clue what might have happened during the upgrade of the OS, especially since no indication of anything failing showed up on the upgrade.
I usually run the computer on the LXDE desktop environment, because it's the easiest on the resources. Is it possible that the upgrade might have blown my system to smithereens?? Everything else works fine, btw.


[update]
I forgot to mention that every time I try to run the upgrade command with apt-get, I get this little ditty and it's been behaving like this since 12.04

```
root@Loonie:~# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libboost-date-time-dev libboost-dev libboost-filesystem-dev
  libboost-iostreams-dev libboost-program-options-dev libboost-regex-dev
  libboost-serialization-dev libboost-signals-dev libboost-test-dev
  libboost-thread-dev
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.


```

I just remembered that I had added a guitar tablature reading program called Tuxguitar, which refuses to play sounds for me, though I did install it before the upgrade to 13.04 and that Jack worked after it's installation. I just wanted it on record, in case it altered something when the upgrade took place

---

### Post by ohnonot on 2013-05-26
just to make sure, are you running lubuntu or ubuntu with lubuntu-desktop installed?
did you upgrade from 12.x to 13.04, or was it a minor maintanence update/upgrade/whatever?
pulseaudio does not show up in your error messages, is it a pulse-free environment?

---

### Post by redaxe90 on 2013-05-26
Sorry for not being too clear on this. I originally installed Ubuntu 64-bit, 12.04 and later upgraded to 12.10, which is when the first upgrade problems started, i.e. the ones I mentioned at the very end of my first post addition. Following that original installation I installed Lubuntu desktop and have been running the LXDE desktop environment ever since. Funny enough, after the upgrade to 12.10, I could no longer log into Gnome or any of the other desktop environments. And this problem has kept up following the upgrade to 13.04.

I have Pulse installed, but I have never seen whether it actually works or not. When I've been running Ardour, Rakarrak, Hydrogen or any other of the programs that have relied on Jack to interact, I've never managed to to get the onboard sound chip to actually port the sound to my speakers, after doing what needs to be done through the external source.

If I've forgotten anything, please smack me around the head, I'm bound to have missed out on something and that wouldn't be for the first time despite my best efforts

---

### Post by ohnonot on 2013-05-27
smacking on the head is something one should do to oneself, not others. ;)

somebody on these forums sure can help (including you and me), but have you considered this:
start from scratch and install lubuntu. or maybe even multiple partitions, one with an os for "normal computering", one for sound production (i personally have good experience with AVLinux; i've even been using it as my main system for a while), and one partition with no os, for data only.
---------------------(rant over)

i couldn't find info about your libboost error, i don't even know if it has anything to do with sound.
[http://askubuntu.com/questions/293395/problem-install-in-boost-lib](http://askubuntu.com/questions/293395/problem-install-in-boost-lib) - maybe this could be a strting point for you.

it would be good to find out if pulseaudio is running when you log in to lubuntu desktop.
open a terminal, type: 'sudo apt-get install htop', then type: 'htop'.
it's a nice tool for many occasions. 
search (F3) 'pulse' and if you get something, then that's not good.
actually now i think of it, ubuntu and lubuntu use different sound architectures and that might cause problems.
even if ubuntus native sound architecture (pulseaudio) is not started when you log into lubuntu-desktop, its config files might still do some harm.

please do some reading: [http://www.tuxradar.com/content/how-it-works-linux-audio-explained](http://www.tuxradar.com/content/how-it-works-linux-audio-explained)

the log messages come from qjackctl?
could you start qjackctl from a terminal and see if it gives some (relevant) messages into the terminal window.

---

### Post by redaxe90 on 2013-05-27
Thanks, I'll have a look at this once I'm done working today and report back

---

### Post by redaxe90 on 2013-05-27
This is the only mention of Pulse in htop

2301 tommi  -6  -11 494M 5676 3016 S 0.0 0.1 0:00.00 /usr/bin/pulseaudio --start --log-target=syslog


As for the links, I'll need to sit down when I have time and have a good read. Hopefully it will help me make any sense of what's been going on in my system

---

### Post by redaxe90 on 2013-05-28
I've been reading until the letters started spinning in front of my eyse and one thing completely evades me. Is it OK to just remove PulseAudio and all of it's components, excluding VLC player, without the sound setup of the computer completely collapsing on me??

Another thing that I'm thinking about is this: What is the interaction between PulseAudio and Jack??? I can't really wrap my head around it. Seems like I don't need both, at least not for recording my own music via my external source.

---

### Post by ohnonot on 2013-05-29
you said you are only using lubuntu desktop - in that case it is ok to remove pulseaudio completely.

you probably understood now that alsa is the base layer, and both jack and pulseaudio are building on top of that.
now there is ways to have pulseaudio as a plugin into jack, iirc, or maybe the other way around... however i would recommend to decide for either pulseaudio or jack and drop the other.

that said, uninstalling pulseaudio, you might have to reinstall jack, too, because your /etc/asound.conf is probably still messed up and needs to be adapted so jack can settle itself onto alsa.
please don't expect jack to work out of the box. it is great for musicking, and lightweight, but requires a minimum of configuration, and you will probably want to configure more once you see how it interacts with your hard- and software.
btw, the package you're looking for is jackd2.

but your using lubuntu on an ubuntu install will probably cause more trouble after the next upgrade. 
i just installed lubuntu 13.04; i really like it, it feels very stable, simple yet complete, nice design... i've been waiting for lxde to develop into a fullgrown DE and here it is.

PS: what is this external source? are you using 2 soundcards?

---

### Post by redaxe90 on 2013-05-29
I'm using an external soundcard/mixer called Lexicon Omega and I had tried using it while still running Windows, but could never get it to communicate with Cubase in a manner I found satisfactory. But after installing Ubuntu, and then the Ubuntu audio package, it worked great. Getting it to work with the programs I got was a learning curve, so you can imagine my frustration when Jack suddenly started behaving like it was possessed, refusing to start up.

The motherboard has a built in soundchip, which I use for general audio use, but it is unable to accept a guitar lead so I could possibly listen to what I play through there, which is why I bought that Lexicon thingimajick :)

I've been thinking about maybe installing [UbuntuStudio]("http://ubuntustudio.org/") but since I don't have a CD burner or a USB stick, it will have to wait a while. I reckon I'll end up doing that, if I don't find any easy to implement solution to this particular problem.

Thanks for your assistance so far.

---

### Post by ohnonot on 2013-05-30
since using jackaudio seems to be a sane choice in your case, i would repeat my recommendations from post #4 (rant).
it is always possible to repair things linux, but difficult.
on the other hand, it's always good to get more aquainted with packet management and your system in general.
as a last measure, you could just uninstall pulseaudio, then take a look at /etc/asound.conf. it should not contain the word pulse. if it does, you have to find a default asound.conf from somewhere and replace it. also there might be .asoundrc in your home folder, that can just be deleted.
after that try restarting jack (qjackctl).

what kind of software are you using? i can look in my [AVLinux]("http://www.bandshed.net/AVLinux.html") install and tell you if it's all there.
(it's 32bit only but works on 64bit systems. if you're hardware is not new it doesn't even make a difference)

genrally, it's nice to hear somebody appreciates linux/ubuntu.
it's driving me nuts, all those folks stating indignantly: "i NEVER had this problem with windows. this is outrageous" as soon as they are asked to open a terminal window (happily ignoring they got a whole operating system completely for free).

---

