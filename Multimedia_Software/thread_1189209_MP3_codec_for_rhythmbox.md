---
title: "MP3 codec for rhythmbox?"
date: 2009-06-16
forum: Multimedia Software
---

### Post by BrynC on 2009-06-16
I'm guessing this has probably been discussed a lot, but what with my having switched my laptop from Vista to Ubuntu (running Jaunty), the sheer effort required to convert all my music from mp3/wma to .ogg or similar, so I was wondering where would be best to nab m'self an mp3 codec for Rhythmbox.
Cheers in advance
Bryn

---

### Post by pytheas22 on 2009-06-16
The easiest way to install mp3 support is to try to open an mp3 file with Movie Player (if that's not the default application for handling .mp3s, you can right-click on the file and select 'Open With...' and choose Movie Player).  Movie Player should automatically prompt you to install mp3 support, provided you are connected to the Internet.  mp3 support is system-wide, so installing it for Movie Player will also make mp3s work in Rhythmbox.

If for some reason this doesn't work, let us know and we can install the mp3 package manually.

---

### Post by murray92 on 2009-06-16
If you plan on using mp3s and a lot of other things you need to install the [Restricted Formats Codecs]("https://help.ubuntu.com/community/RestrictedFormats/"). I'm not sure whether or not Rhythmbox needs an extra codec after that, but restricted formats are one of the first things to get after installing ubuntu

---

### Post by BrynC on 2009-06-16
Cheers, gentlemen, I think you may have sorted my issue in part.

Still won't open in rhythmbox though.

---

### Post by Dragonbite on 2009-06-16
[LIST=1]
[*]Download the free MP3 coded from [Fluendo]("http://www.fluendo.com/")
[*]Unzip it and read the installation file. It tells you how to set it just for the user or system-wide. I've done this with each installation and it works just fine.
[/LIST]

Good thing about Fluendo, is its legal in the US too.

---

### Post by BrynC on 2009-06-16
> **Dragonbite said:**
> 
[LIST=1]
[*]Download the free MP3 coded from [Fluendo]("http://www.fluendo.com/")
[*]Unzip it and read the installation file. It tells you how to set it just for the user or system-wide. I've done this with each installation and it works just fine.
[/LIST]

Good thing about Fluendo, is its legal in the US too.

I'm in the UK, not the US, so legality may be a question, but meh, I'll give it a go.

---

### Post by Dragonbite on 2009-06-16
> **BrynC said:**
> I'm in the UK, not the US, so legality may be a question, but meh, I'll give it a go.

I think they are similar on this account.  Also, I think Fluendo is in the UK, but I'm not certain.

---

### Post by BrynC on 2009-06-17
> **Dragonbite said:**
> I think they are similar on this account.  Also, I think Fluendo is in the UK, but I'm not certain.

I'll give it a go when I get home, provided I can haul the ethernet out of the other PC, because my wireless is epic awful

---

### Post by Dragonbite on 2009-06-17
An advantage to downloading Fluendo MP3 from the Fluendo site is that I go through the same procedures and get this to work regardless of the distribution.  I've added it to Ubuntu, Fedora, CentOS and more.

Otherwise, Canonical store also sells the Fluendo media packs specifically for Ubuntu.  Not sure how portable they are, though.

---

### Post by zen.lee on 2009-10-01
i cant palay mp3

---

### Post by kghavami on 2009-10-01
I do too.

---

### Post by Dragonbite on 2009-10-01
> **zen.lee said:**
> i cant palay mp3

Have you tried any of the methods listed in this thread (Restricted formats, Fluendo, Totem, etc.?)

> **kghavami said:**
> I do too.

Does that mean you cannot play MP3s too?

---

### Post by niite on 2009-10-10
man, i'm about to pull my freakin teeth out..  this is my first time with ubuntu, switched from opensuse, and i gotta be honest when i say, things weren't so hard with opensuse..  i'm stuggling with my video card, had to do a work around for audio..  i've downloaded the mozilla 3.5 package and installed it, but my browser still shows the older version.. and now, freakin mp3's won't play.  I've installed the restricted package, ffmpeg, gstreamer unfiltered, etc..  and now fluendo and it still don't work.  so wtf!!!

someone please give me some advice..  i'm inlcined just to go back over to opensuse, but i really want to give ubuntu a shot.

-j

---

### Post by pytheas22 on 2009-10-11
niite: so you're sure you installed the ubuntu-restricted-extras package?  And you restarted your media applications (or the entire system) after installing the package in order for changes to take effect?  Have you tried playing a variety of different mp3s, or only one or two?  Can you play other restricted media formats (e.g. mpeg video, mp4, etc.)?

---

### Post by niite on 2009-10-13
> **pytheas22 said:**
> niite: so you're sure you installed the ubuntu-restricted-extras package?  And you restarted your media applications (or the entire system) after installing the package in order for changes to take effect?  Have you tried playing a variety of different mp3s, or only one or two?  Can you play other restricted media formats (e.g. mpeg video, mp4, etc.)?

Good to go...  it was a problem with the particular mp3 file i was testing with..  and out of the tons of mp3 files i have, i had to pick the only one with issues to test with...  lol.

Thanks for the response!

-j

---

