---
title: "Please help me with my sound problem"
date: 2006-11-28
forum: Multimedia &amp; Video
---

### Post by Dekunuts on 2006-11-28
Hi, I used to have a pci audio card that worked just fine under ubuntu (using 6.10) but I removed it to give to someone else with a broken audio card. I figured i'd just use my onboard sound card. This did not turn out as I thought. On reboot, without the pci card, and the onboard card turned on in the BIOS,  there was no sound. I checked aplay -l and it shows audio devices. When I run ALSA mixer, it gives me a 'no mixer elems found' error. I don't know what the problem is and I'm sure my onboard sound 'card' should be supported. It is a A7N8X-X motherboard (socket A) with n force 2 chipset. rhytmbox starts up, just as any other media program and simply works, apparently unknowing of a problem.

I also tried reinstalling linux-sound-base alsa-base and alsa-utils , it didn't help.

Does anyone know what I should do, reinstalling will work yes, but that's not really elegant isn't it. Now, I have a pretty good understanding of computers , but have only been using ubuntu for about 5 months and my english is not all that great, thought you should know.

---

### Post by crazedgremlin on 2006-11-28
try:
     sudo pkg-reconfigure alsa-base
     sudo update-modules
     sudo /etc/init.d/alsa restart

here's where I got that from
[http://lists.agnula.org/pipermail/users/2004-February/001044.html]("http://lists.agnula.org/pipermail/users/2004-February/001044.html")

---

### Post by Dekunuts on 2006-11-28
the first two lines worked, but the third one didn't because alsa does not appear to be a command. When i run the command to get the output from reconfigure alsa base, i get an error stating that does not exist. 

Once again, I don't know what to do. I also tried sudo dpkg-reconfigure linux-sound-base but that only lets me choose between alsa and oss, not helpful. I also tried running alsamixer again, that does work now, but the settings are correct, with master and pcm turned way up.

thanks

---

### Post by crazedgremlin on 2006-11-28
> **Dekunuts said:**
> the first two lines worked, but the third one didn't because alsa does not appear to be a command. When i run the command to get the output from reconfigure alsa base, i get an error stating that does not exist. 

Well, if it's working, don't try to fix it 

glad to help :D

---

### Post by Dekunuts on 2006-11-28
aiai, there we go with the bad english. I didn't mean it works now, what I meant to say is that the first two lines triggered something, they ran, worked. But they didn't fix the problem. 

I'm terribly sorry for the wrong impression i gave. The thanks was just, well, because you were helping.

sorry again

---

### Post by crazedgremlin on 2006-11-28
oh well...
maybe the third line doesn't need a sudo?

just
     /etc/init.d/alsa restart

---

### Post by Dekunuts on 2006-11-28
when I go to /etc/init.d and do an ls, it appears there is no file calles alsa in there, maybe that's my problem...

---

### Post by crazedgremlin on 2006-11-28
I actually had to run these lines and it worked fine for me.

Maybe it's because you uninstalled linux-sound-base, alsa-base, and alsa-utils.
Are you absolutely sure you reinstalled them?

If you did install them, I have absolutely no idea how to help you](*,)

---

### Post by crazedgremlin on 2006-11-28
Actually (duh..)
if you do a full reboot, that would be the equivalent to restarting alsa because alsa is started and ended at every startup and shutdown, respectively.  Good luck :)

---

### Post by Dekunuts on 2006-11-29
yes, everything is correctly installed (alsa-base alsa-utils liux-sound-base) , and I did indeed reboot because the restart command didn't work. I will say once more what I deem strange and probably a key factor, no software is giving errors of any kind, everything thinks the sound card works, but I'm not hearing anything. (And yes, my speakersw ork fine :p ) So, here's hoping for a solution

thanks again

---

### Post by Dekunuts on 2006-11-29
I have reinstalled every sound related package again but it is still not working and i am starting to get desperate, I cannot find any solution that actually works, what to do ? I've been at it for over 10 hours already. Please help me.

---

### Post by crazedgremlin on 2006-12-01
hey!! I figured it out!!!!
I made a typo... :)

sudo dpkg-reconfigure alsa-base
sudo update-modules
sudo /etc/init.d/alsa(hit tab right here for the autocompletion) restart

I had a situation where I had to do this.  I hope this works.. Good luck:)

---

### Post by crazedgremlin on 2006-12-01
by the way, it was two typos
in the first command I typed 'pkg' instead of 'dpkg' so you might want to run the command again.

Sorry it took me so long to get back to you--I had a busy week.

---

### Post by crazedgremlin on 2006-12-02
bump...
where'd ya go?

---

