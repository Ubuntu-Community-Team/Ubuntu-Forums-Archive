---
title: "Hulu and Miro"
date: 2009-04-15
forum: Multimedia Software
---

### Post by andrea000 on 2009-04-15
Anyone had a problem with miro playing flash video's
from hulu or any website?Would anyone have a work 
around for it.I am not having a problem with flash
just fixed that a few days ago and i can play a video
from hulu but not with miro.

---

### Post by pytheas22 on 2009-04-16
Perhaps you don't have the codecs installed that Miro needs to play video.  The easiest way to install codecs is via the ubuntu-restricted-extras package.  To install it, just type:
```

sudo apt-get install ubuntu-restricted-extras
```

When it's done installing (it may take a while to download the package), restart Miro and see if it works better.

---

### Post by andrea000 on 2009-04-16
Thank you that worked

---

### Post by mickey12gauge on 2009-04-16
I'm having a similar problem but I already have ubuntu-restricted-extras package installed and still unable to use Miro's "sites" tab. I keep getting the following message:

Sorry! Sites aren't supported on Linux due to an incompatibility with the Flash plugin.

---

### Post by pytheas22 on 2009-04-16
mickey12gauge: which version of flash do you have installed on your computer?  Are you using the plugin from Adobe (installed via the package flashplugin-nonfree) or one of the free players (gnash or swfdec)?

Also, is your computer 32 or 64-bit?

If you don't know the answer to these questions, please post the output of these commands:
```

locate flash | grep firefox
uname -rm
```

---

### Post by mickey12gauge on 2009-04-16
> **pytheas22 said:**
> mickey12gauge: which version of flash do you have installed on your computer?  Are you using the plugin from Adobe (installed via the package flashplugin-nonfree) or one of the free players (gnash or swfdec)?

Also, is your computer 32 or 64-bit?

If you don't know the answer to these questions, please post the output of these commands:
```

locate flash | grep firefox
uname -rm
```

Adobe Flash Player version 10.0.22.87

I'm using the plugin from Adobe

2.6.27-11-generic i686

---

### Post by pytheas22 on 2009-04-16
mickey12gauge: are you sure you don't have any other flash plugins installed anywhere?  It seems that things should work with the Adobe plugin so I'm really not sure what's going on in your case.  If you were on a 64-bit system, that could also potentially complicate things (because Adobe's plugin is 32-bit and requires a special wrapper (although a 64-bit Linux plugin has recently become available, but is still not the default in Ubuntu)), but that doesn't apply to your situation.

When I google the error message that you posted above, it returns virtually no results, which is strange--if this were a common problem, there should be more hits...

---

### Post by gandaran on 2009-04-17
> **mickey12gauge said:**
> Adobe Flash Player version 10.0.22.87

I'm using the plugin from Adobe

2.6.27-11-generic i686
the adobe flash plugin is installed in the firefox plugins directory and can only be used by a web browser, it won't work in miro unless you open the video in firefox.

---

### Post by deshantm on 2009-07-25
A few useful threads on the Miro help search reveal that they intentionally disabled Flash on Linux due to crashing.

See:

[http://getsatisfaction.com/participatoryculturefoundation/topics/_sites_in_the_sidebar_doesnt_work_in_linux?utm_medium=widget&utm_source=widget_participatoryculturefoundation](http://getsatisfaction.com/participatoryculturefoundation/topics/_sites_in_the_sidebar_doesnt_work_in_linux?utm_medium=widget&utm_source=widget_participatoryculturefoundation)

[http://getsatisfaction.com/participatoryculturefoundation/topics/linux_support_should_be_universal?utm_medium=widget&utm_source=widget_participatoryculturefoundation](http://getsatisfaction.com/participatoryculturefoundation/topics/linux_support_should_be_universal?utm_medium=widget&utm_source=widget_participatoryculturefoundation)

[http://getsatisfaction.com/participatoryculturefoundation/topics/why_does_the_site_feed_for_things_like_hulu_not_work_under_linux?utm_medium=widget&utm_source=widget_participatoryculturefoundation](http://getsatisfaction.com/participatoryculturefoundation/topics/why_does_the_site_feed_for_things_like_hulu_not_work_under_linux?utm_medium=widget&utm_source=widget_participatoryculturefoundation)

[http://getsatisfaction.com/participatoryculturefoundation/topics/no_flash_player?utm_medium=widget&utm_source=widget_participatoryculturefoundation](http://getsatisfaction.com/participatoryculturefoundation/topics/no_flash_player?utm_medium=widget&utm_source=widget_participatoryculturefoundation)

---

