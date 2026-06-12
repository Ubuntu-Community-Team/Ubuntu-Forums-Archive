---
title: "1st Time Install - No Audio {dell optiplex gx1}"
date: 2006-10-23
forum: Multimedia &amp; Video
---

### Post by mtbrown73 on 2006-10-23
Hello -

I'm new to Ubuntu and linux. Windows admin. learning a new OS. I have installed Ubuntu on a Dell Optiplex GX1 and it does not recognize the integrated audio card. (Crystal Semiconductor - CS4236)

It says at startup that i do not have the appropriate GStreamer Plugins. How do I get the appropriate plug-in for this audio card?

Thanks,

mb

---

### Post by apast2119 on 2006-11-26
I get the exact same error.  Anyone have any ideas?

Ap

---

### Post by Fred Hooper on 2007-01-14
The driver is not correctly identified during hardware startup.

you can type:

sudo modprobe  snd-cs4236


then type:

aplay -l   

this is confirm whether the new soundcard modules has been identified.

---

### Post by zaphoid on 2007-02-25
I found that this does work, but is not permanent.

The thread hear [http://ubuntuforums.org/showthread.php?t=305269&highlight=gx1+audio](http://ubuntuforums.org/showthread.php?t=305269&highlight=gx1+audio)

shows how to make the stick.

Copy and past from that thread

[I]Run terminal: Click: Applications/Accessories/Terminal
In terminal type:
sudo gedit /etc/modules
enter your password

append line to end of modules file:
snd-cs4236
save and reboot system[/I]

It great that I have no idea what I am doing, but am successful at it.  My Dell Optiplex GX1 now has sound :guitar:  audio.

---

### Post by ravishankart on 2007-10-23
:popcorn:

Great

Thanks, that works for me too!

---

### Post by Tyler D on 2007-12-25
Just wanted to add that Zaphiod's post worked for my GX1 too.

---

### Post by ShockDC on 2008-05-31
I just wanted add that this worked for me, BUT I, for some reason did not have the terminal program.  I went into run, typed in msconfig.exe and this pulled up the configuration panes.  I put the command snd-cs4236 at the bottom of the auto.bat pane, closed and rebooted.  If it had not been so late in the evening, and for fear of waking up my entire household, I would have shouted for sheer glee when it rebooted with sound!  

This machine was a gimme without any manuals, CD's or anything, so this thread was a godsend.  Thank you everyone who worked on this thread.  You rock!!!  :guitar:

---

