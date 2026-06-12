---
title: "Audacity freezes when I try to record"
date: 2007-11-24
forum: Multimedia Production
---

### Post by carusoswi on 2007-11-24
Running Ubuntu 7.04.  I can import a wav file into Audacity, and it will play.  I can apply FX, etc.

If I click record, the program freezes.  The only way to shut it down is to force quit.

I've been browsing the forums for a solution, and also checking my sound preferences.  

If I click System->Preferences->sound, then test the Sound Capture item, I receive this message:

gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Resource busy or not available.

I think this indicates the cause of my problem, but I don't know how to go about fixing it.

Suggestions would be appreciated.

Caruso

---

### Post by dabl on 2007-11-24
What are you trying to record?  You need a source for the signal -- "Line In" if it is a microphone or pre-amp playing some media.  And of course you need your ALSA system to recognize that signal source -- Audacity basically takes its cues from ALSA.

Also, Audacity is very picky -- it wants to be the first and only application to use the source device, so don't think of running Firefox or Amarok or something while you are using Audacity -- that won't work.  :)

---

### Post by carusoswi on 2007-11-25
Thanks for the reply.  I have a Tapco 6306 mixer into which I connect balanced mic cords.  I am running one of the line outs of the mixer to the line in on my PCI sound card.  I have played around with the settings under Preferences, and I also have, since my initial post on this thread, played with the Jack Control application.  Selecting appropriate ins/outs in that application seems to have rid Audacity of the messages I posted, and, also, when I click record now, a new track appears and the program starts to record.

Curiously, the program will not playback when I set preferences in the application to match those that I know should be correct.  I have two sound cards, on onboard and the PCI.  All my settings point to the PCI card, but audacity will not playback (gives me the error message to check settings/sample rates) when I select the PCI card in preferences.  If I select OSS: /dev/dsp1, it works.  Of course, I don't know what device dsp1 is.  It is not (I don't believe) my PCI card, as it shows up (and functions otherwise) with a different name.  Only, when I select it in the Audacity preferences dialog, playback ceases to function.

Now that I finally have Audacity running in the record mode, I need to give it a signal to confirm that it really is working.

It looks as though I'm getting closer to getting this ap to work.  Then I can start to play with it and see if it is a tool I can really make some use of.

FWIW, I dual boot (XP/7.04) and have used Steinberg's Wavelab for years, so, on the XP side, I would consider myself knowledgeable (and somewhat spoiled by that flagship, albeit proprietary ap).  

One more, slightly OT question - I am not familiar with the audio file formats native to Linux.  Do these have limitations for sampe rates/bit depth or length/size of the file?

Wav files cannot exceed 2gb.

Just curious.

Caruso

---

### Post by Stochastic on 2007-11-25
If you're accustomed to wavelab and you're knowledgeable with audio I'd personally recommend using a software setup of: Jack, qjackctl, ardour, rezound, jamin, and jack rack as your basic toolkit.  I'm not too familiar with wavelab but the screenshot on their website looks a lot like rezound.  I personally find audacity to be a cumbersome, flaky, un-intuitive editor that I hear more complaints about than praise for - but that's just my opinion.  Typically, once you get jack up and running, recording should be no sweat.


As for your question about native linux file formats, that sounds like backwards win/mac thinking.  Linux can handle many formats quite well and each have strengths and weaknesses.  If you're from the XP world you might just want to stick with PCM WAV files (I've never heard anything about a 2gig size limit) for your exported projects, and save your projects in the program's respective formats to retain as much floating point data as possible.

---

### Post by legend2440 on 2007-11-25
Carusoswi I had the same problem and same error message.using Gutsy
When I uninstalled pulseaudio it fixed my problem and Sound Recorder app starts up without error message and I can now record

---

### Post by dabl on 2007-11-25
My experience recording with Linux is limited to my own hardware platform.  I set up equipment to play a collection of old 78 rpm records and capture them digitally last summer, running Feisty 64-bit.  From the turntable, through a re-equalizer and a pre-amp and into my onboard Intel HDA sound chip.  I used Audacity to do the capturing and basic cleanup, and Gnome Wave Cleaner for some further processing (de-clicking, de-noising, etc.).  Since Audacity is the only Linux app I've used for this purpose, I wouldn't know whether it is clunkier than all the rest, or not. It works -- I set the sampling rate to 48,000, the export format to 16-bit WAV, and everything seemed to work pretty much as expected.  But I did notice that Audacity won't play nicely if any other app has access to the sound system, so you have to shut down other apps to work with it.  :)

---

### Post by carusoswi on 2007-11-25
> **Stochastic said:**
> If you're accustomed to wavelab and you're knowledgeable with audio I'd personally recommend using a software setup of: Jack, qjackctl, ardour, rezound, jamin, and jack rack as your basic toolkit.  I'm not too familiar with wavelab but the screenshot on their website looks a lot like rezound.  I personally find audacity to be a cumbersome, flaky, un-intuitive editor that I hear more complaints about than praise for - but that's just my opinion.  Typically, once you get jack up and running, recording should be no sweat.


As for your question about native linux file formats, that sounds like backwards win/mac thinking.  Linux can handle many formats quite well and each have strengths and weaknesses.  If you're from the XP world you might just want to stick with PCM WAV files (I've never heard anything about a 2gig size limit) for your exported projects, and save your projects in the program's respective formats to retain as much floating point data as possible.

High, Stochastic.  I have Jack, qjackctl, ardour, just installed rezound, no jamin yet, and I have jack rack.

All of these have decent looking interfaces, I just have no clue how to work with them.  I start Jackctrl, played around with settings until I could get it to connect without an error message, then, played a lot more to getting X(something), the red numbers that were incrementing below the "started" message in the window.

So, now I have it started, what do I use those transport controls for at the bottom of the dialog box?  If I click on the "play" button, the dialog flickers briefly, then does nothing.

Do I run these other apps while Jack is running, or what?

As for my comment concerning the .wav file size limitation, it is a known parameter of that format.  Even in XP, if I record a program using settings that cause the filesize (for a given duration) to exceed 2gb, recording will stop.

Wavelab can be set to automatically and seamlessly start another file that can then be combined and dithered to reduce the combined file size.

Since the limitation is inherent to that file format, I would assume that capturing through a linux OS will have no effect.

My question was whether native linux formats (I assume their native since I didn't hear of them until I got involved with Ubuntu) have any file size limitations.  

Any help you or anyone can offer as to how I make a recording in Ubuntu would be helpful.

I have spent the afternoon trying to make this work.  Jack is up and running, I just don't know what to do with it.

Thanks for any advice.

Caruso

---

### Post by carusoswi on 2007-11-25
> **legend2440 said:**
> Carusoswi I had the same problem and same error message.using Gutsy
When I uninstalled pulseaudio it fixed my problem and Sound Recorder app starts up without error message and I can now record

Thanks, legend.  I looked up pulseaudio in the Add/Remove menu.  It is not installed on my system.  Wish it were so that I could remove it to solve my problems.  No such luck for me.

Thanks for trying to help.

Caruso

---

### Post by Stochastic on 2007-11-26
Jack is an audio server, much like AISO on steriods.  Through qjackctl you can connect the output of one program (like rezound or ardour) to the input of another program or to the soundcard.  The transport buttons control the transport of the various apps that have tied into qjackctl so that everything starts, rewinds, plays, etc.. in sync with one another.

I was not aware that wav had the 2gig limitation, I once read the spec for PCM WAV files and I don't remember reading anything about that.  But that's not the issue here.  Which formats are you asking about for linux?  Various different programs handle audio files in different manners.  I'm no expert in this field so doing your own research here would be best.

As for getting a recording going, once jack is started, open either ardour or rezound.  For ardour, create a new session, add a track, select the record function on that track, select record for the overall project, then hit play.  If that doesn't work, check that qjackctl connections are in the right place and that the input section of the ardour mixer has your soundcard in selected.  For Rezound, hit record, you'll get a dialog that will walk you through the rest.

---

