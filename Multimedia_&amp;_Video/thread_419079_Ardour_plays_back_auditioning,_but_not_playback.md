---
title: "Ardour plays back auditioning, but not playback"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by k1001001 on 2007-04-22
Hi all. I have a rather weird situation going on with my computer at the moment. At one time, I got Ardour to work and I recorded one track of me just playing piano. Now, a few months later, I seem to have no luck getting JACK to play back the project when I hit the play button. However, if I select the "listen" function on the right-hand side and double click the track, it will play back the track while blinking "AUDITION" on the top right (it also plays back at sped up rate). I've looked at the JACK connections and both the "auditioner/out 1" and "master/out 1" are both connected to "playback_1".

Here's a screen shot to hopefully clear this up:
[IMG]http://img.photobucket.com/albums/v62/k1001001/jackandardour.png[/IMG]

I get sound from the auditioner, but not the master, even though they're both connected to the same thing.

Also, I'm getting an error from Ardour that says:
```
ERROR AudioEngine: cannot connect ardour:auditioner/out 2 to alsa_pcm:playback2
```

Any suggestions on how to get playback back to its normal state again? Also, any good sites or threads that clearly explain how to make JACK and Ardour work together?

PS I really can't wait for Ubuntu Studio to come out. Hopefully all my recording needs will be solved then.

---

### Post by TRinQtown on 2007-04-23
I have installed, uninstalled and reinstalled Ardour a couple of times giving up in frustration because of the doubling of some of the menus. At first I thought it was my eyes. I then remembered that I bought an energyXT license a few months ago and that there was a Linux version. I believe the developer Jorgen uses Xubuntu.

---

### Post by k1001001 on 2007-04-24
So are you saying I should use Ardour in Xubuntu?

---

