---
title: "Terminal command to return what Banshee is playing?"
date: 2009-08-29
forum: Multimedia Software
---

### Post by Murrquan on 2009-08-29
Hey, everyone!

Is there a terminal command that'll output the song currently playing in Banshee? Because I'm using the Logjam blog editor to write LiveJournal posts, and it's got this function where it'll detect what music you're playing. The thing is, it doesn't detect from Banshee. And it'll let you assign a custom command of some kind, but the default is

```
sh -c "mpc | grep -v '^volume: .* repeat: .* random: .*'"
```

And that doesn't seem to work.

Any help?

---

### Post by 0andriy on 2010-10-10
> **Murrquan said:**
> Hey, everyone!

Is there a terminal command that'll output the song currently playing in Banshee? Because I'm using the Logjam blog editor to write LiveJournal posts, and it's got this function where it'll detect what music you're playing. The thing is, it doesn't detect from Banshee. And it'll let you assign a custom command of some kind, but the default is

```
sh -c "mpc | grep -v '^volume: .* repeat: .* random: .*'"
```

And that doesn't seem to work.

Any help?

Please, read here:
[http://community.livejournal.com/logjam_dev/39706.html?thread=118298#t118298](http://community.livejournal.com/logjam_dev/39706.html?thread=118298#t118298)

---

