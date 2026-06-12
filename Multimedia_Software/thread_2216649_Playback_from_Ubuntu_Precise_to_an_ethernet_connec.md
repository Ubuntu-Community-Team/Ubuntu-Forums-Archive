---
title: "Playback from Ubuntu Precise to an ethernet connected TV"
date: 2014-04-13
forum: Multimedia Software
---

### Post by johnaaronrose on 2014-04-13
I want to view a movie held in an flv file (though I can  convert it to mp4 if necessary using Transmageddon: the TV is able to playback .mp4 but not .flv files held on a memory stick connected to a usb socket) on my new Sony LCD/LED TV which I can see on my  home network, it's connected to my router by ethernet as device MT8520-1  with a fixed IP address set in my router for the TV. I've looked up Sony's  manuals on their web site and they give no info about using the ethernet  connection. What app(s) are recommended for doing this (I hope) simple task? 
PS I've looked at MediaTomb: from its documentation I was not able to decide if it would do this. Also, the Precise version would not bring up the UI and the documentation looks quite complicated

---

### Post by TheFu on 2014-04-13
For something that seems so very easy, it is fairly complex what needs to happen under the covers.
Almost all current-gen media players will work with MP4 containers holder h.264/AAC video and audio.  So, you can either pre-transcode to that format, OR if you have a strong PC as a server, let the server transcode "on-the-fly" into that format.  I wouldn't attempt the 2nd option without a Core i5 or faster CPU.

mp4 is just a container. Can can hold 50+ different media types, so ... shoving just anything into an mp4 file isn't likely to make the TV happy.

Looked up the specs for that player:
 [LIST]
[*]   Dual-channel MPEG-2, MPEG-4, VC-1 video decoder
[*]    Dual-channel multi-format HD audio decoder
[/LIST]
This information isn't technical enough to be very useful.  Definitely go with transcoding to h.264/aac --> mp4 to be happy. That is also supported by Chromecast and pretty much every current-gen media player in the last 3 yrs out there (roku, WDTV, Android, .... )

I haven't a clue what Transmageddon is - ffmpeg, avconv, handbrake will all transcode to that format easily. Looks like a GStreamer-based transcoder. Meh.

If you want to setup an easy to use media server AND have a strong CPU, then Plex is good (if not F/LOSS). There is no need to provide the Plex corporation any information - no need for an account and blocking their servers with a firewall does NOT stop the program from working.  Any DLNA client/renderer can access the media on the Plex server. There are fairly strict file naming conventions for TV and Movies to get the most of Plex, but for home videos where there isn't any internet DB to be checked for metadata, it works fine too without a "scraper".

---

### Post by johnaaronrose on 2014-04-13
> **TheFu said:**
> For something that seems so very easy, it is fairly complex what needs to happen under the covers.
Almost all current-gen media players will work with MP4 containers holder h.264/AAC video and audio.  So, you can either pre-transcode to that format, OR if you have a strong PC as a server, let the server transcode "on-the-fly" into that format.  I wouldn't attempt the 2nd option without a Core i5 or faster CPU.

mp4 is just a container. Can can hold 50+ different media types, so ... shoving just anything into an mp4 file isn't likely to make the TV happy.

Looked up the specs for that player:
[LIST]
[*]   Dual-channel MPEG-2, MPEG-4, VC-1 video decoder 
[*]    Dual-channel multi-format HD audio decoder 
[/LIST]
This information isn't technical enough to be very useful.  Definitely go with transcoding to h.264/aac --> mp4 to be happy. That is also supported by Chromecast and pretty much every current-gen media player in the last 3 yrs out there (roku, WDTV, Android, .... )

I haven't a clue what Transmageddon is - ffmpeg, avconv, handbrake will all transcode to that format easily. Looks like a GStreamer-based transcoder. Meh.

If you want to setup an easy to use media server AND have a strong CPU, then Plex is good (if not F/LOSS). There is no need to provide the Plex corporation any information - no need for an account and blocking their servers with a firewall does NOT stop the program from working.  Any DLNA client/renderer can access the media on the Plex server. There are fairly strict file naming conventions for TV and Movies to get the most of Plex, but for home videos where there isn't any internet DB to be checked for metadata, it works fine too without a "scraper".

I shouldn't have even mentioned mp4/flv. That isn't my problem. The problem is to find an app which will stream a video from my PC to my TV (both being on my home network with fixed ip addresses): in other words I want to watch movies on my TV where their files are on my PC. I've tried MediaTomb but couldn't even get it to display a UI. I'm now looking at minidlna.

---

### Post by TheFu on 2014-04-13
Been there, done that.  

Plex.

---

### Post by johnaaronrose on 2014-04-13
I don't want to use proprietary software such as Plex. I want something simple: I don't want to create libraries (as in minidlna which I can't even get to work anyway). I just want to use an app to playback one video file from my PC onto my TV.

---

### Post by TheFu on 2014-04-13
> **johnaaronrose said:**
> I don't want to use proprietary software such as Plex. I want something simple: I don't want to create libraries (as in minidlna which I can't even get to work anyway). I just want to use an app to playback one video file from my PC onto my TV.

I completely understand. I was like that too. Tried everything else first. I've been doing this for years. Ran XBMC for a few years after getting frustrated when some hardware players refused to play "some" FLV files. Either I could transcode everything or use a PC. Tried ps2mediacenter, minidlna, mediatomb, even Windows7 MC and decided that samba/nfs was much easier. All the media centers either didn't work or would be months out of data (7MC is like that).  Then I got a Roku box and wanted to play LAN content though it. It doesn't support networked LAN file systems at all, so the search continued without a solution.  Someone gave me a Chromecast for Xmas. It was similar to the Roku - didn't want to playback any LAN media ... without DLNA.  I'd already screwed around with other options for months ... no, years.  They sucked, relatively speaking.

10 minutes to install Plex Server, use the web-gui to point at local media (NFS at the time) and it would let me stream to most of the devices in the house.

Done and done. Wish I'd swallowed it years ago.

---

### Post by johnaaronrose on 2014-04-13
OK, I was able to install Plex from Ubuntu Software Centre. Running Plex brings up a web page. I've signed up for an account, though I wasn't sure if it was necessary? Where is the option to point to local media?
PS I find the signin to Ubutu Forums a pain since they got hacked: it doesn't go back to the place that you were.

---

### Post by TheFu on 2014-04-13
No need for any accounts to access via local media. It is only necessary for internet-based streaming.
If you ever change the internal LAN IPs, then you'll have to locate the preferences file buried under /var/llib .... and modify the subnet there. I had to do this a few weeks ago.  Anything outside that subnet is required to use the plex-pass login ... unless you have a VPN and make it appear to be on the LAN.

So - by now you should be watching that video, assuming it is in the format supported by the playback device.

---

### Post by johnaaronrose on 2014-04-13
> **TheFu said:**
> No need for any accounts to access via local media. It is only necessary for internet-based streaming.
If you ever change the internal LAN IPs, then you'll have to locate the preferences file buried under /var/llib .... and modify the subnet there. I had to do this a few weeks ago.  Anything outside that subnet is required to use the plex-pass login ... unless you have a VPN and make it appear to be on the LAN.

So - by now you should be watching that video, assuming it is in the format supported by the playback device.

I still don't understand how to play a video file stored on & from my Ubuntu PC to my TV.

I don't see any file for Plex in /var/lib/.

---

### Post by TheFu on 2014-04-13
Config directories with the web interface.  Mine is at: [http://istar:32400/](http://istar:32400/) - the hostname:port for plex on my network.
* Movies
* TV
* Music - meh
* Photos - meh
* Home videos (or videos you don't want scraped over the internet)

I use /D for this stuff, then
/D/M - movies
/D/T - TV
/D/V - Home videos
/D/Music - music
The DLNA devices "see" the "Plex Media Server" on the network automatically. Plex automatically scans those folders for changes from time to time - it is odd that I need to manually force a scan. It happens within 5 min usually. Through the web interface you can correct any metadata mistakes (usually due to NOT following their structure and naming conventions). Some Asian movies just don't have English metadata, IME.

If you aren't happy with the TV-connected device menu, load up Bubble UPnP on any wifi android device on the same subnet. It will "find" the server and any DLNA clients. From android, you can choose which DLNA server to be the source and select which DLNA "renderer" to send the video.  Since a Chromecast doesn't have any remote (to keep it cheap), an android device is mandatory for a remote controller.

The /var/lib/ .... place is NOT important today, but since this is where the DB and metadata are stored for TV and Movie files, it will become important to have enough storage available there to hold movie posters, etc. 
"/var/lib/plexmediaserver/Library/Application Support/Plex Media Server" is the path on my Ubuntu box. There are hundreds - thousands of files there.

---

### Post by johnaaronrose on 2014-04-13
> **TheFu said:**
> Config directories with the web interface.  Mine is at: [http://istar:32400/](http://istar:32400/) - the hostname:port for plex on my network.
* Movies
* TV
* Music - meh
* Photos - meh
* Home videos (or videos you don't want scraped over the internet)

I use /D for this stuff, then
/D/M - movies
/D/T - TV
/D/V - Home videos
/D/Music - music
The DLNA devices "see" the "Plex Media Server" on the network automatically. Plex automatically scans those folders for changes from time to time - it is odd that I need to manually force a scan. It happens within 5 min usually. Through the web interface you can correct any metadata mistakes (usually due to NOT following their structure and naming conventions). Some Asian movies just don't have English metadata, IME.

If you aren't happy with the TV-connected device menu, load up Bubble UPnP on any wifi android device on the same subnet. It will "find" the server and any DLNA clients. From android, you can choose which DLNA server to be the source and select which DLNA "renderer" to send the video.  Since a Chromecast doesn't have any remote (to keep it cheap), an android device is mandatory for a remote controller.

The /var/lib/ .... place is NOT important today, but since this is where the DB and metadata are stored for TV and Movie files, it will become important to have enough storage available there to hold movie posters, etc. 
"/var/lib/plexmediaserver/Library/Application Support/Plex Media Server" is the path on my Ubuntu box. There are hundreds - thousands of files there.

I still don't understand. The web page that's brought up when I start Plex Media Server from the Dash doesn't really tell me what to do. I tried add a section. I selected Movies. It prompted for a folder but it couldn't see any folder in my home folder. Does the folder need special permissions? The permissions for e.g. Videos folder are allow Others 'Access files'. Or do the folders have to be created by Plex? So I tried /Plex/Movies but it did nothing?

I eventually found the preferences file. 
MachineIdentifier="524f04eb-f..." ProcessedMachineIdentifier="ffb680339e3..
though I'm baffled as to what you'd change these to the PC's or TV's ip address changed.

---

### Post by TheFu on 2014-04-13
Sorry if I'm not being clear. Ignore the preference file - you don't need it today and probably won't for years. It just took me much longer to find than I'd expect, so I thought it would be useful for others.

Do you understand Linux file and directory permissions?  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) explains. Does the process owner of the plex media center (probably "plex") have read access to those files?  If allowing the "plex" userid read access is special permissions, then yes, that is required. There are many ways to solve this. If you understand the link above, then you'll know what to do.

I don't keep media in my HOME - too hard to handle the different backup methods needed between HOME files and media files for me. I prefer placing media elsewhere (NOT inside HOME) for many, many, many, reasons.

Does "/Plex/Movies" exist AND contain the movie files ****in the correct naming convention****? If not, then that is useless. Plex doesn't create any "content" directories. It doesn't manage any content directories. It just scans them, retrieves metadata from the internet and makes that data available to any DLNA (or plex) clients which request it.  "Plex server" doesn't playback anything - this is just the server. If you want a "Plex client", there are lots of those too. No need for the plex-branded client at all. Any player that supports DLNA works - xbmc, vlc, plus all the hardware devices, tv, bluray players.

Sorry - I can't help with anything related to Dash - don't use it. Most of my systems are CLI-only, no GUI.

---

### Post by johnaaronrose on 2014-04-13
I'm completely baffled by Plex. I don't understand why it can't find folders in my home directory. I certainly do not want to create folders in the root directory. I do know already about Linux file & directory permissions. I'll have another look tomorrow. If I still don't get it, I'll abandon Plex.

---

### Post by TheFu on 2014-04-14
Well, what are the permissions, owner, group from / all the way down to where you store these videos?
That could explain the issues you've had with the other tools as well.

---

### Post by johnaaronrose on 2014-04-15
> **TheFu said:**
> Well, what are the permissions, owner, group from / all the way down to where you store these videos?
That could explain the issues you've had with the other tools as well.

Aplogies for delay in replying. Permissions for the folders were set by Ubuntu install, so I do not wish to change them. They are:
/home:
Owner - root - create & delete files
Group - root - access files
Others -  access files
/home/john:
Owner - john - create & delete files
Group - john - access files
Others -  access files
/home/john/Videos:
Owner - john - create & delete files
Group - john - access files
Others -  access files

File in /home/john/Videos:
Owner - john - read & write
Group - john - read & write
Others -  read only

---

### Post by TheFu on 2014-04-15
Yes, the forum login is less than ideal now.

Thanks for the permissions, but I really need to see the **drwxr-xr-x  userid   groupid ** stuff for every directory to be accessed.  "access files" and "creaete & delete files" are ambiguous.
Here are some examples:

```
$ find /D -maxdepth 2 -type d -ls  |more
    13   24 drwxrwxr-x 538 me       me          24576 Apr 13 10:05 /D/M
640059    4 drwxr-xr-x   2 me       me           4096 Jan 13 18:51 /D/M/Bicentennial_Man
640300    4 drwxr-xr-x   2 me       me           4096 Jan 13 18:51 /D/M/Painted_Skin-ch
640325    4 drwxr-xr-x   2 me       me           4096 Feb 17 11:28 /D/M/Red_Planet
    21    4 drwxr-xr-x   2 me       me           4096 Jan 13 18:51 /D/M/Wedding_Crashers
```
See the r-x for "other"?  THAT is critical, since plex runs as "plex" and is NOT in your/my personal group (me). That makes the plex ID part of the "other" permissions. Both X and R **must** exist for /home, /home/john,  /home/john/videos and for all subdirectories from that point down.  Found this link [https://plexapp.zendesk.com/hc/en-us/articles/200288596-Linux-Permissions-Guide](https://plexapp.zendesk.com/hc/en-us/articles/200288596-Linux-Permissions-Guide) specific to plex.  The other video servers would have needed the same permissions.

OR

you could add your userid to the "plex" group and recursively change the group for /home/john/videos down to be "plex" with 750 permissions, but the parent directories will still need to be 755 for /home and /home/john.  Does this make sense? Do not change other directories outside the "videos" to the plex group.

Oh - I see that "Videos" is capitalized. I'm not gonna fix that above, but it needs to be the same as on your system.

---

### Post by johnaaronrose on 2014-04-15
Is this any good?
john@JudithLaptop:~$ find /home/john/Videos -maxdepth 2 -type d -ls |more
7340052    4 drwxr-xr-x   2 john     john         4096 Apr 13 17:33 /home/john/Videos
john@JudithLaptop:~$ ls -l /home/john/Videos
total 173008
-rw-rw-r-- 1 john john 177152063 Apr 12 20:12 The_Trip_to_Italy_-_2._Da_Giovanni_San_Fruttuoso_b040tnzl_default-201227-12042014.mp4
john@JudithLaptop:~$ ls -l /home/john/
total 68
drwxrwxr-x  2 john john 4096 Dec 11 10:21 Backups
drwxr-xr-x  2 john john 4096 Feb 21 16:57 Desktop
drwx------  2 john john 4096 Apr 11  2013 DesktopConfigurationFiles
drwxr-xr-x  3 john john 4096 Dec 16 20:12 Documents
drwxr-xr-x  2 john john 4096 Apr 13 15:55 Downloads
drwx------ 10 john john 4096 Apr 15 17:49 Dropbox
-rw-r--r--  1 john john 8445 Nov 24  2012 examples.desktop
drwxr-xr-x  3 john john 4096 Jan 21 10:48 Music
drwxr-xr-x  2 john john 4096 Dec 10 12:21 Pictures
drwxr-xr-x  2 john john 4096 Dec 19 22:23 Public
drwx------ 19 john john 4096 Dec 19 17:36 Software
drwxr-xr-x  2 john john 4096 Nov  9 10:13 Templates
drwxrwxr-x  2 john john 4096 Apr 14 10:09 Temporary
drwxrwxr-x  2 john john 4096 Oct 28 10:53 Ubuntu One
drwxr-xr-x  2 john john 4096 Apr 13 17:33 Videos
john@JudithLaptop:~$ ls -l /home
total 8
drwxr-xr-x 62 john   john   4096 Apr 15 17:49 john
drwxr-xr-x 42 judith judith 4096 Mar 30 20:51 judith

---

### Post by TheFu on 2014-04-15
That looks correct.  Crap.  It should work.

Only /home /home/john and ./Videos matters. The other stuff doesn't at all.  Is there an open bug with Plex for videos stored in /home/? A quick search didn't find an issue.

Can you test with a /Videos directory?  It would only be hard if /home is a different partition than /.  If they are in the same partition, a "**sudo mv ~/Videos /**" will be instantaneous.

---

### Post by johnaaronrose on 2014-04-15
Only one partition for /home & /. "**sudo mv ~/Videos /**" moved Videos from /home/john/ to /, as expected. In Plex website, I added a section successfully which contained the 1 movie that I had put in it. I still don't understand how to actually play the movie on my TV now that Plex knows about it. Do I have to add the TV as a device?

---

### Post by TheFu on 2014-04-15
> **johnaaronrose said:**
> Only one partition for /home & /. "**sudo mv ~/Videos /**" moved Videos from /home/john/ to /, as expected. In Plex website, I added a section successfully which contained the 1 movie that I had put in it. I still don't understand how to actually play the movie on my TV now that Plex knows about it. Do I have to add the TV as a device?

You've installed the "plex server" - any DLNA client can "see it" and make requests.   Your TV may be a DLNA client or a Roku or a 4.x Android device or a WD TV Live or any number of other networked "media players" or BluRay players.
Playback depends 100% on the video container, video codec used, audio codec, specific specific settings for those codecs, AND what each media player supports.

For example, I have a plex server and a number of DLNA client devices and DLNA "renderers".  Often, the "client" and the "renderer" are the same - like Android or WDTV or Roku or Chromecast devices. Using the WDTV, when I ask it to connect to a "media server", it shows a list available on the LAN, I select "Plex-something" and it shows a pseudo-menu with Video, Music and Photos.  I select Video and it displays Movies, Adult, Videos, Home, and TV.  Each of those have been specified in the Plex web GUI as "video" content folders.  You probably just want "videos" if there isn't IMDB metadata you want.  TV, Movies **must** be separate and content that won't have metadata needs to be separate.

So ... any DLNA client should "see" the plex server on the network. No authentication needed.  The chromecast is the only device that I have which DOES NOT act like a DLNA client - it is just a "renderer" capable of being "streamed at" from a client.

The Plex web interface doesn't let you "stream at" your TV/media player, at least mine doesn't. My TVs are not networked - all I need is for the damn TV to be hit with a virus and never patched again. ;)

Does all this make sense?  It is harder to explain than it is to use, trust me. There must be 50 youtube videos about this.

---

