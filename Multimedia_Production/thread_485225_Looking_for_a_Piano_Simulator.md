---
title: "Looking for a Piano Simulator"
date: 2007-06-26
forum: Multimedia Production
---

### Post by Onimae on 2007-06-26
Hey guys-

I am currently on the hunt for a decent Linux program that basically simulates a piano. Something to the tune of [KB Piano](http://www.gfsoftware.com/kbp_information.html) for Windows. The only thing I have found so far is Rosegarden but it seemed very complicated to get set up (as in, I couldn't produce any sound with it and wasn't really sure how I should).

If there is anything you guys can suggest, or even anyone who can point me in the direction of getting Rosegarden to work + learning how to use it, that would be awesome. Ideally, I would like to go with option one, as KB Piano was much simpler to use than Rosegarden, and I am looking to find that same simplicity over in happy Linux land :-p.

Thanks for any help-
**Peter**

---

### Post by cryptoguru on 2007-08-09
Hi Peter,

there are a few ways to do this!
It depends how good you want it, how much money you want to spend
and how good you are with linux.

The hard bit! - MAKE YOUR KERNEL REALTIME
You want to make linux run on a realtime kernel.
first install the lowlatency kernel
> sudo apt-get install linux-lowlatency
restart your machine selecting the new kernel from grub
now install module assistant
> sudo apt-get install module-assistant
prepare module assistant to build a new kernel
> sudo m-a prepare
now download the realtime-lsm module and headers
> sudo apt-get install realtime-lsm realtime-lsm-source
now build the new kernel with module assistant
> sudo m-a realtime-lsm
it should build a package called realtime-lsm-blahblahblah.deb
or something like that ;-)
If it doesn't you're probably missing some libraries e.g. gcc or something like
that, although I think m-a prepare should alert you.
Install anything it's complaining for.

install the new kernel module (go to the directory first - usually /usr/src/ )
> dpkg --install realtime-lsm-blahblahblah.deb
restart your machine selecting lowlatency again ...
Now you can run realtime apps on your machine
(you need this to run jack, the sound application, because it makes sure the software and hardware are synchronised so you're not waiting a few seconds after hitting your keyboard for your sound to play)

VST instruments:
1) install jack (i.e. qjackctl)
2) install jack-dssi-host
3) install the latest version of wine with all the development files too
4) get hold of dssi-vst and build according to the readme
    you'll have to get the Steinberg VST headers from their website 
    [http://www.steinberg.de/532+M52087573ab0.html](http://www.steinberg.de/532+M52087573ab0.html) 
    download version 2.3
5) you'll need to set-up the VST_PATH to a suitable directory (maybe ~/vst)
6) download a bunch of VST dlls or buy a good one ([www.pianoteq.com](www.pianoteq.com) - the Receptor version works on Ubuntu) and put them in your vst folder
7) run qjackctl - set the sample-rate to 44100 and buffer to say 128 in the setup part - then hit Start
8) type the following into a terminal
    jack-dssi-host dssi-vst.so:[nameofvst.dll]
replace [nameofvst.dll] with whatever dll you want to use (there are some free ones)
9) Hit the connect button on qjackctl and connect your midi from your keyboard to the midi of your instrument. Check the audio has been connected too from your instrument over to alsa.
10) play away

Obviously nothing's ever as simple as it looks in linux and it may take a while for you to get there, but when you get there it's fantastic!!

Soundfonts:
1) install jack (i.e. qjackctl)
2) install fluidsynth
3) install qt4 
4) install qsynth
5) download as many .sf2 files as you can get your hands on for free
go to [www.hammersound.com](www.hammersound.com), there's loads of piano ones
6) follow step 7 from the VST one above (running qjackctl)
7) run qsynth
8) load the soundfont files into the setup in qsynth (just add and browse for them)
9) follow step 9 from the VST one above (connecting midi and audio)
10) play away

Some VST instruments may crash in linux, they are meant for windows and can somtimes go wrong if wine doesn't know what to do, especially with the window graphics.

Soundfonts should work fine all the time.

If you've got any more questions I'd be happy to help as much as I can.
I'm assuming you have a decent understanding of linux to follow the above steps, please ask if you get stuck ... I know how annoying it is!

Stu

---

### Post by contactMW on 2008-03-28
Stu,

Please could you let me know if I need to follow your advice for my problem also:

[http://ubuntuforums.org/showthread.php?t=736845](http://ubuntuforums.org/showthread.php?t=736845)

I've played-around with various settings in Jack CONTROL and makes no difference to the Rosegarden-only latency.

Really appreciate your help,

Martin

:confused:

---

