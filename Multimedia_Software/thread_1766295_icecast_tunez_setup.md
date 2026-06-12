---
title: "icecast_tunez setup"
date: 2011-05-24
forum: Multimedia Software
---

### Post by m33rkat on 2011-05-24
Hi to all,

With some info on the web (icecast.org) and about 5 threads from the ubuntuforums I am still unsure as to how to setup a icecast server for my mp3 stream and tunez as a voting system.

I am no expert in Linux but would appreciate some quick pointers in getting me started with the icecast box.

I am running ubuntu 10.10 x64 on a virtual machine hosted on esx*

I have had some assistance in getting the basic lib's that will be needed with *cast box and also downloaded the icecast 2.3.2 tar ball. 

A would very much appreciate any assistance in getting me started.

Thx!

---

### Post by m33rkat on 2011-05-24
Got some info here [http://www.communecation.net/2005/08/03/howto-streaming-audio-server-on-debian/]("http://www.communecation.net/2005/08/03/howto-streaming-audio-server-on-debian/") with icecast, darksnow & darkice but unfortunately no mention on MySQL... Is this something to consider or does icecast or tunez not rely on a DB?

What modules should be installed prior to installation of icecast, or is it as simple as apt-get install icecast darksnow darkice

Any advise on what should be configured and what files? 

Or better yet.... any "Beginners Guide" on this ;-P 

Perhaps a url please. No luck with g00gle... :---)

---

### Post by m33rkat on 2011-05-24
I'm getting good at this, thanks to the Ubuntu Forum Topics I missed :oops:

[http://www.howtoforge.com/linux_webradio_with_icecast2_ices2](http://www.howtoforge.com/linux_webradio_with_icecast2_ices2)

---

### Post by m33rkat on 2011-05-25
Ok, so ices2 (ver.2) sends the ogg vorbis stream to the icecast server, but ices (ver.0.4) is used to stream .mp3 data to the icecast server, from disc storage.

I have played with the *playlist*.xml file (ices2) and set the full/path/of/.m3u file and nothing works... I mean:

How do you tell ices2 to start sending the stream?
I just tested the stream, using ices2 but will uninstall this version as I require to stream .mp3 data from storage.

I have mounted the storage device in fstab.
In what fashion should ices be told where to look for the .mp3 data to stream.

ICES* talk about a mount stream (which is referred to a stream name) .... a naming convention for clients do differentiate between streams? 

I would like to stream .mp3's located on a storage device, already mounted and accessible.

Any advise:confused:

---

### Post by m33rkat on 2011-05-25
Any interest at all from the ubunutuforums community, or am I missing something? Any direction please:-k

---

