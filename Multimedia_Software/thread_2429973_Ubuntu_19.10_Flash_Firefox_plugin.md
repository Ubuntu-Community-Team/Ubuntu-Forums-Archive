---
title: "Ubuntu 19.10 Flash Firefox plugin"
date: 2019-10-25
forum: Multimedia Software
---

### Post by setonic on 2019-10-25
I run Ubuntu 19.10 on my Dell XPS 7390 with Firefox 70. To play back videos in Forefox it requires me to install Adobe Flash plugin, but it does not ask for Flash plugin on my another laptop MacBook Air 11" with Debian 10.1 (Buster). Why?

Same situation with Tor Browser - on Ubuntu 19.10 asks for Flash pugin on Debian does not.

---

### Post by uRock on 2019-10-25
Debian uses an older ESR version of Firefox. I've never been asked to install flash in Ubuntu's Firefox on 19.10.

---

### Post by setonic on 2019-10-26
I know that Debian has ESR Firefox - it absolutely does not change anything about Flash Plugin. You have not been asked to install flash just because there are not much web-sites which require flash left. So, I know that debian-live-10.0.0-gnome.iso has some video plugin/codec which allows to watch video content on web-sites which require Adobe Flash installed.

---

### Post by Yellow Pasque on 2019-10-26
> I know that Debian has ESR Firefox - it absolutely does not change anything about Flash Plugin.
False. Firefox 69 and later removed the option to always activate the Flash plugin, even on a per-site basis. It will ask you every single time. It's part of the process to deprecate Flash and minimize security risks for those still using it.
[https://bugzilla.mozilla.org/show_bug.cgi?id=1519434](https://bugzilla.mozilla.org/show_bug.cgi?id=1519434)

---

