---
title: "I get Operating System not supported when I try to watch an episode of Vampire"
date: 2010-05-16
forum: Multimedia Software
---

### Post by gnik1 on 2010-05-16
Has anyone figured out a way around the error at this page when viewing it through firefox on an Ubuntu system?

[http://www.cwtv.com/cw-video/the-vampire-diaries](http://www.cwtv.com/cw-video/the-vampire-diaries)

I have recently enabled 64bit flash. My clicks work on Youtube videos and everything else I've tried.

Until I tried to catch an episode of one of my favorite tv shows.
I am guessing I won't be able to watch Lost either.

Anyone have any luck?

EDIT: Lost played in my browser at abc.com
It's very choppy if I go full screen though.

---

### Post by Sub101 on 2010-05-16
Im outside of the USA so unable to check however in the UK most (all that im aware of) TV channels online services work on Linux.

---

### Post by gnik1 on 2010-05-16
The applet area says it will only play on Windows and Mac OSX.

Why would the O.S. matter for something I am trying to play in my browser? 
Doesn't that seem odd?

---

### Post by lovinglinux on 2010-05-16
> **gnik1 said:**
> The applet area says it will only play on Windows and Mac OSX.

Why would the O.S. matter for something I am trying to play in my browser? 
Doesn't that seem odd?

There are several different ways of streaming videos, most of them use plugins and authentication methods that might not work on Linux, specially the DRM protected ones. The browser itself is not responsible for playing the content, unless you are viewing [HTML5 video](http://en.wikipedia.org/wiki/HTML5_video).

Could you post a screenshot of the error message? I'm outside US, so I can't test it.

It could be Silverlight based, so you would need [Moonlight](http://www.go-mono.org/moonlight/prerelease.aspx) plugin (creepy coincidence).

Also check the [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683") for other plugins and codecs.

---

### Post by gnik1 on 2010-05-16
I'm trying. I'll keep at it. I have been able to find a way for everything except for making flash.

here is a screenie of the error:

[IMG]http://foo.gearsector.com/foo/images/error.png[/IMG]

---

### Post by dtfinch on 2010-05-16
If I try User Agent Switcher to fool it into thinking on Windows, it tells me I need to download and install their proprietary "Move Media Player".

---

### Post by lovinglinux on 2010-05-16
[Here](http://www.cwtv.com/thecw/feedback-help) there is info about the player, which is a custom player for Windows and Mac. 

You could try to install a Windows Firefox version using Wine and then install the plugin.

---

### Post by gnik1 on 2010-05-16
Thanks for the heads up. I will look into it and see how far I can get.

EDIT:
It seems to have worked. After installing firefox in wine. Then their plugin. Then flash. It is working. I don't get any controls like the slider and pop out to full screen. But I can watch the movie.

Thanks for the help!

[IMG]http://foo.gearsector.com/foo/images/dlpic.png[/IMG]


[IMG]http://foo.gearsector.com/foo/images/Screenshot.png[/IMG]

---

