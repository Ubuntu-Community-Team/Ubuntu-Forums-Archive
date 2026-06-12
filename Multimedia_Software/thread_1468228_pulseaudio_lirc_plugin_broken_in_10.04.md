---
title: "pulseaudio lirc plugin broken in 10.04?"
date: 2010-05-01
forum: Multimedia Software
---

### Post by cjlindem on 2010-05-01
The only thing I have found so far which does not work for me after upgrading to 10.04 is the ability to change the master volume via LIRC and the pulseaudio lirc plugin.

LIRC itself is working, I can verify it recognizes my remote control input by using irw, and all other portions of my lircrc file are executed correctly, such as my On Screen Display.  However, no changes are made to the system volume.
---------------------
begin
	prog = pulseaudio
	config = volume-down
	button = Vol-
	repeat = 0
end

begin
	prog = pulseaudio
	config = volume-up
	button = Vol+
	repeat = 0
end
---------------------

I have already reinstalled the lirc pulseaudio plugin to no avail.

Can anyone else confirm if this does/doesn't work on their own system?

Thanks in advance,

---

### Post by damnick on 2010-05-15
i have the same problem.

Is there any solution?

---

### Post by jlenain on 2010-05-22
Hello,

cjlindem, your lirc configuration looks fine.
However, you should add the following at the end of */etc/pulse/default.pa*:

```
load-module module-lirc config=~/.lirc/pulseaudio appname=pulseaudio
```

provided that your configuration for pulseaudio is saved in *~/.lirc/pulseaudio*.

I just post here what is currently working for me under 10.04:

```

begin
remote = mceusb
prog = pulseaudio
config = volume-down
button = VolDown
repeat = 1
delay = 0
end

begin
remote = mceusb
prog = pulseaudio
config = volume-up
button = VolUp
repeat = 1
delay = 0
end

begin
remote = mceusb
prog = pulseaudio
config = mute-toggle
button = Mute
repeat = 0
delay = 0
end

```

Cheers.

---

### Post by forestcomber on 2010-05-24
Hi,

If I could interject with a question...

I am trying this as well with a mceusb remote in Lucid.

What filename and configuration contents goes in the /.lirc/pulseaudio folder ?

Thank-you

---

### Post by cjlindem on 2010-05-24
jlenain, thank you for your post, it helped me finally fix this.

To forestcomber and anyone else, I was also unclear on what to point the config= portion of the code to.  I tried /etc/lirc, and ~/ which are the only two places I know of with lirc configuration files.  When nothing worked, I tried just deleting everything except 

"load-module module-lirc"

Now after a reboot, it is working fine.
I don't remember ever having to manually enable the lirc pulseaudio plugin before..it would be nice if synaptic package manager did it automatically when you install the plugin.

---

### Post by forestcomber on 2010-05-25
Hey Folks,

This is just not working for me ...  Any help would be appreciated !

To review the steps I have taken :

1.  I put this at the end of the /etc/pulse/default.pa :

### Load Lirc for PulseAudio
load-module module-lirc

2.  In Startup Applications I put an item with the command :

irexec -d

3.  In /home/name/.lircrc/lircd.conf I put :

begin
remote = mceusb
prog = pulseaudio
config = volume-down
button = VolDown
repeat = 1
delay = 0
end

begin
remote = mceusb
prog = pulseaudio
config = volume-up
button = VolUp
repeat = 1
delay = 0
end

begin
remote = mceusb
prog = pulseaudio
config = mute-toggle
button = Mute
repeat = 0
delay = 0
end

Volume key presses on the remote still do not control pulse audio.  The remote runs XBMC just fine and the irw command reflects key presses on the remote.

---

### Post by jlenain on 2010-05-28
Hi all,

forestcomber, in fact, irexec will automatically look for the configuration in the file *~/.lircrc* when you launch it.

In my file *~/.lircrc*, I have only something like:

```
include ~/.lirc/pulseaudio
```

and I also have a folder *~/.lirc* in which I put the LIRC configuration for different programs (pulseaudio, vlc, exaile, rhythmbox, ...).

*~/.lirc/pulesaudio* is a file, in which I put the configuration for the LIRC control of pulseaudio. I forgot to say that this file should begin with:

```
#! lircrcd
```

such that you are sure LIRC recognize it as a LIRC configuration.

About the file */etc/pulse/default.pa*, I just left what was already inside and added at the end:

```
load-module module-lirc config=~/.lirc/pulseaudio appname=pulseaudio
```

to link pulse with the LIRC configuration in my home space.

Hope that helps !

Cheers

---

