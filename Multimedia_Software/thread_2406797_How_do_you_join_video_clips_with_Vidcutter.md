---
title: "How do you join video clips with Vidcutter"
date: 2018-11-26
forum: Multimedia Software
---

### Post by jacatone on 2018-11-26
It's easy to figure out how to use the cut feature in Vidcutter but I can't find any instructions for how to join video clips. Anyone know how?

---

### Post by TheFu on 2018-11-26
I've contacted the vidcutter developer previously.  He was very helpful and responsive.

Outside of vidcutter, how to join different videos depends on the v-codec used and the specific settings for those videos.
For any-to-any joins, the only solution is to convert all the clips to an identical audio and video format, then use a merge tool. Using the lowest quality video as the target would be recommended. Scaling up poor quality clips never works out well.

There are multiple optimizations possible, but only with the exact information about each clip known.

For example, I record TV shows, remove commercials and merge the resulting parts back together.  Because the input source is well-known, it is easy to merge the resulting clips together.  I use **mkvmerge**, but that is mainly because retaining multiple SRT and audio tracks with correct alignment is important.  If I only cared about 1 audio track, then almost any joining tool can work.   Vidcutter can certainly make each clip to be exported using an identical.

You are probably aware, there are other GUI video tools which are designed for video production.  openshot and avidemux come to mind.  openshot makes merging clips very easy, but it transcodes everything.

---

### Post by TheFu on 2018-11-26
From [https://forum.videohelp.com/threads/383776-How-can-you-merge-video-files-in-Vidcutter](https://forum.videohelp.com/threads/383776-How-can-you-merge-video-files-in-Vidcutter)

> Since v4.0.0 you can merge/join externally added videos in addition to any clips you have marked to be cut via the main controls. BUT this is restricted to videos being the same format which the app will check and specify why it could not proceed with the join. So if you videos are of the same format, primarily similar codec and most importantly, same frame size, then it will work. Just use the new add button at the bottom of the Clip Index on the right. This can be used without any video preloaded so it serves as a standalone video joiner, but only for direct-stream/copy style joins so as to avoid the need to [B]reencode videos which is outside the app's scope and for that you should really be using a more traditional video editor.
[/B]
Oz is the author of vidcutter.

---

### Post by jacatone on 2018-11-26
Still not seeing how to use this app for joining. Just want to join clips from the same original file. Does Vidcutter do this or not?

---

### Post by logix2 on 2018-11-26
I recommend [OpenShot]("https://www.openshot.org/") for this task. Vidcutter is mostly for cutting... you need to have files using the same audio and video codec to be able to join them using Vidcutter, and then the clips widget seems to have some display issues and doesn't show the added clips, at least that's how it looks on my Ubuntu 18.10 desktop.

---

### Post by jacatone on 2018-11-26
I hate these timeline video programs. They're too complicated to use. Tried "mkvtoolnix? but of coarse there's no instructions on how to use it. That's what I love about linux. After you install it, you spend the rest of your life trying to actually use it.

---

