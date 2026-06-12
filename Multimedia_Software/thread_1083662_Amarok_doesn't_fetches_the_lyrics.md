---
title: "Amarok doesn't fetches the lyrics"
date: 2009-03-01
forum: Multimedia Software
---

### Post by mikesol on 2009-03-01
Hello, 

I'm using amarok 1.4 and when I try to fetch a lyric, amarok prompts this message (if i use the astraweb plugin)

```

The script 'Astraweb' exited with error code: 1

/usr/share/apps/amarok/scripts/lyrics_astraweb/lyrics_astraweb.rb:57:in `fetchLyrics': undefined method `[]' for nil:NilClass (NoMethodError)
	from /usr/share/apps/amarok/scripts/lyrics_astraweb/lyrics_astraweb.rb:56:in `each'
	from /usr/share/apps/amarok/scripts/lyrics_astraweb/lyrics_astraweb.rb:56:in `fetchLyrics'
	from /usr/share/apps/amarok/scripts/lyrics_astraweb/lyrics_astraweb.rb:139
	from /usr/share/apps/amarok/scripts/lyrics_astraweb/lyrics_astraweb.rb:125:in `loop'
	from /usr/share/apps/amarok/scripts/lyrics_astraweb/lyrics_astraweb.rb:125
```

And a similar output if i use the lyrc plugin.

```

The script 'Lyrc' exited with error code: 1

/usr/lib/ruby/1.8/net/http.rb:560:in `initialize': Connection timed out - connect(2) (Errno::ETIMEDOUT)
	from /usr/lib/ruby/1.8/net/http.rb:560:in `open'
	from /usr/lib/ruby/1.8/net/http.rb:560:in `connect'
	from /usr/lib/ruby/1.8/timeout.rb:53:in `timeout'
	from /usr/lib/ruby/1.8/timeout.rb:93:in `timeout'
	from /usr/lib/ruby/1.8/net/http.rb:560:in `connect'
	from /usr/lib/ruby/1.8/net/http.rb:553:in `do_start'
	from /usr/lib/ruby/1.8/net/http.rb:542:in `start'
	from /usr/lib/ruby/1.8/net/http.rb:1035:in `request'
	from /usr/lib/ruby/1.8/net/http.rb:772:in `get'
	from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb:127:in `fetchLyrics'
	from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb:193
	from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb:179:in `loop'
	from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb:179


```

Now i'm using the googlyrics2 and it shows the lyric perfect but takes a long time to display it.

What its happening? 

Thanks in advance.

---

### Post by chudder on 2009-08-28
I'm not sure, I'm sort of having the same problem, I have Amarok 2.  It looks nice but it's buggy.  I have high hopes for 2.1, etc. 

Some of my songs, it fetches the lyrics and they are there but then they disappear.  It gives an error and show other songs' lyrics I can select but none of them are what I want.  Mind you this only happens with certain songs.  

Any help on both of our issues would be great!

Thanks

---

### Post by Lampi on 2009-10-03
Sorry to disappoint you there chudder, this freakin' bug is still in 2.1 if you should use ultimate_lyrics.

Mostly it helps to start the song all over again and again

---

### Post by jaycee23 on 2009-10-03
I've recently upgraded to Amarok 2.2 AKA Amarok Nightly - solved both the lyrics and album cover issues. :P

---

### Post by jaycee23 on 2009-10-03
Sorry this is the howto for Amarok 2.2

Thanks to stir-crazy's post which I've c&p'ed. Remember it may be unstable - but I've had no problems at all!

To easily install Amarok 2.2 (unstable), follow the directions [_[COLOR=Blue]HERE[/COLOR]_]("https://launchpad.net/%7Ekubuntu-ppa/+archive/beta")  I'm doing this now myself, hopefully will have covers again in a few minutes.

:biggrin:

---

### Post by Lampi on 2009-10-03
you made me thinking, since I did change to the ppa version as well some while ago and:
```
:~$ apt-cache policy amarok
amarok:
  installed: 2:2.1mysql5.1.30-0ubuntu2~jaunty2
  candidate: 2:2.1mysql5.1.30-0ubuntu2~jaunty2
  Versions:
 *** 2:2.1mysql5.1.30-0ubuntu2~jaunty2 0
        100 /var/lib/dpkg/status
     2:2.0.2mysql5.1.30-0ubuntu3 0
```
looks like I used 2.2 already without knowing about it - no cover art problems so far, but the lyrics still disappear from time to time. Guess I should change to another lyrics script ... what are you guys using besides ultimate-lyrics?

---

### Post by ov1d1u on 2009-12-26
Sor for this off-topic message but have anyone a copy of GoogLyrics2 beta? It seems that the official download link from kde-loog.org is dead. Thanks :popcorn:

---

