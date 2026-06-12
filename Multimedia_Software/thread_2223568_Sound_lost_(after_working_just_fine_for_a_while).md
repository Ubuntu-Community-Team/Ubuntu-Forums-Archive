---
title: "Sound lost (after working just fine for a while)"
date: 2014-05-11
forum: Multimedia Software
---

### Post by chinchulin on 2014-05-11
Hello everybody,
A couple of days ago I installed Ubuntu Gnome 14.04 in my pc alongside Windows 7 and Linux Mint 15. I was really happy to see my Roland Quad-Capture soundcard recognized and working for the first time in Ubuntu! Everything was running just fine: Youtube, mp3, videos,... I even installed Ardour and checked that the inputs of the card were usable too. Well, today I have realized that Ubuntu has gone mute. The card is still recognized in the Sound Settings menu but no sound is coming out of it. I have tried several guides I have found around but to no avail. And, what is worse and more strange, I have just reinstalled and it hasn't solved my problem. Could anyone shed some light here?

Thanks in advance for your time.

---

### Post by ronb19495 on 2014-05-11
does your roland quad have a switch underneath called ext
[http://ubuntuforums.org/archive/index.php/t-1905531.html](http://ubuntuforums.org/archive/index.php/t-1905531.html) take a look here

---

### Post by chinchulin on 2014-05-12
> **ronb19495 said:**
> does your roland quad have a switch underneath called ext
[http://ubuntuforums.org/archive/index.php/t-1905531.html](http://ubuntuforums.org/archive/index.php/t-1905531.html) take a look here

Hi there, Ron. No, it doesn't have a switch. The card worked for a while during the first installation and then, absolute silence. Reinstalling from scratch didn't solve the issue... Weird stuff.

---

### Post by chinchulin on 2014-05-13
I have been taking a look around and found this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)


First suggestion, ubuntu-bug -s audio 

doesn't work. It does work if I use sudo:sudo ubuntu-bug -s audio

In the terminal I get

(process:6869): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed

And a popup stating:

Pulse Audio seems to have crached. Do you want to report a bug?

which I have.



Alsamixer is not found but the command does exist
[IMG]http://i60.tinypic.com/11kgq4w.jpg[/IMG]


Tried running Alsainfo via this page:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

 The info collected is in this link

[http://www.alsa-project.org/db/?f=6f21090aa1ff38319205d386f02a14f8161c7a78](http://www.alsa-project.org/db/?f=6f21090aa1ff38319205d386f02a14f8161c7a78)

Any ideas?

---

### Post by ronb19495 on 2014-05-13
chinchulin looking at alsa output your roland is detected and should work try this in a terminal sudo apt-get install alsamixer when you have installed alsamixer reboot ubuntu then open a terminal again and type in alsamixer you should get alsamixer with something like this screenshot with the name of your sound card or chip.lso I would recomend doing this in a terminal sudo apt-get install pavucontrol.

---

### Post by chinchulin on 2014-05-13
I have Gnome AlsaMixer installed yet. 
[IMG]http://i57.tinypic.com/209rhbl.png[/IMG]
It crashes as soon as I select Edit > Sound Card Properties

Using the command you provide yields the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package alsamixer

---

### Post by ronb19495 on 2014-05-13
try this type in terminal gnome-alsamixer see if you get what I got if you do see if any of the boxes are checked if not do this sudo apt-get purge gnome-alsamixer and reboot then reinstall see what happens

---

### Post by ronb19495 on 2014-05-13
chinchulin how long since you updated ubuntu if you havent updated, update and see if things start working my alsamixer was playing up now after last nights updates it is ok so maybe there was a bug in something to do with sound

---

### Post by chinchulin on 2014-05-13
The program doesn't show. This is what I get:

heidi@heidi-desktop:~$ gnome-alsamixer

(process:2436): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised

(process:2436): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised

(process:2436): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised

(process:2436): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised

(gnome-alsamixer:2436): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion 'instance != NULL && instance->g_class != NULL' failed
Segmentation fault (core dumped)


Removed alsa mixer with your command and rebooted. Tried to reinstall it again with sudo apt-get install alsamixer:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package alsamixer

The system is just updated from this afternoon. First time I installed 14.04 the sound card worked right away.

---

