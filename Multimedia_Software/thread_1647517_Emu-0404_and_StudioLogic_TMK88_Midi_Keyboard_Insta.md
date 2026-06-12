---
title: "Emu-0404 and StudioLogic TMK88 Midi Keyboard Install"
date: 2010-12-17
forum: Multimedia Software
---

### Post by Clockmender on 2010-12-17
Hi Everybody!

I though I would share with you all my experiences with my recent installation so that others might find all the things I found in one place.

My thanks go to all those who have helped me over many forums (or should that be "fora" given that forum is a Latin word?) so here it is all in one place:

My hardware:

Shop built tower PC with an AMD Athlon processor (2GHz) and 3Gb RAM and on-board Intel sound capability.
ATI Radeon graphics card (RV280 [Radeon 9200 PRO])
E-MU 0404 PCI sound card
StudioLogic TMK88 MIDI keyboard connected to the midi in port of the sound card using midi cable.
Marantz PM5003 Amplifier - Home made Speaker Cabinets with 12" Goodmans Audiom dual cone speakers and Piezo Crystal tweeters. Cabinets are made from 1" chipboard skinned with 20mm Oak

Reason for upgrade to Ubuntu:

My PC was delivered with Wind'ohs XP and worked fine until this year when it started grinding to a halt after about 90 minutes. Causes where all the rubbish in XP now and malware, hacking, etc. My laptop has been running Ubuntu now for nearly two years and works well, so I decided to do the same on my music PC using a dual boot (I had to keep the old system going as my piano tutor arrives every week and expects me to have practised!

Process:

I booted the machine off an ubuntu CD and checked I had sound, graphics, etc. Needless to say the E-MU did not work in this setup so I did a dual install on a 60Gb partition and set to getting the E-MU working. This took some time but the essentials are:

Identify the on-board sound (in my case Intel) so I then blacklisted this in [COLOR="Blue"]/etc/modprobe.d/blacklist.conf[/COLOR] with the line [COLOR="Red"]blacklist snd_intel8x0[/COLOR].

*[COLOR="DarkOrchid"]aplay -l[/COLOR]* gets you the answer!

This ensured that the E-MU was device 0.

I then used Synaptic to download and install the emu10k1 driver. All was well apart from the playback speed for RythmBox - I have a large iTunes library on the Wind'ohs partition and left it there, mounted as a a separate volume under Ubuntu. So I used [COLOR="Blue"]alsamixer[/COLOR] to set the clockrate to 44.1K. Playing my music library now worked.

The midi keyboard required far more effort!

Firstly I tried [COLOR="Blue"]Jack, Jack control[/COLOR], [COLOR="Blue"]Patchage[/COLOR] and [COLOR="Blue"]Phasex synth.[/COLOR] Nothing happened when I pressed a piano key! So I downloaded and installed [COLOR="Blue"]KMidimon[/COLOR] and [COLOR="Blue"]VMPK Virtual Piano[/COLOR] to see what was going on. I noticed I was getting programme changes rather than notes from the TMK88. On advice from others, I used [COLOR="Blue"]alsamixer[/COLOR] to change the clockrate to 48K and behold I got notes instead! - marvellous. Now I could play the keyboard and get sound from [COLOR="Blue"]Phasex[/COLOR].

Having used Fruity Loops, Reason, Cubase, Sonar, Ableton Live, etc on Wind'ohs, I wanted something more in line with these so installed [COLOR="Blue"]LMMS[/COLOR], seemingly the best DAW for Linux unless you know different and if so please let me know here. My first hiccup however was that I could not get LMMS to "see" my keyboard. I have selected [COLOR="Orange"]ALSA Sequencer[/COLOR] as the Midi source and left the device as [COLOR="DarkOrange"]"Default"[/COLOR], little realising that this does not connect the keyboard to any of the tracks, nor can you do this with [COLOR="Blue"]Patchage[/COLOR] as the Midi in to LMMS shows as a RED box that cannot be used. Eventually I found the solution and that is to click on the "Tool" icon on the track, select "midi input" > then the MPU-401 UART item from my E-MU sound card. All works well with the system now and the latency is less than 3 milliseconds!

So all is well, I have found some marvellous sound fonts at:

[http://freesoundvault.com](http://freesoundvault.com)

But beware how many you load at once and how many you have connected to the midi keyboard at any time. An improvement for LMMS would be to have a button on the track to connect to a source selectable in your settings and a disconnect feature as a toggle on this button. I have not yet found a piano quite as good as [COLOR="Blue"]Native Instruments Virtual Grand[/COLOR] or the pianos in [COLOR="Blue"]Reason[/COLOR], but that's being picky and I'm sure one will turn up soon!

I hope this will help some folks along the way and please leave comment here if you need any more information or can add to this.

Cheers

Clock

EDIT

Sustain pedal is NOT being actioned by LMMS. I have checked with KMidimon and the correct data is being sent by my sustain pedal - does anyone have a fix yet? This would seem to be a reported but unresolved bug in LMMS - how can we get this actioned more speedily?

EDIT

I now have a sustain pedal - but not with LMMS. I have installed [COLOR="Blue"]Rosegarden[/COLOR], closed the Jack connection with Patchage and set [COLOR="Blue"]Rosegarden[/COLOR] to install the Fluid Sound Font into the emu card at startup (Edit > Preferences > Midi Tab > Path to asfxload > */usr/bin/asfxload* > Sound Font > */home/alan/Soundfonts/FluidR3_GM.sf2*  Make sure to install [COLOR="Blue"]asfxload[/COLOR] using Synaptic. If you have not got the FluidSynth sound fornt - load it with Synaptic. While you are in the Midi bit set the sequence timer to "EMU10K1 timer" or Rosegarden will bitch about the timer not being accurate enough!

Also make sure that you have the Synth volume up using [COLOR="Blue"]aslamixer[/COLOR], I have put this in my Applications > System menu for ease of use. (Right Mouse Click on the Applications menu > Edit Menus > Type: *Application In terminal* Name: *Alsamixer* > Command: *alsamixer*). The volume is lower than everything else but you can always turn the amplifier volume up!

You will note that I use synaptic to load software, this makes sure all dependencies are taken care of.On the matter of [COLOR="Blue"]Rosegarden[/COLOR] and playback volume, I have found that DSSI plug-ins such as WhySynth, Hextor, XSynth, etc work very well and at a "normal" volume level. I am having trouble getting FluidSynth to work, getting only white noise from it just now and I will report progress here later. I have tried Festige to use my old Wind'ohs VSTi instruments but so far with no real success - again more if progress is made.

I have noticed this post gets a few viewings but no replies - don't be shy - let me know what you think and if you need any more info.

EDIT

More great sound fonts here:

[http://hammersound.net/](http://hammersound.net/)

Enjoy....

Or even try this Wurlitzer:
[http://www.virtualorgan.com/Default.asp?page=58](http://www.virtualorgan.com/Default.asp?page=58)


Update!

Hooray!!!! The soundcard driver for my [COLOR="DarkOrange"]E-MU 0404[/COLOR] seems to have had some updates and cured itself of having to change clock rates to play music and listen to recorded songs, remember you had to switch the clock rate? Well now all works well at the 48000 rate - midi in works and music is at the correct speed - well done whoever did this.

Cheers

Clock

UPDATE!!!!

Well what can I say, I have just upgraded to Ubuntu Studio (fresh install) to get all the advantages of this package. This lost my E-MU card and after three days of trying all the things I did before I could not get the system to see the card although lspci listed it. When I loaded the alsa drivers/firmware, etc. it removed my on-board card as well! Utter frustration followed and I even tried, including the official documentation that said to get various packages from Medibuntu - load the firmware installer and reboot and everything will work - no it did not!!! I was then very p**sed off so in desperation I downloaded Fedora 14 - wrote the image onto a blank CD and booted from it. Much to my surprise and relief it recognised my E-MU 0404 and it worked directly off the CD boot, with no effort other than un-muting it. I then installed Fedora to the disk and it worked again with no loading and compiling various packages and general frustration at having to endlessly f**ny about! So my solution now relies on using Fedora until such times as Bunty can install and recognise my hardware and make it work in under 30mins. Sorry to have to post such criticism and mention of alternative distros but it just worked straight away. I hope Bunty can do the same for me, in which case I will change my music PC back to Bunty, incidentally I have left my laptop on Bunty (Meerkat) in the hope that I will get some message from the dark side that all is well with advanced sound cards and that all you have to do to get them to work is install from an ISO image, so all is not lost - yet.

With regrets at my forced decisions.

Clock

---

### Post by Clockmender on 2012-10-26
**UPDATE!**

Have just tried Bunty 12.04 to see if it would recognise my E-MU sound card, I installed it on a new Sata drive. Still does not want to know my card at all - why is this so difficult? Am I the only person with this sound card who wants to use Bunty as my OS? 

The old problem of clock rates, 44,100 for music and 48,000 for midi returned upon the move to Fedora and persists (I am not entirely convinced they ever went away before). Nobody in the world or Rythmbox, Rosegarden, LMMS, etc. etc. i.e. every music playback or midi instrument package, seem remotely interested in correcting this "feature" Despite I and many others asking for resolution. I have tried a2j (Gna! a2jmidid project), type [COLOR="Purple"]a2jmidid - e[/COLOR] in a terminal to start it and connect instruments in Jack Control to the [COLOR="Purple"]UART[/COLOR] midi connection, to route the midi rather than ALSA but although this makes the Calf and Lash Panel systems work (these will not accept ALSA midi input and the rotary speaker can then be triggered by your keyboard as you play!) it does not cure the underlying problem of incorrect midi codes being passed at 44,100 clock rate. Programme changes are sent rather than key strokes at 44,100 rate.

So some frustrations remain but not many! Incidentally latency values for midi input seem to be better using a2j rather than ALSA midi input and the whole system seems more robust. ZynAddSubFX works much better and Phasex uses much less processing power under a2j. LMMS [COLOR="Red"]still does not action a sustain pedal input[/COLOR] and I have also given up asking for this to be done. I have just loaded MUSE and will report any breakthroughs later, support for Hexter and WhySynth plugins seems good but I cannot find, as yet, a GUI in Muse to control the output from these instruments.

Found a very good piano soundfont - get it here:

[http://www-gmm.insa-toulouse.fr/~guillaum/PIANO/voiced_sfbank.html](http://www-gmm.insa-toulouse.fr/~guillaum/PIANO/voiced_sfbank.html)

and load it into QSynth. I mainly use the "harmo_bjf" version, but both are good.

Just discovered that LMMS will respond to [COLOR="Red"]sustain pedal[/COLOR] codes on ZynAddSubFX instrument only - cannot for the life of me think why all the other instruments do not - this makes playing live a little tricky!

I have also descovered that you can route the midi out from an LMMS instrument into the input of another outside application. So for example if you want to use Phasex inside LMMS, you can simply create a new track with say SFS as the instrument, route you midi in into this track, using LMMS midi control, and your midi out into Phasex (must be running) then turn the volume of the SFS instrument off on the Instrument control Panel and Voila! Phasex works as a LMMS controlled instrument. Just thought I would share this with you!

**D'oh of the year!**

Set Internal Clock rate to ADAT and both playback of music and Midi input work properly! I have set sample rate in Jack Audio Connection Kit Setup to 48000 as well, this may be relevant or not as RythmBox does not use Jack........... I remain confused......

---

### Post by wildmanne39 on 2012-10-27
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

