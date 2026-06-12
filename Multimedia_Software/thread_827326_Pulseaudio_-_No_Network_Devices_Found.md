---
title: "Pulseaudio - No Network Devices Found"
date: 2008-06-12
forum: Multimedia Software
---

### Post by chiefchief on 2008-06-12
I'm trying to get pulseaudio on my server working so that any of the workstations in my office can play through the server's speakers.  I can successfully send from the server to the workstations, and from the workstations to each other, but I can't get anything to go to the server.

I followed the pulseaudio wiki for all computers: [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

I've also searched the forums, but could not find similar problems.

The main issue here is, when the Pulseaudio control applet is clicked on, it does not list the server machine as a default server/sink/source.  It does play sound when just the option default is clicked.

Sorry, this isn't the best description.  Tell me if there's any more info y'all need, or screenshots.

Many thanks!

---

### Post by 00arthuryu on 2008-07-04
I have the same problem :(
did you find a solution?

---

### Post by chiefchief on 2008-07-04
No solution yet.  I'm going to do a reinstall of the OS after I backup all my data in the next week.

---

### Post by monstrfolk on 2008-07-05
i have the same problem too...no solution.

---

### Post by JRAlkire on 2008-07-17
I had a similar problem that I fixed by copying the same ".pulse-cookie" too all machines.

---

### Post by 00arthuryu on 2009-05-15
Not sure if you've found out yet, but its to do with the firewall.
Firestarter will block all pulseaudio connections.
so if you have that installed. Uninstall it and install ufw instead.
```
sudo apt-get install gufw ufw
```
then make sure that you enable all connections from your multicasting host. (i.e. the ip address)

---

