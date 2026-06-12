---
title: "Dual layer large file troubles"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by solidunit on 2007-05-23
I am starting to download large x264 mkv files off usenet and backing them up to dual layer dvd. The files are usually around 6 to 8 gigs each. I use the Nero 3 linux beta to burn them, no problems there.

The problems lies in reading back the disc. First of all, the disc won't mount automatically. I get an "Invalid mount option" dialog box error message that pops up.

So in order to work around this behavior, I go to the console, modprobe the udf module and then manually mount the disc. Success!

Now I'm able to mount the disc, but the file is unreadable by both mplayer and xine. Mplayer says the the file has no audio or video streams (which is not the case). Attempting to play back the file yields the following kernel messages:

```
[10141.295648] attempt to access beyond end of device
[10141.295656] hdc: rw=0, want=16450672, limit=8388604
[10141.295661] Buffer I/O error on device hdc, logical block 4112667
[10141.295667] attempt to access beyond end of device
[10141.295670] hdc: rw=0, want=16450676, limit=8388604
[10141.295672] Buffer I/O error on device hdc, logical block 4112668
[10141.295678] attempt to access beyond end of device
[10141.295681] hdc: rw=0, want=16450672, limit=8388604
[10141.295684] Buffer I/O error on device hdc, logical block 4112667
[10141.295688] attempt to access beyond end of device
[10141.295691] hdc: rw=0, want=16450676, limit=8388604
[10141.295694] Buffer I/O error on device hdc, logical block 4112668

```

I'm using Ubuntu Feisty x64. Is UDF large file support broken in the kernel? Or is large file support for dual layer discs broken? Or is my PC broken?

---

### Post by kioftes on 2008-01-06
I have the same problem. I burned a large video file (~8gb) on a dual layer dvd with nero linux. Everything was ok, i palyed the video but just in the middle of the movie, it stopped! In the properties tab, its full size has been recognized, but not its duration! it always (whenever i try to burn sth of that size) says 55 and sth minutes, although kaffeine sees th full duration, but can't play it. I searched everywhere on the internet and i din't find any solution for it...a bug in udf?Can ext3 manipulate files larger than 4gigs? i tried to burn it using every different option in nero linux but kept getting the same result. Don't know if i can burn it under windows (i don't have any...hehe!).Distro is Gutsy...Any help???

---

### Post by radu_radu on 2008-01-07
I had the same problem, too.
I burned 58 files of 7.4GB with K3B; the verification at the end proved successful, but I can access only half of those files!
Here's a snippet of my /var/log/messages (it had literally hundreds of lines identical to these two except the time)
```
Jan  7 22:31:33 Xanadu kernel: [15271.958085] attempt to access beyond end of device
Jan  7 22:31:33 Xanadu kernel: [15271.958089] hdc: rw=0, want=12770176, limit=8388604

```

EDIT: I found a solution that works for me - in launchpad, [[COLOR="Blue"]_bug #118310_[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/118310")
To make it short, you might need to run ```
sudo pktsetup -d pktcdvd0
```
Read the launchpad bug for details

---

