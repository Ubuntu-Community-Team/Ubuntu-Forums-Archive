---
title: "Movie collection scanner / manager"
date: 2008-09-16
forum: Multimedia Software
---

### Post by Fufkin on 2008-09-16
Hello :)

I have been searching for an application to scan and manage my movie collection, but it is much harder than I thought it would be.

My dream app would do the following:
* scan my movie folder, which is full of .avi files
* download some info for each movie from imdb based on the filename
* display the movies in a nice little list which I can search etc.
* let me click on a movie in the list to launch the associated file in an external player.

I have found and tried four possibilities, but they each have problems:

GCstar: Doesn't scan - have to manually add each movie and manually associate it with a file.

Griffith: Doesn't scan and can't associate movies with a file.

Mythtv with the video plugin: Couldn't get it to scan my movie folder, not sure if it downloads movie info.  I don't really like this option because it's just a plugin for an app whose main function I don't use (don't need all the TV features).

XBMC: This is the best one I've tried so far, but it is still pretty unstable (it's alpha) and I couldn't see a way to correct the movies that it misidentified when it scanned my movie folder.

Are there any other apps or options that I am missing?  Or do I have to accept that the app I am describing doesn't exist?  

Thanks for any help :)

---

### Post by troutbum13 on 2008-09-16
I use XBMC, the mis-scans are annoying, I usually only get them in really odd movies, but you can sometimes change the movie name and rescan, or you can create an NFO and thumbnail and name them the same as the movie and it will default to the NFO and thumb. You could also specify different scrapers

[check here]("http://xbmc.org/wiki/?title=Import_-_Export_Library#Video_nfo_Files")

the XBMC library feature is good for movies, but it is amazing for TV shows, especially with thetvdb.com scraper...I personally have not seen anything better than xbmc, the linux version is pretty stable, I rarely have issues.

I recommend XBMC + mediastream skin...the app will only get better and for core functionality it a damn fine product

If you find something better, I'd love to hear.

---

### Post by Fufkin on 2008-09-16
> **troutbum13 said:**
> I use XBMC, the mis-scans are annoying, I usually only get them in really odd movies, but you can sometimes change the movie name and rescan, or you can create an NFO and thumbnail and name them the same as the movie and it will default to the NFO and thumb. You could also specify different scrapers

[check here]("http://xbmc.org/wiki/?title=Import_-_Export_Library#Video_nfo_Files")

the XBMC library feature is good for movies, but it is amazing for TV shows, especially with thetvdb.com scraper...I personally have not seen anything better than xbmc, the linux version is pretty stable, I rarely have issues.

I recommend XBMC + mediastream skin...the app will only get better and for core functionality it a damn fine product

If you find something better, I'd love to hear.

Thanks for this, I may have dismissed XBMC too quickly.  I just gave it another shot and forgot how impressive it is.  With some work it should do everything I want :)

(this is a whole new issue, but I just compiled the latest version of xbmc and now it won't even load!  I guess I'll have to wait until the impending release of the new version)

---

### Post by troutbum13 on 2008-09-16
there is a PPA and repo so you no longer have to compile unless you want the daily build. I have no problem installing the ppa to hardy and gutsy machines...alternatively post your debug log on XBMC forums and they are pretty good about helping out.

good luck

---

### Post by vjkeito on 2009-06-20
> **Fufkin said:**
> 
GCstar: Doesn't scan - have to manually add each movie and manually associate it with a file.

Dude, to add all your movies you can import a name-list (text file).

Simply place all your correctly named films (or folders) in a directory, cd into that directory and then pipe the output of ls to a text file.  You can then use this to auto-import all your films at once.  Easy.

```
cd ~/Your/Films/Directory/Here

ls > ~/name_list.txt
```


Now I need to work out a way of exporting my collection in gcstar so that I can import it into xbmc with all the artwork already done etc.

---

