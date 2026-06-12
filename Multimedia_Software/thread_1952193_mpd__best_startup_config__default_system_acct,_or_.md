---
title: "mpd:  best startup config?  default system acct, or change to my user acct?"
date: 2012-04-03
forum: Multimedia Software
---

### Post by Kurtosis on 2012-04-03
Hello, mpd's default config (via apt-get) is to start on system boot under user mpd, via /etc/init.d/mpd init script (and the scrobbler /etc/init.d/mpdscribble), using conf file /etc/mpd.conf, and music lib /var/lib/mpd/music.

However, I would have thought the best practice would be mpd running under the user account, using ~/.mpdconf and a music lib somewhere under ~.  Is it?

If so, what's the best way to reconfig it?  Remove ~/etc/init.d/mpd, ~/etc/init.d/mpdscribble, and start mpd and scribble in .profile instead?  Or something else?

Thanks!

---

### Post by papibe on 2012-04-03
Hi Kurtosis.

I'm using mpd in an old laptop as a music server. I control it using a Kindle.

I share your assessment on how to configure mpd. Actually for me it is easier to run it as my own user, and have all files on my own directory. That way I don't need to 'sudo' anything to add/delete/modify content.

I think [this]("https://wiki.archlinux.org/index.php/Music_Player_Daemon") Arch wiki is very good as a general guide. Note that they may made reference to different directories (since it's a different distro), but it is very helpful nevertheless.

Tell us if you need more tips with that.
Regards.

---

