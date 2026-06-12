---
title: "This &quot;mailto: link&quot; How-To doesn't work!"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by fredbird67 on 2008-12-29
I just followed the tip in [this thread]("http://ubuntuforums.org/showthread.php?t=326933") to make Ubuntu open Thunderbird when I click a "mailto:" link, but it still gives me the account setup screen for Evolution, even after I've specifically told Firefox (version 3.0.5 running on Hardy Heron, BTW) that I want my "mailto:" links to open in THUNDERBIRD when clicked on.  This one's really ticking me off. :mad: How do I get Firefox to obey my wishes?  This wouldn't by any chance be a bug, would it?

---

### Post by 2hot6ft2 on 2008-12-29
No it's not a bug. I changed mine a few days ago but don't recall how I did it at the moment.

---

### Post by 2hot6ft2 on 2008-12-29
Here it is
>System>Preferences>Preferred Applications
Internet tab > Mail Reader

---

### Post by 2hot6ft2 on 2008-12-29
In Firefox there's
Edit>Preferences>Applications>mailto

---

### Post by fredbird67 on 2008-12-29
I've tried all that.  Still no go.  I've therefore submitted this as a bug report to Launchpad.

---

### Post by Mander on 2009-03-03
Was there a response to this?  It doesn't work for me, either.

---

### Post by eudemus on 2009-06-04
If you've upgraded from Firefox 2 to Firefox 3, the above may not work. But if so, the following might.

Check out this thread
[http://ubuntuforums.org/showthread.php?t=860010&page=2](http://ubuntuforums.org/showthread.php?t=860010&page=2)

Worked for me when nothing else did.
Basically Firefox 3 doesn't use this "network.protocol-handler.app.mailto" thing any more, but if you've upgraded from Firefox 2, you'll have a load of config data set up for it, which seems to confuse Firefox.

Anyway, that thread tells you how to sort it out.
Cheers,
Eudemus

---

### Post by cariboo on 2009-06-04
Personally, I think it is easier to go to Edit-->Preferences-->Applications, and select Mailto-->Use other, then navigate to File System-->/usr/bin/mozilla-thunderbird. Once selected click Close and your done.

---

### Post by eudemus on 2009-06-04
Yes, I fully agree, *if* that works. It didn't for me, and it looks like it hasn't for some others on this thread. Hence I posted what did work.

And, in case there are any other Kubuntu types on the thread, the equivalent path in KDE to what cariboo907 suggests for Gnome is System Settings > Default Applications. Definitely worth trying first.

---

