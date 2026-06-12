---
title: "Rhythmbox Unknown Audio for any CD"
date: 2009-11-07
forum: Multimedia Software
---

### Post by jameskevindoyle on 2009-11-07
Hi,

I upgraded from Ubuntu 6.06 to 9.04 recently and see that Rhythmbox is the default audio CD ripper, rather than Sound Juicer.  I've been trying out Rhythmbox's CD ripping, but no matter what CD I put in, Rhythmbox identifies it as "Unknown Audio" with "Unknown" Artist and Album and no track names.  This includes CDs like Rolling Stones' Exile on Main Street and Beatles' Rubber Soul, which I would think would be listed in any CD database.  There's no messages from Rhythmbox about trying to find out the CD info, or why it can't find it out, so I'm not sure what to troubleshoot.  I started rhythmbox from the command line as "rhythmbox -d" and I find the message: 

"(21:46:51) [0x984e408] [metadata_cb] rb-audiocd-source.c:722: Failed to load cd metadata: Cannot read CD: Please check that a disc is present in the drive."

This seems wrong since Rhythmbox is able to know how many tracks are on the CD and how long they are, and can even "import" them to music files in my library.  There's no other indication of trouble reading the CD.

I even tried upgrading from Rhythmbox 0.12.0 to 0.12.5, since there seem to be CD ripping improvements in those releases, but it has the same behavior.

I've read that Rhythmbox expects the CD info to be in MusicBrainz, but if it was a problem with MusicBrainz listing that CD, wouldn't I see a different debug message from "Cannot read CD: Please check that a disc is present"?

Any help would be great!  CD info lookup worked nicely under Sound Juicer in Ubuntu 6.06, it would be pretty frustrating if I couldn't get the same thing to work in Ubuntu 9.04.

Thanks,
Jim

---

### Post by jameskevindoyle on 2009-11-08
Hi,

I guess I have to take this question back.

After starting my computer today and opening Rhythmbox (0.12.5, upgraded from .deb on top of Ubuntu 9.04) to investigate this further, it now finds the audio CD info with no problem, logging debug messages like the following:

(17:45:29) [0x869b408] [metadata_cb] rb-audiocd-source.c:800: musicbrainz_albumid: 4e48a9b1-b666-429d-8c33-11fba83f4555
(17:45:29) [0x869b408] [metadata_cb] rb-audiocd-source.c:801: musicbrainz_albumartistid: b071f9fa-14b0-4217-8e97-eb41da73f598
(17:45:29) [0x869b408] [metadata_cb] rb-audiocd-source.c:802: album artist: The Rolling Stones
(17:45:29) [0x869b408] [metadata_cb] rb-audiocd-source.c:803: disc number: 0
(17:45:29) [0x869b408] [metadata_cb] rb-audiocd-source.c:804: genre: (null)
(17:45:29) [0x869b408] [metadata_cb] rb-audiocd-source.c:811: storing metadata for The Rolling Stones - Exile on Main St. - Rocks Off
(17:45:29) [0x869b408] [metadata_cb] rb-audiocd-source.c:813: musicbrainz_trackid: e21eb23c-311a-46a6-a18f-37ad93b92ed1
(17:45:29) [0x8(17:45:29) [0x869b408] [metadata_cb] rb-audiocd-source.c:800: musicbrainz_albumid: 4e48a9b1-b666-429d-8c33-11fba83f4555
(17:45:29) [0x869b408] [metadata_cb] rb-audiocd-source.c:801: musicbrainz_albumartistid: b071f9fa-14b0-4217-8e97-eb41da73f598
(17:45:29) [0x869b408] [metadata_cb] rb-audiocd-source.c:802: album artist: The Rolling Stones
(17:45:29) [0x869b408] [metadata_cb] rb-audiocd-source.c:803: disc number: 0
(17:45:29) [0x869b408] [metadata_cb] rb-audiocd-source.c:804: genre: (null)
(17:45:29) [0x869b408] [metadata_cb] rb-audiocd-source.c:811: storing metadata for The Rolling Stones - Exile on Main St. - Rocks Off
(17:45:29) [0x869b408] [metadata_cb] rb-audiocd-source.c:813: musicbrainz_trackid: e21eb23c-311a-46a6-a18f-37ad93b92ed1
(17:45:29) [0x869b408] [metadata_cb] rb-audiocd-source.c:814: musicbrainz_artistid: b071f9fa-14b0-4217-8e97-eb41da73f598
(17:45:29) [0x869b408] [metadata_cb] rb-audiocd-source.c:815: artist sortname: Rolling Stones, The
69b408] [metadata_cb] rb-audiocd-source.c:814: musicbrainz_artistid: b071f9fa-14b0-4217-8e97-eb41da73f598
(17:45:29) [0x869b408] [metadata_cb] rb-audiocd-source.c:815: artist sortname: Rolling Stones, The


I really don't know what the difference is.  I was trying the same CD in Rhythmbox 0.12.5 yesterday with no luck.  Maybe I had to reboot after upgrading Rhythmbox?  Or maybe it was the fact that other users were logged in using the user switcher?

But it's working now, so I guess there's no problem anymore.

Thanks,
Jim

---

