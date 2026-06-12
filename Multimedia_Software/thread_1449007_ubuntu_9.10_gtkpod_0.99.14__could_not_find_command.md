---
title: "ubuntu 9.10 gtkpod 0.99.14  could not find command 'xmms' specified for 'play now'"
date: 2010-04-07
forum: Multimedia Software
---

### Post by larrybalz on 2010-04-07
Ubuntu 9.10 gtkpod 0.99.14 
Notification: could not find command 'xmms' specified for 'play now'

If you do not have rhythmbox installed, go to synaptic to install it or in Terminal run "sudo apt-get install rhythmbox"

gtkpod 0.99.14
Open gtkpod Ipod Manager
Under Menu Tab Edit  --> Preference
Under Music Tab  --> Import & Synchronization --> Click on Commands

Under Playback You should see something like this
Commands for "play now" xmms %s
Command for "Enqueue" xmms -e %s

Change values under the Playback
Commands for "play now" rhythmbox %s
Command for "Enqueue" rhythmbox -e %s

or you can  browse to the execution path of your preferred music player
example for rhythmbox is /usr/bin/rhythmbox

---

### Post by jimbo99 on 2010-07-03
This is not really an acceptable solution as it launch rhythmbox, which is redundant as you already have a library manager loaded with gtkpod.

---

