---
title: "IMDB Script no longer pulling director?"
date: 2009-07-29
forum: Mythbuntu
---

### Post by Nobodyspeshul on 2009-07-29
Did they change something on imdb.com?

Recently while adding movies through the video manager, the directors are coming back marked as unknown.

Is this something I can modify my imdb.pl script, or do I need to upload a new version?

---

### Post by tgm4883 on 2009-07-29
> **Nobodyspeshul said:**
> Did they change something on imdb.com?

Recently while adding movies through the video manager, the directors are coming back marked as unknown.

Is this something I can modify my imdb.pl script, or do I need to upload a new version?

They may have changed something on their site again. It's actually against their ToS now to do that. What you may want to do is try using tmdb.pl, you can find instructions on that at [http://www.mythtv.org/wiki/Tmdb.pl](http://www.mythtv.org/wiki/Tmdb.pl)

---

### Post by Nobodyspeshul on 2009-07-29
Perfect, thank you very much.

---

### Post by gwagchunks on 2009-07-30
Hi

Silly question... , I followed and the link and how do you know if your using a sub version client? And what does that mean?!:oops:

Thanks as always

---

### Post by tgm4883 on 2009-07-31
> **gwagchunks said:**
> Hi

Silly question... , I followed and the link and how do you know if your using a sub version client? And what does that mean?!:oops:

Thanks as always

Ok, that's one of those things that if you don't know if you are, then you are not. 

Subversion is a revision control system used in the development process. The instruction are asking you to pull down part of the development tree.

I may try to put together something for adding this a little easier.

---

### Post by uncle hammy on 2009-08-01
This may sound crazy, but how do you actually USE the tmdb script?  I am running 9.04, and I see the tmdb.pl script in /usr/share/mythtv/mythvideo/scripts however all my machines were set up some time ago and the settings all still point to /usr/share/mythtv/mythvideo/scripts/imdb.pl -M tv=no;video=no as the script to use.

I am assuming it's not as simple as changing the imdb.pl part to tmdb.pl.  However, the wiki is strong on installation instruction, zero on usage.

---

### Post by uncle hammy on 2009-08-01
Nevermind, apparently it is as simple as changing the "imdb.pl" to "tmdb.pl".  I has tried to set this up before and it didn't work, however for the heck of it I tried it again and it's working.

---

### Post by jb5 on 2009-08-01
Just a quick FYI.

After updates the updated tmdb.pl file does not have it's execute bit set, (or that has been my experience), so I have to re-set this after each update.

---

### Post by pederj on 2009-08-05
I've been having problems with both imdb.pl and tmdb.pl. 

imdb.pl doesnt pull all information as mentioned above. The tmdb.pl script doesnt work for tv-shows, and i really prefere to get user ratings from imdb.

I managed to get the python script imdbpy.py also included in mythtv to work. It pulls pretty much all information from imdb including "plot", "director", "user rating", poster etc and works great with tv-shows too. There are occasional problems with "rumtime" data, which i havent been able to fix, but thats the only problem i noticed.

you will need to install python-imdbpy from the repositories: 

```
sudo apt-get install python-imdbpy
```Depending on your python version and ubuntu version you might get an error message(i did).

```
/var/lib/python-support/python2.6/MySQLdb/__init__.py:34: DeprecationWarning: the sets module is deprecated
  from sets import ImmutableSet

```This appears to be a bug: see [bug #338387]("https://bugs.launchpad.net/python-mysqldb/+bug/338387")
 Get rid of the error message by editing the imdbpy.py script:

```
sudo gedit /usr/share/mythtv/mythvideo/scripts/imdbpy.py
```change the first line to :

```
#!/usr/bin/python -W ignore::DeprecationWarning
```And the script should work

whether this still violates imdb's Terms of Service i don't know. If you dont want to violate these, its safer to use tmdb.

Anyway hope it helps

---

### Post by tgm4883 on 2009-08-05
> **pederj said:**
> 

whether this still violates imdb's Terms of Service i don't know. If you dont want to violate these, its safer to use tmdb.


Why would that method be different in terms of the ToS than the perl script? Are the IMDB site owners perl haters?

---

### Post by pederj on 2009-08-05
> **tgm4883 said:**
> Why would that method be different in terms of the ToS than the perl script? Are the IMDB site owners perl haters?

Well i would assume there's no difference, but as i havent read the ToS of imdb i cant say for sure. I just had to point out it might be a problem, so people can choose the tmdb script if they wanna be sure and dont mind the drawbacks of that script.

If anyone has knowledge of whether or not the imdbpy script is against the ToS of imdb feel free to post.

---

