---
title: "Cannot get Netflix to work."
date: 2014-11-24
forum: Multimedia Software
---

### Post by chris323 on 2014-11-24
Hello everyone,

I have gone through various methods of trying to get Netflix to play; firefox client switcher, pipelight, wine, and google chrome with none of it working.  I keep getting error code M7063-1913 or the install silverlight prompt. Looking in my netflix account there is no option to switch to HTML5 so im not sure if it is automatic or it just won't let me.  If there is anything i am missing let me know, any help would be appreciated.

Thanks


Disclaimer: I am relatively new to Ubuntu and linux so I may just completely be missing a very basic concept but now im in the third hour of searching and attempting various things and I have hit the wall  :confused:

---

### Post by coffeecat on 2014-11-24
I've moved your post into its own thread - always the best option.

The current latest version of Google Chrome should just work in Ubuntu with no configuration neeeded beyond logging into your Netflix account. So...

Which version of Ubuntu are you using, which version of Chrome and, very importantly, are you using Chrome or Chromium? Chromium browser will not do - it has to be Chrome.

---

### Post by QIII on 2014-11-24
You may find some older instructions for Chrome saying you need to use a user agent switcher.  You don't even have to do that any longer.

I just wiped and reinstalled Kubuntu last weekend.  Installed Chrome.  Logged in to Netflix.  Watched "Catching Fire".  No effort at all.

---

### Post by chris323 on 2014-11-24
Ubuntu was installed on this machine yesterday, I am using 14.04 LTS and yes it is chrome, not chromium.

I have done the updates to Ubuntu and I have also uninstalled chrome and then re-installed it still unable to watch.

Edit:  I ran some uninstalls on the programs I had downloaded to try and run it originally and did another restart and it is working now right in chrome with no modifications.

Thanks for the help

---

### Post by jawilljr2 on 2014-11-24
> **chris323 said:**
> Ubuntu was installed on this machine yesterday, I am using 14.04 LTS and yes it is chrome, not chromium.

I have done the updates to Ubuntu and I have also uninstalled chrome and then re-installed it still unable to watch.

Edit:  I ran some uninstalls on the programs I had downloaded to try and run it originally and did another restart and it is working now right in chrome with no modifications.

Thanks for the help

Do you have the latest libnss3 installed? You have to have 3.16.2 or greater.

What is the output of the following?

```
apt-cache policy libnss3
```

the below is what I get when I run the above command:

```
libnss3:
  Installed: 2:3.17.1-0ubuntu0.14.04.1
  Candidate: 2:3.17.1-0ubuntu0.14.04.1
  Version table:
 *** 2:3.17.1-0ubuntu0.14.04.1 0
        500 http://ubuntu.mirror.frontiernet.net/ubuntu/ trusty-updates/main amd64 Packages
        500 http://ubuntu.mirror.frontiernet.net/ubuntu/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2:3.15.4-1ubuntu7 0
        500 http://ubuntu.mirror.frontiernet.net/ubuntu/ trusty/main amd64 Packages
```

You also need Chrome version 38 or greater.

---

### Post by chris323 on 2014-11-24
> **jawilljr2 said:**
> Do you have the latest libnss3 installed? You have to have 3.16.2 or greater.

What is the output of the following?

```
apt-cache policy libnss3
```

I got the same results, there was just some old software that hadn't been un-installed that was for some reason getting in the way.
It all works now thanks though!

```

libnss3:
  Installed: 2:3.17.1-0ubuntu0.14.04.1
  Candidate: 2:3.17.1-0ubuntu0.14.04.1
  Version table:
 *** 2:3.17.1-0ubuntu0.14.04.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2:3.15.4-1ubuntu7 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
```

---

### Post by mfilacchione on 2014-11-25
Hey Chris Check out this thread where I were I have had a extensive discussion on this.  It may help you... if you decide to play with Netflix any further.   [ht]("http://ubuntuforums.org/showthread.php?t=2253183")[URL="http://ubuntuforums.org/showthread.php?t=2253183"]tp://ubuntuforums.org/showthread.php?t=2253183
[/URL]I am going to try to post in other browsers too.  If you do not mind me asking what was the software I am curious to what was causing the problem originally if you have time to share?

---

