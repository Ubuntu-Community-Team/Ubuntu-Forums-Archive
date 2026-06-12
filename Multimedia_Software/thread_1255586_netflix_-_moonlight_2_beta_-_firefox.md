---
title: "netflix - moonlight 2 beta - firefox"
date: 2009-09-01
forum: Multimedia Software
---

### Post by svenwinkle on 2009-09-01
I would like to start some discussion on trying to get moonlight to work with netflix.  It *feels* like it's very close to working.  I could be wrong of course, I'm not a developer and there may be a limitation I'm not considering.  So far I have done the following:

1. Installed latest firefox 3.5
2. Installed the latest Moonlight - [http://www.go-mono.com/moonlight-beta/](http://www.go-mono.com/moonlight-beta/)
3. Installed the Microsoft Codec Pack (little tricky) - [http://tinyurl.com/n9k223](http://tinyurl.com/n9k223)
4. Installed user agent switcher for firefox - [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)
5. Added the following user agent to make websites think I am using Mac OS/X Intel (to get netflix to ignore the fact that I don't have active x):
useragent description="FireFox 3.5.0.0 (Mac OSX)" useragent="Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10.5; en-US; rv:1.9.1.2) Gecko/20090729 Firefox/3.5.2" appcodename="" appname="" appversion="" platform="" vendor="" vendorsub=""

After doing all this, I am able to get netflix to try to play a movie.  It fails however and tells me either error 2105 or that I need to install the latest silverlight (3.0).  Previous to doing everything above it would never actually try to play, it would just error immediately.

My question is now, does anyone have any suggestions for fooling netflix into thinking that my moonlight implementation is actually silverlight 3?  I have tried editing a couple files within my .mozilla/firefox directory with no luck so far.  There is a file in .mozilla/firefox/gibberish.default/extensions/moonlight@novell.com/plugins/moonlight/ called System.Windows.dll that I assume is what needs to be changed and if so then I may be dead in the water.

I'm open to any suggestions.  It would be pretty cool to get this working.

---

### Post by directhex on 2009-09-01
> **svenwinkle said:**
> I would like to start some discussion on trying to get moonlight to work with netflix.  It *feels* like it's very close to working.  I could be wrong of course, I'm not a developer and there may be a limitation I'm not considering.  So far I have done the following:

1. Installed latest firefox 3.5
2. Installed the latest Moonlight - [http://www.go-mono.com/moonlight-beta/](http://www.go-mono.com/moonlight-beta/)
3. Installed the Microsoft Codec Pack (little tricky) - [http://tinyurl.com/n9k223](http://tinyurl.com/n9k223)
4. Installed user agent switcher for firefox - [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)
5. Added the following user agent to make websites think I am using Mac OS/X Intel (to get netflix to ignore the fact that I don't have active x):
useragent description="FireFox 3.5.0.0 (Mac OSX)" useragent="Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10.5; en-US; rv:1.9.1.2) Gecko/20090729 Firefox/3.5.2" appcodename="" appname="" appversion="" platform="" vendor="" vendorsub=""

After doing all this, I am able to get netflix to try to play a movie.  It fails however and tells me either error 2105 or that I need to install the latest silverlight (3.0).  Previous to doing everything above it would never actually try to play, it would just error immediately.

My question is now, does anyone have any suggestions for fooling netflix into thinking that my moonlight implementation is actually silverlight 3?  I have tried editing a couple files within my .mozilla/firefox directory with no luck so far.  There is a file in .mozilla/firefox/gibberish.default/extensions/moonlight@novell.com/plugins/moonlight/ called System.Windows.dll that I assume is what needs to be changed and if so then I may be dead in the water.

I'm open to any suggestions.  It would be pretty cool to get this working.

Netflix uses DRM, which categorically does not work in Moonlight. Sorry. If a) Netflix dump the DRM, b) Microsoft provide access to the required source so DRM support can be added to the Microsoft Media Pack, then it'll work. Otherwise, nope.

If in doubt, complain to Netflix

---

### Post by svenwinkle on 2009-09-01
Ah, I was under the impression that drm was included in the microsoft media pack.  I also did not know that the mono project had forums.  I found them at [www.go-mono.com/forums](www.go-mono.com/forums).  

Thanks

---

