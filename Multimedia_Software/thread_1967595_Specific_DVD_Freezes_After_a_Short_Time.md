---
title: "Specific DVD Freezes After a Short Time"
date: 2012-04-28
forum: Multimedia Software
---

### Post by zorbama on 2012-04-28
Hello,
I have a strange problem regarding a DVD. Now, let me say this: I have libdvdcss, libdvdread and libdvdnav installed, I changed the region with regionset and O scanned the internet for solutions to no avail. Also, other DVDs work just fine for me on Ubuntu.  I'll also manage to find another way to view this movie: I'm just asking this out of curiosity.

Now to the point: I try to play a specific disc (namely, a copy of North by Northwest with Hebrew subtitles), and it plays for a while, then freezes. Totem says that the dvd could not be decrypted, and vlc had an error   p, li { white-space: pre-wrap; }that looked like this: [COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not read -1/4 blocks at 0xed0ee.[/COLOR]
[COLOR=#000000]On mplayer it kept playing for a while, then the image got scrambled, then it stopped working.
[/COLOR]The disc is working perfect on two other machines: my father's Windows 7  computer, and our dvd player (I can't use it because setting up the  sound on it is a terrible experience)
[COLOR=#000000]Does anyone have any idea what I could have missed?[/COLOR]


[COLOR=#000000]Thanks in advance![/COLOR]
[COLOR=#000000]-Amir
[/COLOR]

---

### Post by gordintoronto on 2012-04-28
Sounds like a scratch on the DVD, or some other physical problem.

---

### Post by zorbama on 2012-04-28
Oh, I forgot to say, the disc is working perfect on two other machines: my father's Windows 7 computer, and our dvd player (I can't use it because setting up the sound on it is a terrible experience)

---

### Post by BicyclerBoy on 2012-04-28
This is normal & common.
Linus is not a licensed DVD playback OS.
And the war over DVD playback obfuscation is not over.

libdvdnav & read are still regularly changing, these changes don't make their way into distributions quickly.

Ridiculously &/or ironically  ,the best way to check is to rip using the latest copy of HandBrake for example.

Rip to H264 video if your PC is an i3 or faster.

You can get the latest HandBrake from the developer's daily build ppa.

---

### Post by zorbama on 2012-04-28
I see. Well, my computer isn't an i3: it's actually only a Pentium dual core.
I don't think there's a release for Precise, from what I can see.
I'm trying to rip it with ogmrip now, but it seems to have gotten stuck on 24%
Thanks for the reply. It makes sense, unfortunately. :)

---

### Post by BicyclerBoy on 2012-04-28
Only 15 hours young..
[https://launchpad.net/~stebbins/+archive/handbrake-snapshots?field.series_filter=precise](https://launchpad.net/~stebbins/+archive/handbrake-snapshots?field.series_filter=precise)

IMO the only DVD tools close to the action are mplayer & HandBrake & possibly VLC.
You understand I do not refer to the standard distribution packages.

---

### Post by zorbama on 2012-04-28
Yes, although I'm a little worried about installing other ppas, after a small mess I made to my previous installation...
I watched the movie eventually (downloaded a torrent). It wasn't ideal, but it was okay. I just started this thread to see if maybe I missed something when trying to play the disc, some codecs, but I guess it's just not recognized by libdvdcss yet.

---

### Post by BicyclerBoy on 2012-04-28
The problem is mostly likely in libdvdnav/read. The css stuff is not the cause of the problem.

---

### Post by zorbama on 2012-04-29
How can you tell?

---

### Post by BicyclerBoy on 2012-04-29
DVD players don't have the continuous firmware update requirement.
They don't have the key revocation process via media.
So the CSS protection on DVDs is unchanging as their f/w is fixed.

The navigation part was originally implemented as if a DVD is a valid computer filesystem etc & this is not the case.

Reading the project mailing lists etc..

---

### Post by zorbama on 2012-04-29
I see. Thank you for sharing with me. It's incredible how much I learned since I started using Ubuntu. :)

---

