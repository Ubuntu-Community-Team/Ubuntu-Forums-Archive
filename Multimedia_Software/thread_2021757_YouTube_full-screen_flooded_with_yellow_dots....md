---
title: "YouTube full-screen flooded with yellow dots..."
date: 2012-07-09
forum: Multimedia Software
---

### Post by theirishfrog.sh on 2012-07-09
I'm currently running Ubuntu 11.04 on a Gateway M-6827. Recently, every time I attempt to full-screen a video on YouTube, the screen becomes littered with flashing yellow dots. Any ideas? :(

[IMG]http://saiyanpride.tk/Screenshot at 2012-07-09 19:51:38.png[/IMG]

---

### Post by PaulWilks on 2012-07-13
I have the very same issue... any solutions yet?

---

### Post by vasa1 on 2012-07-13
Neither poster mentioned the browser but ...
here's some more:
[http://productforums.google.com/forum/#!category-topic/chrome/linux/t4bXCYAJxW8](http://productforums.google.com/forum/#!category-topic/chrome/linux/t4bXCYAJxW8)

---

### Post by theirishfrog.sh on 2012-07-14
> **vasa1 said:**
> Neither poster mentioned the browser but ...
here's some more:
[http://productforums.google.com/forum/#!category-topic/chrome/linux/t4bXCYAJxW8](http://productforums.google.com/forum/#!category-topic/chrome/linux/t4bXCYAJxW8)

Google Chrome - Version 20.0.1132.47

Also, I checked out the link you posted, but no luck thus far... Still can't figure out what could be causing this. :confused:

---

### Post by vasa1 on 2012-07-14
> **theirishfrog.sh said:**
> Google Chrome - Version 20.0.1132.47

Also, I checked out the link you posted, but no luck thus far... Still can't figure out what could be causing this. :confused:
Yes, it can be quite frustrating. What makes matters worse is that there are still relatively few users reporting this particular problem and even they are giving minimal details. That makes it difficult to find some common factor that *could possibly* be the source of the problem.

---

### Post by balg on 2012-07-17
Hello!

I have the same problem.
- Ubuntu 12.04
- Chrome Version 20.0.1132.57

---

### Post by skeetwood-mac on 2012-07-19
I am also having this problem. I'm running Ubuntu 12.04 with the latest version of Chrome. I do not have this problem in Firefox, but I prefer to use Chrome.

---

### Post by ToasterThief on 2012-08-03
Exactly same problem here. Changing between Flash-plugin versions sometimes solves for a while.

---

### Post by Yudley on 2012-11-09
Same problem here for many weeks. Updates don't fix it.

I can't find two flash versions in my "**about: plugins**" of Chromium. I have a flash plugin and a VLC plugin (with flv support) though. I tried disabling one of each at a time but the dots remain. If I disable both, Chromium gives error on flash media playback saying I need to install Adobe flash or something. But Adobe flash is already installed on my machine (Firefox uses it I guess).

I have Ubuntu 12.04 and Chromium.

---

### Post by Yudley on 2012-12-01
Hey guys i seem to have SOLVED this problem

I noticed if I watch the same video in "incognito" mode it doesn't have the dots ... so I figured it has something to do with my youtube account login or the youtube cookies:

- i signed out of my youtube account ... dot/grains were still there
- i removed the cookies associated with youtube.com, restarted the browser, logged in to my youtube account and now the dots are gone

hope it helps

(i didn't remove/disable any flash plugins, my about:plugins page only showed one flash plugin and one VLC plugin ... I'm using chromium)

---

### Post by theirishfrog.sh on 2013-01-14
> **Yudley said:**
> Hey guys i seem to have SOLVED this problem

I noticed if I watch the same video in "incognito" mode it doesn't have the dots ... so I figured it has something to do with my youtube account login or the youtube cookies:

- i signed out of my youtube account ... dot/grains were still there
- i removed the cookies associated with youtube.com, restarted the browser, logged in to my youtube account and now the dots are gone

hope it helps

(i didn't remove/disable any flash plugins, my about:plugins page only showed one flash plugin and one VLC plugin ... I'm using chromium)
Sorry, Yudley... But it's just not working for me. I have the issue across distros (Ubuntu & Mint) and video platforms (Flash & HTML5). It does however work in Firefox, which leads me to believe it is specifically related to Chrome, which is hilarious considering that Google runs both projects.

Any more news on this issue? :-(

---

### Post by driv on 2013-01-14
Hi,

I'm having this problem again, it has appeared after the last reboot. Yesterday some upgrades have been installed. After discovering the problem I've tried rebooting but nothing happened.


I'm using:
Ubuntu 12.04
Chrome: Version 24.0.1312.52

Firefox and chromium are working fine!

---

### Post by IQAndreas on 2013-01-20
Same problem here. 

This problem also occurs with embedded non-flash video in all three formats listed here: [http://www.quirksmode.org/html5/tests/video.html](http://www.quirksmode.org/html5/tests/video.html)

[LIST]
[*]The "noise" does not appear in FireFox.
[*]The "noise" does not appear for those same videos downloaded and opened with the default player (so it's not a codec issue)
[*]The "noise" **DOES** appear in incognito mode.
[/LIST]

Running with the following specs:
[LIST]
[*]Ubuntu 12.10
[*]**Chrome version:** 24.0.1312.52
[*]**Graphics card:** Mobile Intel 965 Express Chipset Family
[/LIST]

This problem appeared for me once before, several months back, and a few weeks later disappeared just as mysteriously as it came.

---

### Post by driv on 2013-01-22
Hi,

I've been able to remove the dots! :)

Just followed the instructions in this post: [http://techlogon.com/2011/08/11/shockwave-flash-crashes-in-google-chrome/](http://techlogon.com/2011/08/11/shockwave-flash-crashes-in-google-chrome/)

Hope it helps!

---

### Post by vasa1 on 2013-01-24
A possibly relevant bug is being tracked here: [Flickering rectangles like a swarm of bees when watching youtube and vimeo videos]([http://code.google.com/p/chromium/issues/detail?id=164555](http://code.google.com/p/chromium/issues/detail?id=164555)).

---

### Post by antiw on 2013-01-27
Opening Chrome in command with option: --disable-accelerated-compositing solves the problem in my Ubuntu 12.04 box.

In my case, the yellow line noise appeared in both flash and HTML5 video. With above solution, they've all gone.

---

### Post by IQAndreas on 2013-02-03
> **driv said:**
> Just followed the instructions in this post: [http://techlogon.com/2011/08/11/shockwave-flash-crashes-in-google-chrome/](http://techlogon.com/2011/08/11/shockwave-flash-crashes-in-google-chrome/)
That did fix Flash video, but the HTML5-based video was still acting up.

Also, the HTML5 video would all play with "pink dots", but otherwise would look just like the yellow dots on Flash based video.

This leads me to believe that the Flash video and HTML5 video problems are two different but related issues.


And due to no cause of my own, video is playing normally again (it has been for a few days), and was likely fixed in the latest version (now running Chrome version 24.0.1312.57).


> **antiw said:**
> Opening Chrome in command with option: --disable-accelerated-compositing solves the problem in my Ubuntu 12.04 box.
I'll have to try that if the problem appears again.

---

### Post by BenjaminRH on 2013-03-11
Another relevant bug: [https://code.google.com/p/chromium/issues/detail?id=124569](https://code.google.com/p/chromium/issues/detail?id=124569)

---

### Post by nidelius on 2013-04-17
> **BenjaminRH said:**
> Another relevant bug: [https://code.google.com/p/chromium/issues/detail?id=124569](https://code.google.com/p/chromium/issues/detail?id=124569)

So here is what to do: [http://www.opera.com/download/linux/]("http://www.opera.com/download/linux/") :D

---

