---
title: "problem with video playback in 10.04"
date: 2010-05-22
forum: Multimedia Software
---

### Post by halifaxsites on 2010-05-22
I recently installed 10.04 LTS. I am now having problems with video playback. When I watch an .avi file in media player, it will play for a few minutes and then come up with an error:
 pa_stream_writable_size() failed: Connection terminated

When I play them in vlc and kaffine they will play briefly then the sound will cut out.
KMPlayer just stops without an error message.

Any suggestions on what could be causing this?

---

### Post by proggy on 2010-05-22
Did you  add [Medibuntu  ]("https://help.ubuntu.com/community/Medibuntu?action=fullsearch&context=180&value=linkto%3A%22Medibuntu%22")[repository]("https://help.ubuntu.com/community/Repositories")  to Ubuntu?
[HTML]sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update[/HTML]

---

### Post by halifaxsites on 2010-05-22
Yes, that was in another post somewhere. I did that with no avail. :(

---

### Post by proggy on 2010-05-22
There`a bug report [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/496616](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/496616)

---

### Post by halifaxsites on 2010-05-22
Ok, so I am thinking it best to abandon 10.04 until it is a little more stable. I also have a bunch of flash problems that I am not even going to bother trying to figure out.

---

