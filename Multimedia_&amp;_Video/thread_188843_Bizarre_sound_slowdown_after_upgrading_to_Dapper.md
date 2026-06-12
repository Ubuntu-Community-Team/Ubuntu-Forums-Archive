---
title: "Bizarre sound slowdown after upgrading to Dapper"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by jimbot on 2006-06-04
Hi,

I dist-upgraded from kubuntu breezy to kubuntu dapper and have acquired a strange audio problem. Whenever I play any sound, it comes out veeeeeeeeeeeery sloooooooooowly, like when a hero in a movie shouts "noooooooo!" in slow-motion. Video playback is normal speed, but the audio stream is similarly slowed.

I've tried this with XMMS, Amarok, and mpg123. All play back sound at a crawl. XMMS recognises that the playback is slow and the GUI reports the speed by drawing the analyser slowly. The time remaining counter also decreases slowly. Amarok on the other hand thinks it's playing at normal speed, and eventually crashes, but Amarok usually crashes anyway so I don't think this is related.

I estimate from XMMS's analyser that playback is just over 5 times slower than real-time.

**top** reports no excessive CPU usage from any application during slow playback, and the system remains responsive throughout.

Playback is slow for all audio formats, including mp3, ogg, mod and midi.

My machine is a Shuttle SN25P with an onboard Envy24 sound chip. It worked flawlessly in Kubuntu 5.10.

Has this happened to anyone else? Is there anything I can do to fix it?

Regards,
James

---

### Post by jimbot on 2006-06-04
Holy crap, I solved it on my own! :D 

Apparently, typing "amixer set 'Multi Track Rate Locking' off" as root fixed whatever the problem was. I've put this line in my /etc/rc.local file so hopefully I won't have to worry about this again.

I hope these two posts help anyone else who has this problem; if you want any more tips from me, number one on the list would be to install Dapper from the CD rather than trying to do apt-get dist-upgrade on 5.10, which is a Very bumpy ride.

Best wishes,
James

---

### Post by Jeremy Owens-Boggs on 2006-06-23
I am having this same problem with my BT8XXX Hauppauge WinTV tuner card.  The sound is at about 2/3 speed off of /dev/dsp2.  Hopefully this will solve it.

---

