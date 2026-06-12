---
title: "[SOLVED] wget &amp;amp; Bashpod | podcatcher for low bandwidth"
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by Lutherian on 2007-08-27
Hi

Being on a low bandwidth connection using radio, (not land line / cable) , timeout errors are a reality.
The only way to get *anthing* downloaded is by levering the power of wget.

In my case wget -t0 -c -S --retry-connrefused -no-dns-cache [http://xyz.zxy.com/filename.ext](http://xyz.zxy.com/filename.ext)

Naturally, when I looked for a podcatcher / podcast downloader, I soon realised I would need the wget magic to get complete podcasts downloaded.

I know that podracer and bashpodder use wget, but I'd like some advice as to how I could sneak in the wget -t0 -c -S --retry-connrefused -no-dns-cache option in a config file or sorts in any recommended podcatcher.

In a perfect world voice podcasts would be broadcast in speex format
Audio podcasts would be in aac - and aac would be opensource LOL, although there are some ogg podcasts out there.

Thanks all (^_^)/'

---

### Post by Lutherian on 2007-08-30
Ooookaaaay

Seeing as nobody was able to help me (tut tut)  I had to what normally has to be done.
i.e. I had to help myself (^_^)/'

So, the answer is as follows:

step 1: make a nice directory to install BashPod for example

Code:
sudo mkdir /home/lutherian/BashPod

step 2: get the files

Code:
$ wget [http://linc.homeunix.org:8080/script...shpodder.shell](http://linc.homeunix.org:8080/script...shpodder.shell)
$ wget [http://linc.homeunix.org:8080/script..._enclosure.xsl](http://linc.homeunix.org:8080/script..._enclosure.xsl)
$ wget [http://linc.homeunix.org:8080/script...podder/bp.conf](http://linc.homeunix.org:8080/script...podder/bp.conf)

step 3: make an executeable

Code:
sudo chmod 755 bashpodder.shell

step 4: Add feeds by editing a file

Code:
vi (or gedit) /home/lutherian/bp.conf

and that's all there is to it.

if you want this to run routinely, you can edit your cron file as follows

Code:
02 00 * * *	cd /path/to/bashpodder && ./bashpodder.shell

Now to address my original query, it is possible to tweak the system to keep retrying - and persist past those pesky "time-out" errors

Code:
vi (or gedit) /home/lutherian/bashpodder.shell

scroll down to the part where you see a command wget .......
look for the -t 10 option and change it to -t0

this means that wget will re-try an infinite number of time to get the file down
(as opposed to just giving up after 10 try as was the original config.)

---

