---
title: "Mixer always mute after reboot"
date: 2008-04-24
forum: Multimedia Software
---

### Post by azebuski on 2008-04-24
This is not really a big deal, but whenever I reboot my system the mixer is always muted and the master volume turned down when I turn the computer back on.

I have to turn the mute off and turn up the master volume every time I reboot.

I just updated to Hardy Heron and this never happened in Gutsy Gibbon.

---

### Post by linko47 on 2008-07-02
Sorry to bring back a non-current thread.

I've had the same problem in debian sid, so I ran

```
alsactl store
```

[http://linux.derkeiler.com/Mailing-Lists/Debian/2005-06/1356.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2005-06/1356.html)

Hope it helps.

---

### Post by MrClearPore on 2008-07-03
Yes.  **alsactl store** will save the current **alsamixer** settings, but if you do not have sound upon rebooting your computer, you'll also need to run the following command:

```
alsactl restore
```

The above command will load the settings that were previously saved with **alsactl store** (which needs to be typed only once).

So here are the steps:
1) open **alsamixer** and set the volumes you want;
2) as root, type **alsactl store**;
3) after booting up, type **alsactl restore**.

If you want to have **alsactl restore** started every time you boot up, you can always add it to your **/etc/rc.local** file (just put the command above the line that reads **exit 0**)

Good luck.

---

### Post by orengolan on 2009-07-13
got the same issue on xubuntu 9.04.

When I type  'sudo alsactl store' I get:
E-core/util.c: home directory /home/yuka not ours.

---

### Post by KittyKatt on 2009-07-13
I was with orengolan in #xubuntu when he was having this problem. I was having it too, recently, so I decided to look into it a little further, and found this...

> ##### WORK-AROUND FOR AUDIO PROBLEM #####
 1.) Manually adjust the mixer settings to something that is a good default for your audio needs. These settings will be loaded every time you restart your computer.
 2.)  Change the file permissions for /var/lib/alsa/asound.state to enable read/write access for the group/others (open the folder in Thunar, then right-click the file, select properties, and go to the Permissions tab). If you don't do this, then the next step will give you a permission denied error.
 3.) Open up a terminal and enter the command "alsactl store" (without the quotes). This stores your mixer settings in /var/lib/alsa/asound.state for later use.
 4.) From The Xubuntu/Xfce menu, go to Settings and open Sessions and Startup. Go to the Application Autostart tab and click the Add button.
 5.) Enter the command "alsactl restore" (without the quotes) and the name and description of your choice. This causes the "alsactl restore" command to automatically run when you start your computer. The command restores you mixer settings from /var/lib/alsa/asound.state where you saved them earlier.
 I'm going to click "Problem Solved" instead of "I Still Need an Answer" because even though this is a work-around and not a true solution, it is sufficient for my needs, and I no longer need an answer.


Original Post:  [https://answers.launchpad.net/ubuntu/+question/68564](https://answers.launchpad.net/ubuntu/+question/68564)

I tested this in my XUbuntu, and it worked perfectly. My sound is no longer muted.

The above is basically the same as MrClearPore's solution, except for the fact that CyrusCT mentions the need to give the group "others" read/write permission to the file /var/lib/alsa/asound.state, which is why orengolan got the error they did. I gave that permission, ran the "sudo alsactl store" afterwards, and it worked just fine. Put a "alsactl restore" command in my Startup Applications, rebooted, and my sound was not muted upon boot.

I hope this helped! ^-^

---

### Post by raboofje on 2009-07-14
> **orengolan said:**
> When I type  'sudo alsactl store' I get:
E-core/util.c: home directory /home/yuka not ours.

The problem here is 'sudo' changes the current user, but not the environment (like the 'current home directory' $HOME).

Perhaps simply try running it without 'sudo'? If you really require root, the '-H' switch looks useful.

---

### Post by orengolan on 2009-07-14
yeah, it was a permissions issue. 
this solved it:
sudo chown 777 /var/lib/alsa/asound.state


thanks!

---

### Post by matmbl on 2009-10-22
> **orengolan said:**
> yeah, it was a permissions issue. 
this solved it:
sudo chown 777 /var/lib/alsa/asound.state


thanks!

Most helpful thread, solved my issues but the following command will provide all users r/w access to the file (correcting the above)

sudo chmod 666 /var/lib/alsa/asound.state


Matt

---

### Post by ProDigit on 2009-10-26
Alrighty!

On Xbuntu9 the following order applies:

1- In the terminal:
> sudo chmod 666 /var/lib/alsa/asound.state
2- set volume level
3- In the terminal:
> alsactl store
4- In the terminal:
> sudo mousepad /etc/rc.local
Mousepad is a text writer. It can be replaced by others like 'nano' (without bracklets) if you prefer those.

5- Exit mousepad (nano, or text editor)
Reboot Linux to test.


Just a question, do we need edit a certain script to run or enable rc.local, because within the file there's written:
"In order to enable or disable this script just change the execution bits."

With the 'execution bits' do they mean just to type a line, or do they mean to enable the loading of this file in another file?

---

### Post by Elviswind on 2009-11-13
I'm now running Xubuntu 9.10 and had the sound muting problem, but I was also suffering from crappy sound . . .  high frequencies did not sound correct.  I tried the edit to /etc/rc.local and that sort of worked to correct the muting problem, but the sound was still crummy.

What I found was, and I think this will work better in Xubuntu than other Ubuntu, that removing Pulseaudio solved all the problems.  

Look at post #4 in this [thread]("http://ubuntuforums.org/showthread.php?t=1313253") and give it a whirl.  Note: Becuase I'm running Xubuntu I didn't need to follow the last couple steps to install another mixer program . . . the one included with Xfce still works just fine.  :p

---

### Post by im.wayfarer on 2009-11-20
Instead of changing permissions, you could also just open up a root terminal, which is present by defaults in the Ubuntu "System Tools" menu.

Then you can type "alsactl store" and Ubuntu will not bark at you.

If you don't have a root terminal menu selection, then open a regular terminal and type: sudo gnome-terminal.

---

### Post by ProDigit on 2009-12-07
> If you don't have a root terminal menu selection, then open a regular terminal and type: sudo gnome-terminal.

Can't you simply open a normal terminal and write:
> sudo alsactl store

?

In Xubuntu gnome-terminal does not work, and I believe some people purposely disable gnome services and remove gnome based programs that don't work in Xfce (or KDE)

---

### Post by Puzzled Guy on 2009-12-15
There is a better way to set the "alsactl restore" to execute on startup.

Just go to System>Preferences>Startup Programs and add the command there.

It worked for me! ;)

---

### Post by johnmsmith on 2010-02-01
After upgrading to 9.10 from 9.04 I experienced this "mute" problem.

The procedure in post #5 fixed it :D
Thanks folks!!!

---

### Post by kayaman_00 on 2010-02-10
Thank you very much KittyKatt :D

---

### Post by kickwin on 2010-12-27
> **johnmsmith said:**
> After upgrading to 9.10 from 9.04 I experienced this "mute" problem.

The procedure in post #5 fixed it :D
Thanks folks!!!

Same situation. Post#5 fixed it. Thanks fellows.

---

### Post by David006 on 2011-11-16
Still getting this, but only on some PCs, after install of Ubuntu 11.10 (Oneiric).


No known fix, that doesn't just re-occur.


STILL investigating ..

---

### Post by David006 on 2011-11-16
see also:

speaker trouble after update to 10.04 (dell inspiron 1545)
[http://ubuntuforums.org/showpost.php?p=11464210](http://ubuntuforums.org/showpost.php?p=11464210)

Muting and Sound
[http://ubuntuforums.org/showpost.php?p=11339943](http://ubuntuforums.org/showpost.php?p=11339943)

---

