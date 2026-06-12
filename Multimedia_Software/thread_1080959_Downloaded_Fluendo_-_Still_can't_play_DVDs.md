---
title: "Downloaded Fluendo - Still can't play DVDs"
date: 2009-02-26
forum: Multimedia Software
---

### Post by webdunce on 2009-02-26
When I tried to play a DVD, I got an error saying that I didn't have the plugins required. Ubuntu then gave me the option of downloading "ugly" plugins (that required me to agree that doing so was not illegal in my country, which i have no way to verify) OR buying legitimate plugins.

I opted for the legitimate method. So, I bought, downloaded and installed the COMPLETE fluendo pack. Then I restarted Ubuntu (just in case).

Now, if I'm lucky, Totem says "Totem could not play this media (DVD) although a plugin is present to handle it...You might want to check that a disc is present in the drive and that it is correctly configured."

But, mostly Totem just says "An error occurred: Could not open location; you might not have permission to open the file."

I was going to go thru the "sticky" on this forum and got so far as to install some kind of Medubuntu or other...but after reading a few of the instructions I could tell it was going in the direction of using the "ugly" plugins which I could have downloaded for free but decided not to due to questionable legal-ness.

I am trying to play DVDs that you buy...for instance, Pixar's "The Incredibles."

Any ideas about what to do next to get DVDs to play in Linux using my new 40$ Fluendo pack?

Thanks in advance,
--webdunce

---

### Post by mc4man on 2009-02-26
> Any ideas about what to do next to get DVDs to play in Linux using my new 40$ Fluendo pack?

That pack is not for dvd playback (read what it includes a bit more carefully

The powerdvd package would have been what you were looking for

Edit: I should read more carefully **maybe**, did you get the "complete" version? (it includes mpeg2 playback but doesn't specify commercial dvd's.
did you enable any gstreamer Fluendo plugins in synaptic, if so then it probably doesn't support encrypted dvd's

---

### Post by webdunce on 2009-02-26
okay, thanks.

i bought powerdvd and it DOES play commercial dvds (although, not too well ... so far only Disney DVDs play so the sound syncs correctly with the picture), but that may be my video card or DVD player (although XP's media player plays all my DVDs just fine on the same computer ... so I'm thinking it's not-so-great coding on the part of powerdvd...plus it does funny things like disappear from my desktop but still runs in the background so I can't eject my disc and I keep hearing the sound...weird)

but still, thanks, it was confusing me and now i see that probably fluendo (yes, i got the complete pack) just wasnt intended to play commercial dvds.

This was more or less an experiment for me to see if there was an easy and unquestionably legal way of getting quality dvd playing out of ubuntu.

cheers,
--webdunce

---

### Post by NeferalCrossfireX on 2009-02-26
> **webdunce said:**
> When I tried to play a DVD, I got an error saying that I didn't have the plugins required. Ubuntu then gave me the option of downloading "ugly" plugins (that required me to agree that doing so was not illegal in my country, which i have no way to verify) OR buying legitimate plugins.

I opted for the legitimate method. So, I bought, downloaded and installed the COMPLETE fluendo pack. Then I restarted Ubuntu (just in case).

Now, if I'm lucky, Totem says "Totem could not play this media (DVD) although a plugin is present to handle it...You might want to check that a disc is present in the drive and that it is correctly configured."

But, mostly Totem just says "An error occurred: Could not open location; you might not have permission to open the file."

I was going to go thru the "sticky" on this forum and got so far as to install some kind of Medubuntu or other...but after reading a few of the instructions I could tell it was going in the direction of using the "ugly" plugins which I could have downloaded for free but decided not to due to questionable legal-ness.

I am trying to play DVDs that you buy...for instance, Pixar's "The Incredibles."

Any ideas about what to do next to get DVDs to play in Linux using my new 40$ Fluendo pack?

Thanks in advance,
--webdunce

just download vlc media player from the repository. it'll play virtually anything you can throw at it.

---

### Post by webdunce on 2009-02-26
thanks all for the responses.

in regards to VLC, i was wanting a dvd solution that was paid for, so as to be unquestionably legal...as i wanted a solution that i could freely recommend to others.

also, i fixed my powerdvd issues by -- oddly -- turning of "visual effects" in my desktop appearance properties...it's working quite fine now for all commercial dvd's i tried and also the windowing and menus are working correctly too.

thanks all,
--webdunce

---

