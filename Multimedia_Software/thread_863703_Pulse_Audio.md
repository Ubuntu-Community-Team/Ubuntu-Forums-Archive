---
title: "Pulse Audio"
date: 2008-07-18
forum: Multimedia Software
---

### Post by moberry on 2008-07-18
And that's all I have to say..


Seriously, was this tested at ALL? Alsa does not yet support my Soundblaster XFI (no biggie) so I threw in an old PCI card from the late 90's. Pulse cant even seem to handle THAT gracefully.

<rant>

Why was this include in an LTS version?

Are you guys effin crazy?

I have never, in the past 10 years of using desktop linux had a problem with audio, now i'm doing reboots every 30 minutes when I want to listen to some tunes.

I hear it's based off ESD, that sucked donkey when it was the de-facto as well but didn't lock my audio device up.

In my opinion (very humble) Ubuntu has 3 solutions:

1. Fix this POS
2. Remove it and go back to wtf ever you were using (esd i guess)
3. If the solution is already in an upstream package, by god release it to hardy. You shouldn't have to much of a problem with that seeing as you released it to begin with. I mean, while running gutsy, I read the release notes and it said "Pulseaudio is now the default audio stack" and I thought to myself.. WTF is pulseaudio"

I have read the flame wars lately on the GNOME blogs, I dont care who is right or wrong, but someone is.

</rant>

Now, Im not switching to windows. I like linux, and I have alot invested in it.

With that being said. I dont know crap about audio, but im fluent in C and a fast learner. So if the right person reads this, tell me what to do. 

Lets get this fixed.

Time to reboot.

---

### Post by Melcar on 2008-07-18
What are the problems?  I have never had issues with PA with none of my Creative cards (non-Xfi of course) nor with any of the countless integrated sound chips I have dealt with.  It just works for me.

---

### Post by MasterJS on 2008-07-18
I fixed the sound on my computer by just installing ESD ```
sudo apt-get install esound
```This will remove pulseaudio for you too!

---

