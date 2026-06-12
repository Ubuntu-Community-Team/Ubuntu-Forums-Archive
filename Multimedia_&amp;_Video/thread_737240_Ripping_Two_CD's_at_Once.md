---
title: "Ripping Two CD's at Once?"
date: 2008-03-27
forum: Multimedia &amp; Video
---

### Post by chazdraves on 2008-03-27
Well, that pretty much sums it up. I just created a fresh install and want to rip about 100 CD's to the HDD as fast as possible. I have two DVD Burners that are up for the task, but Sound Juicer only lets me run one session. I can rip in Sound Juicer and in Rhythmbox at the same time, but the Rhythmbox session goes at about 1/5 the speed of Sound Juicer. Also, I would like a program that (like iTunes) automatically begins ripping and auto-ejects when done. Any ideas?

Thanks, all!
- Chaz

---

### Post by logos34 on 2008-03-27
SoundJuicer is so much faster because cdparanoia is set by default at '8' -- i.e. with scratch repair+ disabled.  (gconf-editor>apps>soundjuicer).

Try Grip or abcde. (grip>config>rip>options>rip on insert, auto-eject).

For abcde, you have to copy the config file .abcde.conf to your $HOME, and configure a few things.  There's a couple of howos in the forums, search for them.  And check the man page.

You can try this little howto I drew up a while back for the auto mode part:
> 
AUTOMATIC MODE

$ gnome-volume-properties
	>multimedia tab
		- check 'Play audio CD discs when inserted'
		- Command: [COLOR="Red"]x-terminal-emulator -e abcde[/COLOR]

In .abcde.conf uncomment interactive mode line:

**INTERACTIVE=n**

The next time you insert an audio disc, a terminal window will open and ABCDE will run without prompts.

To eject cd when done, uncomment the following line:

**EJECTCD=y**

---

### Post by chazdraves on 2008-03-28
Well, I finally had a second to get back to this and I have to say that Grip seems a bit intimidating. I like the overall simplicity of SoundJuicer. Also, I want to convert to FLAC lossless, and I didn't see a default option for that (not that I could properly understand the options anyway. Maybe I have to take it one-at-a-time with SoundJuicer, but that seems a bit silly. Though iTunes won't let you do two-at-once, it at least rips one and starts the next immediately after while auto-ejecting both. I just figured something in Linux would have similar features.

Thanks,
- Chaz

---

