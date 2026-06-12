---
title: "Automatic Buffer Copy When Opening Files On Samba Shares"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by fleder on 2009-07-01
Hey guys,

I am accessing a Debian Lenny-hosted Samba share with my Kubuntu computer.

Typing smb://server-name/share-name into Dolphin's address line doesn't get me far, but I'm not a madman and don't expect those kind of tricks to work on Linux machines (only my Windows computer can resolve those network names) ... however, I can access it with smb://server-ip/share-name, which is okay for me.

There are some large files stored on that share, and I want to open them right in place. For instance, there's an about 4GB big video file I'd like to watch over the network. It's no problem at all if I use the Windows PC. However, Kubuntu insists upon copying the whole freaking file before opening it with a video player, which is just ridiculous, because I neither have that kind of time nor enough space in /var/tmp!

I can't find any option in the system settings and after searching these forums for half an hour without success I decided to have a go and whine here a bit.
And no, it doesn't seem to depend on which program I open the file with, it's the same with VLC Media Player, MPlayer and even Kate!
Where the heck can I beat some reason into KDE to make it stop doing stupid things like that?

It's a Kubuntu 9.04 installation:
Linux my-pc 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:55:09 UTC 2009 x86_64 GNU/Linux

Cheers,
fleder

---

### Post by zaeron on 2009-07-01
Same here. But Dragon Player seems to play vids in place.

---

