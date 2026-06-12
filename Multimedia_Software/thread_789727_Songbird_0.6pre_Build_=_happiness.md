---
title: "Songbird 0.6pre Build = happiness"
date: 2008-05-10
forum: Multimedia Software
---

### Post by ufugu on 2008-05-10
I am one of those people who bounce around music players and not been satisfied: Rhythmbox, Banshee, Exaile, Quod Libet, Amarok (yes, even Amarok is not perfect), BMPx, Audacious, XMMS etc etc, but have never quite found one that does everything I want in the way I want it too.

I've been trying Songbird off and on since version .2, and thought it had potential both as a player and with the web integration stuff, but there was always something buggy or broken with it that made it frustrating to use.  My experience with the latest "blessed" nightly has been much better though:

1) It is no longer choking on my 18,000+ library.  After an initial 10 minute build of the database on the first run, it is super smooth and FAST.

2) It edits metadata and writes it back to the file.  Yes!

3) It recognizes my 5.5G iPod instantly, reads and writes to it, including transferring playlists.

4) Etc: Addons like mashTape are working.  The window looks right. My Flash installation is detected correctly. My multimedia keys are recognized. Album art working right.  No smart playlists right now for some reason, but I can live with that.

Sorry if this sounds like an ad, but this is making me really happy.  

The blessed 0.6pre Build and iPod extension are [[COLOR="Blue"]here[/COLOR].]("http://publicsvn.songbirdnest.com/wiki/Nightly_Builds"):guitar:

ufugu

---

### Post by itsjustarumour on 2008-05-11
+1 for being very impressed with the latest Songbird 0.6 build!

Like you I've been keeping an eye on development, and I'd say this is the first version that actually seemed "usable".  A few problems with Java detection and plugins, but apart from that I haven't found anything yet that DOESN'T work.

Give it a little while, and I reckon Songbird will become to Itunes what Firefox is to Internet Explorer - well worth checking out for those who haven't seen it yet :-)  :-)  :-)

---

### Post by amazeing on 2008-05-11
At the risk of sounding noobish, where is that ipod add on link that is compatible with .6?

---

### Post by ufugu on 2008-05-12
The iPod extension is on that same page of nightly builds.  Here's how to load it:

First install Songbird, and then navigate to the builds page from within Songbird itself. Then click on the iPod extension link.  It installs itself as an extension (a la Firefox).  Also like Firefox, you then need to restart Songbird to load it. Then just plug in your iPod and Songbird should see it.

Glad I'm not the only one enjoying this.:)

---

### Post by itsjustarumour on 2008-05-12
> **ufugu said:**
> Glad I'm not the only one enjoying this.:)

Me too, and I'm surprised that Songbird hasn't been getting more coverage on these forums.  I'm sure that will change though!  :-)

---

### Post by Killa Frog on 2008-05-12
I was beta testing this in *REALLY* early development, and it's clunkiness eventually led me away from using it (far too difficult for daily life, even for the purposes of fixing bugs and whatnot), so I'm glad to hear it seems to be turning out well. It was one of my most anticipated software releases last year, so I'll definitely be picking up the new build, thanks for letting me know it was getting up to snuff!

---

### Post by amazeing on 2008-05-12
Alright I got the ipod plugin, thank you.

At first the sound worked but then I clicked some stuff and now I need to install the gstreamer plug in, please help.

---

### Post by itsjustarumour on 2008-05-12
> **Killa Frog said:**
> I was beta testing this in *REALLY* early development, and it's clunkiness eventually led me away from using it (far too difficult for daily life, even for the purposes of fixing bugs and whatnot), so I'm glad to hear it seems to be turning out well. It was one of my most anticipated software releases last year, so I'll definitely be picking up the new build, thanks for letting me know it was getting up to snuff!

Yes, compared to where it was even 6 months ago, its really come on in leaps and bounds.... still a lot of work to do, but there again its a very large and ambitious project!

---

### Post by amazeing on 2008-05-12
Got the gstreamer to work. I downloaded the ipod plug-in, how do i activate it? Doesn't read my ipod automatically or have an option in Preferences.
[http://img522.imageshack.us/img522/1373/screenshot1ib1.png](http://img522.imageshack.us/img522/1373/screenshot1ib1.png)

Unlike the other add-ons, it doesn't have it's own section under Preferences.

---

### Post by ufugu on 2008-05-13
amezing, I'm really not sure, mine was recognized without any special setup.

Make sure you have Songbird running first and then plug in your iPod.  I've had instances with other media players not recognizing the iPod if it was already mounted.

Other than that you might want to fly over to the Songbird forums for help.

u.

---

### Post by amazeing on 2008-05-13
Ok, now I opened Songbird, then plugged in the ipod. It reads it, but only for a brief moment, then exits Songbird itself immediately following reading my ipod. (Its under downloads) =[

[http://img118.imageshack.us/img118/3143/screenshotna7.png](http://img118.imageshack.us/img118/3143/screenshotna7.png)

edit - I got it to work! When it has those reloading arrows on the left of the device name, I clicked on them and it didn't immediately shut down Songird. Well, thanks for helping everyone. Should there be more options? Like displaying the current media on my ipod? (first time syncing with ubuntu)     [http://img127.imageshack.us/img127/2742/screenshoter6.png](http://img127.imageshack.us/img127/2742/screenshoter6.png)

---

### Post by nrayever on 2008-05-15
hi guys:

just one little question? had you installed songbird?? i mean like moving all files to /usr/lib or something like that? or just decompressing it on your home folder??

i'm making this question because rigth know i have a strange bug. i posted it on songbird's bugzilla:


[http://bugzilla.songbirdnest.com/show_bug.cgi?id=8673](http://bugzilla.songbirdnest.com/show_bug.cgi?id=8673)

so i would like to now how are you guys running it.

thanks

nrayever

---

### Post by amazeing on 2008-05-16
extracted to home/name/Songbird

right clicked applications in the panel and added the /home/name/Songbird/songbird to the menu

---

