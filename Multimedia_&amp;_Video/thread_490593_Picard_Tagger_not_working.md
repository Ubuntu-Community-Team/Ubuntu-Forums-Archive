---
title: "Picard Tagger not working"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by Washington Irving on 2007-07-02
Picard won't display mp3 files when they are dragged onto the "New Files (drag files to tag here)" and so I can't tag them. It did display some flac files though. I had it working on Dapper. Anyone know why this is?

---

### Post by Washington Irving on 2007-07-02
Ah, after a little more searching on the net I found [this thread]("http://forums.musicbrainz.org/viewtopic.php?id=489"). i just needed a library installed. It seems I posted too soon. Oh well, at least if anyone else has the same problem the solution is here.

---

### Post by simormate on 2007-07-18
I write it here so no more search is needed:
install the libtunepimp5-mp3 package from the repos.
Mate

---

### Post by grimdestripador on 2007-07-20
I did a google search for "mp3 picard feisty" and was having this exact problem. 
Seriously, those maintainers should realise that a MP3 tagger probally needs MP3 support to get those ID3v2.4 tags written.... Which is the purpose of the program...

Thanks for mentioning that I need libtunepimp5-mp3

---

### Post by midorigin on 2007-07-20
That's sure odd. Thanks for the tip.

---

### Post by gkiller on 2007-07-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/picard/+bug/128600](https://bugs.launchpad.net/ubuntu/+source/picard/+bug/128600) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I ran into the same problem. Thanks for the solution. I opened a bug report about this because not having mp3 support by default is totally contrary to the Ubuntu "just works" philosophy.

---

### Post by theak on 2007-07-28
I've tried this, and also uninstalled and reinstalled Picard and both the libraries, but still Picard will not tag my mp3s. Any suggestions of other taggers to use?

---

