---
title: "Using Kodi - tuner needed"
date: 2022-09-22
forum: Multimedia Software
---

### Post by jonfisher on 2022-09-22
Can someone assist me with adding a "tuner, back end software, & an add-on for the backend to use the PVR" in Kodi.
 
Much thanks in advance!

p.s. Using Synaptic, I see there are a million kodi packages that can be installed for Kodi (including a *bunch* for PVR).  Any that users would recommend, I'd appreciate reading about them.

---

### Post by TheFu on 2022-09-23
The tuner is extremely location specific.  My tuner wouldn't work in Europe, for example.
I gave up trying to get Kodi working directly with a tuner for anything other than watching live TV. It was just too hard.

The solution I ended up with is:
* 2 HDHR tuners - these sit on the LAN and can be accessed by any computing devices.
* Jellyfin DLNA "server" - Jellyfin is like Plex, but without the constant tracking.
* Kodo/OSMC running on 2 raspberry Pi devices using JellyCon to connect to the Jellyfin server.  DLNA also works well.

So Jellyfin supports HDHR tuners well.  For me, getting schedule data is the issue.  Where I live, no free sources of this data are available. Most people pay $35/yr for the TV data. This gives them extremely high quality information for the TV schedules with all the XMLTV fields completed.

Silicon Dust, the makers of the HDHR line of network tuners are the most flexible, most supported, tuners that I know.  Be certain to get a DLNA model. Older models that you'd get used don't work with simple DVR software.  DLNA makes "recording" effectively saving an HTML stream of data for a specific duration.  My blog has an article and simple script using wget to "record" HDHR tuner channels.  For about a year, I recorded shows using that script + 'at'.  'at' is part of cron and runs commands 'at' specific times.  This was before I discovered Jellyfin.

I'm cheap and wrote a website scraper to grab data every 10 days, convert that text into XMLTV with only the main fields - Title, Episode Title, start and end times.  It isn't very elegant and breaks about once a month with some crazy input.  For a period, I found low-quality schedule data in JSON from a tiny website.  I suspect it became too popular, so they shutdown.  My web-scraper uses webbrowser automation and doesn't work with Wayland at all, only X11 with a cnee script. It is ugly, but mostly works.

Jellyfin makes the whole thing work.  It is an apt-get install away.  Jellyfin has client-apps for management and playback. I use the app on Android to control JellyCon on Kodi - it makes global searches for stuff to watch really easy.

Of course, the entire tuner thing goes into many directions - broadcast antennas, cable access, satellite channels, IPTV channels.  I had pluto TV working for a few months, but that was such a hassle - they only have schedules for the next day, so automatic updates are necessary, plus the DVR doesn't work with those channels at all.  Something about ffmpeg support for m8u3 content streams not working. Basically, 1 segment gets recorded, but everything after that is corrupted.  That seems to be an issue with lots of IPTV sources.

Anyway - where in the world are you? That's the most important aspect for which tuner.

As for Kodi and tuners with DVR capabilities - the consensus is to use TVHeadEnd which is an extremely complex, ugly, piece of software.  Got watch a few youtube videos about it and see the setup required. You'll still have the schedule data issue to be solved.  I suspect that's a North American issue only.  I understand that Europe has free schedule data, same for most of the world. Only US/Canada do they charge for schedule data. Sigh.

---

