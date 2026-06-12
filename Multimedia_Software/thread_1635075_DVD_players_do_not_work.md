---
title: "DVD players do not work"
date: 2010-12-01
forum: Multimedia Software
---

### Post by ablot on 2010-12-01
Hi folks,

Before I go into details I just want to say to you that I am amazed at ubuntu ... it works like a dream (well ...almost!). So simple ... so quick ... and so helpful - in most cases ... So I take my hat off to the Ubuntu team ... and to all the other people who have something to do with this distro.

So ... I have what must be just a teething problem.
I wanted to play some DVDs - loaded movie player ... and was told that it could not read 'the resource'. So I tried Kaffeine - similar problem, then Gnome mplayer - it made some truly weird noises on the computer - but no film ... then KM player - nothing ... then Parole - ziltch!

I have now un-installed all of them and I wait,eagerly, to hear any responses.

But be warned ... I know virtually nothing about the technical side of things - so if you want to explain something please, please keep it simple ... don't take it for granted that I will know what to write in the consul ... 

Thanks for your patience ... and sock it to me ... gently.

Ablot

---

### Post by SeijiSensei on 2010-12-01
sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh 
sudo apt-get install smplayer

should get you pretty far down the road.  If you're using Kubuntu, replace "ubuntu" with "kubuntu" above.

---

### Post by endotherm on 2010-12-01
+1 for smplayer.

op, if you continue to have problems with DVDs after installing the ubuntu-restricted-extras package, go to [mediubuntu]("https://help.ubuntu.com/community/Medibuntu"), and follow the repository how to. after you have added the repo, skip the part about "removing the non-free component" and go down to the instructions for installing libdvdcss2 and w32codecs (or w64codecs if you are on a 64bit system.) all the instructions are in terminal commands, but you just copy and paste them into the terminal.

---

### Post by Linux_junkie on 2010-12-01
To watch DVD's through a Ubuntu/Kubuntu system you need to install video and dvd codecs.

The message above telling you to install the restricted extras is only one part of the process you also need to install the following:

Install libdvdcss and libdvdread4, you install these packages by:

sudo apt-get install libdvdread4

sudo /usr/share/doc/libdvdread4/install-css.sh

This should work.

---

### Post by ablot on 2010-12-02
BINGO!! Thanks SeijiSensei ... it worked first time!

Give yourself a biscuit!!

... And thanks guys for your other quick responses.

---

### Post by JustSteph on 2010-12-05
I'm having the same problem, but I'm getting this error when running sudo /usr/share/doc/libdvdread4/install-css.sh

```
--2010-12-05 14:47:43--  http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... failed: No route to host.
Dynamic fetch failed; Falling back to static fetch
--2010-12-05 14:47:52--  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... failed: Connection timed out.
Retrying.

--2010-12-05 14:48:14--  (try: 2)  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb
Connecting to packages.medibuntu.org|88.191.127.22|:80... failed: No route to host.
```

I'm behind a proxy. I have applied it system-wide in preferences, but is this still the problem?

Thanks
Steph

---

### Post by coffeecat on 2010-12-05
I don't know anything about proxies, but the medibuntu server seems OK at the moment, so perhaps the proxy is the problem. Try this. Go to:

[http://packages.medibuntu.org/lucid/libdvdcss2.html](http://packages.medibuntu.org/lucid/libdvdcss2.html)

... and download the libdvdcss2 deb package for your architecture. i386 = 32-bit, AMD64 = 64-bit. Then simply double-click on the downloaded package to install it. That link is for Lucid, although I think the libdvdcss2 package hasn't changed at all for some time, so it should do for other releases as well.

If your proxy prevents you from browsing to that link, you'll have to download the package on another machine outside of a proxy and transfer the file to the machine you want to install it on.

---

### Post by j_keiter on 2010-12-05
Did not work for me.  Installed all the codecs, restricted codecs, medibuntu.   I've tried Movie Player and VLC media player with menus turned off.  I get sound in VLC but no pic.  Trying to play Monster Inc DVD.  Turned off compositing.  Cannot find any more suggestions on the forums???  Ubuntu 10.10

---

### Post by j_keiter on 2010-12-06
p { margin-bottom: 0.08in; }  [COLOR=#000000]Reinstalled VLC media player and it worked!  Reinstalled by using System - Administration - Synaptic Package Manager then search for VLC and check all boxes that come up for reinstall.  Select apply.  Movie DVD's now play well.  No sound on .avi movie files from my digital camera.[/COLOR]

---

### Post by ppjdd on 2010-12-20
Thanks for the info. Was wondering why my DVD's never played.

---

