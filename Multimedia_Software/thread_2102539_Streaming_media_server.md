---
title: "Streaming media server"
date: 2013-01-07
forum: Multimedia Software
---

### Post by p2ranger on 2013-01-07
Running headless 12.04 Ubuntu server. I just reinstalled it after having 10.04 for a while.

I've been reading around about different options for streaming media. I want to be able to stream photos, videos, and music to my Playstation 3.

I'm wondering what +'s &-'s are of some of the server programs out there and any experiences you have had. Lots of the things I've been reading are over a year old. Don't know if things have changed or if there is something new I should be checking out.

I've been reading that some of the favorites for doing this seem to be miniDLNA, Playstation3 Media Server, Serviio, Twonky, and others. My little server isn't too powerful, its running on an atom processor. I suppose home movies will be most of what videos will be streamed. I know Serviio and Twonky cost money, but I don't mind paying for something if it works well.

There's just a command line interface for my server. I've read where someone has gotten PS3MS to run with just command line. I would like to be able to have a web interface to administer it for what ever I'm using instead of having to look up a command to change something. Does PS3MS have a web interface?

I tried using mediatomb on my previous server install, but I had to use command line to start it up, and didn't start on its own. Also development on it has seemed to stop.

Some people say that they don't want the overhead of running java with having PS3MS running. I already have subsonic running, which as I understand it uses java. Does that make a difference? I only know enough about this to get myself in trouble.

Anyway, thanks for any input or links to where this may be discussed already

Jason

---

### Post by Hawkway on 2013-01-13
I'm installing Ubuntu Server 12.04 for the first time and have a similar question.  I'm trying to find a good way to setup media streaming and looked at Subsonic and Tonido, but haven't settled on either.  I would like to be able to stream to my iPhone, iPad and Apple TV, but still not settled on one solution.

---

### Post by p2ranger on 2013-01-13
I wound up installing Serviio:

[http://www.serviio.org/](http://www.serviio.org/)

I'm mainly an android user, so don't know how it works with iOS devices. I'm using it mainly for DLNA to my PS3 for photos and home movies. Downside is that I'm paying $25 for the pro version. There's an android app that I can use for configuring the server as my server is command line and headless. There's a couple of 3rd party developers who are making web gui's for configuring your server. I couldn't get it to work, so I went with just using my adnroid device.

Why I didn't choose the others:

Mediatomb - no development on it for a while
MiniDLNA - lack of transcoding
PS3MS -  I'm not running a GUI and I didn't see an easy way to get around that. Plus it sounds like from reading forums that the developers have split up and part of them have created their own fork.
Twonky - something about it just didn't seem right for me

As for Subsonic, I've been running it for about 3 years for my music, and I really like it. You have to buy an iOS app to stream the music to your iPhone. I think you also have to pay to register your Subsonic server to stream to anything that's not a web browser.

This page may help you make your decisions:

[http://en.wikipedia.org/wiki/Comparison_of_UPnP_AV_media_servers](http://en.wikipedia.org/wiki/Comparison_of_UPnP_AV_media_servers)

Jason

---

### Post by p2ranger on 2013-01-13
Just ran across this article on life hacker FWIW

[http://lifehacker.com/5975362/five-best-desktop-media-servers]("http://lifehacker.com/5975362/five-best-desktop-media-servers")

Jason

---

