---
title: "Flash and Firefox"
date: 2016-06-21
forum: Multimedia Software
---

### Post by oygle on 2016-06-21
Have followed quite a number of posts and done the steps shown to try to fix this.

Can't get Flash to work in Firefox. The addons/plugins in Firefox states Shockwave Flash 13.1.2.3, Firefox is vers 44

From Muon, it says 'adobe-flashplugin' is installed  ??

---

### Post by cmcanulty on 2016-06-21
I love firefox but have finally decided to use chrome for videos, because no matter how much I tweak firefox it will seldom run any video. Ad ons blockers, etc adnauseum.

---

### Post by &amp;KyT$0P# on 2016-06-21
> **oygle said:**
> The addons/plugins in Firefox states Shockwave Flash 13.1.2.3
This sounds like freshplayerplugin Flash missing the PPAPI Flash plugin.
Are you trying to use freshplayerplugin or the adobe-flashplugin from the repository?

---

### Post by cmcanulty on 2016-06-21
I am using the flashplayer plugin.I am wary of fresh player due to this quote
"Currently, to test Fresh Player Plugin (remember, it's in early development stages and its functionality is limited; it doesn't work with many websites, including YouTube!) you must build it from source. " from

[http://www.webupd8.org/2014/05/fresh-player-plugin-pepper-flash.html]("http://www.webupd8.org/2014/05/fresh-player-plugin-pepper-flash.html")

---

### Post by QDR06VV9 on 2016-06-21
But that was posted back in may 2014.
And This as Quoted.
> **Update: you can now [install Fresh Player Plugin in Ubuntu via PPA]("http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html")!**

---

### Post by cmcanulty on 2016-06-21
OK sorry I didn't notice the year. I installed it and same issue flash and youtube don't play in firefox, fine in chrome. Seems like a really dumb problem for firefox.

---

### Post by bearlake on 2016-06-21
Using freshplayerplugin Flash for all sites here with no issues. Even works 100% with [URL="http://www.pogo.com/"]pogo.com


[/URL]

---

### Post by QDR06VV9 on 2016-06-21
No worries:D But i agree it is better to err on the side of caution.
A lot of firefox users report that the flashplugin-installer is needed...I do not know for sure as I use Seamonkey with no problems with fresh-player and pepper-flash.
And I am not trying to convince you to use seamonkey.;)
Regards

---

### Post by bearlake on 2016-06-21
> **runrickus said:**
> No worries:D But i agree it is better to err on the side of caution.
A lot of firefox users report that the flashplugin-installer is needed...I do not know for sure as I use Seamonkey with no problems with fresh-player and pepper-flash.
And I am not trying to convince you to use seamonkey.;)
Regards

I actually remove flashplugin-installer before adding freshplayer to FireFox. ;-)

---

### Post by QDR06VV9 on 2016-06-21
I guess it works with both then.
```
$ apt-cache policy flashplugin-installer
flashplugin-installer:
  Installed: 11.2.202.626ubuntu0.16.04.1
  Candidate: 11.2.202.626ubuntu0.16.04.1
  Version table:
 *** 11.2.202.626ubuntu0.16.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 Packages
        100 /var/lib/dpkg/status
     11.2.202.616ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/multiverse amd64 Packages


```

---

### Post by oygle on 2016-06-24
Thanks for all the replies. It works now. Am using adobe-flashplugin from Muon (installed). The Firefox add-ons display has:

Shockwave Flash 13.1.2.3
Last Updated  03/05/16
File:    libfreshwrapper-flashplayer.so

---

