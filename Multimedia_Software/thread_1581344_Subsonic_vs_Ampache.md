---
title: "Subsonic vs Ampache"
date: 2010-09-24
forum: Multimedia Software
---

### Post by tylersontag on 2010-09-24
I'm looking for a way to stream my music/videos to my droid x and i think i have it narrowed down to these to services to do it.

Now, i have a LAMP server on this box already, so either should be just about as easy to setup (minus, as i understand it, standing up a tomcat plugin for subsonic)

I've looked at both client side players on the droid and i like both fairly well, though its hard to be certain with only a dry run, so to speak.

Could anyone outline maybe a few pros/cons to help me decide?  Perhaps around integration with playlists, maybe performance? ease of administration?  I'm just on the fence here

---

### Post by RickThorpe2006 on 2010-09-27
When I got my Droid X, I initially used Ampache with both Lullaby and Amdroid. Lullaby worked the better of the two, but I still had regular connection issues, such that I started looking for alternatives.  I installed Subsonic and was quickly won over.  Pluses for Subsonic included much better luck sustaining connections, better phone interface, pre-caching of songs to cut gaps between songs when streaming, easy ability to save albums locally while on wifi (as a result of which I now rarely use Cubed, instead using Subsonic for both streamed and saved music), easy and fast updating of library.  The "donation" to unlock streaming to android after the default period was more than worth it.  

Subsonic isn't perfect yet (auto-retrieve of cover art is broke, issues with foreign characters that you have to modify config file manually to fix, the occasional skip in the first seconds of streaming before the cache fills properly), but it is getting close.

---

### Post by ArtInvent on 2010-10-02
Haven't tried Ampache, I would also be interested to hear from someone who's used both. As for Subsonic, it's excellent. If you already have a LAMP server setup, I would think Subsonic is a no-brainer. I just have an Ubuntu desktop, I set up SSH but no LAMP server, and I got it working without too much drama. I use DynDNS to get a static IP for my DSL connected box, that was probably more work than actually installing Subsonic. 

I also have a Droid X and the Subsonic app works pretty well. Over wifi it's excellent, with a decent 3G signal it's fast enough. It caches all the songs as quickly as it can, so even if you lose network you still have your music. Plus it doesn't clear the cache so even rebooting, you still have your most recently played music on the phone. 

My friends and family can now play or download all my music anywhere anytime with just a guest user account. I can make them playlists and store them in Subsonic. 

I even use Subsonic on the local machine. It's just convenient to have a music player in a web browser tab. And the player and interface are that good, I really don't miss Amarok or Rhythmbox at all.

Problems: Subsonic Android app wouldn't play any tracks with funny characters in the filename like Spanish enyas or French accent marks. There is a pretty simple fix for that, google it. Next, on the first couple of tracks you play on the Droid X after startup, there may be a slight glitch/skip about 10-15 seconds into the track. The Android app has been updated a few times but this glitch seems to persist. Not a real big deal though.

I'm looking into Ampache a bit because I notice they seem to have a new function of remote controlling one player (say, on your home theater pc) from another device (say, your cell phone.) I would love to be able to control my stereo from the phone, or play stuff for my parents from 200 miles away. However, Subsonic devs say they are working on that as well for the near future. With that remote control feature on the phone, it would be pretty awesome - no Sonos necessary, no extra hardware.

Being based on Java I was half expecting Subsonic to be slow as molasses. Not at all. I have nearly 100GB of music and it lists with album art pretty quickly.

The only other thing I could possibly wish for is video streaming. Maybe someday. Of course at this point I couldn't even use it cause it would require a much faster internet connection.

Subsonic is also what Ubuntu One's new music streaming service is built off of. Seems like a good endorsement.

Highly recommended, in short. Gladly donate $10 for the key to remove the ads.

---

### Post by tylersontag on 2010-10-18
I've been running both and here are my findings so far.  Both get the job done, i will say i'm favoring subsonic more though.

Lullaby (the best ampache client, i'm told) looks more like the native player BUT it doesn't rotate  if you turn it sideways and as far as i can tell you cannot listen to cached songs youve already DLed when you are out of coverage.  Subsonic was also easier to setup (i had to scratch my head and try to remember what i have root setup in mysql and figure out where the config file wanted to live)

No big differences, but 'll probably be using subsonic

---

### Post by jshayden on 2010-10-30
I've been running Ampache now for about a week, and my only real complaint is with the Android apps: Amdroid is lacking in its interface, and Lullaby skips songs in my playlists at random.

After reading this thread, I'm going to give Subsonic a try.  I love the idea of caching and gapless playback.  The only reason I didn't go with it in the first place is because: 1) I was avoiding Java; and 2) for some reason, I was under the impression it couldn't transcode FLAC on-the-fly, which it CAN.

Installing Subsonic now.  I'll let y'all know what I think.

---

### Post by cjssmo on 2010-12-08
I personally find Ampache much more flexible than Subsonic.

Just a little comparison from my point of view.

1. Do the respective programs meet Debian/Ubuntu DFSG guidelines?
Ampache == yes
Subsonic == no

2. Are either of the respective programs in the Debian/Ubuntu archives and available via apt-get or aptitude?
Ampache == yes
Subsonic == no

3. Do you have to pay to remove advertisements from either app?
Ampache == no
Subsonic == yes

4. Can you use MPD with either of the respective programs to pipe music to you home stereo?
Ampache == yes
Subsonic == no

5. Can you set up a internet radio station with either app?
Ampache == yes (with icecast)
Subsonic == no

6. Do either apps have DLNA support?
Amapche == yes (with python-coherence)
Subsonic == no

7. Are there apps for other phones such as the palm-pre or blackberry?
Ampache == yes
Subsonic == no

8. Can you use either app as a backend to your favorite media player such a rhythmbox, banshee, or Amarok?
Ampache == yes (with the release of natty, has plugins for all three via apt-get)
Subsonic == no

9. Do either apps have a stand alone media player designed especially for that app?
Amapche == yes (viridian which is available via apt-get)
Subsonic == no

10. Do either app stream video?
Ampache == yes (is still beta and rough around the edges)
Subsonic == no

11.  Will either app handle large collections?
Ampache == yes (the largest I have seen so far is 5.5TB)
Subsonic == unknown

12) Are there any VM appliances that can be run in VMware for either app?
Ampache == yes (VMampache)
Subsonic == no

Just because Ubuntu One chose to use Subsonic does not mean it is the best choice for your personal needs.  All it means is that Subsonic fits better into Ubuntu One's money making infrastructure.

I calculated how much it would cost to host my 1.2TB of music through Ubuntu One and it came out to a staggering $1,827.00 USD per year.

Well that's my $0.02, take it for what it's worth.:D

---

### Post by atomney on 2011-01-11
To comment on cjssmo's post,

I personally find Subsonic much more USEFUL than Ampache.

Just a little comparison from my point of view.

1. Do the respective programs meet Debian/Ubuntu DFSG guidelines?
Ampache == yes
Subsonic == no (Also not relevant to which one streams music better)

2. Are either of the respective programs in the Debian/Ubuntu archives and available via apt-get or aptitude?
Ampache == yes
Subsonic == no (But Sindre 'the developer' provides great support for ubuntu and many other OSs with easy pre-made packages.)

3. Do you have to pay to remove advertisements from either app?
Ampache == no
Subsonic == yes (Ever heard the expression "You pay for what you get" ;)

4. Can you use MPD with either of the respective programs to pipe music to you home stereo?
Ampache == yes
Subsonic == no ( actually yes, do your research before posting things like this)

5. Can you set up a internet radio station with either app?
Ampache == yes (with icecast)
Subsonic == no (Who cares.. they both have web interfaces for streaming)

6. Do either apps have DLNA support?
Amapche == yes (with python-coherence)
Subsonic == no ( No quarrels here.. )

7. Are there apps for other phones such as the palm-pre or blackberry?
Ampache == yes
Subsonic == no (YES there is.. the FIRST app was for Blackberry.. and there are also apps for windows phone7 and ipod,ipad,iphone)

8. Can you use either app as a backend to your favorite media player such a rhythmbox, banshee, or Amarok?
Ampache == yes (with the release of natty, has plugins for all three via apt-get)
Subsonic == no (no.. but why would you? it is my favorite media player)

9. Do either apps have a stand alone media player designed especially for that app?
Amapche == yes (viridian which is available via apt-get)
Subsonic == no (YES it does.. it's called SubAIr and it runs on all major OSs great!)

10. Do either app stream video?
Ampache == yes (is still beta and rough around the edges)
Subsonic == no (YES it does, and just like ampache.. it's in beta)

11. Will either app handle large collections?
Ampache == yes (the largest I have seen so far is 5.5TB)
Subsonic == YES (I can only speak for 2TB of music)

12) Are there any VM appliances that can be run in VMware for either app?
Ampache == yes (VMampache)
Subsonic == no (Yes.. it's called any OS on a virtual machine. You can use their nice packages to install it quite easily, Mine runs on an Ubuntu 10.10ServerVM Under Xen ;)

Just because Ubuntu One chose to use Subsonic does not mean it is the best choice for your personal needs. All it means is that Subsonic fits better into Ubuntu One's money making infrastructure. (While this may be true.. It did fit BETTER)


Just some corrections from a long time Ubuntu and Subsonic user ;)

---

### Post by Xlorep DarkHelm on 2011-01-13
I'm only now looking into Ampache personally, and Subsonic didn't meet my requirements, mostly because of how I like to organize my music to produce a continuous stream of music from my collection through my home-made playlist generator. My playlist generator requires the following features to be really useful:

[LIST=1]
[*]Tagging (to define categories my music falls into)
[*]Date/Time Added to library (to figure out what, of the songs I haven't played yet, has been sitting unplayed the longest)
[*]Date/Time Last played (to figure out what, of the songs I have played, has been sitting unplayed the longest)
[*]Ratings (a core separation/partitioning of my music, alongside the category tags -- **must be able to be defined per-song**)
[*]Play count (to determine what has been played the least)
[/LIST]

I also need to have some way to interface with the internal database that the streaming server uses to track the songs, fortunately I can do that with either app.

The problem I had with Subsonic was that the Ratings are strictly based on album, not track. This doesn't work for me, as there are some songs I like less than others in a given album, and would prefer them in a lower rating. It's a shame, since my playlist generator is written in Java, it would be nice to also have the music player be in Java (especially since I have a dedicated Glassfish 3 server running at home), but Subsonic is a bit too limited for my tastes, while Ampache has what I need for my playlist generation (which is central to me listening to music, I have it designed to completely manage what music I listen to at any time, and need each of the elements in the list above to be available to be acceptable for me).

So while I do like Subsonic's functionality in general, and have no real problem forking over money to buy a license if needs be, I just wish I could get it provide everything I need for my playlist generator, which it currently doesn't (as of the last time I actually looked at it). Ampache, on the other hand, does provide everything I need, and I am currently in the process of converting my music library from Logitech's Squeezebox Server, which I currently am using for my music, over to Ampache. Maybe one day Subsonic will provide what I need, and I'll transfer the library over to that app.

---

### Post by samfuzz on 2011-01-13
why not using Music Player daemon :

    - multiple output possibility (can be enable:disable by the client) :
            [LIST=1]
[*]- streaming (httpd, icecast) : ogg, mp3, flac , pcm ...
[*]             - pulseaudio, alsa, jack, oss
[*]             - pipe output ...
[/LIST]
    - possibility to browse :
                 [LIST=1]
[*]by folder
[*]                  by tag : genre, artist, album, comment ....
[*]                    (multiple field tag possibility per song : useful for genre, comment field)
[/LIST]
    - internal stickers database (rating ....)
    - and more (replaygain ,playlist .....)


but it lacks a good client that deals with the stickers database for rating, i was trying this one jiggyMPD 
it extends MPD database for adding features MPD clients typically lack, such as ratings, date added, and last played date
[https://bitbucket.org/cubiczee/jiggympd/wiki/Home](https://bitbucket.org/cubiczee/jiggympd/wiki/Home)
(but it seems it can't run with php5.3)

there is also mpdcron client : use stickers database  (CLI)

edit : forget to say (a little off topic) that the best tool that i known  for create multi-criteria playlist,  is gmusicbrowser

---

### Post by Caesium137 on 2011-01-16
Ok, How do you use MPD with Subsonic?

Google has lots of junk hits and I'm feeling slightly lazy....

Thanks,

Master Nate.

---

### Post by LandRacer on 2011-02-06
Subsonic is a joke, and is NOT free!

Well the app on the droid at least. 30-day use period then they want money. Bite me! So don't be deceived with subsonic. That crap is not free, and these guys claim open-source. NOT ON MY SYSTEM. Spit on that garbage! Subsonic also likes to download requested music files to your system/memory card instead of streaming the music. What was the point of setting up a music server to stream, when it downloads? I could transfer files myself thanks.

Try Jinzora, they are in the development stage for the android app. I was looking at that the other day. Jinzora is written in PHP I believe, It works well with my Apache/lamp Web Server. Jinzora also works with my video files, yay! But so does gnump3d< no more development there...

I've used Ampache and lullaby, way better combo then subsonic.

IF you have a newer droid that will play flash, you can also try Sockso. That is a pretty slick music ONLY server for the novice. Which streams music instead of downloading it. I've used Sockso for a long time. Kind of a resource hog though. Wait NOT kind-of, IT IS. BUT it works good!

I guess I really posted to slander Subsonic, what garbage.

---

### Post by smbell on 2011-03-29
@LandRacer
Really? You're going to whine it about it not being free as in beer?

The code is free and that's what really matters. It's GPL and hosted on sourceforge, as are most of the interfaces.

If you have reasonable gripes about the system that's fine, but going off on a rant about how it's a horrible thing that they might actually charge money for a software product is not just annoying it goes against much of the point of open source software.

If the fee bothers you that much just check out the code, remove the ads, compile, and install, or don't use it.

---

### Post by Esus on 2011-06-23
Seriously LandRacer, if you're so technically inclined, remove the ads yourself. It takes all of editing one line!! -- That's probably a lot of hard work for a guy who whines about getting other peoples hard work for free though. And CJSSMO, so many of your points are just plain wrong... I hope you don't persuade too many people based of your uniformed comments. 

I have to say having been an devoted Ampache user for over 3 years that Subsonic blows amapache out of the water. Every thing that bothered me and every feature Ampache lacked I found in Subsonic.

The active development and better streaming capabilities of Subsonic alone should sell you, but there are so many more reasons beyond that. Everything from the interface, uploading capability, better apps, video, transcoding... i could go on and on.

Set both up if you're deciding and run them side by side for a week. That's what I did until after day one I had seen enough and turned my Ampache server off because Subsonic is so much better.

---

### Post by Roasted on 2011-06-23
> **atomney said:**
> 

3. Do you have to pay to remove advertisements from either app?
Ampache == no
Subsonic == yes (**Ever heard the expression "You pay for what you get"** ;)
Just some corrections from a long time Ubuntu and Subsonic user ;)

I don't mean to single handedly completely downright obliterate this comment with one puny little phrase, but I'm going to since this point you tried to make warrants it.

What's your argument in regard to Windows vs Linux, then? :lolflag:

---

### Post by YogiPaolo on 2011-11-10
This tread god awfully pissy. I think I got some on my pant leg...

---

### Post by airtonix on 2011-12-21
> **atomney said:**
> To comment on cjssmo's post,
...

Just a little comparison from my point of view.

...

5. Can you set up a internet radio station with either app?
Ampache == yes (with icecast)
Subsonic == no (Who cares.. they both have web interfaces for streaming)

...

8. Can you use either app as a backend to your favorite media player such a rhythmbox, banshee, or Amarok?
Ampache == yes (with the release of natty, has plugins for all three via apt-get)
Subsonic == no (no.. but why would you? it is my favorite media player)

...


I think the salient point here about ampache and external radio streams is this : having the ability to vote on tracks discovered from radio streams would be great for a number of reasons.

For one I wouldn't have to deal with any sticky legal issues that arise from an audit on our company hardware.

Secondly, not having to set aside copious storage space for tracks would be a plus.

The downside to this is that I believe ampache may only be able to provide a small list of track candidates for users to vote on when those tracks are discovered from radio streams. Last time I checked radio streams only provide the next 3-5 songs to be played 
(if at all).



> **LandRacer said:**
> Subsonic is a joke, and is NOT free!
Jinzora is written in PHP I believe, It works well with my Apache/lamp Web Server.

I'd actually prefer a web interface that is powered by Django, I find most PHP code to be the most disgusting. Much like four week old spaghetti.


I think in terms of providing an OpenSource Centralised Office Jukebox with Voting and LDAP authentication... Ampache is the only one.

So my experience with Ampache is this : The interface in terms of User Science(tm) is horrible.

I shouldn't have to refer to a manual on what to click just to get vote based localplay running.

---

### Post by lottes70 on 2012-04-03
I appreciated the detail in this thread, thanks to everyone who has posted so far.

I've been using ampache for a while now, and I installed it because I hated the stock music player on my Palm Pre. The Ampache Mobile app on webOS is FANTASTIC. I can not say the same thing about the android ampache app "amdroid". It works, but could be improved in many ways. If I was already a developer, or if I didn't have 3 young kids, I might go for it...

---

### Post by Xlorep DarkHelm on 2012-04-03
> **samfuzz said:**
> why not using Music Player daemon :

    - multiple output possibility (can be enable:disable by the client) :
            [LIST=1]
[*]- streaming (httpd, icecast) : ogg, mp3, flac , pcm ...
[*]             - pulseaudio, alsa, jack, oss
[*]             - pipe output ...
[/LIST]
    - possibility to browse :
                 [LIST=1]
[*]by folder
[*]                  by tag : genre, artist, album, comment ....
[*]                    (multiple field tag possibility per song : useful for genre, comment field)
[/LIST]
    - internal stickers database (rating ....)
    - and more (replaygain ,playlist .....)


but it lacks a good client that deals with the stickers database for rating, i was trying this one jiggyMPD 
it extends MPD database for adding features MPD clients typically lack, such as ratings, date added, and last played date
[https://bitbucket.org/cubiczee/jiggympd/wiki/Home](https://bitbucket.org/cubiczee/jiggympd/wiki/Home)
(but it seems it can't run with php5.3)

there is also mpdcron client : use stickers database  (CLI)

edit : forget to say (a little off topic) that the best tool that i known  for create multi-criteria playlist,  is gmusicbrowser


Well, I've taken your idea into consideration, and am now using MPD. it does everything I need it to do, and whatever it doesn't do, I've built a python script to do it for me (building my playlist the way I want to). Nice, clean, simple, and just streams my music to me the way I want it to.

---

### Post by mydigitalife on 2013-02-25
[QUOTE=cjssmo;10216103]I personally find Ampache much more flexible than Subsonic.

Just a little comparison from my point of view.

1. Do the respective programs meet Debian/Ubuntu DFSG guidelines?
Ampache == yes
Subsonic == no

2. Are either of the respective programs in the Debian/Ubuntu archives and available via apt-get or aptitude?
Ampache == yes
Subsonic == no

3. Do you have to pay to remove advertisements from either app?
Ampache == no
Subsonic == yes

4. Can you use MPD with either of the respective programs to pipe music to you home stereo?
Ampache == yes
Subsonic == no

5. Can you set up a internet radio station with either app?
Ampache == yes (with icecast)
Subsonic == no

6. Do either apps have DLNA support?
Amapche == yes (with python-coherence)
Subsonic == no

7. Are there apps for other phones such as the palm-pre or blackberry?
Ampache == yes
Subsonic == no

8. Can you use either app as a backend to your favorite media player such a rhythmbox, banshee, or Amarok?
Ampache == yes (with the release of natty, has plugins for all three via apt-get)
Subsonic == no

9. Do either apps have a stand alone media player designed especially for that app?
Amapche == yes (viridian which is available via apt-get)
Subsonic == no

10. Do either app stream video?
Ampache == yes (is still beta and rough around the edges)
Subsonic == no

11.  Will either app handle large collections?
Ampache == yes (the largest I have seen so far is 5.5TB)
Subsonic == unknown

12) Are there any VM appliances that can be run in VMware for either app?
Ampache == yes (VMampache)
Subsonic == no

Just because Ubuntu One chose to use Subsonic does not mean it is the best choice for your personal needs.  All it means is that Subsonic fits better into Ubuntu One's money making infrastructure.

I calculated how much it would cost to host my 1.2TB of music through Ubuntu One and it came out to a staggering $1,827.00 USD per year.

Well that's my $0.02, take it for what it's worth.:D[/QUOTE

I've tried both of them 

My question was : 

Are my users geek ? No

Is Ampache simple to use for a basic music listening ? No, with their music listing (pls, m3u, etc) approach not at all. 

Is Subsonic is simple to us for a basic music listening ? Definitively yes

Do i have to pay for Ampache ? No, and i would not pay for that

Do i have to pay for Subsonic ? It depends on what i want and yes i've paid for their excellence,  a donation of some few bucks. 

Is Subsonic still in progress ? yes
Is ampache  still in progress ? Nope ! 


So my choice is definitively Subsonic who is not an alternative of ampache, no, and Ampache doesn't worth to be known as an alternative of Subsonic.

---

### Post by mydigitalife on 2013-02-25
> **LandRacer said:**
> Subsonic is a joke, and is NOT free!

Well the app on the droid at least. 30-day use period then they want money. Bite me! So don't be deceived with subsonic. That crap is not free, and these guys claim open-source. NOT ON MY SYSTEM. Spit on that garbage! Subsonic also likes to download requested music files to your system/memory card instead of streaming the music. What was the point of setting up a music server to stream, when it downloads? I could transfer files myself thanks.

Try Jinzora, they are in the development stage for the android app. I was looking at that the other day. Jinzora is written in PHP I believe, It works well with my Apache/lamp Web Server. Jinzora also works with my video files, yay! But so does gnump3d< no more development there...

I've used Ampache and lullaby, way better combo then subsonic.

IF you have a newer droid that will play flash, you can also try Sockso. That is a pretty slick music ONLY server for the novice. Which streams music instead of downloading it. I've used Sockso for a long time. Kind of a resource hog though. Wait NOT kind-of, IT IS. BUT it works good!

I guess I really posted to slander Subsonic, what garbage.

Jinzora .... Are you serious ? Does this crap make you believe that you are in perfect way of doing streaming in a stable way ? 

Yes there is few buck to pay to get rid of some aspects of Subsonic, but it worth it. And do we care about the fact that it was written in this, and working on that, and technically is ... and bla bla bla, we don't care !! 

as long as this is the interface is working great, have a lot of potential, who is actually the only one who is still in development,  fun to use for users who are not geeks, for users who simply want music listening. 

So don't make me laugh with your Jingozora

---

### Post by mydigitalife on 2013-02-25
> **LandRacer said:**
> Subsonic is a joke, and is NOT free!

"Try Jinzora, they are in the development stage for the android app".


No you are not serious ? They are in development stage for android, what a good news ! Both Subsonic and ampache made it a long time ago and they are still doing it. There is a lot of app made as well for android than for Apple (iphone, ipad, ipod). So Jinzora are in development stage for the android app ? Hey ! that's so cool ! You seems to be someone not quit not informed about everything else than Gongzora ....

---

### Post by maxime5 on 2014-01-02
Ok I will revive this thread but I think the answer match perfectly the topic. A fork named ampache-doped that improve sensibly ampache was created, see [http://ampache-doped.github.io/](http://ampache-doped.github.io/) . It adds several features that was missing on Ampache and existed on Subsonic, and most of all there is now a Subsonic API compatibility in Ampache. Should put Ampache back in the battle ;)

---

