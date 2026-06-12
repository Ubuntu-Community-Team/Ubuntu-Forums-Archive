---
title: "VLC jitters when playing DVDs or Mpegs"
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by sirana on 2007-12-31
I recently upgraded from feisty to gutsy and now the video in VLC player jitters very heavily(unwatchable) when playing DVDs and when playing some types of MPEGS.  The audio seems ok.

I have libdvdcss2, libdvdnav4 and libdvdread3 installed. VLC version is 0.8.6c.

Also playing DVDs in Totem is not possible. it says that I don't have the appropriate plugins installed.

Sorry if this is a newbie question, but I didn't find anything in the forums or elsewhere.
Thanks in advance.

---

### Post by markharding557 on 2007-12-31
one possible cause of unstable playback is not having dma enabled'check this by opening a terminal and type
> sudo hdparm -i /dev/yourdrive
you will see a readout look on the dma line you should see an atarisk against one of the udma eg udma2

---

### Post by sirana on 2008-01-01
it doesn't seem to be dma issues, since it happens with mpeg files as well.
and there is an asterisk before udma2

---

### Post by sirana on 2008-01-04
ok. kinda solved it. 
after a reinstall of ubuntu (yeah, kinda drastic I know) I still had the same problem. 
then I switched from the restricted video drivers (I have a ATI card) to the unrestricted and now it works. dvd playback, mpeg, wmv everything. and when I play video with totem the video isn't green anymore (I didn't post that problem, because I didn't think it was connected)
So, the restricted driver is to blame. 
Bad, bad restricted driver. No cookie for you!!

---

