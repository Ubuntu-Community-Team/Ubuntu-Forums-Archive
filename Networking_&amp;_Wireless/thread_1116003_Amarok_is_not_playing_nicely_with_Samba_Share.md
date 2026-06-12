---
title: "Amarok is not playing nicely with Samba Share"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by dbsoundman on 2009-04-04
I have had this problem before, and somehow fixed it, but now I don't know what I did and I can't make it work again. I have a PC with ubuntu on it in my living room, which is connected to several networked shares on my bedroom PC, one of them being my music share. Previously I had Amarok running on this living room machine connected to a share which contained my entire home drive on the bedroom PC, and I was able, after some fiddling, to get Amarok to properly read the files in my music folder on the share and add them and play them. I have since altered the shares somewhat so that I could share just a few specific folders with a "guest" user on that machine. So now I have a separate share I'm using for the music.

I mounted the share just like I did with the old one in fstab, like so:
```
//192.168.2.2/dan_music /remote/blackdiamond/music cifs -o username=guest,password=xxxxxx,rw,_netdev 0 0
```
This is the EXACT same thing as the share I had before, the only thing that changed is the name of the share and the username. However, now Amarok doesn't read it correctly. I changed the local permissions of the "music" folder in the "remote" directory so that it has 777 permissions, but it still doesn't work. I also tried setting the share as "ro", and using various fmask and dmask options. None of these things have worked. Here is the relevant part of the server's smb.conf file as well:
```
[dan_music]
path = /home/dan/Music
available = yes
browsable = yes
valid users = guest
writable = yes

```
What should I try now? I'm out of ideas. Oh, also, I know this isn't just an Amarok problem because Rhythmbox did the same thing.

Thanks,
Dan

---

