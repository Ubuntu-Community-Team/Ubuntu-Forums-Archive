---
title: "Video/Sound Editors?"
date: 2007-03-28
forum: Multimedia &amp; Video
---

### Post by jesusfr3ak4evr on 2007-03-28
I need to edit a movie and add sound on top of it. Normally I'd use Windows Movie Maker or Adobe Premiere Pro 7, but I only use linux. Are there any programs capable of doing this?

Thanks for any help.

---

### Post by Scunizi on 2007-03-28
Depending on the horsepower of your machine... Cinelerra.  Their home page is here [http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3) but you'll also find it in the repo's.  Might be worth trying to compile the latest version if you know how.  Unfortunatly I haven't tread in those waters yet.

---

### Post by jesusfr3ak4evr on 2007-03-28
I'm working on compiling cinelerra right now. Edit: wish me luck with the compiling. This isn't like linking my programming projects' .c and .h files, creating object files, and running an a.out ;) 

My system specs:

Dell D600 laptop. Pentium M 1.4 GHz/512MB PC-2100/60GB HDD

I'm looking at actually getting one of these programs to work. LiVES installed on my system but does not run. It looks like it is starting up for about 15 seconds then nothing happens.

---

### Post by Matt Yun on 2007-03-28
> **jesusfr3ak4evr said:**
> I need to edit a movie and add sound on top of it. Normally I'd use Windows Movie Maker or Adobe Premiere Pro 7, but I only use linux. Are there any programs capable of doing this?

Thanks for any help.

Last week, Linux.com did a series of articles on video editing in Linux:

[Kino 1.0 release marks shift into maintenance mode]("http://applications.linux.com/article.pl?sid=07/03/20/2121230&tid=39")
[How to create video titles and graphics with Kino]("http://applications.linux.com/article.pl?sid=07/03/09/0644209&tid=39")
[Screencasting with Linux]("http://applications.linux.com/article.pl?sid=07/03/09/2013236&tid=39")
[Become a digital video editing guru using Linux tools]("http://applications.linux.com/article.pl?sid=07/03/05/1949213&tid=39&tid=13")
[Special Report: Video editing on Linux]("http://specialreports.linux.com/article.pl?sid=07/03/15/0633233&tid=139")

And especially read:  [Open source video editing still has a long way to go]("http://specialreports.linux.com/article.pl?sid=07/03/15/0321242&tid=139&tid=39")

BTW, I wouldn't recommend Cinelerra to an inexperienced Linux user.  Unfortunately, that leaves Kino, which is not as powerful as Premiere, but at least is easy to try out: just open your **Add/Remove** tool in the Applications menu, and search for 'kino'.

---

### Post by jesusfr3ak4evr on 2007-03-29
Thanks for the informative reply, Matt. I tried Kino just now, and it has to be the least useful program I've ever used. It can't edit .avi files? Or .wmv? Or .mpg?

---

### Post by reclusivemonkey on 2007-03-29
> **jesusfr3ak4evr said:**
> Thanks for the informative reply, Matt. I tried Kino just now, and it has to be the least useful program I've ever used. It can't edit .avi files? Or .wmv? Or .mpg?

The version of Kino in Dapper didn't convert much for me either. However, the versions in Edgy and Feisty seemed to convert my .avi files without a problem. It seems to use mencoder, so it should be able to handle any format mencoder can.

---

