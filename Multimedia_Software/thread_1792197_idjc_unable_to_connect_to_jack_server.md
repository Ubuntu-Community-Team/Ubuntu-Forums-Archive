---
title: "idjc unable to connect to jack server"
date: 2011-06-27
forum: Multimedia Software
---

### Post by dimas869 on 2011-06-27
Hello people, i am using ubuntu 11.04
trying get working Internet DJ Console but i am experiencing problem to connect to the Jack server

i already checked the intructions given in the idjc project webpage, installing the application and configuring the jack

i had already properly set the correct sound card chipset name(snd-hda-intel) on the kermel module and configured to load everytime is boot

installed all the dependecies for jack...but i am still not knowing what i am doing wrong

here i am going to post the info when i try load the application on the terminal:

root@ubuntu:~# sudo echo "@audio   -   rtprio   100" >> /etc/security/limits.conf
root@ubuntu:~# sudo echo "@audio   -   nice     -10" >> /etc/security/limits.conf
root@ubuntu:~# echo "/usr/bin/jackd -d alsa -r 44100 -p 256" > ~/.jackdrc
root@ubuntu:~# idjc
Could not find a suitable language match - will use en_US
Internet DJ Console Version 0.8.4
Copyright 2005-2010 Stephen Fairchild
Released under the GNU General Public License V2.0

Language translation: en_US
jack client IDs: idjc-mx idjc-sc
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
no message buffer overruns
no message buffer overruns
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
JackTemporaryException : now quits...
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
jack_client_close called with a NULL client
something bad happened and IDJC could not continue

update:jun30,2011

i had upgrade ubuntu to ubuntu studio and have pulseaudio interacting with alsa but i belive some how pulseaudio also use a dependency (correct me if i am wrong) call libjack-dev which also use jack, so everything works good withthe other applications as hydrogen, audacity, banshee etc (as also playing one on to of the other) but when i install idjc automaticly install a dependency call qjackctl which replace the one is working and then nothing works no more...no even idjc...so i really want to understand this if is any explanation about it

update july03
i belive i finally manage to connect IDJC to the audio server after replacing jack2 for jack1 in Qjackctl while i was installing pulseaudio

but now all i just dont hear anything from the speakers as a DJ or i cant get to connect myself as a listener with a media player application

why am i getting this?

Toggle ON recieved for signal: Play
player_startup left
song title: Artista desconocido - Pista 13

updated song metadata successfully
Seek time is 0 seconds
not using replay gain
frames 7765
bytes 4099844
toc has been read
player context id is 1

Player has started
[/home/dimas/.pulse/client.conf:1] Unknown lvalue '&#8220;autospawn' in section 'n/a'.

**i guess the last line is what it kills pulseaudio but why i dont see anything about jack?**


i am posting some photos so you can have a visual look of it

**i really appretiate any good advise**

and many thanks in advance

---

### Post by StephenF on 2011-07-02
Reinstall Ubuntu to fix the JACK audio then [follow the instructions here]("http://idjc.sourceforge.net/install_build.html"). Don't try to use the out of date IDJC package.

---

### Post by dimas869 on 2011-07-08
after reinstalling ubuntu from scratch and digging all over

i just find out for some reason even i did install again the whole platform from scratch something was missing in the alsa modules

so i did this:

[PHP]sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update[/PHP]


and then this:

[PHP]sudo apt-get install linux-alsa-driver-modules-$(uname -r)[/PHP]


so maybe someone is quite there but with the same problem as me

oh!...and of course after i could here i was able to properly configure my jack and and always idjc was good

---

