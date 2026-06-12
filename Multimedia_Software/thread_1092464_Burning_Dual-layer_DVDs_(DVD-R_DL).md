---
title: "Burning Dual-layer DVDs (DVD-R DL)???"
date: 2009-03-10
forum: Multimedia Software
---

### Post by jrj127 on 2009-03-10
I have Ubuntu-8.10 Intrepid Ibex and am trying to burn to DVD-R DL media.  I have Verbatim DVD-R DL media.  I have two burners and neither work with Brasero or K3b:

Sony DRX-830U
TSST SH-S203N


Are there any known hacks or packages I need to install to get this simple feature working?  Both drives definitely support this media.  Thanks!

---

### Post by s.dalas on 2009-03-10
> **jrj127 said:**
> I have Ubuntu-8.10 Intrepid Ibex and am trying to burn to DVD-R DL media.  I have Verbatim DVD-R DL media.  I have two burners and neither work with Brasero or K3b:

Sony DRX-830U
TSST SH-S203N


Are there any known hacks or packages I need to install to get this simple feature working?  Both drives definitely support this media.  Thanks!

Good question i need this too.

---

### Post by cariboo on 2009-03-10
WHat error messages are you getting? I use Verbatim DVD+R DL, and have no problem burning dual-layer disks with k3b. I know there was a problem with Brasero and dual-layer, so I haven't tried it yet.

I always burn dual-layer at the slowest speed my drive will burn. It takes a lot longer, but at least I don't make any coasters. :)

Jim

---

### Post by jrj127 on 2009-03-10
I can't get the original error messages back.  The Ubuntu/GNOME automounter keeps screwing with things.  Brasero and K3b cannot determine that a blank DVD is in the drive because it keeps getting automounted.  Any tips?

---

### Post by jrj127 on 2009-03-16
Bump...

1. How can I prevent Ubuntu's DVD automounting, which does not let K3b or Brasero see the blank DVD?

2. Does anyone have success burning to a DVD-R DL in Ubuntu-8.10 Intrepid Ibex?

---

### Post by taurus on 2009-03-16
What if you don't insert the disc first.  Instead, wait for k3b to ask you to insert the disc.  Then do so.

---

### Post by jrj127 on 2009-03-16
From Brasero, I get this dialog box:

Insert a rewritable or blank disc

Please put a disc, with at least 7.5 GiB free, into the drive.  The following disc types are supported:
DVD+R DL

---

### Post by taurus on 2009-03-16
Have you tried to use DVD+R DL instead of DVD-R DL?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16827151154&Tpk=samsung](http://www.newegg.com/Product/Product.aspx?Item=N82E16827151154&Tpk=samsung) SH-S203N

Which burner are you trying to use, Sony or Samsung?

---

### Post by jrj127 on 2009-03-16
Both burners give the same message.  They are both spec'd to support DVD-R DL.

I only bought DVD-R DL because my home theater DVD player does not support DVD+R.

---

### Post by mc4man on 2009-03-16
> From Brasero, I get this dialog box: ....DVD[COLOR="Red"]+[/COLOR]R DL 

You should try k3b

If no go there Imgburn running in wine works flawlessly

In the the long run DVD-R DL's aren't the way to go as far as DL media
The verbatium +R DL's are far superior media and more likely to work in most standalones. If your standalone doesn't support dvd+r then it may not support the -R DL. 

Most dual layer burners will by default booktype the +R DL media to DVD-ROM, in other words your player will see it as a normal commercial dual layer disk. 
(see screen - notice it says dvd+r dl as the media's booktype but then in the 'last recorded" it shows DVD-ROM

DVD-R and DVD-R DL media cannot be booktyped.

Imgburm can set many players to booktype single layer DVD+r's to dvd-rom also, though it may only be able to in windows wiith some drives. screen 2

---

### Post by jrj127 on 2009-03-29
Thanks for the info about the booktyping.  I did not know the details behind writing DVDs for standalone players.

I bought Memorex DVD+R DL blank media and it works correctly on my standalone DVD player.  Thanks a million!

ISSUE RESOLVED.

---

