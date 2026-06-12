---
title: "HBO NOW on Ubuntu 14.04"
date: 2015-04-12
forum: Multimedia Software
---

### Post by dancljohnson on 2015-04-12
I've been trying to get HBO NOW to work on my Ubuntu 14.04 machine with no success. Since it is a rather new service, the only forum posts I've been able to find are in reference to HBO GO which it seems like some people were able to get to work with firefox and HAL. I've tried this route, but still get the "HBONOW requires Flash Player version 17 or higher. Download FlashPlayer. -playbackTechError" message. I realize that flash isn't supported on Ubuntu anymore, but I was wondering what the outlook is for a similar workaround.

---

### Post by dino99 on 2015-04-12
this might help  [http://www.webupd8.org/2014/01/pipelight-brings-widevine-support-for.html](http://www.webupd8.org/2014/01/pipelight-brings-widevine-support-for.html)

---

### Post by ErikFaug on 2015-04-14
I'm having the same problems.
After a year of well functioning hbo on ubuntu, with the help of the link that dancljohnson mentions, it stopped working.
I'm located in norway, so we use hbonordic.com, but I believe the technology is the same.

It stopped working just a couple of weeks ago, after HBO renewed the website, and stopped using the widewine plugin.

Flash is integrated in the chrome browser, if you want to try that. I have tried without luck, but it seems it is almost working. My flash version 11 in firefox is differently not working than flash 17 in chrome.

Symptoms: 
Firefox + flash 11: The little animated loading circle just goes on, and the movie won't start.
Chrome (flash 17): The little animated loading circle goes away and the movie seems to be starting, but the progress bar does not move, movie won't start.

---

### Post by ErikFaug on 2015-04-20
Fix from [here]("http://askubuntu.com/questions/609073/new-hbo-nordic-wont-play") worked for hbo nordic:

> Installing the following worked in firefox:

sudo add-apt-repository ppa:mjblenner/hal-flash
sudo apt-get update
sudo apt-get install libhal1-flash 
sudo apt-get install ubuntu-restricted-extras

restart firefox.

---

### Post by michaelchirico4 on 2015-04-20
*ubuntu-restricted-extras *did nothing for me on hbonow.com from the US; I'm running Linux Mint but usually Ubuntu solutions work (Mint is built on Ubuntu).

---

### Post by Sargonmetal on 2015-06-02
Just wanted to say that I followed [these instructions]("http://ubuntuforums.org/showthread.php?t=2274467") and now I can watch HBO Now in the US using Ubuntu 14.04. Should we mark this as solved?

---

### Post by QIII on 2015-06-02
We'll leave that up to the original poster.

---

### Post by michaelchirico4 on 2015-06-15
> **Sargonmetal said:**
> Just wanted to say that I followed [these instructions]("http://ubuntuforums.org/showthread.php?t=2274467") and now I can watch HBO Now in the US using Ubuntu 14.04. Should we mark this as solved?

Confirming this worked on Linux Mint 17.1 (built on Trusty)

---

### Post by windspirit on 2016-04-24
Just though that I would mention I was originally not able to get this to work because I had a really old version of pipelight and apparently update from the older version is broken (see the comments here [https://bugs.launchpad.net/pipelight/+bug/1450622](https://bugs.launchpad.net/pipelight/+bug/1450622) ).  Removing pipelight and starting these instructions from scratch solved the problem.  Running Ubuntu 14.04 in the US.  Also first post!

---

