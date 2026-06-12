---
title: "ubuntu tag editing specially aac"
date: 2007-03-02
forum: Multimedia &amp; Video
---

### Post by zorkerz on 2007-03-02
Ive been searching the forums for a good way to edit my music files.  In particular i have had trouble with the aac (.m4a or .m4p for some i guess) format.  I have reverted at times to windows and used itunes to to do this.  There are many old threads here about this none of which have come up with an easy solution at least for gnome users.  I think amarok has worked for some.  Easytag is supposed to hove aac support however it is disabled in the ubuntu and i believe debian packages.  Editing tags in rhythmbox works for some files and not others.  This would be the most preferable method for me because i am already using rhythmbox and would not need a new app.  Is anyone else still struggling with this problem?  Does anyone have a good solution? thanks
elias

---

### Post by compwiz18 on 2007-03-22
I'm trying to do the same thing with m4a files.  I can play them, I can rightclick on them and click audio, but I want to rename them by song name instead of ****.m4a (as is standard on the iPod)  I need a program that can read the tags, and rename them.  Just for the record, easytag and cowbell don't work.

---

### Post by zorkerz on 2007-03-22
I hear your cries.  I posted similar posts a couple times over the last year or so most with no response at all. Apparently easy tag can do this but it is disabled in the debian packages.  I wander if some one compiled it from source if you could get around this? Anyways don't hold your breath ive found little interest and less progress on this.  Currently i boot in windows if i really need to edit .m4a tags. cheers

---

### Post by MetalMusicAddict on 2007-03-22
Compiling EasyTag yourself will let you edit the tags.

---

### Post by zorkerz on 2007-03-22
alright looking for some help compiling easy tag from source.
-I downloaded easytag-2.0.tar.bz2 from easytag.sourceforge.net
-extracted with the archive manager
-changed directories to the extracted folder
-ran ./configure
-then make
-then sudo make install

ok never mind i just did this a second time and it worked nice.  However when i open easy tag it does not recognize any music files at all no matter the extension (a have .m4a, .mp3, and .ogg at least).
any ideas what could have caused this?

---

### Post by compwiz18 on 2007-03-23
> **zorkerz said:**
> alright looking for some help compiling easy tag from source.
-I downloaded easytag-2.0.tar.bz2 from easytag.sourceforge.net
-extracted with the archive manager
-changed directories to the extracted folder
-ran ./configure
-then make
-then sudo make install

ok never mind i just did this a second time and it worked nice.  However when i open easy tag it does not recognize any music files at all no matter the extension (a have .m4a, .mp3, and .ogg at least).
any ideas what could have caused this?
I'll try compiling this myself tomorrow, and I'll post how it works.

---

### Post by zorkerz on 2007-03-26
I was just messing around and installed the easytag in the repositories and it also does not find any media files that i know are there. Ive completely deleted .easytag file in home to try and reset the settings. So im not sure if my compile worked or not or how to approach this new problem.

---

### Post by cdrom600 on 2007-06-05
Did you ever get this working?  If so, how?

---

### Post by compwiz18 on 2007-06-05
Easytag can do it - you'll have to compile it somehow though...

---

### Post by zorkerz on 2007-06-06
Yes that is what i see. I am no expert at compiling and have had no luck at it yet. If anyone has success please fill us in.
cheers

---

### Post by compwiz18 on 2007-06-06
> **zorkerz said:**
> Yes that is what i see. I am no expert at compiling and have had no luck at it yet. If anyone has success please fill us in.
cheers
I could compile it for you...are you on a 64bit system or 32bit system?

---

### Post by cdrom600 on 2007-06-06
I'm on a 32 bit.

---

### Post by compwiz18 on 2007-06-07
I can't get it to compile with aac support on Ubuntu. It says ```
checking for MP4/AAC file support... no
***
*** Warning: MP4 file support disabled
*** (Install libmp4v2 to enable it)
***

```
but after I install libmp4v2(-dev) it still doesn't compile with that...

anyone have suggestions?

---

### Post by finite9 on 2007-06-07
im in a moaning mood--sorry for the negativity...

Why can medibuntu not compile packages with full support for restricted formats, if it is legally dodgy for Canonical to do this in the main repos?  It is way too much hassle to have to compile from source ten different apps, just because they lack support for the popular restricted formats.  Then we could all just add medibuntus repos to sources.list and get auto upgrades.  When I compile something myself, I don't get security updates for that package from then on.

---

### Post by compwiz18 on 2007-06-07
I don't know - I'm on Arch right now and easytag ships with aac support :)  Why Ubuntu doesn't, I don't know.  I believe aac is a patent free format so there shouldn't be any issues...

---

### Post by zorkerz on 2007-06-07
I remember somewhere it was not actually aac support that was the problem but it was the tagging methods for aac that were restricted somehow. This could be wrong but I think I read it somewhere. Im also on 32 bit.

---

### Post by logos34 on 2007-08-02
I just compiled 2.1 stable and it did so WITHOUT aac/mp4 support!  
> 
EasyTAG 2.1 
(compiled:Aug 2 2007)
(using:GTK+ 2.10.11 and id3lib 3.8.3)
(MP4/AAC file support disabled)

Wtf is going on?  I have all the dependencies, and the INSTALL file explicitly indicates it will be enabled by default:
> 
 - libmp4v2 ([http://resare.com/libmp4v2/](http://resare.com/libmp4v2/)) (if not desactivated by './configure --disable-mp4') (Recommended: libmp4v2-1.5.0.1)

Ideas, anyone?  I'd would really like to find a way to read the tags on my iTunes .m4a/alac (apple lossless files)

---

### Post by kostkon on 2007-08-02
> **finite9 said:**
> im in a moaning mood--sorry for the negativity...

Why can medibuntu not compile packages with full support for restricted formats, if it is legally dodgy for Canonical to do this in the main repos?  It is way too much hassle to have to compile from source ten different apps, just because they lack support for the popular restricted formats.  Then we could all just add medibuntus repos to sources.list and get auto upgrades.  When I compile something myself, I don't get security updates for that package from then on.

I agree with you. *Medibuntu* should provide a package *EasyTAG* with the *aac* support enabled, like it does the same for many other packages for similar restricted stuff, like *ffmpeg*, *K3B*, to name a few.

---

### Post by zorkerz on 2007-08-02
how do we contact medibuntu to ask them to do this?

---

