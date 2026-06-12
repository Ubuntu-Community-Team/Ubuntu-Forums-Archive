---
title: "Anyone know of a good movie organizer?"
date: 2009-12-30
forum: Multimedia Software
---

### Post by Skyler0 on 2009-12-30
Greetings,

I'm curious to know if there is any kind of application that will organize movies (avi/xvid/mpeg etc).

What I would like is to to be able to search/grab data from IMDB or other database, and then be able to organize the actual directories structure and file name based on that. (for example "/Videos/[Genre]/Name [Year].avi" or something similar.

Something that also contained a library of videos with the same type of database grab would be sufficient as well, although not as ideal as the above.

I'm thinking something similar to how musicbrainz is, only for movies.

Thanks,
-Sky

---

### Post by fancypiper on 2009-12-30
I really like [Miro]("http://www.getmiro.com/download/for-ubuntu/") for videos.

---

### Post by LuisGMarine on 2009-12-30
> **fancypiper said:**
> I really like [Miro]("http://www.getmiro.com/download/for-ubuntu/") for videos.

That looks like a very interesting piece of software I think I'm going to install it and give it a whirl. :guitar:

---

### Post by lovinglinux on 2009-12-31
[GCstar](http://www.gcstar.org)

---

### Post by jdunka on 2009-12-31
I just looked at GCStar and Miro. I'm digging Miro.

---

### Post by Skyler0 on 2009-12-31
I looked a Miro, but I didn't really see any kind of organization thing to the movies. They were just listed. :/. I also tried GCStar, but it kept freezing when I tried to import a folder.

I found some other canditates I'm going to check out though:

[Data Crow]("http://www.datacrow.net/")
[Griffith]("http://www.griffith.cc/")
[CeeMedia Movie Catalogue]("http://ceemedia.sosdg.org/")
[MeD's Movie Manager]("http://xmm.sourceforge.net/index.php?menu=main")
[MovieFly]("http://savannah.nongnu.org/projects/lmc/")

---

### Post by papibe on 2009-12-31
I had a similar concern a few weeks ago and this is what I have learned so far:

IMDB has a web API (so does themoviedb.org) that let you fetch media metadata. Most media center software display their cool menus using addons that use these APIs.

One way to go would be installing a media center and let it manage your movies. I didn't go that way (too bloated).

Luckily, there are standalone media managers like:
[INDENT]
[LIST]
[*][YAMJ or MovieJukebox]("http://code.google.com/p/moviejukebox/wiki/MovieJukebox")
[*][meta<browser/>]("http://themetabrowser.com/")
[*][TVScout]("http://www.codeplex.com/TVScout")
[*][medianav]("http://code.google.com/p/medianav/")
[/LIST][/INDENT]

(sorry same of them are windows only)

I end up using YAMJ, that is multiplataform (Java). I didn't need a database like yourself, but a easier way to browse my movies and choose what to watch.

I hope it helps,
Regards.


Note: YAMJ was designed for the PopcornHour (something like an appleTV), but the menus are created and maintained on the computer side.

---

### Post by Skyler0 on 2009-12-31
I never said I wanted/needed a database myself. It just seemed like the easier way.

I would be most happy with somethimg that simple reorganized the directory structure in that above format

/Videos/[Genre]/Name [Year].ext

That way movies are semi-easily listable just from directory alone.

---

### Post by LuisGMarine on 2009-12-31
Well whatever you decide to do I'm going to suggest a similar feature to banshee.  For example banshee can organize all your songs into folder like artist/album/song, but the option to organize is not there for video.  I'll submit a request so just keep your eyes out for it in the future.

---

### Post by fancypiper on 2009-12-31
I am just now trying [Moovida]("http://www.moovida.com/").  It looks promising as well.

---

### Post by fancypiper on 2009-12-31
> **lovinglinux said:**
> [GCstar](http://www.gcstar.org)On my system, it crashes fluxbox.  I haven't tried it in gnome as of yet, but unless it works in fluxbox, it doesn't work for me.

---

### Post by iggykoopa on 2009-12-31
It's a windows app but look into ember media manager. I run a virtual machine purely for that app, it's works really really good (it's designed to use along with xbmc)

---

### Post by embra55 on 2010-06-05
hi there, try using Data Crow from sourceforge. I used it when I was using windows, but am now a newbie on linux, and as such haven't quite figured out how to install it on linux. It lets you create a data base of vitually anything you want. Give it a try, it's easy to use, the result is great, and you can export, back up etc. Good luck,
embra55 [ronnie]

---

### Post by madeinfamous on 2010-06-05
allo Skyler0,

have you try Griffith,

in add/remove ;)

[http://www.griffith.cc/]("http://www.griffith.cc/")

"Griffith is a media collection manager application. Adding items to the collection is as quick and easy as typing the film title and selecting a supported source. Griffith will then try to fetch all the related information from the Web."

plaisir :)

---

### Post by Skyler0 on 2010-06-05
Thanks for the replies :)

I've recently been using MeD's Movie Manager. It seems to work pretty well, supports Linux and Windows, and supports SQL databases. It also has a static html export for movie listings.

I ended up creating a couple php pages and using the sql database it creates, created a dynamic webpage to list the movies along with the program itself which is a little more powerful at the moment.

The only issue I have now is pretty much just the fact that the cover isn't stored in the SQL, just a location, and thus I need to update the covers manually *sadface*


But, it gets the job done and I'm happy with it :)

---

### Post by ShizzlePDX503 on 2010-06-16
I know this is hella late but you can always run [Ember Media Manager]("http://www.embermm.com")...

[http://www.embermm.com/boards/2/topics/837?r=1196](http://www.embermm.com/boards/2/topics/837?r=1196)

---

### Post by Bramkaandorp on 2011-07-07
Even though this thread has been down for a long time, I think that posting a new reply here would be more constructive than starting a new thread.


I am looking for a video organizer in which I can put different TV series present on my computer under different categories (airing, pending, canceled to give a few examples) without having those changes imposed on the hard disk drive on a directory level.

This would be a great improvement on my current method, since I use Unison to sync my computer once in a while, and you can imagine how irritating it can be to see one folder go from one directory to another, and then back again with the next sync.


I hope I'm not too vague.

---

### Post by handy on 2011-07-07
> **madeinfamous said:**
> allo Skyler0,

have you try Griffith,

in add/remove ;)

[http://www.griffith.cc/]("http://www.griffith.cc/")

"Griffith is a media collection manager application. Adding items to the collection is as quick and easy as typing the film title and selecting a supported source. Griffith will then try to fetch all the related information from the Web."

plaisir :)

+1

I use Griffith it does everything I need, it is certainly well worth a look:

[http://griffith.cc/index.php?option=com_content&task=view&id=27&Itemid=35](http://griffith.cc/index.php?option=com_content&task=view&id=27&Itemid=35)

Though I will eventually use Haiku to manage my media, as the Haiku file system is brilliant, it has the built in ability to simply set up a database using its inherent functions of Filetypes, Attributes, Index and Queries. Here is a link to tutorial which may or may not wet your appetite for R1 of Haiku:

[http://www.haiku-os.org/docs/userguide/en/workshop-filetypes+attributes.html](http://www.haiku-os.org/docs/userguide/en/workshop-filetypes+attributes.html)

---

### Post by Bramkaandorp on 2011-07-07
How should I look at it?

I mean, is it a program in which I add films and episodes of TV series by adding the actual files to the program, or do I create items in the same way I would do with a book? That is, merely adding the data (title, year and so on).

because I am specifically looking for a program in which I can insert all the folders (or all files), and categorize them according to whether they are still airing, on hiatus, unsure or other criteria.

Best case scenario would be if I could actually add files to the folders through the program, so that I can avoid Nautilus as much as possible, because I don't want to change the directories too much, and having a lot of folders without categorization is pretty messy.

---

### Post by Bramkaandorp on 2011-08-24
Bump

---

### Post by HouseMafia on 2013-03-27
Perhaps you should try jMovieManager [http://www.addictivetips.com/windows-tips/jmoviemanager-offers-all-you-need-from-a-film-tv-series-organizer/](http://www.addictivetips.com/windows-tips/jmoviemanager-offers-all-you-need-from-a-film-tv-series-organizer/)

---

### Post by overdrank on 2013-03-27
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

