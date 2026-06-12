---
title: "Recurring Problem with sound on Dell Studio 540"
date: 2009-06-02
forum: Multimedia Software
---

### Post by sictransitgloria on 2009-06-02
**Update** Accepting the risk of sounding like a moron, I'll tell you what was wrong.  The master volume under the volume control icon was muted.  In my defense, though, I typically don't display the master volume control, and it showed that it had sound under the ```
alsamixer -c 0
``` command.  What strikes me as odd is the fact that I never muted this myself.  Either way, I am back to having music!

Hello all.

I used [this]("http://ubuntuforums.org/showthread.php?t=969611&page=1") post and got the sound up and running on my Dell Studio 540 about 2 weeks ago.  The only difference between what I did and the solution was where I saved the ```
options snd-hda-intel probe_mask=1
``` command was in the /etc/modprobe.d/alsa-base.conf.dpkg-new file instead of the alsa-base file (which does not exist on my machine.)  This fixed the sound, but I had to use the two commands ```
sudo modprobe -r snd-hda-intel 
sudo modprobe snd-hda-intel probe_mask=1
``` to get the sound to work after every time I turned on/restarted my computer.

So I got ambitious, and sought a way to make the computer execute these commands automatically.  I tried three ways - putting the commands in the /etc/modules file, in the /etc/rc.local file, and adding the two commands under System-->Preferences-->Startup Applications.  And this worked for a couple of reboots.  Then the sound would work before I logged in, but not after.

Now, the sound has stopped working all together, even if I erase any changes made to the files and just reset the sound module manually.  My question is thus: has anyone else had this fix suddenly stop working?  Am I doing something wrong?  I guess more generally, how is it that something that used to work no longer works?

I should note, too, that, from the beginning, after typing in the two commands the terminal always output ```
WARNING: /etc/modprobe.d/alsa-base.conf line 1: ignoring bad line starting with 'snd_hda_intel'
``` which I found odd because I couldn't find any line with snd_hda_intel with underscores (only hyphens.)

It's not my speakers (I have a dual boot with Vista on the other side, and they still work for it.)

Sorry that this post is so long, but  I was trying to walk through all of my steps.  If there are any other details you need, please let me know.  I've kept track of all the changes I have made.

Cheers,

-Jonathan

---

