---
title: "mythtv setup fails - 8.04"
date: 2008-05-07
forum: Mythbuntu
---

### Post by bah1976 on 2008-05-07
I've installed 8.04 from scratch, wiping the drive in the process. (This is my test box)  I am unable to run mythtv-setup to configure the backend.  I did a standard install without changing any of the options (that I can recall)  

If I run the backend Setup from the appilcations menu, I get prompted to close the backend processes, then a MythTV Setup Terminal window flashes, then closes, and I'm prompted to run mythfilldatabase, which shows a brief terminal window that says something about Illegal Instruction (I can't catch it in time)

If I run sudo mythtv-setup, there are a three identical warnings:
(zenity:5779): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap"
followed by a prompt to close the backend, then the teminal says "No /usr/bin/mythbackend found running; none killed."
Followed immediately by the prompt to run mythfilldatabase again, 
followed by the same three Gtk-WARNING errors.

If I run mythfilldatabase myself, it fails with an immediate Illegal instruction.

I think there's something very basic missing, but I don't know what it is or what log to look in.  Can anybody provide any ideas?

Thanks!

---

### Post by andrewc6l on 2008-05-07
You might want to try making sure mythbackend is stopped, then running mythtv-setup.real from the command line. That will let you see the error message. If I had to guess, it would be that you've got a 64-bit machine with a 32-bit binary on it or something like that.

The pixmap error is easy to get rid of:
  > sudo apt-get install gtk2-engines-pixbuf
I'm not sure why pixbuf isn't there by default, but it's not. That doesn't have anything to do with the other error, though.

---

### Post by bah1976 on 2008-05-07
The iso that I have on my windows desktop, that I burned in order to make the myth box, is called mythbuntu-8.04-desktop-i386.iso - that should be the right one, right?  It is an old old processor, I wouldn't be too surprised if it didn't work right under this new kernel.  

If I run the mythtv-setup.real, I get "Illegal Instruction"

I was just browsing through dmesg, and it seems the proc is older than I initially thought.  It's an AMD K6 400Mhz proc from pre-y2k.  I'm surprised it even boots.  Unless there's any other ideas, I guess I have to wait for my new hardware to get here to experiment.

---

### Post by superm1 on 2008-05-08
What CPU do you have?

---

### Post by bah1976 on 2008-05-08
When it boots, it says AMD K6 2 400 Mhz.  I found this link:
[http://en.wikipedia.org/wiki/AMD_K6-2]("http://en.wikipedia.org/wiki/AMD_K6-2")

I'm not terribly concerned, as my new hardware should be here in a day or two.  That's when I'll have to worry about getting it to work...

---

### Post by superm1 on 2008-05-08
> **bah1976 said:**
> When it boots, it says AMD K6 2 400 Mhz.  I found this link:
[http://en.wikipedia.org/wiki/AMD_K6-2](http://en.wikipedia.org/wiki/AMD_K6-2)

I'm not terribly concerned, as my new hardware should be here in a day or two.  That's when I'll have to worry about getting it to work...
That CPU is most definitely not supported.  Sorry.  It was either optimize for the common and later crowd with leaving old stuff in the dust or make it slower for everyone.

---

