---
title: "This is not a bug."
date: 2009-09-08
forum: Mythbuntu
---

### Post by rusty0101 on 2009-09-08
Though it does mean that there will be a number of people who will find certain aspects of mythbuntu and mythtv unusable.

Mythtv-frontend is database schema locked to the same version of mythtv-backend. This means that if you have been happily avoiding the bugs in Intel video driver support that were introduced in 9.04 by running a previous version of Mythtv-backend which also serves as your front end on that system, you don't get to blindly install a client on your Karmic laptop and start talking to that backend.

I could go into a philisophical discussion about writing a client that understands that the data is being served by a system that might just not be the same platform that the client is running on, but since the fundamental rule about even reporting a bug at MythTV is that you have to be running from the most recent SVN, I suspect that it's a lost cause.

---

### Post by SiHa on 2009-09-08
I'm with you. I'd dearly love to try out 0.22 on a spare remote FE, but as the BE is 0.21, and I have absolutely no intention of changing that and risking the wrath of the wife, then I guess I'm stuck for the time being.

---

### Post by klc5555 on 2009-09-08
> **rusty0101 said:**
> Though it does mean that there will be a number of people who will find certain aspects of mythbuntu and mythtv unusable.

Mythtv-frontend is database schema locked to the same version of mythtv-backend. This means that if you have been happily avoiding the bugs in Intel video driver support that were introduced in 9.04 by running a previous version of Mythtv-backend which also serves as your front end on that system, you don't get to blindly install a client on your Karmic laptop and start talking to that backend.

I could go into a philisophical discussion about writing a client that understands that the data is being served by a system that might just not be the same platform that the client is running on, but since the fundamental rule about even reporting a bug at MythTV is that you have to be running from the most recent SVN, I suspect that it's a lost cause.

As others have discovered, the Jaunty Mythtv .021 common and frontend packages appear to install and run without difficulty on Karmic Ubuntu.

---

### Post by superm1 on 2009-09-08
So although it's possible for us to create a 0.21 package for karmic, that will quickly end up in a messy scenario where it's incredibly difficult to upgrade to 0.22 for anyone that wants to.

Anyone familiar with debian packaging should understand that the latest version number is used in a buildd process, and the only way to make a version that is alphanumerically less than another be selected is by introducing an epoch.  You add one epoch and then you have to do it again to get people an upgrade scenario.  It's not a path we're gonna support.

If you want 0.21 on karmic, please just install the jaunty packages on top of karmic and lock them using apt or synaptic.  They'll likely run fine, albeit they won't be as optimized as the trunk packages that are on karmic since they're built with the new GCC.

---

### Post by rusty0101 on 2009-09-10
The thing is, I don't really want to have to install earlier versions on top of the latest version.

My point is that not supporting backwards compatibility either in a client communicating with an earlier version back-end, or with a newer version back-end is going to cause users problems, and looks bad.

If Firefox would only talk to web servers that talked version 3.0.5-26 of the HTTP spec, no-one would use the browser because almost no-one would be using that version of the spec.

Now I understand that it's nice to have all the capabilities of the database template you would like to use to communicate between the client and the server. I'm not disputing that. And at some point not having similar release versions will pose significant issues, but it shouldn't be because you are using 0.21 one place and 0.22 some place else.

Will it mean that some features may not work? Yes. And as the user decides that that feature is a make or break feature for them, that decision should be made by the user. However something like a list of cut points and bookmarks does not seem to me to be something that is likely to be a significant change between any two version. And if it does change, perhaps because the possiblity of recording a show that takes over 2 terabytes of storage (as an example) and you need to switch from Integer references to long, or long to double-long, it makes sense to build in a compatibility layer to handle the fact that you very likely have a good sized collection of recordings that currently use the old spec. They may even be on separate back ends that will take time to update as well.

Is it a flaw? Yes. Is it a bug? No. It can't be reproduced if you install the latest SVN versions of the client and server. Duh!

It's a flaw that is not 'new' to the Jaunty/Karmic update. It's been an ongoing flaw with MythTV for years, and I first saw it manifest while running KnopMyth. Because everyone is hyped on this idea of 'it's only a bug if it shows up as a problem with the latest SVN (git, tlaothp)' it will never be corrected.

At best you get a warning message that the database template is outdated and the client is not going to play with the server. At worst your client 'updates' the template that the server is not able to use, and you pretty much lose your entire platform.

---

### Post by superm1 on 2009-09-10
I entirely understand your point of view now, and I tend to agree that the situation pretty much sucks right now that different versions are not compatible to one another.

But I wouldn't say it "will never be corrected".  The software is still young, and when the developers feel comfortable enough to call it's protocol API stable, then they can start looking at backwards compatibility for new versions.  Adding such things to an already unstable API adds tons of overhead to an already stressed development team.

---

### Post by the Goat on 2009-09-10
> **rusty0101 said:**
> Is it a flaw? Yes. Is it a bug? No. It can't be reproduced if you install the latest SVN versions of the client and server.

You are 100% wrong.  MythTV consists of two parts the frontend and the backend.  Of coarse they must be the same version to work together.  Why would you think otherwise?  MythTV does not use a published industry standard defined API for a reason.

---

### Post by rusty0101 on 2009-09-12
MythTV is not 'two parts, a frontend and a backend' in it's current implementation. It is many more parts than that. It is also a collection of templates for MySQL, customized drivers for capture cards and devices, customized scripts to call stand alone and integrated applications, a buhch of PHP templates for web servers, and a upnp server for stand alone devices to stream content from.

The structure of the platform is supposed to be client and server. The Client side should no more need to know the database internals than it needs to know whether the signal leaving the TV broadcast station is polarized vertically, horizontally, or circularly. It's a detail that should not be in that interface.

What has been built is two clients that access the same mysql server, and as a result the 'server' portion of the platform is not really the back-end. It's that database. As far as I can tell, the only 'server' that the back-end provides is the ability to stream the A/V data to one or more the front ends. There are enhancements available through the custom link between a MythTV front end and the back end that are not available for clients such as the upnp client on a PS3, or other device, but those enhancements appear to be nothing more than the client being able to specify where to jump from and to based on a database request for cut point information. Does the PS3 care what version of database layout is being used by the server? No.

Properly built, it would not matter which version was being used. In fact your back end could communicate with my back end and share cut point information, so that I could quickly grab a couple of gop-frames on either side of the specified cut point, slide ofset's if needed, and merge your cut points into my recording of the same program, and start watching on my PS3, without having to use the 'normal' front end on my system at all. The back end would be 'configured' to either warn about cuts, follow cuts, or ignore cuts as I would like, and the PS3 (VLC, whatever) could send 'play', 'pause', 'stop' messages, or even fast forward.

Is the platform 'young'? Well if you define that by it hasn't released a 1.0 version, then yes. If you count the number of 18 month generation cycles that just about every other computer based product tries to work within, then it should be considered to be at least 3 generations old, and probably two or three more generations.

There are two reasons that MythTV does not use a published industry standard defined API. It's their product to drive into the ground if they would like, and there isn't a 'published industry standard defined API'.

I may seem a bit bitter over this, but I'm really only noting that this is an area that very much can use improvement, and could be handled a lot more cleanly, but there is no way that it can be identified as a bug, or for that matter really a wish list item in the current development system, because the very first step in reporting a 'bug' is to 'compile from the latest SVN version' and see if the flaw has already been addressed. And everythign else I see at the MythTV site is 'if it won't show up in the latest SVN, don't bother us.'

Ok, Rant over. I very much like MythTV. I strongly expect to use it for years to come, and will be very happy to see many improvements in that time. Hey perhaps they will even define an API that can be used to build plug in for platforms like vlc, gstreamer, and so on, such that not only can those clients play, fast-forward, rewind, pause and stop playback, but they could build cut-points, avidemux could connect and you can edit the content and push it back with the cut points processed, and so on.

But hey if you like the illusion that the current implementation is the model of perfection. OK. Glad you like that.

---

### Post by rusty0101 on 2009-09-12
I understand. Mostly I was frustrated in that it's both a situation that has been around for over 5 years, and the public image place for noting that this is a concern presents the image that the developers don't care.

In a way this feels like the IP conversion from using a centralized server that handed out host files to all IP connected systems, to the predecessor to the DNS host system we enjoy today. That didn't prevent systems that were using the old system from connecting at all, it just ment that they wouldn't get the latest information until the updates for the system were applied. Because of the method of implementation, an application compiled for IPv4 will not be able to communicate over an IPv6 network, except via IPv4 over IPv6 tunnels. And the reverse is also true. However if you compiled an IPv4 application 10 years ago, it will still work on an IPv4 network today, even though substantial parts of the infrastructure have gone through significant changes.

Because of the fact that there is not a clearly defined, documented and stable API between the front and back end, the best that the developers can say about the application as a fronend/backend application is that it is a demonstrator. Something presented as a proof of concept. The 'version' bears this out, but it's frustrating for the end users

---

### Post by July1234 on 2009-09-12
The Escapist has posted an article on "The Secret of WoW" which is an in-depth look at the many many reasons why people still play World of Warcraft.The article also makes suggestions to new developers about what they need to include to take on the giant! [http://www.powerleveling-gold.com](http://www.powerleveling-gold.com)
The author points out the obvious skew in the industry when he says, "Ten million subscribers. At $15 a month each, that comes to $150 million a month and 1.8 billion a year.  [http://www.powerleveling-gold.com/](http://www.powerleveling-gold.com/) If you could capture just one in ten WoW users and get them to jump to your MMO, you'd be a massive success by industry standards".
Here's a look at the article, take a look and reply with your comments below:
If I had a double bacon cheeseburger for every forum post titled "Why do people [still] play World of Warcraft?" then I would have died of a coronary a year before The Burning Crusade went into beta.  [http://www.powerleveling-gold.com/](http://www.powerleveling-gold.com/)  Now, mostly these posts are from basic internet-level malcontents and trolls, or people who can't grasp the idea of different people having different personal tastes. But I want to take the question seriously for a minute, partly so that you can just drop a link to this article the next time one of those threads appears, but mostly because I think that hopeful MMO game designers might be asking themselves the same thing. 
  [http://www.powerleveling-gold.com/](http://www.powerleveling-gold.com/) Ten million subscribers. At $15 a month each, that comes to $150 million a month and 1.8 billion a year. If you could capture just one in ten WoW users and get them to jump to your MMO, you'd be a massive success by industry standards.

---

### Post by SiHa on 2009-09-12
Post removed, spurious post about World of Warcraft disappeared! Note the title...

---

### Post by foxbuntu on 2009-09-12
> **rusty0101 said:**
> ..the image that the developers don't care..

As a developer for Mythbuntu and working closely with the MythTV community over the last several years, I find it offensive when users make snap judgments about the products we, as developers, have spent so many hours of our own personal time improving and building without thanks or charge for, you the user. 

To clear this up, the MythTV Database has a large schema that support multiple projects and plugins from the frontend. The version locking is in place to prevent issues with data corruption or loss. So in-fact the developers do care, because if we did not we would leave you in the wind and at will loosing data from the database with bad decisions like mismatching software versions and causing data loss. 

As a final note to anyone out there that thinks we don't care, perhaps you should come ask questions and learn about what we, as developers, do to contribute to the community before making snap judgments about us.

---

### Post by dsbw on 2009-09-12
Yeah, this is pretty much a classic software development issue. It's seldom easy, often ugly, and you're kind of screwed no matter what you do (break backward compatibility and piss people off, or try to support it with potentially disastrous results&#8212;and piss people off).

If anyone really thinks that there's no one on the development team that cares about some issue they care about, there's a solution for that: get on the dev team yourself. But don't expect your ideas to be as revelatory as they might appear to you from the outside.

---

### Post by rusty0101 on 2009-09-22
First let me say thank you to the developers who are paying attention. This did get sidetracked with the different version issue, but having experienced the situation where a front end 'setup' changed the template on the back-end that was running at an earlier version that couldn't use the new template and thus broke the entire environment, I know better than to run 'mythtv-setup' on a freshly updated release. First make sure that the backend is running the same release. Giving the front end the ability to break the back-end is a bad idea. Presenting the user with the message "run mythtv-setup to correct this issue" qualifies in my mind as monumentally stupid. The correct error dialog should be "The front end you are attempting to run is incompatible with the back end you have running." There are two possible courses of action that should be available, advise the user to upgrade the backend with updated database templates, or advise the user of what version of frontend is available for them to run until such time as the backend is compatible with the freshly installed front end.  

I've already vented enough on this. My initial complaint was not about the fact that release 0.22 is incompatible with release 0.20.2 or earlier. I may not be happy about the fact that the incompatability exists, or I may be excstatic. That's not important. My complaint was, and remains that the developers of MythTV if not Mythbuntu have raised a barrier to reporting problems that prevents end users who are looking to run a stable platform from reporting issues that they experience. That barrier is that to be considered a bug whatever the end user is seeing as failing has to be apparent in the current SVN. 

End users should be expected to be able to report crashes, bugs and events that go contrary to expectations, regardless of what version they are running. They may get better support if they are running a version that is considered long term support (perhaps only from the ubuntu folks) or a current 'release' version (support should be provided by MythTV.org, hopefully at a better than 'we'll get around to the ticket some day' level.

---

