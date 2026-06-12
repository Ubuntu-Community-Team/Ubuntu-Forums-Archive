---
title: "Ubuntu 12.04 Freezes Until Mouse Move Or Keyboard Interaction."
date: 2013-09-16
forum: Multimedia Software
---

### Post by Steven_Carman on 2013-09-16
Ubuntu 12.04 on Toshiba NB205 (also tried LinuxMint 15 at first), using it as my media player in my car. Seems to be the best support for FLAC and higher sound quality. Anyway, after a few minutes of playing music the session freezes up and the music skips until I open the lid / move mouse / hit a key. This is the case with both Rhythmbox and Banshee in both Ubuntu 12.04 and LinuxMint 15. Fresh install with any available updates from stock repos.

Googled a few suggestions. Modified some line in GRUB, forgot what it was exactly, and removed PulseAudio relying solely on ALSA. Personally I think it's a kernal issue rather than just the media players but any ideas, suggestions, or resolutions will be a HUGE help! I do car shows and this little netbook is perfect for my setup if only I could get it to work correctly.

Toshiba NB205
-Intel Atom
-1 GB RAM
-160 GB HDD

Ubuntu 12.04 & LinuxMint 15

---

### Post by Kirboosy on 2013-09-16
Welcome to the forums!

How much music is in your library? I've seen issues where if you have lots of music (3000+ songs) the music players can crash and become unstable. Also it might be the limited resources in your computer. You might want to have a resource window open and monitor your RAM usage while you are using your music applications. 

Also you may wanna check the power settings on Ubuntu and make sure its not going to sleep or anything after so many minutes of inactivity.


Hope that helps!
~Caboose

---

### Post by Steven_Carman on 2013-09-16
> **Caboose885 said:**
> How much music is in your library? I've seen issues where if you have lots of music (3000+ songs) the music players can crash and become unstable.

Well over 9000. It's good to hear that may just be the problem. I can redirect a lot of the music elsewhere.

> **Caboose885 said:**
> Also it might be the limited resources in your computer. You might want to have a resource window open and monitor your RAM usage while you are using your music applications. 

Also you may wanna check the power settings on Ubuntu and make sure its not going to sleep or anything after so many minutes of inactivity.

RAM and CPU bottoms out. But that may be because the resource monitor stops working when it freezes. I've turned off all hibernate / power save aids. It definitely doesn't seem to be that because it'll freeze.. I'll move the mouse.. and freeze again 1 minute later. Then it won't freeze at all for maybe 30 minutes and start acting up again.

---

### Post by Kirboosy on 2013-09-16
Lets try a different Media manager. Try installing [Guayadeque]("http://guayadeque.org/index.php?p=/wiki/page/Home") (weird name, I know)

You can install it via [Software center]("https://apps.ubuntu.com/cat/applications/precise/guayadeque/")

I'm trying to think of any other players that might be a bit lighter but easy to use...

**EDIT**: Take a look at [Audacious]("http://audacious-media-player.org/"). One of them is bound to suit your taste and work well

---

### Post by Kirboosy on 2013-09-20
I just thought of another suggestion that might help. Since you are using a netbook you might want to try a lighter version of Ubuntu ([Xubuntu]("http://xubuntu.org/") or [Lubuntu]("http://www.lubuntu.net/")) I know reinstalling can be a pain in the butt, however since you have weaker hardware the lighter versions of Ubuntu will run better.

The only other way to get lighter than Xubuntu or Lubuntu would be manually setup your machine with a super light window manager. You could also switch to a featherlight version of linux with an empasis on resource friendly computing.

---

### Post by zombienerd1 on 2013-09-21
I have the exact same issue, same computer model, but I've upgraded my RAM to 2gb and HDD to a 320gb unit.  I posted about it last week.

[http://ubuntuforums.org/showthread.php?t=2173738](http://ubuntuforums.org/showthread.php?t=2173738)

I can add that it happens when playing single songs or videos in VLC as well, and watching videos in Youtube.  Pretty much anything that activates the sound card.  In my thread, I mentioned that I left it "skipping" for several hours, and VLC threw an error, but its advice was useless, as my machine did not have an alternate sample rate.

[COLOR=#000000]---------------[/COLOR]
[COLOR=#000000]Potential PulseAudio version problem:[/COLOR]
[COLOR=#000000]PulseAudio is streaming with an excessive latency. Sound may be lost or quality degraded.[/COLOR]
[COLOR=#000000]to address that issue, upgrade the PulseAudio daemon to version 3.0, or disable the alternate sampling rate in its configuration.[/COLOR]
[COLOR=#000000]---------------[/COLOR]

---

### Post by zombienerd1 on 2013-10-16
Probable Solution found.  2 hours without a skip yet.

Searching for others with the NB204, I came across a post from 2010 referring to 10.10, applied the recommended change, and so far it's good to go!

>sudo gedit /etc/default/grub

Find the line:
[COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[/COLOR]
Change it to:
[COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic_timer clocksource=jiffies"
[/COLOR]
Save file, exit gEdit.
then:
>sudo update-grub
>sudo reboot



From: [http://ubuntuforums.org/showthread.php?t=1619219&highlight=NB205](http://ubuntuforums.org/showthread.php?t=1619219&highlight=NB205)

> [COLOR=#000000]try adding "clocksource=jiffies nolapic_timers" to the kernel command line[/COLOR]
[COLOR=#000000]parameter.[/COLOR]

[COLOR=#000000]sudo pico /etc/default/grub[/COLOR]

[COLOR=#000000]change[/COLOR]

[COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/COLOR]

[COLOR=#000000]to[/COLOR]

[COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapci_timer clocksource=jiffies"[/COLOR]

[COLOR=#000000]save changes[/COLOR]

[COLOR=#000000]sudo update-grub[/COLOR]

[COLOR=#000000]reboot[/COLOR]


[COLOR=#000000]sfranzyshen[/COLOR]

---

