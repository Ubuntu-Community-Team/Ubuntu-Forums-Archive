---
title: "Mubuntu - Multimedia derivative of Ubuntu..."
date: 2006-08-15
forum: Multimedia &amp; Video
---

### Post by dolson on 2006-08-15
This is NOT an official announcement or anything of that nature, but this post, and thread, will contain all information that I can collect for you.

First and foremost. Please stop asking in email, on the forum, or on IRC about when the Ubuntu Studio Project will release a custom distro. We will not. We are simply a wiki - a documentation project only. Why? Because when I say "we" I really mean "mostly me, with some minor help from others." I can't create a derivative distro single-handedly. I thank everyone who has contributed anything to the wiki, but it seems that most people don't even read it, so I feel like I'm wasting what little time I have left to put into it these days. I also thank people who work on packaging. Specifically Forest. Thanks to him, we have some good work in Ubuntu that hadn't even hit Debian at Dapper's release. But that's where it ends. Any contributions made by the Ubuntu Studio Community are currently made directly into Ubuntu, by way of the MOTU team and the lovely REVU system. So, to sum up: Ubuntu Studio Project != distro.

All that said, I am part of ongoing discussions with several others regarding a multimedia-oriented derivative of Ubuntu, tentatively titled Mubuntu. This is not set in stone, but the name makes sense, and the domain name is owned by the right people.

This has been a long time coming, yes, but it's starting to get underway. There is a lot of work to be done, and I have very little time. If anyone wants to get involved and knows anything about packaging and creating derivative distros, get in contact with myself, panickedthumb, or Mark Shuttleworth.

The goal that I see for the Mubuntu project is to be a spinoff like Kubuntu, Xubuntu, and Edubuntu. So you would be able to apt-get install mubuntu-desktop to get everything installed, just like you can with the other metapackages today. If it is maintained outside of Ubuntu and the infrastructure put in place by Canonical, I won't have any part of it, because I detest 3rd-party repositories (my reasons are that they frequently go missing, can be easier corrupted or hijacked, are of a lesser standard of quality, doesn't affect standard Ubuntu and can eventually lead to conflicts between packages, and so on) and a separate distro entirely is even worse. But the way Kubuntu, for example, is handled, is good because it's all a part of Ubuntu as a whole, in some form or fashion. And that has always been my goal for Ubuntu. This is why I host as few files as possible on my site, because it is just not beneficial.

Anyhow, as Mubuntu progresses (if it does), I will give you what updates I can.

Right now it's only in the beginning discussion stages between a few people with similar goals, and even then, communication seems to be going slowly. There isn't a lot I can do to speed it up right now, but if other people have been involved with the other *ubuntu projects and would share a similar vision, please get involved with us. The more people with experience, the better. That's how things get done.

Until further news, that's all I have.

---

### Post by edev on 2006-08-15
Great !

If I can be of any help, let me know. I'm not a programmer and I don't know how to do packaging but I have a great expérience on linux audio oriented for musicians and studio work. I have myself a professionnal studio running on Dapper. 

So if you need specific documentation or anything related to hardware or usability of of the whole system, I can help.

Eric,

---

### Post by dolson on 2006-08-15
Well, have a look at ubuntustudio.com and whatever information is missing, feel free to get an account and add.

---

### Post by em3raldxiii on 2006-08-16
It's great to hear that there are other music-oriented folks out there trying to make Ubuntu into a DAW. My wife's band is looking at using Ardour actually, and I am likely to be the lucky fellow who figures out how to "make it go".
 
So, I eagerly await further info on this subject, and I am going to surf around on optimizing Ubuntu for music. Any and all links are more than welcome!
 
## Begin shameless plugging
And for anyone who's mildly curious, my wife's band is called Anxiety of Influence, they're an alt-rock-metalish sort of band reminiscent of Evanescence. Click the link in my sig and you can stream 4 of their tracks directly from their site (which is hosted on a Kubuntu machine, I might add). Leave them a comment on their forum if you like their stuff. 
## End shameless plugging
 
PS.  I am using a flash applet to stream the MP3s from her site, but if anyone can suggest a better way (one that doesn't require flash), especially if it uses OGG, please let me know.

---

### Post by djst on 2006-08-21
Just wanted to say that thanks to UbuntuStudio, I was able to actually hear something from Rosegarden. If it wasn't for your work, dolson, I would have given up. Thank you!

---

### Post by bobbyshane on 2006-08-24
I think a lot of people do read it and then jump head first into their music and forget to say thanks. If it weren't for the work you've done I would be back at square one when it comes to ubuntu audio... ever since dapper came out i've been trying to get my tascam us-428 to work on my laptop with ubuntu and I finally was able to pull that off last night! So as soon as I can figure out how to get on the discussion page on your page I will put in a how to on my audio card...

---

### Post by dolson on 2006-08-24
I don't care if people say thanks or not, I care that people take the time to read it instead of emailing or posting things like "I installed your Breezy PAM packages on Dapper and now my system is screwed up, what did I do wrong?" Well, for starters, you were reading the Breezy tutorials... There are lots postings and emails and chats on IRC about things that are covered in the wiki, and this is just one of the examples.

Another is that people don't know how to sign up for wiki editing, and it is a bit hidden on the About page. I will make it more obvious on the front page. Basically, email me your username, default password (or I can generate one), email address and full name.

---

### Post by em3raldxiii on 2006-08-25
Thanks Dolson ... I was kinda wondering about that myself :D

---

### Post by dolson on 2006-08-25
[http://wiki.ubuntu.com/Mubuntu](http://wiki.ubuntu.com/Mubuntu) if anyone wants to get involved.

---

### Post by floogy on 2006-08-25
Hello dolson,

You should use tasksel to define sets of applications to select, this way you can keep it modular:

Example:

[ ] audio workstation alsa based
[ ] audio workstation OSS based (not recommended, but it might be useful
[ ] audio workstation jackbased (recommended, we test your audio hardware, if it will match the requirements (latency), and enable the realtime features of a rt-kernel)
[ ] streaming server
[ ] Home Video TV and Music Station
[ ] video-editing workstation
[ ] graphics workstation
[ ] 3D-graphics and Modeling Workstation
[ ] DTP workstation
[ ] CAD workstation

---

### Post by bennyp on 2006-08-31
Considering that there are already so many offshoots of ubu, wouldn't it make more sence to distribute Mubuntu as a set of packages, or an autoinstaller?

---

### Post by dolson on 2006-08-31
It isn't an offshoot or a fork, it's a derivative. So you would be able to get Mubuntu simply by apt-get install mubuntu-desktop, just like you can with edubuntu-desktop, xubuntu-desktop, kubuntu-desktop, etc.

---

### Post by dolson on 2006-09-08
If you want any ideas to be heard regarding this, please contribute to the wiki page located here: [http://wiki.ubuntu.com/Mubuntu](http://wiki.ubuntu.com/Mubuntu)

You don't need to be a programmer or anything to contribute ideas. Just add to the wiki page so that people working on it can know what users want.

---

### Post by em3raldxiii on 2006-09-08
:D  work in progress my friend ... you've opened a can of worms now!  Haha ... you'll never hear the end of me! :twisted:

---

### Post by redneckr1 on 2006-09-27
i didnt even know this flavour of ubuntu existed.

i will definatly give the 3d tools a going over as i use them heavily in my degree.


peace out.

---

### Post by Paulus on 2006-09-27
Wow, how have I missed this in the forum!!

Nice job and I'm very happy to see this.

I'm gunna give Logic a shot in Vmware soon, should be interesting!

---

### Post by MetalMusicAddict on 2006-09-28
Hello all. Id like to announce that this project is slowly gaining momentum again. Dolson and I are working hard together to make this happen.

At present we are organizing and focusing the idea of exactly what Mubuntu will be. The constraint of using a CD has posed a particular challenge but that will be overcome.

At present we are working to pick up where [Demudi]("http://demudi.agnula.org/") left off. Gnome based and audio centric. Video editing to ultimately be added but is not the current priority.

A clear set of goals and information should be up sometime soon on the [WIKI]("https://wiki.ubuntu.com/Mubuntu").

---

### Post by dolson on 2006-09-28
We are looking for a few people who are willing to work on this project with us. You must have the desire to see it completed, and also have some time (not your entire life) to work on it, and work well in a team. If you're serious about it and want to help, please let us know.

---

### Post by Loffe_ on 2006-09-28
Very good project. Very good initiative making a derivative and then users only do an apt-get.

So wonderfully easy to get a music studio. I'm really looking forward to see this project come true.

Maybe I will contribute one day :D

//Loffe

---

### Post by casainho on 2006-10-04
> **dolson said:**
> Well, have a look at ubuntustudio.com and whatever information is missing, feel free to get an account and add.

I will look after to this project - I work with some multimedia, in a cultural association from Portugal. I am using Ubuntu since 2 years ago and happy, also doing some multimedia :-)

If I can help, I will ;-)

Good luck man!! :p

---

### Post by maniacmusician on 2006-10-04
> We are looking for a few people who are willing to work on this project with us. You must have the desire to see it completed, and also have some time (not your entire life) to work on it, and work well in a team. If you're serious about it and want to help, please let us know.

what do you need help with? i have extremely limited experience with this kind of stuff, but if there is something I can do...

---

### Post by Shin_Gouki2501 on 2006-10-04
I agreewith bennyp  a set of packages, or an autoinstaller would be absolutly sufficent!
everything else seems like wasted effort.
wbr Shin Gouki

---

### Post by MetalMusicAddict on 2006-10-04
> **maniacmusician said:**
> what do you need help with? i have extremely limited experience with this kind of stuff, but if there is something I can do...
For a list of things we need help on please go to the [WIKI]("https://wiki.ubuntu.com/Mubuntu").
> **Shin_Gouki2501 said:**
> I agreewith bennyp  a set of packages, or an autoinstaller would be absolutly sufficent!
everything else seems like wasted effort.
wbr Shin Gouki
The plan currently is that you will be able to install things with metapackages to make things easier. Go to the [WIKI]("https://wiki.ubuntu.com/Mubuntu") to see our plans.

The [WIKI]("https://wiki.ubuntu.com/Mubuntu") is currently being reorganized so if your are into the project keep comming back. There will be new info all the time.

---

### Post by maniacmusician on 2006-10-04
actually it is now [https://wiki.ubuntu.com/Mubuntu-ProjectGoals](https://wiki.ubuntu.com/Mubuntu-ProjectGoals) 

and unfortunately i can't really help with any of those :(

---

### Post by MetalMusicAddict on 2006-10-04
> **maniacmusician said:**
> actually it is now [https://wiki.ubuntu.com/Mubuntu-ProjectGoals](https://wiki.ubuntu.com/Mubuntu-ProjectGoals)
Actually, I linked to the 1st page on purpose. ;)
> and unfortunately i can't really help with any of those :(
Too bad.

For later reference. I am the project lead on this. So you know who direct questions to.

---

### Post by rytmisk on 2006-10-10
None of the mubuntu wiki links works...

Please continue the work!! I love ubuntu, but a realtime kernel and a community effort behind the multimedia/music part of it would really help!!

Best
Ketil

---

### Post by MetalMusicAddict on 2006-10-10
The project is being officially renamed Ubuntu Studio. [HERE]("https://wiki.ubuntu.com/UbuntuStudio") is the new link to the WIKI. Its currently being reworked.

---

