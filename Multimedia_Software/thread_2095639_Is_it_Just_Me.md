---
title: "Is it Just Me?"
date: 2012-12-17
forum: Multimedia Software
---

### Post by PaulyWally on 2012-12-17
Is it just me?  Or did Ubuntu lose more than 50% of it's multimedia usability with 12.04?





I don't mean to rant, but I'm kinda pissed.  This is NOT the way a company successfully evolves a product.

I do a lot of video/audio work as part of the way I make a living. And I have always been happy using Ubuntu as one of the tools for the job.

Until 12.04

When I upgraded, I had been generally pleased with it.  Then I started actually working in the new system.

The first thing I noticed is that the developers decided ffmpeg is not the future of Ubuntu.  All of a sudden, all my GUI tools that rely on ffmpeg will not work.

So I searched, and searched, and searched.  What I found was that Cononical not only had set their sights on the 'avconv' package, but they made it near impossible for the ordinary user to revert to ffmpeg.  To sum up:  avconv = the future of Ubuntu.  But what I found is that avconv is not compatible with any of the GUI tools that can be downloaded in the official Ubuntu repositories.  They rely on ffmpeg.

...in the **_OFFICIAL_** Ubuntu Repositories.

Well... you didn't think that one through.  Did ya?

So after spending 4+ hours researching any possible fixes to my problem, I managed to install ffmpeg by hand and point my most-used GUI tools to that package.  I wasn't happy about it... but life goes on.

Right at this moment, I'm trying to rip video segments off a client's DVD using one of my most favored tools for that job (acidrip). The resulting video tracks look horrendous, and the audio stream is out of sync because of skips in the video stream.  i.e. - no way to fix that with any muxer.

I tried downloading 2 or 3 other tools that either don't fit my needs the way acidrip did, or they crash whenever they decide my simple requests have become too annoying.

All-in-all, the things I used Ubuntu for the most, have become cumbersome or unusable.  And I'm starting to feel that this is some kind of joke Cononical is playing on its users.

---

### Post by evilsoup on 2012-12-17
Installing 'proper' ffmpeg is as easy as [adding a PPA](https://launchpad.net/~jon-severinsson/+archive/ffmpeg), but you shouldn't even need to do that: in 12.04, ffmpeg is effectively an alias of avconv, any program that calls ffmpeg by name should work with avconv.

I can't speak for acidrip, though. Personally, I rip an ISO with Brasero (the only useful thing that brasero can do reliably in my experience), and then convert it to MP4/MKV with Handbrake (from [this PPA](https://launchpad.net/~stebbins/+archive/handbrake-releases)). That may or may not be suitable for your needs though, you'd have to be more specific as to what you're using it for.

Generally, if you can't find an answer in half an hour of googling around, it's best to just ask about your problem here, or at askubuntu.com.

---

### Post by andrew.46 on 2012-12-17
Not so much a decision by *Canonical* as a decision by the packager of FFmpeg who decided to go with the fork avconv. I am sure that everybody would be happier if the developers of avconv and FFmpeg healed the rift...

---

### Post by evilsoup on 2012-12-17
Well yes, but that's not much help to the end-users, is it?

---

### Post by andrew.46 on 2012-12-17
> **evilsoup said:**
> Well yes, but that's not much help to the end-users, is it?

I agree completely, the end-user has not done well with all of the squabbling :(

---

### Post by evilsoup on 2012-12-17
Yeah. It's fairly easily solved, but it's an annoyance up with which people should not have to put.

---

### Post by FakeOutdoorsman on 2012-12-17
> **PaulyWally said:**
> Is it just me?

Welcome to the club. I am a member too. See [Who can tell me the difference and relation between ffmpeg, libav, and avconv](http://stackoverflow.com/a/9477756/1109017) and [The FFmpeg/Libav situation](http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html) for more information.

---

### Post by PaulyWally on 2012-12-17
> **evilsoup said:**
> Installing 'proper' ffmpeg is as easy as [adding a PPA](https://launchpad.net/~jon-severinsson/+archive/ffmpeg)

Perhaps.  But the point is that the end user should not have to (IMHO). If an end user installs a package from the official repositories, it should work without spitting out a bunch of ffmpeg deprecation notices.

>  in 12.04, ffmpeg is effectively an alias of avconv, any program that calls ffmpeg by name should work with avconv.

When I first ran into this, I heard that urban legend as well.  I tried it.  It doesn't work.

But once again, I don't even think that is an issue the end user should be concerning themselves with.

> I can't speak for acidrip, though.

Acidrip uses mencoder, and adds a whole new set of issues.  I tried another package that relies on mencoder and I end up with the same lousy product.  I don't know if 12.04 messed with mencoder as well... I didn't look into it yet.  I just know that these were rock-solid packages prior to 12.04.  Now they don't even have their basic functionality.

> Generally, if you can't find an answer in half an hour of googling around, it's best to just ask about your problem here, or at askubuntu.com.

I always try to fix the problem before squabbling about it.  But after upgrading to 12.04 (on two different machines, that exhibit the same poor behavior) I've run into broken packages and incompatibility issues at least once a week.  It's getting old and also difficult to spend more time fixing problems than getting actual work done.

If this wasn't Ubuntu, I might not be ranting.  But I *thought* one of Ubuntu's goals were to close the gap on ordinary desktop users.  If you don't give your users the basic functionality of the packages in your official repositories, you are failing to meet that goal.

---

