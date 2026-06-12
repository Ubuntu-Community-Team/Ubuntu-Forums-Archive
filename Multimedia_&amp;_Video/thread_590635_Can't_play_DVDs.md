---
title: "Can't play DVDs"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by yang on 2007-10-24
When I popped in a DVD, totem appeared and said "Could not read from resource." I searched and found [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs), so from that I ran regionset (set to 1 as reported by vlc) and tried vlc. vlc *crashes* with:

```

libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:218: ifoOpenNewVTSI: Assertion `0' failed.

```

Then I tried gxine, but it fails with:

```

libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
xine-lib: error: Read error from::  Error opening vtsN=-1, domain=2.

```

I give up! Please! Anything to play a fricking DVD under Linux on non-exotic desktop hardware in 2007! :)

```

$ aptitude search libdvd restricted-extras gxine$ vlc$ regionset|grep ^i
i   gxine                           - the xine video player, GTK+/Gnome user int
i   libdvdcss2                      - Library for accessing DVDs like block devi
i A libdvdnav4                      - The DVD navigation library                
i A libdvdread3                     - library for reading DVDs                  
i   regionset                       - view and modify the region code of DVD dri
i   ubuntu-restricted-extras        - Commonly used restricted packages         
i   vlc                             - multimedia player and streamer            

```

Using Gutsy 64-bit on (Dell-approved) Dell XPS 410. FWIW the disc is mounted as /media/cdrom[0]; not sure if that's a sign of something awry.

---

