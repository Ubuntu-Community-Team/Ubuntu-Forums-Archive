---
title: "[SOLVED] BBC Freeview Channels - Partial Lock"
date: 2007-11-28
forum: Mythbuntu
---

### Post by Chongo on 2007-11-28
I have installed Mythbuntu 7.10 on my media PC.

Everything is working fine except for the fact that my BBC television channels on Freeview only get a partial lock and so don't work.

All of the other television channels and the BBC Radio channels work fine.

When I first installed the OS, the BBC television channels were working fine to, although I have rescanned since then. I have made no other changes to the DVB / MythTV set up other than getting my remote control (Nebula DigiTV) to work with LIRC.

I've tried removing all channels from the backend setup and then exiting and then going back in and rescanning again.

Is this maybe a problem with multple channels with the same name / number being in the database (how do I check that?) or of MythTV usign multiple transmitters (I live in Edinburgh, and Craigkelly is my preferred transmitter, but I noticed during the scan a reference to Black Hill).

Could anyone suggest a resolution here?

That would be most tremendously kind!

Thanks loads,

Tom

:guitar:

---

### Post by roseway on 2007-11-28
Are you sure it isn't just a matter of signal strength? Where I live the main BBC multiplex is weaker than the others, and is the first to break up when signal conditions are poor.
The other possibility is that there is some problem with your particular tuner card or its driver. I've had that problem with a Hauppauge HVR-1100 (it only receives two of the available multiplexes).

PS I doubt if there's a problem with multiple channels of the same name. My local transmitter is Dover, but I also get Bluebell Hill channels during scanning, but it all gets sorted out and only the main source gets stored.

---

### Post by Chongo on 2007-11-28
Hey thanks for replying.

I am pretty sure that there is nothing wrong with the card or the signal strength. Both work fine in Kaffeine on Kubuntu 7.04, and these channels were working OK when I first installed Mythbuntu? The aerial is atop a tall building on a hill pointing right at the Craigkelly transmitter (not at the Black Hill one which is another direction over the hill).

---

### Post by Chongo on 2007-12-24
I've finally found out what was wrong here!

I was using a Belkin Pure AV Coaxial cable, and I tried swapping in a much cheaper cable and everything works perfectly now!? I don't really understand why though, as the Belkin cable is a much higher quality?

---

### Post by kidalabama on 2009-11-26
i have got same problem i will test tomorrow.

---

