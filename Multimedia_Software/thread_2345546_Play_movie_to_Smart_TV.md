---
title: "Play movie to Smart TV"
date: 2016-12-05
forum: Multimedia Software
---

### Post by dzooska on 2016-12-05
Hello all,
im looking for application, that sends a movie to smart tv (DLNA) from PC's command line. (In Windows is that functionality in WMP-> Play to device). I need for my application do this in console, for example in format:

$>appname -IP TV_IP_ADDRESS -FILE SOMETHING.AVI (or something similar in this style).

If any app exists, could me someone help, how to tell tv: "here you have url to file on DLNA server, play it"

My tv supports DLNA. DLNA server have too.

Thanks very much.
D.

---

### Post by ajgreeny on 2016-12-05
Plexmediaserver by default runs with its dlna server enabled so will do that for you.

PMS is not open source, so if that is important to you have a look at minidlna. It is a command line application that uses a fairly simple text config file (/etc/minidlna.conf) that you will need to edit for your own setup, though there is a webmin for it but I have no experience of that.

See [https://help.ubuntu.com/community/MiniDLNA](https://help.ubuntu.com/community/MiniDLNA) for a lot of helpful info on it

Others swear by mediatomb but I have no experience of that either so can't help with any more info about that.

---

### Post by dzooska on 2016-12-05
Thank you for response,

Minidlna i've installed, but its only dlna server. I would like to have some app or script, that push movie file to play on tv. That minidlna cant. Mediatomb is, i think, the same.

About PMS i didnt read, thanks for tip. Edit: it looks like media server too. I need something like samsung smartview. In smartphone i select music/video/photo and its send to smart tv. This, but only in linux cmd version.

---

### Post by ajgreeny on 2016-12-05
> **dzooska said:**
> Thank you for response,

Minidlna i've installed, but its only dlna server. I would like to have some app or script, that push movie file to play on tv. That minidlna cant. Mediatomb is, i think, the same.

About PMS i didnt read, thanks for tip. Edit: it looks like media server too. I need something like samsung smartview. In smartphone i select music/video/photo and its send to smart tv. This, but only in linux cmd version.
I think I must have misunderstood what you are looking for or trying to do!

I use both minidlna and Plexmediaserver to "push", as you call it, movie files to my LG Smart TV.  The TV has a smartshare app which sees dlna servers using wifi, and I have also installed a Plex app to the TV which can see the movies.
I do not know any applications that can specifically "push" and play a movie using a command run on a Linux computer, but that does not mean none exist.

However both plex and minidlna allow you to search on the TV for the files, movies, music and images, that are being served ("pushed" out by wifi) by the mediaserver. Unfortunately I do not know Samsung TVs and they may be very different from LG in their ability to read and use output from mediaservers.

---

