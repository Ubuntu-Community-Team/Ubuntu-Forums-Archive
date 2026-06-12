---
title: "Audio Stuff - Just made the switch from Windows"
date: 2008-01-10
forum: Multimedia Production
---

### Post by ex5bn on 2008-01-10
Hi all.

Gee i love being the clumsy new guy on the forums.

Well, i've just installed Ubuntu 7.10 on my PC, after using Windows XP for several years. I've never tried anything other than Windows, so i'm a little bit out my league when it comes to... everything!

I thought i'd try Ubuntu after finding out about the numerous Open Source Audio programs that are free to use. I've traditionally used Cubase SX on Windows XP, with a Sound Blaster Live! 24-Bit sound card (i think). I would mainly do some composing using the Piano-Roll matrix view in Cubase, and i understand it's possible to do similar things with programs such as Rosegarden and Ardour (but Ardour won't let me "check" it in the "Add/Remove" thingo).

Now, i've gathered i need to use JACK, and this is where my knowledge (or whatever you'd call it at the moment) stops. I have absolutely no idea how to configure my hardware and software to communicate with each other.

Can anyone point me in the right direction? Thanks

---

### Post by orange2k on 2008-01-10
For my music production needs in Linux one of my choices is Energy XT2 which works natively in Ubuntu. But you might want to be able to work with VST-plugs so it is preferable to work on a wine version of the programm and to install wineasio for VST-support.

I havent tried wineasio stuff yet, but you can find a nice tutorial on kvraudio forum in the Energy XT section - here is a link:
[http://www.kvraudio.com/forum/viewtopic.php?t=182682&highlight=wineasio](http://www.kvraudio.com/forum/viewtopic.php?t=182682&highlight=wineasio)

I admit - Ive been quite lazy, so I havent tried it yet - I still use windows for music.:(

edit: in the mentioned tutorial you`ll find many other usefull information and how-tos including Jack and Low-latency kernel stuff...

---

### Post by ex5bn on 2008-01-10
Okay, cheers for the help. I'll give that alook :)

---

### Post by programmer8922 on 2008-01-18
[http://linux-sound.org/](http://linux-sound.org/) 
Seems like it would be a good site for you to check out.

---

### Post by radi0j0hn on 2008-02-09
Can anyone address why ardour cannot be checked for Add installation on some setups?  TIA  John

---

### Post by gtrtx on 2008-02-09
> Can anyone address why ardour cannot be checked for Add installation on some setups? TIA John

Is it only through the Add/Remove that it can't be chosen?  It does have quite a few dependencies that need to be met.  I would recommend trying it through Synaptic or by doing "apt-get install ardour" in a terminal.

I'm using Ubuntu Studio which has it installed by default. I would actually recommend
Ubuntu Studio as it comes with a real time kernel that allows for low latencies when dealing with sound/music production.  Of course you could install RT kernel through Synaptic as well.

---

### Post by nalmeth on 2008-02-10
Perhaps the repositories are not enabled.. In Synaptic you can enable extra repositories. Or edit your sources manually.

Hit alt-F2, and enter:
gksu gedit /etc/apt/sources.list

Remove the number sign (#) in front of the URL's. Number sign's cause lines to be ignored in Linux configuration files. Removing them will allow you to access those repositories.

Now hit the update/refresh in Synaptic, or do this manually via the terminal:
sudo apt-get update
sudo apt-get install ardour2 qjackctl jackd

---

### Post by sodasound on 2008-02-17
In Synaptic, if you look in "Universe" Metapackages, there you will find the "Studio" Metapackages. You can install Audio, Video, Graphics or all of the above plus the desktop. I don't know if you need the desktop, but I have it.

---

### Post by Sandsound on 2008-04-07
> **orange2k said:**
> I admit - Ive been quite lazy, so I havent tried it yet - I still use windows for music.:(

I've made a script that install wineasio 0.7.3 and everything you need to use it in Ubuntu, so now you don't have an excuse for using "that other OS"... ;-)

[http://www.sandgreen.dk/index.php?side=linux_wineasio](http://www.sandgreen.dk/index.php?side=linux_wineasio)

---

