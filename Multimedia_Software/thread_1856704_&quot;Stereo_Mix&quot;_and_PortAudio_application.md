---
title: "&quot;Stereo Mix&quot; and PortAudio application"
date: 2011-10-08
forum: Multimedia Software
---

### Post by Xelort on 2011-10-08
Hi there people.

I've searched the forum to find a thread talking about this, but i've only found the same responses over and over again, none of them working for my case.

The situation is: i want to access my "stereo mix" (as is usually called on Windows) channel.

What i really want to do is making live radio programs, using this software called BUTT: [http://butt.sourceforge.net/](http://butt.sourceforge.net/)


Here's what i got so far, after lots of tries:

* PulseAudio's monitors can let me record the "wave out" of my sound card. I've tried successfully to broadcast with parec + ffmpeg + ezstream. But the application i need to use works different, i think because of the way PortAudio (not PulseAudio) gets record channels from the system (no idea here).

* When i don't plug a microphone, BUTT gets the system's wave output, exactly as i want, so i can broadcast whatever any of my players may be playing. But if i plug in a mic, BUTT gets only the mic signal, and stops from getting anything else. So, the part i'm missing is the "mix" part.

* Another "symthom" i can see is that i do not listen to my microphone input. That is, when i plug a mic, the VU Metter in any soft for the case moves ok, but there's no sound on the speakers. A few days ago, i saw an option for this on Windows, but none on Ubuntu so far. 

* I've sucessfully fixed this issue on Windows, by enabling "stereo mix" when it's disabled (nasty stuff). So, in order to fix this on Linux too, i need the same solution. However, any place talking about this send me to pavucontrol, and alsamixer, and audacity or parec or Ubuntu's sound recorder application. There's nowhere any "mix" option, no "stereo mix", and my application does not appear in the "recording" tab of PulseAudio's volume control in order to change its input stream. 

* I DON'T WANT to use any other recording or broadcasting software, even  when i know there are plenty of them. This software is perfect for my organization: muti-platform (already compiled), free software, extremely easy to use, it lets me change all the configurations i need, it lets me record the broadcast to make podcasts, and works great. I'm working on a project of  collective internet radio, and users are mostly newbies on computers;  they will never read any tutorial about anything, and even if they do  they will mostly not understand it. Most softwares for this are console based, or privative, or lacks funcionalities, or are hard to install, and most of them only work on a single platform (users may have Windows, or Mac, or  Linux). So this software is perfect for my organization, except for this  "stereo mix" ONLY problem; i want to fix the problem, not change the software. 

* I COULD modify the software, but first need to understand what's going on beetween PulseAudio, ALSA, and PortAudio. I bet there's an easyer solution for this.


Well, that's almost all. It happens on two machines of mine: a desktop with a Realtek ALC889A, and a netbook with an ALC269. I got Ubuntu 10.04 on both, netbook remix on the little one.


Any help will be appreciated, thanks.

---

### Post by Xelort on 2011-10-09
bump

---

### Post by kakyoism on 2011-10-09
I have the same question.

May I know how you got the soundcard output (stereo mix) through portaudio?
I'm pretty new to portaudio and doesn't have any clue how to access the soundcard output.

---

### Post by Xelort on 2011-10-11
> **kakyoism said:**
> 
May I know how you got the soundcard output (stereo mix) through portaudio?


Hi there.

I didn't: that's the problem in this thread :P

What i already did is accesing "Stereo Mix" ON WINDOWS, not Ubuntu; once active, the PortAudio application i want to use detects "Stereo Mix" as a valid "input device". That simple.
In order to do that, i'm affraid you'll have to go search on internet, as the procedure is different on every combination of windows version + hardware model. RealTek and SoundMax devices are the most commented.

I don't know how to use PortAudio. I'm about to go and learn PortAudio in order to make a Python application replacing the one linked in the first post, but so far didn't needed to. And i still hoping there's some better solution for this problem :(

---

### Post by Xelort on 2011-10-11
Funny bump: [http://ubuntuforums.org/showthread.php?t=1547694](http://ubuntuforums.org/showthread.php?t=1547694)

That was a nice answer. But the guy has a point: all this RIAA thing (i'm on Argentina, no such organization here, just a bunch of pro-copyright organizations and collective right managers) everybody asumes of Windows... may it apply to Ubuntu too?

I've readed a lot of sites about this "stereo mix" stuff, and some people says it has nothing to do with Microsoft or Windows, but the hardware manufacturers. Some other say it's a Hardware Vendor problem (like HP, Dell, and so on, apparently they are the ones who make custom drivers for other manufacturer's hardware).

Anyone has data on this? 
Maybe i have to edit some driver, like i had to on Windows (for another computer). 

Please people, any comment will be nice. 
Thanks.

---

### Post by StephenF on 2011-10-11
This thread should not go without mentioning idjc.

---

### Post by Xelort on 2011-10-12
> **StephenF said:**
> This thread should not go without mentioning idjc.

Thanks for the answer Stephen.

IDJC was the first software i tried to use for this organization. Windows people used VirtualDJ, and IDJC was a great replacement... on Linux, not Windows. And as you may guess, most people use Windows, i can't go and tell them something like "if you want to broadcast, you gotta install linux".

Also, IDJC brought some install problems, wich, as i said, is not something i want for this project.

I want to get privative and/or cracked software out of the way, like VirtualDJ, and want to use just one cross platform application, like BUTT, without having to make a tutorial in order to get it running.
BUTT is absolutely perfect, except for this "Stereo Mix" stuff.


My other strategy is making a Python broadcaster, with ability to play media playlists. PyAudio should let me do that, and i can use some libShoutCast or cURL or anything like that to broadcast. But it brings new problems, like building libraries on Windows, and a lot of work before having a basic cross-platform app.
The other thing i would do is to modify BUTT, adding reproduction capabilities, and making it mix the mic with its inner playlist. Again, kinda lot of work. Just knowing how to fix "Stereo mix" should be enough to avoid all that.

---

### Post by StephenF on 2011-10-13
> **Xelort said:**
> My other strategy is making a Python broadcaster, with ability to play media playlists.
Python is great but was not created specifically for the job.
[http://savonet.sourceforge.net/doc-svn/quick_start.html](http://savonet.sourceforge.net/doc-svn/quick_start.html)

---

### Post by Xelort on 2011-10-13
Hmmm... very interesting. 
I remember i made a quick reading on Liquisoap's site a few months ago, and said: "too complicated, not what i want". Now i see this:

> 
we have  modules for various languages (OCaml, Ruby, Python, Perl) providing high-level  communication with liquidsoap.And this:

> 
Debian/Ubuntu
Windows
Mac OS X
FreeBSD
Looks like the right tool for the job.

It's a shame that this %&$%& "Stereo Mix" thing doesn't seems to have a simple solution... and the reasons are even worse (privative crippleware, secrecy, licences, criminalization, persecution techniques, rights violations, attepmts to avoid any judicial system, and so on)... we should not let this thing happen. But hell, making this kind of software is fighting that anyway.

Thank you Stephen, your post was very useful. If i ever finish my broadcasting GUI for Liquidsoap, i'll post a link to it here, in this thread.

---

### Post by StephenF on 2011-10-14
> **Xelort said:**
> GUI for Liquidsoap.
There's a GUI for liquidsoap called liguidsoap which I assume to mean a visual programming tool. I'm not a fan of programming with such things but Glade has semantics that are not apparent from looking at the GTK documentation so I think liguidsoap is also worth a look even if it's just to acquire the big picture.

---

### Post by Xelort on 2011-10-14
> **StephenF said:**
> There's a GUI for liquidsoap called liguidsoap which I assume to mean a visual programming tool. I'm not a fan of programming with such things but Glade has semantics that are not apparent from looking at the GTK documentation so I think liguidsoap is also worth a look even if it's just to acquire the big picture.

Yap, i saw liguidsoap yesterday, after reading your post. Didn't understood it though: as you say, looks like a GUI script programming tool, but seems to have an integrated server and playlist manager... don't know for sure. My plan is to take a deeper look at it this weekend. Anyway, making a playlist, mix two input signals, and set a remote streaming server, SHOULDN'T be too hard to design. If li**g**uidsoap turns to be too complicated, i'll use wxPython for GUI cross-platform scripting. 

BTW, my best experience trying to do something like that was with XRC (using a tool called "xrced"). Unfortunatelly, free software still has a lot to do in order to reach Microsoft's tools for visual programming, like the classic vb6 ide, as they're still unintuitive and have a nasty learning curve (IMO). FS is the right thing to do anyway, so that's what i'll do. I also saw Gambas, wich was cool for the case, but it's only for Linux: can't use that.

---

### Post by StephenF on 2011-10-14
If it's just an implementation then your code is almost written for you. :) I think you missed the word assume.

---

### Post by Xelort on 2011-11-20
I have some new data on this topic. I'll post it here because it could be useful for others facing similar problems. I hope my english don't ruin this; please know that i speak spanish, not english.


A few hours ago i successfully configured a computer to work with the build commented on the first post (BUTT, with Stereo Mix, using _**Port**_Audio, not _**Pulse**_Audio). That's the good news: it's perfectly possible.

The trick seems to be: Port and Pulse don't get along, but both of them works well over ALSA. Therefore, i just need to configure "stereo mix" through ALSA, and PortAudio will be able to use it as an input device, without touching any other PulseAudio configuration.

To change that configuration, i went to ALSA mixers: qmix, and later gnome-alsamixer. Bot of them let me state "mix" as an input device.
Also, it's important to set the output of any player to ALSA (instead of Pulse), so it can be in the mix. 

That machine had a U8668G motherboard, wich comes with an integrated AC'97 sound board. Before installing Ubuntu (10.04), it had a Windows XP running, and i checked out if had "stereo mix" on its input devices list. It was there. So, it was there also for ALSA when the time came. Happy ending.

Now i'm with my personal machine, wich has a EX58-UD5 motherboard, and comes with a  Realtek ALC889A sound chip that doesn't seems to have "stereo mix" enabled (when i plug in a mic, it stops recording the master pcm stream and locks on the mic input, as explained on the first post). Maybe it's some of those crippleware sound boards and will have to face another approach in order to get "stereo mix" here; will post any data on this issue here when i have something.


Now, after a few readings, i can let some stuff noted on the thread as backgound information:

* Linux audio is overcomplicated because of different systems working together. There's ALSA, OSS, PulseAudio, JACK, and other stuff, all at the same time in almost every contemporary linux distro. You can get a good explanation of this issue here: [http://www.tuxradar.com/content/how-it-works-linux-audio-explained](http://www.tuxradar.com/content/how-it-works-linux-audio-explained)

* PulseAudio, the (apparently) new (or current) standar system in linux audio, does not have any option anywhere for a "stereo mix" input device, as it works different (monitor streams). So, almost every soul on the internet that wants to use stereo mix on linux is sent to use audacity or soundrecorder or parec (and its aliases), and "configure it with pavucontrol". That, of course, does not apply to people who want to use any non PulseAudio application (BUTT never appears on the "recording" tab of pavucontrol).

* Reading old ~2007 posts in different forums, i saw that there's some kernel module for ALSA called "snd-aloop". Wich, it seems (didn't tried it yet), was used before PortAudio in order to create "a loopback device" (wich i understand is some kind of "fake stereo mix", correct me if i'm wrong). 
I saw recent data of this here: [http://www.sm5bsz.com/linuxdsp/install/snd-aloop.htm](http://www.sm5bsz.com/linuxdsp/install/snd-aloop.htm)
That link explains how to install that module in current Debian (and Ubuntu) distributions.


Now, will search for data of my soundcard and "stereo mix", so maybe i could confirm if it has some way of activate it without any ALSA kernel fix. Otherwise, snd-aloop it is, and one way or another will post the results here.

---

