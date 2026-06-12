---
title: "KDE 4.5 beta (Meerkat and Lucid) Impressions"
date: 2010-06-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by PGHammer on 2010-06-06
While Kubuntu Maverick Meerkat is going to be largely designed *around* the forthcoming KDE 4.5, it's the backport to Lucid Lynx that is showing just what it can really do; however, that is entirely because unlike MM, Lucid has graphical acceleration for hardware that can use it (via either FOSS or proprietary drivers).  My biggest issue with previous dealings with the beta is that I had to deal with a decided lack of graphical giddyup (the plasma workspace seems *heavier* than that of earlier versions of KDE; likely because a lot more is asked of it).  Also, comparing the Lucid backport to the extant backport for openSuSE 11.2 (also a released distribution), Team Kubuntu is much further along (considering that I came to the Lucid backport directly from a crashed-and-roasted oS 11.2 attempt that left me without a GUI at all, while I have a single problematical red X where the showdesktop widget should be in the notification area (meanwhile, five widgets are in the workspace; three to the left and two to the right of the central Firefox) as the only sore spot!).  Those of you that can should seriously consider adding the KDE 4.5 PPA to your Lynx' diet; not just your Meerkat's.

---

### Post by screaminj3sus on 2010-06-06
What vid card/driver are you using? I've tried KDE4 - 4.4 and I always end up going back to gnome because on my ati card (mobility 2600) - using foss or fglrx its REALLY REALLY REALLY slow compared to gnome. The whole desktop feels ridiculously sluggish.

---

### Post by xebian on 2010-06-06
> **screaminj3sus said:**
> What vid card/driver are you using? I've tried KDE4 - 4.4 and I always end up going back to gnome because on my ati card (mobility 2600) - using foss or fglrx its REALLY REALLY REALLY slow compared to gnome. The whole desktop feels ridiculously sluggish.

No problem here..Turion X1 1.6GHZ Ati xpress 200M pretty old (5yrs+).  The FOSS radeon works pretty well including KDE composting.  Could not get the fglrx to run though I know it did once (hardy?) but the radeon is working quite well so why bother.

---

### Post by PGHammer on 2010-06-06
> **screaminj3sus said:**
> What vid card/driver are you using? I've tried KDE4 - 4.4 and I always end up going back to gnome because on my ati card (mobility 2600) - using foss or fglrx its REALLY REALLY REALLY slow compared to gnome. The whole desktop feels ridiculously sluggish.

Check the system settings - if you have it set for High Resolution and High CPU Settings (as I do), due to the beta nature, it will feel *really* sluggish (with either Kwin *or* compiz, though with Kwin it is more noticeable).  I have the HD5450 (512 MB Visiontek fanless) with a Celly DC E1200; and I haven't really played with the performance settings yet.  I haven't tried the lower-CPU/high resolution (since I run my desktop at 1920x1080, that would be considered *high*) options.

Also, comparing it to the established (some would actually say *staid*) GNOME, considering it's a beta, is really unfair; if anything, compare it to GNOME-Shell (which is supposed to be ahead of KDE 4.5), which feels even *more* sluggish.

---

### Post by _khAttAm_ on 2010-06-07
KDE reminds me of great looks, awesome plasmoids and Desktop Effects well integrated to the UI. But unfortunately, it also reminds me of heavy resource usage, frequent disk-writes and awful look of gtk apps (when I have to use one and I know I will have to use one, while I can avoid KDE apps and find similar GTK apps), lack of good package manager like Synaptic.

BTW, whats in place as an Empathy alternative on Kubuntu Maverick? Does it support what Empathy already does? Will it be developed along Empathy? coz I think Empathy is ahead of it...
Has KNetworkManager improved? Does it have proper support for PPPoE?
Is there some non-superkaramba system monitoring plasmoid?

I think it is a difficult switch for a Gnome user, and I think I should stay with Gnome for now.... what do you people think?

---

### Post by krazyd on 2010-06-07
> **_khAttAm_ said:**
> BTW, whats in place as an Empathy alternative on Kubuntu Maverick? Does it support what Empathy already does? Will it be developed along Empathy? coz I think Empathy is ahead of it...
That would be Kopete.

> **_khAttAm_ said:**
> Is there some non-superkaramba system monitoring plasmoid?
Yes, there are several.

> **_khAttAm_ said:**
> I think it is a difficult switch for a Gnome user, and I think I should stay with Gnome for now.... what do you people think?

I would not make my first move from Gnome onto an alpha release of Kubuntu. Bugs in the distro will probably give you a negative view of KDE!

Try Lucid if you want KDE, or wait until Maverick is released.

---

### Post by _khAttAm_ on 2010-06-07
> **krazyd said:**
> That would be Kopete.
Let me reframe the question? Does it live upto an Empathy user's expectation? I mean how is it heading?


> **krazyd said:**
> Yes, there are several.Last time I used KDE, I had to depend on Superkaramba for System Monitoring and it does not look so integrated with rest of KDE...
Others had something missing.. I want multicore usage/temperature, HDD temperature, top processes (highest MEM and Highest CPU), overall memory and swap usage, I/O disqueue, Network Monitor graph + total data transferred, partition space usage.. are all these available via plasmoids... I am not much into coding plasmoids.. so I'd like them available or easily installable..



> **krazyd said:**
> I would not make my first move from Gnome onto an alpha release of Kubuntu. Bugs in the distro will probably give you a negative view of KDE!

Try Lucid if you want KDE, or wait until Maverick is released.


Thank you.. I'll take that into consideration..

---

### Post by krazyd on 2010-06-08
> **_khAttAm_ said:**
> Let me reframe the question? Does it live upto an Empathy user's expectation? I mean how is it heading?
I haven't used it in a while, but last time I did it was fine.. multiple networks etc. Haven't used Empathy so can't really comment.


> **_khAttAm_ said:**
> Last time I used KDE, I had to depend on Superkaramba for System Monitoring and it does not look so integrated with rest of KDE...
Others had something missing.. I want multicore usage/temperature, HDD temperature, top processes (highest MEM and Highest CPU), overall memory and swap usage, I/O disqueue, Network Monitor graph + total data transferred, partition space usage.. are all these available via plasmoids... I am not much into coding plasmoids.. so I'd like them available or easily installable..

yasp-scripted or stdin plasmoid - both available on kde-look.org look like they'd fill your needs. 

the default monitoring plasmoids are really quite good though :)

---

### Post by _khAttAm_ on 2010-06-10
> **krazyd said:**
> yasp-scripted or stdin plasmoid - both available on kde-look.org look like they'd fill your needs. 

the default monitoring plasmoids are really quite good though :)

Thank you very much. I will try kubuntu-desktop shortly.

---

### Post by _khAttAm_ on 2010-06-10
**EDIT:** Don't bother.. this one has been fixed now and I can install kubuntu-desktop

I see Kubuntu Beta PPA has no entry for Maverick, only for Lucid (I tried this: [https://launchpad.net/~kubuntu-ppa/+archive/beta](https://launchpad.net/~kubuntu-ppa/+archive/beta) ). Is there another PPA for Maverick?

and by 4.5 beta, do you mean one with kdebase 4:4.4.85-0ubuntu1?

In my repos, I have 4.4.80, but when I try to select kubuntu-desktop, I get the following error:
```


kubuntu-desktop:
 Depends: ark but it is not going to be installed
 Depends: dolphin but it is not going to be installed
 Depends: kde-window-manager but it is not going to be installed
 Depends: kdebase-workspace-bin but it is not going to be installed
 Depends: kdemultimedia-kio-plugins but it is not going to be installed
 Depends: kdepasswd but it is not going to be installed
 Depends: kdm but it is not going to be installed
 Depends: khelpcenter4 but it is not going to be installed
 Depends: klipper but it is not going to be installed
 Depends: kmix but it is not going to be installed
 Depends: konsole but it is not going to be installed
 Depends: ksnapshot but it is not going to be installed
 Depends: ksysguard but it is not going to be installed
 Depends: ksystemlog but it is not going to be installed
 Depends: language-selector-qt but it is not going to be installed
 Depends: okular but it is not going to be installed
 Depends: plasma-desktop but it is not going to be installed
 Depends: software-properties-kde but it is not going to be installed
 Depends: systemsettings but it is not going to be installed
 Recommends: akregator but it is not going to be installed
 Recommends: amarok but it is not going to be installed
 Recommends: apport-kde but it is not going to be installed
 Recommends: apturl-kde but it is not going to be installed
 Recommends: dragonplayer but it is not going to be installed
 Recommends: gwenview but it is not going to be installed
 Recommends: install-package but it is not going to be installed
 Recommends: jockey-kde but it is not going to be installed
 Recommends: k3b but it is not going to be installed
 Recommends: kaddressbook but it is not going to be installed
 Recommends: kate but it is not going to be installed
 Recommends: kbluetooth but it is not going to be installed
 Recommends: kcalc but it is not going to be installed
 Recommends: kdepim-kresources but it is not going to be installed
 Recommends: kdepim-runtime but it is not going to be installed
 Recommends: kdepim-strigi-plugins but it is not going to be installed
 Recommends: kdepim-wizards but it is not going to be installed
 Recommends: kdesudo but it is not going to be installed
 Recommends: kmag but it is not going to be installed
 Recommends: kmail but it is not going to be installed
 Recommends: kmousetool but it is not going to be installed
 Recommends: knotes but it is not going to be installed
 Recommends: kontact but it is not going to be installed
 Recommends: kopete but it is not going to be installed
 Recommends: korganizer but it is not going to be installed
 Recommends: kpackagekit but it is not going to be installed
 Recommends: kppp but it is not going to be installed
 Recommends: ktorrent but it is not going to be installed
 Recommends: kubuntu-firefox-installer but it is not going to be installed
 Recommends: kubuntu-konqueror-shortcuts but it is not going to be installed
 Recommends: kubuntu-notification-helper but it is not going to be installed
 Recommends: kvkbd but it is not going to be installed
 Recommends: kwalletmanager but it is not going to be installed
 Recommends: network-manager-kde but it is not going to be installed
 Recommends: openoffice.org-kde but it is not going to be installed
 Recommends: plasma-widget-facebook but it is not going to be installed
 Recommends: plasma-widget-folderview but it is not going to be installed
 Recommends: plasma-widget-kimpanel but it is not going to be installed
 Recommends: plasma-widget-kubuntu-feedback but it is not going to be installed
 Recommends: plasma-widget-message-indicator but it is not going to be installed
 Recommends: plasma-widget-quickaccess but it is not going to be installed
 Recommends: printer-applet but it is not going to be installed
 Recommends: quassel but it is not going to be installed
 Recommends: system-config-printer-kde but it is not going to be installed
 Recommends: usb-creator-kde but it is not going to be installed
 Recommends: userconfig but it is not going to be installed

```

when I tracked down ark, I got to libplasma:
```

libplasma3:
 Depends: libkdewebkit5 but it is not going to be installed
  Depends: libqt4-webkit (>=4:4.7.0~beta1+git20100522) but 4:4.7~beta1+git20100522-0ubuntu2 is to be installed
```

seems like some problem with this package. Should I file a bug? or something wrong on my side?

FYI, 
I have reloaded to get the latest package info, and was successful at that.. 
I am using main server for repos...
I am not using any external PPA for libqt4-webkit

any input will be appreciated.

---

### Post by eumel on 2010-06-10
got the same problem here. can't upgrade kde libs caused by libqt4-webkit 4.7.

but libqt4-webkit is installed in version 4.7

* libkdewebkit5 hängt ab von libqt4-webkit (>= 4:4.7.0~beta1+git20100522) [NICHT VERFÜGBAR]  



libqt4-webkit ist zurzeit installiert.                                                                                                                                                                                                       &#9618;
                                                                                                                                                                                                                                             &#9618;
                                                                                                                                                                                                                                             &#9618;
Die folgenden Pakete hängen von einer anderen Version von libqt4-webkit als der momentan installierten Version von 4:4.7~beta1+git20100522-0ubuntu2 ab:                                                                                      &#9618;
                                                                                                                                                                                                                                             &#9618;
                                                                                                                                                                                                                                             &#9618;
  * libkdewebkit5 hängt ab von libqt4-webkit (>= 4:4.7.0~beta1+git20100522) [NICHT VERFÜGBAR]                                                                                                                                                &#9618;
  * libplasma3 hängt ab von libqt4-webkit (>= 4:4.7.0~beta1+git20100522) [NICHT VERFÜGBAR]            




i think its the "-0ubuntu2" at the end of the library that does not match the dependency of the new updated packages.

greetz eumel

---

### Post by descendent87 on 2010-06-10
Just wait, they're currently updating KDE to beta 2 so until all the updates are in there's going to be loads of dependency problems. Should hopefully be sorted today

---

### Post by eumel on 2010-06-10
> **descendent87 said:**
> Just wait, they're currently updating KDE to beta 2 so until all the updates are in there's going to be loads of dependency problems. Should hopefully be sorted today

yeah, that's nice. it seems that the german mirror (de.archive.ubuntu.com) is behind archive.ubuntu.com. i switched that in my sources.list and updating seems possible :-)

---

### Post by descendent87 on 2010-06-10
I'm using the gb mirror and all the KDE updates seem to be done, updating at the moment

---

### Post by Aries K on 2010-06-11
> **_khAttAm_ said:**
> KDE reminds me of great looks, awesome plasmoids and Desktop Effects well integrated to the UI. But unfortunately, it also reminds me of heavy resource usage, frequent disk-writes and awful look of gtk apps (when I have to use one and I know I will have to use one, while I can avoid KDE apps and find similar GTK apps), lack of good package manager like Synaptic.

BTW, whats in place as an Empathy alternative on Kubuntu Maverick? Does it support what Empathy already does? Will it be developed along Empathy? coz I think Empathy is ahead of it...
Has KNetworkManager improved? Does it have proper support for PPPoE?
Is there some non-superkaramba system monitoring plasmoid?

I think it is a difficult switch for a Gnome user, and I think I should stay with Gnome for now.... what do you people think?

Kopete is miles ahead of any multi-protocol messenger available in Gnome. It supports webcam for Yahoo, file transfers for most protocols, huge plugin support with a wide array of plugins available, custom message styles with a gui that can download them straight from Kde-look.org, meta contacts, Yahoo and MSN buzz support, the list goes on... Kopete does fine on it's own and does not need to be developed along with anything. I do not even think Empathy has file transfers for anything outside of XMPP although it does have voice and video (but once again only for XMPP which most people unfortunatly do not use). Empathy used to support MSN voice and video but since Microsoft changed their protocols that pretty much slowed that down so do not expect that anytime soon from any Linux instant messenger. I will say Empathy is a step in the right direction for Gnome instant-messaging especially compared to things like Pidgin. I hope to see file transfer support for most protocols and webcam support for Yahoo someday on Empathy especially since Yahoo seems to be the most popular for webcams around the world. I do understand that it is hard to reverse-engineer an I-M protocol so these things are completely understandable.

As for speed on KDE, I do not have a problem with speed. I just have a basic 1.8ghz Intel Dual Core (not even a Core Duo) and it hums along just fine. Kwin renders the 3d cube more crisply than Compiz plus it is available without installing/configuring anything else granted  you have the proper 3d hardware and drivers installed. No problems here with "frequent disk writes", everything here is going nice and smoothly. The preview video/pictures panel in Dolphin operates similar to Apple's preview feature, very nice and modern. I switched to KDE since I always caught myself adding things to Gnome to suit my needs such as Screenlets thus making it slugish vs KDE has everything I need out of the box so no need to add anything along with the fact that I did not like where Gnome Shell was going (I am not a fan of the "Netbook" or  "Cloud Computing" way of doing things). Do not know why everyone says Kubuntu does  not have good package management. I never had a problem with Kpackagekit, to me it is a nice simple package manager that works nothing more nothing less. It has always managed dependencies well for me, can't speak for other's experiences though. :confused: This along with terminal worked great my application management/installations. Thanks to QtCurve GTK apps actually look pretty nice in KDE, that is something of the past people keep bringing up without even trying KDE 4 since it's early stages. After testing KDE 4 you might actually like some of the KDE 4 apps like Kdenlive which is a far more usable and easy to use video editor than Pitivii, even some hardcore Gnome users install it since nothing else in Linux comes closer to Windows Live Movie Maker/ I-Movie. Kamoso, a webcam app like Cheese has features where you can upload your video straight to places such as YouTube. Multimedia applications such as Amarok, K3B, Kaffine are also solid. KDE also seems to handle multimedia quite nicely, it has a control panel to manage file types etc. which Gnome lacks.

I cannot answer the Knetwork/PPPoE question since I do not use PPPoE.

Is the switch from Gnome difficult? Maybe so maybe not. All I can say is it depends what you prefer. I wanted a DE with widgets out the gate, a rich multi-media experience, good integration, beautiful looks, and a decent multi-protocol messenger with decent support around most protocols and Yahoo webcam support. Your needs maybe completely different from mine where you might something a little scaled down like Gnome. Keep in mind Gnome is making advancements as well and is not the lean DE it used to be so something like LXDE or XFCE might be for you. I guess what it all boils down to is apps, yes you can install KDE apps in Gnome or vice versa but there is nothing like natural integration. I can honestly say if Gnome had a better video editor and Empathy got Yahoo webcam support and file transfers in most major protocols I would definitely give it a fair shot. Anyways hope this helps.

My [[IMG]http://www.smileyvault.com/albums/signs/smiley-vault-signs-007.gif[/IMG]](http://www.smileyvault.com/).

---

### Post by cespinal on 2010-06-19
So I have been reading about the new 4.5 beta2...I quite compelled to get it but you know... it is a beta release so...can I get some feedback about general usability? Im currently running the previous version and I'm generally pleased.

---

### Post by Reiger on 2010-06-19
There's the odd bump in the road*, but for me the Plasma crashes (a part of early look alpha/beta packages) have gone. 

* KDM is not installed correctly, you must manually change ownership of /var/lib/kdm e.g.: chown kdm:kdm -R /var/lib/kdm
* For some reason I can't get Plasma to remember that I want it to display a slideshow...
* KDM session/leave buttons don't work on left-click, for some reason they now require a middle mouse button... there is a bugreport for that in the KDE bug tracker
...

---

### Post by cespinal on 2010-06-19
Thanks for your insight... it seems im staying out until August :P...

---

### Post by caryb on 2010-06-20
Is it my hardware or is sound pooched in Maverick Kubuntu atm?

Thanks Cary

---

### Post by reub2000 on 2010-06-21
I'm enjoying the accelerated effects with nouveau. Some of the kwin effects like wobbly windows or cover switch won't work with the foss driver, but things I consider important like shadows and transparency work fine. I've experienced a frequent crashes in plasma, but hopefully that will get sorted out by the time of the final release.

---

### Post by koso on 2010-06-21
Anyone testing KDE 4.5 with intel graphics card? (GMA 965, X3100). A am having problems with graphics. After xorg updates, I am not able to start kwin with OpenGL support, it fails to Xrender, which is very slow ...

---

### Post by jaxxed on 2010-08-30
It's not easy to find reports on it, but apparantly the compositing for kdewin using certain drivers (Intel and FOSS Radeon) is disabled.  You used to be able to bypass (bypass func. checks checbox) but now that doesn't get you anywhere.

I've heard rumours of a fix for this coming, but I'm not holding my breath.  I miss my desktop effects though.

I was using LL with the beta kde repo to get 4.5, and the edgers radeon/mesa drivers, an I thought that maybe I was pushing LL too far.  I've since switched to MM hoping to find things fixed, but no such luck.  It's nice to be back in Beta land though.

J

---

### Post by x-shaney-x on 2010-08-30
Well so far the future of linux isn't looking so good for me and maybe other intel users.
I have tried kde 4.5 on a mint install upgraded via backports then upgraded to maverick - non-stop problems.
kubuntu maverick - non-stop problems.
PCLinuxOS - desktop effects wouldn't enable at all.
OpenSUSE - effects wouldn't enable there either.

I switched to KDE recently because I don't like the way gnome is heading and unity also has intel issues.

I only got my comp a couple of months ago and went for intel specifically because I was sick of the hassle of getting nvidia prop drivers.

---

### Post by buzzmandt on 2010-08-30
I think it's a matter of patience. i have an intel video laptop and have been running kde 4.x since 4.3 and it hasn't been a problem.  I do have some issues with maverick/kde/kwin but have no problem with lucid/kde4.5 backport.  I'm guessing it's either kernel or the new xorg. I'm severely hoping it gets squared away cause kde is the future for my pc experience and hoping it stays that way :)

---

