---
title: "Specifying language and correcting metadata in MythVideo"
date: 2017-08-16
forum: Multimedia Software
---

### Post by quadari2 on 2017-08-16
Hi-  I'm running MythTV 0.29.  I have a number of videos stored on the computer and loaded into the MythVideo module.  Some of them are in English, some in other languages.  However, some of the ones in other languages are foreign language versions of originally English movies.  For example, the Spanish version of "Finding Nemo".

I've found that the script that automatically downloads the metadata & cover image for the videos works great, but it always pulls down the English Language title/cover image/description.  Is there a way that I can tell it what language to get?  Note that I don't want to do this universally, but need to specify it for certain videos.

Example:
For "Finding Nemo" it automatically pulls down the English data from here:
[https://www.themoviedb.org/movie/12-finding-nemo](https://www.themoviedb.org/movie/12-finding-nemo)

What I really want is the Spanish data from here:
[https://www.themoviedb.org/movie/12-finding-nemo?language=ES](https://www.themoviedb.org/movie/12-finding-nemo?language=ES)

Any and all help appreciated!
Thanks.

---

### Post by deadflowr on 2017-08-17
Do you know what script you're using?

There are two scripts that come to mind that allow downloading metadata for specific movies and tv shows.
One is tmdb3.py and the other is ttvdb.py

Not sure what their status is on 0.29 but they might be located at /usr/share/mythtv/metadata.
One would be in the Movie folder and the other would be in the Television folder.
(If they do exist there you might consider simply copying them into your home folder for easier use.

They both usually run the same basic commands: run with the -h option will list all options
for language the default is english, but you can search other languages by adding the -l option.

As I say this all maybe outdated on 0.29, but just in case here are some links:
Television scrapper script: [https://www.mythtv.org/wiki/Ttvdb.py]("https://www.mythtv.org/wiki/Ttvdb.py")
Movie scrapper script: [https://www.mythtv.org/wiki/Tmdb.py]("https://www.mythtv.org/wiki/Tmdb.py")

Hope it helps

---

### Post by quadari2 on 2017-08-29
[SIZE=3][FONT=arial]Hmmm...that helps point in the right direction, thanks.  But I'm not quite sure how to get it to run and actually update the metadata to MythTV.    For example, I try running:
[/FONT][/SIZE][SIZE=3][FONT=arial][/FONT][/SIZE][COLOR=#000000][FONT=Menlo][FONT=&quot]tmdb3.py --language=ES  Movie_Name.mp4[/FONT][FONT=&quot] [/FONT]

[SIZE=3][FONT=arial]It seems to run and produces no errors, but that doesn't appear to change anything on the front end.  Do I need to pipe/feed it into MythVideo somehow?

Thanks.[/FONT][/SIZE][/FONT][/COLOR]

---

