---
title: "How do I make Firefox run vlc with URL?"
date: 2011-05-29
forum: Multimedia Software
---

### Post by jtgd on 2011-05-29
I have a server that delivers media via HTTP (or FTP). If I click on a link, it downloads to /tmp and then plays in vlc, but what I want is for it to run vlc and give it the URL so that it will play it as a stream.  I am generating the HTML and I'm using thttpd for the server. If I do it manually (Copy Link Location, paste into vlc) it works fine, but I'd like click-and-play. I've Googled for hours and can't even see the topic addressed.  This is possible, right?

(Lucid-64, XFCE, Firefox 4.0b11, thttpd, vlc 1.0.6)

---

### Post by jtgd on 2011-06-09
I did figure out how to make Firefox run vlc with the URL, but it was by defining a protocol so I could say "vlc://..." This will indeed run vlc and hand it the protocol, but vlc doesn't know how to handle a URL like "vlc://...".

Another solution I found was to have my page download a little .XSPF file which had the URL in it. vlc knows how to parse this file and it will play the video.

---

