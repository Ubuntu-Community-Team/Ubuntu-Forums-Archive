---
title: "Any one Familiar with DeVeDe"
date: 2007-11-19
forum: Multimedia Production
---

### Post by speedsterdm on 2007-11-19
I have a bunch of avi videos that make up a season of a TV show and I wanted to put them onto a DVD playable in any and all players. I tried using DeVeDe and adding the first episode under title 1 and adding a title and putting the second episode under title 2 and so on, hoping that it would make a DVD image with each of the episodes being a title. But it didn't seem to work. Any suggestions or maybe a different program that would do what I am looking for? thanks.

---

### Post by Stochastic on 2007-11-20
I really don't know the answer but it might be helpful if you clarify "It didn't seem to work" into "It burned but only played the first episode", "It didn't burn", "the program crashed" or "It burned but wouldn't read in the DVD player" etc...

---

### Post by MepisReign on 2007-11-20
Exactly, would you be a little more specific please?

Regards,

MepisReign

---

### Post by yabbies on 2007-11-20
tovid and todisc will do exactly what you need to do while making a complete menu for you.
make sure you have plenty of hard disc space.

Make sure all repos are open, if you are not sure take a look[ here]("https://help.ubuntu.com/community/Repositories/Ubuntu") and open all repositories.

Tovid is not in the repositories so you have to install it manually.
Grab the latest DEB from [here.]("http://tovid.sourceforge.net/download/ubuntu/") Download it to your desktop so that it is easy to find.

As long as you are using dapper 6.06 or higher then just double click the deb to install.

After installed you can either use the GUI or command line. GUI doesn't always burn correctly so I opt for the command line.

First you need to transcode all the AVI files to MPG.
create a new folder on your desktop  and stick all your AVI's in the folder.
now open a terminal and change to the correct directory where your avi folder is

```
cd Destop
cd name_of_AVI_folder
```

do a```
 ls
``` command to make sure you are in the right folder and help you with the names of your files.

Now to transcode the avi to mpg

for a widescreen(16:9) ratio in NTSC(North American) format:

```
tovid -wide -in avi_file_name.avi -out new_name
```

for a fullscreen(4:3) ratio in NTSC(North American) format:

```
tovid -full -in avi_file_name.avi -out new_name
```

for a widescreen(16:9) ration in PAL(Europe) format:

```
tovid -wide -pal -in avi_file.avi -out new_name
```

for a fullscreen(4:3) ratio in PAL(Europe) format:

```
tovid -full -pal -in avi_file.avi -out new_name
```

**You just need the name of the mpg on the -out command. No need to  add the extension .mpg it automatically knows to encode to mpg.**
This will take a while depending on the size of the avi. Go take the dog for a walk. 
When you get back you will have a new mpg format of your avi. Do this for the rest of your avi's.

After you have encoded all your AVI's to MPG's then you are ready to make a playable dvd with complete menu.

right click each of your mpg's and click properties to check the size of each of your episodes. I always write mine down and calculate what will fit on a 4.7 gb dvd. Usually you can fit 4, 1  hour long episodes on one dvd.


first, open your favorite browser and in your fav search engine pull up a list of images for the tv show or movie that you are burning. I always like to save a picture that has the title of the show in the picture.
save your favorite images to the avi folder that contains your avi's and now your mpg's.

open the terminal back up to the avi folder and do a ls command to make sure your jpg picture is there and all the names of your mpg's.

now to make a cool menu for all those titles.

first to make a menu title, lets say your tv show is season 1 of Dexter

```
todisc -menu-title "Season 1\nEpisodes 1-4" \
```

make sure you use quotes. and don't forget the forward slash at the end to continue the command. The \n command staggers the title so that  it would look like this with two lines:

Season 1
Episodes 1-4

if you left it out it would all be on one line: 

Season 1 Episodes 1-4

personal preference but since the name of the show is already in the picture you saved, no need to tell anyone what the name of the show is.

next line is for the files

```
-files file1.mpg file2.mpg file3.mpg file4.mpg \
```

don't forget the forward slash. without it todisc will try to run and fail because not all commands have been entered.

now it's time for the titles

```
-titles "title 1" "title 2" "title 3" "title 4" \
```

notice the forward slash at the end. There must be the exact some number of titles as there are files. 

now to make a menu style

```
-showcase name_of_picture.jpg \
```

this will make a menu style where the picture will "showcased" on the left side of the screen and 4 thumbnails will be on the right. Again don't forget the forward slash.

Now for tv shows just because the thumbnails that will be created will be animated, and to avoid seeing four of the same opening sequences on your main menu I always seek to a place in the show.
to do this

```
-seek 300 \
```

the number you -seek to is in seconds so by using 300 I'm seeking to 5 minutes in the movie. I know, I know, but I have to say it again, don't forget the forward slash.

almost done. all you need now is a name for the out file. 
also if you have a audio file you want to use as background music for your main menu you can put that in now

```
-bgaudio AUDIO-FILE \
```

and also if you want a nifty play all button just add

```
-playall \
```

if not then just just make an out command

```
-out Season_1
```

notice that there is no forward slash "YEAH"

todisc will get down business and about after 5 minutes if will show you a preview of what your main menu will look like.
if everything looks good and correctly spelled then X out of the preview
and type **yes** in the terminal to continue the operation.

Todisc will now make a dvd directory of your tv show.
when it is done running 
in the terminal do a ls command to make sure the Season_1 directory was created.
pop in a blank dvd
and type

```
makedvd -burn Season_1
```

make some popcorn, pop in dvd and notice the awe of your friends and family.

todisc has a nice gui also, it's very easy to use
just type
```
todiscgui
```
in the terminal to get it started

experiment with todisc it is very cool and makes some awesome menus.

[todisc wiki]("http://tovid.wikia.com/wiki/Making_a_DVD_with_thumbnail_menus")
[URL="http://tovid.wikia.com/wiki/Tovid"]
tovid wiki
[/URL]

---

### Post by speedsterdm on 2007-11-21
Sorry, to clarify, it only plays the first episode and there is no menu or anything. Thanks for the great guide yabbies. Very detailed and exactly what i need. hopefully it works. I might need some more help. Thanks for all of the help everyone!!

---

### Post by sharris203 on 2008-03-06
I'm using Devede 3.6, and it works perfect for me. Maybe you have an older version. Put each episode under it's own Title. At the bottom there is an option, enabled by default, to include a menu. No further work necessary.

---

