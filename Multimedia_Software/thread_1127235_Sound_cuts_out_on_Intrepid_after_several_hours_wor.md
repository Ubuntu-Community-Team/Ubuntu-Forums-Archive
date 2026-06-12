---
title: "Sound cuts out on Intrepid after several hours working fine"
date: 2009-04-16
forum: Multimedia Software
---

### Post by BuggyBY on 2009-04-16
I run Intrepid on my PC with an Asus A8N32-SLI Deluxe motherboard &#8212; the on-board sound hardware is nVidia CK804, which usually works fine in ALSA ... except that after a couple hours of uptime and working perfectly, it refuses to play anything but PC speaker beeps.

Since I don't normally have constant background music while I use the PC (primarily for IRC and webbrowsing, though I also watch a lot of videos sometimes), I'm unable to identify the exact moment when all sound except the PC speaker beeps stops working. The first warning sign is usually when I load up an online video on a site such as youtube, and the video plays as if muted. The first thing I check, of course, is whether there is any actual muting going on. There isn't, anywhere. I then try to load a sound file in Totem, and discover that the volume regulator in its window is greyed out. :mad:
Being a relative Linux newbie and an immigrant from the wonderful world of Windows, my next instinctive response is to save all my work and browser sessions and restart the system. Voilà, the sound is back after a reboot, but having to open up all my programs again is annoying (especially as those 150-tab Firefox sessions take ages to restore). Plus it's only buying me a few hours before the sound will stop again.

So now, with my headphones in their usual state of silence once more, I turn to this forum for help in how to get sound working again without restarting the system &#8212; and, ideally, how to prevent this issue from ever bugging me again.
Now, like the good forum user that I aspire to be, I read the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") before I started typing up this post. Indeed, I found something quite unusual when I followed the advice to try the command ```
sudo nano /etc/group
``` in a terminal.
There are two regular user accounts on my system. For the sake of privacy, I'll refer to them as *user1* and *user2* &#8212; my own account is *user1*. However, the audio file in my /etc/group file read as follows:```
audio:x:29:pulse,user2
```
I don't know what this "pulse" user is supposed to be, but I assume it's something put there by one of my audio players. I've now amended the line to: ```
audio:x:29:pulse,user1,user2
``` and also installed the alsa-oss package, which seems like a useful thing to have. So far no change in my system's sound behaviour &#8212; do I need to restart for the change to take effect?
It also occurred to me while writing, though after saving the modified /etc/group file, to attempt to open up a sound file in GNOME MPlayer (did I mention I use the Gnome desktop?) rather than totem. When I did, I got this interesting error message:
[IMG]http://img2.imageshack.us/img2/9535/gnomemplayererror.png[/IMG]

I'd be grateful for any solution suggestions. It would be nice to know which processes I may have to end/restart to get sound back in working order without restarting the entire system, for starters.

***Edit:** When I double-clicked the volume control item in the menu panel on the top again just now, the PC speaker (i.e. the only sound currently playing at all) was **muted**. Curiouser and curiouser.*

---

