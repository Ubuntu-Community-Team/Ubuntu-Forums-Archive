---
title: "Miro Bandwidth Limit not limiting"
date: 2010-08-13
forum: Multimedia Software
---

### Post by mdgill on 2010-08-13
Hello Miro Users :)

When I try to limit the download bandwidth in Miro, the download bandwidth is not limited.

I want to trickle my torrents at 5KB/s because I am on hotel wifi.  So, I go to Video --> Preferences --> Downloads, set "Limit downstream bandwidth to" 5 KB/s and I check the box.  Unfortunately, this doesn't seem to limit the downloads because the Downloads screen indicates > "100 kb/s downloading".  Even if the capitalization is correct and I am limiting to 5 kiloBytes per second, it is still downloading faster than 40 kilobits per second.

Sorry for the idiot's explanation, but I first want to see if I am the problem and maybe I need an idiot's solution.

---

### Post by KlinerDraken on 2010-10-19
I am seeing this issue also, I have set the limit anywhere from 200KB/s to 0.01 KB/s and it keeps downloading up to 1000 kb/s.

Is there a fix for this because it sometimes makes my computer slow down when there is a lot of data downloading in miro.

Miro 3.0.3 (51067950)
Ubuntu 10.10

---

### Post by NothingToSeeHere on 2011-02-16
I am using Miro 3.5.1 and this still does not work as expected. It it always frustrating when basic functionality is not tested at all and problems like these exist for ages. I mean, does any of the developers use Miro themselves? How can you provide such an option and not test it at all? It's really frustrating, cause I have a lot of those bugs it a lot of software. Some smaller, some really annoying.

I will try to find a solution.

EDIT:
There already is a bugreport on their system at [http://bugzilla.pculture.org/show_bug.cgi?id=12619]("http://bugzilla.pculture.org/show_bug.cgi?id=12619")

The problem here is, that the Preferences menu is badly designed. Notice that the fields to limit upload and download bandwidth are under a label named "BitTorrent:". This means that these limits only have something to do with limiting the BitTorrent bandwith.
So I thought that miro uses the BitTorrent protocol to make the downloads and I could limit the bandwidth with these options. But: I seems that miro does not do that, but instead performs the "normal" downloads "traditionally", but also has a bittorrent client built in (which seems
to be mandatory for about every software nowadays, cause I stumbled across a lot of tools which also offer download via bittorrent).

The problem here which is probably creating confusion (hence why I call it "bad design") is the following:
  1. There is NO possibility to limit bandwidth on those normal downloads. This results in the wrong assumption of users that the fields under "BitTorrent:" are used to limit all downloading, because these are the only "limit bandwidth" fields and they are under "Downloads" and why would a software offer limiting options for one form of download only, but use a different type of download without limiting capabilities for most stuff, right?
  2. The BitTorrent options are displayed on the "Download" tab in the Preferences tab", although most options do have nothing to do with Downloading at all.

So, I would say they should either create a new tab "BitTorrent" and put the options their, so that people who look under "Download" don't get confused or they should have too areas under "Downloads", one for "Normal Downloads" and one for "BitTorrent", so that people realize that features like limiting bandwidth are not implemented yet for downloads, but only for bittorrent downloads.

I find this very confusing, especially because most people will look under "Downloads", find an "limit download bandwidth" option as expected and ingore the "BitTorrent:" label, because who the hell knows which protocol or technology they use for downloading anyway. Right now it gives the impression that probably everything is BitTorrent based. 

But hey, at least we have clarity now.

---

