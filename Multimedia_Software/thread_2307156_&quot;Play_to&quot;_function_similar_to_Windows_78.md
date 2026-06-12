---
title: "&quot;Play to&quot; function similar to Windows 7/8/10?"
date: 2015-12-22
forum: Multimedia Software
---

### Post by kaefert66014235 on 2015-12-22
User mehepsk asked this question in 2010 here:
[http://ubuntuforums.org/showthread.php?t=1491399](http://ubuntuforums.org/showthread.php?t=1491399)

but since the answers from back then are not really satisfactory, I thought let's make a new thread 5 years later and see if there is some new/easier/more transparent way to get a functionality similar to what Microsoft has since Windows 7.

Short simple feature explanation:
Right click on any media file in Nautilus (or any file browser) and select "play to" and get a list of DLNA-renderers in your network. This file must then be served from a DLNA-server and the DLNA-renderer selected must then be instructed to play it using the DLNA-controller standard.

I guess the most awesome implementation would be if this would be a CLI utility that can simply be passed a filepath (of the media file) and some name/id of the target DLNA-renderer.

Does something like that exist? Or does someone maybe have enough experience with existing Linux DLNA software and can draw a path how this could be achieved using existing libraries?

---

### Post by blm-ubunet on 2015-12-26
If anything the situation is worse (excluding android).

The coherence python plugin for nautilus & coherence plugin for rhythmbox are no more.
Luckily gmediarender lives on (& better) in gmrender-resurrect.
Apart from smart TVs, gmediarender & kodi are the few potential DMRs.

The most flexible solution is something like BubbleUpnp control point running on android & using modern TV as media renderer.

upnp-inspector still works as media controller, can have server content browsing & renderer control windows open at same time or can use gunp-av-cp.

---

### Post by kaefert66014235 on 2015-12-26
hmm. okey. well I know and use BubbleUpnp, it's a very useful app.
I do have quite some gimmicks that have implemented the DLNA-renderer profile, and I have BubbleUpnp on Android to make them play stuff and in Windows I have a simple "play to" in the Windows Explorer context menu.

On the Linux desktop, this feature is annoyingly complex to acquire.
What I usually do is create an adhoc minidlna-server pointing to the folder of interest from which I want to play media and then use BubbleUpnp on my phone to make my entertainment equipment play the media files I want.

upnp-inspector is feature rich, but it's UI does not seem to be optimized for that sort of usage.. It's much easier to use my phone (BubbleUpnp) as DLNA-controller.

---

### Post by blm-ubunet on 2015-12-26
Push rendering to a DMR seems to be feature misunderstood by most or they are completely ignorant of the concept. I think most people just use the built-in browser UI on the client. If the client device is a PC then that's not so bad.

Sadly MythTV only has (or had) this DMR feature for Airplay & was regularly broken by f/w updates.
AFAIK kodi & Rygel (uses obsolete gmediarender) are the only other FOSS DMRs.
[https://wiki.gnome.org/Projects/Rygel](https://wiki.gnome.org/Projects/Rygel)

Gadgets:
IMO The consumer electronics manufacturers have used DLNA "interoperability" for vendor lock-in.
Airplay probably works fantastically well in their ecosystem.
IIUC you can push the audio & video to different renderers (including locally).
BubbleUPnP can do this ? The free version as well?

A Unity lens for DLNA/UPnP (does not exist?) could integrate with desktop?
UbuntuTV project usecases makes an interesting read..
[https://wiki.ubuntu.com/UbuntuTV/UseCases](https://wiki.ubuntu.com/UbuntuTV/UseCases)

upnp-inspector looks to be a proof of concept/ demonstration app for all possible functionality.
Not so easy to use.

---

### Post by kaefert66014235 on 2015-12-27
Hmm, well, I have quite a few devices that implement the the DLNA-renderer profile in my network:
-) Pioneer VSX-924
-) Western Digital TV Live Streaming Media Player (Gen 3)
-) Mede8er 600X3D
-) Xtreamer SideWinder 3

Since I have found those hardware media players, I have given up on home cinema PCs because those are more expensive and more work to setup and maintain.

Therefore my interest in FOSS (or any) software that implements the DLNA DMR role is quite low.

What I am looking for is software that unites both the other roles (DMS & DMC) and makes any DMR device of the users choosing play a certain media file that is not already hosted by an existing DMS but exists locally on the users Linux-PC.

For Windows this feature is integrated into the File-Explorer ("play to" in media files context menu) and for Android the App BubbleUPNP has that feature. For the Linux desktop, there (still) does not seem to be an equivalent.

---
About your question / comment about pushing audio & video to different renderers:
No I don't think that BubbleUPNP can do this, and I haven't seen any DLNA-controller that can do that sort of thing. And if there was one that can do it, I think you would always have sync issues since as least in my experience there always seems to be quite high latencies when using DLNA.

---

### Post by blm-ubunet on 2016-01-06
Airplay does allow rendering audio & video on different DMRs but it's not UPnP/DLNA.

I have "Play to DMR" working in nautilus on Ubuntu 14.04. The DMR used for testing is gmedia-render(resurrect).
This link has partial working instructions.
[http://askubuntu.com/questions/624814/how-to-make-a-nautilus-context-menu-script-to-play-media-files-in-local-lcd-tv](http://askubuntu.com/questions/624814/how-to-make-a-nautilus-context-menu-script-to-play-media-files-in-local-lcd-tv)
Install python-nautilus, this has (3) components one of which is "play-on".
Have to use the replacement python plugin script from the above link.
The other (2) components prob. need similar modifications.

The coherence project seems unmaintained & old so I installed later "python-coherence" from github.
May not be necessary but I used "cohen" fork from github as a replacement for coherence.
So need to change a few config files to reflect correct install path & filename.

The installed python "twisted" networking library has bad bug that stops UPnP functioning correctly.
sudo pip install --upgrade twisted
Might need to first install "pip".

---

