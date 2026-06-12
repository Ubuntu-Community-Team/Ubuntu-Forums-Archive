---
title: "GUI RDP client in repos (not reminna)?"
date: 2012-11-27
forum: Networking &amp; Wireless
---

### Post by anonymousdog on 2012-11-27
It looks like KRDC isn't awful, but I'm really disappointed with Remmina (after trying to work with it since April), and I'm equally disappointed that tsclient is unsupported.  Remmina couldn't be more buggy with weird placement bugs, window sizing issues, random disconnects (with no attempt to reconnect), and random keyboard non-responsiveness (which also requires reconnect or worse); it's gotten to the point that, in my trying to accommodate it, I find myself becoming uncomfortably angry.  So, it's time to ditch remmina.

Vinagre almost looks attractive except that it is also plagued with the worst of Remmina's problems: random disconnects and keyboard issues (on all my boxes whether fresh installs or upgrades, multiple monitors or single, all MB with xfce4 [no Unity, Gnome or KDE]).

I know tsclient hadn't been actively developed for a few years, but you know the nice thing about it?  It worked!  It had zero (significant) bugs that I ever encountered in years of use across multiple distros.  Maintainers, **_please_** reconsider bringing tsclient back into the fold (even though it's not maintained).

So, does anyone know of a stable, basic GUI RDP/RDC client that is relatively free of bugs?  I don't care a thing for tricks with sound, SSH tunneling right in the app, or advanced RDC features associated with RDC Proxy services and such fanciness.  I just need a stable remote connection to Windows boxes; I can create my own ssh tunnels, thanks.  It doesn't even need to support VNC.

I've tried neither gnome-rdp nor grdesktop because both would require a number of supporting libraries on my MB boxes (12.04 x68_64, all of them).  I'll do it if they are worth the gnome kruft, but I'd prefer something without dependencies not installed with MB.

I have VERY briefly dabbled with KRDC which looks pretty good but doesn't insinuate itself in the xfce4 menus (which is minor and can be fixed but would be nice).  I can do plain rdesktop, but I DO like tabbed GUIs that help organize many, concurrent remote sessions.

Any suggestions (in the repos)?

---

### Post by ZippyUbu on 2012-11-27
Hi,

I feel your pain with Remmina. I constantly get random disconnects and keyboard freezes.  The original TsClient was awesome and worked well across all platforms. Looking through Launchpad there are lots of bugs listed. I too would be interested in another GUI solution...

--Zu

---

### Post by PhilGil on 2012-11-27
@[anonymousdog]("http://ubuntuforums.org/member.php?u=631994")

I agree with you, the newest versions of Remmina are a mess. It's a shame as it showed so much promise when the project first began.

I've given up on GUI RDP clients for now and am just using rdesktop. Made a launcher with the proper command - now I just click on it and I'm in business. It's not as convenient as a GUI if you're managing multiple sessions, put it's fine for my use.

---

