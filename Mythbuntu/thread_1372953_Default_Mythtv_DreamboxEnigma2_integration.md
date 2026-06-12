---
title: "Default Mythtv Dreambox/Enigma2 integration"
date: 2010-01-05
forum: Mythbuntu
---

### Post by sachag on 2010-01-05
I wish everyone the best for 2010. 
 
I have documented my Mythtv Dreambox integration. In my setup the dreamboxes acts like a DVB tunercard.
 
Here is the link to the wiki: 
 
[http://www.mythtv.org/wiki/Dreambox-NetworkRecorder](http://www.mythtv.org/wiki/Dreambox-NetworkRecorder)
 
Best regards
 
 Sacha

---

### Post by kleinlappies on 2011-06-28
I just wanted to say THX,
gonna give it a try, have it for a while but just not the time.
I would Love this to work as you said. 
cheers

---

### Post by espowsong on 2011-11-12
There are many different models regarding dreambox has been launched through the business for example [dreambox 800]("http://www.myclickshop.co.uk/dreambox-800-hd-dm800-hd-pvr-v72-supports-hdtv-2-5-sata-hdd-esata.html"), DM 7000, DM 5600, DM 5620, DM Five hundred HD, DM 500+, DM 7020, DM 7025, DM 7025+ and more.

---

### Post by vinprivat on 2012-01-27
Has anybody got that working? I got that far:

1.) I can view a stream from my Dreambox in VLC directly on my mythtv backend.
2.) I have setup the VLC streaming as described and can watch a stream going through vlc in daemon mode in another vlc instance running on the mythtv backend.
3.) I have setup everything in mythtv backend, the channels are there, the backend reports that it loaded 20 channels from the .m3u file.

When I switch to the new source 3 things can happen:

1.) the frontend crashes completely.
2.) I can't get a channel lock
3.) I receive an error message saying something like error opening jump program file buffer

I am on mythtv 0.24 most actual patches as of today.

Any ideas?

Michael

---

### Post by nickrout on 2012-01-27
> **vinprivat said:**
> Has anybody got that working? I got that far:

1.) I can view a stream from my Dreambox in VLC directly on my mythtv backend.
2.) I have setup the VLC streaming as described and can watch a stream going through vlc in daemon mode in another vlc instance running on the mythtv backend.
3.) I have setup everything in mythtv backend, the channels are there, the backend reports that it loaded 20 channels from the .m3u file.

When I switch to the new source 3 things can happen:

1.) the frontend crashes completely.
2.) I can't get a channel lock
3.) I receive an error message saying something like error opening jump program file buffer

I am on mythtv 0.24 most actual patches as of today.

Any ideas?

Michael

Yes, look at your logs!

---

### Post by ian dobson on 2012-01-29
Hi,

I've got the dreambox integration working.

Your error is due to a too short timeout set for tuning. The vlc script takes several seconds to run.

Regards
Ian Dobson

---

