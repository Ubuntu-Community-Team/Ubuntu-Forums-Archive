---
title: "Problem with smplayer"
date: 2009-04-21
forum: Multimedia Software
---

### Post by colau on 2009-04-21
Hi,
I installed smplayer.
But it is not playing the video file like "dbgt38.rmvb".
It is playing the audio of that file but there no picture(black screen).

---

### Post by rvm4000 on 2009-04-21
Install the w32codecs (or w64codecs) package.

You can find it in [medibuntu](http://www.medibuntu.org/).

---

### Post by colau on 2009-04-22
> **rvm4000 said:**
> Install the w32codecs (or w64codecs) package.

You can find it in [medibuntu](http://www.medibuntu.org/).

Would you please tell how to install it.
I downloaded it from that link extracted.

---

### Post by andrew.46 on 2009-04-22
Hi colau,

> **colau said:**
> Would you please tell how to install it.
I downloaded it from that link extracted.

If you have downloaded a single .deb file you may have chosen the hard way to accomplish this :-). If you have a look at this page:

Medibuntu
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

You will see details of how to add the Medibuntu repository to your system's list of APT repositories. When you have done this you can download the w32codecs or w64codecs as you normally do. Can I suggest that you also download MPlayer from here? It is a more capable version than the Ubuntu repository version.

If all the above suggestions do not allow you to play your rmvb file try adding libstdc++5 from the Ubuntu repositories, I am not sure if this little oddity has been sorted out yet or not.

All the best,

Andrew

---

### Post by colau on 2009-04-23
> **andrew.46 said:**
> Hi colau,



If you have downloaded a single .deb file you may have chosen the hard way to accomplish this :-). If you have a look at this page:

Medibuntu
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

You will see details of how to add the Medibuntu repository to your system's list of APT repositories. When you have done this you can download the w32codecs or w64codecs as you normally do. Can I suggest that you also download MPlayer from here? It is a more capable version than the Ubuntu repository version.

If all the above suggestions do not allow you to play your rmvb file try adding libstdc++5 from the Ubuntu repositories, I am not sure if this little oddity has been sorted out yet or not.

All the best,

Andrew
Downloaded the win32codecs tarball and extracted it and put it in 
/usr/lib/codecs(making codecs directory)
/usr/lib/win32(making win32 directory)
Installed libstdc++6.
libstdc++5 may be broken.

It's working for now.

---

