---
title: "Not able to add to system"
date: 2016-01-14
forum: Multimedia Software
---

### Post by ccdavis77 on 2016-01-14
Hi, running Kodi media center on Saucy Ubuntu HTPC.  When I recently upgraded the platform, I lost music visualizations.  Via the terminal, I add the visualizations using, for example, "[COLOR=#000000][FONT=Verdana]sudo apt-get install kodi-visualization-projectm".  Output reflects this being added to the media center, and it can be selected and options for the particular visualization accessed while using the media center.  However, the screen remains pitch black.  Debug log indicates: 

[/FONT][/COLOR]
[LIST=1]
[*]DEBUG: ADDON: Dll Initializing - projectM
[*]16:45:00 T:140528761083904   ERROR: ADDON: Could not locate visualization.projectm.so.1.0.17

So I add it but it can't be located...any ideas as to what is going wrong here?
Thanks for any help!
[/LIST]

---

### Post by sandyd on 2016-01-14
Hi, can you post the output of
```

ls -l /usr/lib/kodi/addons/
ls -l ~/.kodi/addons
```

---

### Post by Bucky Ball on 2016-01-14
*Thread moved to **Multimedia Software**.*

Just throwing this in: Saucy (and I presume you mean Ubuntu Saucy 13.10) is woefully out of date. How do you mean you 'upgraded the platform'?

Suggest you upgrade the OS to a supported one. ;)

---

### Post by ccdavis77 on 2016-01-17
Sorry, my mistake, I am running Trusty 14.04.3. Here's the output:

```
davismc@davismc:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty
davismc@davismc:~$ ls -l /usr/lib/kodi/addons/
total 24
drwxr-xr-x 2 root root 4096 Jan 13 00:15 library.kodi.adsp
drwxr-xr-x 2 root root 4096 Jan 13 00:15 library.kodi.audioengine
drwxr-xr-x 2 root root 4096 Jan 13 00:15 library.kodi.guilib
drwxr-xr-x 2 root root 4096 Jan 13 00:15 library.xbmc.addon
drwxr-xr-x 2 root root 4096 Jan 13 00:15 library.xbmc.codec
drwxr-xr-x 2 root root 4096 Jan 13 00:15 library.xbmc.pvr
davismc@davismc:~$ ls -l ~/.kodi/addons
total 1240
drwxrwxr-x  3 davismc davismc  4096 Dec 20 11:41 metadata.albums.theaudiodb.com
drwxr-xr-x  3 davismc davismc  4096 Dec 20 11:41 metadata.album.universal
drwxrwxr-x  3 davismc davismc  4096 Dec 20 11:41 metadata.artists.theaudiodb.com
drwxr-xr-x  3 davismc davismc  4096 Dec 20 11:41 metadata.artists.universal
drwxr-xr-x  2 davismc davismc  4096 Dec 21 11:40 metadata.common.allmusic.com
drwxr-xr-x  2 davismc davismc  4096 Dec 20 11:41 metadata.common.amazon.de
drwxr-xr-x  2 davismc davismc  4096 Dec 20 11:41 metadata.common.fanart.tv
drwxr-xr-x  2 davismc davismc  4096 Aug 17  2014 metadata.common.hdtrailers.net
drwxr-xr-x  2 davismc davismc  4096 Dec 20 11:41 metadata.common.htbackdrops.com
drwxr-xr-x  2 davismc davismc  4096 Dec 20 11:41 metadata.common.imdb.com
drwxrwxr-x  2 davismc davismc  4096 Dec 20 11:41 metadata.common.impa.com
drwxr-xr-x  2 davismc davismc  4096 Nov 23  2014 metadata.common.last.fm
drwxrwxr-x  2 davismc davismc  4096 Dec 20 11:41 metadata.common.movieposterdb.com
drwxr-xr-x  2 davismc davismc  4096 Dec 20 11:41 metadata.common.musicbrainz.org
drwxrwxr-x  2 davismc davismc  4096 Dec 21 11:40 metadata.common.ofdb.de
drwxr-xr-x  2 davismc davismc  4096 Nov 27 04:49 metadata.common.omdbapi.com
drwxrwxr-x  2 davismc davismc  4096 Jul  8  2015 metadata.common.port.hu
drwxrwxr-x  2 davismc davismc  4096 Nov 23  2014 metadata.common.rottentomatoes.com
drwxrwxr-x  2 davismc davismc  4096 Oct  9  2014 metadata.common.rt.com
drwxr-xr-x  2 davismc davismc  4096 Dec 20 11:41 metadata.common.theaudiodb.com
drwxr-xr-x  2 davismc davismc  4096 Dec 20 11:41 metadata.common.themoviedb.org
drwxrwxr-x  2 davismc davismc  4096 Nov 23  2014 metadata.common.trakt.tv
drwxrwxr-x  2 davismc davismc  4096 Aug 17  2014 metadata.common.youtubetrailers
drwxr-xr-x  3 davismc davismc  4096 Nov 30 17:48 metadata.musicvideos.theaudiodb.com
drwxr-xr-x  3 davismc davismc  4096 Dec 20 11:41 metadata.themoviedb.org
drwxr-xr-x  3 davismc davismc  4096 Dec 20 11:41 metadata.tvdb.com
drwxrwxr-x  3 davismc davismc  4096 Dec 20 11:41 metadata.universal
drwxrwxr-x  8 davismc davismc  4096 Aug 17  2014 Navi-X
drwxr-xr-x  2 davismc davismc 20480 Jan 17 22:43 packages
drwxr-xr-x  3 davismc davismc  4096 Nov  2 17:44 plugin.audio.binaural
drwxrwxr-x  3 davismc davismc  4096 Mar 27  2015 plugin.audio.di.fm
drwxr-xr-x  3 davismc davismc  4096 Nov 29  2014 plugin.audio.iheart-0.0.2
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 plugin.audio.internet.archive
drwxrwxr-x  3 davismc davismc  4096 Jan 12 14:47 plugin.audio.mixcloud
drwxr-xr-x  5 davismc davismc  4096 Jan  6 14:47 plugin.audio.mp3streams
drwxr-xr-x  3 davismc davismc  4096 Jan  8 14:47 plugin.audio.phish_in
drwxrwxr-x  3 davismc davismc  4096 Feb 16  2015 plugin.audio.radio_de
drwxrwxr-x  3 davismc davismc  4096 Sep  7 17:24 plugin.audio.radioreference
drwxr-xr-x  3 davismc davismc  4096 Aug 13 18:54 plugin.audio.radiotunes.com
drwxr-xr-x  3 davismc davismc  4096 Jan 13 12:06 plugin.audio.rockradio.com
drwxrwxr-x  3 davismc davismc  4096 Dec  8 18:20 plugin.audio.soundcloud
drwxrwxr-x  4 davismc davismc  4096 Aug 17  2014 plugin.audio.XBMCmp3
drwxrwxr-x  4 davismc davismc  4096 Dec 11 10:01 plugin.program.addoninstaller
drwxrwxr-x  3 davismc davismc  4096 Dec 29  2014 plugin.program.advanced.launcher
drwxr-xr-x  3 davismc davismc  4096 Jan 17 22:33 plugin.program.chrome.launcher
drwxrwxr-x  4 davismc davismc  4096 May  3  2015 plugin.program.xbmchub.notifications
drwxr-xr-x  3 davismc davismc  4096 Aug 10 23:07 plugin.video.80smusicvideos
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 plugin.video.classiccinema
drwxrwxr-x  4 davismc davismc  4096 Apr 21  2015 plugin.video.concertarchive
drwxr-xr-x  3 davismc davismc  4096 Mar 15  2015 plugin.video.crackler
drwxrwxr-x  3 davismc davismc  4096 Jan 13  2015 plugin.video.dailyflix
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 plugin.video.dailymotion_com
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 plugin.video.desitvforum
drwxr-xr-x  3 davismc davismc  4096 Dec  7 18:20 plugin.video.dextertv
drwxrwxr-x  4 davismc davismc  4096 Aug 17  2014 plugin.video.docuhub
drwxr-xr-x  4 davismc davismc  4096 Jun 13  2015 plugin.video.earthcam
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 plugin.video.ebaumsworld_com
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 plugin.video.espn3
drwxrwxr-x  3 davismc davismc  4096 Sep 24 21:57 plugin.video.espn_3
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 plugin.video.espn.video
drwxrwxr-x  3 davismc davismc  4096 Dec 11 09:14 plugin.video.football.today
drwxrwxr-x  3 davismc davismc  4096 Jun 11  2015 plugin.video.fox.news
drwxrwxr-x  4 davismc davismc  4096 Aug 17  2014 plugin.video.free.cable
drwxr-xr-x  3 davismc davismc  4096 Nov  5  2014 plugin.video.freefunvid
drwxrwxr-x  2 davismc davismc  4096 Sep  9  2014 plugin.video.freshstart
drwxr-xr-x  4 davismc davismc  4096 Dec  4  2014 plugin.video.fr.filmsdefrance
drwxr-xr-x  3 davismc davismc  4096 Dec 30 12:59 plugin.video.funniermoments
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 plugin.video.hdtrailers_net
drwxr-xr-x  3 davismc davismc  4096 Aug  6 09:23 plugin.video.HQZone
drwxrwxr-x  3 davismc davismc  4096 Aug 24 22:57 plugin.video.hubwizard
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 plugin.video.hulu
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 plugin.video.imdb.trailers
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 plugin.video.itunes_podcasts
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 plugin.video.khanacademy
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 plugin.video.live.shows
drwxr-xr-x  4 davismc davismc  4096 Jan 13 12:09 plugin.video.MikeysKaraoke
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 plugin.video.mtv
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 plugin.video.muzu.tv
drwxrwxr-x  6 davismc davismc  4096 May  3  2015 plugin.video.mysubscriptions
drwxr-xr-x  3 davismc davismc  4096 Nov  9 02:57 plugin.video.myvevo
drwxrwxr-x  3 davismc davismc  4096 Sep 25 23:58 plugin.video.newcrackle
drwxrwxr-x  2 davismc davismc  4096 Aug 17  2014 plugin.video.newjerryseinfeld.com
drwxrwxr-x  2 davismc davismc  4096 Aug 17  2014 plugin.video.newslook
drwxrwxr-x  3 davismc davismc  4096 Oct 24 22:58 plugin.video.ororotv
drwxr-xr-x  4 davismc davismc  4096 Jan 17 13:03 plugin.video.phstreams
drwxrwxr-x  4 davismc davismc  4096 Aug 21 20:05 plugin.video.projectfreetv
drwxrwxr-x  3 davismc davismc  4096 Oct 11 04:50 plugin.video.rt
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 plugin.video.simply.player
drwxr-xr-x  4 davismc davismc  4096 Jan 13 00:54 plugin.video.streamengine
drwxrwxr-x  4 davismc davismc  4096 Oct 16 22:07 plugin.video.ted.talks
drwxrwxr-x  3 davismc davismc  4096 May 13  2015 plugin.video.tgun
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 plugin.video.the.colbert.report
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 plugin.video.the.daily.show
drwxrwxr-x  3 davismc davismc  4096 Aug 10 23:06 plugin.video.thegreat80s
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 plugin.video.theonion_com
drwxrwxr-x  3 davismc davismc  4096 Feb 17  2015 plugin.video.tmz
drwxrwxr-x  3 davismc davismc  4096 Dec 24 11:41 plugin.video.trailer.addict
drwxrwxr-x  4 davismc davismc  4096 Jan  3 14:47 plugin.video.ultimateguitar
drwxr-xr-x  3 davismc davismc  4096 Sep  2 23:03 plugin.video.ustvnow
drwxrwxr-x  4 davismc davismc  4096 Sep 27 12:14 plugin.video.veetle
drwxr-xr-x  5 davismc davismc  4096 Jan  9 15:19 plugin.video.vevo
drwxr-xr-x  3 davismc davismc  4096 Nov 29  2014 plugin.video.vevo_tv-1.1.3
drwxrwxr-x  3 davismc davismc  4096 Jan  4  2015 plugin.video.xbmb3c
drwxrwxr-x  4 davismc davismc  4096 Jul 23 22:25 plugin.video.xbmchubmaintenance
drwxrwxr-x  4 davismc davismc  4096 May  4  2015 plugin.video.XBMCKaraoke
drwxrwxr-x  3 davismc davismc  4096 Jan  2 14:47 plugin.video.youtube
drwxrwxr-x  2 davismc davismc  4096 Apr  2  2015 repository.angelscry.xcmc-plugins
drwxrwxr-x  2 davismc davismc  4096 Jan 13 00:19 repository.BlazeRepo
drwxrwxr-x  2 davismc davismc  4096 Aug 17  2014 repository.bluecop.xbmc-plugins
drwxrwxr-x  2 davismc davismc  4096 Feb 23  2015 repository.bstrdsmkr
drwxrwxr-x  2 davismc davismc  4096 Aug 17  2014 repository.bunkford
drwxr-xr-x  2 davismc davismc  4096 Sep  7 00:05 repository.dextertv
drwxrwxr-x  2 davismc davismc  4096 Feb  1  2015 repository.eldorado
drwxrwxr-x  2 davismc davismc  4096 Dec 22 11:41 repository.eleazar
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 repository.googlecode.anarchintosh-projects
drwxrwxr-x  2 davismc davismc  4096 Jul 20 18:45 repository.Kinkin
drwxrwxr-x  2 davismc davismc  4096 Dec  7  2014 repository.lambda
drwxrwxr-x  2 davismc davismc  4096 Dec 20  2014 repository.mash2k3
drwxrwxr-x  2 davismc davismc  4096 Aug 17  2014 repository.MaxMustermann.xbmc
drwxr-xr-x  2 davismc davismc  4096 Jan 13 00:52 repository.mdrepo
drwxrwxr-x  2 davismc davismc  4096 Oct 18 16:55 repository.metalkettle
drwxrwxr-x  2 davismc davismc  4096 Aug 17  2014 repository.o9r1sh
drwxr-xr-x  2 davismc davismc  4096 Nov 29  2014 repository.queeup
drwxrwxr-x  2 davismc davismc  4096 May  2  2015 repository.Rodrigo
drwxrwxr-x  2 davismc davismc  4096 Aug 17  2014 repository.spoyser
-rw-rw-r--  1 davismc davismc 57322 Aug 25  2014 repository.superrepo.org.gotham.all-0.5.1.zip
drwxrwxr-x  2 davismc davismc  4096 Mar 14  2015 repository.thehighway
drwxrwxr-x  2 davismc davismc  4096 Aug 17  2014 repository.The_Silencer
drwxrwxr-x  2 davismc davismc  4096 Nov 26  2014 repository.TheYid
drwxrwxr-x  2 davismc davismc  4096 Aug 17  2014 repository.Vinnydude
drwxrwxr-x  2 davismc davismc  4096 Jun 10  2015 repository.xbmchub
drwxr-xr-x  3 davismc davismc  4096 Dec  5 18:20 resource.images.moviegenreicons.coloured
drwxr-xr-x  3 davismc davismc  4096 Dec  5 18:21 resource.images.musicgenreicons.poster
drwxr-xr-x  3 davismc davismc  4096 Dec  5 18:21 resource.images.recordlabels.white
drwxr-xr-x  3 davismc davismc  4096 Dec  5 18:20 resource.images.studios.white
drwxr-xr-x  3 davismc davismc  4096 Dec  5 18:21 resource.images.weatherfanart.multi
drwxr-xr-x  3 davismc davismc  4096 Dec  5 18:21 resource.images.weatherfanart.prairie
drwxr-xr-x  3 davismc davismc  4096 Dec  5 18:21 resource.images.weathericons.animated
drwxr-xr-x  3 davismc davismc  4096 Oct 19 20:41 resource.uisounds.amber
drwxr-xr-x  3 davismc davismc  4096 Nov 20 07:30 resource.uisounds.titan.modern
drwxr-xr-x  3 davismc davismc  4096 Jan 13 12:03 resource.uisounds.transparency
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 script.ace.extrapack
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 script.aeonmq5.extrapack
drwxrwxr-x  3 davismc davismc  4096 Dec  5 13:56 script.artistslideshow
drwxrwxr-x  4 davismc davismc  4096 Nov 21 14:53 script.artwork.downloader
drwxrwxr-x  4 davismc davismc  4096 Aug 17  2014 script.audio.pandora
drwxrwxr-x  3 davismc davismc  4096 May 11  2015 script.cinema.experience
drwxrwxr-x  4 davismc davismc  4096 Jan  8 14:47 script.common.plugin.cache
drwxrwxr-x  3 davismc davismc  4096 Dec  5 18:20 script.cu.lrclyrics
drwxr-xr-x  3 davismc davismc  4096 Dec  5 18:20 script.extendedinfo
drwxr-xr-x  4 davismc davismc  4096 Apr 22  2015 script.facebook.media
drwxrwxr-x  3 davismc davismc  4096 Dec  5 13:56 script.favourites
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 script.funnyordie
drwxrwxr-x  3 davismc davismc  4096 Mar  9  2015 script.games.rom.collection.browser
drwxrwxr-x  3 davismc davismc  4096 Dec 31 12:59 script.globalsearch
drwxrwxr-x  3 davismc davismc  4096 Mar 25  2015 script.grab.fanart
drwxr-xr-x  2 davismc davismc  4096 Dec  7 18:20 script.image.resource.select
drwxr-xr-x  3 davismc davismc  4096 Dec  6 18:20 script.module.actionhandler
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 script.module.addon.common
drwxr-xr-x  3 davismc davismc  4096 Apr 11  2015 script.module.addon.signals
drwxr-xr-x  3 davismc davismc  4096 Dec 20 11:41 script.module.autoupdate
drwxrwxr-x  3 davismc davismc  4096 Mar 21  2015 script.module.axel.downloader
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 script.module.beautifulsoup
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 script.module.beautifulsoup4
drwxrwxr-x  4 davismc davismc  4096 Oct  9  2014 script.module.buggalo
drwxrwxr-x  3 davismc davismc  4096 Sep  8  2014 script.module.chardet
drwxrwxr-x  3 davismc davismc  4096 Jun 26  2015 script.module.coveapi
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 script.module.cryptopy
drwxrwxr-x  3 davismc davismc  4096 Jun  3  2015 script.module.demjson
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 script.module.elementtree
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 script.module.feedparser
drwxrwxr-x  3 davismc davismc  4096 Oct 13  2014 script.module.free.cable.database
drwxr-xr-x  3 davismc davismc  4096 Sep  7 00:06 script.module.httplib2
drwxrwxr-x  4 davismc davismc  4096 Sep 13  2014 script.module.hubparentalcontrol
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 script.module.mechanize
drwxrwxr-x  4 davismc davismc  4096 Oct 16 22:07 script.module.metahandler
drwxr-xr-x  3 davismc davismc  4096 Nov 29  2014 script.module.mutagen
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 script.module.myconnpy
drwxr-xr-x  4 davismc davismc  4096 Apr 19  2015 script.module.oauth.helper
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 script.module.parsedom
drwxr-xr-x  3 davismc davismc  4096 Dec  5 13:56 script.module.pyxbmct
drwxr-xr-x  3 davismc davismc  4096 Aug 24 22:51 script.module.pyxbmctmanager
drwxrwxr-x  3 davismc davismc  4096 Jan  1 14:47 script.module.requests
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 script.module.requests2
drwxrwxr-x  4 davismc davismc  4096 Oct  4  2014 script.module.simple.downloader
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 script.module.simplejson
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 script.module.simpleYT
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 script.module.t0mm0.common
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 script.module.TheYid.common
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 script.module.unidecode
drwxrwxr-x  4 davismc davismc  4096 Jan 17 13:03 script.module.urlresolver
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 script.module.xbmcswift2
drwxr-xr-x  4 davismc davismc  4096 Dec 31 12:59 script.module.youtube.dl
drwxr-xr-x  6 davismc davismc  4096 May  4  2015 script.navi-x
drwxr-xr-x  3 davismc davismc  4096 Dec  7 18:20 script.openweathermap.maps
drwxrwxr-x  2 davismc davismc  4096 Dec  7 18:20 script.playalbum
drwxrwxr-x  2 davismc davismc  4096 Dec  1  2014 script.playlists
drwxrwxr-x  2 davismc davismc  4096 Dec  4  2014 script.randomandlastitems
drwxrwxr-x  3 davismc davismc  4096 Nov 26  2014 script.rss.editor
drwxr-xr-x  3 davismc davismc  4096 Aug 24 22:51 script.simpleplaylists
drwxr-xr-x  3 davismc davismc  4096 Dec 16 09:15 script.skin.helper.service
drwxrwxr-x  3 davismc davismc  4096 Dec 16 09:15 script.skinshortcuts
drwxr-xr-x  2 davismc davismc  4096 Nov 20 07:29 script.titanskin.helpers
drwxr-xr-x  3 davismc davismc  4096 Dec 19 09:33 script.toolbox
drwxrwxr-x  5 davismc davismc  4096 Dec  5 13:56 script.tv.show.next.aired
drwxrwxr-x  4 davismc davismc  4096 Jan 12 14:47 script.tvtunes
drwxrwxr-x  2 davismc davismc  4096 Aug 17  2014 script.videolanguage
drwxr-xr-x  3 davismc davismc  4096 Sep 10  2014 script.watchlist
drwxr-xr-x  4 davismc davismc  4096 Jan 17 22:44 script.web.viewer
drwxrwxr-x  3 davismc davismc  4096 Feb 25  2015 script.xbmc.debug.log
drwxrwxr-x  4 davismc davismc  4096 Jun 12  2015 script.xbmc.pandorajson
drwxrwxr-x  3 davismc davismc  4096 Aug 17  2014 script.xbmc.subtitles
drwxrwxr-x  3 davismc davismc  4096 Dec  5 13:56 service.library.data.provider
drwxrwxr-x  2 davismc davismc  4096 Aug 17  2014 service.rom.collection.browser
drwxrwxr-x  3 davismc davismc  4096 Jul 22 22:12 service.skin.widgets
drwxr-xr-x  3 davismc davismc  4096 Nov 21 14:33 service.subtitles.divxplanet
drwxrwxr-x  3 davismc davismc  4096 Nov 13 22:11 service.subtitles.opensubtitles
drwxr-xr-x  3 davismc davismc  4096 Dec 24 11:41 service.subtitles.subscene
drwxr-xr-x  3 davismc davismc  4096 Dec 13 09:14 service.subtitles.supersubtitles
drwxr-xr-x  4 davismc davismc  4096 Jan 12 14:47 service.xbmc.versioncheck
drwxr-xr-x  9 davismc davismc  4096 Mar  4  2015 skin.1080xf
drwxrwxr-x 10 davismc davismc  4096 Aug 17  2014 skin.ace
drwxrwxr-x  9 davismc davismc  4096 Aug 17  2014 skin.aeonmq5
drwxrwxr-x 11 davismc davismc  4096 Aug 17  2014 skin.aeon.nox
drwxr-xr-x 11 davismc davismc  4096 Dec 20 11:41 skin.aeon.nox.5
drwxrwxr-x  8 davismc davismc  4096 Jan 16 12:09 skin.amber
drwxrwxr-x  8 davismc davismc  4096 Nov  5 01:34 skin.back-row
drwxr-xr-x 10 davismc davismc  4096 Jul  2  2015 skin.bello
drwxrwxr-x  9 davismc davismc  4096 Aug 17  2014 skin.confluence
drwxr-xr-x 10 davismc davismc  4096 Aug 24 22:51 skin.convergence
drwxrwxr-x 11 davismc davismc  4096 Aug 24 22:51 skin.hybrid
drwxrwxr-x 11 davismc davismc  4096 Oct 19 20:41 skin.metropolis
drwxr-xr-x  9 davismc davismc  4096 Dec  5 18:20 skin.nebula
drwxr-xr-x 10 davismc davismc  4096 May  3  2015 skin.neon
drwxr-xr-x 12 davismc davismc  4096 Mar  8  2015 skin.refocus
drwxr-xr-x  9 davismc davismc  4096 Dec 23 11:42 skin.titan
drwxr-xr-x  8 davismc davismc  4096 Jan  1 14:47 skin.transparency
drwxr-xr-x  2 davismc davismc  4096 Aug 24 23:15 superrepo.kodi.isengard.all
drwxr-xr-x  2 davismc davismc  4096 Jan 13 12:09 superrepo.kodi.jarvis.all
drwxrwxr-x  3 davismc davismc  4096 Jul 23 00:41 ustvnow
drwxr-xr-x  3 davismc davismc  4096 Jan  1 14:47 weather.openweathermap.extended
drwxrwxr-x  3 davismc davismc  4096 Dec 24  2014 weather.wunderground
drwxrwxr-x  3 davismc davismc  4096 Dec  7 18:20 weather.yahoo
davismc@davismc:~$
```

---

### Post by ccdavis77 on 2016-01-19
Is this any help? Any ideas as to how I can fix this? thanks!

---

### Post by ccdavis77 on 2016-03-06
Bump

---

