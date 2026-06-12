---
title: "Newbie help with Banshee"
date: 2009-12-30
forum: Multimedia Software
---

### Post by Da CalebMan on 2009-12-30
Hey guys,:)

I'm using banshee now, which looks great compared to rythmbox. :popcorn:

However, I got this problem when I tried to import my songs onto my ipod shuffle, All the songs were in .ogg format, and some in .wma format, and instead of encoding the songs to mp3 like rythmbox, it imported them straight like that.

Do I have to get additional plugins for banshee to encode mp3? or Do I have to convert my entire collection to mp3?

Thanks in advance!:lolflag:

---

### Post by boombox1387 on 2010-01-09
Banshee should also transcode on the fly.  Which version of Banshee are you using?  Also, do you have all of the appropriate gstreamer plugins installed (good, bad, and ugly)?  Also, do you know what generation your iPod shuffle is?

---

### Post by Da CalebMan on 2010-01-09
I am using "Banshee 1.6 Beta 2 (1.5.1)"
I have all the required codecs (That I know of)
And my ipod is a, 2nd generation ipod shuffle 1GB.

I have used GTKpod once in the past, which left all kinds of different files on my ipod, Also Rhythmbox wouldn't import to it whatsoever, the only one that worked was gtkpod. I haven't tried any others.

~Caleb.

---

### Post by boombox1387 on 2010-01-09
Hmmm...  I'm not quite sure what to tell you except that it's supposed to work ;)  I follow Banshee's bug tracker pretty closely, and I hadn't heard reports of it not working before now.

How are you adding music to the iPod?  Is Banshee automatically moving your files, or are you manually managing the iPod?

Some things you might try:

Upgrade your Banshee to something a little newer.  1.5.2 might help, but I'd recommend using [the daily builds]("https://launchpad.net/~banshee-team/+archive/banshee-daily").  You get a lot of great features, and I've been using daily builds for months without any stability issues.  Newer versions of Banshee will let you sync your Nano with a specific playlist, which is a handy feature.

If your lucky, a newer Banshee will fix your problem.  If not, I don't know of any way to rebuild your iPod using Banshee unless you first reformat it with iTunes.  Plug it into iTunes, rebuild the database.  Plug it into Banshee, it should offer to rebuild the database again.  Maybe after that, the transcoding problem will go away.

If not, or if you want advice from people who know more than me, I'd recommend posting your question to [the Banshee mailing list]("http://old.nabble.com/Banshee-f33893.html"), or even filing a bug in [Banshee's bug tracker]("https://bugzilla.gnome.org/browse.cgi?product=banshee").  If you do that, you're almost sure to get help from a developer sooner or later.

---

### Post by Da CalebMan on 2010-01-09
Thanks Mate, I use both methods of adding files to the ipod. Auto sync, and manual. But after all the files are put on it just says: 

"Device does not support .ogg format"

I think I'll just format my ipod, rebuild it in itunes, and convert my .ogg collection into .mp3.

Anyway, Thanks a bunch! ~Caleb

---

### Post by boombox1387 on 2010-01-09
After you've rebuilt it with iTunes, it might be worth it to plug it in to your linux computer and see if Banshee offers to rebuild it correctly for you (with all the transcoding business sorted out).  Converting from one lossy format (ogg) to another lossy format (mp3) can lose audio quality pretty quickly.  Having to do that for songs on the iPod is one thing, but making your whole music library that way would be worth avoiding if you can.

Either way, good luck.  I hope it all works out well for you.

---

### Post by Da CalebMan on 2010-01-10
Hey, I think I got it!

My sister asked me to put songs on her b-grade MP3 player. The first thing I noticed was that when it automatically opens in nautilus, there's a banner near the top that says, "This device is an mp3 player" And a button that says "open in banshee" I used to get that with my ipod, but not anymore. 

Do you think there could be any connection between this and banshee? I also noticed that her mp3 player encodes them, so it's definitely not banshee.

What do you think?

(P.S I haven't formated yet. I don't have itunes so I will have to go to a friends house):popcorn:

---

### Post by boombox1387 on 2010-01-10
> **Da CalebMan said:**
> Hey, I think I got it!

Do you think there could be any connection between this and banshee? I also noticed that her mp3 player encodes them, so it's definitely not banshee.

What do you think?

(P.S I haven't formated yet. I don't have itunes so I will have to go to a friends house):popcorn:

It's more than a little possible.  You're using Banshee 1.5.1 with Ubuntu 9.10 which has a pretty major known issue with iPod connections.  Generally, Banshee 1.5.1 doesn't see iPods at all with Ubuntu 9.10.  Since you were seeing your iPod in Banshee, I assumed you were already working around this issue.

If you aren't doing anything special to get Banshee to see your iPod, then there's a good chance Banshee's seeing your iPod wrong.  Hopefully if we can get your iPod correctly recognized in Banshee, transcoding will sort itself out.  So...

For Banshee to work well with your iPod in Karmic (and any other distribution that uses devicekit-disks to mount devices), you need to either upgrade to the latest Banshee or turn off automounting.  If you want help upgrading it, I'll be glad to provide it, but in the meantime, you can turn off automounting by opening the Gnome Configuration Editor (Alt-F2, type 'gconf-editor', no quotes, press run)  In the left side, navigate to apps > nautilus > preferences.  In the main window (right side) uncheck the media_automount box.  This will keep devices from automatically mounting when you plug them into your computer.  You can manually mount them by opening them from the "Places" menu or the sidebar in the file browser.

With automounting turned off, Banshee should have no (fewer?) problems working with your iPod.  Hopefully this will take care of transcoding.

---

### Post by mangasan on 2010-01-13
Hi all.

I am having similar problems with banshee (I am using 1.6 Beta 3 - 1.5.2) after upgrading to Karmic.  

As confirmed by boombox1387 banshee does not see my ipods (1st and 5th gen) anymore. Curiously both Rythmbox and gtkpod work fine.


I have tried - unsuccessfully - to turn automounting off as suggested, so I am wandering what's wrong with banshee and Karmic... :confused:

Maybe we could raise a bug to the Banshee team.

cheers.

---

### Post by mangasan on 2010-01-13
I think it could be useful.

> 
There is a known issue with iPod not being recognized by Banshee on openSUSE 11.2 and Ubuntu Karmic.

(from [http://banshee-project.org/download/archives/1.5.2/](http://banshee-project.org/download/archives/1.5.2/) )

related bug is **#586508 "Underlying distros moving from HAL to DeviceKit breaks Podsleuths ability to mount device"**

More details at

[https://bugzilla.gnome.org/show_bug.cgi?id=586508](https://bugzilla.gnome.org/show_bug.cgi?id=586508)

HTH

---

### Post by boombox1387 on 2010-01-13
> **mangasan said:**
> Hi all.

I am having similar problems with banshee (I am using 1.6 Beta 3 - 1.5.2) after upgrading to Karmic....

Maybe we could raise a bug to the Banshee team.

cheers.

The problem:
Fedora (11, I think?), Ubuntu 9.10, and OpenSuse 11.2 all began using devicekit-disks to mount external devices.  This was a move away from HAL, which all of those distros had been using before.  HAL is deprecated, but Banshee's Podsleuth tool still depended on it for recognizing iPods.  Podsleuth didn't play well with devicekit-disks, which is why Banshee couldn't see your iPod, even though so many other Linux music players could.

The good news:

Banshee developers have known about this issue for a while (see the report that mangasan linked to), and the problem was fixed back in December.  Unfortunately, there hasn't been an official release yet that includes this fix.

The way to fix things:

The workaround I posted should be a pretty reliable way to fix things, because it keeps devicekit-disks from mounting your device, which should avoid the messy business with Podsleuth.  Which part, specifically, was unsuccessful for you?  Did you get automounting turned off?  If so, unplug your device (if it's in), (you might want to restart your session by logging out and logging back in), plug your device in, mount the device (the "Places" sidebar in Nautilus is a good way to do this), and open Banshee.   Your iPod should be there.

If that doesn't work, you can upgrade to a newer (unreleased) Banshee by adding the [Banshee Daily Builds PPA]("https://launchpad.net/~banshee-team/+archive/banshee-daily") to your software sources.

Other wise, you can wait for the next official Banshee release (which should come in about 2 weeks).

Good luck!

---

### Post by mangasan on 2010-01-13
Thanks boombox1387! Unfortunately your workaround did not work. Turning automonting off was not enough for me. Even if it keeps devicekit-disks from mounting the ipod device, banshee refuses to see it.

On the other hand I have verified the comment 27 posted on bugzilla 

[https://bugzilla.gnome.org/show_bug.cgi?id=586508#c27](https://bugzilla.gnome.org/show_bug.cgi?id=586508#c27)

is a valid temporary solution.

Glad to know about the incoming next official Banshee release. :cool:

Thanks again.

---

### Post by LuisGMarine on 2010-01-13
Glad it helped you.  I used to do that one and tried boombox and it worked for me.

---

