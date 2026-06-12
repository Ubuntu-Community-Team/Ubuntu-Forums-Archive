---
title: "ubuntu 12.04 corrupted videos"
date: 2012-12-10
forum: Multimedia Software
---

### Post by sanghei on 2012-12-10
hello everyone,

so after upgrade my ubuntu 10.04 to 12.04 a LOT of my videos are now corrupted :(

videos that i cannot download somewhere else, some of them even play audio only, but most of them are completly dead


any ideas?

thanks

---

### Post by Bucky Ball on 2012-12-10
Sure it's the videos that are corrupted or are you missing the codecs to play them??? Have you only tried them out on the Ubuntu install? Did you upgrade through the update manager or a fresh install?

The former can be problematic and may need some tweaking. If the former could also be there has been a mix up with codecs or something video related. 10.04 codecs may remain and not be compatible and you might need to install newer version to suit 12.04.

Try this in the terminal, one command at a time:

```
sudo apt-get update
sudo apt-get upgrade
```That will upgrade all packages, not the distro to 13.04. Might just fix something. If you get an error from the upgrade command please post it back here in full between [code] tags.

---

### Post by sanghei on 2012-12-10
i have all codecs, i think thats not the problem 

thanks

---

### Post by andrew.46 on 2012-12-11
Can I suggest you try SMPlayer to play these videos? Download in this fashion:

```
sudo apt-get smplayer mplayer
```

in a terminal window. Then try and play one of your troublesome videos again and if it fails post the SMPlayer and MPlayer logs here. These can be seen in Options --> View Logs.

---

### Post by NightsShadeQueen on 2012-12-11
What's the extension on these video files?

Do they work on anyone else's computer?

---

### Post by Bucky Ball on 2012-12-11
> **sanghei said:**
> i have all codecs, i think thats not the problem 

thanks

Glad you're so sure. The point I'm trying to make is if you did and upgrade through the update manager, you may have all the codecs, may have, but they may be 10.04 codecs and incompatible with 12.04 LTS. Strange mix ups can happen with upgrades of this kind, especially if you have installed codecs manually. They won't necessarily be upgraded.

---

### Post by Bucky Ball on 2012-12-11
> **sanghei said:**
> i have all codecs, i think thats not the problem 

thanks

Glad you're so sure. The point I'm trying to make is if you did an upgrade through the update manager, you may have all the codecs, may have, but they may be 10.04 codecs and incompatible with 12.04 LTS. Strange mix ups can happen with upgrades of this kind, especially if you have installed codecs manually. They won't necessarily be upgraded. 

As asked by NightShadeQueen, have you tried these files on another machine? I really can't see how an upgrade can 'corrupt' a video file. There would be some other explanation. Wipe them into oblivion, yes, but corrupt them? Never heard of it ...

Pretty hard to help much further without more information. If you have already solved this problem, please mark the thread that way from 'Thread Tools' above and give an explanation of how to help others. Thanks.

---

### Post by sanghei on 2012-12-11
thank you all for your time and sorry,

the problem seems to be with the standar movie player, any other from VLC to SMPlayer are able to play those. 

i should have tried a little bit more before posting

once again thanks !

---

### Post by Bucky Ball on 2012-12-11
No problems. Enjoy the OS and the forums and see you round the place. ;)

---

