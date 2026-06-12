---
title: "Cubase 4 working ubunto"
date: 2010-09-09
forum: Multimedia Software
---

### Post by Subdepth on 2010-09-09
hey people, iv got a working version of cubase 4 on ubunto... i cant seem to select my fast track sound card though was wanderin if anyone could offer any help?

It works fine with my midi keyboard, i can select the insider vsti's and vst's and make sounds (altho with great latency due to it using my onboard asio card instead of my external m audio)

Iv got wine...wineasio....reaper...and jack installed (altho i have very little idea what im doing with them) and iv read up alot about using jack as a way to use your sound card but as you can tell im a bit of a n00b to all this linux stuff and id appreciate any advice you guys can give me! 

im running the beta version of ubunto btw

Thanks in advance...

---

### Post by Subdepth on 2010-09-09
k now iv been messing around with jack i can see it in the device menu next to ASIO FULL DUPLEX but it says no hardware found or device already in use when i select it...

If you are experienced with jack or could just offer any help it would be really helpfull, i really want to continue making music with cubase on ubuntu as i have deleted my vista partian to make a deep end start in ubunto!

cheers everyone!

---

### Post by cchhrriiss121212 on 2010-09-09
Hi,
What you need to do is select the fast track as your interface under the jack setup window. According to another recent thread you should put "hw:Pro" as the selected interface.
Shut down any other programs that are using audio before trying to start jack. If jack is still not running, then post the output of the message window and what settings you are using.

---

### Post by Subdepth on 2010-09-09
im not entirely sure what you mean by changing the interface? and hwoew? iv been trying this all day haha sorry. would a screenshot be more helpfull? i cant see m audio/fast track as a selection anywhere on jack... 

Thank you for the reply!

---

### Post by cchhrriiss121212 on 2010-09-09
Open up qjackctl, then click to open the setup window. On the right there is a box that says - 
Interface:(default)
If you click on the drop down list you should see options like hw:0,1 etc. If the fast track is listed there then you can simply type in hw:Pro (if it is not listed then we will have to go back a few steps).

---

### Post by Subdepth on 2010-09-09
iv now selected hw:o as my interface, as its not a fast track pro im using so that isnt a selection... i also ran some script in terminal ealier wich informed me im correct in thinking my m audio is under 0 of the 4 audio choices on my setup.

However i am still *experiencing the hardware found / already in use error when ever i select m audio asio in cubase... extremely frustating as iv been working toward this all day!

---

### Post by Subdepth on 2010-09-09
it isnt listed as obviously as fast track, but i read in a forum ealier that hw:0 is your setup 0 choice wich happens to be my m audio according to some script i ran in the terminal ealier, does that still count?

Also, my pc recognises the m audio fast track  in the little speaker icon in the top right hand corner, but just not in cubase or jack >.<

cheers for your help!

---

### Post by cchhrriiss121212 on 2010-09-09
Sorry about that, I assumed you had a Pro for some reason. To find out what it is listed as, you can put aplay -l into a terminal window. Could you paste the output of aplay -l here? 
I ask because hw:0 is usually your onboard soundcard, and USB cards will show up with other numberings.
When you say jack does not recognise the fast track what do you mean? Do you see the fast track listed under the drop down interface menu?

---

### Post by Subdepth on 2010-09-10
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Track [Fast Track], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


OK now im confused, does that mean it has to be hw 2? 


im not sure how to attatch images here without uploadin them to my ftp (wich i havnt got a software on ubuntu for yet) so ill try it like this...

Inteface: hw:0,0
              plughw: 0
              hw:0
              /dev/audio
               /dev/dsp

hope this gives you a clearer idea!

THanks alot for your efforts mate!

---

### Post by Subdepth on 2010-09-10
also when i clikc the > button i get the list:

hw:0 HDA Intel

hw:0,0 ALC 662 REV1 Analog

hw:0,1 ALC 662 REV 1 Digital

hw:1 Digital Camera

hw:2.0 Fast Track

hw:2.1 USB Audio

hw:3.0 MIDI instrument

---

### Post by cchhrriiss121212 on 2010-09-10
That looks OK, so what you need to do is select hw:2,0 as your interface, then start jack. You should be able to get <10ms latency.
The thing about using a USB card is that if you unplug it and use another port, it may show up as a different number like hw:3, which will confuse jack, so keep that in mind for the future.

---

### Post by Subdepth on 2010-09-10
i do select the interface properly, then when i open cubase when i try to select m audio asio it gives me the error message that its already in use or not working... this is whats confusing me?

---

### Post by cchhrriiss121212 on 2010-09-10
What you need to do is get jack running first. I don't know enough to help you with using Cubase in wine, but I do know a bit about jack. 
So is jack running OK with the fast track? 
Could you show what error messages you are getting?

---

### Post by Subdepth on 2010-09-10
ok i understand, i will show you as much info as i can concerning jack.

This is me running in 

Sever path - Jackd

Driver - Alsa 

Interface - hw:0 Fast Track (the hw's keep switching round from 0-2 as far as i can tell)

---

### Post by Subdepth on 2010-09-10
forgot to post the messages haha!

 jackdmp 1.9.6
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 2
 audio_reservation_init
 Acquire audio card Audio0
 creating alsa driver ... hw:0|hw:0|256|3|44100|0|0|nomon|swmeter|-|32bit
 Using ALSA driver USB-Audio running on card 0 - M-Audio Fast Track at usb-0000:00:1d.1-2, full speed
 configuring for 44100Hz, period = 256 frames (5.8 ms), buffer = 3 periods
 ALSA: final selected sample format for capture: 24bit little-endian
 ALSA: use 3 periods for capture
 ALSA: final selected sample format for playback: 24bit little-endian
 ALSA: use 3 periods for playback
 [COLOR=#999933]15:02:42.595 Server configuration saved to "/home/subdepth/.jackdrc".[/COLOR]
 [COLOR=#999999]15:02:42.596 Statistics reset.[/COLOR]
 [COLOR=#999999]15:02:42.602 Client activated.[/COLOR]
 [COLOR=#9999cc]15:02:42.603 JACK connection change.[/COLOR]
 [COLOR=#cc9966]15:02:42.606 JACK connection graph change.[/COLOR]

---

### Post by cchhrriiss121212 on 2010-09-10
That looks fine to me. You said earlier in the thread about using Reaper as well, does that work with wineasio?

As a side note have you considered using any native programs? If you are going to use Reaper as a VST host, then you could use Ardour or Qtractor as a multitracker.

---

### Post by Subdepth on 2010-09-10
im not quite following... My end aim is to be able to use cubase with m audio fast track, so that there is no delay when i am making music and the audio quality is better.

repeaer works fine with the asio duplex driver, as does cubase minus the latency issue, hence why i want it to work with fast track.

i guess what i am unsure of now is what is JACK connecting to?... what is it full stop?
its working and apparantly its working with my fast track, but i have no idea how to enitiate that with cubase, or what is wine? wine configoration is a completely different ballgame

is cubase working through wine? when i select wine asio as a driver it dosnt work at all... im so unclear about things and despite litrelly spending the past 2 days searching for info i am still unclear.

cheers for the help!

---

### Post by cchhrriiss121212 on 2010-09-10
Cubase is a Windows program, and you are using Ubuntu which does not run Windows programs. WINE is a program that allows you to use programs designed for Windows in Ubuntu. The problem is that they do not always run perfectly. So yes, Cubase is running via WINE.

Jack however, is designed for the Ubuntu/Linux platform. Jack is a sound server, and it allows you complete control over where your audio is routed. It is a great tool once you get used to it.

When I mentioned native programs, I am referring to programs that were designed to run with jack and Ubuntu (unlike Cubase). If you tell me what you use Cubase for, I could suggest some native programs that might be able to do the same thing for you. They will obviously run better, and be easier to set up as they are working in the environment they are designed for.

I know you said you already deleted Windows, but I should say there is no advantage to recording music on Ubuntu if you are going to use Windows programs for everything.

---

### Post by Subdepth on 2010-09-10
ok, i am very set in my cubase ways tho haha! 

I basically produce electronic music, but if there was a DAW on ubuntu that could do the following i would be willing to learn it:

Use outsider vsts, preferbly ones like NI Massive and Izotope ozone that run on mac and windows, but i have recently read they will work in linux.

Preferbly work with my m audio fast track (altho if it wasnt a big cpu hog then as i dont currently record instruments into my pc then it wouldnt be a problem just being able to run under a decent ammount of vst/sample pressure untill i can afford a soundcard that has a linux patch)

anything else would just be a bonus to be honest. Although i am quite bummed i couldnt get cubase to work =/ im sure someone alot smarter then myself will come along with a patch sooner or later!!

---

### Post by cchhrriiss121212 on 2010-09-10
VST support on native linux programs is shaky at best. 
But - Reaper running through WINE is said to work very well, which would cover your VSTs. Then you could use Ardour (a native DAW) as a recording program at the same time. I think the reason Reaper works so well is because it is a simple program, and I think Cubase is somewhat more complex.  
Compatibility with the fast track is not an issue, as you already have jack running with it, and every linux pro-audio program will be routed through jack.

If you are set on Cubase then you should either switch back to Windows, or be prepared for some tinkering. Seeing as you are already using Ubuntu, it would be a shame not to try out some of the things it has in the repos. My highlights: Hydrogen (drum sequencer), Phasex (synth), Bristol (synth), Qtractor (DAW) and rakarrack+guitarix (guitar fx/amp modeling).

If you want to try and set up Reaper as a VST host, try posting a new thread in the [Studio forum]("http://ubuntuforums.org/forumdisplay.php?f=335"). There is a regular poster there who goes by sgx that can help you out.

I think that is about all I can help you with, so I hope it has been useful. Don't be afraid to ask for clarification on anything posted here.

---

### Post by Subdepth on 2010-09-11
OK i will try your suggestions. I am pretty set in cubase but i am willing to give reaper a try as it looks to be better then the Linux daws (no offence if anyone disagrees).

Are you saying that repear will automatically work through jack? or that the linux daws will work auto with jack? thats the only bit im confused on really.

Thanks alot for your help man, and i hope someone reading this eventually will provide a solution to my origional problem, as its a shame for me to have cubase 4 working perfectly on my ubuntu maverick but with no access to my external sound card.

Thanks again and happy ubuntuing! =]

---

