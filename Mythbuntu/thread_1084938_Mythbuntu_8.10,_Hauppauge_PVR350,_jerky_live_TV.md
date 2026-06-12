---
title: "Mythbuntu 8.10, Hauppauge PVR350, jerky live TV"
date: 2009-03-02
forum: Mythbuntu
---

### Post by jamoo1980 on 2009-03-02
Hello

I have just installed Mythbuntu 8.10, which I'm using with a Hauppauge PVR350 for capture, and Hercules 3D Prophet (Kyro2 chipset I think) graphics card for VGA playback. The machine itself has a Pentium 4 processor, 2.0GHz (see attached cpuinfo.txt) and 256MB RAM.

Everything is basically working okay; all of the functionality is there. However, when watching live TV, the video playback is very jerky.

I recorded a few minutes of live TV and played the resulting .mpg video back in xine. The playback was (more or less) smooth. So I don't think there is a problem with capture. And my VGA card can certain cope with playing back the recorded video no problem.

Any ideas why live TV should be so jerky?

I have attached my xorg.conf and Xorg.0.log files.

Any help would be appreciated.

Thanks :)
James

---

### Post by scary_jeff on 2009-03-03
Have you tried changing the playback profile in the frontend setup? you could start with the cpu-- one. You could also try changing deinterlacer.

If you watch TV, try pressing J to decrease the playback speed - is the playback still jerky? If not, press U to return to normal speed. Also, if you open the TV guide, is the video in the corner jerky?

---

