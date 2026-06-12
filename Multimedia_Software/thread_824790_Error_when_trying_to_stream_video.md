---
title: "Error when trying to stream video"
date: 2008-06-10
forum: Multimedia Software
---

### Post by hakins90 on 2008-06-10
I am trying to watch the apple 2008 keynote. Link here - [http://www.apple.com/quicktime/qtv/wwdc08/](http://www.apple.com/quicktime/qtv/wwdc08/)
or here - [http://events.apple.com.edgesuite.net/0806wdt546x/event/index.html](http://events.apple.com.edgesuite.net/0806wdt546x/event/index.html)

When i click the link to watch the video, i get an error in totem movie player saying i need a "text/html decoder plugin". After extensive searching i can't find the answer to my problem. 

I downloaded and installed the ubuntu-restricted-extras but it didn't help my situation.

Can anyone help?

Thanks

harry

---

### Post by tooferson5 on 2008-06-11
same problem - same video

---

### Post by Rhubarb on 2008-06-11
Got it to work!

Ok, here's what I did:
I looked at the source of apple's website to find the URL of the stream.

So here's how I got it to play:
Install VLC:
```
sudo aptitude install vlc
```
Open up VLC
File --> Open Network Stream
Click on the radio button "HTTP/HTTPS/FTP/MMS"
Paste this URL in there:  [http://stream.qtv.apple.com/events/jun/0806wdt546x/m_080690210abcn_1200_ref.mov](http://stream.qtv.apple.com/events/jun/0806wdt546x/m_080690210abcn_1200_ref.mov)
Press ok, sit back, and watch the turtle neck guy talk about lots of boring stuff (imho)

---

### Post by tooferson5 on 2008-06-12
that worked.  thanks alot!

---

