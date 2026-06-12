---
title: "Has anyone gotten sflphone working with DiamondCard?"
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by greybeard95a on 2011-07-13
Hi,

Since Twinkle is apparently a dead project, I'm experimenting with SFLphone.  I got it to connect to my instance of sipwitch on my server without difficulty.

Getting it to connect to DiamondCard.us seems to be another matter.  All it tells me is 401 Unauthorized.  I'm using my login password for the password.

Has anyone figured this out?

Thanks!

---

### Post by DuncanNZ on 2012-04-20
Bummer, same problem here. Please post a link if anyone finds the answer...

---

### Post by mdurham on 2012-09-14
I got it to work.

**Alias:** your name (fred jim etc)
**Protocol:** SIP
**User name:** your 6 digit diamondcard ID
**Password:** your 12 digit diamondcard PIN

Thats all I did to make it work. Make sure User name & Password are numeric.
I found it a bit clunky to use and it doesn't even have a directory for stored numbers.
I think Twinkle is way better than this. It's a pity that it's been abandoned by it's creator.

Cheers Mike

---

### Post by grashdur on 2013-03-17
Today I installed SFLPhone and it seems to be working fine with Diamondcard. Yes, I too am annoyed by the lack of any address book. It's supposed to link up with Evolution or KAddressbook, but that feature does not seem to actually be working. 

Right now this is the only softphone I can get to work. I did use Twinkle for a number of years, but it has become so buggy in recent months that I just can't rely on it any more. My next task is to fiddle with the codecs to see if I can reduce the long sound delay (currently 6 seconds, round-trip!).

Bria is a great program, except for the very poor quality of incoming sound.

Jitsi looks like a wonderful program, but I can't make it work with Diamondcard (in spite of their own instructions), and it seems to not have any sound either.

Linphone also looks nice but I can't make it work with Diamondcard.

============

By the way: I just got rid of that long sound delay, by disabling all audio codecs except for PCMU/8000 (and maybe turn off noise cancellation).

---

