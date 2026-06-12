---
title: "two installs of an app, one via apt, one via snap?"
date: 2020-03-28
forum: Multimedia Software
---

### Post by babag on 2020-03-28
i'm wondering if i can use the native apt install of an app for some things and also have a snap install for others. i use ffmpeg some and the apt repository has an older version. for some things, i'd like to be able to use the newer version in the snap store. is this possible? is there any info on how to go about this? normally, i'd just uninstall the apt version but i'm using ubuntu studio and removing ffmpeg breaks a lot of things for me.

thanks,
babag

---

### Post by mc4man on 2020-03-28
You can have both the .deb  ffmpeg package & snap ffmpeg installed at same time, no conflict there..
When you have both then the .deb binary(s) will always be used over the snap binary(s) as  /snap/bin is last in $PATH
Only way to use the snap ffmpeg binary is to explicitly do so, i.e /snap/bin/ffmpeg blah, blah or snap run ffmpeg blah, blah 

If an application uses the ffmpeg binary then it'll use 1st one found in $PATH.

---

### Post by babag on 2020-03-28
thanks, mc4man! that's actually great. lets me keep the ubuntu studio install intact while getting the benefits of some newer conversion features. very helpful.

thanks again,
babag

---

