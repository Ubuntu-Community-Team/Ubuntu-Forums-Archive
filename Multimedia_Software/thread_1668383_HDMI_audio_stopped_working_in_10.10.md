---
title: "HDMI audio stopped working in 10.10"
date: 2011-01-16
forum: Multimedia Software
---

### Post by Mathias_mm on 2011-01-16
Hi,

Somewhat of a noob in linux-land, i'd say, but I've had this system up an running for about half a year now. It's an HTPC with an old a64 in an NF4 mobo and an Nvidia 8400 GS, which is connected to the onboard soundcards spdif out for sound through the card. I'm connecting to my TV via HDMI, and it all worked well in 10.04. I decided to try out 10.10, which, it turns out was a bad idea, sindce the audio stopped working. I'm unsure exactly how i got it to work the first time, but i was just fooling around with some settings (in the GUI), that i thought made sense.
I've tried all sorts of different things now, so i might have messed it up even worse now. Can anyone help? It's doing my head in...

---

### Post by Mathias_mm on 2011-01-16
Perhaps i should add that sound works fine via the analog jack. Also, I am working on a brand new install of Ubuntu, since there were other nagging things wrong with the system - but sound was the real reason i reinstalled. I'd think the sound should work fine if i choose digital duplex, but it doesn't. I've unmuted everything in alsamixer and the digital source listed there is PCM.

Edit: I've played around a bit, and in SMPlayer preferences i can choose sound device. alsa(0.0) is my analog out, and if i choose this it works just fine. If i then choose alsa(0.2), it won't work. I've checked the connection of the cable, and it seems fine, although i have no alternate OS on the machine to test. As i said, it stopped working when I updated the system.
Another thing I've noticed is that Boxee has stopped making sounds in the UI. Videos and music is fine, using analog. I have NO idea what's going on :(

---

### Post by Mathias_mm on 2011-01-17
No ideas?

---

### Post by tjones00 on 2011-01-17
I was going to respond to this yesterday but mid post I just changed my reply into a howto. Then I forgot to link it to you.

[http://ubuntuforums.org/showthread.php?t=1668737](http://ubuntuforums.org/showthread.php?t=1668737)

---

### Post by Mathias_mm on 2011-01-17
> **tjones00 said:**
> I was going to respond to this yesterday but mid post I just changed my reply into a howto. Then I forgot to link it to you.

[http://ubuntuforums.org/showthread.php?t=1668737](http://ubuntuforums.org/showthread.php?t=1668737)

Yeah, actually your thread was my reason for editing my post. I now also noticed it did not actually update the title in the boards, just inside the thread. Annoying.
Anyway, that may work, but I can't figure out what i need to do and what I won't need to do - the thing is I actually don't have any audio chip on the gfx, audio is fed in from the spdif on my motherboard.
As I said, i have a feeling your thread may work, but I can't figure out exactly what i does, and I can't follow it from end to end because i have different devices :)

Also, in the NVnews thing linked in your thread, there is a link to this:
[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)
I did this before reinstall, the problem is 1) it didn't work and 2) I don't want daily updates of this, I'd rather it worked and then never update again ;)

---

### Post by tjones00 on 2011-01-17
Ah thanks for the heads up I included the alsa link with that howto now.

If you don't want the daily you could always remove the ppa after the initial install. Another way to do it is to check for standard released packages that are already available via ubuntu backports using apt-cache search or synaptic.

---

### Post by Mathias_mm on 2011-01-17
> **tjones00 said:**
> Ah thanks for the heads up I included the alsa link with that howto now.

If you don't want the daily you could always remove the ppa after the initial install. Another way to do it is to check for standard released packages that are already available via ubuntu backports using apt-cache search or synaptic.

Alright, I might try this later today, even though it seems weird I need new drivers for a motherboard that is over 5 years old, especially as it was running just fine in 10.4. Oh well...

---

