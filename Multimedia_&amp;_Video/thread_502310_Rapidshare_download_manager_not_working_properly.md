---
title: "Rapidshare download manager not working properly"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by Robbyx on 2007-07-16
Instead of downloading the full file flashgot is getting just a small html file. This should not happen because I have set the download options in Rapidshare to direct downloads. The underlying file  manager is wxdownload fast. Has anyone else defeated this problem?

---

### Post by Robbyx on 2007-07-17
Does anyone know the answer?

---

### Post by dysphasi on 2007-10-27
Afraid I can't give you an answer as such, but have you tried using linkification and downthemall addons if you use firefox? 

You can just copy and paste all your links in a text file and fire it up in firefox and download them all easily with downthemall.

If you use opera, it's even easier, just use the linkify java script:
[http://userjs.org/scripts/browser/enhancements/linkify-text-files](http://userjs.org/scripts/browser/enhancements/linkify-text-files)
and download using 'links' in the side panel and filter away for the files you want.

---

### Post by jdownloader.com on 2008-02-26
**jDownloader** is realized in Java and it's a good download manager for Rapidshare
:KS

---

### Post by zambangi on 2008-03-01
This is what works for me....

- Feisty Fawn
- Latest Wine(forgot exact version)
- Latest Flashget
- Latest firefox with latest Flashgot add-0n

Steps :

-make sure firefox and flashgot installed and working
- install flashget using wine...just download flashget and open terminal type wine flashget installer.exe(make sure run the command fr the same folder where to dl the flashget installer....just to make sure wine find it)

- during installation do not tick any feature offered by flashget....just untick evything

- after finish installation...just exit the terminal
- try launching flashget via the gnome panel....flashget must be able to run if you want to continue the next steps

- if flashget OK...now open firefox..make sure flashgot addon are running..just right click on anylink, there will be flashgot option

- right click on any link then choose flashgot options then more option...

- on the General tab click Add...give any bame name then browse to where you have installed flashget.

- choose flashget executeable...

- then back to flashget...

- click tools...click default download properties ...

- MOST IMPORTANT 4 rapidshare premium member...enter your rs ID n Password into the Login to Server field...untick ShareURL and choose ur download directory...

- now just open any page with a list of RS dl link, highlight all the link then right click...choose Flashgot Selection..

- in a while, your flashget shud prompt u if u want to dl all the link...just select OK..

- then if all OK, it shud start to download...

HAVE FUN...:)

---

### Post by lible on 2008-03-04
I must admit it worked quite well.. i prefer using idm but this comes in as a close second.
Thanks for the help

---

### Post by cor2y on 2008-03-04
I just used wget and a small wget batch download script to get files from rapidshare

---

### Post by Robbyx on 2008-03-04
I have it all working now. I am using a combination of flashgot selection calling download them all (DTA). It is working extremely well because DTA can also pick out all the links on a page and give me options as to which type I wish to download,  from RS.

---

### Post by Reban on 2008-03-09
Just to drop by a note,
RSConsole is a Rapidshare.com Premium file download accelerator and scheduler for Linux, Unix and BSD.

I've just tried it, and it works like a charm. Probably the best Rapidshare Premium downloader around that's open source.

You can find it here:
[http://www.addedworth.com/rsconsole.php](http://www.addedworth.com/rsconsole.php)
Cheers,
Reban

---

