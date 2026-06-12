---
title: "Fixed xmltv-util package for Mythbuntu: when? Workaround?"
date: 2010-10-29
forum: Mythbuntu
---

### Post by enrico123 on 2010-10-29
Hi,

about 20 days ago the XMLTV grabber tv_grab_ch_search stopped working after a layout change of grabbed homepage.

After a few days I've seen that at sourceforge the bug has been fixed.

My question is when the fix will be released and included in a new xmltv-util package for Ubuntu/Mythbuntu.
How long will it take presumably till it will be abailable?

Is there a workaround, for the case that waiting for the package will take long time?

I have seen that it's possible to download the nightly sources and to generate the code first with perl and then with make and to install it with make install.

But I've a few concerns about this, because it could mess the mythbuntu installation and prevent a later uninstall of the workaround and consequent installation of the stable package once that it will be available.

Any suggestion?

Many thanks!
Enrico

---

### Post by LowSky on 2010-10-29
have you installed the mybuntu autobuild repo? if no you can enable it here:
[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

it is the only way to get mythtv fixes between ubuntu upgrades.

---

### Post by ian dobson on 2010-10-29
Hi,

I just downloaded the daily build, followed the instructions in the readme file (Makefile.PL,make,make test,make install) the copied the tv_grab_ch_search from /usr/local/bin to /usr/bin).

After running the grabber with the --configure option and manually correcting the xmltv id's in the channel table in mythtv, the script worked for me. I only need afew channels (3+,3sat,Pro7) but the epg appears to be correct. 

Regards
Ian Dobson

---

### Post by nickrout on 2010-10-29
> **LowSky said:**
> have you installed the mybuntu autobuild repo? if no you can enable it here:
[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

it is the only way to get mythtv fixes between ubuntu upgrades.

It's not an update to mythtv, it's an update to xmltv. The question is being posed in the wrong forum.

However just downloading the new xmltv tarball and extract the grabber you want to use, put it in /usr/bin/

---

### Post by superm1 on 2010-10-30
To get bugs fixed in Ubuntu, you need to file them first.  You can do so using the "ubuntu-bug" tool and the package name.
Eg:

```
ubuntu-bug xmltv
```

Since you know it's been fixed upstream, if you can provide a link to the exact diff that fixed it, that will help to get the fix included.

---

