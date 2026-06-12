---
title: "A way to force Adobe Flash video to maintain aspect ratio when maximized?"
date: 2012-04-24
forum: Multimedia Software
---

### Post by Curious00 on 2012-04-24
Is there a workaround to force Adobe Flash applets running within a browser like Chromium to maintain their proper widescreen aspect ratio when they're maximized onto a squareish screen? The video display performance is much better when they're displayed in full screen mode, than when I try to enlarge the browser window to an appropriate scale.

Or even better yet, is there an application which will scrape URIs and let me play streaming flash video independently of the web browser, itself?

---

### Post by gordintoronto on 2012-04-24
I use "Magic Actions for YouTube" with Chrome, and I'm very happy with the results -- on Youtube.

When I play videos from Vimeo in full-screen mode, the aspect ratio is preserved by putting black bars at top and bottom or left and right.

There are also add-ons which let you download a video, then play it offline with your choice of program.

---

### Post by Curious00 on 2012-04-24
Yes, I do have a Chromium extension which allows me to download videos. Youtube is fairly reliable when it comes to aspect ratio, unlike the various streaming news services I watch over the web. That's where I really have concerns. Thanks for your kind words.

---

### Post by Curious00 on 2012-06-20
I've recently learned how to use mplayer and rtmpdump to stream the url of the station I wanted to watch (NHK TV from Japan).

```
rtmpdump -r rtmp://yoururl | mplayer -cache 128 -
```

(The NHK TV url is rtmp://ca-1.net.fivecool.org/nhkw/gwm)

Similarly, you can watch CNTV from China like this:

```
mplayer mms://a529.l7906022528.c79060.g.lm.akamaistream.net/D/529/79060/v0001/reflector:22528 -cache 4096
```

---

### Post by gordintoronto on 2012-06-20
The Chinese link spent several minutes getting the buffer up to 20%, then gave an error message.

For live Chinese TV, Sopcast works very well. It's peer to peer. ppa:ferramroberto/sopcast

---

### Post by Curious00 on 2012-06-20
I've found the the download speed of data from CNTV to be quite slow... you'll notice that the url which I gave you has a 4 megabyte buffer. You could try making that smaller (Instead of 4096, write in "512" for example). I find that a larger buffer helps the feed not skip as much.

---

