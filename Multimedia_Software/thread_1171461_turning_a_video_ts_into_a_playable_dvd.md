---
title: "turning a video_ts into a playable dvd"
date: 2009-05-27
forum: Multimedia Software
---

### Post by curiousnoob on 2009-05-27
I have a file that contains VIDEO_TS folder which in turn contains .bup .ifo and .vob files.  
I know how to burn an .iso file to a DVD and even how to convert .avi and .mpg files into an .iso but how do I make this into something a DVD player will play?

---

### Post by curiousnoob on 2009-05-27
bump?

---

### Post by mikezila on 2009-05-27
This one's easy, you just burn it as a data DVD.

Make an empty audio_ts folder, and put that on the DVD alongside the video_ts folder.  The _ts stands for "tile set".  The audio_ts folder has to be there (sometimes it doesn't, on newer players, but just to be safe) even if it's empty.  It's usually only used on dedicated music DVDs, of which very few are still made.

Just throw it on the root of a standard data DVD with a blank audio_ts folder and burn it.

---

### Post by mikezila on 2009-05-27
Just to make clear, you put the folder, not its contents.  The root should look like
```

video_ts
 |- bunch of vobs and some other stuff
audio_ts
 |- probably empty

```

---

### Post by curiousnoob on 2009-06-02
> **mikezila said:**
> Just to make clear, you put the folder, not its contents.  The root should look like
```

video_ts
 |- bunch of vobs and some other stuff
audio_ts
 |- probably empty

```

That did it.  Thanks.

---

