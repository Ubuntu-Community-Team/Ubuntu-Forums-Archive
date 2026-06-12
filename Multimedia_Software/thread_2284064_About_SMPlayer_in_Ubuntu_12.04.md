---
title: "About SMPlayer in Ubuntu 12.04?"
date: 2015-06-26
forum: Multimedia Software
---

### Post by remmas-sido on 2015-06-26
Hello guys 
Whenever I tried to open a video using SMPlayer a message pop out telling me this: 
SMPlayer could not identify the MPlayer version you're using.
Version reported by MPlayer:
n r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
Please, select the correct version:
And it gives me three options:
1.0rc1 or older 
1.0rc2
1.0rc3 or newer
My question is: which one should I pick from the three options?

---

### Post by monkeybrain20122 on 2015-06-26
1.0rc3 and newer.

BTW How did you install Smplayer? If you installed it from 12.04's repo it is a very old and outdated version.You should upgrade it 
```
sudo add-apt-repository ppa:rvm/ppa 
sudo apt-get update
sudo apt-get upgrade
```

[https://launchpad.net/~rvm/+archive/ubuntu/ppa?field.series_filter=precise](https://launchpad.net/~rvm/+archive/ubuntu/ppa?field.series_filter=precise)

---

### Post by remmas-sido on 2015-06-26
> **monkeybrain20122 said:**
> 1.0rc3 and newer.

BTW How did you install Smplayer? If you installed it from 12.04's repo it is a very old and outdated version.You should upgrade it 
```
sudo add-apt-repository ppa:rvm/ppa 
sudo apt-get update
sudo apt-get upgrade
```

[https://launchpad.net/~rvm/+archive/ubuntu/ppa?field.series_filter=precise](https://launchpad.net/~rvm/+archive/ubuntu/ppa?field.series_filter=precise)
Yes, it's from the repo.

---

