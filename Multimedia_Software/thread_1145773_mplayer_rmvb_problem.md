---
title: "mplayer rmvb problem"
date: 2009-05-01
forum: Multimedia Software
---

### Post by tomcheng76 on 2009-05-01
Hello,
[INDENT]I just upgrade from Interpid to Jaunty amd64, fixed compiz startup problem, so far so gd.[/INDENT]
[INDENT]when i close the gmplayer while it is playing .rmvb, it shows "MPlayer interrupted by signal 11 in module: uninit_vcodec".[/INDENT]
[INDENT]Installed mplayer version is 2:1.0~rc2-0ubuntu19+medibuntu1 from jaunty medibuntu repository.[/INDENT]
[INDENT]Interpid don't have such problem at all. Please help, thanks in advance:)[/INDENT]

---

### Post by andrew.46 on 2009-05-02
Hi tomcheng,

> **tomcheng76 said:**
> 
when i close the gmplayer while it is playing .rmvb, it shows "MPlayer interrupted by signal 11 in module: uninit_vcodec". Installed mplayer version is 2:1.0~rc2-0ubuntu19+medibuntu1 from jaunty medibuntu repository

Unfortunately even the Medibuntu MPlayer is quite dated and I would suggest as a first start that you install a newer version. RVM has a PPA here:

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

that will give a much newer version which may very well eliminate the problem for you. I would also suggest using SMPlayer rather than gmplayer which is in the process of being slowly abandoned by even the MPlayer developers. A decent copy of SMplayer can be found in the Ubuntu repository.

I hope this fixes the problem for you,

Andrew

---

### Post by tomcheng76 on 2009-05-02
> **andrew.46 said:**
> Hi tomcheng,



Unfortunately even the Medibuntu MPlayer is quite dated and I would suggest as a first start that you install a newer version. RVM has a PPA here:

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

that will give a much newer version which may very well eliminate the problem for you. I would also suggest using SMPlayer rather than gmplayer which is in the process of being slowly abandoned by even the MPlayer developers. A decent copy of SMplayer can be found in the Ubuntu repository.

I hope this fixes the problem for you,

Andrew
Thanks for the rvm mplayer svn repo.
I think the problem is fixed.
smplayer has too many control, that's why i try to avoid it.:P

---

