---
title: "Freebob and Dapper"
date: 2006-07-13
forum: Multimedia &amp; Video
---

### Post by aldous on 2006-07-13
I bought an M-Audio FireWire Solo yesterday and stayed up for hours late into the night trying to get freebob to build for me and my 64bit Dapper.  I'm following David Morrelli's instructions here:

[http://www.davidemorelli.it/dokuwiki/doku.php?id=other:freebob_on_ubuntu](http://www.davidemorelli.it/dokuwiki/doku.php?id=other:freebob_on_ubuntu)

I faced hours of headache trying get libfreebob to build from svn due to an automake problem.  The docs mentioned that you have to build autoconf, etc. from source, a fact that I failed to recognize for some time.  Even after gettting them all built, I still had trouble compiling because aclocal could not find the libtool.m4 file and I was getting a LIBTOOL error.  Finally fixed this like so:

sudo cp /usr/share/aclocal/libtool.m4  /usr/local/share/aclocal

Now when I try to compile the lib, I'm getting this error during the configure step:

./configure: line 20647: syntax error near unexpected token `LIBRAW1394,'
./configure: line 20647: `PKG_CHECK_MODULES(LIBRAW1394, libraw1394 >= 1.2.1)'

I already built the latest libraw1394 from source and did make install.  In fact, it will fail on all of the PKG_CHECK_MODULES lines:

PKG_CHECK_MODULES(LIBRAW1394, libraw1394 >= 1.2.1)
PKG_CHECK_MODULES(LIBIEC61883, libiec61883 >= 1.0.0)
PKG_CHECK_MODULES(LIBAVC1394, libavc1394 >= 0.5.3)
PKG_CHECK_MODULES(ALSA, alsa >= 1.0.0)
PKG_CHECK_MODULES(LIBXML, libxml-2.0 >= 2.6.0)

I should be able to pass all of these checks.  I'm confused.

Can anyone offer a suggestion?

Also, I noticed that there is a package for jack 1.101.1, which has support for freebob, in Ubuntu Edgy.  Obviously, someone has already worked through these issues.  I sure would like to selectively bring the freebob related packages back into my Dapper world without going 100% edgy.  

How tough would this be?

I just know if I keep at it (he says with a forced smile through gritted teeth), I'll eventually get to use my FireWire Studio box!  Thanks for everyone's help on this board.

---

### Post by quilted on 2006-07-14
I would also like to know this as I have a Presonus Firebox here that is just waiting to be used.

---

### Post by aldous on 2006-07-15
For the record, most of my grief building freebob from svn had to do with the versions of autoconf, automake and libtool.  I built all from source, latest versions, and got nothing but weird macro errors.  Finally I got them to all behave by changing my configure prefix from --prefix=/usr to --prefix=/usr/local, which I'm almost certain is the wrong thing to do for Dapper.  I reverted this later, and seem to have a good build environment using these versions:

automake version 1.8.5
autoconf version 2.60
libtool version 1.5.22
pkg-config version 0.20

I've got freebob installed along with jackd.  I "feel" like I'm almost there...

But I'm getting this when I try to run jackd:
 sudo jackd -d freebob
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
Root node has no children!
Root node has no children!
LibFreeBoB ERR: No connections specified, bailing out
FreeBoB ERR: FREEBOB: Error creating virtual device
cannot load driver module freebob
no message buffer overruns

Still working toward success...

---

### Post by quilted on 2006-07-15
As I was going to reinstall Ubuntu anyway, I tried to bring over the edgy packages to dapper. And well, freebob worked really well, but a lot of other things stopped working properly. So I wouldn't recommend that anyway. I guess building for source is the way to go. Let me know if you get it going.

---

### Post by aldous on 2006-07-15
What worked and what didn't?  I might be willing to do it.  Trying to recompile everything from scratch quite painful.  

I managed to get freebob-enabled-jackd going.  It now runs, but I can't connect anything to it.  I haven't been able to get qjackctl to compile yet.  I compiled hydrogen from source, but the gui is flaky, and it still can't connect to the new jack.

---

### Post by aldous on 2006-07-15
An update:  I am able to run jackd and record wav files using FireWire studio.  No playback yet.  The idea of having to build all of my audio programs is daunting.  I'm having trouble with ajackctl. 

Very tempted to go with Edgy.  Somebody stop me if this is a terrible idea.](*,)

---

### Post by quilted on 2006-07-16
Well for starters, gnome-panel and nautilus froze on startup rendering gnome unusable so I had to start a KDE-session which went well. Then I found that a lot of GTK-apps didn't work properly.
To be honest I didn't take the time to find out why exactly as I needed to have a working system to do my work. But I suspect that libc6 was to blame.

---

### Post by aldous on 2006-07-16
I went forward to edgy, but like you, I had some X related problems, plus I was getting weird errors using apt.  For a time I lost Ubuntu Desktop, but was able to get KDE working.  I decided I wanted to revert back to Dapper and wasn't sure how other than just change edgy back to dapper in the sources.list and dist-upgrade.  

My system is almost back to normal.  I've got some weirdness still, because I think the packages I picked up when trying to go edgy are still here.  I'm guessing that apt uses a >= when comparing packages, and if I have something newer just leaves it alone.  Don't know this for sure though.

On the Freebob front, I've been able to get qjackctl to compile and I can see my m-audio FireWire ports in the connect window. I've been able to record a wav using the jackrec that I built along with jackd.  But no playback yet.  

In fact, I haven't been able to connect any jack clients to the freebob-enabled-jack.  Why, FSM, WHY???

---

### Post by aldous on 2006-07-17
Update: Other jack apps are now able to startup.  They didn't need to be recompiled, they were simply picking up the old jacklibs floating around under /usr/local or /usr.

Sadly, my temporary switch to Edgy and back to Dapper made my system unstable.  I'm going to temporarily switch to pure Debian, because all of the packages I need are ready and usable.  I'm impatient and want to use freebob now.  I'll come back to Ubuntu once freebob and jack 0.101.1 are available as standard packages, which I hope will be soon.

---

### Post by aldous on 2006-07-18
Nevermind that...I'm sticking with Ubuntu.  Too much pain to switch distros and, besides, I'm really digging Ubuntu.  I'm now able to connect Hydrogen to jack, but only when I run everything as root.  I'll work out permission issues later.  At this point I can see everything working, but no sound comes out of the FireWire Solo.  I'll keep at it...

---

### Post by aldous on 2006-07-23
I split my harddrive into two partitions and on one I'm running Debian and I have the full suite of audio applications now working with freebob-enabled-jack.  This setup can also be made to work with Ubuntu (64 bit too), but I had to spend a great deal of time getting all of the packages built from source.  In the end I opted to use the Debian 32bit packages (and Debian), since it was easier.  I WAS able to record using freebob and the FireWire Solo under Ubuntu, so it WILL work.

Important note:  My M-Audio FireWire would not play back using the freebob driver out of the box.  It was almost as if the internal mixer playback settings were turned down.   You can't use alsamixer to turn them up as freebob is not using the alsa backend. To test this I installed the M-Audio drivers on a Windoz box with the intent of using the windows software shipped with M-Audio, and sure enough, they appeared to be down the first time I opened the mixer program.  By the second time I opened it, the volume "sliders" were up.  (I didn't move them up myself.)  After this, I reconneded the m-audio back to Linux, and for the first time I could hear playback.

---

### Post by RIV@NVX on 2006-08-07
> **aldous said:**
> I split my harddrive into two partitions and on one I'm running Debian and I have the full suite of audio applications now working with freebob-enabled-jack.  This setup can also be made to work with Ubuntu (64 bit too), but I had to spend a great deal of time getting all of the packages built from source.  In the end I opted to use the Debian 32bit packages (and Debian), since it was easier.  I WAS able to record using freebob and the FireWire Solo under Ubuntu, so it WILL work.

Important note:  My M-Audio FireWire would not play back using the freebob driver out of the box.  It was almost as if the internal mixer playback settings were turned down.   You can't use alsamixer to turn them up as freebob is not using the alsa backend. To test this I installed the M-Audio drivers on a Windoz box with the intent of using the windows software shipped with M-Audio, and sure enough, they appeared to be down the first time I opened the mixer program.  By the second time I opened it, the volume "sliders" were up.  (I didn't move them up myself.)  After this, I reconneded the m-audio back to Linux, and for the first time I could hear playback.
This is rather strange, as this is the first report of this card actually working. All mailing lists suggest Audiophile and Solo as unsupported, even freebob.sf.net lists it on supported device list. Can you provide all console logs that could be useful?
Also, are you using FreeBoB 0.9.0, 1.0-svn or trunk? What versions of relevant libraries?
And, can you provide a *detailed* of your exact actions to get it working?
I would be very grateful if you did.

---

### Post by dumbace on 2006-08-15
Hi all there...

I'm a newbie on Linux and installed Ubuntu three days ago. No skill on it, at all...

I own a presonus firebox too, that's the major issue...

My Ubuntu version (6) doesn't like any driver from freebob, expecially as it asks for a million of other stuff (e.g. libc6) that seems to be older and system refuses to go downgrade...well, it's wonderful, isn't it.
My questions are:
do I better run another distro?
or have I to force down to new older drivers?
... 
thanx in advance for any contribution
cheers
paolo

---

### Post by quilted on 2006-08-17
If you have the patience, then wait for the next release of ubuntu as it contains the freebob driver. Don't try to force install it, it will screw up the system.
You could try compiling it yourself, but I had no luck getting it to work.

---

### Post by libertyforever on 2006-08-21
I am looking to get FreeBob on Dapper as well with the intent of running a Presonus Firebox.  The [FreeBob project]("http://freebob.sourceforge.net/index.php/Main_Page") lists the Firebox as one of it's supported devices.  They have instructions for installing it [here]("http://freebob.sourceforge.net/index.php/Building_and_Installing").  My problem is I'm a newbie and the instructions are over my head.  Does anyone know of a resource that could possibly catch me up to speed on how to install freebob in Dapper?  My problem is I don't know how to install much of  anything without using synaptic package manager (that's how newbie I am :) ).  Any chance Ubuntu will have a build of it sometime soon in the repositories?  Anyone out there have any suggestions?  . . . . .  Anyone???? [-o<

---

### Post by libertyforever on 2006-08-24
Oops, guess I should read more carefully!  Am I reading that right: Edgy will have FreeBob included?  That would make things a lot smoother for newbies (like me).  Can someone please explain how the whole set up works?  I have gone through the Ubuntu Studio set up wiki and studied the FreeBob page, but I'm still confused as to how they work together.  Does the audio interface connect to FreeBob, and then FreeBob to jack, and so on?

---

### Post by dumbace on 2006-08-27
> If you have the patience...

lotsa patience here, thanks for the (hopefully) good incoming news....;)

---

### Post by phatmonkey on 2006-10-29
Is Freebob in the edgy repositories then? I can't seem to find it if it is! Jackd doesn't seem to have been compiled with freebob support.

---

### Post by AgenT on 2006-10-29
> **phatmonkey said:**
> Is Freebob in the edgy repositories then? I can't seem to find it if it is! Jackd doesn't seem to have been compiled with freebob support.
[Ubuntu Package Search]("http://packages.ubuntu.com/")

---

### Post by phatmonkey on 2006-11-01
> **AgenT said:**
> [Ubuntu Package Search]("http://packages.ubuntu.com/")
Yeah, I tried that. I guess it isn't then!

---

### Post by leleobhz on 2006-11-13
Well, this is my history:

A few days ago, i have tryed to compile it on fedora and ubuntu. And.... i forgotten fedora :]

Well, on ubuntu, the problem itself isnt the libfreebob, but:

1) Jackd without freebob support
2) libiec61883 deprecated on repos (and im using edgy!)

So, ive decided fork the jackd compilation, with more two dependences: my libiec and my libfreebob.

Good news: i`ve gotten the packages.

Bad News: Have a lot o wrong things... I'm not a very experienced packager, so, my packages have a lot of badthings, like errors on gpg signature and libs, headers and binaryes on same file, altrought separatelly on libxpto, libxpto-dev and xpto, and another bad things (if someone want help, i ll try search a server to put it).

But my major objective arent aimed. Unfortunelly, firewire 410 dont work on linux because the boot problem, what i think may be solved, like the usb adsl modems, but im highly sad about this.

So, if someone want help on this jouney, be wellcome and plz talk with me! I NEED BETA-TESTERS! ;) ;) ;) ;) ;)

---

### Post by dogbreath on 2006-11-15
I've got a M-Audio Solo.
Can I test your jack package?

---

### Post by leleobhz on 2006-11-16
> **dogbreath said:**
> I've got a M-Audio Solo.
Can I test your jack package?

Well,i need pay my server (im late :[) so, when it get online again, i ll send the line for sources.list, ok?

---

### Post by dogbreath on 2006-11-16
Ok.

If you can, you could send me the package too.

---

### Post by Rush_898 on 2006-11-20
I've been combing forums and guides for a week or better, I have tried agnula and was not happy with it.  My question is, has anyone gotten freebob to fully work on an ubuntu release (dapper or edgy), and if so, what guides/advice can be shared?  My specific hardware is a firepod, so far I cannot get Jack to recognize freebob correctly.

---

### Post by phatmonkey on 2006-11-20
> **Rush_898 said:**
> I've been combing forums and guides for a week or better, I have tried agnula and was not happy with it.  My question is, has anyone gotten freebob to fully work on an ubuntu release (dapper or edgy), and if so, what guides/advice can be shared?  My specific hardware is a firepod, so far I cannot get Jack to recognize freebob correctly.

I compiled the dependancies for libfreebob that weren't included in ubuntu (firewire libraries I believe), then compiled the latest versions of libfreebob and jack. Then any JACK programs you need to use will probably need to be recompiled too (use apt-build).

---

### Post by leleobhz on 2007-02-21
GOOD NEWS!!!!!!!!!!!!!

Finally ive finished the packaging of freebob + jackd. As jackd is a complicated package, and the version of ubuntu is too hard to put support for freebob, ive decided to backport it from debian-experimental, rebuilding the dependences. Ive tested here, but my sound card isnt supported (firewire 410), but it loads on jackd too.

Have too the lattest qjackctl too, so enjoy!!!

Instructions to install the repository: [http://wiki.ubuntubrasil.org/Praat/English]("http://wiki.ubuntubrasil.org/Praat/English")

Any questions, myusername at myusername.org

---

### Post by w3sz on 2007-02-26
Didn't read the whole forum...was looking for other things...I have had Freebob and Firebox working with Dapper for quite a while [since October 2006].

Here is my website where I listed what I did.

[http://www.nitehawk.com/w3sz/dttspw3sz.htm#15](http://www.nitehawk.com/w3sz/dttspw3sz.htm#15)

Best Regards to all.

---

### Post by leleobhz on 2007-02-27
Well, my packages are a little backported from Debian experimental (lattest jack w/ freebob and deps), and the libfreebob are compiled from 0.

---

### Post by vivichrist on 2007-03-02
I have feisty and all is well and good in the world.
freebob works (its a bit wonky but either works or can't connect ,which seems to me to be a matter of timing) with my presonus firepod. feisty has low-latency kernel, make changes to your limits.conf and realtime jackd with sub 10ms latency:KS :) :guitar:

---

### Post by unclernie on 2007-03-06
Thanks for shining a light at the end of the tunnel.  I've got a new AMD64 laptop that I'm trying to set up as a DAW with Feisty.  CUrrently playing with herd 5, I managed to install all but one of the packages of ubuntustudio-audio, (supercollider is currently broken), and the linux-image-lowlatency kernel.
  Jackd and Ardour seem to work (I've got a lot to learn about both of them!) with the alsa package, but when I select freebob, it crashes immediately.  Several messages - one asking if raw1394 is loaded(yes), another about permissions(could not get 1394 handle: Permission denied, and 'Could not create virtual device'.
   I have a friend with a Presonus Firepod, which he will allow me to use for testing before I buy my own, but I haven't borrowed it yet.  Are these messages just the result of no physical device being there?  Or have I got some more things to sort out before I make the trek to his place?

---

### Post by vivichrist on 2007-03-12
Ok
raw1394 by default belongs to the disk group.
and you don't have permissions to use this file if you do not belong to the disk group.
you can either add the same limit.conf stuff for disk and add yourself to the disk group to get realtime permissions.
or as I did make raw1394 permanently audio group.
through ... I think it was /etc/udev/rules.d/40-permissions.rules? ... you should already be in the audio group

---

### Post by heimo on 2007-03-30
vivichrist: Did you have to compile any software to get Firebox working on Feisty? I'm planning to buy either Presonus Firebox or Edirol FA-66, and I'm using Feisty. Thanks!

---

### Post by leleobhz on 2007-03-30
> **heimo said:**
> vivichrist: Did you have to compile any software to get Firebox working on Feisty? I'm planning to buy either Presonus Firebox or Edirol FA-66, and I'm using Feisty. Thanks!

Try install with edge packages....

---

### Post by vivichrist on 2007-04-01
heimo

nay all software was from the ubuntu feisty repository.

---

### Post by heimo on 2007-04-02
> **vivichrist said:**
> heimo

nay all software was from the ubuntu feisty repository.

Excellent news, thank You very much!

---

### Post by vivichrist on 2007-04-10
although there have been many updates since I last used jackd -d freebob. Idont really have time to  do recordings. many thank to my crap job. so status may have changed for better ... or worse ...?

---

### Post by demonsi on 2007-04-24
Hi, 
I finaly decided to liberate my self of the curse of winXP, migrating to the all mighty ubuntu 7.04.
I was before using Cubase SX3 with Guitar Rig 2 as VST with an EDIROL FA-101, everyting worked fine with that setting, but i since hate windows and microsoft and propriety in general, I wanted to get to an open source alternative,  giving a shot to ardour2.

So, i managed to install all the above even if i'm still a newbe to linux, thanx to the synaptic package manager and then learned a few basic bash commands. I figured that if the FA66 is working then the FA101 should too, i saw on a forum that a guy managed to make it work, but does not tell how... But still, i can't get it to work yet.. here what it says when I start JACK with freebob as the drivers:

[INDENT]loading driver ..
Freebob using Firewire port 0, node -1
showDevice: not implemented
FreeBoB ERR: FREEBOB: Error creating virtual device
cannot load driver module freebob
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via gettimeofday
required capabilities not available
capabilities: =
new client: freebob_pcm, id = 1 type 1 @ 0x806e450 fd = -1
new buffer size 256
starting server engine shutdown
freeing shared port segments
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
no message buffer overruns
cleaning up shared memory
cleaning up files
unregistering server `default'
17:27:13.465 JACK was stopped successfully.
17:27:13.499 Post-shutdown script...
17:27:13.500 killall jackd
jackd: aucun processus tuÃ©
17:27:13.638 Could not connect to JACK server as client. Please check the messages window for more info.
17:27:16.794 Post-shutdown script terminated with exit status=256.
cleaning up files
unregistering server `default'
17:15:34.851 JACK was stopped successfully.
17:15:34.853 Post-shutdown script...
17:15:34.853 killall jackd
jackd: aucun processus tuÃ©
17:15:35.070 Post-shutdown script terminated with exit status=256.
17:15:36.049 Could not connect to JACK server as client. Please check the messages window for more info.[/INDENT]

When I start gscanbus, i can see that my EDIROL FA101 is detected.

any clues? thanks for your gratefull help.

---

### Post by vivichrist on 2007-04-28
did you usr qt jack control gui or ....?
and if so what were you settings

i.e I had to specify hw:0 or hw:0,0 and not "default" for the interface

also number of inputs and outputs had to be specified to get my firepod to work

---

### Post by demonsi on 2007-04-30
alright, i think it was it, i used hw:0 as insterface and in the connect tab, now i can see all ins and outs in jack
i can only get realtime in root access, but thats okay for me

now i think ill do some readings to get the good connections settings in ardour2, thanks a lot!
:)

---

