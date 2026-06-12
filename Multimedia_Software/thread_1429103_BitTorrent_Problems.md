---
title: "BitTorrent Problems"
date: 2010-03-13
forum: Multimedia Software
---

### Post by Wiedzmin on 2010-03-13
Hi,

My BitTorrent clients freeze the second I give a file to download. This happens regardless of the files I download, trackers, or clients. I tried all sorts of different things but cannot seem to pinpoint the problem.

Any ideas?

Thank you in advance.

---

### Post by wojox on 2010-03-13
This may help. I noticed with a few tweaks I was able to speed up mine: [BitTorrent optimization and troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=1259923")

---

### Post by lovinglinux on 2010-03-13
What client are you using?

---

### Post by perham on 2010-03-13
use deluge. (I'm assuming you're using transmission right now)

---

### Post by Wiedzmin on 2010-03-13
I normally use Transmission, but the same problem occurs with BitStormLite and BitTornado as well. Will Deluge really help?

---

### Post by perham on 2010-03-13
> **Wiedzmin said:**
> I normally use Transmission, but the same problem occurs with BitStormLite and BitTornado as well. Will Deluge really help?

it's always good to try. it's the most bug free bittorrent software for linux I came across yet. if it freezes too, then either it's something wrong with your network settings or your isp is blocking something.

---

### Post by Wiedzmin on 2010-03-13
I just tried it. Works great so far! Amazing speeds too. Thank you so much.

Though it is still interesting why all those other clients did not work.

P.S. Wojox, LovingLinux -
Did not get a chance to look at it thoroughly yet, but thank you for the guide, I am sure I will make use of it quite soon. =)

---

### Post by lovinglinux on 2010-03-13
> **perham said:**
> it's always good to try. it's the most bug free bittorrent software for linux I came across yet. if it freezes too, then either it's something wrong with your network settings or your isp is blocking something.

I think what the OP means with "freezing" is that the program becomes not responsive, not that the torrent is stalling. More likely to be a file system issue than network problem.

Nevertheless, if the OP means the torrents are stalling and not downloading anything, than see [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923) as already suggested.

---

### Post by Wiedzmin on 2010-03-13
You are right, I did mean that the program became unresponsive. Sorry if I confused anybody with my language. This has not happened with Deluge yet, but how would I find out if it is a file system issue, and what could I do to fix it if it is?

---

### Post by lovinglinux on 2010-03-13
> **Wiedzmin said:**
> You are right, I did mean that the program became unresponsive. Sorry if I confused anybody with my language. This has not happened with Deluge yet, but how would I find out if it is a file system issue, and what could I do to fix it if it is?

I have seen several threads about Transmission having problems with folder permissions. I never heard of BitStormLite, but the latest version BitTornado was released 3 years ago. So it is definitely not a good option.

The best clients for Linux, IMO, are Deluge and Ktorrent (Gnome and KDE respectively). I have used Deluge for a long time, but I'm using Ktorrent since I switched to KDE and I love it.

Anyway, I guess your problem was just a client bug or incompatibility of some sort. Now that you have Deluge, you don't have to worry about that anymore.

---

### Post by Wiedzmin on 2010-03-13
Interesting. Yes, KTorrent is very good. I used it before when I had KDE, but have been unable to find something compatible for GNOME until now.

---

### Post by chisophugis on 2010-03-14
If you're comfortable with the CLI and a lot of tweaking then [rTorrent (libTorrent rakshasa)]("http://libtorrent.rakshasa.no/") works really well I hear (not to be confused with [libtorrent rasterbar]("http://www.rasterbar.com/products/libtorrent/") which is actually the library that Deluge uses)

---

