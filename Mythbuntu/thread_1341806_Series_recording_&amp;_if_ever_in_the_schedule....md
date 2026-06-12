---
title: "Series recording &amp; if ever in the schedule..."
date: 2009-11-30
forum: Mythbuntu
---

### Post by byronmyth on 2009-11-30
Firstly, now that I've gotten past most of the irritations of MythTV, I'm very pleased with the results I'm getting, the Developers deserve a lot of gratitude for the hard work that they put into this program.
 
I've still got a couple of issues relating to HD content viewing in a stuttering manner, but it would seem that there is a patch ([[COLOR=#444444]http://svn.mythtv.org/trac/ticket/7522[/COLOR]]("http://svn.mythtv.org/trac/ticket/7522")) in the pipeline, if this could be released sometime soon please.
 
I was very surprised to see that "Series" recording isn't available in MythTV, is this something that will be added later? 
 
Also it would be nice to have a feature added, that say if a film "Wolf Creek" appears in the schedule, record it.
 
These are both features that MCE has, I need bragging rights over my friend running MCE, so let's have those soon please. :)

---

### Post by SiHa on 2009-11-30
Series link isn't available, but 'Record every week/day in this timeslot' does the job for me, unless the broadcaster moves is by five minutes! Or 'Record whenever on this channel' can be useful.
> Also it would be nice to have a feature added, that say if a film "Wolf Creek" appears in the schedule, record it.
Fairly sure you can do this with a custom record. You can specify a search expression, and it will record anything that matches this. 

Also, there is an unofficial plugin called TVWish for just this, look [[COLOR="Blue"]_here_[/COLOR]](http://www.templetons.com/brad/myth/tvwish.html). Not sure how it would integrate with the new MythUI / 0.22 though.

---

### Post by byronmyth on 2009-11-30
Surely the series link info is included in the EPG info? shouldn't be that hard to tag it I would have thought. Problem is that with some series, they move the time around and series recording sorts that. Of course "record at any time on this channel" can end up with all sorts of unecessary programmes recorded.
 
I'll have a look at the custom recording, see if that helps, yep just looked you are quite correct cheers matey :)

---

### Post by ReddogOne on 2009-12-02
> **byronmyth said:**
> Surely the series link info is included in the EPG info? 

I should imagine it is quite easy. Just guess no one with the correct knowledge or both the series information and mythTv either exists or cares enough to update it.

Would be a great thing to have. Currently have two different series of Scrubs being recorded at once but they call get intermixed. Would be great if sorted by series Id and episode.

Wonder it a simple program exists to see the EPG data to see what format the series and episode information is in.

---

### Post by Flecko on 2009-12-02
I would like to throw my hat in the ring for support of this one. I mean, Tivo has had the "season pass" feature for years, and to be honest, the way you mark a series to record in MythTV has a very low WAF (wife acceptance factor) at my house currently.

My DVR gets jammed up with duplicates and rebroadcasts of shows from other channels.

Anyone heard of a sensible solution to this problem?

---

### Post by nickrout on 2009-12-02
> **Flecko said:**
> I would like to throw my hat in the ring for support of this one. I mean, Tivo has had the "season pass" feature for years, and to be honest, the way you mark a series to record in MythTV has a very low WAF (wife acceptance factor) at my house currently.

My DVR gets jammed up with duplicates and rebroadcasts of shows from other channels.

Anyone heard of a sensible solution to this problem?

yes "record at any time on this channel" or "at any time on any channel" along with duplicate detection (so you don't get the same episode recorded more than once)

---

### Post by t3chn0b0y on 2009-12-03
> **byronmyth said:**
> Firstly, now that I've gotten past most of the irritations of MythTV, I'm very pleased with the results I'm getting, the Developers deserve a lot of gratitude for the hard work that they put into this program.
 
I've still got a couple of issues relating to HD content viewing in a stuttering manner, but it would seem that there is a patch ([[COLOR=#444444]http://svn.mythtv.org/trac/ticket/7522[/COLOR]]("http://svn.mythtv.org/trac/ticket/7522")) in the pipeline, if this could be released sometime soon please.
 
I was very surprised to see that "Series" recording isn't available in MythTV, is this something that will be added later? 
 
Also it would be nice to have a feature added, that say if a film "Wolf Creek" appears in the schedule, record it.
 
These are both features that MCE has, I need bragging rights over my friend running MCE, so let's have those soon please. :)



It probably wouldn't be very hard to incorporate a season pass
like feature..


But in the schedule recordings, there is a custom record settings
that has alot of power once one can learn to use it, that gives
more power then said MCE.. Ahh the power of Sql makes me druel with
excitement..

Rule Name: The Simpsons (New Episodes)
program.title = 'The Simpsons'
AND program.previouslyshown = 0

The above will record all the new simpson episodes no
matter what time, or channel the show comes on.

so if the show changes channel, or time you will not miss your
episode..

TV Wish that has been discussed uses a rating based system which one can find on many sites for the episodes in a series,and that way you can record only the highest rating episodes, But it can also be used with a list of Movies that one wants to watch before they die for example.. and will schedule those recordings once they appear in the guide.

I like to use a site called Jinni to get a listing of similar movies to a movie I like, and I will create a list based on that those similarities and use that with the TVWish.. Jinni is based on genome much like Pandora radio. 

If you only wanting a given season to be recorded you could create a
list of the episodes in a text file for TVWish and when they come on
it will record just that season for you, that way also.. and one can get the names of
the episodes of the shows from TheTVdb.

Anywayz just food for thought...	:lolflag:

---

### Post by byronmyth on 2009-12-03
> Ahh the power of Sql makes me druel with
excitement..

Rule Name: The Simpsons (New Episodes)
program.title = 'The Simpsons'
AND program.previouslyshown = 0
 
Fantastic for us, but for getting wives/girlfriends who just want their series to record, forget it! Series recording is a one click "no brainer"....

---

### Post by ReddogOne on 2009-12-04
> **nickrout said:**
> yes "record at any time on this channel" or "at any time on any channel" along with duplicate detection (so you don't get the same episode recorded more than once)

A good solution if you start watching from the very first airing of the first episode of the first series. Otherwise it is prone to failure say when they show series one in the morning and then series two in the evening... because the series all get mixed up. 

Using the series information (available on UK TV and probably others) would be just the icing on the cake. 

Currently all the million and one configurations of mythTv are confusing to the 'just want to watch TV; crowd. A simple to use record show or series or all [still sorts by series] would be brilliant.

Also by using such things as the series and episode numbers you can do things like: Half was through the second series someone tells you of a great series but you MUST watch it from the beginning. So you select to record it [but all recording]. It starts recording from that point but when they do [for example] the catchup some weekend it gets you the missing programs from episode 1 series 1 but orders them nicely so you can start watching in order!

Very cool. This is what DirecTV does. Not that I live in USA but worked on the Software.

---

### Post by ReddogOne on 2009-12-04
> **byronmyth said:**
> Fantastic for us, but for getting wives/girlfriends who just want their series to record, forget it! Series recording is a one click "no brainer"....

Can't you just select "Record at any time on any channel."? In fact in the guide Record twice and you'll get the "A" for all! Duplicate detection is on by default (though can be adjusted).

---

### Post by Flecko on 2009-12-06
I didn't meant to say that MythTV doesn't have this functionality, it cetainly does. What I am saying is that my wife was more than capable of recording a series using a Comcast or DirectTV DVR, but fails with my MythTV DVR because the wording is extremely confusing.

To a layperson, the phrase "record at any time on any channel" doesn't sound like duplicates would be excluded, or reruns, or anything like that. And as you're probably aware, shows like House are syndicated across multiple carriers, so it sounds like it would get duplicates, non-HD feeds, and reruns to my wife.

It's possible for the recording dialog to have the very same amount of power and flexibility it has now, but yet also be user friendly. I was just saying that it's something that I'd love to see changed, thats all. MythTV is extremely powerful, but I just get the feeling that it wasn't made with the wives in mind, thats all ;)

---

### Post by ReddogOne on 2009-12-07
> **Flecko said:**
> it wasn't made with the wives in mind, thats all ;)

I'd say MythTV is overly complicated. Probably because its developed my DTV fanatics for DTV digital fanatics and its not attracted enough UI design and usability people.

But its so close... like all open source its hard for people to get excited enough (with the right skills) to removed all the complicated (mostly) unwanted bits and bobs.

Its also just unfortunate that the first response/answer you usually find is the complicated (jump through a hoop) rather than the much more wife friendly press record twice in the guide. Which always seems to be a problem with Linux et al. 

I'd love to see a cut down UI that is simple, easy to use and stable. I'd also like to have the time to do it myself. 

A some probably simple to improve things like recorded programs be listed and selected so the oldest is at the top. Who watches a series in reverse order so why list it that way.

---

### Post by nickrout on 2009-12-07
Well the place to make such suggestions is the mythtv-users mailing list!

---

### Post by ReddogOne on 2009-12-08
> **nickrout said:**
> Well the place to make such suggestions is the mythtv-users mailing list!

Thanks, joined and ready to make some suggestions (and hopefully not upset anyone).

---

### Post by Flecko on 2009-12-08
I began looking into seeing if this can be taken care of by altering the theme. Not sure yet, but if I find anything I'll be sure to let everyone know.

All it would really require is rewording the way the recording is done.

---

### Post by nickrout on 2009-12-08
> **Flecko said:**
> I began looking into seeing if this can be taken care of by altering the theme. Not sure yet, but if I find anything I'll be sure to let everyone know.

All it would really require is rewording the way the recording is done.

The sceduler is a complex beast,. much more so than the scheduler in any of the competing products!

One problem is that the epg info does not always have series and episode data in terms of numbers (eg series 2 episode3) it more often just has an episode title (eg "The One Where Heckles Dies") and description (eg "After Mr. Heckles dies and leaves all his belongings to Monica and Rachel, Chandler discovers eerie similarities between the late eccentric man and his own life. Ross and Phoebe have a dispute over the progression of evolution.")

---

### Post by t3chn0b0y on 2009-12-08
> **ReddogOne said:**
> 

I'd love to see a cut down UI that is simple, easy to use and stable. I'd also like to have the time to do it myself. 

A some probably simple to improve things like recorded programs be listed and selected so the oldest is at the top. Who watches a series in reverse order so why list it that way.


So your saying you want a what you see is what you get media center, where people like myself who like to be able to do things his own way would not have the ability to do so, because of a group of people that don't like their software to be complex.. I came to mythtv because of that complexity.. if one was to remove the ability to create custom record rules for example, and one was stuck with just a few presets then someone like myself wouldn't be able to customize it to his liking. 

take for example looking for movies with a particular actor and actress in the movie, and I want the movie to be by a given director, and lets say I dont want the movie to be recorded in prime time, and  I want the commericals removed, and I want it converted into xvid, and I want it transfered over to an external hard drive, which could be taken out to the living room and attached to portable media player for everyone to watch, and I want it to be converted between given hours, which is the time the hard drive would be attached to the pc.

a wysiwyg system works great for some, but I prefer to have my freedom to go about doing as I want to my settings, and how I want to go about using the media instead of what someone else thinks would be a perfect MythBox. But since everyone is different.. that perfect media center would be impossible without the complexity of customization.

perhaps some one can create a script to compile the code that adds and removes features to suit the given specific users needs & complexity.

---

### Post by t3chn0b0y on 2009-12-08
> **Flecko said:**
> To a layperson, the phrase "record at any time on any channel" doesn't sound like duplicates would be excluded, or reruns, or anything like that. And as you're probably aware, shows like House are syndicated across multiple carriers, so it sounds like it would get duplicates, non-HD feeds, and reruns to my wife.

It's possible for the recording dialog to have the very same amount of power and flexibility it has now, but yet also be user friendly. I was just saying that it's something that I'd love to see changed, thats all. MythTV is extremely powerful, but I just get the feeling that it wasn't made with the wives in mind, thats all ;)


I hear ya with the layperson, and the phrasing within Myth,
It took me quiet awhile to get use to it, and sometimes Im still finding myself a bit surprised about a feature from time to time because of the wording. But as I previously brought up, a script that can create needed patches and patch the source to change things like the wording, and add & remove features would be very nice.. and possibly with a GUI.. this would of course mean that one would have to be willing to compile the code oneself.

some of the terms and the layout can be changed a bit within the themes.. take for example the theme mepo.. the wordings where changed to say things like "seasonal pass".. which has not been converted over to 0.22 as of yet.. I started to work on the old patch and try to bring it up to date about a week ago, and set it aside because of a few other things that came up in my life.. and I might get back to it..

---

### Post by ReddogOne on 2009-12-09
> **t3chn0b0y said:**
> So your saying you want a what you see is what you get media center, where people like myself who like to be able to do things his own way would not have the ability to do so, because of a group of people that don't like their software to be complex.. I came to mythtv because of that complexity.. if one was to remove the ability to create custom record rules for example, and one was stuck with just a few presets then someone like myself wouldn't be able to customize it to his liking. 

No what I said is I would like to see a cut down VERSION... not we should only have a cut down version. I'd wager most want TV to be simple and just work.

> **t3chn0b0y said:**
> 

snip

perhaps some one can create a script to compile the code that adds and removes features to suit the given specific users needs & complexity.

Brilliant Idea and just what I think the doctor would order!

---

### Post by nickrout on 2009-12-09
> **ReddogOne said:**
> No what I said is I would like to see a cut down VERSION... not we should only have a cut down version. I'd wager most want TV to be simple and just work.



Brilliant Idea and just what I think the doctor would order!

so you want to fork mythtv? good luck!

---

### Post by ReddogOne on 2009-12-10
> **nickrout said:**
> so you want to fork mythtv? good luck!

Well no, not sure I said I wanted anything like that. Would have thought all that was required was a theme and maybe a bit of configuration to make life easy for the majority.

---

### Post by nickrout on 2009-12-10
If you seriously want to raise that as a proposed feature enhancement, post to the mailing list. Thats where feature requests go.

---

### Post by matt06 on 2009-12-10
> **ReddogOne said:**
> I'd say MythTV is overly complicated. Probably because its developed my DTV fanatics for DTV digital fanatics and its not attracted enough UI design and usability people.
I like Myth's complexity.  Complexity + power = control (or something like that).
> **ReddogOne said:**
> I'd love to see a cut down UI that is simple, easy to use and stable.
Not necessarily a cut-down UI, but you could certainly group sets of options or some of the menus into "basic" or "advanced" categories and ask during install if you want "Basic" or "Advanced" control and UI.  Of course it should be selectable, similar to picking a theme, you would be picking a UI complexity and control level.  Someone could even put together a theme "cloning" the Tivo look and control (not so much as to infringe) and install could ask if you want your box to look like a Tivo as much as possible.  Anything to get additional WAF is usually always a good thing ;)

The UI does need some, hmm, consistency in some places as far as keywords, phrases and other elements.  For example, scheduling a program using mythfrontend vs. mythweb is quite a different UI experience.  But that has nothing to do with the complexity of the scheduling facility running behind the scenes, which is what gives Myth such great power and control!

---

### Post by gbutters on 2009-12-11
> **ReddogOne said:**
> 
A some probably simple to improve things like recorded programs be listed and selected so the oldest is at the top. Who watches a series in reverse order so why list it that way.

You can control how the recorded programs are displayed. This is changed in setup under TV Settings -> Playback on screen 4.

---

### Post by ReddogOne on 2009-12-12
> **matt06 said:**
> I like Myth's complexity.  Complexity + power = control (or something like that).

Unfortunately Complexity + power also tend to equal inconsistency, bugs, confusion and frustration. 

Configurations often don't play well together, bugs are hard to determine and people will leave because they can't find that special option that'll make the system easier to use or use at all.

MythTV is well brilliant but I think its probably loosing because of some needed fine tuning in ease of use and convention over configuration.

---

### Post by ReddogOne on 2009-12-12
> **gbutters said:**
> You can control how the recorded programs are displayed. This is changed in setup under TV Settings -> Playback on screen 4.


Brilliant and thanks, been though screens a number of times and totally missed it.

---

