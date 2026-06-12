---
title: "Banshee freezing very often on 12.04"
date: 2012-05-11
forum: Multimedia Software
---

### Post by mtclare on 2012-05-11
I did not have this problem with  Ubuntu 11.10, but since installing 12.04, banshee will freeze every  time I switch songs or every other song.  It returns control after one  to two minutes or so, but happens so often that it is becoming unusable  as my music player.
 I noticed these warnings when running banshee --debug:
[1 Warn  18:17:38.242] Failed to load media-player-info file for 1
 And also:
[8 Warn  18:17:39.401] Failed to start DAAP client - System.Exception:  No Zeroconf providers could be found or initialized. Necessary daemon  may not be running. (in `Mono.Zeroconf')
  at Mono.Zeroconf.Providers.ProviderFactory.GetProviders () [0x00000] in <filename unknown>:0
  at Mono.Zeroconf.Providers.ProviderFactory.get_DefaultProvider () [0x00000] in <filename unknown>:0
  at Mono.Zeroconf.Providers.ProviderFactory.get_SelectedProvider () [0x00000] in <filename unknown>:0
  at Mono.Zeroconf.ServiceBrowser..ctor () [0x00000] in <filename unknown>:0
  at Daap.ServiceLocator.Start () [0x00000] in <filename unknown>:0
  at Banshee.Daap.DaapService.ThreadedInitialize () [0x00000] in <filename unknown>:0
 Also:
michael@michael-122-CK-NF68:~$ apt-cache policy banshee
banshee:
  Installed: 2.4.0-2ubuntu1
  Candidate: 2.4.0-2ubuntu1
  Version table:
 *** 2.4.0-2ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe i386 Packages
        100 /var/lib/dpkg/status

---

