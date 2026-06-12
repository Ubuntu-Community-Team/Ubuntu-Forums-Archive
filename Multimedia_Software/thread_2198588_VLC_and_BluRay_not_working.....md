---
title: "VLC and BluRay not working...."
date: 2014-01-09
forum: Multimedia Software
---

### Post by Jamie_Edwards on 2014-01-09
Hi guys,

I've tried quite a few fixes for this problem, but none seem to be working. I've tried to install the "KEYDB.cfg" into my .conf/aacs directory, but the following error gets thrown up inside vlc:

"BluRay Error:
    No valid processing key found in AACS config file."

How can I solve that issue, because I've literally just bought "Star Trek Into Darkness" today ( on blu ray obviously ) and I'd like to watch it asap, and in linux too!

Thanks guys

Jamie.

---

### Post by andrew.46 on 2014-01-09
> **Jamie_Edwards said:**
>  I've tried to install the "KEYDB.cfg" into my .conf/aacs directory [...].

I presume that this is a typo? The correct location is of course $HOME/.config/aacs. On my own system for example:


```

andrew@corinth:~$ find $HOME -iname keydb.cfg
/home/andrew/vlc_build/libaacs-0.7.0/KEYDB.cfg
[COLOR="#FF0000"]**/home/andrew/.config/aacs/KEYDB.cfg**[/COLOR]

```

---

### Post by Jamie_Edwards on 2014-01-10
Typo? On my system it's here:

```

jamie@jamie:~$ find $HOME -iname keydb.cfg
/home/jamie/.config/aacs/KEYDB.cfg

```

EDIT... I now know what you mean by typo... Yeah, it was supposed to be "~/.config/aacs/KEYDB.cfg" XDv

---

### Post by andrew.46 on 2014-01-10
My only other thought is to try with MakeMKV and stream to vlc or MPlayer, otherwise you may be in a little trouble :(

---

### Post by Jamie_Edwards on 2014-01-10
only problem with that is that it costs to use makemkv after 30 days doesn't it?

---

### Post by andrew.46 on 2014-01-10
Hmmmm.... unless things have changed, which is always possible, it is time limited for 60 days at which time you will need to install the newest version. A quote from the website confirms this:

```

Program is time-limited -- it will stop functioning after 60 days. You can always download the
latest version from makemkv.com that will reset the expiration date.

```

---

