---
title: "ffmpeg libfaac was working, now not"
date: 2012-06-20
forum: Multimedia Software
---

### Post by CoximusPrime on 2012-06-20
Hi guys,

I don't know what I could have done here but I'm running the command ```
ffmpeg -i audio_orig -acodec libfaac -ab 128K -ac 2 audio.aac
``` which worked fine last night, but this morning now gives me the error "unknown encoder 'libfaac'

I installed libfaac using the packages from Medibuntu as described on here [http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283) using the commands 

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```

and 

```
sudo apt-get install ffmpeg libavcodec-extra-52
```

does anybody know what could have changed or how I can get this working again??

Cheers

---

### Post by CoximusPrime on 2012-06-20
it's ok, I've found the problem and a work around on the last page of the thread mentioned above.

---

