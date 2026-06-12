---
title: "Best Media Player?"
date: 2009-06-02
forum: Multimedia Software
---

### Post by ffixcollector on 2009-06-02
I would like to know what is the best media player out there for 9.04

I have tun Rythmbox, and:
*it wont play all types of files, I have trouble with wma, some ape, and flac.
*It get confused and plays several sound tracks at once, resulting in a complete mess.
**Interferes when I have any other program also using Gstramer resulting in each program using each others stream.

Banshee:
*Can read most all files.
*Difficult to compile playlist, it will sometimes and some of the music, none of the music, but rarely all of the music.
**It uses a TON of bandwidth. Cuts my Internet steed down +75%

Songbird:
**Excellent iPod support
*Crashes, and freezes often.
*Will not play WMA, and some FLAC
**It filters music by their tags, So I retagged all 20,000 of my song and it still will not display the title, author or album of all of my music.
*Doesn't work with my logitech multimedia keyboard. (pause, play, skip)

Amarok:
*haven't tried it. I run Gnome, so installing all the KDE dependencies just to run amarok seams like a waste, and a good way to clutter my system



So, what would be the best media player out there for what I need?
* easy to compile playlist
* does not crash, or freeze. (often)
* does not use any bandwith (unless I tell it to)
* Plays ALL types of files
* work with my logitech keyboard. (pause, play, skip)
* Good Ipod support (not the most important, since I don't own one, but my friends and family do)
I hate to say it, but the last good media player I used was Windows media player. The reason I liked it is because it just worked!

---

### Post by inspriation26 on 2009-06-02
Have you had a look at RealPlayer's linux port? It supports WMA's, MP3, and I'm not totaly sure about .ape files. Also have a look at Mplayer. It's gotten pretty good reviews in the linux world and you may have to install some plugins here and there. I think the problem you had in RHythembox was that you needed to get two packages to get it play that: gstreamer-plugins-bad and gstreamer-plugins-ugly. I know that sounds all bad and ugly but it should help you out no matter what your using as far as I know, correct me if im wrong. I hope you find what your looking for.

---

### Post by ffixcollector on 2009-06-02
I use Mplayer for video, VDPAU support is unbelievable. How do you use it for music?

---

### Post by inspriation26 on 2009-06-03
I'm not totaly sure because I dont use it. Remeber that google is your friend. I'll look around becasue that sounds interesting. Right now i'm looking into parental controls on linux because if I can get my family to go linux I'm going to need it for my yonger siblings but thats for another thread.

---

### Post by glotz on 2009-06-03
[http://mpd.wikia.com/](http://mpd.wikia.com/)

---

### Post by baneberry on 2009-06-03
You forgot to mention the worst flaw of Banshee: it's built on Mono which apes Microsoft's .Net.  I oppose Mono both ideologically and practically.  Ideologically, because if I wanted to be using Microsoft "technology", I'd use an operating system called Windows.  Practically, because in the long run, Microsoft will sue Linux distros that include Mono based apps for patent royalties, just as Microsoft recently sued Tom-Tom over a ridiculous FAT patent.  The concern is sufficient that Fedora is removing Mono.

---

### Post by alternatealias on 2009-06-03
> **baneberry said:**
> You forgot to mention the worst flaw of Banshee: it's built on Mono which apes Microsoft's .Net.  I oppose Mono both ideologically and practically.  Ideologically, because if I wanted to be using Microsoft "technology", I'd use an operating system called Windows.  Practically, because in the long run, Microsoft will sue Linux distros that include Mono based apps for patent royalties, just as Microsoft recently sued Tom-Tom over a ridiculous FAT patent.  The concern is sufficient that Fedora is removing Mono.

Stop with the FUD & trolling, it's pathetic.

You can't guarantee that Microsoft will sue over Mono, besides it'd be far more benefitial to them to sue over the hundreds of other patents they (claim to) have in OpenOffice, the Linux kernel, etc.

Also note that VFAT still hasn't been removed from the Linux kernel, even after TomTom was sued over it. Why not? Because Microsoft only cares about hardware vendors licensing their FAT patents, not software vendors.

It should also be noted that if you are so against "Microsoft technologies" then you should avoid AJAX (they invented XmlHTTPRequst as well as the HTML DOM), Firefox (because it supports AJAX but also because it implements COM which is a Microsoft technology), OpenOffice (it too has it's own implementation of COM called UNO), etc.

Just because you dislike Microsoft (and Novell by association) doesn't give you the right to badmouth projects that Novell sponsors.

---

### Post by alternatealias on 2009-06-03
> **ffixcollector said:**
> So, what would be the best media player out there for what I need?
* easy to compile playlist
* does not crash, or freeze. (often)
* does not use any bandwith (unless I tell it to)
* Plays ALL types of files
* work with my logitech keyboard. (pause, play, skip)
* Good Ipod support (not the most important, since I don't own one, but my friends and family do)
I hate to say it, but the last good media player I used was Windows media player. The reason I liked it is because it just worked!

Well, it sounds like you've pretty much tried them all (or at least all the players that are closest to matching your needs). The only thing you really have left at this point is to submit bug reports to the players you listed above so that they might fix the problems you have.

* FWIW, Banshee doesn't use ANY bandwidth for me unless I use the Last.Fm feature (which I've only used once to try it out).

---

### Post by ad_267 on 2009-06-03
I haven't had any of the issues you mention with Rhythmbox and Banshee.

Do you have the ubuntu-restricted-extras package installed to get most of the required codecs?

Also what version of Ubuntu are you using? That problem with different applications interfering sounds like an old pulseaudio problem, which I haven't had any problem with in 9.04.

---

### Post by albinootje on 2009-06-03
> **alternatealias said:**
>  You can't guarantee that Microsoft will sue over Mono

You also can't guarantee that MS won't.

And why use Mono when there's loads of other toolkits to use ?

---

### Post by 0per4t0r on 2009-06-03
[http://videolan.org/vlc/](http://videolan.org/vlc/)

best.

---

### Post by alternatealias on 2009-06-03
> **albinootje said:**
> You also can't guarantee that MS won't.

By that logic, we should all just stop using Linux because there's no guarantees that Microsoft won't sue over the 60-some-odd patents they say they have on Linux, the 60-some-odd patents they claim to have on OpenOffice, etc.

> **albinootje said:**
> And why use Mono when there's loads of other toolkits to use ?

For the same reason people would rather use Gtk+ instead of libXt as their GUI toolkit.

Mono is a more modern development platform that makes developer's lives easier. Added syntactic sugar, garbage collection, has a comprehensive base library so that you don't have to reinvent so many wheels, etc.

You can still use Gtk+ as your GUI toolkit, but subclassing widgets is a lot simpler.

---

### Post by Rogue Jedi X on 2009-06-04
Regarding playing ape, I think you may be out of luck. However, you can still convert it to your favorite lossy or lossless format after uncompressing it with JMAC [[link]]("http://jmac.sourceforge.net/").
I'd also like to point out another player I keep using when I'm on a Ubuntu machine: Exaile [[link]]("http://www.exaile.org/").

---

