---
title: "A Note on Downloading the Ubuntu 10.10 Final Release"
date: 2010-10-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by 23meg on 2010-10-05
We're approaching the Ubuntu 10.10 final release, and lots of people will be downloading the release images immediately after the release. Which is fine.

What isn't fine is people attempting to download the release images *before* release. This has been a growing problem in recent milestone releases: it makes the work of the release team harder, and can potentially cause problems due to downloads of broken or superseded images. Hence this note.

**[SIZE="3"]Short Version[/SIZE]**
[SIZE="1"]*"TL;DR, just give me that ISO!"*[/SIZE]

On Sunday, October 10th, lots of people will be linking to blog posts, news articles, ISO URLs, and even various pages on ubuntu.com with the claim that Ubuntu 10.10 has been released, many hours before the actual release. If you believe them, and download images at the links they provide, you can end up with broken or old images, and you'll be making the job of the release team harder. You should refrain from downloading the images before the official release announcement. If you want to be notified about the release via official means as soon as it happens, or just want to check if it's out or not, do one of the following:

[list][*] Check or subscribe to the [Ubuntu Release Blog]("http://release-blog.ubuntu.com/"). 
[*] Join the #ubuntu-release-party [IRC channel]("https://help.ubuntu.com/community/InternetRelayChat").
[*] Subscribe to the [ubuntu-announce mailing list]("https://lists.ubuntu.com/archives/ubuntu-announce/"), or check for the announcement via the [web archive]("https://lists.ubuntu.com/archives/ubuntu-announce/2010-September/date.html").[/list]

**[SIZE="3"]Long Version[/SIZE]**
*[SIZE="1"]"Really? Why shouldn't I download an image that's already out there?"[/SIZE]*

An Ubuntu release is a time consuming, laborious [process]("https://wiki.ubuntu.com/ReleaseProcess") that involves multiple steps undertaken by multiple people working in different timezones. A while before the release, the final release images have to be made publicly accessible, since some Ubuntu mirrors that do not have authenticated access to them need to download them, and the synchronization of all mirrors needs to be assured.

The fact that the images are available somewhere on the web does not mean that they are final, much less ready to be downloaded. The images can be changed, replaced or removed until the very last minute; this has happened before, and can happen again. The release process involves much more than building an image and uploading it to a server, and downloading images before it's complete is technically risky (since you risk getting images that are not final and can be broken, and your download may be interrupted), and socially uncourteous (since you'll be interfering with the release process; details below).

**[SIZE="2"]Q&A [/SIZE]**

[list][*] **If the release is not out, why are lots of blogs and news sites reporting that it is?**

Because they want to be the first to announce the release, to get more traffic than others, and make more money on ads, and they don't care if they are making the Ubuntu release harder, or giving Ubuntu users a bad experience due to failed, incomplete or broken downloads.


[*] **If the release is not out, why does the ubuntu.com home page / some page on ubuntu.com say that it is?**

Updating the home page and the various pages related to the release on ubuntu.com is just one part of the release process, and is carried out independently of the uploading and syncing of the images, so you can expect a certain degree of asynchrony. The website can be changed to reflect possible last minute changes at any moment, and there can be a considerable delay between the home page being updated and the release announcement being sent, the latter of which is the definitive sign that the release has happened. 


[*] **If the release is not out, why are lots of people saying that it is on forums and IRC?**

Either because they are informed by the wrong sources (see above) and haven't read this thread, or because they don't care. You can use the "Report abuse" button on the bottom left of each post and report to moderators that a link is posted prematurely.


[*] **I don't care; I'm impatient and will download it as soon as I see a link posted! What's the worst that can happen?**

You'll be risking downloading an incomplete or superseded image, you'll be delaying the actual release by hammering on the datacenter and using up the bandwidth that's needed for syncing the mirrors, and consequently you'll be making the job of the release team (which consists of volunteers as well as Canonical employees) harder and giving Canonical an unnecessarily bigger bandwidth bill. 


[*] **What time of the day is it going to be released?**

It's impossible to tell when precisely it's going to happen. It depends on when the work that needs to be carried out before publishing the images is complete and on when mirrors complete syncing, which in turn depends on network conditions all over the world. Just wait for the announcement.


[*] **So how do I know for certain that it's out?**

You can do any of the following:


[list][*] Check or subscribe to the [Ubuntu Release Blog]("http://release-blog.ubuntu.com/"). The release will be reported immediately with a new post.
[*] Join the #ubuntu-release-party or #ubuntu+1 channels [on irc.freenode.net]("https://help.ubuntu.com/community/InternetRelayChat"), where the release will be announced the moment it happens.
[*] Subscribe to the [ubuntu-announce mailing list]("https://lists.ubuntu.com/ubuntu-announce"), or check for the announcement via the [web archive]("https://lists.ubuntu.com/archives/ubuntu-announce/2010-September/date.html").[/list][/list]

A few additional points to remember:

[list][*] [Upgrades]("http://www.ubuntu.com/desktop/get-ubuntu/upgrade") are a well supported, official method of going from one Ubuntu release to the next. If you have a working installation of a supported stable release, you don't need to download the release images and reinstall; you can upgrade.


[*] You don't have to download the release images if you have a well maintained testing installation of Maverick. Some caveats apply; see [this thread]("http://ubuntuforums.org/showthread.php?t=1500648") for details.


[*] If you determine that you need to download the images on release date, please prefer torrents or zsync.[/list]

Thanks for caring.

---

### Post by amauk on 2010-10-05
call me silly, but why not setup simple HTTP-auth on the ISO locations prior to release
Provide the mirrors with the credentials, and they can grab the images but keep out the riff-raff ;)

Then when the red-button is pressed and the releas is official, just remove the auth
should be easy to automate all this

---

### Post by 23meg on 2010-10-05
> **amauk said:**
> call me silly, but why not setup simple HTTP-auth on the ISO locations prior to release
Provide the mirrors with the credentials, and they can grab the images but keep out the riff-raff ;)

Then when the red-button is pressed and the releas is official, just remove the auth
should be easy to automate all this

That's not silly; it's basically how part of the mirrors work. But my understanding is that some mirrors have a different level of affiliation and cannot work in the same authenticated manner. I don't have the exact details on how it works and why it works this way (it might be the difference between country mirrors and normal mirrors), but you can ask about the details in the #ubuntu-release channel on Freenode if curious.

---

### Post by andrewabc on 2010-10-05
Would be nice if this was a forum wide sticky thread. I'd say it's more the people that don't do dev testing that don't know this. I'm usually one of many here in dev forum telling people to wait for official announcement (and sometimes community cafe). A sticky thread would make this job easier so that when someone posts links I can just link to forumwide sticky that they obviously ignored. :)

---

### Post by cariboo on 2010-10-05
We will be placing the usual work-a-round thread in General Help with a link to this thread.

---

### Post by 23meg on 2010-10-06
> **andrewabc said:**
> Would be nice if this was a forum wide sticky thread. I'd say it's more the people that don't do dev testing that don't know this. I'm usually one of many here in dev forum telling people to wait for official announcement (and sometimes community cafe). A sticky thread would make this job easier so that when someone posts links I can just link to forumwide sticky that they obviously ignored. :)

I requested the thread to be copied to Community Cafe as well.

> **cariboo907 said:**
> We will be placing the usual work-a-round thread in General Help with a link to this thread.

Isn't that thread posted after the release? If so, there would be no point linking to this, since this is only useful before the release.

---

### Post by coffeecat on 2010-10-06
> **cariboo907 said:**
> We will be placing the usual work-a-round thread in General Help with a link to this thread.

I know this would be a lot of work for the moderators, but would it be feasible to jail, without mercy, any post that provides a download link before the official release announcement? You would probably have to announce such a policy in a sticky but I, for one, would be happy to spend my Sunday morning with my finger hovering over the "report abuse" button to help this process. :)

---

### Post by 23meg on 2010-10-06
> **coffeecat said:**
> I know this would be a lot of work for the moderators, but would it be feasible to jail, without mercy, any post that provides a download link before the official release announcement? You would probably have to announce such a policy in a sticky but I, for one, would be happy to spend my Sunday morning with my finger hovering over the "report abuse" button to help this process. :)

Jailing might be a bit heavy handed; simply editing out the URLs should suffice, and as long as a link to this thread is provided in the "Reason for editing" below, there's no need to announce a policy.

---

### Post by coffeecat on 2010-10-06
> **mgunes said:**
> Jailing might be a bit heavy handed

Point taken; it's not my place to say what any action should be. My thought was that reviewing all posts made in the few hours before release would be burdensome for the staff. Ordinary responsible members could help by reporting irresponsible posts if that would help, but only if reporting posts with download URLs would lead to some action.

---

### Post by 23meg on 2010-10-06
> **coffeecat said:**
> Point taken; it's not my place to say what any action should be. My thought was that reviewing all posts made in the few hours before release would be burdensome for the staff. Ordinary responsible members could help by reporting irresponsible posts if that would help, but only if reporting posts with download URLs would lead to some action.

Thanks for reminding me of "Report abuse"; I'll add a suggestion to use that to the post.

I agree that it's going to be burdensome either way (jailing or removing links), but if it's done to the greatest extent possible, together with an explanation as to why it's being done, that will still be beneficial.

---

### Post by philinux on 2010-10-06
> **mgunes said:**
> I requested the thread to be copied to Community Cafe as well.



Isn't that thread posted after the release? If so, there would be no point linking to this, since this is only useful before the release.

I've just copied the first post into the cafe as temporary sticky thread.

Also the sticky in GH has a link to this thread now.

---

### Post by Elfy on 2010-10-06
> **coffeecat said:**
> I know this would be a lot of work for the moderators, but would it be feasible to jail, ...

> **mgunes said:**
> Jailing might be a bit heavy handed; simply editing out the URLs should suffice.

> **coffeecat said:**
> .Ordinary responsible members could help by reporting irresponsible posts if that would help, but only if reporting posts with download URLs would lead to some action.

> **mgunes said:**
> Thanks for reminding me of "Report abuse"; I'll add a suggestion to use that to the post.

I agree that it's going to be burdensome either way (jailing or removing links), but if it's done to the greatest extent possible, together with an explanation as to why it's being done, that will still be beneficial.

Can I just say that while a whole bunch of reports sounds a good idea - we are all volunteers and it is entirely possible that whoever happens to be kicking about prior to release (and it won't be all of us) is going to get a whole lot of reports that will all need looking at - we can't tell whether it is spam - absolutely disgusting language - trolling - requests to change a thread title - without opening and reading them.

As to whether to jail or edit - jailing is quick and relatively painfree - editing will be much slower - especially given that is possible that the servers will be taking a bit hit as they normally do.

Personally I don't think it is down to us to police whether the iso is available in some places prior to it's actual release.


Edit - hotfoot from using the kettle - I hasten to add that this is not an official view - but purely my own and unlikely to affect me - I will not be online on Sunday when it releases.

---

### Post by 23meg on 2010-10-06
> **philinux said:**
> I've just copied the first post into the cafe as temporary sticky thread.

Thanks.

> **philinux said:**
> Also the sticky in GH has a link to this thread now.

Which one? I can't see a sticky in GH. 

> **forestpiskie said:**
> Can I just say that while a whole bunch of reports sounds a good idea - we are all volunteers and it is entirely possible that whoever happens to be kicking about prior to release (and it won't be all of us) is going to get a whole lot of reports that will all need looking at - we can't tell whether it is spam - absolutely disgusting language - trolling - requests to change a thread title - without opening and reading them.

I thought that might be the case, so I tried to use somewhat less encouraging language ("You can.." rather than "You should..") in recommending "Report abuse". Feel free to remove that part from the Community Cafe thread altogether if there's consensus among staff that it's going to be problematic.

> **forestpiskie said:**
> Personally I don't think it is down to us to police whether the iso is available in some places prior to it's actual release.

We can't and don't have to police it, but we can do something about it. That nobody can control whether a publicly available file is downloaded or not is the very heart of the matter in the first place.

Like I said, whatever extent we can make people aware is a win, not just for this release but future ones as well, and not just the people we inform, but the ones they'll spread the message to as well.

---

### Post by philinux on 2010-10-06
mgunes,

The one and only GH sticky.

[http://ubuntuforums.org/showpost.php?p=9928449&postcount=1](http://ubuntuforums.org/showpost.php?p=9928449&postcount=1)

---

### Post by VMC on 2010-10-06
Even if you were successful in removing any download links, their just a google away finding them on an irresponsible site.

Personally I never understood why all the rush. Its like those folks that camp out for days to get the latest gadgets. If they waited one or two days they could walk in unabated.

---

### Post by amauk on 2010-10-06
> **VMC said:**
> Even if you were successful in removing any download links, their just a google away finding them on an irresponsible site.

Personally I never understood why all the rush. Its like those folks that camp out for days to get the latest gadgets. If they waited one or two days they could walk in unabated.

Indeed
It's the tech blogs mainly
They all want the scoop first (even though the release schedule is published 6 months in advance)
They all want the "Ubuntu xx.xx released" story first

I still believe the only way to stop people hammering the servers prior to release is to actively stop them

You can ask, and edit links out all you want,
ain't going to do much good

Devise a way to keep them from reaching the ISOs until all the mirrors are sync'ed up and everythings ready to go

anyhow...

---

### Post by Elfy on 2010-10-06
> **philinux said:**
> mgunes,

The one and only GH sticky.

[http://ubuntuforums.org/showpost.php?p=9928449&postcount=1](http://ubuntuforums.org/showpost.php?p=9928449&postcount=1)

Which at present is moderated and only visible to staff ...

---

### Post by philinux on 2010-10-06
> **forestpiskie said:**
> Which at present is moderated and only visible to staff ...

Doh. Ok so the link in there to here is useless as the thread wont be visible until after the 10th. :confused:

---

### Post by philinux on 2010-10-07
mgunes,

I've stickied it in Installation and upgrade too as a temp sticky.

---

### Post by MikeDK on 2010-10-08
Torrents rules | Torrents rules | Torrents rules | Torrents Rules Torrents rules.............

---

### Post by MacUntu on 2010-10-08
I agree with amauk. Fighting the symptoms rather than the cause isn't the right approach to fix this. If this really is such a problem for the release team then maybe address it at the upcoming UDS?

---

### Post by plun on 2010-10-08
> **MacUntu said:**
>  If this really is such a problem for the release team then maybe address it at the upcoming UDS?

I haven't seen the "problem" with this.....:confused:

You can for sure make this to a "problem" !!


[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

---

### Post by jerrylamos on 2010-10-08
Usually the CD Daily Build shortly before the release date is awfully close, then just do update when the dust clears.  Testing install won't catch last minute ubiquity bugs though.

Oh, rsync is pretty good about lightening the load on the Daily Build server.

Why do an install?? For whatever reason, a new install seems to take noticeably less space on the hard drive than a previous install updated.  Yes I do apt-get clean, autoclean, autoremove, and dump previous /boot entries.

Anyway Maverick's running pretty good on video graphics i830, i845G, ati Radeon Xpress 200 & Mobility 7500.  I don't have any performance measurements - so far Lubuntu Maverick would be fastest.

Jerry

---

### Post by plun on 2010-10-08
Well... I also don't think there are "hidden" updates....

[https://lists.ubuntu.com/archives/maverick-changes/2010-October/thread.html](https://lists.ubuntu.com/archives/maverick-changes/2010-October/thread.html)

Strange "problem"......

---

### Post by MacUntu on 2010-10-08
> **plun said:**
> I haven't seen the "problem" with this.....:confused:
Maybe because you aren't part of the release team? :P

---

### Post by neglesaks on 2010-10-09
> **MikeDK said:**
> Torrents rules | Torrents rules | Torrents rules | Torrents Rules Torrents rules.............

I emphatically agree.

---

### Post by solitaire on 2010-10-09
Torrents rule...
or do what I do...
Download the RC image a week before the release, Install it and keep it updated!

Come 10/10/10 i'll already be running the latest version while most others still have 4h:23m left to download the ISO from an overloaded mirror.... ^_~ lol

---

### Post by andrewabc on 2010-10-09
A tip for the forum wide announcement that was on main forum page like was up for last release (please use torrents message):

Have in the announcement a link to a thread that links every torrent possible. That would make it real easy for users to get torrent instead of various download websites or directories.

1 click on word torrents in announcement, and another when looking through the torrent post. Simple.

---

### Post by jerrylamos on 2010-10-09
> **solitaire said:**
> Torrents rule...
or do what I do...
Download the RC image a week before the release, Install it and keep it updated!

Come 10/10/10 i'll already be running the latest version while most others still have 4h:23m left to download the ISO from an overloaded mirror.... ^_~ lol

CD Daily Build has been at 20101007 for the last couple days.  I just did an install on 20101009 and update said there were no updates.....

When the release is published I'll check md5sums.  Previously, it sometimes matched the last daily build and sometimes didn't, but in any case the update list was small.

Jerry

---

### Post by solitaire on 2010-10-09
This time I did an "update-manager -d" this time (last Wednesday 29th). Been keeping upto date with the updates..

---

### Post by VastOne on 2010-10-10
Having been testing Maverick with daily updates for 6 weeks now, I just did an dist-upgrade and my Conky Screen is telling me that I am at Ubuntu 10.10 'maverick'

Which gets its information from /etc/lsb-release

Just 5 minutes ago I was still at the Development Release.

:P :P :P

With that I only now have to wait for the Forums here to put up Ubuntu Maverick 10.10 as a choice in the User CP of what I am using... Hint Hint Nudge Nudge 

^ ^ That is a Joke!!!

---

### Post by ktp on 2010-10-10
Well it is 10-10 somewhere so...enjoy the release =)

---

### Post by VastOne on 2010-10-10
> **ktp said:**
> Well it is 10-10 somewhere so...enjoy the release =)

That I am... Interestingly this all happened right at the midnight hour switching to the 10th..

A good omen!  And 10.10 has be rock solid for me all during the testing..

---

### Post by gorski on 2010-10-10
[http://releases.ubuntu.com/kubuntu/10.10/](http://releases.ubuntu.com/kubuntu/10.10/) - it doesn't say RC... but I guess it must be... ;)

Just subscribing to the thread...:guitar:

---

