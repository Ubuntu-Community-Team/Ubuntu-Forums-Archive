---
title: "flash dialog freeze"
date: 2013-01-04
forum: Multimedia Software
---

### Post by caersith on 2013-01-04
Hi guys, I'm new here.

I'm having trouble with flash on firefox lately. When I watch live streaming on [[COLOR="Blue"]_niconicolive_[/COLOR]]("http://live.nicovideo.jp/") (it's a live streaming site), a dialog would appear asking permisssion for local storage. This is normal and I don't mind giving permission. The problem is the dialog kinda freeze, so I couldn't click it and couldn't close it. It just stay there, while the video is playing. Which is really really annoying.

Anyone experience something like this on other live streaming sites? What I meant by live is not video streaming, because I could still play video streaming sites like you tube and niconicovideo. Anyway If I remember correctly it used to work just fine, maybe it started to break after I updated my Ubuntu 12.04. So I just wonder whether this is a known bug or not? I'm on Ubuntu 12.04 as a guest in virtual box.

I found a fix from this site [[COLOR="Blue"]_http://devslog.com/article/20121025120056.html_[/COLOR]]("http://devslog.com/article/20121025120056.html")

Here's the fix:
$ cd ~/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#live.nicovideo.jp
$ python s2x.py -x setting.sol # convert .sol to .xml
$ nano setting.xml # change klimit to -2.0
$ python s2x.py -s setting.xml # convert it back to .sol

[_[COLOR="Blue"]s2x.py[/COLOR]_]("http://osflash.org/s2x")

I tried the fix and it works, but I'd rather have this issue resolves as a bug if it is indeed a bug from your end.

Thanks.

---

