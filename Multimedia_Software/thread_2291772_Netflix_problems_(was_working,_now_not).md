---
title: "Netflix problems (was working, now not)"
date: 2015-08-22
forum: Multimedia Software
---

### Post by T Stew on 2015-08-22
Hi all, been a linux Ubuntu 12.04 user for a few years now. It took some work, but one of the first things I did was got Netflix working. I don't really watch any other TV besides Netflix on this computer.

Recently I had been getting a message at the top of the Netflix screen that I needed to update my browser to continue using Netflix... but it still worked despite that. Then a few days ago when I signed on the layout of Netflix was very different, and when I selected something to watch it just spun and never played. I thought maybe the error message before was a forewarning, and finally they implemented whatever changes that required me to upgrade. So I went and clicked on it and started the upgrade process. I honestly don't even remember what exactly it was upgrading, but it seemed to freeze up in the middle of the process. Eventually I had to quite to app, and when I retried Netflix the icon would appear on my app bar flashing for a few seconds, then disappearing. Nothing ever launched on the screen.

Not really knowing how to troubleshoot, I sought out help on google, and just tried to follow a few of the pages with instructions on how to install Netflix. One thing I tried was pipelight [http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html) and that did not work. I did run the indicated system check (Pipelight can now check your system  for common issues which could prevent it from working. To run the  Pipelight system check tool, use this command:pipelight-plugin --system-check )

And I got a few things passed and then a failure under Libraries. All the instructions out there are how to get it going from scratch so not sure if my situation is different seeing how it was working. Perhaps I just need to wipe out everything that is installed for it, but I don't know how to do that. Any suggestions? If I upgrade to 14.04 will it wipe everything out so I can start over? I've been meaning to do the update but everything had been working fine and I haven't had a lot of time or the ambition to tempt fate upgrading my nicely working system!

I am not sure if its related, but I recently found that my blu-ray playing capability broke as well (I used VLC). I sought out instruction as if I were doing it for the first time and installed a few things via the command line and got blu-ray working again. 

I would really appreciate any help, Thanks!

---

### Post by monkeybrain20122 on 2015-08-22
What are you using to watch Netflix? The old Netflix app (probably deprecated) was basically a copy of Windows Firefox running in wine, seems it hasn't been updated for a while and the FF version is outdated.

Anyway, this is no longer the recommended way. There are two options:

1. Chrome (not Chromium) plays netflix out of the box. Don't need to do anything.

2. Firefox with pipelight's silverlight plugin and the user-agent-overrider addon. If after enabling silverlight it still doesn't register in FF (Tools > Addons > Plugins should show an entry for it, if it doesn't show it is not registered) Close FF and run in the terminal

```
sudo pipelight-plugin --create-mozilla-plugins
```

You may need to update your user-agent-overrider addon's version for Windows' Firefox (check what is the latest Windows version of FF in uao's drop down, if it is Firefox 29 it wouldn't work) If you already have something like Windows Firefox 38 in uao's drop down then just pick that; if you have only a very old Winows Firefox (say 29), do this:

Click the arrow beside the user-agent-overrider's icon, from the drop down choose Preferences, then change the line
> Windows / Firefox 29: Mozilla/5.0 (Windows NT 6.1; WOW64; rv:29.0) Gecko/20100101 Firefox/29.0
to
> Windows / Firefox 40: Mozilla/5.0 (Windows NT 6.1; WOW64; rv:29.0) Gecko/20100101 Firefox/40.0

Note rv:29 doesn't change. Then you will see an entry for Windows Firefox 40 in uao's drop down and Netflix should be ok with that.

---

### Post by T Stew on 2015-08-22
Hey thanks for the response. I believe it was an actual Netflix app I was running, and it opened in what seemed a different version of firefox than the firefox I would browse the web with, probably like you say a windows version of firefox in wine. This worked fine up until just recently.

Sounds like Chrome would be the easiest way if it supports it directly! I'll look into installing that maybe tonight. But since I have just a minute I tried your next suggestion since silverlight was not showing in my add-ons. After running that code (with FF closed) it is still not showing up. I got to run so haven't tried those uao things. Will do that next, unless I just decide to load Chrome.

---

### Post by T Stew on 2015-08-22
Ok just got back home - went straight for the Chrome solution and even though not in software center, a pretty easy download and install. Already signed in an Netflux up. Thanks a million! If your in central Ohio I'll buy ya a beer.

---

### Post by QIII on 2015-08-23
Hello!

Glad that worked!

I usually don't like to see "try something else" as an answer to requests for support on the Forums.

However, Netflix is an unusual case.  Chrome really is the best answer at the moment.  I think that attempting to help get it working with Firefox would have been an exercise in frustration so great that answering the original question of how to get Firefox to work would have been a disservice. 

Cheers!

---

### Post by T Stew on 2015-08-23
QIII, agreed. In this case I just wanted to get it working by any method.

Curious though, this install of Chrome seems to be the only app I've ever had on Ubuntu that does not leave an icon or even an entry on the 'recent apps' on the dash home button. Is there an easy way to get this to show up in recent apps or leave an icon on the launch bar instead of typing a command in terminal each time? No big deal if I have to use terminal, but just thought I'd ask.

---

### Post by coffeecat on 2015-08-23
> **T Stew said:**
> Is there an easy way to get this to show up in recent apps or leave an icon on the launch bar instead of typing a command in terminal each time? No big deal if I have to use terminal, but just thought I'd ask.

No need to use the terminal at all. Type "chrome" in the dash in order to show up the Google Chrome icon there and then drag and drop it into the launcher.

**Edit:** That might not work with 12.04. If not, type chrome as before and open Chrome from its icon in the dash. While it is open, an icon will appear in the launcher. Right-click on the launcher icon and select lock to launcher.

---

### Post by monkeybrain20122 on 2015-08-23
> **QIII said:**
> Hello!

Glad that worked!

I usually don't like to see "try something else" as an answer to requests for support on the Forums.

However, Netflix is an unusual case.  Chrome really is the best answer at the moment.  I think that attempting to help get it working with Firefox would have been an exercise in frustration so great that answering the original question of how to get Firefox to work would have been a disservice. 

Cheers!

Actually, it works rather well in FF (with pipelight) and not too hard to set up. OP originally used the Netflix app, which is different from using pipelight in Firefox, but basically to run a modified version of Windows' Firefox itself in Wine and that is deprecated I think. Hardware acceleration of HTML5 in Chrome works much than silverlight in FF (not sure if hardware acceleration even works in pipelight even though dev claims it does) so this is one thing to consider if you have a weak cpu,--on my corei5 I can't see a difference in performance

Some people don't like to use Chrome so I included instructions for FF as well.

---

### Post by T Stew on 2015-08-23
> **coffeecat said:**
> No need to use the terminal at all. Type "chrome" in the dash in order to show up the Google Chrome icon there and then drag and drop it into the launcher.

**Edit:** That might not work with 12.04. If not, type chrome as before and open Chrome from its icon in the dash. While it is open, an icon will appear in the launcher. Right-click on the launcher icon and select lock to launcher.

That's odd. Of course I tired the right click and 'lock to launcher' prior but it did not have that as an option, just to open a new tab or quit. When I just did it, I did have the option, so locked it to the launcher. 

Edit> Oh wait, I think the difference is launching from terminal - in that case it doesn't give you the lock to launcher option. All is good now.

---

