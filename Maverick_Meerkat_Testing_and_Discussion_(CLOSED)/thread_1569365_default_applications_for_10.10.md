---
title: "default applications for 10.10"
date: 2010-09-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2010-09-06
will the default applications be installed with the final release of 10.10. i have a separate home partition and noticed that parole the new replacement for totem was not installed. i had to do it manually

---

### Post by cariboo on 2010-09-06
As far as I know, totem is still the default movie player. At least it is on all 4 systems I have running up-to-date Maverick.

---

### Post by mc4man on 2010-09-06
> that parole the new replacement for totem was not installed.
If you're using xubuntu then the beta .iso has it listed (also in the amd64
[http://cdimage.ubuntu.com/xubuntu/releases/10.10/beta/xubuntu-10.10-beta-desktop-i386.manifest](http://cdimage.ubuntu.com/xubuntu/releases/10.10/beta/xubuntu-10.10-beta-desktop-i386.manifest)

---

### Post by Speed_arg on 2010-09-06
I don't get it, why not choosing VLC? I'ts 500x times better, best video player, even in windows.

---

### Post by Mr. Picklesworth on 2010-09-06
> **Speed_arg said:**
> I don't get it, why not choosing VLC? I'ts 500x times better, best video player, even in windows.

Parole, Totem, etc. use GStreamer, which is the very nice multimedia framework used across every desktop environment that isn't KDE. We like to keep everything using GStreamer, because it alone can be enhanced to do stuff like hardware video decoding (and every application that uses it will immediately benefit); configuration for video playback only needs to happen in one place; you only need to install decoders / encoders once (for it); and every format your media player understands you can expect anything else to understand, too.

Unfortunately, VLC doesn't do GStreamer. It also, as I understand it, doesn't use the same UI toolkit we prefer on every desktop other than KDE, opting for Qt now instead of GTK+. That introduces a wealth of issues. Curable issues (there's a nice Gnome UI for VLC that someone else made), but issues nonetheless.
Also, if you prefer VLC for supporting DVDs out of the box, that wouldn't be the case if it was shipped by default; we would need to split proprietary codecs and patented things into separate packages in Universe, leaving a legally pristine (and simpler) core in Main.

Not that there's anything wrong with VLC as it is, but there's a fair bit to it :)

---

### Post by kahumba on 2010-09-06
@[Mr. Picklesworth]("http://ubuntuforums.org/member.php?u=68780")
Those are all nice and noble reasons why we _should_ use totem, interestingly enough, in real world it's the other way around and people mostly prefer vlc even if using Gnome.
I think, roughly saying, it's because **people care more about the quality of the app itself** rather than how well it integrates (with Gnome) so they choose a good app (VLC) with poorer gnome integration rather than a crappy app (totem) with good integration. Not flaming, just facts.
Btw. in Ubuntu 10.10 VLC is even better yay!!

---

### Post by mc4man on 2010-09-06
> all nice and noble reasons why we _should_ use totem, blah blah

I believe he was trying to show why vlc can't be part of the default, distributed install, nothing more.
Ubuntu is not going to re-invent vlc and a plugin system for it after install just for the sake of a different 'default' player.

(all somewhat unrelated to what the Op was asking anyway

---

### Post by Longinus00 on 2010-09-06
> **kahumba said:**
> @[Mr. Picklesworth]("http://ubuntuforums.org/member.php?u=68780")
Those are all nice and noble reasons why we _should_ use totem, interestingly enough, in real world it's the other way around and people mostly prefer vlc even if using Gnome.
I think, roughly saying, it's because **people care more about the quality of the app itself** rather than how well it integrates (with Gnome) so they choose a good app (VLC) with poorer gnome integration rather than a crappy app (totem) with good integration. Not flaming, just facts.
Btw. in Ubuntu 10.10 VLC is even better yay!!

vlc has qt dependencies so including it by the default will eat LOTS of space on the iso.

---

### Post by kahumba on 2010-09-06
> **Longinus00 said:**
> vlc has qt dependencies so including it by the default will eat LOTS of space on the iso.
_**I know**_ and **I haven't even implied it should be installed by default**, I'm just saying that people like good applications and don't care about CD iso limitations or how easy it is for devs to maintain anything, they just use what's better and to many (maybe most) VLC is "better" than totem by which I'm implying that if I were Canonical I would do something about totem either rewrite it or replace it with something or write a new app cause the default video/media player is a very important issue on the desktop no matter how one prefers to look at it. It's historically typical for distros to have to cope with "such situations", noticeably, look at openoffice: it's open source etc etc so it's easy/possible to maintain but generally it's crap compared to office 2007/2010 (let's forget it doesn't run on Linux) so people would rather use the latter no matter how much the former is better from a devs point of view and from other views. You'd say it's apples and oranges  - if you read carefully - no it's not, or that the comparison has nothing to do with totem/vlc - it does in slightly broader terms of analogy. A slight hijacking of the overall thread issue was not on purpose. sorry.

---

### Post by zekopeko on 2010-09-07
> **Speed_arg said:**
> I don't get it, why not choosing VLC? I'ts 500x times better, best video player, even in windows.

VLC is one of the most horrible applications from a usability and design perspective. It's also not much better in the technical department.

I think that people that continue to recommend VLC are suffering from some type of Stockholm syndrome.

---

### Post by raghavdeepak on 2010-09-07
> **zekopeko said:**
> VLC is one of the most horrible applications from a usability and design perspective. It's also not much better in the technical department.

I think that people that continue to recommend VLC are suffering from some type of Stockholm syndrome.

Thats sounds weird!!! THOUGHT...........

---

### Post by zaphod777 on 2010-09-07
I have VLC installed but rarely use it. I like Totem better. I have never had trouble playing a video on it.

---

### Post by seeker5528 on 2010-09-09
> **zekopeko said:**
> VLC is one of the most horrible applications from a usability and design perspective. It's also not much better in the technical department.

Is that why it seems to be a permanent member of the top ten most popular projects at [freshmeat](http://freshmeat.net/)?

And I'm guessing it must not be *that* bad in the technical department since it seems the KDE folk have decided Phonon-VLC should eventually be the single supported phonon backend.

[http://amarok.kde.org/blog/archives/1171-Rapid-Progress-in-KDE-Multimedia.html](http://amarok.kde.org/blog/archives/1171-Rapid-Progress-in-KDE-Multimedia.html)

Yes, phonon-vlc is in Maverick, but I'm pretty sure it doesn't get installed/pulled in by default by any Kubuntu/KDE yet.

Later, Seeker

---

### Post by rburkartjo on 2010-09-09
just for giggles i used ubuntu tweak and set all my media files to be opened with parole media player. since they were thinking of making this the default media player in 10.10 just had to check it out

---

### Post by rburkartjo on 2010-09-10
just an update. i couldnt get parole to work until the last series of updates. seems to be fine however i have shoutcast radio stations(made a shortcut to my desktop) and cant get parole to play these. but it is fine with my music files and dvds.

---

### Post by MacUntu on 2010-09-10
> **kahumba said:**
> crappy app (totem) ... Not flaming

Yeah, obviously.

---

### Post by rburkartjo on 2010-09-12
does anyone know how to set the parole media player to play mp3 shoutcast playlist. had to change the default to vlc or movie player or xbmc. parole just wont play these or i just dont have setup right/tks

---

### Post by mc4man on 2010-09-12
> parole just wont play these or i just dont have setup right
It appears parole can't handle a .pls - you could file a bug - bottom of page
[http://goodies.xfce.org/projects/applications/parole](http://goodies.xfce.org/projects/applications/parole)

In the meantime you could open your .pls in a text editor and copy a url ([http://.](http://.)..) and give to parole thru 'open location'.
If you wanted it to open the full set - open your .pls in vlc, then Media -> 'save playlist as' and save it as a .m3u
parole can deal with it as a .m3u

---

### Post by rburkartjo on 2010-09-12
mc tks for the info will try that. tks for taking the time to respond with a fix

---

### Post by rburkartjo on 2010-09-12
tks mac that works like a charm

---

### Post by rburkartjo on 2010-09-12
mc tks again really impressed with parole light weight and works out of the box except for your fix

---

