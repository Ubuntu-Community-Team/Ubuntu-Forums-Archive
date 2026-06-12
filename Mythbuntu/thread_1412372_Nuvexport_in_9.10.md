---
title: "Nuvexport in 9.10"
date: 2010-02-21
forum: Mythbuntu
---

### Post by hylsan on 2010-02-21
Since I started using karmic I cant use nuvexport.
Have always used "nuvexport --transcode" and it have always worked.

Now I get this when running in debug-mode:
```

tomas@MythCube:~/Skrivbord$ /usr/bin/nice -n19 transcode -V --print_status 16 --import_asr 2 --export_asr 2 --export_fps 25.000,3 -Z 512x384 -k -i /tmp/fifodir_4150/vidout -p /tmp/fifodir_4150/audout -H 0 -x raw -g 720x576 -f 25.000,3 -n 0x1 -e 48000,16,2 -j 8,10,8,10 -J smartyuv  -y xvid,null  -N 0x55 -b 128,0,2,0 -R 1,/tmp/xvid.4150.log -w 768  -o /dev/null 2>&1
[transcode] critical: bad argument for -V/--video_format, should be one of: yuv420p (default), yuv422p, rgb24
tomas@MythCube:~/Skrivbord$ 

```

How do I change this???

note: Im quite new to linux.

MY hdd starts to fill up so all ideas are appreciated.

/Hylsan

---

### Post by russell5 on 2010-02-21
i had this problem. i believe if you remove -printstatus 16 fomr the command it works.

---

### Post by hylsan on 2010-02-22
yeah, but how do I do it when typing "nuvexport --transcode"?
Cant really remove something I dont write, and I dont feel like running in debug-mode all the time...

/Hylsan

---

