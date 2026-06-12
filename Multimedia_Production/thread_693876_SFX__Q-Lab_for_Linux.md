---
title: "SFX / Q-Lab for Linux"
date: 2008-02-11
forum: Multimedia Production
---

### Post by mpc350 on 2008-02-11
After much browsing, I am fairly sure that there is no linux app that can approximate what SFX or Q-Lab do.  I would love to find someone who is willing to create a program that can cue sound files and midi commands.  This is not similar to various sampling and drum machine or DJ applications, and this is not an editor like audacity.  This is for live sound show control.  I need to be able to fade cues in and out, start at various points within a file, have a choice of output routing options.  It needs to be low latency.  Triggering needs to be by keyboard commands or midi messages.  I need the ability to accept multiple file types (ogg, wav, aiff, mp3, aac, etc...up to 96kHz 24 bit).  The Linux platform because of it's sturdiness and configurability would be perfect as a show control device.  As a model, I really like how Q-Lab (available for mac as freeware at [www.figure53.com](www.figure53.com)) works extremely well, but is not portable to Linux.  Can someone please help.  For me, this is a long term solution.  I work as a sound designer in live theater and currently use Windows and OSX for show control and manipulation, and am not looking at a quick fix app that partly does what I need.  I understand this may take a while for development, and I would love to help in any way that I can, but currently know very little about creating software.   If you would like to help me out, please contact me directly at [email]sound@pcpa.org[/email]

Thank you 
Matt Carpenter
Director of Sound
PCPA Theaterfest

---

### Post by Steveway on 2008-02-11
I didn't look at your applications but I can do everything you said with IDJC except for the part with keyboard-strokes or midi messages (no clue what midi has to do with the whole thing) but I didn't really look into that since that is not really needed with IDJC.
You can find .deb files for it in the thread in my signature, but I'm not sure if the workaround for Skype still works since much changed in the sid-packages.
(But since you didn't mention Skype that doesn't apply to you.)

---

### Post by mpc350 on 2008-02-11
The midi cueing is important because lighting consoles and digital mixing consoles can spit out a midi program change message and that can be used to cue the sound playback device.
I'll check out IDJC like you mentioned.

Thanks,

Matt

---

### Post by gorgon on 2008-02-22
You might want to have a look at pure data (pd) or supercollider. Although you wrote that you don't have much experience creating software, pd at least is quite easy to get around. I've made small apps to run theater plays where I need to play multiple sounds, or manipulate the sound itself during the play. Also, both got a nice community around them, and I bet there are some making patches (/apps) for theater sound who would like to share experiences or code. You would have to use the same samplerate though, afaik.
Good luck, and do post if you find anything - Q-Lab looks very smart indeed!
[http://puredata.info/](http://puredata.info/)
[http://supercollider.sourceforge.net/](http://supercollider.sourceforge.net/)

---

### Post by IanW on 2008-02-23
Could [this]("http://www.salemradiolabs.com/soundpanel/") be what you're looking for?

---

### Post by prismatic7 on 2008-02-25
> **IanW said:**
> Could [this]("http://www.salemradiolabs.com/soundpanel/") be what you're looking for?

It's close, but no cigar - SoundPanel is designed for radio work, so it lacks the complex layering and fading that a theatre soundie needs.

---

### Post by reaby on 2008-05-26
Hi, as a fellow sound engineer i was also looking for sfx replacement for linux and stumbled my way to here. but after some looking i found one - named tttrigger. it doesn't come with ubuntu repoisities, but it's easy to install as it doesn't need compiling, just make sure you got right libraries installed.

program can be found at [http://sourceforge.net/project/showfiles.php?group_id=145131](http://sourceforge.net/project/showfiles.php?group_id=145131)

you need to have working kde installation or core libraries and jack in order to run program. also you need libgc, which ships with hardy and libsoundfile, that has to install. all can be found with search on synaptics.

be sure that jack is running.
Download source and program is allready compiled at /src-folder, it starts just double clicking program name. 

Some preferences has to be made in order to get sound out, but it's all easy. There is no midi support, nor panning / fading automation or support, but it works for summer theater project for me, as it has better controlling environment that minidisk ever has.

-- edit:
for some reason i didn't manage to get sound output - hopefully there is a solution for this.

---

### Post by reaby on 2008-05-26
i got it working, apparently you need to assign output ports for each sample by pressing ctrl and klicking mouse 1 on empty space between none and arrows.

---

