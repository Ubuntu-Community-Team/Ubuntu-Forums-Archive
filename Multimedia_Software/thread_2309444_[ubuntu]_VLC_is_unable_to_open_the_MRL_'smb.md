---
title: "[ubuntu] VLC is unable to open the MRL 'smb://"
date: 2016-01-10
forum: Multimedia Software
---

### Post by LucienMidnight on 2016-01-10
I have been getting this error for over a month now, and have googled & searched various posts culminating in an entire evening download and tweaking but with no luck. The files are held on a Zyxel NAS550 and were working perfectly previous to this.. I can only assume update(s). Previously I would only need to log in to the NAS, browse to the files I wanted a play in VLC (Rincewind 2.1.6) - this included subtitles. I even have playlists set up on the NAS which do not work either. 

I have run updates, updated samba (there wasn't anything to update) and downloaded more samba files to tweak samba; I have reset, apt-get removed and reinstalled vlc (although possibly not all dependecies); I have checked settings on the NAS to see if anything has been changed (unfortunately there has been a significant update this week and that didn't fix the issue either); I have no firewall in ubuntu to tweak; I have downloaded SMPlayer and Miro which do not seem to respond at all.

Files are all visible in 'Files' and still play in Videos but I can no longer play any .mkv files. I would be tempted to try Totem but I'm guessing this would be a waste of time, especially when vlc was working fine. I have discovered I am unable to see the network through vlc so am unable to browse files through the program. Although I downloaded various files to tweak samba - samba was never set up to specially register the NAS and in a last ditch attempt I even changed my password back to the original one (I had changed it around the time it stopped working) and still no luck.

This is the log from vlc (below), any assistance will be gratefully received.


 [COLOR=#00008b]*pulse*[/COLOR][COLOR=#808080]* debug: *[/COLOR]changing sink 0: alsa_output.pci-0000_00_1b.0.hdmi-stereo (Built-in Audio Digital Stereo (HDMI))

 [COLOR=#00008b]*pulse*[/COLOR][COLOR=#808080]* debug: *[/COLOR]changing sink 0: alsa_output.pci-0000_00_1b.0.hdmi-stereo (Built-in Audio Digital Stereo (HDMI))

 [COLOR=#00008b]*pulse*[/COLOR][COLOR=#808080]* debug: *[/COLOR]changing sink 0: alsa_output.pci-0000_00_1b.0.hdmi-stereo (Built-in Audio Digital Stereo (HDMI))

 [COLOR=#00008b]*pulse*[/COLOR][COLOR=#808080]* debug: *[/COLOR]changing sink 0: alsa_output.pci-0000_00_1b.0.hdmi-stereo (Built-in Audio Digital Stereo (HDMI))

 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]adding item `smb://emeraldcloud/series/DRAMA/Ashes%20to%20Ashes/Ashes%20to%20Ashes%20-%20Season%201%20-%20Complete%20%5BBBC%20One%5D%20%5BXvid%5D/Ashes%20to%20Ashes%20S01E01%20Deja%20Vue%20%5Bxvid%5D.avi' ( smb://emeraldcloud/series/DRAMA/Ashes%20to%20Ashes/Ashes%20to%20Ashes%20-%20Season%201%20-%20Complete%20%5BBBC%20One%5D%20%5BXvid%5D/Ashes%20to%20Ashes%20S01E01%20Deja%20Vue%20%5Bxvid%5D.avi )
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]processing request item: smb://emeraldcloud/series/DRAMA/Ashes%20to%20Ashes/Ashes%20to%20Ashes%20-%20Season%201%20-%20Complete%20%5BBBC%20One%5D%20%5BXvid%5D/Ashes%20to%20Ashes%20S01E01%20Deja%20Vue%20%5Bxvid%5D.avi, node: null, skip: 0
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]rebuilding array of current - root Playlist
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]rebuild done - 2 items, index 1
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]starting playback of the new playlist item

 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]resyncing on smb://emeraldcloud/series/DRAMA/Ashes%20to%20Ashes/Ashes%20to%20Ashes%20-%20Season%201%20-%20Complete%20%5BBBC%20One%5D%20%5BXvid%5D/Ashes%20to%20Ashes%20S01E01%20Deja%20Vue%20%5Bxvid%5D.avi
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]smb://emeraldcloud/series/DRAMA/Ashes%20to%20Ashes/Ashes%20to%20Ashes%20-%20Season%201%20-%20Complete%20%5BBBC%20One%5D%20%5BXvid%5D/Ashes%20to%20Ashes%20S01E01%20Deja%20Vue%20%5Bxvid%5D.avi is at 1
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating new input thread
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Creating an input for 'smb://emeraldcloud/series/DRAMA/Ashes%20to%20Ashes/Ashes%20to%20Ashes%20-%20Season%201%20-%20Complete%20%5BBBC%20One%5D%20%5BXvid%5D/Ashes%20to%20Ashes%20S01E01%20Deja%20Vue%20%5Bxvid%5D.avi'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using timeshift granularity of 50 MiB, in path '/tmp'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]`smb://emeraldcloud/series/DRAMA/Ashes%20to%20Ashes/Ashes%20to%20Ashes%20-%20Season%201%20-%20Complete%20%5BBBC%20One%5D%20%5BXvid%5D/Ashes%20to%20Ashes%20S01E01%20Deja%20Vue%20%5Bxvid%5D.avi' gives access `smb' demux `' path `emeraldcloud/series/DRAMA/Ashes%20to%20Ashes/Ashes%20to%20Ashes%20-%20Season%201%20-%20Complete%20%5BBBC%20One%5D%20%5BXvid%5D/Ashes%20to%20Ashes%20S01E01%20Deja%20Vue%20%5Bxvid%5D.avi'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating demux: access='smb' demux='' location='emeraldcloud/series/DRAMA/Ashes%20to%20Ashes/Ashes%20to%20Ashes%20-%20Season%201%20-%20Complete%20%5BBBC%20One%5D%20%5BXvid%5D/Ashes%20to%20Ashes%20S01E01%20Deja%20Vue%20%5Bxvid%5D.avi' file='(null)'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for access_demux module matching "smb": 21 candidates
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no access_demux modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating access 'smb' location='emeraldcloud/series/DRAMA/Ashes%20to%20Ashes/Ashes%20to%20Ashes%20-%20Season%201%20-%20Complete%20%5BBBC%20One%5D%20%5BXvid%5D/Ashes%20to%20Ashes%20S01E01%20Deja%20Vue%20%5Bxvid%5D.avi', path='(null)'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for access module matching "smb": 25 candidates
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]meta ok for (null), need to fetch art
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for meta fetcher module matching "any": 1 candidates
 [COLOR=#00008b]*qt4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]IM: Setting an input

 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /home/zen_pirate/.local/share/vlc/lua/meta/fetcher
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/lib/vlc/lua/meta/fetcher
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/vlc/lua/meta/fetcher/tvrage.luac
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using meta fetcher module "lua"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]removing module "lua"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]searching art for smb://emeraldcloud/series/DRAMA/Ashes%20to%20Ashes/Ashes%20to%20Ashes%20-%20Season%201%20-%20Complete%20%5BBBC%20One%5D%20%5BXvid%5D/Ashes%20to%20Ashes%20S01E01%20Deja%20Vue%20%5Bxvid%5D.avi
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for art finder module matching "any": 2 candidates
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /home/zen_pirate/.local/share/vlc/lua/meta/art

 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/lib/vlc/lua/meta/art
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/vlc/lua/meta/art/00_musicbrainz.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/vlc/lua/meta/art/01_googleimage.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/vlc/lua/meta/art/02_frenchtv.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/vlc/lua/meta/art/03_lastfm.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/share/vlc/lua/meta/art
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no art finder modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]art not found for smb://emeraldcloud/series/DRAMA/Ashes%20to%20Ashes/Ashes%20to%20Ashes%20-%20Season%201%20-%20Complete%20%5BBBC%20One%5D%20%5BXvid%5D/Ashes%20to%20Ashes%20S01E01%20Deja%20Vue%20%5Bxvid%5D.avi
 [COLOR=#00008b]*access_smb*[/COLOR][COLOR=#ff0000]* error: *[/COLOR]open failed for 'emeraldcloud/series/DRAMA/Ashes%20to%20Ashes/Ashes%20to%20Ashes%20-%20Season%201%20-%20Complete%20%5BBBC%20One%5D%20%5BXvid%5D/Ashes%20to%20Ashes%20S01E01%20Deja%20Vue%20%5Bxvid%5D.avi' (Permission denied)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no access modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#ff0000]* error: *[/COLOR]open of `smb://emeraldcloud/series/DRAMA/Ashes%20to%20Ashes/Ashes%20to%20Ashes%20-%20Season%201%20-%20Complete%20%5BBBC%20One%5D%20%5BXvid%5D/Ashes%20to%20Ashes%20S01E01%20Deja%20Vue%20%5Bxvid%5D.avi' failed
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]dead input
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]changing item without a request (current 1/2)

 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]nothing to play
 [COLOR=#00008b]*qt4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]IM: Deleting the input
 [COLOR=#00008b]*pulse*[/COLOR][COLOR=#808080]* debug: *[/COLOR]changing sink 0: alsa_output.pci-0000_00_1b.0.hdmi-stereo (Built-in Audio Digital Stereo (HDMI))

..and there are no permissions visible for the NAS or NAS shares, I assume due to being a NAS.

---

### Post by LucienMidnight on 2016-01-21
Problem solved. I've just reinstalled everything and I have no problems again.

---

