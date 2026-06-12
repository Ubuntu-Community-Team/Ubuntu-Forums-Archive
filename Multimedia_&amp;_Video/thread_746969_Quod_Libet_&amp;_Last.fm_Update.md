---
title: "Quod Libet &amp; Last.fm Update"
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by Ashly on 2008-04-06
Hi all.

I've been using Quod Libet 1.0, and just recently I installed a random update via the Update Notifier, and it mucked things up. Quod Libet lost the ability to play anything, and flicked through about five hundred songs before I could stop it.

I restarted my session and things were fine, except ever since Last.fm hasn't been updating. It's been a few days now, and I'm wondering if this is related at all. The plugin doesn't output any errors, and it's configured properly.

I guess my question is: Does anyone else have the same problem, or have any possible solutions?

---

### Post by hugmenot on 2008-04-06
When you start it in a terminal you will see some output about songs being submitted, or not. You could try that.

---

### Post by Ashly on 2008-04-08
I tried this after you suggested it, but again, absolutely no output.

I also tried apt-get removing quodlibet-plugins and installing the plugin provided on the QL site, but it does the same thing.

My Last.FM page tells me unhelpfully that some tracks triggered spam protection, but I've no idea if that was Quod Libet or not. It's a disaster.

I'm using Exaile as an alternative, but the album view really isn't as mature as Quod Libet. On the plus side, I've been able to report some bugs for it, so maybe something came out of this after all.

---

### Post by hugmenot on 2008-04-09
Check your plugin settings. The plugin you want is called QLScrobbler. Set your username there, again, and see whether it's enabled and all that jazz.
I've been using QLScrobbler over the last two years continuously. It works.

---

