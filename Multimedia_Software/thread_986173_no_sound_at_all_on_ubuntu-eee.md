---
title: "no sound at all on ubuntu-eee"
date: 2008-11-18
forum: Multimedia Software
---

### Post by davidstern on 2008-11-18
Dear Ones

I did read and search allready in the forum, but couldn't discover a hint for my particular problem yet. It's about ubuntu on an eee (ubuntu-eee 8.04, which I guess is an adapted hardy), it's not about no sound after resume/standby, it's about no sound at all. Strange thing: I tested against a live version booted from the SD-card and in comparison to the installed one I do get audible sound signal testing whatever device in the Sound dialog.

I quit Xandros because I couldn't fix an error message with the keyboard layout altough I tried for about 8 hours.
Now I have ubuntu-eee 8.04 (hardy) running on my eee 900 (latest BIOS), so far so good, I updated, installed additional software and all of a sudden, I realized there is no sound. I tested with several applications, the Sound and Multimedia dialog in the Settings, it's surely not muted, according mixers and display it's almost fully up, but whatever soundsystem I choose for playback, there is nothing to hear when I click on "Test".
It took me around a 16h day to get this distro set up and configured. After I recognized the no-sound-problem I've runned the riceeey-Script, but personally/manually not done any audio-related editing and no other deep tweaking yet. I had also uninstalled eee-control and replaced with eee-config again to see whether it makes a difference. Seemingly not.

kernel is 2.6.24-21-eeepc which must be the one that installs as the distro's default.



This is what my screen looks like:


[img]http://print.kikireon.com/mastervolume.png[/img]



In what log-file did you find these lines? All the logs I searched on my eee900 had no entry with "alsa", strange enough. The service alsa-mixer-utils is marked active in the gui service control.This is what my screen looks like:


[img]http://print.kikireon.com/master.png[/img]



All the logs I searched on my eee900 had no entry with "alsa", strange enough - where would I find information about the loading of the modules? The service alsa-mixer-utils is marked active in the gui service control.

I very deeply appreciate any help!

Thanks.

David

---

### Post by davidstern on 2008-11-19
I got it solved, I tried with the sticky guide, but everything looked ok so far and I gave up reading through those 1xx pages of posting.
Chose the other hard way: reinstallation, more than once.
Two things I was suspecting:
-an effect of the riceeey.sh-skript that was designed for 8.0.4.0 and not especially for eee 900
-a result of one of the packages from the system update

Instead of running the riceeey.sh-script, I would rather recommend this one: [http://eee.ricey.co.uk/index.php?name=F](http://eee.ricey.co.uk/index.php?name=F) … c&t=18
which is a eee 900-adjusted modification thereof.

When I installed ubuntu-eee 8.0.4.1 again I had sound, just after applying the riceeey-script and all the suggested updates plus reboot, I lost it again.

After reinstallation, I went through the system update recommendations more carefully, there was a package linux-ubuntu-moduls-2.6.24-21-eeepc, I unchecked it before doing the update, runned the modified riceeey-script mentionned above and had sound again.

I think it might be an imcompability with this newer module.

To facilitate a reinstallation, I created a list with my installed packages

    dpkg --get-selections | awk '!/deinstall|purge|hold/ {print $1}' > packages.list

and reinstalled them with

    xargs -a "packages.list" sudo apt-get install

---

### Post by Azyx on 2008-12-19
I uninstall eee-control and reinstalled eeepc-config. It worked and I hope this help for more than now.

---

