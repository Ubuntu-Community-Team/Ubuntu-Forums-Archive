---
title: "All music players except VLC crash on starting"
date: 2013-01-19
forum: Multimedia Software
---

### Post by HuaiDan on 2013-01-19
Hello,
The issue I'm experiencing is very similar to this one:

[http://askubuntu.com/questions/165895/no-media-player-working-except-vlc-by-an-ordinary-user]("http://askubuntu.com/questions/165895/no-media-player-working-except-vlc-by-an-ordinary-user")

In summary, all of the following music players won't start: Banshee, Amarok, Clementine, and Rhythmbox.
Clementine gives me the following error from shell:
Bus error (core dumped)
All of them hang for a time, and then give me a crash report. I could post some of those if it would be helpful.
I am able to start Clementine and Banshee with su privileges. My normal user is in both the "audio" and "pulse" user groups, however this does not fix the issue as mentioned in the askubunutu thread. The peculiar thing is, the issue doesn't appear to be sound hardware related. Whenever I start any of these apps, the system hangs for a minute, then I get all kinds of  dmesg output that seems to indicate a hard disk disconnect, which ONLY happens for music player  apps. See below.
>   156.304262] ata2.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[  156.304268] ata2.00: irq_stat 0x40000008
[  156.304272] ata2.00: failed command: READ FPDMA QUEUED
[  156.304281] ata2.00: cmd 60/00:00:00:50:04/01:00:00:00:00/40 tag 0 ncq 131072 in
[  156.304282]          res 41/40:00:a0:50:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  156.304286] ata2.00: status: { DRDY ERR }
[  156.304290] ata2.00: error: { UNC }
[  156.308336] ata2.00: configured for UDMA/133
[  156.308349] ata2: EH complete
[  159.070810] ata2.00: exception Emask 0x0 SAct 0x4 SErr 0x0 action 0x0
[  159.070815] ata2.00: irq_stat 0x40000008
[  159.070820] ata2.00: failed command: READ FPDMA QUEUED
[  159.070829] ata2.00: cmd 60/00:10:00:50:04/01:00:00:00:00/40 tag 2 ncq 131072 in
[  159.070830]          res 41/40:00:a0:50:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  159.070834] ata2.00: status: { DRDY ERR }
[  159.070837] ata2.00: error: { UNC }
[  159.074046] ata2.00: configured for UDMA/133
[  159.074057] ata2: EH complete
[  161.837406] ata2.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  161.837411] ata2.00: irq_stat 0x40000008
[  161.837416] ata2.00: failed command: READ FPDMA QUEUED
[  161.837424] ata2.00: cmd 60/00:00:00:50:04/01:00:00:00:00/40 tag 0 ncq 131072 in
[  161.837426]          res 41/40:00:a0:50:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  161.837430] ata2.00: status: { DRDY ERR }
[  161.837433] ata2.00: error: { UNC }
[  161.840751] ata2.00: configured for UDMA/133
[  161.840762] ata2: EH complete
[  164.604000] ata2.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  164.604016] ata2.00: irq_stat 0x40000008
[  164.604023] ata2.00: failed command: READ FPDMA QUEUED
[  164.604034] ata2.00: cmd 60/00:00:00:50:04/01:00:00:00:00/40 tag 0 ncq 131072 in
[  164.604036]          res 41/40:00:a0:50:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  164.604043] ata2.00: status: { DRDY ERR }
[  164.604047] ata2.00: error: { UNC }
[  164.607475] ata2.00: configured for UDMA/133
[  164.607486] ata2: EH complete
[  167.370597] ata2.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  167.370602] ata2.00: irq_stat 0x40000008
[  167.370607] ata2.00: failed command: READ FPDMA QUEUED
[  167.370616] ata2.00: cmd 60/00:00:00:50:04/01:00:00:00:00/40 tag 0 ncq 131072 in
[  167.370617]          res 41/40:00:a0:50:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  167.370621] ata2.00: status: { DRDY ERR }
[  167.370624] ata2.00: error: { UNC }
[  167.374192] ata2.00: configured for UDMA/133
[  167.374203] ata2: EH complete
[  170.137198] ata2.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  170.137204] ata2.00: irq_stat 0x40000008
[  170.137209] ata2.00: failed command: READ FPDMA QUEUED
[  170.137217] ata2.00: cmd 60/00:00:00:50:04/01:00:00:00:00/40 tag 0 ncq 131072 in
[  170.137219]          res 41/40:00:a0:50:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  170.137223] ata2.00: status: { DRDY ERR }
[  170.137226] ata2.00: error: { UNC }
[  170.140908] ata2.00: configured for UDMA/133
[  170.140922] sd 1:0:0:0: [sdb] Unhandled sense code
[  170.140925] sd 1:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  170.140930] sd 1:0:0:0: [sdb]  Sense Key : Medium Error [current] [descriptor]
[  170.140936] Descriptor sense data with sense descriptors (in hex):
[  170.140939]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  170.140951]         00 04 50 a0 
[  170.140957] sd 1:0:0:0: [sdb]  Add. Sense: Unrecovered read error - auto reallocate failed
[  170.140963] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 00 04 50 00 00 01 00 00
[  170.140975] end_request: I/O error, dev sdb, sector 282784
[  170.141009] ata2: EH complete
[  173.092707] ata2.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  173.092712] ata2.00: irq_stat 0x40000001
[  173.092717] ata2.00: failed command: READ FPDMA QUEUED
[  173.092725] ata2.00: cmd 60/08:00:a0:50:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  173.092727]          res 41/40:00:a0:50:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  173.092731] ata2.00: status: { DRDY ERR }
[  173.092734] ata2.00: error: { UNC }
[  173.092737] ata2.00: failed command: READ FPDMA QUEUED
[  173.092745] ata2.00: cmd 60/08:08:18:c1:0b/00:00:36:00:00/40 tag 1 ncq 4096 in
[  173.092746]          res 41/40:00:00:00:00/00:00:00:00:00/00 Emask 0x9 (media error)
[  173.092750] ata2.00: status: { DRDY ERR }
[  173.092753] ata2.00: error: { UNC }
[  173.096803] ata2.00: configured for UDMA/133
[  173.096814] ata2: EH complete
[  175.870414] ata2.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  175.870419] ata2.00: irq_stat 0x40000008
[  175.870424] ata2.00: failed command: READ FPDMA QUEUED
[  175.870432] ata2.00: cmd 60/08:08:a0:50:04/00:00:00:00:00/40 tag 1 ncq 4096 in
[  175.870434]          res 41/40:00:a0:50:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  175.870438] ata2.00: status: { DRDY ERR }
[  175.870442] ata2.00: error: { UNC }
[  175.874515] ata2.00: configured for UDMA/133
[  175.874526] ata2: EH complete
[  178.648121] ata2.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  178.648127] ata2.00: irq_stat 0x40000008
[  178.648132] ata2.00: failed command: READ FPDMA QUEUED
[  178.648140] ata2.00: cmd 60/08:00:a0:50:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  178.648142]          res 41/40:00:a0:50:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  178.648146] ata2.00: status: { DRDY ERR }
[  178.648149] ata2.00: error: { UNC }
[  178.652255] ata2.00: configured for UDMA/133
[  178.652267] ata2: EH complete
[  181.425829] ata2.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  181.425835] ata2.00: irq_stat 0x40000008
[  181.425839] ata2.00: failed command: READ FPDMA QUEUED
[  181.425848] ata2.00: cmd 60/08:08:a0:50:04/00:00:00:00:00/40 tag 1 ncq 4096 in
[  181.425849]          res 41/40:00:a0:50:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  181.425853] ata2.00: status: { DRDY ERR }
[  181.425856] ata2.00: error: { UNC }
[  181.429962] ata2.00: configured for UDMA/133
[  181.429974] ata2: EH complete
[  184.203539] ata2.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  184.203544] ata2.00: irq_stat 0x40000008
[  184.203548] ata2.00: failed command: READ FPDMA QUEUED
[  184.203555] ata2.00: cmd 60/08:00:a0:50:04/00:00:00:00:00/40 tag 0 ncq 4096 in
[  184.203557]          res 41/40:00:a0:50:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  184.203560] ata2.00: status: { DRDY ERR }
[  184.203563] ata2.00: error: { UNC }
[  184.207693] ata2.00: configured for UDMA/133
[  184.207704] ata2: EH complete
[  186.981244] ata2.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  186.981249] ata2.00: irq_stat 0x40000008
[  186.981253] ata2.00: failed command: READ FPDMA QUEUED
[  186.981260] ata2.00: cmd 60/08:08:a0:50:04/00:00:00:00:00/40 tag 1 ncq 4096 in
[  186.981261]          res 41/40:00:a0:50:04/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  186.981265] ata2.00: status: { DRDY ERR }
[  186.981268] ata2.00: error: { UNC }
[  186.984542] ata2.00: configured for UDMA/133
[  186.984562] sd 1:0:0:0: [sdb] Unhandled sense code
[  186.984565] sd 1:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  186.984570] sd 1:0:0:0: [sdb]  Sense Key : Medium Error [current] [descriptor]
[  186.984575] Descriptor sense data with sense descriptors (in hex):
[  186.984578]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  186.984589]         00 04 50 a0 
[  186.984593] sd 1:0:0:0: [sdb]  Add. Sense: Unrecovered read error - auto reallocate failed
[  186.984599] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 00 04 50 a0 00 00 08 00
[  186.984610] end_request: I/O error, dev sdb, sector 282784
[  186.984628] ata2: EH complete

The hard drives are fine overall.
It's worth noting that this only started occurring after I installed openSUSE in a dual boot setup. SUSE works fine. I have it set up to start using GNU grub rather than its own version, and it doesn't seem to have a problem with that. Admittedly I haven't tried any of the music players with SUSE, I'll check next time I restart.
I'm using 12.04 LTS amd64, kernel 3.2.0-36 generic.

---

### Post by HuaiDan on 2013-01-19
As I suspected, all music players work fine in openSUSE.

Can anybody give me any ideas? Next thing I'm going to try is to create a new user and see if the issue is repicated there.


Edit: Clementine can start in a new user profile, so this seems to be profile/permission related. I did not give the new user any special permissions or include in any groups.

I also let fsck do a complete scan on all drives, which took an hour and found nothing wrong.

---

### Post by andrew.46 on 2013-01-19
I presume that MPlayer / SMPlayer also have no issues with your files? Try:

```

sudo apt-get install mplayer smplayer 

```

just for a test...

---

### Post by HuaiDan on 2013-01-19
SMplayer works. When I started it, it told me it couldn't identify thhe mplayer version number, so I just selected the newest version and it was ok with that.

---

### Post by ivotkl on 2013-01-20
I know the following text might not help you solve the problem on installed programs that crash on startup.

However, just to have a broad idea (will help me too), I would like to know what do you use all the media programs for. I am running Ubuntu 12.04 32 bits, using Rythmbox for audio files (mainly mp3s) and VLC media player for everything else.

By the way, what errors are given to you if you excecute the file from terminal? (You'll definitely get to the roots of all evil there).

---

### Post by HuaiDan on 2013-01-20
I'm trying to play mp3's but I can't even get to that stage, except with VLC and SMPlayer.
I uninstalled Amarok, which gave me numerous messages warning that it was crashing from prompt.
Clementine gives me the following error:
Bus error (core dumped)

I'm currently following up on a new lead. It seems I get all the dmesg output when I open my music folder. It's peculiar that this would cause the music players to crash, since I haven't even configured them to point them to the music folder. I even tried moving (to another drive) and renaming the folderthen opening it through Nautilus, and it gives me the same dmesg output. It's strange that openSUSE does not have the same issue when pointed to the same folder.
Next step is to restore the music folder from backup, and see if I get the same disk errors.

---

### Post by HuaiDan on 2013-01-20
I completely removed the music folder from my system, then purged and re-installed clementine.
This is what I get when I start it with su privileges:
> desktop:~$ sudo clementine
15:24:44.009 DEBUG WorkerPool<HandlerType>:281      Starting worker 0x7fd71534a2f0 "/usr/bin/clementine-tagreader" "/tmp/clementine_526462001" 
15:24:44.028 INFO  main:46                          TagReader worker connecting to "/tmp/clementine_526462001" 
15:24:44.029 DEBUG WorkerPool<HandlerType>:301      Worker 0x7fd71000c610 connected to "/tmp/clementine_526462001" 
15:24:44.045 INFO  Player:550                       Registered URL handler for "di" 
15:24:44.046 DEBUG InternetModel:98                 Adding internet service: "DigitallyImported" 
15:24:44.083 DEBUG InternetModel:98                 Adding internet service: "Icecast" 
15:24:44.108 DEBUG InternetModel:98                 Adding internet service: "Jamendo" 
Error: "/var/tmp/kdecache-dh" is owned by uid 1000 instead of uid 0.
15:24:44.173 INFO  Player:550                       Registered URL handler for "lastfm" 
15:24:44.173 DEBUG CoverProviders:34                Registered cover provider "last.fm" 
15:24:44.174 DEBUG InternetModel:98                 Adding internet service: "Last.fm" 
15:24:44.175 INFO  Player:550                       Registered URL handler for "googledrive" 
15:24:44.175 DEBUG InternetModel:98                 Adding internet service: "Google Drive" 
15:24:44.178 INFO  Player:550                       Registered URL handler for "grooveshark" 
15:24:44.179 DEBUG InternetModel:98                 Adding internet service: "Grooveshark" 
15:24:44.179 INFO  Player:550                       Registered URL handler for "jazzradio" 
15:24:44.180 DEBUG InternetModel:98                 Adding internet service: "JazzRadio" 
15:24:44.181 INFO  Player:550                       Registered URL handler for "magnatune" 
15:24:44.181 DEBUG InternetModel:98                 Adding internet service: "Magnatune" 
15:24:44.181 DEBUG InternetModel:98                 Adding internet service: "Podcasts" 
15:24:44.189 DEBUG InternetModel:98                 Adding internet service: "SavedRadio" 
15:24:44.189 INFO  Player:550                       Registered URL handler for "sky" 
15:24:44.190 DEBUG InternetModel:98                 Adding internet service: "SKY.fm" 
15:24:44.190 INFO  Player:550                       Registered URL handler for "somafm" 
15:24:44.191 DEBUG InternetModel:98                 Adding internet service: "SomaFM" 
15:24:44.193 DEBUG InternetModel:98                 Adding internet service: "SoundCloud" 
15:24:44.194 DEBUG SpotifyService:77                Spotify system blob path: "/usr/bin/clementine-spotifyblob" 
15:24:44.194 DEBUG SpotifyService:78                Spotify local blob path: "/home/dh/.config/Clementine/spotifyblob/version14-64bit/blob" 
15:24:44.195 DEBUG InternetModel:98                 Adding internet service: "Spotify" 
15:24:44.206 DEBUG NetworkProxyFactory:30           Detected system proxy URLs: ("", "", "", "") 
15:24:44.207 DEBUG CoverProviders:34                Registered cover provider "Amazon" 
15:24:44.211 DEBUG CoverProviders:34                Registered cover provider "Discogs" 
15:24:44.250 WARN  IconLoader:54                    Couldn't load icon "clementine-panel" 
15:24:44.266 WARN  IconLoader:54                    Couldn't load icon "clementine-panel-grey" 
15:24:44.292 WARN  OSD:89                           Error connecting to notifications service. 
15:24:44.294 DEBUG GnomeGlobalShortcutBackend:50    registering 
15:24:44.294 WARN  GnomeGlobalShortcutBackend:53    gnome settings daemon not registered 
15:24:44.294 DEBUG QxtGlobalShortcutBackend:32      registering 
15:24:44.432 DEBUG MainWindow:194                   Starting 
15:24:44.453 WARN  IconLoader:54                    Couldn't load icon "find" 
15:24:44.548 DEBUG MainWindow:245                   Initialising player 
15:24:44.555 DEBUG MainWindow:251                   Creating models 
15:24:44.563 DEBUG MainWindow:269                   Creating UI 
15:24:44.649 DEBUG MainWindow:626                   Creating equalizer 
15:24:44.650 DEBUG MainWindow:648                   Creating now playing widget 
15:24:44.713 DEBUG MainWindow:689                   Loading settings 
15:24:44.724 WARN  unknown                          "sni-qt/3634" WARN  15:24:44.724 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE  
15:24:44.789 DEBUG MainWindow:744                   Started 
15:24:44.794 INFO  DeviceManager:426                Device added: "/dev/sr0" 
15:24:44.797 INFO  DeviceManager:426                Device added: "Gio//ext3/ext4/20645040128" 
15:24:44.806 INFO  DeviceManager:426                Device added: "Gio//ext3/ext4/20645072896" 
15:24:44.806 INFO  DeviceManager:426                Device added: "Gio//ext3/ext4/37476704256" 
15:24:44.807 INFO  DeviceManager:426                Device added: "Gio/unmounted/140561059165760" 
15:24:44.808 INFO  DeviceManager:426                Device added: "Gio//ext3/ext4/488192884736" 
15:24:44.809 INFO  DeviceManager:426                Device added: "Gio/unmounted/140561059165568" 
15:24:44.856 DEBUG UbuntuUnityHack:74               Unity whitelist is "['JavaEmbeddedFrame', 'Wine', 'Update-notifier', 'clementine']
" 
15:24:45.354 DEBUG Geolocator:115                   Gelocated to: (39904030,116407526)  

It works fine this way, and I don't get disk errors.

Starting without root priviliges:

> desktop:~$ clementine
15:22:25.863 DEBUG WorkerPool<HandlerType>:281      Starting worker 0x7f8679f3d2f0 "/usr/bin/clementine-tagreader" "/tmp/clementine_518254881" 
15:22:25.876 INFO  main:46                          TagReader worker connecting to "/tmp/clementine_518254881" 
15:22:25.877 DEBUG WorkerPool<HandlerType>:301      Worker 0x7f866c00c5f0 connected to "/tmp/clementine_518254881" 
15:22:26.033 INFO  Player:550                       Registered URL handler for "di" 
15:22:26.033 DEBUG InternetModel:98                 Adding internet service: "DigitallyImported" 
15:22:26.101 DEBUG InternetModel:98                 Adding internet service: "Icecast" 
15:22:26.129 DEBUG InternetModel:98                 Adding internet service: "Jamendo" 
15:22:26.187 INFO  Player:550                       Registered URL handler for "lastfm" 
15:22:26.187 DEBUG CoverProviders:34                Registered cover provider "last.fm" 
15:22:26.188 DEBUG InternetModel:98                 Adding internet service: "Last.fm" 
15:22:26.190 INFO  Player:550                       Registered URL handler for "googledrive" 
15:22:26.190 DEBUG InternetModel:98                 Adding internet service: "Google Drive" 
15:22:26.195 INFO  Player:550                       Registered URL handler for "grooveshark" 
15:22:26.195 DEBUG InternetModel:98                 Adding internet service: "Grooveshark" 
15:22:26.196 INFO  Player:550                       Registered URL handler for "jazzradio" 
15:22:26.196 DEBUG InternetModel:98                 Adding internet service: "JazzRadio" 
15:22:26.198 INFO  Player:550                       Registered URL handler for "magnatune" 
15:22:26.198 DEBUG InternetModel:98                 Adding internet service: "Magnatune" 
15:22:26.199 DEBUG InternetModel:98                 Adding internet service: "Podcasts" 
15:22:26.210 DEBUG InternetModel:98                 Adding internet service: "SavedRadio" 
15:22:26.211 INFO  Player:550                       Registered URL handler for "sky" 
15:22:26.211 DEBUG InternetModel:98                 Adding internet service: "SKY.fm" 
15:22:26.211 INFO  Player:550                       Registered URL handler for "somafm" 
15:22:26.212 DEBUG InternetModel:98                 Adding internet service: "SomaFM" 
15:22:26.213 DEBUG InternetModel:98                 Adding internet service: "SoundCloud" 
15:22:26.214 DEBUG SpotifyService:77                Spotify system blob path: "/usr/bin/clementine-spotifyblob" 
15:22:26.214 DEBUG SpotifyService:78                Spotify local blob path: "/home/dh/.config/Clementine/spotifyblob/version14-64bit/blob" 
15:22:26.215 DEBUG InternetModel:98                 Adding internet service: "Spotify" 
15:22:26.221 DEBUG NetworkProxyFactory:30           Detected system proxy URLs: ("", "", "", "") 
15:22:26.221 DEBUG CoverProviders:34                Registered cover provider "Amazon" 
15:22:26.221 DEBUG CoverProviders:34                Registered cover provider "Discogs" 
15:22:26.290 WARN  OSD:89                           Error connecting to notifications service. 
15:22:26.296 DEBUG GnomeGlobalShortcutBackend:50    registering 
15:22:26.429 DEBUG MainWindow:194                   Starting 
15:22:26.577 DEBUG MainWindow:245                   Initialising player 
15:22:26.581 DEBUG MainWindow:251                   Creating models 
15:22:26.592 DEBUG MainWindow:269                   Creating UI 
Bus error (core dumped)


It crashes, and I get disk errors.

---

### Post by HuaiDan on 2013-01-20
Starting Amarok with root privileges works fine, except for the errors that come from starting it with root privileges:
```
sudo amarok
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
KGlobal::locale::Warning your global KLocale is being recreated with a valid main component instead of a fake component, this usually means you tried to call i18n related functions before your main component was created. You should not do that since it most likely will not work 
Error: "/var/tmp/kdecache-dh" is owned by uid 1000 instead of uid 0.
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Error: "/var/tmp/kdecache-dh" is owned by uid 1000 instead of uid 0.
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-dh" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-dh" is owned by uid 1000 instead of uid 0.
 QUrl( "http://ws.audioscrobbler.com/2.0/?api_key=&lang=en&method=user.getNeighbours&user=" )  
 QUrl( "http://ws.audioscrobbler.com/2.0/?api_key=&lang=en&method=user.getFriends&user=" )  
 QUrl( "http://ws.audioscrobbler.com/2.0/?api_key=&lang=en&method=user.getTopTags&user=" )  
 QUrl( "http://ws.audioscrobbler.com/2.0/?api_key=&lang=en&method=user.getTopArtists&user=" )  
********************************************************************************************** 
** AMAROK WAS STARTED IN NORMAL MODE. IF YOU WANT TO SEE DEBUGGING INFORMATION, PLEASE USE: ** 
** amarok --debug                                                                           ** 
********************************************************************************************** 
dh@dh-desktop:~$ Expected node absent: topartists 
Expected node absent: friends 
Expected node absent: neighbours 
QMetaObject::invokeMethod: No such method App::onWsError(lastfm::ws::Error)
lastfm::ws::Error 
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Error: "/var/tmp/kdecache-dh" is owned by uid 1000 instead of uid 0.
amarok(4731)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(4731)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(4731)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Error: "/var/tmp/kdecache-dh" is owned by uid 1000 instead of uid 0.
QWidget::insertAction: Attempt to insert null action
amarok(4731)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
QSystemTrayIcon::setVisible: No Icon set
"sni-qt/4731" WARN  15:32:59.238 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (100,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (0,-1) are not possible
QDBusConnection: name 'org.kde.kglobalaccel' had owner '' but we thought it was ':1.10'
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (100,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (0,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (66,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (66,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (73,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (79,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (185,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (185,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (100,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (100,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (100,-1) are not possible
QWidget::setMinimumSize: (Playlist dock/Playlist::Dock) Negative sizes (185,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (129,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (129,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (129,-1) are not possible
Error: "/var/tmp/kdecache-dh" is owned by uid 1000 instead of uid 0.
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (129,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (129,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (129,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (129,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (129,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (129,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (129,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (109,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (129,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (100,-1) are not possible
QWidget::setMinimumSize: (Media Sources dock/BrowserDock) Negative sizes (100,-1) are not possible

```
Without root privileges, it crashes and gives me disk errors:
```
desktop:~$ amarok
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
KGlobal::locale::Warning your global KLocale is being recreated with a valid main component instead of a fake component, this usually means you tried to call i18n related functions before your main component was created. You should not do that since it most likely will not work 
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Error: "/tmp/kde-dh" is owned by uid 0 instead of uid 1000.
Error: "/tmp/kde-dh" is owned by uid 0 instead of uid 1000.
Error: "/tmp/ksocket-dh" is owned by uid 0 instead of uid 1000.
Error: "/tmp/ksocket-dh" is owned by uid 0 instead of uid 1000.

Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
kbuildsycoca4 running...
KCrash: Application 'amarok' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/dh/.kde/socket-dh-desktop/kdeinit4__0
unnamed app(5112): Communication problem with  "amarok" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" "
```

---

### Post by HuaiDan on 2013-01-20
It's definitely related to my user account. I don't get the same issue on other user accounts. Putting my user account into the root group didn't work.

---

### Post by HuaiDan on 2013-01-20
It's the music players that are causing the disk errors when started by my user account. I was getting disk errors when I opened the music folder with Nautilus becasue I had previews enabled, which invoked the music player. I got around that by disabling previews, but Nautilus crashes if I try to go into mp3 file properties to change the associated application.

My user account is really behaving badly when it comes to music players and mp3's all of the sudden. I'm really at a loss as to how to continue troubleshooting this.

---

### Post by HuaiDan on 2013-01-20
I finally fixed it. I found the reason as I was cloning my user account, hoping just to fix the problem.
 While using cp -a to copy all my files over, I got an i/o error while it was trying to copy ~/.gstreamer-0.10/registry.x86_64.bin.
When i deleted this file in the old user account, I was able to start Clementine, but not Amarok.
In the new (cloned)user account, I am able to start both Clementine and Amarok.

Apparently, it was all due to this one corrupt file.

---

### Post by HuaiDan on 2013-01-22
Deleting ~/.kde4 brought back Amarok in the old profile.

---

