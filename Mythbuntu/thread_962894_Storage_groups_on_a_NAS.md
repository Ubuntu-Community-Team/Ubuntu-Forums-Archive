---
title: "Storage groups on a NAS"
date: 2008-10-29
forum: Mythbuntu
---

### Post by Beebock on 2008-10-29
Hi All,

I have just brought online a 1Tb NAS and was pondering the wisdom of creating a storage group that is liked to this. Now the NAS is not going to be used for direct recording, but only for storage post recording / transcoding etc... (see question 3)

There are some questions that I have, and hoping that some of you can answer

1) What is the playback going to be like? ( I have a 54mb wireless network)
2) What would happen should the NAS be off line? Will I loose references to the movies or will myth just not play until available?
3) Is it possible to move movies to the NAS after they have been recorded for 1 week and not watched?

*** edit: I am using NFS protocole

Thanks
Richard

---

### Post by newlinux on 2008-10-30
> **Beebock said:**
> Hi All,

I have just brought online a 1Tb NAS and was pondering the wisdom of creating a storage group that is liked to this. Now the NAS is not going to be used for direct recording, but only for storage post recording / transcoding etc... (see question 3)

There are some questions that I have, and hoping that some of you can answer

1) What is the playback going to be like? ( I have a 54mb wireless network)
2) What would happen should the NAS be off line? Will I loose references to the movies or will myth just not play until available?
3) Is it possible to move movies to the NAS after they have been recorded for 1 week and not watched?

*** edit: I am using NFS protocole

Thanks
Richard
Are you talking storage groups for TV recording, live viewing, or mythvideo?


1. Depends on what types of signals you are trying to play back (HD, SD, Mpeg-2, etc.). And the quality of your wireless network connection. HD Mpeg-2 is unlikely to work well.

2. IF you are talking mythvideo, you'll lose access to the movies. If you do a video scan while this is off, it will ask you if you want to delete the files it can't find from the DB. If you are talking storage groups for liveTV and recordings, you won't have access to either if all your storage groups are on the NAS.

3. Yes, I don't do this, but I'm sure you could set up a cron job if you want to move recordings to be accessible via mythvideo.

---

### Post by Beebock on 2008-10-30
> **newlinux said:**
> Are you talking storage groups for TV recording, live viewing, or mythvideo?


1. Depends on what types of signals you are trying to play back (HD, SD, Mpeg-2, etc.). And the quality of your wireless network connection. HD Mpeg-2 is unlikely to work well.

2. IF you are talking mythvideo, you'll lose access to the movies. If you do a video scan while this is off, it will ask you if you want to delete the files it can't find from the DB. If you are talking storage groups for liveTV and recordings, you won't have access to either if all your storage groups are on the NAS.

3. Yes, I don't do this, but I'm sure you could set up a cron job if you want to move recordings to be accessible via mythvideo.

Hi,

Thanks for the answers. Here are the details

1) it's AVI and the stuff that Myth records. No HD etc.... just box standard TV stuff. The network is a 54Mb strong signal wireless. So far it has been as stable as a rock (2 years...)

2) I was talking about storage groups. I don't want the DB to update itself for the hell of it and loose everything, but by the sound of it this won't happen (thanks)

3) cool. I'll work on that saturday

---

### Post by newlinux on 2008-10-30
> **Beebock said:**
> Hi,

Thanks for the answers. Here are the details

1) it's AVI and the stuff that Myth records. No HD etc.... just box standard TV stuff. The network is a 54Mb strong signal wireless. So far it has been as stable as a rock (2 years...)

2) I was talking about storage groups. I don't want the DB to update itself for the hell of it and loose everything, but by the sound of it this won't happen (thanks)

3) cool. I'll work on that saturday

1. I stream lower bit rate SD stuff on my wireless g, so you have a good shot their if your signal is good.

2. Nope, myth will just complain that it can't find the files. I'm pretty sure it won't do any DB updating.

3. Happy hacking!

---

