---
title: "[SOLVED] LIRC (and irw) not working"
date: 2007-11-02
forum: Mythbuntu
---

### Post by de3pc77 on 2007-11-02
Hi-  I am completely new to Linux and decided to start learning by installing Mythbuntu 7.10.  It has been interesting learning how Linux works and so far I have managed to get things working, except Lirc.  I have a Snapstream Firefly remote and am having a lot if trouble with it. I used the ControlCenter to enable the Snapstream remote.  Then I copied my lirc.conf and .lircrc file to the appropriate directories.  I modified the hardware.conf to read [DEVICE="/dev/lirc0"].  The [DRIVER=""], I assume that is correct. 

What I have noticed:
irw does not run, it simply return me to the prompt.  Sometimes I get a "connection refused" message.

What I have found out so far:
"/dev/lirc" does not exist. Do I need this?
I can make irw (and the remote) function properly by creating a /dev/lirc link to /dev/lirc0 [% ln -s /dev/lirc0 /dev/lirc]. Then I need to open 2 terminals and in one run [% sudo lircd -n] and in the other [% irw].  But once I restart my pc, the link is gone and nothing works again.  

Do I need to write a start-up script to create this link every time i reboot?  How have others got their remote to work?  Is this link typical?

I appreciate any help and can provide more info if needed.  Thanks

---

### Post by superm1 on 2007-11-02
> **de3pc77 said:**
> Hi-  I am completely new to Linux and decided to start learning by installing Mythbuntu 7.10.  It has been interesting learning how Linux works and so far I have managed to get things working, except Lirc.  I have a Snapstream Firefly remote and am having a lot if trouble with it. I used the ControlCenter to enable the Snapstream remote.  Then I copied my lirc.conf and .lircrc file to the appropriate directories.  I modified the hardware.conf to read [DEVICE="/dev/lirc0"].  The [DRIVER=""], I assume that is correct. 

What I have noticed:
irw does not run, it simply return me to the prompt.  Sometimes I get a "connection refused" message.

What I have found out so far:
"/dev/lirc" does not exist. Do I need this?
I can make irw (and the remote) function properly by creating a /dev/lirc link to /dev/lirc0 [% ln -s /dev/lirc0 /dev/lirc]. Then I need to open 2 terminals and in one run [% sudo lircd -n] and in the other [% irw].  But once I restart my pc, the link is gone and nothing works again.  

Do I need to write a start-up script to create this link every time i reboot?  How have others got their remote to work?  Is this link typical?

I appreciate any help and can provide more info if needed.  Thanks
Don't start lirc like that.  Use the init script

[B]sudo /etc/init.d/lirc restart
[/B]
This sets up the right device as listed in hardware.conf and such.
If you have errors anywhere in your hardware.conf or you put the lircd.conf in the wrong place it won't work obviously.

---

### Post by de3pc77 on 2007-11-02
thanks for the quick reply!

when I use sudo /etc/init.d/lirc restart i get...
: not foundardware.conf: 5:
: not foundardware.conf: 8:
: not foundardware.conf: 11:
: not foundardware.conf: 14:
: not foundardware.conf: 21:
: not foundardware.conf: 5:
: not foundardware.conf: 8:
: not foundardware.conf: 11:
: not foundardware.conf: 14:
: not foundardware.conf: 21:
Stopping lirc daemon: lircmd lircd.
: not foundardware.conf: 5:
: not foundardware.conf: 8:
: not foundardware.conf: 11:
: not foundardware.conf: 14:
: not foundardware.conf: 21:
starting lirc daemon: lircd.
~$

after this irw still does not work, simply returns me to the prompt.

my hardware.conf file is in /etc/lirc
Any ideas?  Thanks again

---

### Post by superm1 on 2007-11-02
> **de3pc77 said:**
> thanks for the quick reply!

when I use sudo /etc/init.d/lirc restart i get...
: not foundardware.conf: 5:
: not foundardware.conf: 8:
: not foundardware.conf: 11:
: not foundardware.conf: 14:
: not foundardware.conf: 21:
: not foundardware.conf: 5:
: not foundardware.conf: 8:
: not foundardware.conf: 11:
: not foundardware.conf: 14:
: not foundardware.conf: 21:
Stopping lirc daemon: lircmd lircd.
: not foundardware.conf: 5:
: not foundardware.conf: 8:
: not foundardware.conf: 11:
: not foundardware.conf: 14:
: not foundardware.conf: 21:
starting lirc daemon: lircd.
~$

after this irw still does not work, simply returns me to the prompt.

my hardware.conf file is in /etc/lirc
Any ideas?  Thanks again
Post your hardware.conf.  This sounds like a typo in it or possibly in the init script (if you modified that)

---

### Post by de3pc77 on 2007-11-02
I have attached my hardware.conf file. 

The only thing I changed was the DEVICE = "/dev/lirc0".

I didn't modify the init script (at least not that I am aware of).

---

### Post by superm1 on 2007-11-02
Okay here is the deal.

You modified that file in an editor that converted it to a windows format line ending.  I don't know what editor you used, but don't use it in the future for editing files in Linux.

In the future you might consider these command line editors:
nano, pico, vi

Or these gui editors:
mousepad,geany,gedit,leafpad

I'm quite partial to nano for command line and geany for GUI editing myself.


As for your direct problem, you need to use the utility dos2unix.  It's in the package [B]tofrodos.

[/B]```
sudo apt-get intsall tofrodos
```

---

### Post by de3pc77 on 2007-11-02
Are you referring to the .txt extension?  i had to add the .txt in order to attach it in this forum.  Leaving it as hardware.conf gave me an error.  To edit the file in Linux I used Gedit.  Do I need to use the dos2unix utility?

---

### Post by superm1 on 2007-11-02
> **de3pc77 said:**
> Are you referring to the .txt extension?  i had to add the .txt in order to attach it in this forum.  Leaving it as hardware.conf gave me an error.  To edit the file in Linux I used Gedit.  Do I need to use the dos2unix utility?
According to the file you gave me, it contained windows line endings.  That gave me the exact same errors until I converted it.

---

### Post by de3pc77 on 2007-11-02
It is working, thanks for your help superm1!!!!

---

### Post by michwill on 2007-11-08
Hi All,

I'm having a  similar issue.  But a bit of backstory. . .Basically I had an Ubuntu Desktop 6.10 installed running an older version of MythTV I'd installed from source.  Everything was running fine until one day my drive filled up (apparently when you have all your favorite shows slated for "never delete", bad things happen. :P).


Anyway, I wiped the system and started from scratch with Mythbuntu 7.10.  For the most part all things work well, except irw.  I was having the same problem as "de3pc77", but got that taken care of.  Now, however, no remote seems to be picked up by irw.  So that leaves me with  two hypotheses:

1) irw is simply broken in Mythbuntu

2) the IR adapter for my computer was magically physically broken during the software install


. . .as you can see, I'm pretty much left in a terribly odd spot.  Any ideas?

---

### Post by superm1 on 2007-11-08
> **michwill said:**
> Hi All,

I'm having a  similar issue.  But a bit of backstory. . .Basically I had an Ubuntu Desktop 6.10 installed running an older version of MythTV I'd installed from source.  Everything was running fine until one day my drive filled up (apparently when you have all your favorite shows slated for "never delete", bad things happen. :P).


Anyway, I wiped the system and started from scratch with Mythbuntu 7.10.  For the most part all things work well, except irw.  I was having the same problem as "de3pc77", but got that taken care of.  Now, however, no remote seems to be picked up by irw.  So that leaves me with  two hypotheses:

1) irw is simply broken in Mythbuntu

2) the IR adapter for my computer was magically physically broken during the software install


. . .as you can see, I'm pretty much left in a terribly odd spot.  Any ideas?

I can tell you that irw works fine.

If you had the same issue as above, my guess would be that you backed up /etc/lirc and restored it w/ the mythbuntu install.   Check all the other files in that directory for a similar problem.  If that's not the case, open up another thread since this will end up being a completely separate issue.  (I'm trying to keep problems in separate threads so that this forum is more easily searchable without someone having to dig through a 20 page thread on lirc)

---

### Post by michwill on 2007-11-08
My apologies for the confusion, but the only issue I shared in common was the fact that "irw" wasn't working.  It would just return me to a prompt.  Then I got it working (meaning it didn't return me to a prompt, but waited patiently), however, it doesn't recognize input from the IR Remote.  I'm guessing this has something to do with GPIO, but since the new kernel doesn't support it, and the info in this link doesn't seem to work ([https://blueprints.launchpad.net/mythbuntu/+spec/lirc-gpio-alternative](https://blueprints.launchpad.net/mythbuntu/+spec/lirc-gpio-alternative)) I'm a bit lost.

I'd be happy to start another thread, but I see several similar.  No solutions that work for me though.  Keep in mind that nothing has been preserved from past systems.  All drives, etc have been wiped.

---

