---
title: "Streaming sound over the network"
date: 2009-08-14
forum: Multimedia Software
---

### Post by smbm on 2009-08-14
Hi

I've recently silenced my Ubuntu running server so can stand to have it in the same room as me when doing stuff.

What I plan is to connect it to my amp and speakers and have the output from audio apps piped over the network so I can have one less connection to my laptop when working.

Does anyone have any ideas about the best way to go about this?

I've very little experience in this sort of thing.

Any help gratefully received.

Cheers

---

### Post by efgevh on 2009-08-14
pulseaudio is excellent for this. Ubuntu 9.04 comes with Pulseaudio and you should only need some minor tweaking to have that going.

Perhaps start by installing some extra pacages, typing in a the terminal
sudo apt-get install padevchooser
sudo apt-get install ubuntu-restricted-extras

try and restart pulseaudio by issuing
service pulseaudio restart

System --> preferences --> sound

Select pulseaudio sound server for everything excepty for the default mixer tracks where you select your sound card

Test that you can play music on the system

In application --> sound & video 
look for pulseaudio device chooser
click it and check off to start this app on system boot
ricght click the puseadudio icon in the panel and select "configure ..
tick of all the network options to have other computers be able to detect the this computer

same routine on other computer

possibly now on yuor laptop your sound box will be available in the pulseaudio menu under "default sink". If you select it music played on lappy should be heard on stereo.

---

### Post by Choobie on 2009-08-16
Are you running this off of the server or desktop edition of Ubuntu (i.e. command line only or GUI?)

As far as playing music, you could set up MPD(music player daemon) and then use a program such as sonata on other computers and sonata will control mpd that is on your server which is connected to your sound system. See their website: [http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki](http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki)

MPD is in the repositories (sudo apt-get install mpd mpc).

To address the title of your thread, you can stream over a network using a program such as icecast or web app like Jinzora or ampache.

Also if you are running Ubuntu Server Edition I am fairly certain that you will need to install other packages, I am about to create a post asking about that so I will put a link in here to that thread after I make it. Its funny that you ask this because I am about to do the exact same thing ;)

Edit: Here is my thread on server sound, in case you run into any problems maybe someone can come and help us ;)

---

