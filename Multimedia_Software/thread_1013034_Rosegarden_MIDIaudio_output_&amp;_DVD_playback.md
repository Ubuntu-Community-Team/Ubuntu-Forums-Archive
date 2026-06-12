---
title: "Rosegarden MIDI/audio output &amp; DVD playback"
date: 2008-12-16
forum: Multimedia Software
---

### Post by Roy Nel on 2008-12-16
Hi everyone,

I've always been a Windows user so I'm a beginner to Ubuntu, and although I've managed to get reasonably far with it, there's one issue that's really baffling me.  I'm running Ubuntu 8.04 LTS.

I installed Rosegarden and I cannot get a single sound out of it.  I have an Acer Aspire E571-PB70 desktop PC with a Realtek audio chipset, and it seems to be the only software I'm running that isn't producing sound (Rhythmbox is fine with my MP3s and MID files).  Where in Rosegarden do I set it to output the MIDI and audio to the Realtek chipset?  I've already been to "Configure Rosegarden".

I'm also having big hassles playing a couple of commercial DVDs, trying software like Mplayer, VLC, gxine, Totem - nothing seems to work!  I've downloaded every codec I could lay my hands on.  However, DVDs made with Windows Movie Maker and our DVD video recorder do work.

Please help, guys!  Thanks so much.

---

### Post by kwtm2 on 2009-01-14
I feel your pain!  I got it working, so hopefully this posting can help.  I originally posted it yesterday at
[http://www.linuxquestions.org/questions/linuxquestions.org-member-success-stories-23/setting-up-rosegarden-for-midi-music-in-linux-ubuntu-8.04-697198/#post3408082](http://www.linuxquestions.org/questions/linuxquestions.org-member-success-stories-23/setting-up-rosegarden-for-midi-music-in-linux-ubuntu-8.04-697198/#post3408082)

It took me a long time to set up Rosegarden, the Midi music composer/player software.  Rosegarden would seem to run, load the music files, show the notes and tracks etc.  The ONLY thing I could not do was to get the sound out to my speakers. A kind soul on IRC finally told me how to do it, so I decided to post it here so that the effort would not go wasted.

I use (k)Ubuntu 8.04, but this probably works for other distros, too.

One confusing thing is that the programs kept referring to the JACK software.  Although JACK seems to be versatile and powerful, I still haven't figured out how to use it after spending quite a bit of time on it --and you don't need it to run Rosegarden.  So here's how I did it.

I found out that, like many Musical Instrument Digital Interface ("MIDI") applications, Rosegarden itself does not produce sound, and must tell a separate "midi synthesizer" what sounds to produce.  This "midi synthesizer" can be software or hardware (if you have a sound card with midi).  So the key is to:

1. get a midi synthesizer running
2. install a sound font
2. tell Rosegarden to send the music to that midi synthesizer

_Step 1: Get a MIDI synthesizer running_

You need to install a MIDI synthesizer program.  You can install QSynth/FluidSynth.  (Another alternative not covered here is TiMidity++.)  QSynth is the GUI front-end that lets you easily control FluidSynth, which is the actual synthesizer.  In Ubuntu (and probably most distros), if you install QSynth, it will automatically realize that you need FluidSynth to go with it, and install that program also.  So, either open a terminal and type the command:
**	sudo apt-get install qsynth**
or use Synaptic or whatever program.  Other distros will have their own way of installing the qsynth package.

In a terminal, type the command "qsynth".  This will activate QSynth.  Unfortunately, it will also probably bring up an error message and complain that the JACK software isn't running.  But all you need to do is tell it that you don't want to use JACK, so close the error message windows and:
- click the Setup button on the left (NOT the "Options" button on the right)
- click the Audio tab
- for Audio Driver, select "alsa" instead of "jack".  (This changes the rest of the options on the screen.)

_Step 2: Install a sound font_

You need to get install a soundfont file.  This tells QSynth what each instrument sounds like.  There are various types of soundfont files; the kind gentleman who helped me pointed me to a small basic all-purpose soundfont file that contains the General Midi ("GM") standard 128 instruments.  That file was hosted on his own website, so I won't post the URL link until I get permission.  However, you can also use the Ubuntu package "fluid-soundfont-gm".  This file is about 140MB in size --presumably the instruments sound that much better!  If you install that package, whether using the command "sudo apt-get install fluid-soundfont-gm" or using Synaptic, then the soundfont file will end up at:
	/usr/share/sounds/sf2/FluidR3_GM.sf2
Other distros might put it elsewhere; your package manager can tell you where the file is installed.

If you want to get a soundfont from somewhere else, I was told to try these web sites:
	[http://personalcopy.com/](http://personalcopy.com/)
	[http://personalcopy.com/linuxfiles.htm](http://personalcopy.com/linuxfiles.htm)
or
	[http://hammersound.net/](http://hammersound.net/)

I checked out both sites.  Hammersound seemed to have more specialized sounds that were better as add-ons, but I didn't find a general soundfont file for all-purpose use.  PersonalCopy seemed to be better, but I didn't actually download their soundfont to try, so try at your own risk!

Once you have a soundfont file on your computer, tell QSynth where it is:
- click the Setup button on the left (NOT the "Options" button on the right)
- click the Soundfont tab
- click the Open button, and open your soundfont file

Now QSynth is ready to play your notes.  You just need to get Rosegarden to tell it what notes to play!

_Step 3: set up Rosegarden_

In Ubuntu, you install Rosegarden with the command "**sudo apt-get install rosegarden**" or use Synaptic.  Do whatever the equivalent is for your distro.

Before you run Rosegarden, make sure QSynth is already set up and running.  Now go ahead and run Rosegarden.  If it doesn't appear on your menu, you can type the "**rosegarden**" command at a terminal.

When you run Rosegarden, it will also complain that the JACK software is not running.  Ignore it.  Go to the Rosegarden main menu > Studio > Manage MIDI Devices.  Under "Play devices", you can choose which MIDI device for "General MIDI Device" and "MIDI output system device".  You might need to set up each of these two settings, but it worked for me when I just set the "General MIDI Device" one.  It lets you choose a connection or "No connection".  The available connections will NOT be marked "QSynth" so you have to figure out which is the correct one.  Mine says "128:0 Synth input port" but maybe yours is different.

Okay, that's it!  Rosegarden should now play actual sound to your speakers!  Of course, make sure that your computer speakers are plugged in and the volume is high enough to hear.  Grab a MIDI file or one of the included Rosegarden "RG" files (an RG file is a MIDI file with some added features) and play it to see if it works.

_Some notes_:

I found that when I loaded one of the RG files, it reset the MIDI output to the wrong connection, so I had to go back to main menu > Studio > Manage MIDI Devices > Play devices and change the General MIDI Output device to the right connection again.

Note that if you already have TiMidity++ running in the background, then QSynth won't work properly.  While trying to get Rosegarden working, I ran TiMidity++ once --but after it was done, it stayed running in the background (as root!) and I found that things didn't work any more.  You can check if it's running with the command:
	**ps -ef | grep timidity**
If it comes back with only one line that says somewhere "grep timidity", then timidity is NOT running.  If the response has more than one line, and one or more lines contain the word "timidity" but not "grep timidity", then timidity is running, and you need to use the command "**sudo killall -s9 timidity**" to get rid of it BEFORE you run QSynth.

In the same way, if the JACK software daemon is running in the background, it can make things confusing (since Rosegarden and QSynth will try to use it).  If you know how to use JACK, go ahead.  (And also tell *me* how to use it!)  (And what are you doing reading this guide if you already know how to use JACK?)  Otherwise, you can make sure the JACK daemon software is not running using a similar method:
	**ps -ef | grep jackd**
If it comes back with only one line that says somewhere "grep jackd", then jackd is NOT running.  If the response has more than one line, and one or more lines contain the word "jackd" but not "grep jackd", then jackd is running, and you need to use the command "**sudo killall -s9 jackd**" to get rid of it BEFORE you run QSynth.

Hope that helps!

---

### Post by strangeattractor on 2012-01-05
Thank you kwtm2!  By following your instructions, I was able to hear a midi file play in Rosegarden for the first time.  It still doesn't quite sound right.  It's too slow and there are clicks, so I suspect some sort of timing issue.  But it is playing something that I can hear, and that is quite a relief after spending hours attempting to figure this out.

I'm using Ubuntu 10.04 Lucid Lynx and Rosegarden 11.06 "Don Juan" and the generic kernel (there don't seem to be any low-latency ones available lately.)

---

### Post by shantiq on 2012-01-05
much easier way


```
timidity -iA
```in your terminal    then go to Rosegarden and set

[[IMG]http://img717.imageshack.us/img717/8716/managemididevices006.th.png[/IMG]](http://img717.imageshack.us/img717/8716/managemididevices006.png)

---

### Post by JamesTheAwesomeDude on 2012-12-26
> **shantiq said:**
> much easier way


```
timidity -iA
```in your terminal    then go to Rosegarden and set

[[IMG]http://img717.imageshack.us/img717/8716/managemididevices006.th.png[/IMG]](http://img717.imageshack.us/img717/8716/managemididevices006.png)

What do you mean by "Link port 0 with port 0"? How do I do this?

---

### Post by shantiq on 2012-12-26
click on line on panel on the left where it says port 0 then click on the one on the panel on the right where it says port 0 [the lowest one of the list]


that simple!


then they are connected

---

