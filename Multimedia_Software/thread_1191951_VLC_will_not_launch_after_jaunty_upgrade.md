---
title: "VLC will not launch after jaunty upgrade"
date: 2009-06-19
forum: Multimedia Software
---

### Post by mixtri on 2009-06-19
Hi guys. Please could someone help.
I recently upgraded to jaunty via update manager.

The upgrade was successful, but upon launching VLC - media player it opened with two windows. I made some tweaks in preferences sub menu so that it would behave the way it did prior to the upgrade.
After that VLC wouldn't launch anymore.
I have removed, purged and reinstalled VLC a few times but iT REFUSES  to launch. its as if its not installed even though it is.

Has anyone else had this problem? Is there anyway I can resolve this issue?

---

### Post by starcraft.man on 2009-06-19
I really REALLY hate the default broken VLC package. It's by far the best video player and it really irks me that they still haven't fixed it.

[This link]("http://webupd8.blogspot.com/2009/05/install-vlc-10-rc-in-ubuntu-from-ppa.html") gives the repository for the 1.0 RC release. I assume you know how to add it to your sources and get the key with the command. After that simply install from the terminal or synaptic VLC and you should get the latest working version.

I had a better link with more details, but I'm not on my main machine atm.

---

### Post by mixtri on 2009-06-19
Thanks a bunch StarCraft.
You're spot on! VLC is the best player. Currently using Mplayer which is alright but still no match for VLC; and thats why i've spent a ridiculous amount of time trying to sort this problem.

Thanks for the link, it has all the details I need. Will let you know how it pans out .
Cheers

---

### Post by mixtri on 2009-06-19
I tried your suggestion and reinstalled VLC. and still won't launch. It won't put any launch icons in the menu area and will not launch from the executable either.

Grr:mad:
Further assistance required ):P

---

### Post by starcraft.man on 2009-06-19
> **mixtri said:**
> I tried your suggestion and reinstalled VLC. and still won't launch. It won't put any launch icons in the menu area and will not launch from the executable either.

Grr:mad:
Further assistance required ):P

Push alt + F2 (the run dialog) then just type in vlc then push enter. If an error is returned please printscreen it (then attach to reply) or just type it here. If it launches, then it's simply a small bug with shortcuts and you can make your own.

---

### Post by cotcot on 2009-06-19
I got mine OK with some code I picked up from another thread :

```
vlc --reset-config --reset-plugins-cache
```

---

### Post by mixtri on 2009-06-19
Cotcot!1 You're a genious!!
Thanks a lot guys. This solved my problem.
Why isn't there a fix for this problem? Are the Ubuntu team not aware of this problem with vlc?

---

### Post by mixtri on 2009-06-19
A thanks to u starcraft for your help. cheers

---

### Post by starcraft.man on 2009-06-19
> **mixtri said:**
> Cotcot!1 You're a genious!!
Thanks a lot guys. This solved my problem.
Why isn't there a fix for this problem? Are the Ubuntu team not aware of this problem with vlc?

It's a long story. The gist of it I believe is it's kinda a bureaucratic thing based on how packages get approved and put into the repos. VLC has already fixed the problem as noted by the later 1.0 RC your using. I'm fairly certain it's been submitted numerous times to launchpad though I don't follow such closely.

Edit: Your very welcome my friend, enjoy!

---

### Post by mixtri on 2009-06-19
Hmm. So what exactly was fixed in 1.0RC; the issue with vlc failing to launch after messing around with the settings in Prefences Menu? (Previous release), or is it the issue of vlc **failing** to relaunch after a _fresh install_? (This affected both the old version as well as the current release when i reinstalled them both?

It just seems to me that this particular issue has not yet been addressed, otherwise I wouldn't have needed to **manually** reset the plugins - cache blah blah as Colcolt suggested, it should have been done automatically during either an uninstallation or fresh install of the application dont you think?

---

### Post by mc4man on 2009-06-19
> So what exactly was fixed in 1.0RC
Among other things having the 'embedded video' would no longer possibly cause a race condition (plus some interesting new features in rc3

> the issue with vlc failing to launch after messing around with the settings in Prefences Menu

That's not an 'issue', just the result of

Whenever you switch versions you should reset the config, most certainly if going from 0.9.x to 1.x, even when going from 0.9.4 to 0.9.9a.
 On a fresh install it wouldn't be necessary, when you do an upgrade though, anything can happen

The overall fact is 0.9.x has some issues, 1.0.0Rc3 also has some issues unresolved, not everything will work right.
1.0 will hopefully be 'fixed', 0.9.9a is what it is (maybe there will be a 0.9.9b probably not

---

### Post by mixtri on 2009-06-19
Ok I suppose that makes some sense. but I still think it makes sense the config reset be handled by the application installer/uninstaller automatically rather than leave it to user intervention.

Thank God for the forums!

---

### Post by papiaud on 2009-06-28
> **mixtri said:**
> Cotcot!1 You're a genious!!
Thanks a lot guys. This solved my problem.
Why isn't there a fix for this problem? Are the Ubuntu team not aware of this problem with vlc?

I fully agree with all the remarks of mixtri. I had vlc not working : I still don't know why, but with the command line given by cotcot it works again. Thanks to you both. I continue and insist with the request of mixtri : "Why isn't there a fix for this problem?". Very often I get fixes (and for this I thanks very much those people working for us) but I think this one is missing.

---

