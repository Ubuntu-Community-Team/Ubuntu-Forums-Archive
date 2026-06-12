---
title: "How To Do Batch Video Watermarking?"
date: 2008-09-02
forum: Multimedia Software
---

### Post by camerong on 2008-09-02
i have about 500 videos i need to batch watermark. They are avi and mpeg. I cannot do this by hand. Please help me. What software/scripting language can do this?

I just need to put text or a logo on them, before I can release them to the public.

thanks

---

### Post by camerong on 2008-09-03
bump

anyone, please?

---

### Post by FakeOutdoorsman on 2008-09-03
First check out [FFmpeg Video Hook documentation]("http://ffmpeg.mplayerhq.hu/hooks.html#SEC7").  Once you get a working ffmpeg command, you can turn it into a batch command:
```
find ~/path/ -iname "*avi" -exec ffmpeg -i {} -vhook '/path/watermark.so -f /path/wm.png' -acodec copy -vcodec copy ~/newpath/{}.avi \;
```
My example above is untested since I don't have vhook enabled in my version of ffmpeg.  You may need to use ffmpeg from a third-party repository such as Medibuntu since Ubuntu's ffmpeg does not support restricted formats.  MEncoder should also be able to do this, but I'm not familiar with it.

---

### Post by camerong on 2008-09-04
thanks a lot.

1 q: what's a .so file?

---

### Post by FakeOutdoorsman on 2008-09-04
I noticed I gave you a link to the wrong documentation in my post above, but I just fixed it.  The watermark.so file is a module that does the watermarking.  I'm not sure where watermark.so is located since I disabled it in my version, but you can find it with:
```
locate watermark.so
```
If your search database is too old then update it (this may take several minutes) and run the search again:
```
sudo updatedb
```

---

