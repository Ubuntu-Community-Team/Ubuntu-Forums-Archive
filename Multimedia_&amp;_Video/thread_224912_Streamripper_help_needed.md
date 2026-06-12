---
title: "Streamripper help needed"
date: 2006-07-28
forum: Multimedia &amp; Video
---

### Post by mauro007 on 2006-07-28
I'm new to ubuntu and I have a problem with streamripper in ripping radio stations.
I open Stramtuner, tune in onto any station and start playing music.
Stramtuner opens xmms and so far everytink is ok.
However, when I press record in order to rip the radio stream the terminal opens and closes almost immediately without recording anything.
Streamtuner and Streamripper are both installed with the latest library,
this is my music folder: /home/mauro007/Music
and this is the string for streamripper
 under the streamtuner preferences:
x-terminal-emulator -e streamripper %q -d /home/mauro007/Music -r -q

Please someone help

Thanks

Mauro

---

### Post by jordilin on 2006-07-28
I always use streamripper within the command line. With xmms you can get the url of the server, then just type:
```
streamripper url
```
and it does the trick.

---

### Post by T700 on 2006-07-28
> **mauro007 said:**
> Streamtuner and Streamripper are both installed with the latest library,
this is my music folder: /home/mauro007/Music
and this is the string for streamripper
 under the streamtuner preferences:
x-terminal-emulator -e streamripper %q -d /home/mauro007/Music -r -q


Try this:  

```
 x-terminal-emulator -e streamripper %q -d /home/mauro007/Music -r
```

Paul

---

### Post by mauro007 on 2006-07-28
> **T700 said:**
> Try this:  

```
 x-terminal-emulator -e streamripper %q -d /home/mauro007/Music -r
```

Paul
I tried with the comand line: streamripper url [http://194.79.31.246:8000](http://194.79.31.246:8000), and I got command not found.

As for the previous solution ie:  x-terminal-emulator -e streamripper %q -d /home/mauro007/Music -r, it didn't work either. it seems terminal just crashes when I try to record any stream from within Streamtuner.

---

### Post by T700 on 2006-07-28
I'm sure you've already checked, but are you *absolutely* postive about that path?  It can be tricky, since in Linux, things are case sensitive (i.e. joe, Joe, and joE are all different).

Paul

---

### Post by mauro007 on 2006-07-29
I checked the directory, and there's no error. I even changed it to /home/mauro007/Desktop but the same thing happens: when I press record from Streamtuner, the terminal appears for a splitsecond and then disappears and nothing happened.
I then did this:

mauro007@Nippur:~$ sudo apt-get install streamripper
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  kstreamripper
The following NEW packages will be installed
  streamripper
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 60.9kB of archives.
After unpacking 176kB of additional disk space will be used.
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe streamripper 1.61.17-1 [60.9kB]Fetched 60.9kB in 0s (60.9kB/s)
Selecting previously deselected package streamripper.
(Reading database ... 88953 files and directories currently installed.)
Unpacking streamripper (from .../streamripper_1.61.17-1_i386.deb) ...
Setting up streamripper (1.61.17-1) ...
mauro007@Nippur:~$

I swear I had streamripper installed!
On the side note, why is the installer suggesting kstreamripper?
Do I just close the terminal to stop the recording?

Thanks for all who helped me
Mauro

---

### Post by jordilin on 2006-07-29
> **mauro007 said:**
> I tried with the comand line: streamripper url [http://194.79.31.246:8000](http://194.79.31.246:8000), and I got command not found.

As for the previous solution ie:  x-terminal-emulator -e streamripper %q -d /home/mauro007/Music -r, it didn't work either. it seems terminal just crashes when I try to record any stream from within Streamtuner.

Substitute **url** by [http://194.79.31.246:8000](http://194.79.31.246:8000). Url was a generic name for [http://194.79.31.246:8000](http://194.79.31.246:8000). Now it will work :D

---

### Post by T700 on 2006-07-29
Glad you got it working.  This stuff can be really frustrating!

Not sure why it is suggesting kstreamripper, but yes, you just close the terminal to end it.

Paul

---

