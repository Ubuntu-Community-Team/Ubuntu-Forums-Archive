---
title: "PS3 - Play content from networked windoez share"
date: 2009-01-19
forum: Multimedia Software
---

### Post by kleptik on 2009-01-19
Hello All,
Trying to decide on what apps I need to accomplish the following:
I have a windows "Server" with all my DVD's ripped to a shared folder in the format:
serverName/movies/superCoolMovie/video_ts/ifo and multiple vobs
(These movies are all unencrypted)

From my PS3 I would like to use my sixaxis controller to navigate a 'Library' including dvd movie covers etc and start playing the movie.

I was thinking xubuntu and freevo? Does this make sense, or is there a better solution or combination I should consider?

It seems allot of the posts I read have something streaming the content from the server to the ps3. This isn't what I want to do, I want to have no dependency on the server other then it being up and sharing the folder.

Additional note; I don't want to have to rename my movie files, merge vobs, or re-encode them. :)

Thanks for your expertise.

:popcorn:

---

### Post by kleptik on 2009-01-19
I'm tempted to bump this as I would love to get this running Asap, but I'll just wait for a reply. :)

---

### Post by kleptik on 2009-01-19
Anyone have any pointers? Should I have posted this in a more applicable forum? If so, what might that be? 

Thanks!

---

### Post by kleptik on 2009-01-20
Hoping to get some advice on this today. Thanks!

---

### Post by Chris Musampa on 2009-01-20
As far as I'm aware (I'm no expert on the subject) PS3 can't access windows/linux shares directly so you would need some kind of media server (dlna) on the PC.  I believe Windows media player can so it, also Tversity, for linux there is Mediatomb.

I never tried it with dvd format media.

---

### Post by kleptik on 2009-01-20
> **Chris Musampa said:**
> As far as I'm aware (I'm no expert on the subject) PS3 can't access windows/linux shares directly so you would need some kind of media server (dlna) on the PC.  I believe Windows media player can so it, also Tversity, for linux there is Mediatomb.

I never tried it with dvd format media.

Was so excited to see a reply to my post made by somone other than me. :) Thanks..

I guess the buck would stop there if I wasn't even able to access the share. I really don't want my 'Windows Server' impacted by having to run an additional tool. Hmm. Wonder if it's something like a Service that runs to provide the files. I've seen how Windows Media will server the files to the GameOS but they way in which it serves them dosen't fit my needs as it dosen't treat multiple vobs as 1 movie.

---

### Post by Chris Musampa on 2009-01-20
> **kleptik said:**
> Was so excited to see a reply to my post made by somone other than me. :) Thanks..

I guess the buck would stop there if I wasn't even able to access the share. I really don't want my 'Windows Server' impacted by having to run an additional tool. Hmm. Wonder if it's something like a Service that runs to provide the files. I've seen how Windows Media will server the files to the GameOS but they way in which it serves them dosen't fit my needs as it dosen't treat multiple vobs as 1 movie.

I think you would have to accept *some* resources being used on the serving PC, how much depends on whether there is on-the-fly transcoding going on (might not be necessary as PS3 can play MPEG2).

Regarding the multiple VOB issue, I think its a case of trying the different software until you find one which serves a VIDEO_TS directory as a single movie.  There are several options available but I came across this:
[http://code.google.com/p/ps3mediaserver/](http://code.google.com/p/ps3mediaserver/)
No idea how good it is but it does specifically claim "DVD ISOs images / VIDEO_TS Folder transcoder" in its feature list.

HTH

---

