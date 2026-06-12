---
title: "Banshee import library tool"
date: 2008-08-04
forum: Multimedia Software
---

### Post by boombox1387 on 2008-08-04
The first time you run Banshee, it's apparently supposed to run an import tool that allows you to import data from iTunes, amaroK, or other music players.  For some reason this doesn't seem to happen automatically for me (and I've tried reinstalling Banshee-1 several times).  I have a large iTunes library on another partition, and I'd really like to be able to move things like playcounts over to my Ubuntu partition.  Is there anyway that I can force Banshee to import data from the iTunes xml file if it didn't do it the first time?

---

### Post by thunderbirdje on 2008-08-04
Hi boombox

Did you try the menu item "Music" > "Import Music" or CTRL + I? 

For me this is the same windows as at the first startup.

Good luck!

---

### Post by boombox1387 on 2008-08-05
Hey, thanks for the quick reply.  I don't have my computer with me (and I won't for a couple weeks) so I can't really check this right now, but when I tried the "Import Music" option, the only options were folder, file, and home directory, but I was thinking that the first time Banshee runs it also should give the option of importing directly from another media player.  Maybe I'm wrong on this one.

---

### Post by boombox1387 on 2008-08-18
I mean, I think this should be a pretty simple thing, but I just can't figure out how to import my iTunes library into Banshee.  If anyone can help, that would be awesome.

---

### Post by boombox1387 on 2008-08-20
Sorry to bump this, but... bump.

This really seems like it should be a pretty easy thing to do.  I'm probably just missing something obvious, but I'd really like to be able to import my iTunes library to Banshee.

---

### Post by boombox1387 on 2008-08-22
Just in case anyone else stops by this thread looking for answers...

As of right now it looks like Banshee 1.2.1 doesn't have the iTunes Import Plugin that you could use with .13.2 and older releases.  Currently Banshee-1 only seems to import from Amarok, but a [request to bring back the importer]("http://bugzilla.gnome.org/show_bug.cgi?id=547925") has been added to Banshee's Bugzilla page.

While waiting for the plugin to be rewritten for the new Banshee, I thought I'd try something creative and install Banshee 13.2, run the plugin, and then replace my Banshee-1 database file with the database from .13.2.  This all worked well except for the part where Banshee-1 seems to have a hard time upgrading the database (which it tries to do automatically).  Now I have a library in Banshee-1 with all of the correct playcounts and ratings, but when I try to arrange the library by artist it arranges the whole thing by track number.  So I filed my own bug: [http://bugzilla.gnome.org/show_bug.cgi?id=549035]("http://bugzilla.gnome.org/show_bug.cgi?id=549035")

Anyway, if anyone else has dealt with this, I'd love to hear some feedback on what's worked for you and what hasn't.  In the meantime I'll probably just keep having conversations with myself in this thread. :)

---

### Post by boombox1387 on 2008-11-13
Just an update: The 1.2 series had that weird sorting problem, but that was fixed in the 1.3.x development series, and I would assume 1.4(.1) also works fine with migrating old Banshee databases.

---

### Post by HanZo on 2009-04-14
Any updates on this matter... seems pretty much unresolved still... and searching the web does not show a lot of discussion about it... would be great to be able to not have to re-rate all the songs in my library...

---

### Post by narmoture on 2009-04-14
I would like to know too, as I'm still in the progress of migrating from Windows to Ubuntu and would like to use a media player that can import the data and the music files from my old iTunes library (in a very easy way!)

Any updates?

---

### Post by nortexoid on 2009-11-10
The only way I found to import my itunes library (including ratings, play count, etc.) was through Songbird (currently ver. 1.2) by modifying the itunes database by replacing the Windows folder structure (C:\...) with the linux one (/media/disk-1/...) It worked like a charm. Too bad I prefer both Banshee and Rhythmbox to Songbird since they integrate fully with gnome. (There is Firetray for Songbird but it doesn't grab hotkeys as claimed, at least in Karmic on my machine.)

---

### Post by boombox1387 on 2009-11-12
For those who are interested in this, the bleeding edge version of Banshee is now able to import from iTunes.  It's been more than a year since I opened this thread, so it's obviously a bit late for me, but hopefully someone will benefit from this.

If you want to read about it, the information is here[1].  I don't think the option is a part of Banshee's "first run" import dialog yet, but it is available from Media > Import.

You can get the latest and greatest by downloading banshee from git master[2] and building it yourself.  If you're using Karmic, it should be as simple as adding the Banshee Daily Build PPA[3].

[1] [https://bugzilla.gnome.org/show_bug.cgi?id=441093](https://bugzilla.gnome.org/show_bug.cgi?id=441093)
[2] git://git.gnome.org/banshee
[3] [https://launchpad.net/~banshee-team/+archive/banshee-daily](https://launchpad.net/~banshee-team/+archive/banshee-daily)

---

### Post by nortexoid on 2009-11-12
> **boombox1387 said:**
> For those who are interested in this, the bleeding edge version of Banshee is now able to import from iTunes.  It's been more than a year since I opened this thread, so it's obviously a bit late for me, but hopefully someone will benefit from this.

If you want to read about it, the information is here[1].  I don't think the option is a part of Banshee's "first run" import dialog yet, but it is available from Media > Import.

You can get the latest and greatest by downloading banshee from git master[2] and building it yourself.  If you're using Karmic, it should be as simple as adding the Banshee Daily Build PPA[3].

[1] [https://bugzilla.gnome.org/show_bug.cgi?id=441093](https://bugzilla.gnome.org/show_bug.cgi?id=441093)
[2] git://git.gnome.org/banshee
[3] [https://launchpad.net/~banshee-team/+archive/banshee-daily](https://launchpad.net/~banshee-team/+archive/banshee-daily)

Fabulous! I backed up my Banshee database, deleted it, and then imported the entire library from iTunes without a hitch! Everything was imported included playlists. Ratings and play counts intact!

Note that when I tried to import over my preexisting database (all songs overlapping) I got thousands of errors and none of the playlists worked. Basically it didn't work at all.

This saves me a lot of manual rating!

I should add that I just ran update manager, having the banshee daily ppa in my sources. The iTunes import showed up after a restart.

---

### Post by boombox1387 on 2009-11-13
> **nortexoid said:**
> Fabulous! I backed up my Banshee database, deleted it, and then imported the entire library from iTunes without a hitch! Everything was imported included playlists. Ratings and play counts intact!

Note that when I tried to import over my preexisting database (all songs overlapping) I got thousands of errors and none of the playlists worked. Basically it didn't work at all.

This saves me a lot of manual rating!

I should add that I just ran update manager, having the banshee daily ppa in my sources. The iTunes import showed up after a restart.

Awesome!  I hadn't actually tried it, so I was speaking only in theory.  Good to know that it actually works in practice as well :)

---

### Post by kgroll on 2009-11-14
> **boombox1387 said:**
> For those who are interested in this, the bleeding edge version of Banshee is now able to import from iTunes.  It's been more than a year since I opened this thread, so it's obviously a bit late for me, but hopefully someone will benefit from this.

If you want to read about it, the information is here[1].  I don't think the option is a part of Banshee's "first run" import dialog yet, but it is available from Media > Import.

You can get the latest and greatest by downloading banshee from git master[2] and building it yourself.  If you're using Karmic, it should be as simple as adding the Banshee Daily Build PPA[3].

[1] [https://bugzilla.gnome.org/show_bug.cgi?id=441093](https://bugzilla.gnome.org/show_bug.cgi?id=441093)
[2] git://git.gnome.org/banshee
[3] [https://launchpad.net/~banshee-team/+archive/banshee-daily]("https://launchpad.net/%7Ebanshee-team/+archive/banshee-daily")
Much thanks for this update boombox, it couldn't have come at a better time.

To elaborate for new users like myself:
1. Go to System>Administration>Software Sources
2. Click Other Sources tab, then Add...\
3. Paste **ppa:banshee-team/banshee-daily** into the APT Line: field. Add source then close.
Now you need to add the key for authentication.  From link #3 above, note the key [                 1024R/6E80C6B7               ]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0x9D2C2E0A3C88DD807EC787D74874D3686E80C6B7&op=index")
4. Open up your terminal. Type **[FONT=Courier New]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7[/FONT]**  (the last part is the banshee ppa key).
5. Now you can use the Software Center, or however you prefer to install/update apps to get the latest build of Banshee, containing the new iTunes importer.

---

### Post by molond on 2011-04-15
hi all
i have had full success with banshee 2 on natty narwhal but i am woundering if it is possible have it sync the iTunes library every time it open as i buy all my songs in iTunes

---

### Post by Willynux on 2011-04-29
Hi, 
I've spent three days on this, I finaly found out that Banshee 2.0 can import iTunes library from the menu midia>import media> import iTunes

My issue now is that Banshee only imported about half of my music, the rest gives an error "file not found" although files ARE at the location indicated by Banshee.

Did someone get this error too? did someone manage to use this feature successfully?
I was on iTunes 10 and Banshee 2, on ubuntu 11.04

---

### Post by boombox1387 on 2011-05-01
> **Willynux said:**
> 

My issue now is that Banshee only imported about half of my music, the rest gives an error "file not found" although files ARE at the location indicated by Banshee.

Did someone get this error too? did someone manage to use this feature successfully?
I was on iTunes 10 and Banshee 2, on ubuntu 11.04

It's been years since I've played around with Banshee's iTunes importer, but if it's not working as expected, it probably wouldn't hurt to grab a debug log[1] and file a new bug report[2].

[1] [https://live.gnome.org/Banshee/CommonQuestions/Logs](https://live.gnome.org/Banshee/CommonQuestions/Logs)
[2] [http://banshee.fm/contribute/file-bugs/](http://banshee.fm/contribute/file-bugs/)

---

### Post by Willynux on 2011-06-30
Hey,
What happens is that Banshee won't import songs that contain Latin  accents for some reason... Is there a work around (maybe converting the  .xml library to another format?) for me to import songs that contain  accents?

In any case hanks for the suggestion, it took me some time to learn how to do it but was definitely worth it. I had to dig deeper to understand the problem and found a bug report that describes the issue:
[https://bugzilla.gnome.org/show_bug.cgi?id=521401](https://bugzilla.gnome.org/show_bug.cgi?id=521401)

The reply from gnome bugzilla is that there's not much that can be done in Banshee for this...

---

