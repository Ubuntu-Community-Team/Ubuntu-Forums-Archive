---
title: "Xine can't play swedish subtitles"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by ikkA on 2007-07-27
Hi dear Ubuntu users. :)
This is what I get when I try to play subtitles who contains "ÅÄÖ" 
[http://pici.se/pictures/YPEhTDgVa.png](http://pici.se/pictures/YPEhTDgVa.png)
I never got a good answer on the swedish forum, but there must be a setting to change or something?
I can play it in VLC, but HD movies don't stream so well in VLC for me.

Have a great day! :)

---

### Post by madmetal on 2007-07-28
> **ikkA said:**
> Hi dear Ubuntu users. :)
This is what I get when I try to play subtitles who contains "ÅÄÖ" 
[http://pici.se/pictures/YPEhTDgVa.png](http://pici.se/pictures/YPEhTDgVa.png)
I never got a good answer on the swedish forum, but there must be a setting to change or something?
I can play it in VLC, but HD movies don't stream so well in VLC for me.

Have a great day! :)

maybe its encoding problem?
since you dont get a reply from swedish forum try also the ubuntu-se mail list
[email]ubuntu-se@lists.ubuntu.com[/email]
;)

---

### Post by Matakoo on 2007-07-28
> **ikkA said:**
> Hi dear Ubuntu users. :)
This is what I get when I try to play subtitles who contains "ÅÄÖ" 
[http://pici.se/pictures/YPEhTDgVa.png](http://pici.se/pictures/YPEhTDgVa.png)
I never got a good answer on the swedish forum, but there must be a setting to change or something?
I can play it in VLC, but HD movies don't stream so well in VLC for me.

Have a great day! :)

Well, I don't have an answer I'm afraid. All I know is that Swedish subtitles work perfectly for me, and I haven't even bothered to change any settings within xine.

One suggestion: move everything from $HOME/.xine to somewhere else and try again. The files in there should, IIRC, be re-created automatically if missing (and if not, just move them back again). There might be a setting you've changed that has caused this behavior.

I've only tried with regular DVD discs, and it works there. I have no experience with HD-def I'm afraid, but try a regular DVD at first and see if the problem persists. AFAIK, you can't play HD-DVD or Blueray discs using Linux so I assume you mean subtitles in .srt or a similar format? If so, are you sure the subtitle files are correct?

---

### Post by Gremlinzzz on 2007-07-28
You can try smplayer plays all my DVD movies
[http://smplayer.sourceforge.net/linux/screenshots_en.php](http://smplayer.sourceforge.net/linux/screenshots_en.php)
heres the deb package. i installed smplayer package (Qt3; without KDE support)
[http://wesley.debianbox.be/packages/](http://wesley.debianbox.be/packages/)
:guitar:

---

