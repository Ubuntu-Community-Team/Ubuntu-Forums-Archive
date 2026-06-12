---
title: "Looking for AVI tag editing tool"
date: 2008-08-30
forum: Multimedia Software
---

### Post by Dolgan on 2008-08-30
Are there meta tags embedded in the avi files produced by a Flip vid camera like the ID3 tags on an mp3 file?  And if there are is there a tool that would allow me to read those tags?  I apologize if this is an ignorant question, but I'd love to attach/manipulate meta data on some of the video files I've created.

Thanks!

---

### Post by lovinglinux on 2008-08-30
I used to manipulate avi tags a while ago, so I know it is possible. Unfortunately, I'm also searching such a tool.

You could consider converting the avi files to matroska. This process can be done very fast, without re-encoding using "MKV Files Creator", which is in the repos.

Matroska is just a container, like AVI, but has more capabilities. You can add multiple audio track, subtitles (srt, ssa...) and tags. This can be done using "MKV Files Creator".

---

### Post by Dolgan on 2008-08-31
Thanks! If I can find no way to directly manipulate those tags then I'll check out matroska. Actually, I'm going to check it out anyway. :)

> **lovinglinux said:**
> I used to manipulate avi tags a while ago, so I know it is possible. Unfortunately, I'm also searching such a tool.

You could consider converting the avi files to matroska. This process can be done very fast, without re-encoding using "MKV Files Creator", which is in the repos.

Matroska is just a container, like AVI, but has more capabilities. You can add multiple audio track, subtitles (srt, ssa...) and tags. This can be done using "MKV Files Creator".

---

### Post by K3N8 on 2009-02-13
Does anybody have an idea how to do this?

---

### Post by dotdot on 2009-05-15
> **K3N8 said:**
> Does anybody have an idea how to do this?

free bump - i have recently bought a fine cam - which produced avi with no datestamp which is not quite what i'd expect.

need to update file with correct data for historical reference.

any help would be much apprec.

---

### Post by dotdot on 2009-05-15
> **dotdot said:**
> free bump - i have recently bought a fine cam - which produced avi with no datestamp which is not quite what i'd expect.

need to update file with correct data for historical reference.

any help would be much apprec.

ok here's a decent if not totally ubu answer.

1/ you've got wine ? cool - if not install it.

2/ download abcavi

3/ it could ask to install by wine - env.

4/ pickup your avi (without useful tags)  drop into wine env

5/ startup abcavi inside wine - inside the panel.

6/ edit  & add your tags... ->>  save - then move your filey to where ever you store your avis..

7/ job done.

cheers

--now where  was i ? ?  
can someone write some software xx.deb pref to do this ? ;)

cheers in adv.

---

### Post by timcredible on 2009-05-15
don't know if avidemux2 does what you're asking or not, but it's worth trying.  avidemux2 is in the repos, just install it via synaptic

---

