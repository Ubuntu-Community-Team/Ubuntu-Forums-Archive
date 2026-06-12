---
title: "How(to) I make jack stop crackle"
date: 2007-01-12
forum: Multimedia &amp; Video
---

### Post by rytmisk on 2007-01-12
Hi

I just managed to get my new laptop (asus a9rp) to play nicely with ubuntu by installing ubuntustudio and upgrading alsa and jackd. It was crackling like h&¤%ll before, but now it sounds smooth with good latency (1.33 ms) without the generic default edgy kernel.

[LIST=1]
[*]Add the following lines to /etc/apt/sources.list (or in synaptic):

```
deb http://apt.64studio.com/64studio/stable/ 64studio main
deb http://archive.ubuntustudio.org/ubuntustudio edgy main

```

NB! DO not perform a system update with the studio64 repository active!!! Deactivate it as soon as this how(to) is finished!

[*]Installed ubuntustudio-audio and ubuntustudio-plugins("apt install ubuntustudio-audio " or synaptic) just to have all themusic  apps I could ever need (almost - a few more are found if you go to [http://devlinuxbr.codigolivre.org.br](http://devlinuxbr.codigolivre.org.br))

[*] I then updated all packages alsa and jack using synaptic -> pressing Status (lower left hand corner) and upgradable.

[*] I rebooted and started Jack Control. After a bit of tweaking I ended up with using these settings:
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=22823&stc=1&d=1168636446[/IMG]
[/LIST]

So now I am happily able to create music again:-)

See ya
Ketil

---

