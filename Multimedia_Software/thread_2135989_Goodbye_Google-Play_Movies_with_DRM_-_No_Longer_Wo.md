---
title: "Goodbye Google-Play Movies with DRM - No Longer Working on Ubuntu or Linux"
date: 2013-04-16
forum: Multimedia Software
---

### Post by phillipblake on 2013-04-16
I hired 'Rise of the Guardians' today off of Google Play.  Cool, my  son's off school, let's watch a movie.  Oh dread... error message just  popped up saying 'You need to upgrade your flash player'.  Ok well  that's impossible in Firefox as flash is stuck at version 11.2.  My  son's starting to hate me for putting Ubuntu on the laptop connected to  the TV.  Think quick, right let's install Google Chrome.  I know that  has the Pepper API which runs the latest version of Flash.  Great, all  done.  Now let's play the movie.  Crap... just a black screen but no  movie.  Let's investigate further.  Are you kidding me, the Pepper API  has a known issue with supporting DRM content on Linux. Argh... 

So  my question to anyone who knows... WTF can I do to get movies streaming  on Ubuntu now?  I had to resort to using my son's Windows 8 machine to  play the movie.  Here's the rub... Google uses its own version of Ubuntu  to develop Andriod and other services (in-house, Mac OS and Windows are  vaguely supported).  So why would they make a stupid move like this,  knowing the limited support for Flash on Linux, to force everyone to use  a later version where DRM won't work?

I did ring Google  directly, they returned my call immediately (respect for that).  I'm in Sydney Australia,  and the gentleman who called back was from Ohio I think, not sure on  that one.  Anyway, his support PC was a Windows machine.  Wow, even  Google still use their competitor's OS for daily tasks.  Anyway, he  couldn't answer my query, he had no experience with Linux (disappointed on that).  So develop  on Linux and run your support on Windows, brilliant!

Can anyone shed any light on a possible solution?  Installing HAL is not going to save us here.... I've already done that.  It worked fine up until today.

Thanks in advance.
Phil

---

### Post by evilsoup on 2013-04-16
Hmm. Have you tried running Chrome, which has its own version of flash for Linux (Pepper Flash)?

This is probably because the various streaming sites are requiring the latest version of flash, which Adobe aren't providing to Linux (they've abandoned the platform entirely). There have been a few threads on this board about 4OD (the online offering of the UK's Channel 4) not working, and the consensus seems to be that the problem is in not having the latest flash.

So - your best hope is probably to try Google Chrome.

---

### Post by phillipblake on 2013-04-16
This sucks!

Chrome Version (type about:version into your omnibox):
Operating System (Windows 7/8/Vista/XP, Mac, Linux, Android, iOS):
Extensions (type Chrome:extensions into your omnibox):when you go to Amazon - Instant Video you get this message:
If  you're using the Chrome browser with Linux, you must disable PPAPI to  continue using Amazon Instant Video. You can also use a different Web  browser, like Firefox. hundreds of other compatible devices -> 
The  Flash Player Plugin in Chrome removed support for Digital Rights  Management (DRM) in Linux as part of the upgrade from 11.3 to 11.4. This  upgrade was bundled with the latest Chrome 22 update for Linux. If you  applied the Chrome update, you are no longer able to watch DRM-protected  content, such as movies and TV episodes. Trailers are unaffected as  they do not use DRM. To get around this issue, you can use a different  browser, such as Firefox. For information on Chrome and the Flash Player  plug-in, see: [https://support.google.com/chrome/bin/answer.py?hl=en&answer=108086](https://support.google.com/chrome/bin/answer.py?hl=en&answer=108086).
the  same problem was in the chromebook however it has been fixed months ago  by Google. Linux tho kernel you use for your net book has not been  fixed. 

Taken from here: [http://productforums.google.com/forum/#!msg/chrome/C-WNbUQI4gU/OyOnK4joy3MJ](http://productforums.google.com/forum/#!msg/chrome/C-WNbUQI4gU/OyOnK4joy3MJ)

Does anyone know if this has been fixed in more recent Kernel updates?

---

### Post by phillipblake on 2013-04-16
Now This is a bit frustrating... So today the Flash player in Firefox is streaming the movie I hired yesterday from Google Play.  I guess I'm to suppose Google reversed the Flash version upgrade requirement ???  I don't know.  But in all I'm a very happy man that I can now play their movies on Ubuntu 12.10 using my favourite browser, Firefox.  Chrome's nice, but firefox just feels more native to Ubuntu.  The integration is more complete from a UI perspective.  Fingers crossed the Flash issues remains solved for now.

---

