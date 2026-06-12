---
title: "Audio Problems ticking, clicking sounds, freezing and disappearance"
date: 2011-07-15
forum: Multimedia Software
---

### Post by RudyG on 2011-07-15
Hello.

I have the 11.04 installed (see hardware below) and am getting this ticking sound from the moment that Kubuntu boots and you hear the booting sound and until I shut down and it plays the shutdown sound. It doesn't matter whether I watch online audio/video or play my music library. I still hear it. :(
Been trying to find a solution for it for a couple of weeks, but all I've found was other people with same problem but in different releases and with different sound cards. Some describe it as clicking, echo and so forth.  The interesting thing is that if I stop the song while it is playing and then restart it again then sometimes the ticking will go away.

The second problem is, if something is playing and something else happens like an alert will pop up from the OS, or I open a menu of the player. Then the song will simply freeze in that spot, like a damaged CD and will repeat the last noise heard indefinitely.

The third problem happens mostly online, but I thought I'd post it here just in case all of these are related. Anyway, if I play a You tube video and then click on another one. Then the second one will not have a sound. I have to reload that page and then the sound comes in. :(

My sound card is a Turtle Beach Santa Cruz, which reported as a Cirrus Logic CS46xx (14/22/24/30) , KDE SC 4.6.2

Anyone have any ideas?
Rudy

---

### Post by RudyG on 2011-07-17
Hmmm the only solution I'm finding so far is to install a different distribution, like Debian or Mint. :(
Is this really the only solution?

Rudy

---

### Post by juhaszjozsef on 2011-07-18
Try removing pulseaudio and use alsa only and disabling desktop effects. It helped for me...
There is some kind of bug in photon and / or alsa / pulseaudio.
[bug here]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/763065")

---

### Post by RudyG on 2011-07-18
> **juhaszjozsef said:**
> Try removing pulseaudio and use alsa only and disabling desktop effects. It helped for me...
There is some kind of bug in photon and / or alsa / pulseaudio.
[bug here]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/763065")
Thank you very much for your reply.

I've been searching for the past few weeks trying to figure out how to remove pulseaudio but have come up empty. Every place I've found says it is not possible to remove. This is the reason I'm thinking of moving to a Debian distribution, as I'm hoping it will give me an option on whether to install Pulseaudio or not. Do you have a link or a set of steps you used to remove pulseaudio?

Also, before I installed Kubuntu I had Ubuntu 11.04 with Gnome on this desktop and it had the exact same problem.

Rudy

---

### Post by RudyG on 2011-07-22
Update for those who may read this in the future.

Well, it turned out to be much ado about nothing. The KDE package manager allowed me to uninstall pulseaudio and even the plugins related to it.
The accounts of others that I had read that reported problems didn't apply to me.

After a reboot the system popped up a somewhat confusing mesage asking if I want to remove the pulseaudio hardware from my config. What it really removes is the pulseaudio association with that hardware. So I clicked Yes.

Rudy

---

