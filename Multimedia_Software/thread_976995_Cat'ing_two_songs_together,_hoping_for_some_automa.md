---
title: "Cat'ing two songs together, hoping for some automation"
date: 2008-11-09
forum: Multimedia Software
---

### Post by voteforpedro36 on 2008-11-09
Well, I've posted on Arch's forums, as that is what I'm running, but it doesn't really make any difference, and since I'm registered here and I thought maybe someone here could help... Here's the situation:

I have a load of mp3s that are split into 2 parts. I have decided to use cat to put these two files together (unless someone has a better tool), so that they make one mp3. Here's what I mean:

folder called songs -> folder called first -> files such as ```

0263_Pantera - Walk.mp3
0267_Ozzy Osbourne - Sabbath Bloody Sabbath.mp3

```

folder called songs -> folder called second -> files such as ```

0264_Pantera - Walk - -Requested by Jared - MSG- Pantera Yeah-.mp3
0268_Ozzy Osbourne - Sabbath Bloody Sabbath - -Requested by Flipzeroccs9 - MSG- OZZY ROCKS--.mp3

```

folder called songs -> folder called merged -> no files yet, this is where the final copies would go

I need cat these files together (obviosuly "Walk" with the other "Walk", but I thought I'd let you see the file names). This isn't too hard, I run ```
cat "first/0263_Pantera - Walk.mp3" "second/0264_Pantera - Walk - -Requested by Jared - MSG- Pantera Yeah-.mp3" > "merged/Pantera - Walk.mp3"
```
and it's fine. But seeing as how I have ~200 songs, this is going to be a pain. I hate to ask, as I already have at one forum, but I'm no scripter and I was wondering if anyone could try it?

---

