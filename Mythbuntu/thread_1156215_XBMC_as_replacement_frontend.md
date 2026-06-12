---
title: "XBMC as replacement frontend"
date: 2009-05-11
forum: Mythbuntu
---

### Post by NTolerance on 2009-05-11
I'm running Mythbuntu Hardy on a combined backend/frontend/desktop system.  It's mainly used to record and play back shows as well as play Xvid videos using MythVideo.  

XBMC 9.04 has been getting lots of praise and I wonder if it's worth looking into as a replacement for the MythTV frontend.  

Does it work well with an MCE remote?  Is this something worth trying or should I stick with the stock frontend?  I found a PPA for Hardy right here:

[https://launchpad.net/~team-xbmc/+archive/hardy-ppa](https://launchpad.net/~team-xbmc/+archive/hardy-ppa)

Here are some features that my Hardy setup lacks and that I hope would be available in XBMC:

1.  Ability to delete Xvid videos from frontend menu
2.  Ability to resume Xvid videos from last watched position

---

### Post by Boppy3125 on 2009-05-11
I have been considering this recently too.  I just ran across this link today and am very interested:

[http://code.google.com/p/mythbox/](http://code.google.com/p/mythbox/)

I really need to find some time to work on this, because I think it will have to beat the myth frontend for usability.  I am thinking if I get this working I would look into making the standard MythFrontend a program link available from the XBMC menu just in case I need it.

Thanks for the link on the ppa, I will hopefully use that later this week.

---

### Post by nickrout on 2009-05-11
> **NTolerance said:**
> 
2.  Ability to resume Xvid videos from last watched position

mythfrontend has this ability if you use the Internal player.

Having said that I am seriously looking at doing the same.

Music is so much better in XBMC for one thing!

---

### Post by nunrgguy on 2009-05-12
xbmc as a front end works great on linux. On the xbox itself, In my instance, it works great as a front end with the proviso that the video has to be transcoded first, the NIC in the xbox isn't quick enough.
At the moment what you get is like a folder and file view and AFAIK program guide isn't working yet. Apart form that, on Linux it works great, and for the other features that xbmc was originally made for, fantastic, much better than myth front end in that respect.
MCE remote will also work straight out of the box if you install on top of mythbuntu.
I've got the ppa installed and the only niggle I've had is w.r.t only being able to do partial upgrades if the xbmc software sources are selected, whether keys are added or not. Stil trying to sort that out.

---

### Post by NTolerance on 2009-05-12
> **nunrgguy said:**
> xbmc as a front end works great on linux. On the xbox itself, In my instance, it works great as a front end with the proviso that the video has to be transcoded first, the NIC in the xbox isn't quick enough.
At the moment what you get is like a folder and file view and AFAIK program guide isn't working yet. Apart form that, on Linux it works great, and for the other features that xbmc was originally made for, fantastic, much better than myth front end in that respect.
MCE remote will also work straight out of the box if you install on top of mythbuntu.
I've got the ppa installed and the only niggle I've had is w.r.t only being able to do partial upgrades if the xbmc software sources are selected, whether keys are added or not. Stil trying to sort that out.

Thanks for the info.  I don't watch live TV on MythTV and I use Mythweb for all my program guide needs.  All I really want is playback, deletion, and commercial skip capabilities.

---

### Post by Boppy3125 on 2009-05-13
I heard that commercial skip on playback doesn't work with XBMC.  The plugin I linked above says it can do that though, anyone know from experience?

---

### Post by nunrgguy on 2009-05-13
ATM playback and deletion work great. Commercial skipping not yet implemented.

---

### Post by newlinux on 2009-05-13
I just run both. Have a button that exits one app and opens the other. I watch recordings in myth, and pull up XBMC when I want to do music or show off my vid collection. Pictures work fine for me in either one.

I use a harmony remote (emulating MCE remote) with a MCE receivers on all my frontends.

---

### Post by ohzopants on 2009-08-17
I'm considering setting up myth on my PC (I'm waiting on 0.22 for the hauppauge hd-pvr support so that i can record HD off my dish).  Currently I use XBMC, and I simply love it.

I've been reading everything I can find about using xbmc as a myth frontend and the only thing sort of bugging me is that it there doesn't seem to be a way to use xbmc's main video library (which is f*ing awesome) to browse myth recordings.  Has anyone been able to do this?

I already have a bunch of TV shows ripped from DVD backed up on my PC and I use XBMC's library to browse them and it would be a shame to have two differrent "libraries" for TV shows.

---

### Post by nickrout on 2009-08-17
Use mythrename to set up meaningful names for your recordings, then browse the directory with the renamed files.

---

### Post by NTolerance on 2009-08-17
> **newlinux said:**
> I just run both. Have a button that exits one app and opens the other. I watch recordings in myth, and pull up XBMC when I want to do music or show off my vid collection. Pictures work fine for me in either one.

I use a harmony remote (emulating MCE remote) with a MCE receivers on all my frontends.

I'd love to see your scripts for exiting one frontend and starting another.  Is there a way to do a graceful XBMC/Myth frontend exit via a shell script?  I don't want to kill processes mercilessly.  

Oh, and BTW I have been using XBMC as a MythTV frontend.  It's not a replacement at this point.  It trumps MythTV on features for sure, but there are some bugs such as intermittent lockups, improper reporting of MythTV recording filesizes, and failure to fast forward/rewind during playback of ATSC recordings.

---

### Post by NTolerance on 2009-08-17
> **ohzopants said:**
> I'm considering setting up myth on my PC (I'm waiting on 0.22 for the hauppauge hd-pvr support so that i can record HD off my dish).  Currently I use XBMC, and I simply love it.

I've been reading everything I can find about using xbmc as a myth frontend and the only thing sort of bugging me is that it there doesn't seem to be a way to use xbmc's main video library (which is f*ing awesome) to browse myth recordings.  Has anyone been able to do this?

I already have a bunch of TV shows ripped from DVD backed up on my PC and I use XBMC's library to browse them and it would be a shame to have two differrent "libraries" for TV shows.

I might not fully understand your question, but are you using the [myth::](http://www.mythtv.org/wiki/Xbox_Frontend#Add_MythTV_as_a_Video_Source) video source configuration?  If that is set up properly it will pull the human-readable show titles from the MythTV mySQL database.

---

### Post by newlinux on 2009-08-17
> **NTolerance said:**
> I'd love to see your scripts for exiting one frontend and starting another.  Is there a way to do a graceful XBMC/Myth frontend exit via a shell script?  I don't want to kill processes mercilessly.  

Oh, and BTW I have been using XBMC as a MythTV frontend.  It's not a replacement at this point.  It trumps MythTV on features for sure, but there are some bugs such as intermittent lockups, improper reporting of MythTV recording filesizes, and failure to fast forward/rewind during playback of ATSC recordings.

yeah, I don't like using it as a frontend for myth, I found it buggy, and missing too many myth features.

My scripts check for and kill the processes... nothing fancy about them. Suppose you could use irsend with XBMC's shutdown command (I have a button mapped to just turn off xbmc too via it's shutdown command). not show about myth.

---

### Post by kadafi69 on 2009-08-18
> **NTolerance said:**
> I'd love to see your scripts for exiting one frontend and starting another.  Is there a way to do a graceful XBMC/Myth frontend exit via a shell script?  I don't want to kill processes mercilessly.


All I did was create a new item on the MythTv main menu, called it XBMC, when selected it runs xbmc, leaving MythTV on in the background. When I close XBMC, MythTV comes back to the foreground. Works pretty seamlessly for me. If thats the kinda thing your after?

The only trouble im having is getting my Streamzap remote to work with XBMC (but im considering getting a new remote anyway). Also had a bit of trouble getting the MythBox script to work properly.

---

### Post by nickrout on 2009-08-18
> **kadafi69 said:**
> All I did was create a new item on the MythTv main menu, called it XBMC, when selected it runs xbmc, leaving MythTV on in the background. When I close XBMC, MythTV comes back to the foreground. Works pretty seamlessly for me. If thats the kinda thing your after?



Exactly, there is no need to kill mythtv, just run xbmc from a menu item.

My menu item says

<button>
        <type>XBMC_CLIENT</type>
        <text>XBMC</text>
        <action>EXEC xbmc</action>
</button>

---

### Post by newlinux on 2009-08-18
> **nickrout said:**
> Exactly, there is no need to kill mythtv, just run xbmc from a menu item.

My menu item says

<button>
        <type>XBMC_CLIENT</type>
        <text>XBMC</text>
        <action>EXEC xbmc</action>
</button>


Yep that works. The menu button is less seamless for my users because I want them to press an activity button on my harmony remote (I modify what keys are mapped to what irsignal they send when in XBMC activity as opposed to the Mythtv activity for convenience, and the XBMC activity also changes the softmenu labels). But I could have the remote spawn XBMC upon changing to XBMC and issue the shutdown command upon exiting the XBMC activity as opposed to killing processes...

---

### Post by ohzopants on 2009-08-18
> **NTolerance said:**
> I might not fully understand your question, but are you using the [myth::](http://www.mythtv.org/wiki/Xbox_Frontend#Add_MythTV_as_a_Video_Source) video source configuration?  If that is set up properly it will pull the human-readable show titles from the MythTV mySQL database.

That's what I **plan** on using, but from what I've read on various forums is that Myth relies primarily on a show's airdate for it's metadat whereas XBMC uses season/episode info in the file name itself.  Apparently this can lead to problems in importing the files properly into XBMC.

---

### Post by NTolerance on 2009-09-04
Anyone had XBMC completely lock up their system?  It's hosed mine so bad that while you can SSH into the system, it doesn't respond to kill or shutdown commands.  Have to do a hard reset with the reset button.  :(

---

### Post by williammanda on 2009-09-06
I tried XBMC yesterday and found the following:
1. XBMC itself has a great user graphic interface but without a backend for live tv or recording tv....it seems worthless.
2. XBMC with mythtv as a source is very lacking in features and buggy.
3. XBMC with mythbox is a little better than XBMC with mythtv but still lacking features of a mythfrontend and still buggy. Several times when selecting a recording XBMC would quit.

I would like to see mythtv incorporate XBMC graphical interface.
Thanks

---

### Post by nickrout on 2009-09-06
> **williammanda said:**
> I tried XBMC yesterday and found the following:
1. XBMC itself has a great user graphic interface but without a backend for live tv or recording tv....it seems worthless.
2. XBMC with mythtv as a source is very lacking in features and buggy.
3. XBMC with mythbox is a little better than XBMC with mythtv but still lacking features of a mythfrontend and still buggy. Several times when selecting a recording XBMC would quit.

I would like to see mythtv incorporate XBMC graphical interface.
Thanks

Have you tried mythtv 0.22?

---

### Post by williammanda on 2009-09-06
No I'm still using .21. Is there a feature for a better GUI? IF so where is the info?
Thanks

---

### Post by williammanda on 2009-09-06
Ok I found it. I didn't realize they post the changes. The UI changes look promising. Here's what I reviewed.

[http://www.mythtv.org/wiki/Theme_Terra]("http://www.mythtv.org/wiki/Theme_Terra")

[http://www.mythtv.org/wiki/MythUI_Demo_Theme]("http://www.mythtv.org/wiki/MythUI_Demo_Theme")

---

### Post by bgiannes on 2009-10-12
I've been using XBMC for +8months, (on my HTPC ubuntu 9.04, 40" HDTV) last week i install a mythtv-backend w/ a HDHomeRun, then config XBMC native support.  ie myth://user:password@IP as a source, OTA only!  

I'd install mythtv-frontend after that, as i needed to do config's.  However i do like mythweb, and use that to program the TVshow/movie stuff.

With xbmc's del and renaming turned on i can del any show i'm finish with.

I also install mythbox, which is a project that took over from xbmcmythtv (now dead?).  It's bugy but it mostly works.  You can setup new shows to record with it, and view a timetable.  But again the mythweb is better.

The mythtv-frontend is good, but it's mythvideo plugin, and metadata is just bad, i just don't have the time to correct the metadata and art-work on ea movies i have.  Not after i have everything looking so sexy in xbmc!

XBMC has a big team so i Hope they will do more with native mythtv support. ie More show info in the recording dir, with original aired date!, full info please. A live guide in live TV, quicker ch changes, (but i can just use the TV for live tv so i don't care about that really).

So as is, (no builds just default installs) mythtv-backend with mythweb, and XBMC as a myth-frontend is a very cool work-able solution.  

ps, this week I will be un-sub from tivo!

my2cents

---

### Post by NTolerance on 2009-10-12
> **bgiannes said:**
> I've been using XBMC for +8months, (on my HTPC ubuntu 9.04, 40" HDTV) last week i install a mythtv-backend w/ a HDHomeRun, then config XBMC native support.  ie myth://user:password@IP as a source, OTA only!  

I'd install mythtv-frontend after that, as i needed to do config's.  However i do like mythweb, and use that to program the TVshow/movie stuff.

With xbmc's del and renaming turned on i can del any show i'm finish with.

I also install mythbox, which is a project that took over from xbmcmythtv (now dead?).  It's bugy but it mostly works.  You can setup new shows to record with it, and view a timetable.  But again the mythweb is better.

The mythtv-frontend is good, but it's mythvideo plugin, and metadata is just bad, i just don't have the time to correct the metadata and art-work on ea movies i have.  Not after i have everything looking so sexy in xbmc!

XBMC has a big team so i Hope they will do more with native mythtv support. ie More show info in the recording dir, with original aired date!, full info please. A live guide in live TV, quicker ch changes, (but i can just use the TV for live tv so i don't care about that really).

So as is, (no builds just default installs) mythtv-backend with mythweb, and XBMC as a myth-frontend is a very cool work-able solution.  

ps, this week I will be un-sub from tivo!

my2cents

Your comment about the Mythvideo plugin is spot-on.  I was reading the changelog for Mythvideo 0.22 and there are a bunch of new features but still no delete function!

Not being able to delete videos from my remote was the primary reason I even installed XBMC.  

The answer to this from the Mythvideo side is that the plugin was only intended for permanently-stored DVD rips.  I guess it's surprising that someone would want to play something other than a DVD rip on their TV.  I mean, who would care about watching TV shows, music videos or any of that nonsense?  :confused:

---

### Post by nickrout on 2009-10-12
> **NTolerance said:**
> Your comment about the Mythvideo plugin is spot-on.  I was reading the changelog for Mythvideo 0.22 and there are a bunch of new features but still no delete function!

Not being able to delete videos from my remote was the primary reason I even installed XBMC.  

The answer to this from the Mythvideo side is that the plugin was only intended for permanently-stored DVD rips.  I guess it's surprising that someone would want to play something other than a DVD rip on their TV.  I mean, who would care about watching TV shows, music videos or any of that nonsense?  :confused:

Have you requested this feature? Have you written the code? Have you submitted a bug report with your patch?

Frankly most stuff in my videos directory is stuff I probably want to watch again and again, and which different members of the family might want to watch at different times.

If I want to get rid of it I can use rm. I can see the utility of delete from the remote, but its certainly not a killer feature!

---

### Post by bcg30506 on 2009-10-12
I've tried xbmc as a frontend for myth and actually prefer mythfrontend.  It seems snappier and the video quality watching TV in xbmc was far worse.

---

### Post by NTolerance on 2009-10-12
> **nickrout said:**
> Have you requested this feature? Have you written the code? Have you submitted a bug report with your patch?

Frankly most stuff in my videos directory is stuff I probably want to watch again and again, and which different members of the family might want to watch at different times.

If I want to get rid of it I can use rm. I can see the utility of delete from the remote, but its certainly not a killer feature!

Negative sir.  I do not write code, but I do file bug reports.  Unfortunately, MythTV's "trac" system is heavily developer-oriented.  It's not like Launchpad or Bugzilla where it's easy for normal users to report their issues or feature requests.  

There are some listings in their system that indicate some sort of delete function has been written.  Hopefully the changelog I saw was outdated and delete will make its way into 0.22.

Not everyone has the time or software awareness to file bug reports.  I don't think it should be a prerequisite to sharing opinions with users at this forum.

---

### Post by nickrout on 2009-10-12
> **NTolerance said:**
> Negative sir.  I do not write code, but I do file bug reports.  Unfortunately, MythTV's "trac" system is heavily developer-oriented.  It's not like Launchpad or Bugzilla where it's easy for normal users to report their issues or feature requests.  

There are some listings in their system that indicate some sort of delete function has been written.  Hopefully the changelog I saw was outdated and delete will make its way into 0.22.

Not everyone has the time or software awareness to file bug reports.  I don't think it should be a prerequisite to sharing opinions with users at this forum.

Just reminding you of the standard response in open source projects to user requests :)

Seriously though, those who use open source projects (a) shouldn't complain if it doesn't work as they want, and (b) should be prepared to take the time to report bugs and feature requests. I know not everyone is a coder. Opinions always welcome of course.

Cheers, Nick.

---

### Post by bgiannes on 2009-10-13
One big problem i'm having with xbmc frontend is that the wife (very non-techy) has trouble using the XBMC interface, she gets stuck in the menus?? :( and saids the system gets stuck/hangs?  

So I'm going to try and train her on mythtv-frontend.  It's more basic so fingers crossed.


Note:
xbmc 'Full HD' playback seems to develop a audio sync problem after ~10 minutes play?  If i try and set a audio off-set (mid play) the picture start falling apart, and becomes un-watchable.

mythtv don't seem to have this problem?

---

### Post by tgm4883 on 2009-10-13
Did anyone actually check Mythvideo in 0.22? You can totally delete videos from there.

---

### Post by NTolerance on 2009-10-13
> **bgiannes said:**
> One big problem i'm having with xbmc frontend is that the wife (very non-techy) has trouble using the XBMC interface, she gets stuck in the menus?? :( and saids the system gets stuck/hangs?  

So I'm going to try and train her on mythtv-frontend.  It's more basic so fingers crossed.


Note:
xbmc 'Full HD' playback seems to develop a audio sync problem after ~10 minutes play?  If i try and set a audio off-set (mid play) the picture start falling apart, and becomes un-watchable.

mythtv don't seem to have this problem?

Yes, as I reported earlier in this thread, XBMC 9.04 has lockup issues, making it unusable for me.  

Actually I find the interface in XBMC superior when it works.  One UI thing in MythTV that's always baffled me is that you can't drill into a show/video submenu by selecting it with the OK button on your remote (analogous to the ENTER key).  Rather, you have to hit the RIGHT arrow key on your remote to get there.  Quite odd.  I've never used another "set-top box" that worked this way.

---

### Post by NTolerance on 2009-10-13
> **tgm4883 said:**
> Did anyone actually check Mythvideo in 0.22? You can totally delete videos from there.

Sweet!  :guitar:

---

### Post by tgm4883 on 2009-10-13
> **NTolerance said:**
> Yes, as I reported earlier in this thread, XBMC 9.04 has lockup issues, making it unusable for me.  

Actually I find the interface in XBMC superior when it works.  One UI thing in MythTV that's always baffled me is that you can't drill into a show/video submenu by selecting it with the OK button on your remote (analogous to the ENTER key).  Rather, you have to hit the RIGHT arrow key on your remote to get there.  Quite odd.  I've never used another "set-top box" that worked this way.

You can't even hit the right arrow key anymore. On the MCEUSB2 remote, you hit the i key (for info)

It might be that way on 0.21 too for the i key, I don't have a system to test on though.

:EDIT:

I also don't think that would make XBMC superior to the MythTV frontend though. Maybe you should just list everything you prefer in XBMC over MythTV, rather than string us along for so long.

---

### Post by nickrout on 2009-10-13
> **NTolerance said:**
> Yes, as I reported earlier in this thread, XBMC 9.04 has lockup issues, making it unusable for me.  

Actually I find the interface in XBMC superior when it works.  One UI thing in MythTV that's always baffled me is that you can't drill into a show/video submenu by selecting it with the OK button on your remote (analogous to the ENTER key).  Rather, you have to hit the RIGHT arrow key on your remote to get there.  Quite odd.  I've never used another "set-top box" that worked this way.

What each button does is programmable. How many other STB's have thta feature?

---

### Post by NTolerance on 2009-10-13
> **tgm4883 said:**
> Maybe you should just list everything you prefer in XBMC over MythTV, rather than string us along for so long.

I'm sorry that some people in this thread do not like my comments or how this thread has developed, but I tihnk that software usability assessments take time.  You can't fire a program up in a single sitting and point out every feature that works counter-intuitively.  If it were this easy every revision 1.0 would be easy and natural to use.  But you and I know that isn't how things work.

---

### Post by NTolerance on 2009-10-13
> **nickrout said:**
> What each button does is programmable. How many other STB's have thta feature?

Are you referring to key bindings within MythTV or LIRC?  Sure, those can be changed.  I could re-bind my enter key to be the right arrow key, but obviously this would have disastrous consequences for many other functions.  

If you know something about configuring this setup that I don't, please help me out.  I'm quite curious.

---

### Post by nickrout on 2009-10-13
> **NTolerance said:**
> Are you referring to key bindings within MythTV or LIRC?  Sure, those can be changed.  I could re-bind my enter key to be the right arrow key, but obviously this would have disastrous consequences for many other functions.  

If you know something about configuring this setup that I don't, please help me out.  I'm quite curious.

I don't play with my keybindings or lirc bindings very much at all. You can play with either. The myth ones are accessible in the menus somewhere, or in mythweb. Oh and different distros do things different too. In mythbuntu on my MCE remote the stop button reverses back up the menus. In knoppmyth the <- button does the same. Moving from knopp to buntu was confusing!

I have to say that switching to XBMC (which i do use a lot for videos and music) from Myth, I find the way the remote works in XBMC to be counterintuitive. I guess its a matter of what you are used to.

---

### Post by tgm4883 on 2009-10-13
> **NTolerance said:**
> Are you referring to key bindings within MythTV or LIRC?  Sure, those can be changed.  I could re-bind my enter key to be the right arrow key, but obviously this would have disastrous consequences for many other functions.  

If you know something about configuring this setup that I don't, please help me out.  I'm quite curious.

The keybindings are context sensitive, so if you hit the enter key while in mythvideo, it should have no affect on other items (exception being global keybindings)

---

