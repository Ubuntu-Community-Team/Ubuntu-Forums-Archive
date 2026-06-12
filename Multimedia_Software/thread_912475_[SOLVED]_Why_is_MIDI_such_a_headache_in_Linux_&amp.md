---
title: "[SOLVED] Why is MIDI such a headache in Linux &amp;amp; Ubuntu?"
date: 2008-09-06
forum: Multimedia Software
---

### Post by Mark_in_Hollywood on 2008-09-06
About once a year since Breezy Badger, I've tried to get MIDI to do nothing more than playback in/on Ubuntu. It ain't happenin'.

This year (2008), I find some guy who says he's got it working and I get all excited to try it. (I can't seem to learn from my previous mistakes here) ...

So, from Linuxtechie's 'blog:

How To: Ubuntu MIDI Playback with Audacious
**[http://linuxtechie.wordpress.com/2008/01/22/how-to-ubuntu-midi-playback-with-audacious/](http://linuxtechie.wordpress.com/2008/01/22/how-to-ubuntu-midi-playback-with-audacious/)**

I get a warm fuzzy feeling and the next thing you know, my terminal is open and I'm trying his "thing". Boy oh! Boy -- it sure looks good. Not a lot of instructions, etc. So I'm busy getting Audacious in the plug-ins/extras when I have to stop, mid-stream, and get a Sound Font (I'm not a musician, I only want MIDI playback), whatever that is. So, reading further someone has set a link to Fluid3. I download and un-archive that file. I don't know where the contents of the archive are supposed to go, but for my own ease sake, I make a directory called: soundfont. In it goes and then, I discover it's got it's own compressed file format. 

That takes me to another page: sfArk SoundFont Compression
**[http://melodymachine.com/sfark.htm](http://melodymachine.com/sfark.htm)** and while this page is kind enough to offer a method to uncompress the soundfont file, the author gives no model or example of the command line structure to do so. Why? I download the (again) compressed file. It's all of 35 kilo bytes, so is another compressed file really necessary? Then I try to extract it into my soundfont directory. I look in the directory and Lo! and Behold!, the extracted directory has the padlock icon symbol on it. Why? I'm not a computer techie, so I have to find the chown code to make it useful. Again, why has this happened. Nothing is simple as it should be. MIDI is the only place in all of Linux where Microsoft is better. (That does point out how bad MS is, but that's another story).

I try again, and the program to extract the soundfont has been extracted from the compressed directory with the padlock symbol on it. The name of this is:

sfarkxtc

and the file properties show it as an "executable". Does that mean .exe, as in Microsoft? I can't tell. So I highlight the icon and right-click. It offers to open under Wine. I decline that. I'm sure I downloaded the Linux version of this.

More confoundingly, the file name for the Fluid soundfont has a blank space (a touch of the space bar) in the file name. I don't recall how you do that in Linux either. Worse, the explanation of how to use the decompression tools reads:

Installing and removing
Simply copy the contents of the distribution archive to the folder of your choice (typically the "applications" folder).  In addition you may want set sfArkXT to be the "Open with application" used by Finder to open sfArk files.  There are some minor complications here.. see "sfArk File Extensions" below.  To remove the program, simply delete it.

[I]Basic Use
Select a sfArk file to decompress using "File, Open" from the main menu.  Then press "start" to decompress the file.  The uncompressed SoundFont plus notes and license files (if included) will be created in the same directory as the source sfArk file.  Note that decompression may take several minutes if the file is large and sfArk's "maximum compression" mode was used to create the file.  For sfArk's "standard" compression mode, decompression will normally run at around 1 megabyte per second (depending on the speed of your Mac of course).[/I]

Once again, I'm back where I started. 

So, if you are probably the nicest person on the face of God's Green Earth, and have read all the way to here, and still want to help me. Go ahead. I'll try anything. I got into MIDI in Microsoft through VanBasco's MIDI player. Why it's not been ported into Linux I'll never understand. And it won't run under Wine. I've tried for over 3 years with that. Soooooo, if you have time and lots of patience, and you can understand how to get MIDI to work with the above method, kindly let me know how to do that, too.

Looking into Synaptic Pkg. Mgr. I see some soundfonts and such, but as I won't know where they are installed, I won't be able to use Audacious Preferences config to point it at those soundfonts. Yikes. Way to complicated for a non-tech guy.

Thanks, community.

---

### Post by Jack Waugh on 2012-03-04
So, what was the solution?

---

### Post by grey1beard on 2012-03-07
I'm at the same point in the hunt for a _simple_ solution to getting a midi keyboard working in Ubuntu 10.10, and seeing the Solved heading my heart leapt...for long enough to read the thread.
I, too, not a techie, have downloaded lots of software that others recommend, all of which show gui's that are mind-numbingly complex, and with little or no overall picture of how to start.

Is it worth starting a new thread, I ask myself, but no answer came the reply. 
:(

John

---

### Post by grey1beard on 2012-03-07
What for, Frances, just my little rant ?
John

---

### Post by Grenage on 2012-03-07
> **grey1beard said:**
> What for, Frances, just my little rant ?
John

It's a spam account, I wouldn't worry. ;)

---

### Post by grey1beard on 2012-03-07
Thanks Grenage. It's nice to know that at least the thread is being read :)

---

### Post by Jack Waugh on 2012-08-15
Here's what I did to get MIDI playing back from .mid files in Audacious on Lubuntu.

It's August of 2012 and I'm running Lubuntu 12.04 (the Precise Pangolin (on a Pangolin computer from System 76, coincidentally)) with Audacious 3.2.1-2.  This is the version showing in Synaptic for the Audacious package that I currently have downloaded.  I didn't do anything special to get that version; it came with the version of Lubuntu that I'm running.  I mention the specific version of Audacious just because the look of it differs from what some guide out there from 2008 or so shows.

Now are a couple of steps I actually took, but that I do not think are necessary.

sudo apt-get install timidity-interfaces-extra
# Is a separate tool
# that plays MIDI, but does not enable playing from Audacious.

sudo apt-get install audacious-plugins # Already installed?

Here are the steps I took that I think are necessary:

sudo apt-get install musescore-soundfont-gm
# May be smaller than the alternative mentioned elsewhere.

Go into Audacious and from the File menu, open Preferences.  Choose Plugins.
Choose Input, then AMIDI-Plug (click on the row without unticking the box).
Click Preferences on the bottom.
Switch to FluidSynth.
Choose FluidSynth on the left to change its settings.
Click the button to add a sound font file.  That brings up a file navigator;
navigate that to /usr/share/sounds/sf2/TimGM6mb.sf2 exactly.
Maybe up the gain a little in the synthesizer settings (I raised it from .2 to .4).

Having done the above steps, I find I can open a .mid file from Audacious and play it.

---

### Post by grey1beard on 2012-08-15
Hi Jack.
My first reading of your post gives me the impression that you can now play .mid files OK, but does this also mean that this has enabled a midi keyboard ?

Still early in the morning for me, so I'm a bit slow on the uptake till the second cup kicks in ;)

John

---

### Post by Jack Waugh on 2012-08-15
Sorry, grey1beard, but I do not own a MIDI keyboard and so I haven't tested a procedure to get one to work.

---

### Post by Jack Waugh on 2012-08-15
I want to address specifically this quote from the original post: "Looking into Synaptic Pkg. Mgr. I see some soundfonts and such, but as I won't know where they are installed, I won't be able to use Audacious Preferences config to point it at those soundfonts."

In Synaptic, when you are looking at a package that you have installed, you can bring up Properties on the package (right click on the row of text about the package).  One of the tabs in the Properties will list for you the installed files.  The file whose name ends in ".sf2" is the sound-font file, and that's what you have to navigate to in Audacious prefs.

Yes, I know, things are more complex than they ought to be just to get things going.  It would seem reasonable to me if the packagers of Lubuntu would include the smaller sound-font file (referenced in my post above) and pre-configure Audacious to use it.

---

### Post by ads52 on 2012-08-15
Some might be interested to know that a similar procedure will enable midi playback with vlc, but vlc must have been compiled against libfluidsynth. Another hint for the Ubuntu packagers :).

---

### Post by Andrew_P on 2012-11-19
> **Mark_in_Hollywood said:**
> That takes me to another page: sfArk SoundFont Compression
**[http://melodymachine.com/sfark.htm](http://melodymachine.com/sfark.htm)** and while this page is kind enough to offer a method to uncompress the soundfont file, the author gives no model or example of the command line structure to do so. Why? I download the (again) compressed file. It's all of 35 kilo bytes, so is another compressed file really necessary? Then I try to extract it into my soundfont directory. I look in the directory and Lo! and Behold!, the extracted directory has the padlock icon symbol on it. Why? I'm not a computer techie, so I have to find the chown code to make it useful. Again, why has this happened. Nothing is simple as it should be. MIDI is the only place in all of Linux where Microsoft is better. (That does point out how bad MS is, but that's another story).

I went down that dead end, too, while trying to get Rosegarden to work on Lucid Lynx (10.04).  Read more about it at **[http://www.linuxmusicians.com/viewtopic.php?f=24&t=9854](http://www.linuxmusicians.com/viewtopic.php?f=24&t=9854)**.  Unfortunately for us still using GNOME 2 on 32-bit systems, Jeff Glatt's sfArk extractor for Linux was designed for GNOME 3 only, with the executable compiled for 64-bit systems and it hasn't been back-ported for earlier systems.  Fortunately, it turns out that musescore-soundfont-gm, fluid-soundfont-gm and fluid-soundfont-gs are all available from the Ubuntu repositories and you don't need to mess with sfArk.exe, a pathetic piece of proprietary Windows abandonware, or dealing with revising the source code for Jeff's extractor so it can be compiled for GNOME 2.

---

### Post by Jack Waugh on 2012-11-19
Here is the solution I use on Lubuntu 12.04 (precise) 32-bit:

# For playing MIDI:

sudo apt-get install timidity-interfaces-extra # Maybe?  Is a
# separate tool
# that plays MIDI, but does not enable playing from Audacious.

sudo apt-get install audacious-plugins # Already installed?

sudo apt-get install musescore-soundfont-gm # May be smaller than
# the alternative (whatever that may have been).

Go into Audacious and from the File menu, open Preferences.  Choose Plugins.
Choose Input, then AMIDI-Plug (click on the row without unticking the box).
Click Preferences on the bottom.
Switch to FluidSynth.
Choose FluidSynth on the left to change its settings.
Click the button to add a sound font file.  That brings up a file navigator;
navigate that to /usr/share/sounds/sf2/TimGM6mb.sf2 exactly.
Maybe up the gain a little in the synthesizer settings (I raised it from .2 to .4).

---

### Post by Andrew_P on 2012-11-20
Thanks for that information, Jack Waugh!  I was frustrated by not getting MIDI sound out of Audacious until your August 15, 2012 post pointed me in the right direction.  It works for me now.  However, now that I've been playing with it, I don't think the TiMidity++ player as described in your most recent post is needed at all for machines that have FluidSynth installed.  In fact, under AMIDI-Plug configuration, I've selected "FluidSynth backend 0.8b2", then I click on the FluidSynth backend icon on the left of the configuration window to select the SoundFont file(s) and other synthesizer settings.

Only the ALSA backend offers selection of TiMidity, but the ALSA/TiMidity menu path in Audacious doesn't allow one to specify SoundFont files at all.  TiMidity++ does use SoundFont files, but they can only be configured through the text file /usr/etc/timidity/timidity.cfg.  Ugly.

This is what I see in the ALSA BACKEND CONFIGURATION dialog in Audacious:
```
  Port   Client name   Port name
  14:0   Midi Through  Midi Through Port-0
x 128:0  TiMidity      TiMidity port 0
x 128:1  TiMidity      TiMidity port 1
  128:2  TiMidity      TiMidity port 2
  128:3  TiMidity      TiMidity port 3
```

I can get Audacious to play MIDI if I check 128:0 and 128:1, but none of the other options.  After this bit of experimentation, I uninstalled TiMidity++ from my system and deleted the /etc/timidity directory, restarted Audacious and configured it to run through the FluidSynth backend, and it works fine.  MIDI preview in Nautilus still works with TiMidity++ gone.  Moreover, FluidSynth has the Qsynth Qt GUI interface for configuration, whereas TiMidity++ is stuck with its primitive text file configuration scheme.  I suppose that's OK for geeks who want to set up  minimalist GUI-free Linux-based MIDI player machines, but it's not really practical for the average Ubuntu user.

> **Jack Waugh said:**
> 
sudo apt-get install musescore-soundfont-gm
May be smaller than the alternative (whatever that may have been).
The different SoundFont (.sf2) files make the MIDI output sound different, depending on whether the sounds were synthetically created, sampled from real acoustic instruments, the acoustics of the space in which the instruments were sampled, the characteristics of the instruments that were sampled, and so on.  Having multiple SoundFont files in /usr/share/sounds/sf2 is OK, and one may want to choose a different SoundFont file for Audacious to use from time to time, depending on mood.

I happen to have an old Pentium 4 machine running Windows 98SE, equipped with a genuine Creative Sound Blaster Live! Platinum card, and I found that by copying the 8 MB SoundFont file from that system (8MBGMSFX.SF2) to my Linux machine &#8212; an IBM ThinkCentre without hardware MIDI synthesizer &#8212; I can make Audacious sound identical to Winamp on the Windows machine playing through the Creative card, even though in Linux the sound is piped through the FluidSynth software MIDI synthesizer instead of an EMU10K chip on a Soundblaster card.  The Creative file is 7.2 megabytes in size, while the MuseScore (TimGM6mb) file is 5.7 megabytes.  Generally, the better and more realistic the instrument sound samples are, the bigger the SoundFont .sf2 file will be.  The "8MBGMSFX.SF2" file is included on the Soundblaster Live! installation CD, but I've found it on the 'net for free downloading as well, notably from [ALSA open source wiki]("http://alsa.opensrc.org/8MBGMSFX.SF2").

Bottom line:  Since I'm also fiddling with Rosegarden, and Rosegarden seems to work best with JACK and FluidSynth, I'm sticking with FluidSynth as the sole software MIDI synthesizer on my machine for now, although I'll keep the TimGM6mb.sf2 SoundFont file.

---

### Post by Jack Waugh on 2012-11-20
Yes, I was pretty sure that timidity-interfaces-extra wasn't necessary (as I indicated in my comments).  But I still mentioned it, because I wasn't 100% sure, because I didn't happen to test without it.  I'm kind like the cat that knows that an adequate sequence of events for getting food is: observe sign from human that I am about to get fed, approach refrigerator closely, get hit on the nose when door is opened, wait for person to extract food from refrigerator and serve it, chow down.

---

### Post by shantiq on 2012-11-21
another very easy way to play a bunch of mid files


is to go into the directory where they are and enter


> [SIZE="2"]for f in *.mid ; do timidity "$f"; done[/SIZE]

ctrl+c to go to the next
ctrl+z to quit

sadly no pause



**================**

---

### Post by adam s on 2012-12-01
> **Jack Waugh said:**
> Here's what I did to get MIDI playing back from .mid files in Audacious on Lubuntu.

It's August of 2012 and I'm running Lubuntu 12.04 (the Precise Pangolin (on a Pangolin computer from System 76, coincidentally)) with Audacious 3.2.1-2.  This is the version showing in Synaptic for the Audacious package that I currently have downloaded.  I didn't do anything special to get that version; it came with the version of Lubuntu that I'm running.  I mention the specific version of Audacious just because the look of it differs from what some guide out there from 2008 or so shows.

Now are a couple of steps I actually took, but that I do not think are necessary.

sudo apt-get install timidity-interfaces-extra
# Is a separate tool
# that plays MIDI, but does not enable playing from Audacious.

sudo apt-get install audacious-plugins # Already installed?

Here are the steps I took that I think are necessary:

sudo apt-get install musescore-soundfont-gm
# May be smaller than the alternative mentioned elsewhere.

Go into Audacious and from the File menu, open Preferences.  Choose Plugins.
Choose Input, then AMIDI-Plug (click on the row without unticking the box).
Click Preferences on the bottom.
Switch to FluidSynth.
Choose FluidSynth on the left to change its settings.
Click the button to add a sound font file.  That brings up a file navigator;
navigate that to /usr/share/sounds/sf2/TimGM6mb.sf2 exactly.
Maybe up the gain a little in the synthesizer settings (I raised it from .2 to .4).

Having done the above steps, I find I can open a .mid file from Audacious and play it.



Thanks - after a long evening - this worked (almost) first time.
For some reason I just had to install the sf2 file twice.

Adam.

---

