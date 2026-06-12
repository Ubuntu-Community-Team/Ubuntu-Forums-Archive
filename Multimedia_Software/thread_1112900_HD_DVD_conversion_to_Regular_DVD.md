---
title: "HD DVD conversion to Regular DVD"
date: 2009-04-01
forum: Multimedia Software
---

### Post by CraigPaleo on 2009-04-01
My sister-in-law bought some HD DVDs mistakenly thinking she could play them in an ordinary DVD player because they have an HD TV.

Is there any way to convert HD DVDs to regular DVDs using something like K9copy or ffmepeg?

---

### Post by 3rdalbum on 2009-04-01
Are you prepared to do some serious work?

If you have an HD-DVD drive in your computer, you can possibly convert those discs. You will need to follow the instructions for HD-DVD playback from [https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

Then once you have the SVN Mplayer and the disc ripped to your hard drive, you can convert the main feature to a different video format by putting it into the "DeVeDe" program available from [www.getdeb.net](www.getdeb.net), and pointing Devede to your local copy of Mplayer.

This is, assuming that Mplayer will play the main feature of your chosen HD-DVD properly without giving special parameters; in the two HD-DVDs I bought, this has not been the case. $25 down the drain because I assumed HD-DVDs would be better supported than Blu-rays on Linux... oh well.

---

### Post by andrew.46 on 2009-04-01
Hi,

[That page]("https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD") does indeed look like hard work :-). The installation of the svn MPlayer is not such a small part of that but there is [a guide on these forums]("http://ubuntuforums.org/showthread.php?t=1024592") that should at least make this part easier.

All the best,

Andrew

---

### Post by CraigPaleo on 2009-04-02
Thanks! You've saved me much time and effort! I don't have an HD DVD drive but was hoping there were a way I could have gotten the data from it with a regular DVD drive. Alas, no software solution could make the HD DVD readable.

I'll have to see about borrowing on Xbox 360

---

### Post by binbash on 2009-04-02
dvd::rip also supports 2 pass x264 (latest one, maynot be in intrepid repos) encoding if you are going to make it mkv ;)

---

