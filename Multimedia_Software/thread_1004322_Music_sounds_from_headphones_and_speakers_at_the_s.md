---
title: "Music sounds from headphones and speakers at the same time"
date: 2008-12-07
forum: Multimedia Software
---

### Post by semyon on 2008-12-07
I have Ubuntu 8.10 and music sounds from headphones and speakers at the same time. What must I do?

---

### Post by Maltaboy on 2008-12-07
Right-click on the speaker icon in your task bar. Then click on "open volume control". From there you can choose your prevered settings.

Regards,

---

### Post by olejorgen on 2008-12-07
[http://ubuntuforums.org/search.php?searchid=52783867](http://ubuntuforums.org/search.php?searchid=52783867) if it's possible to use search urls. (If not search in titles only after "speakers headphones")

---

### Post by Senesence on 2008-12-07
> **olejorgen said:**
> [http://ubuntuforums.org/search.php?searchid=52783867](http://ubuntuforums.org/search.php?searchid=52783867) if it's possible to use search urls. (If not search in titles only after "speakers headphones")

Well, that link leads to a "No matches found" page.

Anyway, I have the same exact problem, and in searching the existing threads I've yet to find a *working* solution.

Here's one of the threads I've looked at:
[http://ubuntuforums.org/showthread.php?p=6321442](http://ubuntuforums.org/showthread.php?p=6321442)

The guy who created the thread claims it worked for him, although I still need some help, because I'm unable to find my device in the file he specified.

If anyone could help out here, I would really appreciate it.

---

### Post by vtired on 2008-12-16
Advanced Linux Sound Architecture - Driver
                ==========================================
                            Configuration guide


Kernel Configuration
====================

To enable ALSA support you need at least to build the kernel with
primary sound card support (CONFIG_SOUND).  Since ALSA can emulate OSS,
you don't have to choose any of the OSS modules.

Enable "OSS API emulation" (CONFIG_SND_OSSEMUL) and both OSS mixer and
PCM supports if you want to run OSS applications with ALSA.

If you want to support the WaveTable functionality on cards such as
SB Live! then you need to enable "Sequencer support"
(CONFIG_SND_SEQUENCER).

To make ALSA debug messages more verbose, enable the "Verbose printk"
and "Debug" options.  To check for memory leaks, turn on "Debug memory"
too.  "Debug detection" will add checks for the detection of cards.
/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz 

Thats what I get when I try to solve headphone speakers problem From here, in a beginners language who can only copy and paste commnds to terminal, what should I do?

---

### Post by SerpicoUK on 2008-12-21
Have you guys solved this yet?

I'm a novice and had the same problem. The solution I used was to edit the alsa-basic file.

You can navigate to it by typing the following into the terminal:

cd /etc/modprobe.d

then edit the file by typing:

sudo gedit alsa-base

After entering your password the file should open in the text editor.

You then need to add a line to the bottom and then save and re-boot you system for it to take effect. Unfortunately, the line to add seems to vary depending on the computer model.

I tried a few for my Sony Vaio SR before finding the one that worked:

options snd-hda-intel model=sony-assamd

What computer do you guys have? You may need to do a wider search to find what model= should be for your computer.

Serp

---

