---
title: "Brand New Linux/Ubuntu User"
date: 2010-03-28
forum: Multimedia Software
---

### Post by Disco Soup on 2010-03-28
Old 'puter died when I downloaded a bad copy of the Love Never Dies Soundtrack, so, fed up with Windows malware I decided to convert to Linux.

I mostly use the computer to watch Doctor Who and listen to music. I installed VLC to watch DVDs, but right now it only plays the audio and the image is black.

I also installed Kaffeine, but being new to Ubuntu, I'm not sure how to download and install codecs for the video.

Any help would be appreciated.

---

### Post by snowpine on 2010-03-28
Welcome to the forums Disco!

Here's how to play DVDs in Ubuntu: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

I find the easiest way to get lots of yummy codecs is to open a terminal (Applications->Accessories->Terminal) and type:

```
sudo apt-get update
sudo apt-get install ubuntu-restricted extras
```

You'll be prompted for your password... the password will not show on the screen while you're typing it, but don't worry. :) ubuntu-restricted-extras is a "meta-package" that pulls in a lot of good stuff like mp3 support, flash video, Windows media format, etc.

---

