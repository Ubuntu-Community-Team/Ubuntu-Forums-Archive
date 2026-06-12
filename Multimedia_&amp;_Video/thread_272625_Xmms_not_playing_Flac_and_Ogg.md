---
title: "Xmms not playing Flac and Ogg"
date: 2006-10-06
forum: Multimedia &amp; Video
---

### Post by Theimon on 2006-10-06
As the title suggests, my Xmms is not playing Flac and Ogg files. Ogg support is native in Xmms from version 1.2.4, I have 1.2.10. When I load Ogg files and select them to be played, Xmms skips to the next song just like that. So I get nothing at all.
Same goes for Flac files. I have installed Flac, xmms-flac, libflac........you name it, I got it. All repos enabled.
Strange thing is, Totem and Songbird (a multiplatform Itunes ripoff) play the flac and ogg files fine, so if anyone can shed some light on this........

```

dpkg -l | grep xmms
```
shows me it does see the flac plugin but it still doesn't work.

---

### Post by Theimon on 2006-10-07
Please discard this post, it turned out to be coding errors in multiple audiofiles. Xmms is playing flac as I write this. Sorry for taking up space here, the problem was persistent but eventually not a problem at all.

---

### Post by DantePasquale on 2007-11-15
What did you or anyone do to get xmms to play flac audio? I created a bunch of flac audio files using Sound Juicer, flac --test shows they are OK, but can't get xmms to play them. When I look at Preferences -> Input Plugins - no flac plugin is listed. I have  xmms-flac                                        1.1.2-3ubuntu1.1 and dpkg -l | grep xmms shows xmms-flac is installed. I've tried reconfiguring/reinstalling, but no luck. Totem, mplayer play them, but xmms and audacity don't.

Ideas?

---

### Post by LondoMollari on 2007-11-18
Same problem here. dpkg -l | grep xmms shows the xmms-flac plugin, but it does not appear in the list of input plugins under preferences. However, this problem occured after a recommended update (update manager) just about a week ago, and I did notice that some of the upgrades had something to do with flac (libflac or something... don't know for sure)... I don't know how to go back to the previous settings, but maybe some others out there know... Is there some kind of log-file were I can check which updates that was actually installed? That would be a start...:)

by the way I'm using 7.04 Feisty at the moment

---

### Post by LondoMollari on 2007-11-18
Alright.... look and thou shalt find...

here's the log from the update that effed xmms-flac up for me

Commit Log for Wed Nov 14 08:06:51 2007

Upgraded the following packages:
cdrecord (9:1.1.2-1) to 9:1.1.2-1ubuntu1
genisoimage (9:1.1.2-1) to 9:1.1.2-1ubuntu1
libflac7 (1.1.2-5ubuntu2) to 1.1.2-5ubuntu2.1                  <<<<<<
libpoppler1 (0.5.4-0ubuntu8.1) to 0.5.4-0ubuntu8.2
libpoppler1-glib (0.5.4-0ubuntu8.1) to 0.5.4-0ubuntu8.2
libpoppler1-qt4 (0.5.4-0ubuntu8.1) to 0.5.4-0ubuntu8.2
mkisofs (9:1.1.2-1) to 9:1.1.2-1ubuntu1
wodim (9:1.1.2-1) to 9:1.1.2-1ubuntu1
xmms-flac (1.1.2-5ubuntu2) to 1.1.2-5ubuntu2.1         <<<<<<<<

i'm guessing one of <<<<  messed things up... question is, how to go back to the previous versions?

---

### Post by LondoMollari on 2007-11-18
Well guess downgrading was'nt that difficult after all... In synaptic, search for "flac" and locate libflac7, to downgrade from 2.1 to 2, click package in the to menu, and go to force version, now select the previous version... do the same for xmms-flac.... my xmms now plays flac files again :)

---

### Post by ske1fr on 2007-11-18
This happened to me tonight with my older Kubuntu Dapper machine - the flac file I last played was still there in the playlist but after the latest flac updates there was "no input plugin" to handle it.  Downgrading as per your instructions has restored flac playback capability in xmms.  Sadly this update was to counteract a security vulnerability in the flac libraries ([http://www.ubuntulinux.org/usn/usn-540-1]("http://www.ubuntulinux.org/usn/usn-540-1") refers), so downgrading leaves your system still vulnerable, but at least it still works.  Just beware the playing of files from untrusted sources until a fresh update is released.

Thank you, your Excellency :) .

---

### Post by stchman on 2007-11-19
> **LondoMollari said:**
> Well guess downgrading was'nt that difficult after all... In synaptic, search for "flac" and locate libflac7, to downgrade from 2.1 to 2, click package in the to menu, and go to force version, now select the previous version... do the same for xmms-flac.... my xmms now plays flac files again :)

Hopefully the Ubuntu team will correct the problem it introduced in the lib upgrade.  It has only been about 5 days so a  fix should be coming along soon.

---

### Post by ubu-for on 2008-01-07
> **LondoMollari said:**
> Well guess downgrading was'nt that difficult after all... In synaptic, search for "flac" and locate libflac7, to downgrade from 2.1 to 2, click package in the to menu, and go to force version, now select the previous version... do the same for xmms-flac.... my xmms now plays flac files again :)

I had the same problem with XMMS.

Thank you!

---

### Post by glotz on 2008-01-07
Note that you're vulnerable now since you downgraded. I wish we'd get a proper fix...

---

### Post by ubu-for on 2008-01-08
> **glotz said:**
> Note that you're vulnerable now since you downgraded. I wish we'd get a proper fix...

In general or only if XMMS gets a connection to the web?

---

### Post by glotz on 2008-01-08
Bad things can happen if you've got evil flac files. No need for a web connection. [http://www.ubuntu.com/usn/usn-540-1](http://www.ubuntu.com/usn/usn-540-1)

You can find the latest security notices on ubuntu.com > news > sec notices.

---

### Post by ubu-for on 2008-01-09
> **glotz said:**
> Bad things can happen if you've got evil flac files. No need for a web connection.

Thanks!

---

### Post by glotz on 2008-01-09
You're welcome.

---

### Post by rasemmi on 2008-04-06
Hiho,

had the same problem with xmms and xmms-flac plugin under feisty 7.04: No playback and xmms-flac plugin not listed in xmms options although installed.

So I kept the updated lib:
libflac7, 1.1.2-5ubuntu2.1

BUT

installed from the original debian repo using gdebi:
xmms-flac, 1.1.2-8

Works perfectly well for me! :) Due to the updated libflac I hope the security issue mentioned above keeps solved too.

Regards raLLi

---

