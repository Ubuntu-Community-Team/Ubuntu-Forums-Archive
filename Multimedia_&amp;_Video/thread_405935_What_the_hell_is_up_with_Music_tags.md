---
title: "What the hell is up with Music tags?"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by leech on 2007-04-10
Ok, here's the deal.  A lot of us are getting a rather large collection of MP3, OGG, WMA, whatever files.  

Now the problem is that not all rippers are created equal.  And apparently not all players are either.

Let us take for example some of the GTK / Gnome ones.  We have those that are just players like beep media player and XMMS, etc.  Then we have the Library style ones like Rhythmbox, Exaile, and Listen.

It's the latter here that I'm talking about.

In a perfect world, we could tell them to import a directory of music files, and they'd be able to categorize all the songs by whatever criteria we wished, like artist, album, track number, song name, year of release, etc.  

Unfortunately this isn't a perfect world, and apparently not all tag readers / creators are created equally.

Here's my problem.  Let's say I extract and rip a CD into my MP3 directory.  Usually Sound Juicer will properly fetch the Album, Artist, Track Number and Track name from the internet.  This works well, and usually works with Rhythmbox, Exaile, etc.  But sometimes I've noticed that Exaile will pick up the proper tags, but Rhythmbox won't.  Or the other way around.  Then I also have tried Easytag, which is a tag editing program in the repositories in case anyone wasn't aware of it.

Easy tag basically allows you to select a directory to scan through and find all your MP3 files, then edit them.  It's actually quite nice in that you can select large groups of them, say if you want to grab all of the songs that are by the same artist and make sure they all match (some people who rip aren't very concerned with capitalization, and such).  The problem with Easytag though, is that sometimes it can't understand a tag and so it will just remove it outright.  Then I've had some that I tagged with Easy tag and they wouldn't show up properly in Rhythmbox, but would work under Exaile.

Then I could try to modify the tags within Rhythmbox as well, but it's rather tedious and much more difficult (it's rather cumbersome in it's methods).  

So then I tried Audio Tag Tool ( sudo apt-get install tagtool ) Which is much simpler, and yet at the same time more complex than Easy tag.  (What I mean by this is that Easy tag looks more complicated because it has more options and yet is more of a flat interface (meaning it doesn't use a lot of tabs or menus, which makes it easy to use (probably why they call it 'easy tag').  But Audio Tag Tool has a tab for id3v1 and id3v2 tags, as well as you have to select different tabs for if you want to change just the tag, or tag multiple files and other things, etc.)  Audio Tag Tool worked well enough, but again, the tags didn't work across all applications.

So anyone know why this is?  Is it really possible that there is NO real standard way of tagging an mp3 file?  Anyone else have this issue?

It's driving me nuts that I try to have everything organized, yet it seems to break if I play around with different music library applications.  

Leech

---

### Post by tino27 on 2007-04-24
I ran into this same problem just today. I've been using EasyTag for a while, since it is so flexible in letting me have file names the way I want them. Looking for a new player, I decided to try BMPx (a library style program). I was just getting the hang of having it grab album names and cover art, when I went back to EasyTag to check something, and noticed all the tags were missing.

After a bit of looking into, it turns out EasyTag uses id3lib, which stopped being developed when it was on spec ID3v2.3, and BMPx (as well as RhythmBox and others) use the newer ID3v2.4. Apparently the two aren't compatible, so it in effect makes EasyTag obsolete until they switch libraries. Not sure about the other programs you mention, but I'd check to see which version of ID3 they're using.

---

### Post by robrmd9 on 2007-04-25
You both should consider trying out Ex Falso, the tag editor that comes with Quod Libet (a great music player).  It is the best tag editor I have found (on Windows and Linux) - it is easy to use and extremely powerful.

---

### Post by roadrocket13 on 2007-12-19
... i use Rhythmbox exclusively and the only .mp3 tag editor that i've been able to find even moderate results with is Kyamo (though it crashes more than any other program i've ever used). i read on another thread here that Rhythmbox uses the ID3v2.4 tags now which is probably why most of the tag tools don't play nicely with it. however that still does not explain why i can't get my files to keep their tags after they have been transferred to a different hard disk or after an OS reinstall (i have a 2nd hard disk for media files that is mounted as a slave to the "boot" drive which contains the OS). if anybody can recommend a halfway decent .mp3 tag editor i would be eternally grateful. thanks in advance.

---

