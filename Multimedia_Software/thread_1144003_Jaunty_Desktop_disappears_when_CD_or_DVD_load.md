---
title: "Jaunty Desktop disappears when CD or DVD load"
date: 2009-04-30
forum: Multimedia Software
---

### Post by raymondvillain on 2009-04-30
Running Jaunty.  Everything worked fine in Intrepid, but now when I put an audio CD or a DVD into my CD/DVD ROM drive all Desktop icons disappear.  Even if I restart, as long as the disc is in the drive, no desktop icons.  If I remove the disc from the drive, the icons stay lost in the cosmos until I restart (without a disc in the drive).

With an audio CD in the drive, I can play tracks with VLC, Amarok, and Rythmbox.

With a DVD in the drive, VLC will open, but as soon as I tell it to play the DVD it vanishes.

I have carefully followed the instructions at [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).

Gnome MPlayer does not work, but I wasn't able to use it in Intrepid, either, so I don't think it is any different now.

Also, Audio CD Extractor will not open.

Any suggestions would be greatly appreciated.

Thanks in advance!

---

### Post by deletarus on 2009-05-02
I'm having similar issues. All desktop icons will disappear for seemingly random reasons and not re-appear until either I restart or once they re-appeared after some magic when I opened some random folder. I thought it had something to do with WINE or my mounted network drives, but it very well could be the DVD problem you're experiencing.

I also had difficulties with VLC in 9.04. Even after installing libdvdread4 and libdvdcss2 (I fixed it by installing the version in libdvdread4 after reading the instructions) but I still have issues when using the right click "open with VLC" option; VLC just crashes instantly. I have to add each file to the playlist in order for it to play properly.

I'm also unable to re-allow the Ctrl-Alt-Backspace command even when running the "sudo dontzap --disable" command (and yes I have dontzap installed).

9.04 also doesn't seem as snappy as it should be. I experience frequent slowly responding apps. My system is a Q9450 2.6GHz quad with 4GB ram and an 8800gt so I really shouldn't be seeing too many slow downs, especially only running a couple of apps.

I suppose we should probably be submitting these as bugs... Maybe I'll get around to it later.

On the plus side, I do think it boots pretty quickly.

[edit]
@raymondvillain 
I think this will fix your VLC issues.
after installing libdvdread4 from the package manager, run this command.
/usr/share/doc/libdvdread4/install-css.sh

[edit2]
nmind about the Ctrl-Alt-Backspace. It works now, I think I just needed a good restart after running the command.

---

### Post by deletarus on 2009-05-02
Just found this as well. It might help with the disappearing desktop. I'll try it when I finish burning some DVDs...

[https://lists.ubuntu.com/archives/ubuntu-burning/2009-April/008678.html](https://lists.ubuntu.com/archives/ubuntu-burning/2009-April/008678.html)
"
Chris,

I'm not registered to post on the forums.

The easiest workaround is install nautilus-cd-burner.  This has the
side-effect of un-installing two brasero packages, and fixes the
disappearing desktop problem.

We'll be able to re-install brasero when the problem is fixed, although
right now I don't see any big advantages to it.

Hope this helps,

Steve
"

It looks like brasero may be to blame.

You'd think these things would get caught while Jaunty was still in Alpha or Beta. Oh well. I'm sure they'll get all the kinks out eventually.

---

### Post by raymondvillain on 2009-05-04
That was it, delatarus.  Thanks for the info.  Now my desktop icons stick around and Nautilus works.

Amazing what one bit of advice can do.

---

