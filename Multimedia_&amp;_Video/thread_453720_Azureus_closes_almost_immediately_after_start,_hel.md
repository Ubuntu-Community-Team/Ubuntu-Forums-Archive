---
title: "Azureus closes almost immediately after start, help?"
date: 2007-05-24
forum: Multimedia &amp; Video
---

### Post by rainwalker on 2007-05-24
I want to create a torrent of a movie I have to send to a friend, so I installed Azureus through Synaptic.
When I start Azureus (Applications -> Internet -> Azureus) the startup window comes up, with the progress/loading bar, then it shows the language selection window, but right after that window appears the whole program just closes. Bang. Just like that.
It happens every time.

My friend just told me it's a java-based program, is this true? If so, would this guide that I used to install FrostWire have changed some important Java configuration: [http://www.ubuntuforums.org/showthread.php?t=305337](http://www.ubuntuforums.org/showthread.php?t=305337)

---

### Post by PilotJLR on 2007-05-24
Yes, it is Java based, so you need a JRE. You probably have that, since you can at least get a splash screen.

Leave what you have now intact, and download this:

[http://prdownloads.sourceforge.net/azureus/Azureus_2.5.0.4_linux.tar.bz2?download](http://prdownloads.sourceforge.net/azureus/Azureus_2.5.0.4_linux.tar.bz2?download)

Then extract Azureus2.jar and move it to /usr/share/java/

---

### Post by rainwalker on 2007-05-25
I have to have permission to extract it there, what's the terminal command to extract somthing?

---

### Post by rainwalker on 2007-05-25
Or can I just extract the Azureus2.jar thing on my desktop and COPY it there (because I do know the command to copy)?

---

### Post by fenian on 2007-05-25
Run these commands...

> rm .azureus/.lock
rm .azureus/logs/*.log
rm .azureus/logs/save/*

Azureus should then be able to start up.

---

### Post by rainwalker on 2007-05-25
what directory do I have to be in when I do that?

---

### Post by fenian on 2007-05-25
just open a terminal and enter those commands.

---

### Post by rainwalker on 2007-05-25
ok, just a sec...

---

### Post by rainwalker on 2007-05-25
Nope, it still closes right after the language selection window comes up

---

### Post by fenian on 2007-05-25
Download the file  llisted above and extract to your desktop.Then run this in a trminal to copy the jarfile to the right place (I am assuming your username is rainwalker,if its not replace rainwalker wityh your username..

> sudo cp /home/rainwalker/Desktop/azureus/Azureus2.jar /usr/share/java/

---

### Post by rainwalker on 2007-05-25
Ohhh, so I just copy the .jar! This whole time I thought I had to actually extract it there (just figured out you don't extract jars, oops)

Thanks, I'll try that now

---

### Post by rainwalker on 2007-05-25
I got 4 warnings (it didn't close though, w00t!)
> Azureus did not shutdown tidily. Check for diagnostic log files and consider reporting them to the Azureus team if this is the result of an application error. Also check the Wiki (see the Help menu) for 'Azureus Disappears'
> The following ports have been changed to avoid UPnP device problems: Incoming Peer Data Port (TCP/58112) [old port=20616] Incoming Peer Data Port (UDP/62058 ), UDP Tracker Client Port (UDP/62058 ), Distributed DB (UDP/62058 ) [old port=20626]

> SWT library loaded from "/usr/lib/eclipse/plugins" can't be automatically updated from version 3235 to 3318 (must be loaded from "/home/<username>/.azureus"). Please see the wiki for details.
> UPnP: Mapping 'Incoming Peer Data Port (TCP/58112)' failed

What do these mean?

---

### Post by rainwalker on 2007-05-25
Well it all seems to be working, I'll post any probelms I run into

---

### Post by jackmc on 2007-05-26
When this happened to me, I uninstalled Azureus, then reinstalled via their webpage. There was a known bug I think. Good to see you fixed it though :)

---

### Post by squee on 2007-06-13
if you do get anymore problems try this

Running these commands will allow azureus to start again...

Quote:
rm .azureus/.lock
rm .azureus/logs/*.log
rm .azureus/logs/save/*

i got it from here
[http://ubuntuforums.org/showthread.php?t=435935&highlight=azureus+shutdown&page=2](http://ubuntuforums.org/showthread.php?t=435935&highlight=azureus+shutdown&page=2)

the thread deals with a different problem but it solved this one for me.

Good luck!

---

### Post by seek3r on 2007-06-27
Great post, fixed me up twice. Thanks.

---

