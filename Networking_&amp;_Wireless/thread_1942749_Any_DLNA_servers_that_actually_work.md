---
title: "Any DLNA servers that actually work?"
date: 2012-03-18
forum: Networking &amp; Wireless
---

### Post by pbryd on 2012-03-18
I've got Ubunutu 11.10 on an old AMD PC, I'm looking for a media streamer that actually works.

I have two TVs in the house that are DLNA capable, I'd like the Ubuntu machine to sit in the spare room and stream media to the TV's

I've tried mediatomb, rygel and minidlna but none of them are exactly easy to use, easy to configure and run from booting up.

On the the other hand my old laptop running XP and mediaplayer does just what I need.

Any suggestions?

---

### Post by SeijiSensei on 2012-03-18
Have you tried [ps3mediaserver]("http://code.google.com/p/ps3mediaserver/")?  It generally gets good reviews.

---

### Post by pbryd on 2012-03-18
Yeah just been looking at it, I've used this on the PC before too.

I'm no noob and consider myself pretty competent when it comes to PC stuff but I couldn't work out how to get it to install.

After spending hours on the other media servers and failing I just gave up.

It's shame developers are working on this stuff but Ubuntu really lets itself down when it comes to useability and support.

I might try ps3mediaserver again after I've had a break to refresh my head.

---

### Post by pbryd on 2012-03-18
Success

I managed to install PS3 Media Server and the extras needed.

I'm using Ubuntu 11.10

It runs automatically at boot and streams media to both TVs (Samsung / Sony)

First I installed the decoders or whatever they're called using the terminal 

sudp apt-get install mplayer
sudo apt-get install mencoder
sudo apt-get install ffmpeg

Then I installed the main program with 

sudo add-apt-repository ppa:happy-neko/ps3mediaserver
sudo apt-get update
sudo apt-get install ps3mediaserver

Now you can run PS3 Media Server from Applications -> Audio and Video. Don't forget to restart GUI server after update.

You'll need to add the folders you want to share.

I run it automatically when Ubuntu boots by adding it to the start up programs.

The executable you need to add is

/usr/bin/ps3mediaserver

That's it

Phil

---

