---
title: "Missing In Action: All the sounds"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by Speque on 2008-02-27
Hello.

My problem is that I have lost all the audio in my system. Th story goes like this:

I saw this post 

[http://4front-tech.com/forum/viewtopic.php?p=7485#7485](http://4front-tech.com/forum/viewtopic.php?p=7485#7485)

and as I have an X-Fi sound card in my machine I decided to give it a try. I installed the deb-package and true enough, alsatest was able to get sounds out of my X-Fi-card. Nothing else worked though, so I decided to go back my old ways, which is using the integrated sound chip of the main board in Ubuntu and the X-Fi-card when playing games in Windows. So I removed oss-linux, but then I realised I have no sound at all. System -> Preferences -> Sound does not recognize any sound card at all. Alsamixer returns this error

```
alsamixer: function snd_ctl_open failed for default: No such device
```

and command 

```
asoundconf list 
```

returns an empty list.

```
lspci
```

gives me this 

```
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:08.0 Multimedia audio controller: Creative Labs SB X-Fi
02:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
```

You can see the nForce2 AC97 sound controller there, but how to get it in use?

Anyone, can you help me?

---

### Post by Speque on 2008-03-05
I rudely bump up the thread, as a solution is still not found.

---

