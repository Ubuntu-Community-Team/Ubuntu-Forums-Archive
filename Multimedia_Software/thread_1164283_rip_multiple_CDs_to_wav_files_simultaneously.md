---
title: "rip multiple CDs to wav files simultaneously"
date: 2009-05-19
forum: Multimedia Software
---

### Post by clownschoolphd on 2009-05-19
Greetings,

We're looking to rip ~10,000 CDs to contiguous wav files.  I'd like to build a few machines with multiple CD decks to make this process as painless as possible.  

Does anyone have any experience ripping from multiple drives at once?  Is there an existing software project for this type of action?  It seems to me that it could be scripted with one of the cli ripping utilities.  

I'm happy to go through all the man pages and find the best option but if someone has been down a similar road and has some advice, I'd appreciate the passing on of that knowledge.

thanks!

---

### Post by logos34 on 2009-05-19
> **clownschoolphd said:**
> Greetings,

We're looking to rip ~10,000 CDs to contiguous wav files. 

wow, talk about an industrial-size ripping job!

By using ABCDE cli ripper, and with a few tweaks to your desktop preferences, you can partially automate the process so basically the only input required of the user is to shove the disc in. Maybe a simple bash script would do the rest.

You can also set it for SMP/multicore support to speed up encoding, but you say you only want wavs.

---

### Post by nanonils on 2009-05-28
> **clownschoolphd said:**
> ripping from multiple drives at once? 

Sooo - what exactly _**is**_ the command for multiple CD encoding for ABCDE? 

There are a few comments out there on the web but they are too cryptic for me. I'm trying to get about 1000 CDs converted to MP3, a poor format, I know, but it'll work on my non-hacked iPhone and iPod and since it is a jazz collection, I won't loose much. 

Thanks!

---

### Post by logos34 on 2009-05-29
With the older gnome desktop you used yo bea able to do something like this to speed things up:
> 
$ gnome-volume-properties
	>multimedia tab
		- check 'Play audio CD discs when inserted'
		- Command: x-terminal-emulator -e abcde

In .abcde.conf uncomment interactive mode line:

INTERACTIVE=n

The next time you insert an audio disc, a terminal window will open and ABCDE will run without prompts.

To eject cd when done, uncomment the following line:

EJECTCD=y

As it is now you have to configure the settings in nautilus>edit>prefs>media>cd audio disc

but I don't think it gives you a command-line dialog box, just a choice of cd players (gui).

But with non-interactive mode you won't get cddb track and album info.

There's also a line to specify multicore cpus (smp), but that just speeds up the encoding process (which doesn't make the ripping go any faster)

---

### Post by nanonils on 2009-05-29
Too bad: I have 3 CD drives hooked up to to one computer but I have to go through them sequentially with Rhythmbox. On the upside, it allows me to stick in 3 CDs, choose "extract to library" and walk away for 15 minutes... I was hoping to parallel rip them (as I guess clownschoolphd does).

---

