---
title: "Transfer to MTP player VERY slow from Rhythmbox"
date: 2010-06-21
forum: Multimedia Software
---

### Post by ePierre on 2010-06-21
Hello all!

I've been using Rhythmbox for a while now on my Ubuntu 10.04, mainly because it's the default application and also because it handled my Android phone properly (I could drag&drop albums without a problem).

But a few days ago, I tried to copy a bunch of albums on my Android phone as I usually do, and the transfer was extremely slow!

I checked the processor use with a top command, and realized that rhytmbox process was taking 90% of my proc time!


If I copy a directory using Nautilus or command line, the job is done very quickly...

Can anybody help me on that issue?

Thanks in advance!

---

### Post by ePierre on 2010-06-21
I installed Banshee and tried the transfer, and it was very quick. This problem only happens in Rhythmbox apparently!

Do you know how I could analyze what causes the soft to use so much CPU?

Thanks...

---

### Post by ePierre on 2010-06-23
Problem solved.

Rhythmbox was probably trying to convert the files I transfered on my player, which would explain the CPU use.

I adapted the .is_audio_player putting these information inside:


```
audio_folders=Music/
folder_depth=8
output_formats=application/ogg,audio/mpeg,audio/x-ms-wma
```

---

