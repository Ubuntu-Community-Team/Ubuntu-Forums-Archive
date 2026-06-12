---
title: "Seek and Destroy! (Maverick -&gt; Natty Beta 1, mostly flawless)"
date: 2011-04-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by manzdagratiano on 2011-04-04
BUGS that is!

I could not resist the temptation to upgrade to the beta release, considering this is a release that has polarized such a humongous number of people. Here is my experience and issues I encountered, and I wish to write useful bug reports so all these are ironed out one by one for the final polished version, and to this end, I would request for help from the community in properly identifying the problems - since in the end what we all want is the same thing - the perfect user experience:

The device in question is a Sony Vaio VGNAR520E, which comes with nvidia Geforce 8400 (I do not have it at the moment - it is mostly a home "desktop", but I will fiddle with it once I am back in the evening).

**ISSUES:**

The upgrade itself went flawlessly - no complaints whatsoever. The system offered for a successful reboot.

*> As is known by a wide audience who use nvidia cards, installing the proprietary nvidia drivers kills the framebuffer, which problem can be corrected by installing the framebuffer-in-userspace drivers, or v86d. I had, a couple of days **prior to the upgrade**, followed mostly the guide in:
[HTML]http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml[/HTML]and had ended up with a beautiful framebuffer.
However, after the upgrade, there is no more plymouth logo upon booting. Booting also takes longer than it did in Maverick.

*> I logged into the "Ubuntu" option in GDM, which is the one with Unity enabled. Panels took a few extra seconds to load, but everything seemed to be working well. A few seconds into the session I received an error message "**System Program Problem Detected**" which does **not** mention what program and offers to send a bug report. However, apport did not start after I chose to send the report (then again, I have never successfully sent out a bug report using apport - I always do it from Launchpad). I guess I shall have to look at the log file regarding what it was, but that will have to wait till the evening.

*> Followed by this was an error that **plymouthd had crashed**. There is an old bug report on this dating from the days of Lucid that states that a fix has been released, but I guess the issue persists. There are bug #740071, bug # 739290 and bug # 738374 all of which are stated to be duplicated of bug # 708517, but that Launchpad page does not exist! This did not affect the running of the system though.

*> Changing settings in ccsm (enable wobbly windows, thereby disabling snapping windows) caused compiz to momentarily crash (error message), but it was back up without me having to do anything.

*> I noticed that the upgrade had installed network-manager **on top of wicd**, which was in the previous install (For myself alone, I think network-manager is useless since in other distros - mostly Arch, Slack (no kde) and Gentoo, you begin without X, and network-manager cannot connect unless the GUI is loaded. I have tried cnetworkmanager but it did not work, while wicd-curses is phenomenally awesome and has never failed me). Naturally, network-manager failed to connect since wicd was also up and connected. I uninstalled it right away. However, there was **no wicd tray icon** in unity. Nor was there a dropbox icon, and I did not see a way (at least then) to add them back. Maybe this is the "zero-configuration experience" part, but I would like to see these two things back in the tray.

*> Also installed were **banshee, tomboy** and **shotwell**, all three of which I do not care about (I love my sticky notes in the panel, and the gimp is what I prefer since it allows me greater control). If the upgrade-manager does not see these programs on the machine, it should assume that they were removed manually, since they come with the default distribution, and **not re-install them**. Banshee I guess was installed because it was a new change, but I prefer rhythmbox, and I am going with it.

*> **Logging out of the session caused X to black out**. Also, I could see that the framebuffer was acting up again. Pressing CTRL+ALT+DEL caused the system to reboot.

*> Choosing **Ubuntu Classic**, the session without Unity, dropped me back to the familiar Gnome interface, with both wicd and dropbox back in the tray. **No system program problem, no plymouthd crash**. The wobbly windows plugin was disabled again; **re-enabling it this time caused no compiz crash**.
However, **logging out of the gnome session caused X to crash again** (no gdm respawn).

The new "magic kernel" seems to indeed be running faster than before, though I have not had time to test it extensively.
I cannot say I dislike Unity, but in the event I cannot customize it (or at least certain aspects of it), I would be *very* unhappy. I am happy putting a few programs in the launcher, and searching for programs as opposed to looking serially in a menu is not half-bad either, but the absence of icons from the system tray is a killer - I should be able to customize them. I would also like to put sticky-notes back into the panel, which I realize cannot be done right now since this is not gnome-panel.

So there are all the issues so far, and I want to write bug reports. I guess the serious bugs so far are:

*> plymouthd crash (unity), compiz crash upon ccsm changes (unity),  X crash upon session logout (Unity/Gnome Classic).

Minor bugs:

*> Update manager re-installs network-manager, shotwell, tomboy, even though these were removed (of these, I believe network-manager would be the real issue).

*> Tray icons missing in the unity panel.

I would like to know which of these issues have been duplicated elsewhere, and which of them are genuine, and also which have already been resolved. I do know that a clean install may be preferable to an upgrade, but I do not think that that's what the goal of the devs is.

And I do believe that we should all strive to move forward to the next evolution of Ubuntu, and not be dissuaded just by Unity in the event one does not like it - installing the old gnome interface (which for now is installed by default anyway) is just a few commands away! As re-iterated many times in the forums, the choice factor is still there first and foremost. Distros ship with what they think is the direction they want to take, but they also allow the users freedom to make them they way they would like. (I would merely point to the example of slackware dropping gnome from its repos, and shipping kde. I used to be a kde person when I first got into GNU/Linux, but am not anymore, but that would not prevent me from using Slackware itself.)

---

### Post by lucazade on 2011-04-04
> As is known by a wide audience who use nvidia cards, installing the proprietary nvidia drivers kills the framebuffer, which problem can be corrected by installing the framebuffer-in-userspace drivers, or v86d. I had, a couple of days prior to the upgrade, followed mostly the guide in:
HTML Code:
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)
and had ended up with a beautiful framebuffer.
However, after the upgrade, there is no more plymouth logo upon booting. Booting also takes longer than it did in Maverick.

I think that guide is not good for Natty, because from this release uvesafb framebuffer is used when a closed driver (without KMS) is finded at boot.
Also grub now identifies monitor modelines and keeps resolution untill plymouth is loaded. (gfx_payload= keep)
I suggest you to revert to defaults (removing v86d and friends) and try again to see if it helps.
(there is a blue print about plymouth improvements in this release on launchpad)

> >* I logged into the "Ubuntu" option in GDM, which is the one with Unity enabled. Panels took a few extra seconds to load, but everything seemed to be working well. A few seconds into the session I received an error message "System Program Problem Detected" which does not mention what program and offers to send a bug report. However, apport did not start after I chose to send the report (then again, I have never successfully sent out a bug report using apport - I always do it from Launchpad). I guess I shall have to look at the log file regarding what it was, but that will have to wait till the evening.

*> Followed by this was an error that plymouthd had crashed. There is an old bug report on this dating from the days of Lucid that states that a fix has been released, but I guess the issue persists. There are bug #740071, bug # 739290 and bug # 738374 all of which are stated to be duplicated of bug # 708517, but that Launchpad page does not exist! This did not affect the running of the system though.

I don't have these issues.. might be also related to the previous plymouth issue.

> *> Changing settings in ccsm (enable wobbly windows, thereby disabling snapping windows) caused compiz to momentarily crash (error message), but it was back up without me having to do anything.

This is a known issue, I think it is related to compiz++  and glib (I've read some bug reports and something in ayatana irc channel from authors)

> *> I noticed that the upgrade had installed network-manager on top of wicd, which was in the previous install (For myself alone, I think network-manager is useless since in other distros - mostly Arch, Slack (no kde) and Gentoo, you begin without X, and network-manager cannot connect unless the GUI is loaded. I have tried cnetworkmanager but it did not work, while wicd-curses is phenomenally awesome and has never failed me). Naturally, network-manager failed to connect since wicd was also up and connected. I uninstalled it right away. However, there was no wicd tray icon in unity. Nor was there a dropbox icon, and I did not see a way (at least then) to add them back. Maybe this is the "zero-configuration experience" part, but I would like to see these two things back in the tray.

There is a whitelist where to enable old systray icons (notification-area) like for skype and also for wicd. Don't remeber now which is this file.. I'll look! 

> *> Also installed were tomboy and shotwell, both of which I do not care about (I love my sticky notes in the panel, and the gimp is what I prefer since it allows me greater control). If the upgrade-manager does not see these programs on the machine, it should assume that they were removed manually, since they come with the default distribution, and not re-install them.

*> Logging out of the session caused X to black out. Also, I could see that the framebuffer was acting up again. Pressing CTRL+ALT+DEL caused the system to reboot.

*> Choosing Ubuntu Classic, the session without Unity, dropped me back to the familiar Gnome interface, with both wicd and dropbox back in the tray. No system program problem, no plymouthd crash. The wobbly windows plugin was disabled again; re-enabling it this time caused no compiz crash.
However, logging out of the gnome session caused X to crash again (no gdm respawn).
Don't have these, I can't help.

If I find bug report number I'll report here.

---

### Post by manzdagratiano on 2011-04-04
> **lucazade said:**
> I think that guide is not good for Natty, because from this release uvesafb framebuffer is used when a closed driver (without KMS) is finded at boot.
Also grub now identifies monitor modelines and keeps resolution untill plymouth is loaded. (gfx_payload= keep)
I suggest you to revert to defaults (removing v86d and friends) and try again to see if it helps.
(there is a blue print about plymouth improvements in this release on launchpad)



I don't have these issues.. might be also related to the previous plymouth issue.


This is a known issue, I think it is related to compiz++  and glib (I've read some bug reports and something in ayatana irc channel from authors)



There is a whitelist where to enable old systray icons (notification-area) like for skype and also for wicd. Don't remeber now which is this file.. I'll look! 


Don't have these, I can't help.

If I find bug report number I'll report here.

Thank you very very much!!! I will get on these when I get back in the evening and get back to you!

---

### Post by cariboo on 2011-04-04
With the latest updates, networking is enabled, even wireless before X starts, I haven't tried  dropping to netroot in recovery mode to see if it works there yet.

---

### Post by manzdagratiano on 2011-04-04
> **cariboo907 said:**
> With the latest updates, networking is enabled, even wireless before X starts, I haven't tried  dropping to netroot in recovery mode to see if it works there yet.

Aha! Thanks for the heads up! That seems quite awesome... maybe it is time to give network-manager another try. But good sir are there good command-line/curses tools for dealing with network-manager? I remember cnetworkmanager being awkward and dysfunctional.

---

### Post by el_koraco on 2011-04-04
> **lucazade said:**
> There is a whitelist where to enable old systray icons (notification-area) like for skype and also for wicd. Don't remeber now which is this file.. I'll look! 

i'm not currently on natty, but i think it's dconf-editor - unity - panel -whitelist. i suggest the respected op try to poke around in there.

---

### Post by manzdagratiano on 2011-04-05
> **el_koraco said:**
> i'm not currently on natty, but i think it's dconf-editor - unity - panel -whitelist. i suggest the respected op try to poke around in there.

Thank you very very much everyone! I uninstalled v86d and undid the changes in /etc/default/grub, and the plymouth crash issues as well as the crashing of X upon logging out are completely gone :) However, the framebuffer is back to crappy mode as before with the nvidia drivers installed and no uvesafb being used. I can live with that for the time being though.

Compiz and unity have not given me any further trouble so far. I have yet to try out the whitelist - that is the next item on the agenda.

Something weird that happened today was that I do not have sound anymore in Gnome through the internal audio. I had used HDMI out yesterday evening, and what I normally need to do is to detect the second display using nvidia; select Twinview, and then change the audio hardware to the HDMI out through Sound preferences. That worked just as well as before, but there is no sound in gnome upon reverting back (I did remember to change the audio hardware). If I log out of gnome and log into Blackbox, sound works without hassle, so I suspect that this is an issue with Gnome sound. I will tackle that when I get back.

---

### Post by manzdagratiano on 2011-04-05
It seems like a simple reboot fixed the gnome sound problem... Oh well... I do find it weird though when weird things happen :)

I now have both wicd and Dropbox sitting in the indicator applet. What I did was the following to tweak the whitelist, listed at:

[HTML]http://www.omgubuntu.co.uk/2011/03/how-to-hide-or-show-app-tray-applets-in-ubuntu-11-04/[/HTML]

To see what's on the whitelist:

```
$ gsettings get com.canonical.Unity.Panel systray-whitelist
['JavaEmbeddedFrame', 'Wine', 'Skype']
```

To edit this list:

```
$ gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'wicd', 'Dropbox']"
```

and we're all set!

So I guess that that presages the end of Unity trouble for me so far... Apart from a couple of crashes that have so far affected almost everybody out there, it seems to be running reasonably well! Thanks again everybody for pointing out all the subtleties!

---

