---
title: "sound issues and audacity problem"
date: 2005-11-22
forum: Multimedia &amp; Video
---

### Post by porsher_puddles on 2005-11-22
i have been using ubuntu for about 3 months and i had heaps of problems, but with help on the forums and reading lots of threads i have nearly everything working fine, except an issue with Audacity when i start it up it comes up with an error something like io can't initialise sound system, i read the threads and i'm not alone, but as yet i can't find the answer.
i also have another sound issue on games like frozen bubble no sound or on battleships and many other games, yet system sounds music, vids are all fine.
In audacity when i go to preferences there are no sound devices to choose any ideas?

---

### Post by porsher_puddles on 2005-11-22
ii'm going to answer my own question here as i have found the answer
: How to configure sound to work properly in GNOME?

   1. Read General Notes
   2. Read How to add extra repositories?
   3.

sudo killall esd
sudo cp /etc/esound/esd.conf /etc/esound/esd.conf_backup
sudo gedit /etc/esound/esd.conf

   4. Find this section

...
auto_spawn=0
spawn_options=-terminate -nobeeps -as 5
...

   5. Replace with the following lines

auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default

   6. Save the edited file (sample)
   7.

sudo apt-get install libesd-alsa0
sudo gedit /etc/asound.conf

   8. Insert the following lines into the new file

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

   9. Save the edited file (sample)
  10.

sudo ln -fs /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

  11. System -> Preferences -> Sound
  12. Sound preferences

General Tab -> Sounds for events (Un-Checked)

  13. Save and close all opened applications, Reboot computer

hope this helps someone

---

