---
title: "Gnomad 2 No longer working after upgrade"
date: 2010-05-10
forum: Multimedia Software
---

### Post by Throne777 on 2010-05-10
After upgrading to Lucid Lynx I can't get Gnomad2 to work with my Creative Zen X-Fi. I used to get it to work by running Gnomad2 as a super user, but now the program quits itself when trying to get the songs from the device claiming a segmentation fault.

```

Device 0 (VID=041e and PID=4162) is a Creative ZEN X-Fi.
Queried Creative ZEN X-Fi
Segmentation fault

```

Any ideas?

---

### Post by gurpal2000 on 2010-05-10
> **Throne777 said:**
> After upgrading to Lucid Lynx I can't get Gnomad2 to work with my Creative Zen X-Fi. I used to get it to work by running Gnomad2 as a super user, but now the program quits itself when trying to get the songs from the device claiming a segmentation fault.

```

Device 0 (VID=041e and PID=4162) is a Creative ZEN X-Fi.
Queried Creative ZEN X-Fi
Segmentation fault

```Any ideas?

There's a bug open. Apparently the problem is libmtp8. You have to install the karmic version of it. Search via Google and you'll see bug report.
I've been using Banshee and i find it works well for video+audio, but not sure if ordinary data can be transferred with Banshee like you can in Gnomad2.

---

### Post by Red62 on 2010-07-20
gurpal.. so are you using banshee to transfer mp3 to a zen?  If so is album art transfering ok?

---

### Post by gurpal2000 on 2010-07-20
> **Red62 said:**
> gurpal.. so are you using banshee to transfer mp3 to a zen?  If so is album art transfering ok?

To be honest i can't remember! i ended up using my Nokia N900 with Banshee and that syns album art fine.

---

### Post by senken12 on 2010-10-20
When I try to use Banshee it doesn't recognise my Zen. =/

---

