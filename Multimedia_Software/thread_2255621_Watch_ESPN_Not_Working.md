---
title: "Watch ESPN Not Working"
date: 2014-12-06
forum: Multimedia Software
---

### Post by shelbytheguy on 2014-12-06
I'm trying to watch College GameDay on Watch ESPN.

I'm using the latest stock Ubuntu Desktop version, and I have tried using latest stocks versions of Chrome and Firefox. Netflix and YouTube work normally in both. I have cleared all browsing history/cookies/cache/etc. I am able to watch the stream using my Windows 8 laptop running Internet Explorer (though Chrome doesn't work there either) using the username and password for my provider (confirmed the correct details too).

Once I get into the Watch ESPN pop-up window, the play buttons don't do anything once clicked. However, if I go to [http://espn.go.com/college-football/](http://espn.go.com/college-football/) and click the play button there, the Watch ESPN pop-up windows comes up and automatically tries loading the stream.

In Chrome: I get prompted for my provider details. I enter them and get directed back to the stream where it continues to try loading endlessly.
In Firefox: I get prompted for my provider details, except I receive the N9000 error code.

Any thoughts? I searched endlessly for others with this problem, but none of the solutions I found fixed this.

---

### Post by SeijiSensei on 2014-12-06
I had a problem launching WatchESPN the other night in Firefox. For me the solution was to turn off all pop-up blocking.  I also use AdBlock Plus and Ghostery and turned them both off as well.  

I called the number for ESPN to ask about the N9000 error.  The "support" person I spoke with was useless, and never asked about pop-up blocking.

---

### Post by shelbytheguy on 2014-12-06
> **SeijiSensei said:**
> I had a problem launching WatchESPN the other night in Firefox. For me the solution was to turn off all pop-up blocking.  I also use AdBlock Plus and Ghostery and turned them both off as well.  

I called the number for ESPN to ask about the N9000 error.  The "support" person I spoke with was useless, and never asked about pop-up blocking.
Yeah, that was my first guess, which is why I went to stock on everything. There are no pop-up blockers installed, and I set Chrome to allow all.

---

### Post by jeremy-lane on 2014-12-24
Well, I don't have an answer, but I wanted to say that this, too, is happening to me. I was able to watch ESPN3, etc., while on 14.04, but after doing a clean install of 14.10, it no longer works. Similar issues have occurred with NBC Sports Live Extra, which also used to work fine on 14.04. I'm sure it's related to Flash somehow, and authentication, but have yet to figure it out.

I've had problems like this in the past, but switching browsers usually worked, or it would just work eventually, after various updates. I can only hope the same happens here. Frustrating.

---

### Post by jeremy-lane on 2014-12-26
Well, I found a solution that worked for me. Adobe requires the Hardware Abstraction Layer (HAL) be installed in order to play protected content, but 14.10 doesn't use it anymore. (14.04 doesn't either, but I must have installed it without remembering at some point, or as part of something else.) Anyway, to install it, I used the directions here: [http://linuxg.net/how-to-enable-the-playback-of-flash-content-protected-by-drm-on-ubuntu-14-04-ubuntu-13-10-and-derivative-systems/](http://linuxg.net/how-to-enable-the-playback-of-flash-content-protected-by-drm-on-ubuntu-14-04-ubuntu-13-10-and-derivative-systems/).

Here's the important stuff:
> $ sudo add-apt-repository ppa:mjblenner/ppa-hal
$ sudo apt-get update
$ sudo apt-get install hal

Hope that helps you, too.

---

### Post by JohnCUbu on 2015-02-07
> **jeremy-lane said:**
> Well, I found a solution that worked for me. Adobe requires the Hardware Abstraction Layer (HAL) be installed in order to play protected content, but 14.10 doesn't use it anymore. (14.04 doesn't either, but I must have installed it without remembering at some point, or as part of something else.) Anyway, to install it, I used the directions here: [http://linuxg.net/how-to-enable-the-playback-of-flash-content-protected-by-drm-on-ubuntu-14-04-ubuntu-13-10-and-derivative-systems/](http://linuxg.net/how-to-enable-the-playback-of-flash-content-protected-by-drm-on-ubuntu-14-04-ubuntu-13-10-and-derivative-systems/).

Here's the important stuff:


Hope that helps you, too.

I know this thread is a little old, but thank you! This worked.

---

### Post by sviginak on 2015-02-23
For NBC Sports Live Extra this worked for me today

$ sudo add-apt-repository ppa:mjblenner/ppa-hal
$ sudo apt-get update
$ sudo apt-get install hal

More info: [https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal](https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal)

---

### Post by MikeMecanic on 2015-02-24
February 2015
The link below works fine on **Ubuntu 14.04.2 LTS** while using the latest version of Goolgle and/or Opera.  ** Also, Ghostery, Disconnect and Ad block are On**.
[B]Opera:[COLOR=#000000][FONT=Arial]27.0.1689.76 / [/FONT][/COLOR]Ubuntu 14.04.2 LTS (x86_64; Unity
Chrome:[COLOR=#303942][FONT=Ubuntu]Version 40.0.2214.115 (64-bit)[/FONT][/COLOR]
[/B]

> **shelbytheguy said:**
> I'm trying to watch College GameDay on Watch ESPN.

I'm using the latest stock Ubuntu Desktop version, and I have tried using latest stocks versions of Chrome and Firefox. Netflix and YouTube work normally in both. I have cleared all browsing history/cookies/cache/etc. I am able to watch the stream using my Windows 8 laptop running Internet Explorer (though Chrome doesn't work there either) using the username and password for my provider (confirmed the correct details too).

Once I get into the Watch ESPN pop-up window, the play buttons don't do anything once clicked. However, if I go to [http://espn.go.com/college-football/](http://espn.go.com/college-football/) and click the play button there, the Watch ESPN pop-up windows comes up and automatically tries loading the stream.

In Chrome: I get prompted for my provider details. I enter them and get directed back to the stream where it continues to try loading endlessly.
In Firefox: I get prompted for my provider details, except I receive the N9000 error code.

Any thoughts? I searched endlessly for others with this problem, but none of the solutions I found fixed this.

---

### Post by cg4288 on 2015-03-04
It is March and I am having this problem.  Just put Xubuntu 14.04.2 on my laptop, using the latest version of Chrome, cleared my cookies, turned off adblock and pop-up blocker, installed hal, closed all my stuff and cleared it again, and watch ESPN isn't working.  I can login with my ISP on the watch ESPN site, but when I click on a link there, the link doesn't load.  The link only works, like someone else said, if I go through the college basketball page - but the video will not load.  Tried it on Firefox, the only thing that changes is that a DRM error box pops up.  I tried some other DRM protected video streams (my ISP lets you watch TBS live) and that didn't work either.

So, I don't know what I'm doing wrong or if there is any other solution for this.

---

