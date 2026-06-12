---
title: "can't run ardour gtk2"
date: 2010-06-30
forum: Multimedia Software
---

### Post by iiiicon on 2010-06-30
I can't run Ardour GTK2 in Ubuntu 10.04.

JACK control is open, but sends error messages relating to not being able to connect to the JACK server whenever I try to press play.

Ardour says JACK is running in another user's profile, and I haven't even made it to the program yet. Error message also says audio controls could be messed up.

---

### Post by cchhrriiss121212 on 2010-07-01
Ardour will not run without jack, so as soon as you get jack running Ardour will follow. In order for jack to work in realtime mode (you can run jack in non realtime mode but it will be slower) you need to edit a system file like this:
Open a terminal, paste this:
```
sudo gedit /etc/security/limits.d/audio.conf
```
then paste these lines at the bottom of the file:[FONT=monospace]
[/FONT]> @audio - rtprio 99[FONT=monospace]
[/FONT]@audio - memlock unlimited
Then go to system>users & groups and add yourself to the audio group. Reboot.

Then open jack and press start, if it is not running post the output of the message window.

---

### Post by PRM on 2010-07-02
I had the same problem with Jack being unable to connect to the server. I discovered that in the **Server Path** dialogue I had to change the default value. It defaulted to [COLOR=Blue]/usr/bin/jackd [/COLOR]but I had to use the drop down menu and change it to[COLOR=Blue] jackd[/COLOR]. I had already downloaded the -rt real time kernel and was running that kernel.

Jack settings seem far from obvious to me.

Make sure you read [UbuntuStudioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation") lots of helpful information there and useful links to follow.

However, I am still struggling to get Ardour working right even though Jack now runs. When I record I get occasional clicks. Also Ardour can freeze after several minutes of recording.

Ubuntu 10.04, Sony Vaio laptop PCG FR315 with external USB audio interface Behringer UCA202.

---

### Post by talebinezhad on 2011-08-29
> **cchhrriiss121212 said:**
> Ardour will not run without jack, so as soon as you get jack running Ardour will follow. In order for jack to work in realtime mode (you can run jack in non realtime mode but it will be slower) you need to edit a system file like this:
Open a terminal, paste this:
```
sudo gedit /etc/security/limits.d/audio.conf
```then paste these lines at the bottom of the file:[FONT=monospace]
[/FONT]
Then go to system>users & groups and add yourself to the audio group. Reboot.

Then open jack and press start, if it is not running post the output of the message window.
Thank you it works now !
1. run a terminal :
```
 sudo dpkg-reconfigure -p high jackd
```2.choose "yes"
3.then go to System>>Administration>>users and groups>>Manage groups>>
select "audio" hit properties and mark your name
4.re login

---

