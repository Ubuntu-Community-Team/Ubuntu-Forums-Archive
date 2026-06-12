---
title: "MythTV upstream project is becoming disfunctional."
date: 2010-07-20
forum: Mythbuntu
---

### Post by barberio on 2010-07-20
First, I'm going to give the background on this. I've been a long time user of Mythbuntu, and have used MythTV since 0.19

After updating to the latest fixes version, my clients all stopped working. I use Myth as my network PVR, watching on Windows 7 and Mac OS 10.6, and so rely on the third party binary distributions there. Particularly since the build environments keep breaking on these platforms, so building my own is not really an option.

The protocol version has been changed in fixes. This shouldn't happen. Protocol changes were supposed to be major revision only. In fact, they've incremented from protocol version 56 to protocol version 23056, to "avoid using 57" since that's the trunk version.

This is the final straw for me. I keep tolerating the MythTV project's little idiosyncrasies because it's been the only network PVR around. But now there are alternatives, and at this point even using Windows Media Center is looking better.

I strongly feel the Mythbuntu project needs to apply pressure on the Upstream that they *MUST* start cleaning up their act if they're going to be included in Ubuntu's distributions. Clean up the code base, provide an actual spec for the network protocol, and maintain a stable branch that is actually stable. MythTV is going from kludge to kludge, hack to hack at the moment. The project is at risk of caving in under it's own weight. At the very least, they need to go through a version iteration with a feature freeze, and concentrate on fixing everything in the code-base that is currently broken or is working in a hard to use way because of early design choices that don't make sense now.

I fear it may even come down to using the threat of code fork to push the MythTV upstream into focusing on stability and usability.

---

### Post by foxbuntu on 2010-07-21
> **barberio said:**
> First, I'm going to give the background on this. I've been a long time user of Mythbuntu, and have used MythTV since 0.19

After updating to the latest fixes version, my clients all stopped working. I use Myth as my network PVR, watching on Windows 7 and Mac OS 10.6, and so rely on the third party binary distributions there. Particularly since the build environments keep breaking on these platforms, so building my own is not really an option.

The protocol version has been changed in fixes. This shouldn't happen. Protocol changes were supposed to be major revision only. In fact, they've incremented from protocol version 56 to protocol version 23056, to "avoid using 57" since that's the trunk version.

This is the final straw for me. I keep tolerating the MythTV project's little idiosyncrasies because it's been the only network PVR around. But now there are alternatives, and at this point even using Windows Media Center is looking better.

I strongly feel the Mythbuntu project needs to apply pressure on the Upstream that they *MUST* start cleaning up their act if they're going to be included in Ubuntu's distributions. Clean up the code base, provide an actual spec for the network protocol, and maintain a stable branch that is actually stable. MythTV is going from kludge to kludge, hack to hack at the moment. The project is at risk of caving in under it's own weight. At the very least, they need to go through a version iteration with a feature freeze, and concentrate on fixing everything in the code-base that is currently broken or is working in a hard to use way because of early design choices that don't make sense now.

I fear it may even come down to using the threat of code fork to push the MythTV upstream into focusing on stability and usability.

Thanks for the post. On the dev side of Mythbuntu we had a discussion about this very thing and we agree with the post. We can protest similar to any user but it still lies in the hands of the upstream team. It will certainly be brought up with the Upstream team but it will be their final decision on how to proceed. 

While we can put "pressure" on them as you put it, Mythbuntu relies on MythTV far more than MythTV relies on Ubuntu, so the relationship cannot be thrown away or become heated, as it will only lead to bad results for everyone involved. 

Always remember though, its a FOSS community for a reason, its software by the users and for the users. Make your concerns heard in a clam and collected manner, enough voices will lead to change. Also, don't forget the "dig in and fix it if you can" approach is always an option as well.

---

### Post by superm1 on 2010-07-21
I'd like to raise to your attention the conversation that happened in #mythtv shortly ago about this exact issue.

> <superm1> gigem_, a protocol change in -fixes is acceptable?  isn't that asking for trouble with all sorts of people who use binary packages for their different systems?
* rossand has quit (Quit: Leaving.)
* Goga777 (~Goga777@shpd-92-101-155-81.vologda.ru) has joined #mythtv
* inordkuo has quit (Quit: Leaving.)
* inordkuo (~inorkuo@adsl-177-189-64.int.bellsouth.net) has joined #mythtv
* Goga777 has quit (Remote host closed the connection)
* wylie has quit (Quit: wylie)
<xris> superm1: I think it's been done before, but I'm inclined to agree..  changing the protocol in a stable branch is probably asking for trouble
<wagnerrp> the DB schema has been changed before, i dont think the protocol ever has
* ceros has quit (Ping timeout: 258 seconds)
<superm1> i don't mean to introduce a lot of bureaucracy, but were all of the developers in agreement about that type of change  before making it?  it seems like one of those things that can have rash implications
<xris> nope
<xris> unless I missed some bit chat about it here
<xris> imho something like that should have at least had signoff from me, Captain_Murdoch, or janneg 
* sulx has quit (Ping timeout: 252 seconds)
<superm1> yeah, i'd agree
<xris> I think people are still sort of getting used to the steering committee idea
<xris> especially since we sort of quieted down
<wagnerrp> i think it was an unexpected backport
<sphery> FWIW (and not saying anything about whether this one should or should not have been done), we have changed proto version in -fixes before.  Did it in 0.20-fixes ( [http://svn.mythtv.org/trac/changeset/11281](http://svn.mythtv.org/trac/changeset/11281) + [http://www.gossamer-threads.com/lists/mythtv/dev/226499#226499](http://www.gossamer-threads.com/lists/mythtv/dev/226499#226499) ).
<xris> sphery: thx..  I was pretty sure it had happened before
<wagnerrp> an hour or so after it happened, there was a bit of chatter between iamlindoro, Captain_Murdoch, and i about how to fix it
* sulx (~sulx@85-23-15-158-Karjasilta-TR1.suomi.net) has joined #mythtv
<xris> and I don't mind doing it.  but it's something that should take some discussion.  or at least coordination with packagers so we could cut an 0.23.1 or something
<superm1> i think the difference there, is that 0.20 actually had a follow up point release though, didn't it?
<wagnerrp> as it stood, the original commit had an incompatible protocol collision between trunk and -fixes
<wagnerrp> it did for schedules direct support, yes
<xris> wagnerrp: yeah, that's another issue altogether.
* xris adds it as another talking point for steering ideas...
<superm1> wagnerrp, wouldn't it have made more sense to bump the protocol in trunk in the case of a collision?
<superm1> people already have the expectation that they need to be updating trunk regularly
<xris> superm1: when it happens it's more an issue of sequential numbers
<superm1> ah
<sphery> superm1: that change to 0.20-fixes was 7 months before 0.20.1 release
<xris> and next sequential in -fixes would be bigger than trunk...  but similar to older stuff in trunk
<xris> protocol really needs to be two-fold in these kinds of cases
<xris> appversion + protoversion
<sphery> yeah, that's what wagnerrp's #8681 is for
* xris wonders how protobuffers deals with that
<wagnerrp> xris: yeah, the python bindings and mythweb have already been updated to take a string, mythtv itself already did
<wagnerrp> just waiting on perl
<wagnerrp> the intent being that in future cases of this, we can go to '56b', '56c', etc...
<superm1> awesome, that does sound like a nice way to be able to account for stuff like this
<wagnerrp> its 'cleaner', but the end result is still the same
<wagnerrp> they would still be incompatible revisions, and users would still have to upgrade all systems at once
<wagnerrp> of course it lets us have a little fun with the non-compliant clients that simply iterate up to an accepted protocol revision
superm1> well as long as individual developers don't unilaterally decide to backport things to cause protocol or db schema changes without consulting with at least a few others, hopefully it won't have to be used too often

---

### Post by barberio on 2010-07-21
There's more to the MythTV project's problems than just this incident, but this incident demonstrates that they suffer greatly from a lack of planning.

For a start, the protocol should be well defined, that's a pretty basic tenant of software design. MythTV has developed an adhoc protocol that's not only undocumented, but apparently obscure enough to the people maintaining MythTV that it causes problems.

That various portions of the code *do individual checks* of the version number, and use *different methods to do it*, is a *huge* flashing red light that spaghetti code and reinvention of the wheel has taken place. There should have been a common 'protocol version check' function that could have been changed to accept a string.

The response to not being able to use a string for the version number because of bad coding assumptions, highlights another problem with the project.

Bad coding decisions are never fixed, even when they generate howlers like this, they're just not fixed. The correct response here was "well we need to fix that so it's all using a common version check function that can take a string", not "well, we better kludge together a weird protocol numbering scheme so we don't have to fix that code". There are so many of these weird coding decisions, that not even the current developers really seem to understand why MythTV works in the way it does. For example, why it's using NUV, and why the pnp server doesn't quite work right.

I also note the line from the conversation about hassling third party frontend developers...

The reason third party frontends lag behind the protocol, is because the protocol is totally undocumented and opaque. And the attitude of developers is that third party frontends don't matter, are unsupported, and don't deserve the crumbs that the project deigns to give them. Open Source should be about Open Formats as well, but the MythTV project's formats are pretty opaque!

---

### Post by barberio on 2010-07-21
After consideration, I think the threat of code fork isn't going to work. I wouldn't want to be in charge of fixing the MythTV code base, and I can't imagine anyone wanting to take it on a cleanup project of such magnitude.

With any complicated project that has been neglected, there comes a tipping point where maintenance and repair is impossible and all that's left is demolition and replacement. I suspect MythTV's codebase has passed that point.

I suspect any code fork would ultimately end up with abandoning the  original code base to create a new cut down PVR server that just used  XBMC or similar as it's frontend. If any daring developers want to, I'd offer assistance with "use-case design" for how a distributed system PVR should work. Not a great coder, but I know how to draw a UML chart.

---

### Post by foxbuntu on 2010-07-23
I am not sure I would go so far as to say *all* of the upstream code base is a lost cause, but I would agree it needs some very distinct leadership and a vision. I would also agree a cleanup and repair/remodel project are in-order to move some things to standardized code. 

Furthermore, allowing a better API to the backend would be very useful in furthering the use of MythTV as a core application to a PVR system, such as Google Apps has positioned itself in the Office Productivity/Collaboration arena.

I am a very inexperienced C/C++ coder which leaves me at a very big loss on where to even dive in, but if there where enough support from existing upstream leadership/developers and new devs, I would be glad to help where I could.

---

### Post by barberio on 2010-07-23
> **barberio said:**
> Not a great coder, but I know how to draw a UML chart.

And some hacking around led me to [http://wall-e.deliverator.homeip.net/~barberio/temp/Media%20Use%20Case.png]("http://wall-e.deliverator.homeip.net/%7Ebarberio/temp/Media%20Use%20Case.png") as a system design for something that could replace MythTV.

The benefits of this design are that we don't actually need to make a frontend. The existing projects such as XBMC would serve fine, so long as we speak to them. The "Frontend" could even be any generic computer that has a browser and can playback video, like an iPad.

And the bits that do need creating can be broken down into the blocks shown, and developed individually, by assuming a common interim media format with metadata. And there can be a clear timeline for which parts get developed in which order. ie, there's no need for a transcoder, or deletion framework in early development. The scheduler can be implemented after live-tv and basic recording functions. 

And by having the schedualing and media management interfaces put together as remote control friendly web-apps running on the servers, there would be a common user interface and no need for us to make individual frontend plugins.

**Edit: **Diagram updated to better show use of web-apps for the TV Source and the Media File Server's user interfaces, and how they would be intended for use via a frontend or browser. This better shows that the Frontend can be a totally abstract blackbox for our purposes.

**Edit**: And a more abstracted top level shows how "TV recording" could only be a part of a suite of Media Center systems. [http://wall-e.deliverator.homeip.net/~barberio/temp/Media%20Use%20Case%20-%20Top%20Level.png](http://wall-e.deliverator.homeip.net/~barberio/temp/Media%20Use%20Case%20-%20Top%20Level.png)

---

### Post by brianafischer on 2010-07-30
It looks like they corrected the issue by creating 0.23.1 and reverting the 0.23 fixes branch.  I guess a benefit of open source is to admit and correct mistakes.

[http://www.mythtv.org/wiki/Release_Notes_-_0.23.1]("http://www.mythtv.org/wiki/Release_Notes_-_0.23.1")
[http://thehtpcblog.com/2010/07/25/mythtv-0-23-1-is-now-available/]("http://thehtpcblog.com/2010/07/25/mythtv-0-23-1-is-now-available/")


The amount of effort to create a new architecture would take years to accomplish.  Although not perfect, I have embraced the open source mythtv project and have accepted that things are not going to always be perfect.  However, anyone can influence the direction and features with some time.

---

### Post by nickrout on 2010-08-01
> **barberio said:**
> And some hacking around led me to [http://wall-e.deliverator.homeip.net/~barberio/temp/Media%20Use%20Case.png]("http://wall-e.deliverator.homeip.net/%7Ebarberio/temp/Media%20Use%20Case.png") as a system design for something that could replace MythTV.



I guess a pre-requisite would be a developer that can spell "schedule".

---

### Post by joshoekstra on 2010-08-01
I can understand barberio a bit, because he's probably and end-user like me who got bitten by this 'bug'. For me there are several places where I could see this could have been done differently, but als, I'm not behind the wheel...

I actually like the current set goals for certain dates, I follow the commits and dev-lists but still having set dates(which also seem to be kept) gives me an better idea what's going on and helps me place the different messages there.

Just give the 'committee' some time, I see some real progress especially in the 'unter the hood' department but also in the 'what is this button supposed to do' department.

The old adagio: 'If you can do it better, better do it' still holds ;)

// Offtopic: Schedual is fonetic! isn't it? ;)

---

### Post by uncle hammy on 2010-08-02
> **nickrout said:**
> I guess a pre-requisite would be a developer that can spell "schedule".
[QUOTE=barberio]**Not a great coder**, but I know how to draw a UML chart.[/quote]
I guess a prerequisite would be a jackass who can read ;)....and spell "prerequisite"...

---

### Post by jlipoth on 2010-08-03
As some one who is an end user and has relied on Mythbuntu for our family server, this has become completely unusable.  I have enjoyed the new features that have come along; however, I am away from home a fair bit and getting a call from my wife to say that Mythtv is broken is a common occurrence.  I originally moved from GBPVR, because Mythbuntu was much more stable.  Unfortunately it appears that Mythtv has turned into a coding project and not an actual piece of usable software from an end user point of view.  I hope this will change soon, otherwise I'll probably upgrade all my hardware and buy some Windows 7 licenses.  This move would definitely not be my preference, but we need something in our house that just works.

---

### Post by nickrout on 2010-08-03
Funny mine just works (on 0.23-fixes)

---

### Post by dakota34 on 2010-08-03
I wonder how many who are experiencing problems are using autobuilds/daily upstream fixes? I started running into problems with autobuilds a few months ago, escalating into a *lot* of issues with nvidia drivers. but since getting off autobuilds all systems (2 frontends and a combined backend/frontend) have been rock solid for about 6 weeks now. 

Sidenote: maybe it's  too much of a contradiction to expect to remain cutting edge current with daily fixes and also totally stable and 'hands off'. In any event, I just don't think yelling for someone else to fork a project, whether it's this one or any other, is in any way helpful, no matter how frustrated you are. Free country and all that, but IMHO there are far more productive ways of promoting change.

---

### Post by nickrout on 2010-08-04
> **dakota34 said:**
> I wonder how many who are experiencing problems are using autobuilds/daily upstream fixes? I started running into problems with autobuilds a few months ago, escalating into a *lot* of issues with nvidia drivers. but since getting off autobuilds all systems (2 frontends and a combined backend/frontend) have been rock solid for about 6 weeks now. 

The version of mythtv shipped with 10.04, and which remains in the mythbuntu repos is a release candidate of 0.23, NOT the release version. You really do need to update to autobuilds at least once to get a half way stable version. 

0.23-fixes from autobuilds is very stable. Only true fixes are ported to the -fixes branch. There are no new features added. I am on autobuilds and the system is very stable (although because I don't update every day, I missed the problem that triggered this thread)

OTOH if you use trunk (currently 0.24) autobuilds, you can expect instability. That's the expense of testing the latest code, you are an adventurer and a tester. if you have problems, that's to be expected.

> 

Sidenote: maybe it's  too much of a contradiction to expect to remain cutting edge current with daily fixes and also totally stable and 'hands off'. In any event, I just don't think yelling for someone else to fork a project, whether it's this one or any other, is in any way helpful, no matter how frustrated you are. Free country and all that, but IMHO there are far more productive ways of promoting change.

As I say, there are two versions of autobuilds. Only trunk/0.24 is cutting edge. -fixes is very stable, but I do update my backend and two frontends all at the same time.

The other thing, if you want to follow trunk, the developers Do expect you to FOLLOW the -commits and -dev mailing lists. Don't say you haven't been warned.

Patches are posted to trak, feature requests without a patch are posted to the -users mailing list.

---

### Post by barberio on 2010-08-05
> **nickrout said:**
> I guess a pre-requisite would be a developer that can spell "schedule".

Oh cute. Someone who thinks constructive criticism includes spelling flames. And doesn't know the difference between design and development.

On that note, I fixed the typo in an updated chart. As well as working through it to get a clear dependency path, and a flow of client-server relationships that has no re-iteration. Then producing a top-level graph which shows how an independent TV-Source should slot into a generic media system.

[IMG]http://wall-e.deliverator.homeip.net/%7Ebarberio/TV%20Source/Media%20Use%20Case%20-%20Top%20Level.png[/IMG]

[IMG]http://wall-e.deliverator.homeip.net/%7Ebarberio/TV%20Source/Media%20Use%20Case%20-%20TV%20Source.png[/IMG]

This lays out that it would be surprisingly simple a project to replace MythTV. The recording process and a meta-data friendly storage system are the starting points, then each client of those can be developed.

Note, I acknowledge that MythTV now have a 'steering committee', but the existence of a committee does not imply the existence of a plan. And MythTV still seem set on maintaining the status quo.

---

### Post by tgm4883 on 2010-08-05
> **barberio said:**
> Oh cute. Someone who thinks constructive criticism includes spelling flames. And doesn't know the difference between design and development.

On that note, I fixed the typo in an updated chart. As well as working through it to get a clear dependency path, and a flow of client-server relationships that has no re-iteration. Then producing a top-level graph which shows how an independent TV-Source should slot into a generic media system.

[IMG]http://wall-e.deliverator.homeip.net/%7Ebarberio/TV%20Source/Media%20Use%20Case%20-%20Top%20Level.png[/IMG]

[IMG]http://wall-e.deliverator.homeip.net/%7Ebarberio/TV%20Source/Media%20Use%20Case%20-%20TV%20Source.png[/IMG]

This lays out that it would be surprisingly simple a project to replace MythTV. The recording process and a meta-data friendly storage system are the starting points, then each client of those can be developed.

Note, I acknowledge that MythTV now have a 'steering committee', but the existence of a committee does not imply the existence of a plan. And MythTV still seem set on maintaining the status quo.

Ok, I've tried really hard to stay out of this thread. I try not to get down on users because the work I do isn't just for me, but for everyone. I just couldn't help it anymore.

All this shows is that is surprisingly simple to draw a diagram. You said yourself that you are "Not a great coder", proven by thinking that it is "surprisingly simple" to replace the functionality of MythTV. For someone that has had multiple issues with MythTV, this protocol version seems to be the only one you have listed, which was reversed by upstream MythTV developers (they cut a new point release and said that won't happen in the future). Seems to me that upstream is doing the right thing.

I sure hope you have filed bug reports for the issues you are having. After all, developers can't fix what they don't know about and I doubt you are fixing the bugs yourself since you are "Not a great coder". Does the MythTV project have its problems? Sure, but so does any project. I can list a few of the other media centre projects that have their own issues as well. Whats the point in that though since it is "surprisingly simple" to replace MythTV. 

But since you believe it is so "surprisingly simple" to replace MythTV, I suppose I will see a 1.0 release from you soon. I guess I should expect to see it released in about a month. I gave you extra time "Not a great coder". I won't hold my breath though, since I know that it is "surprisingly simple" to draw a diagram with cute stick people and arrows and not so "surprisingly simple" to replace a complex project such as MythTV.

---

### Post by bcg30506 on 2010-08-05
> **nickrout said:**
> Funny mine just works (on 0.23-fixes)

Mine too.  While not perfect, it is light years ahead of where it began when I started using it at 0.17 and far better than anything else I've seen for the price.

---

### Post by barberio on 2010-08-05
> **tgm4883 said:**
> 
But since you believe it is so "surprisingly simple" to replace MythTV, I suppose I will see a 1.0 release from you soon. I guess I should expect to see it released in about a month. I gave you extra time "Not a great coder". I won't hold my breath though, since I know that it is "surprisingly simple" to draw a diagram with cute stick people and arrows and not so "surprisingly simple" to replace a complex project such as MythTV.

You're so big and clever with your sarcastic comments... Er... You realise those 'cute stick people' are the Use Case UML standard symbol for 'Actors' external to a system that either operate it or provide it with input or are an output sink.

You know, I wonder if you'd actually be able to, from scratch, Use Case Model any major system?

Do you even know what Use Case Model means?

Have you ever taken a single course of Computer Engineering and Design, as opposed to code hacking?

Do you understand how much of a turn off it is to reject design input from people who aren't interested in spending time on your coding project?

Do you actually understand what you're talking about, or are you just butting in for the kudos of defending MythTV "from attack"?

Are you really saying that MythTV isn't beset with systemic issues, such as it's protocol being undocumented and utter refusal to support third party front-ends? It's use of a totally obscure, and altered at will, storage format? The UPNP server being non-UPNP compliant?

Maybe if the MythTV project had more non-coders doing QA testing, pointing out errors in the design, and talking about usability over programmer comfort, they wouldn't have so many of these "unique characteristics".

I also point out that one of the important parts of the **Ubuntu** project is how much input is taken from non-coders. The existence of Brainstorm, and ubuntu's other non-coder targeted QA projects, and the open-bug reporting system and extensive user documentation, is almost the opposite of MythTV's user-hostile coders are gods ethos.

Someone who can bash out C code is not more important than someone who can work out the system archetechture, someone who runs unit test, or someone who identifies how an end user will work with a system. Many Open Source projects fail exactly because of people like you who insist they be praised, and directly insult those who are not coders.

---

### Post by nickrout on 2010-08-05
If you have patches submit them to trak.

If you want to discuss development, joint the -dev mailing list.

You possibly have some good ideas, but couching them as criticisms and denigrating the current setup will hardly engender sympathy for your views.

OTOH if you just want yo start your own project, gather some programmers and get on with it. Competition is healthy, I will be interested in your progress.

---

### Post by tgm4883 on 2010-08-05
> **barberio said:**
> You're so big and clever with your sarcastic comments... Er... You realise those 'cute stick people' are the Use Case UML standard symbol for 'Actors' external to a system that either operate it or provide it with input or are an output sink.

You know, I wonder if you'd actually be able to, from scratch, Use Case Model any major system?

Do you even know what Use Case Model means?

Only what wikipedia tells me :) [http://en.wikipedia.org/wiki/Use_case_diagram](http://en.wikipedia.org/wiki/Use_case_diagram)


> **barberio said:**
> 
Have you ever taken a single course of Computer Engineering and Design, as opposed to code hacking?

Yep


> **barberio said:**
> 
Do you understand how much of a turn off it is to reject design input from people who aren't interested in spending time on your coding project?

I'm not a MythTV developer, I develop for Mythbuntu


> **barberio said:**
> 
Do you actually understand what you're talking about, or are you just butting in for the kudos of defending MythTV "from attack"?

I know what I'm talking about, do you? Seems to me that you think recreating a project to replace MythTV should be fairly simple. Heck, I bet a few dedicated programmers could whip it out is a few days.

Oh, and I don't need to defend MythTV. They are big boys over there.


> **barberio said:**
> 
Are you really saying that MythTV isn't beset with systemic issues, such as it's protocol being undocumented and utter refusal to support third party front-ends? It's use of a totally obscure, and altered at will, storage format? The UPNP server being non-UPNP compliant?

Sure the MythTV project has issues. As do other projects. You want to entirely replace Gnome or KDE too?


> **barberio said:**
> 
Maybe if the MythTV project had more non-coders doing QA testing, pointing out errors in the design, and talking about usability over programmer comfort, they wouldn't have so many of these "unique characteristics".

Hmm, QA testing isn't fun and the MythTV developers aren't paid. Are you volunteering to do the QA testing? See you around in the #mythtv channel.


> **barberio said:**
> 
I also point out that one of the important parts of the **Ubuntu** project is how much input is taken from non-coders. The existence of Brainstorm, and ubuntu's other non-coder targeted QA projects, and the open-bug reporting system and extensive user documentation, is almost the opposite of MythTV's user-hostile coders are gods ethos.

Yea brainstorm is great! Whats your user ID so I can look up your submissions?


> **barberio said:**
> 
Someone who can bash out C code is not more important than someone who can work out the system archetechture, someone who runs unit test, or someone who identifies how an end user will work with a system. Many Open Source projects fail exactly because of people like you who insist they be praised, and directly insult those who are not coders.
I couldn't agree more, I wouldn't want to have to praise people who know how to code better than I. That would be almost everyone....  Oh. You thought I was some expert programmer? No, I barely know Python. I do code what I can, test patches, file/triage/sort bug reports, write documentation, moderate the Mythbuntu forums, make sure the ISO's are available for people to download, and help coordinate development of the Mythbuntu project. 

All I'm saying is that it is far easier to draw a picture that it is to completely replace the functionality of MythTV. Judging based on what you have said, and some brief searching, that is all you have done. I don't see any bug reports, patches, other forum threads, etc. But here, praise where it is due. Have some popcorn :popcorn:

---

### Post by iamlindoro on 2010-08-05
> **barberio said:**
> You're so big and clever with your sarcastic comments... Er... You realise those 'cute stick people' are the Use Case UML standard symbol for 'Actors' external to a system that either operate it or provide it with input or are an output sink.

[disclaimer:  I am a MythTV developer.  I am speaking for myself, not the project.]

Your attitude is troubling.  You come to a MythTV forum to deride the project, and it seems as though you are surprised that people aren't open to your ideas.  Moreover, you have a lot of insulting, thoughtless, and rude language about the project, and anyone who disagrees with you when one of your primary complaints is the allegedly antagonistic attitude of MythTV devs.  

Here's what open source is, and what it isn't.

Open source means you can use, or not use the software.  If you disagree with coding or management decisions, you can take some or all of the code and use it to make something better, provided the derived code is under a compatible license.  Alternately, you can start your own project from scratch and license it any way you like.

Open source is *not* free reign to demand that changes be made to fit your use case.  By definition, the decisions are made by those doing the work.  

It may surprise you to know that we have long term plans for the project and that we are working hard to address many issues you have issues with.  The protocol change was made without prior consultation with the rest of devs, and it was something we corrected within hours by tagging a point release.  Further, we forumlated a formal policy to avoid this kind of mistake in the future.  I know that this flies in the face of your assessment that we are somehow "disfunctional" (sic), so please don't let it prevent you starting your own project.

In all seriousness, the very very few of us who actually contribute code to MythTV work very hard with our own free time to try to constantly improve the code.  We are not perfect, nor is our code.  I can say, however, that you are exactly the kind of user that I am happy to do without.  I care very deeply about the user experience in MythTV and have made it my personal crusade for the past serveral years to slowly begin to creep out of our usability hole.  To have that effort derided, mocked, and insulted is hurtful, and I would be just as happy to see you, and anyone who feels this way, provide us with options.  Open source is also about options, and I use MythTV because it is the best available, and because I enjoy working with my teammates on the project.

> **barberio said:**
> You know, I wonder if you'd actually be able to, from scratch, Use Case Model any major system?

Do you even know what Use Case Model means?

Have you ever taken a single course of Computer Engineering and Design, as opposed to code hacking?

This is another puzzling perspective to me.  You want your talents and abilities to be recognized, but deride those of us who do the implementation as "code hackers" and producers of "spaghetti code."  Moreover, you claim not to have much talent in the coding department, but apparently consider yourself authority enough to pass judgment on the quality of the code.  Are there bugs?  Yes.  But when they get filed, we fix them.  And we continue to fix them and attempt to troubleshoot basic functionality and usability issues.

> **barberio said:**
> Do you understand how much of a turn off it is to reject design input from people who aren't interested in spending time on your coding project?

Do you actually understand what you're talking about, or are you just butting in for the kudos of defending MythTV "from attack"?

Are you really saying that MythTV isn't beset with systemic issues, such as it's protocol being undocumented and utter refusal to support third party front-ends? It's use of a totally obscure, and altered at will, storage format? The UPNP server being non-UPNP compliant?

I will go on record:  MythTV has issues, and nobody but those contributing code is doing anything to address them.  Layout out a roadmap for us to implement at your whim does nothing for us.  You appear to be under the impression that the project lacks for ideas-- it doesn't.  What we lack are *implementors*.  We are absolutely open to great design ideas so long as they are paired with a willingness to roll up your sleeves and do the work to scratch your own itch.

On a minor note, uPnP as a standard is not very "u,"  And the uPnP server functions fine on all my devices.  If you see an issue, you can always file a bug... Gavin Hurlbut has been busting his hump trying to get diagnostic information to improve the uPnP server, with little community response.  If we cannot get a response when asking for basic console output, what hope do we have to improve it and make it better?  Some common frustrations with the uPnP server is that various files are unplayable on various clients-- but those are client issues, not server ones.  Take, for example, the Xbox 360, which refuses to play MPEG-2 in TS (it needs to be in ASF for its uPnP client to play it) or the countless other products that are picky about containers and formats-- for that to all work, someone needs to write a transcoder in to the uPnP server, which is not part of the uPnP spec-- just a requirement to make more devices play nice.


> **barberio said:**
> Someone who can bash out C code is not more important than someone who can work out the system archetechture, someone who runs unit test, or someone who identifies how an end user will work with a system. Many Open Source projects fail exactly because of people like you who insist they be praised, and directly insult those who are not coders.

I have already covered the general derisiveness of any talent you lack above, so I'll just leave some concluding remarks.  You have made a lot of noise about how difficult we are to work with, and your laundry list of complaints.  It seems that no matter what anyone says, you are convinced that we cannot meet your needs.  So what can I say to convince you to take it elsewhere?  If you are serious about producing a better product, I invite you to put your money where your mouth is.  Start a site, solicit some like-minded people to work on it with you, and feel free to use any portion of the MythTV code you like, so long as the result is GPLv2.  Minimally, demonstrate some common sense and see that drumming up a revolution against MythTV is not going to be particularly effective when you do it under the auspices of a MythTV-specific forum.

Best of luck with your project, let us know how it goes.

Robert McNamara
MythTV

---

### Post by barberio on 2010-08-05
I've attempted to discuss design issues with MythTV on the dev mailing list before. It's bounced every time, with the same responses. As I said, MythTV is a firm example of the "Programmers are God, Users Don't Matter" ethic.

These issues are not going to be fixed with patches. I can't submit a patch for "the project will not support alternative frontends", "the project does not have a specific design for its network protocols" or "the project breaks binary comparability in a minor stable version update".

---

### Post by iamlindoro on 2010-08-05
> **barberio said:**
> I've attempted to discuss design issues with MythTV on the dev mailing list before. It's bounced every time, with the same responses. As I said, MythTV is a firm example of the "Programmers are God, Users Don't Matter" ethic.

These issues are not going to be fixed with patches. I can't submit a patch for "the project will not support alternative frontends", "the project does not have a specific design for its network protocols" or "the project breaks binary comparability in a minor stable version update".

Once again, we are very happy to rethink design when it comes with a willingness to do the implementation.  Unfortunately, it's a fact of life that you need to be capable of one to have a say in the other.  That's just how our project works.  Sorry.

We happily supoprt any third party frontend that uses the protocol.  The protocol is fully documented on the wiki, in spite of your protestations that it is undocumented.

[http://www.mythtv.org/wiki/Protocol](http://www.mythtv.org/wiki/Protocol)

Each protocol command is clickable, with its own doc page.

I have addressed the binary compatibility issue, and acknowledged that it was a mistake that we corrected within hours, and then put in place measures so that it would not happen again.  It appears there is no satisfying you.  When your project's site is up, please let us know, I am eager to follow your progress.

Robert

---

### Post by barberio on 2010-08-05
> **iamlindoro said:**
> [disclaimer:  I am a MythTV developer.  I am speaking for myself, not the project.]

Your attitude is troubling.  You come to a MythTV forum to deride the project, and it seems as though you are surprised that people aren't open to your ideas.  Moreover, you have a lot of insulting, thoughtless, and rude language about the project, and anyone who disagrees with you when one of your primary complaints is the allegedly antagonistic attitude of MythTV devs.  



Er... No... This is a UBUNTU forum. 

> 
Here's what open source is, and what it isn't.

Open source means you can use, or not use the software.  If you disagree with coding or management decisions, you can take some or all of the code and use it to make something better, provided the derived code is under a compatible license.  Alternately, you can start your own project from scratch and license it any way you like.

Open source is *not* free reign to demand that changes be made to fit your use case.  By definition, the decisions are made by those doing the work.  

It may surprise you to know that we have long term plans for the project and that we are working hard to address many issues you have issues with.  The protocol change was made without prior consultation with the rest of devs, and it was something we corrected within hours by tagging a point release.  Further, we forumlated a formal policy to avoid this kind of mistake in the future.  I know that this flies in the face of your assessment that we are somehow "disfunctional" (sic), so please don't let it prevent you starting your own project.
What are these long term plans?

Can you show me a system design for MythTV?

Can you show me a protocol spec for MythTV?

Can you show me a development roadmap?

If you can show me these things, I'll back down on MythTV being dysfunctional.

But until you *have those things*, your project is dysfunctional.

> 
In all seriousness, the very very few of us who actually contribute code to MythTV work very hard with our own free time to try to constantly improve the code.  We are not perfect, nor is our code.  I can say, however, that you are exactly the kind of user that I am happy to do without.  I care very deeply about the user experience in MythTV and have made it my personal crusade for the past serveral years to slowly begin to creep out of our usability hole.  To have that effort derided, mocked, and insulted is hurtful, and I would be just as happy to see you, and anyone who feels this way, provide us with options.  Open source is also about options, and I use MythTV because it is the best available, and because I enjoy working with my teammates on the project.
I'm happy that you're trying. But you're a long long way off from engaging your userbase in any realistic way.

And I know this because I've tried to explain to you before why your user-feed back system is broken. You deliberately prevent people discussing and explaining the problems they have filed ticket for on the web based ticket tracker, and force them to subscribe to a mailing list to discuss any problems they have. Tickets are locked to prevent "user discussion". 

Tickets that described problems are converted to task tickets that focus on a single patch, rather than the problem it's self. Then reports of a similar or linked problem are often marked as duplicates of this problem, even if patch will not address it. Then the ticket is closed when the work on the patch is completed, even if it doesn't fix the original problem.

I was told you would not consider any changes to how you manage your issues tracker. 

> 
This is another puzzling perspective to me.  You want your talents and abilities to be recognized, but deride those of us who do the implementation as "code hackers" and producers of "spaghetti code."  Moreover, you claim not to have much talent in the coding department, but apparently consider yourself authority enough to pass judgment on the quality of the code.  Are there bugs?  Yes.  But when they get filed, we fix them.  And we continue to fix them and attempt to troubleshoot basic functionality and usability issues.
Actually, often you don't. I've read the dev and user mailing list. I've seen developers browbeat users. The ethos amongst MythTV developers, is that a previous development choice is not to be changed unless it explicitly breaks something else. If a user request might mean altering that development choice, then the user request will not be considered no matter it's merits.

There are lots of interesting legacy issues with MythTV, not least of which is using *nupple video*.

> 
I will go on record:  MythTV has issues, and nobody but those contributing code is doing anything to address them.  Layout out a roadmap for us to implement at your whim does nothing for us.  You appear to be under the impression that the project lacks for ideas-- it doesn't.  What we lack are *implementors*.  We are absolutely open to great design ideas so long as they are paired with a willingness to roll up your sleeves and do the work to scratch your own itch.
See, there's your problem.

You don't want to listen to anyone who isn't going to directly assist you with coding.

So by definition, you're *not* open to new design ideas. Because the best designers are often not the best implementers. Just as someone who's good at setting up QA testing isn't always good at doing the programming to fix the bugs they find. So you're instantly limiting the project.

You demand that the people who work on MythTV have to be good designers, good testers, good user behaviour profilers, and good programmers all in one package... And then complain that you don't have enough people?

> 
On a minor note, uPnP as a standard is not very "u,"  And the uPnP server functions fine on all my devices.  If you see an issue, you can always file a bug... Gavin Hurlbut has been busting his hump trying to get diagnostic information to improve the uPnP server, with little community response.  If we cannot get a response when asking for basic console output, what hope do we have to improve it and make it better?
Again, see my comments that your User Feedback system is broken, and actively hostile to people who want to try and report issues with MythTV. You want feedback, make it easy for the user to give it. Give them simple easy to use tools to get those diagnostic dumps to you, don't expect them to know how to find the right way to turn on that diagnostic debug logging, don't expect your users to be sysadmins or programmers.

> 
I have already covered the general derisiveness of any talent you lack above, so I'll just leave some concluding remarks.  You have made a lot of noise about how difficult we are to work with, and your laundry list of complaints.  It seems that no matter what anyone says, you are convinced that we cannot meet your needs.  So what can I say to convince you to take it elsewhere?  If you are serious about producing a better product, I invite you to put your money where your mouth is.  Start a site, solicit some like-minded people to work on it with you, and feel free to use any portion of the MythTV code you like, so long as the result is GPLv2.  Minimally, demonstrate some common sense and see that drumming up a revolution against MythTV is not going to be particularly effective when you do it under the auspices of a MythTV-specific forum.
Here's what my deal is...

I tried several times on the MythTV mailing list, and it was like banging my head on a brick wall.

It took being straightforwardly antagonistic towards the project, and suggest it might need to be abandoned, for you to come here any admit there were major problems with MythTV.

And really, what do you think I'm *doing*? I'm not putting that system design together for jollies, or to upset you.  I'm doing it in hopes that some programmers who agree that MythTV is broken, might take it up. I'll accept you cleaning up MythTV's issues instead, because the MythTV backend with a lot of work could take up the place of the TV source. But you'd have to drop your incomprehensible refusal to support third-party frontends.

And again, this is an Ubuntu forum, not MythTV's backyard. Where else might I best find User-friendly developers interested in PVR systems?

---

### Post by barberio on 2010-08-05
> **iamlindoro said:**
> 
[http://www.mythtv.org/wiki/Protocol](http://www.mythtv.org/wiki/Protocol)

Each protocol command is clickable, with its own doc page.


You have a unique definition of documented. Would someone be able to re-create a server and client from that documentation? Could you draw me a state-diagram for this protocol?

I also note how you directly refer to other developer's attempts as badly implemented and dangerous. And you say that because they don't try to keep up with a moving target of a constantly changing protocol for a server that refuses to talk to earlier protocol version clients.

Did you happen to talk to these developers before you called their work badly implemented and dangerous?

By your own words, you would have no standing to complain about their work if you haven't submitted patches to their projects. Have you?

---

### Post by iamlindoro on 2010-08-05
> **barberio said:**
> Er... No... This is a UBUNTU forum. 

What are these long term plans?

Can you show me a system design for MythTV?

Can you show me a protocol spec for MythTV?

Can you show me a development roadmap?

If you can show me these things, I'll back down on MythTV being dysfunctional.

I have posted the protocol documentation above.  Our task and bug roadmap is available in trac by clicking "Roadmap."  Our developement tasks/plans are documented on the trac wiki as well.  Any further planning information is freely available by simply *asking* on the developer list or in #mythtv on freenode.  If someone would like more detailed information, they need only ask.

> But until you *have those things*, your project is dysfunctional.

I accept your apology.

> There are lots of interesting legacy issues with MythTV, not least of which is using *nupple video*.

Actually, the player no longer references Nuppel Video, and the container itself is slated for replacement.  The NUV container is *only* used when capturing with framegrabbers *** lossily transcoding, and is easily remuxed in those limited scenarios.

> See, there's your problem.

You don't want to listen to anyone who isn't going to directly assist you with coding.

So by definition, you're *not* open to new design ideas. Because the best designers are often not the best implementers. Just as someone who's good at setting up QA testing isn't always good at doing the programming to fix the bugs they find. So you're instantly limiting the project.

Necessarily, this is true.  I'll reiterate that we do not lack for ideas or design.  We lack implementors.  We all have a very firm idea of where we want to see MythTV go, but lack the manpower to accomplish it.  So, when someone "rescues" us by providing a conflicting viewpoint, we can't help but disappoint them.  Sorry.

> And again, this is an Ubuntu forum, not MythTV's backyard. Where else might I best find User-friendly developers interested in PVR systems?

I suggest someplace more software-agnostic.  This particular forum is for Mythbuntu, which means you are speaking to MythTV users only.  Common sense suggests that you will find people who prefer it to other solutions.  If you want to find people share your poor opinion of MythTV, I suggest somewhere not composed entirely of MythTV users.

But once again to the point, when can we expect work to begin on your solution which is, in your own words, simple to implement?

Robert

---

### Post by iamlindoro on 2010-08-05
> **barberio said:**
> By your own words, you would have no standing to complain about their work if you haven't submitted patches to their projects. Have you?

Why would I?  I don't want to use them, I certainly don't need to work to fix them.  If they want recognition as a safe frontend, they can use the documentation to make themselves one.

It appears you have not carefully read the protocol docs, which also link a Guide that talks you through a basic communication.  So yes, while you might be unable to produce a frontend from the docs, someone capable of actually writing a frontend could.

The Python bindings are also exhaustively documented and could be used to produce a qualifying frontend.

Robert

---

### Post by barberio on 2010-08-05
> **iamlindoro said:**
> Why would I?  I don't want to use them, I certainly don't need to work to fix them.  If they want recognition as a safe frontend, they can use the documentation to make themselves one.


Again side stepping that the reason why it's hard to develop an independent MythTV client library; that you sustain the protocol as a moving target and make the server reject previous protocol version rather than try to handle them.

> 
It appears you have not carefully read the protocol docs, which also link a Guide that talks you through a basic communication.  So yes, while you might be unable to produce a frontend from the docs, someone capable of actually writing a frontend could.


Since the XBMC project abandoned their recent attempts to make a MythTV frontend, I suspect not.

And again can you show me a state-diagram of your protocol? Look it up on wikipedia if you don't know what the term means.

> 
The Python bindings are also exhaustively documented and could be used to produce a qualifying frontend.
While the python bindings allow for data retrevel, and control of a backend and a mythtv frontend, it does not appear possible to create a replacement frontend client from the python bindings.

If it is your intent that the Python bindings should be used to do so, you need to focus some work there. I'd also strongly suggest defining a strict API document that you code to, rather than the other way around, otherwise you will have simply recreated the moving target problem as a python API.

I'd also wonder why you haven't created a general purpose shared library API.

---

### Post by barberio on 2010-08-05
> **iamlindoro said:**
> I have posted the protocol documentation above.  Our task and bug roadmap is available in trac by clicking "Roadmap."  Our developement tasks/plans are documented on the trac wiki as well.  Any further planning information is freely available by simply *asking* on the developer list or in #mythtv on freenode.  If someone would like more detailed information, they need only ask.

That's not actually what a roadmap is, you've let the Trac interface trick you into thinking it offers you full-service project management when it doesn't.

The Trac roadmap is only your bug-fixing roadmap.

This - [https://wiki.ubuntu.com/MaverickReleaseSchedule](https://wiki.ubuntu.com/MaverickReleaseSchedule) - is a Roadmap. It lays out a development cycle that produces a new stable version. You know when there will be a feature-freeze cut off point after which new features won't be added to the stable branch. You identify the design, development, testing focus phases.

"We'll put all of X stuff in version Y" is not a Roadmap.

---

### Post by barberio on 2010-08-05
> **iamlindoro said:**
> 
Necessarily, this is true.  I'll reiterate that we do not lack for ideas or design.  We lack implementors.  We all have a very firm idea of where we want to see MythTV go, but lack the manpower to accomplish it.  So, when someone "rescues" us by providing a conflicting viewpoint, we can't help but disappoint them.  Sorry.


Dare I suggest you have enough coders. You're just handling your project resources in a hugely inefficient manner.

By refusing assistance from testers and people who could be managing your ticket reports for you, you're piling that work on your programmers. If you weren't so hostile to non-coders, you wouldn't have had to "waste your time" on all those users who don't know how to find and upload debug logs, you'd have non-coders who would *want* to do that for you. Don't like documenting, there are people out there who are not hard-core coders but can and will spend their time documenting a system for users, you don't have to waste programmer time on doing an inefficient job on the now programming tasks.

Be declaring that you're not going to accept help on the project from non-programmers, you're making more work for yourself, and making your project isolationist and hostile.

---

### Post by iamlindoro on 2010-08-05
> **barberio said:**
> Dare I suggest you have enough coders. You're just handling your project resources in a hugely inefficient manner.

You can suggest anything you like, but as you are entirely unfamiliar with our development (and moreover, it seems you are willfully ignorant when presented with contradictory information), it would only be a suggestion and not statement of fact.

> By refusing assistance from testers and people who could be managing your ticket reports for you, you're piling that work on your programmers. If you weren't so hostile to non-coders, you wouldn't have had to "waste your time" on all those users who don't know how to find and upload debug logs, you'd have non-coders who would *want* to do that for you. Don't like documenting, there are people out there who are not hard-core coders but can and will spend their time documenting a system for users, you don't have to waste programmer time on doing an inefficient job on the now programming tasks.

Be declaring that you're not going to accept help on the project from non-programmers, you're making more work for yourself, and making your project isolationist and hostile.

One can only conclude that you are happier cutting down than building up.  A search of our mailing lists archives suggests that this desire to order others around is a way of life for you, and it's no wonder that you felt unwelcome in our community-- Your hysterical and antagonistic ramblings and dictatorial behavior were evident from your very earliest postings to our lists, and others quite naturally took your desire to order them around personally.  I have attempted to take a diplomatic tone and calmly address your concerns in this thread, but it is all too evident that nothing we can possibly do will be enough.

I do not work for you, nor does any other Myth dev.  You have yet to offer anything new or revolutionary to the discussion.  You are so convinced that we have no plan, no documentation, and no goal that any attempt to enlighten you as to reality is met with further rudeness.  I am officially done with this thread and will respond no further.  There are intangibles involved in working with anyone, and even if you were offering me the holy grail itself, the cost of working with you appears to be just too darn high.

On behalf of myself, I do not feel you have anything to offer us, and I hope that you will take my this interaction as a friendly challenge to put your money where your mouth is.  Prove me wrong.  Competition is good and I would love to see what you come up with.  I have a rather firm belief that your aspirations to come up with anything even remotely as capable as MythTV will start and end in this thread.

Best of luck,

Robert

---

### Post by barberio on 2010-08-05
> **iamlindoro said:**
> 
One can only conclude that you are happier cutting down than building up.  A search of our mailing lists archives suggests that this desire to order others around is a way of life for you, and it's no wonder that you felt unwelcome in our community-- Your hysterical and antagonistic ramblings and dictatorial behavior were evident from your very earliest postings to our lists, and others quite naturally took your desire to order them around personally.  I have attempted to take a diplomatic tone and calmly address your concerns in this thread, but it is all too evident that nothing we can possibly do will be enough.


I have never been rude to you. On the contrary, you set out to belittle, diminish and insult me. If this is your diplomatic tone, I'd hate to see you deliberately trying to upset me.

You have only provided half answers to my questions. Then berated me when I pointed that out. You conveniently ignored my concerns about the lack of true 'Stable Release' branching, and the 'Moving Target' problem of the protocol. 

If it were possible to make a replacement MythTV Frontend, then there would have been one created. The XBMC had a Google Summer of Code funded project part of which was trying to do just that! They failed, and abandoned the idea.

The MythTV project refuses to support third party frontends, and the way the project is managed  and the design of the system makes it hard to create one.

> 
On behalf of myself, I do not feel you have anything to offer us, and I hope that you will take my this interaction as a friendly challenge to put your money where your mouth is.  Prove me wrong.  Competition is good and I would love to see what you come up with.  I have a rather firm belief that your aspirations to come up with anything even remotely as capable as MythTV will start and end in this thread.

Best of luck,

Robert

Frankly, you came here to squash me. And you now appear to be trying to bully me out of organising an alternative to MythTV, by telling me I'm doomed to fail. And telling others I am incompetent, to try and disaude anyone from working with me.

Your behaviour has been that of a bully.

---

### Post by nickrout on 2010-08-05
> **barberio said:**
> 

If it is your intent that the Python bindings should be used to do so, you need to focus some work there. I'd also strongly suggest defining a strict API document that you code to, rather than the other way around, otherwise you will have simply recreated the moving target problem as a python API.

I'd also wonder why you haven't created a general purpose shared library API.

I think you miss the IMHO important point that mythtv, although getting more stable all the time, deliberately doesn't have a stable API because it is still in development. As new features are added both the database schema and mythprotocol must change. 

The clue is in the version numbers. Current release is **zero **point two three not **one** point two three.

---

### Post by tgm4883 on 2010-08-05
> **barberio said:**
> Don't like documenting, there are people out there who are not hard-core coders but can and will spend their time documenting a system for users, you don't have to waste programmer time on doing an inefficient job on the now programming tasks.

I actually laughed out loud when I read that. If these people exist, I surely haven't met them. Sure I've met the occasional people that would pitch in for a short while, but the shear fact that the Mythbuntu documentation (wiki) is in such bad shape is testimony to the fact that these people are far and few between.

Barberio, you are argumentative and appear to see your way as the only way. Iamlindoro isn't trying to disuade people from wanting to work with you, you are doing a pretty good job of that yourself.

As for this thread. This is the official Mythbuntu forum and we need to keep it civil. Let this stand as a warning that we need to keep a civil tone when posting here If this thread continues down this path, I will need to take action.

---

### Post by barberio on 2010-08-06
> **nickrout said:**
> I think you miss the IMHO important point that mythtv, although getting more stable all the time, deliberately doesn't have a stable API because it is still in development. As new features are added both the database schema and mythprotocol must change. 

The clue is in the version numbers. Current release is **zero **point two three not **one** point two three.

Eight years is a long time to still be in Alpha. At what point would the MythTV project consider creating a stable API?

---

### Post by barberio on 2010-08-06
> **tgm4883 said:**
> I actually laughed out loud when I read that. If these people exist, I surely haven't met them. Sure I've met the occasional people that would pitch in for a short while, but the shear fact that the Mythbuntu documentation (wiki) is in such bad shape is testimony to the fact that these people are far and few between.

Barberio, you are argumentative and appear to see your way as the only way. Iamlindoro isn't trying to disuade people from wanting to work with you, you are doing a pretty good job of that yourself.

As for this thread. This is the official Mythbuntu forum and we need to keep it civil. Let this stand as a warning that we need to keep a civil tone when posting here If this thread continues down this path, I will need to take action.

I'm sorry if I came off as argumentative... But the "Patches or GTFO" ethos *does* annoy those of us who want to contribute, but can't because Uber Coders only want to talk to Uber Coders.

And yes, these people *do* Exist. Look at Ubuntu. Look at Ubuntu's wiki. That's because Ubutnu welcomes non-coders, and doesn't require you to sign up to a developer mailing list and contribute patches to have a say.

---

### Post by nickrout on 2010-08-06
> **barberio said:**
> I'm sorry if I came off as argumentative... But the "Patches or GTFO" ethos *does* annoy those of us who want to contribute, but can't because Uber Coders only want to talk to Uber Coders.

And yes, these people *do* Exist. Look at Ubuntu. Look at Ubuntu's wiki. That's because Ubutnu welcomes non-coders, and doesn't require you to sign up to a developer mailing list and contribute patches to have a say.

There is no qualification on contributing documentation. go to the myth wiki and contribute.

Go to the feature request page and suggest a code refactor to take into account your ideas.

But you will achieve NOTHING here. This forum is dedicated to mythbuntu. mythbuntu <> mythtv. mythbuntu merely follows mythtv and fits it into the *buntu framework, and provides some useful tools like control-centre. This is not the place to achieve change to mythtv. So stop pissing into the wind. I could be blunter, and maybe you need blunt, but I won't use the language here that I feel when I hear your arrogance.

PS I have seen people go from being pilloried the "circle" to becoming members of the dev team, so it's not impossible. Prove yourself with usefulness and you WILL be accepted.

---

### Post by barberio on 2010-08-06
Ah, a little looking around for what XBMC's experiemental PVR client supports, and I find [http://lonelycoder.com/hts/tvheadend_overview.html](http://lonelycoder.com/hts/tvheadend_overview.html) which looks promising and seems deserving of my contributions.

Good bye MythTV. I won't miss your developers.

---

### Post by nickrout on 2010-08-06
I am sure the feeling is mutual.

tvheadend looks interesting, albeit limited.

---

### Post by wombo on 2010-08-07
barberio, Can I please ask if you could start documenting Mythtv based on what you have said you have the skills.

All you need is to register on their Wiki, then start reading and typing.

Pretty easy actually, hope to see some good things from you soon :)

---

### Post by barberio on 2010-08-07
> **wombo said:**
> barberio, Can I please ask if you could start documenting Mythtv based on what you have said you have the skills.

All you need is to register on their Wiki, then start reading and typing.

Pretty easy actually, hope to see some good things from you soon :)

Nope. As I mentioned, I'll be directing my efforts towards tvheadend. I'm sorry but MythTV is not worth the effort to document, because the developers refuse to maintain any stability that would make documentation meaningful.

A project that spends eight years without defining a stable API or protocol, is a dysfunctional project.

---

### Post by LowSky on 2010-08-09
> **barberio said:**
> Nope. As I mentioned, I'll be directing my efforts towards tvheadend. I'm sorry but MythTV is not worth the effort to document, because the developers refuse to maintain any stability that would make documentation meaningful.

A project that spends eight years without defining a stable API or protocol, is a dysfunctional project.

I just read through this 5 pages of quarreling and I just laughed a lot.

I'm a heavy Ubuntu supporter, and I try my best to help in the Mythbuntu area as much as possible. I might not know how to code but I know how to write a kick-*** tutorial. When it comes to fixing a solution I try to find simple and easy to follow instructions and pass that info on. I help where I can.

MythTV is a huge project and I think people overlook the amount of hard work that goes into maintaining it. So when people do complain and the developers try to fight back both come out looking like jackasses. People like barberio want things a certain way. I think all he wanted to do was vent, but a few developers caught wind and decided to vent back. And a political correctiveness word battle ensued.

My personal fight is to create a better UI. I think MythTV lacks in that department a great deal. But I'm horrible at coding so what I'm doing is trying to learn and in the process taking an existing theme and modifying to work the way I want it to, until I can build one from scratch. I don't bash the creators for their work. They made what they think is good but for me it isn't hence my own theme.

If these forums have told me anything, is that if you want to vent here, be prepared for criticism.

---

### Post by jlipoth on 2010-09-08
I don't know much about what goes on behind the scenes, but there has been a change for the worse in my experience on the user end.  

In 2006 I used GBPVR and enjoyed it quite a bit until it started getting buggy in 2007.  On a whim I made a Mythbuntu CD and was up and running in 20-30 minutes - I was amazed!  Since then I have upgraded to each new version of Mythbuntu as it came out, which usually had some trade off (new features and old bug fixes for new bugs), but everything seemed to run quite well: well enough to make it our family mediacentre.  

I could be off by a version, but it seemed that somewhere around version 9.10 I started getting phone calls from my wife about the database breaking or the tuners would quit working.  Strange enough the solution usually ended up in getting some developmental builds (or something like that - once again I don't know much about all the background stuff).  This once again introduced some fixes and a host of other bugs.   

All in all, it strikes me as strange to have a major release (Mythbuntu installed straight off the CD with basic updates) that is so buggy and the developmental builds to be more stable (although still buggy because of the nature of what they are).  Isn't this kinda backwards?

I personally am not angry at anyone; however, I am disappointed that something our family relies on has now become so unreliable. I do not want to switch to a different media centre setup, but unless something has changed or is changing in the near future, I really don't have much of a choice.

I guess my question is, "does it look like this issue will be fixed?"

Thanks

---

### Post by tgm4883 on 2010-09-08
> **jlipoth said:**
> I don't know much about what goes on behind the scenes, but there has been a change for the worse in my experience on the user end.  

In 2006 I used GBPVR and enjoyed it quite a bit until it started getting buggy in 2007.  On a whim I made a Mythbuntu CD and was up and running in 20-30 minutes - I was amazed!  Since then I have upgraded to each new version of Mythbuntu as it came out, which usually had some trade off (new features and old bug fixes for new bugs), but everything seemed to run quite well: well enough to make it our family mediacentre.  

I could be off by a version, but it seemed that somewhere around version 9.10 I started getting phone calls from my wife about the database breaking or the tuners would quit working.  Strange enough the solution usually ended up in getting some developmental builds (or something like that - once again I don't know much about all the background stuff).  This once again introduced some fixes and a host of other bugs.   

All in all, it strikes me as strange to have a major release (Mythbuntu installed straight off the CD with basic updates) that is so buggy and the developmental builds to be more stable (although still buggy because of the nature of what they are).  Isn't this kinda backwards?

I personally am not angry at anyone; however, I am disappointed that something our family relies on has now become so unreliable. I do not want to switch to a different media centre setup, but unless something has changed or is changing in the near future, I really don't have much of a choice.

I guess my question is, "does it look like this issue will be fixed?"

Thanks

You probably weren't running the development build, you were probably running auto-builds from the fixes branch. This is something that the Mythbuntu team recommends to do anyway.

In the future, we aren't planning on shipping non-released versions of MythTV (previous two releases actually shipped with RCs), so that might be what you are looking for as a change for the future. We will still provide auto-builds for people who want to stick with a Mythbuntu release and update to the next version of MythTV

---

### Post by jlipoth on 2010-09-08
That sounds promising enough to give Mythbuntu another try when 10.10 comes out.  I think it is a safe bet the using the Release Candidate may have been the source of my problems.  Thanks for the clarification on the autobuilds.  As long as autobuilds introduces updates are aimed at "use" and not "testing", they are fine by me. Will the recommendation of using auto builds continue for the next versions of Mythbuntu or was that more important because the last two versions were using the RC?

---

### Post by tgm4883 on 2010-09-08
> **jlipoth said:**
> That sounds promising enough to give Mythbuntu another try when 10.10 comes out.  I think it is a safe bet the using the Release Candidate may have been the source of my problems.  Thanks for the clarification on the autobuilds.  As long as autobuilds introduces updates are aimed at "use" and not "testing", they are fine by me. Will the recommendation of using auto builds continue for the next versions of Mythbuntu or was that more important because the last two versions were using the RC?

It was more important on previous versions. Usually i recommend not touching it unless you need to. Upstream provides commits for 2 branches, fixes and trunk, so using the auto-builds from the fixes branch may be beneficial

---

### Post by dborn on 2010-10-05
Wow, that was an interesting thread... :shock:

All I'd like to add is this: I'm currently using Mythbuntu 9.10 and I'm in the process of upgrading to 10.04 which is proving to be a challenge for the Linux semi-noob that I am.
But that's fine, I LIKE doing that. I learn as I go along and I am proud of myself when I get it working _just_ the way I want. If I wanted something that was closed, off-the-shelf and stable and "just works", I'd go buy it and then *demand* for it to be fixed when it breaks.

I tip my hat off to all the devs and _volunteers_ that work on projects such as Myth because they are much more talented, dedicated and willing than I am. What I get for the money and effort I put into it, is VASTLY superior (in my mind) to any off-the-shelf commercial product out there (warts and all).

Yes there are problems but I have confidence that they will get sorted out with minimal effort on my part.

Cheers,
Daniel Born
P.S. At some point, I'd love to contribute something back to the project but for now my main "effort" is to use it and be thankful for it.

---

### Post by nickrout on 2010-10-06
> **dborn said:**
> 
P.S. At some point, I'd love to contribute something back to the project but for now my main "effort" is to use it and be thankful for it.

By posting here you contribute. By reporting bugs you contribute. By posting questions here, that other people answer and are recorded here for posterity you contribute.

---

### Post by IceCap on 2010-10-06
Maybe it is a generation thing.  Young(er) people that are about to reach adulthood (I love using that word, it makes them mad) seem to take lot of things for granted and expect to get get most of it for free.  Like, they can get free movies, free pass on performing at school, free music, and of course, free software that someone else writes (and plans, and documents, and tests, and fixes, ....).

  My bet is that the thread author falls into this category.

  IC

BTW, 10.04 with the fixes seems to work great.  With the exception of LIRC and some Flash player issues (can we move away from Flash please...) everything seems to work on my combined backend-frontend.  Thanks

---

### Post by torrent99 on 2010-10-27
Barberio I'm with you on this one, myth really has become a bit of a spaghetti project, and recently has started to concentrate on UI glitz over core, stable functionality.
 
This wouldn't be a problem, however because of the lack of a ***stable**, defined protocol it means that even when stability changes to the backend occur they can't be installed without also upgrading the frontend. Naturally that comes with all the UI glitz which isn't compatible with older hardware. 
 
Many of us spent a lot of time and money building specific hardware for our specific media PC task (in my case playing SD only).  Many hours were spent building the hardware to be silent and neat. Now I find that to get improved backend stability features I have to upgrade my hardware completely! Had the protocol at least remained stable, this would not be the case, the frontend software could have remained the same with an updated backend providing fixes e.g. for DVB tuning and EIT that the older versions struggled with.
 
So if I had a wish list for 0.25 or 0.26 it would be:
   * No new features. (apart from ones that make it easier to maintain and more robust).
   * Make it rock rock solid. (e.g. the backend should always record what it's asked to no matter what, it should try, try and try again! WAF is important and there's nothing worse that missing a recording for WAF)
    * A stable, defined protocol that third parties can work with. (Commercial hardware HD Myth client anyone? Won't happen until the protocol can be relied upon to be stable.)
    * Ability to tune out the glitz features at all levels so you canget a nice, basic, solid system.
    * When it's solid, back to the new features.... :-)
 
However, it's easy to criticize and harder to make a useful contribution. It would take a gargantuan effort to fix some of the spaghetti code in Myth, and I'm sure the devs like anyone else would prefer to concentrate on the sexier elements of the app. As I only get about 2hrs a week tops to maintain my PVR, I'm unable to contribute properly myself (though I have done one or 2 wiki pages). I guess I'll have to concentrate on backporting stability fixes to old versions in future.
 
 
I do agree that the devs attitude can sometimes leave a bit to be desired, and this extends to all areas, I've even seen snide comments in the source code!!! But then it's probably pretty stressful being the most popular linux PVR and having to support all of us users.
 
  
 
Anyway, if you are looking for another PVR software to contribute to, may I suggest Freevo? 
Freevo has taken the route of using existing programs such as DVBStreamer and mplayer to solve some of the "heavy lifting" problems, and so is much freer to concentrate on building a solid architecture. Freevo 2.0 looks like it could be very good, and the codebase is still small enough to understand fairly quickly. There are very few devs at the moment and I'm sure they'd welcome a new one with open arms!

---

### Post by Don Geddis on 2010-11-03
So, I'm confused about how this is all supposed to work, from an end-user's perspective.  What design do the mythtv people have in mind?

I've got a backend running Debian.  My mythtv-backend version there is "the latest", version "0.23.1-0.1".  There is no newer version even in unstable.

On my desktop, I was running Ubuntu 10.4 until this morning.  I just upgraded to 10.10.  My previous myth-frontend worked just fine with my backend server.  Now, since the upgrade to 10.10, the version of mythtv I seem to be running is "0.23.1+fixes26437-0ubuntu1".

So.  BOTH versions, front and backend, seem to have a version number of "0.23.1".  But they're running protocol versions that are SO incompatible, they now refuse to work together at all?  My front-end claims to be using protocol "23056", while the backend is using protocol "56".

Surely even the mythtv developers will admit, that if they're going to break compatibility between front ends and back ends, what greater change can there possibly be, to require a new version number?  It's insane that these incompatible builds are both given the version number "0.23.1".

If anyone has a workaround, please let me know.  As it is, I no longer have a way to watch any of my tv shows.  And I don't know when (or if) this will ever be fixed: Debian doesn't even seem to have a later version in the pipeline.  (And how could I tell, anyway, since apparently the version number of the "fixed" software will still be 0.23.1.)

---

### Post by tgm4883 on 2010-11-03
> **Don Geddis said:**
> So, I'm confused about how this is all supposed to work, from an end-user's perspective.  What design do the mythtv people have in mind?

I've got a backend running Debian.  My mythtv-backend version there is "the latest", version "0.23.1-0.1".  There is no newer version even in unstable.

On my desktop, I was running Ubuntu 10.4 until this morning.  I just upgraded to 10.10.  My previous myth-frontend worked just fine with my backend server.  Now, since the upgrade to 10.10, the version of mythtv I seem to be running is "0.23.1+fixes26437-0ubuntu1".

So.  BOTH versions, front and backend, seem to have a version number of "0.23.1".  But they're running protocol versions that are SO incompatible, they now refuse to work together at all?  My front-end claims to be using protocol "23056", while the backend is using protocol "56".

Surely even the mythtv developers will admit, that if they're going to break compatibility between front ends and back ends, what greater change can there possibly be, to require a new version number?  It's insane that these incompatible builds are both given the version number "0.23.1".

If anyone has a workaround, please let me know.  As it is, I no longer have a way to watch any of my tv shows.  And I don't know when (or if) this will ever be fixed: Debian doesn't even seem to have a later version in the pipeline.  (And how could I tell, anyway, since apparently the version number of the "fixed" software will still be 0.23.1.)

That isn't a MythTV issue. That's a packaging issue with Debian. 0.23.1 works with all other 0.23.1 versions. I assure you that the version in Debian that is reporting 0.23.1 is in fact not 0.23.1. It looks like Debian packaged an old version of MythTV and called it 0.23.1. You will likely need to file a bug report against the debian package for this to get fixed. 

On the Debian backend, what does this report

```
mythbackend --version
```

---

### Post by Don Geddis on 2010-11-03
Thank you for the reply.  I tried running your query ... and discovered that I'm a total idiot.  I had forgotten that I had moved my mythtv backend to a completely different server than I originally set it up on.  I unfairly disparaged both mythtv and/or Debian in my original post.

In truth, my actual mythtv backend is running Ubuntu (Mythbuntu) 10.4, and surely all I need to do is upgrade to 10.10.

I apologize for wasting everybody's time.

---

### Post by tgm4883 on 2010-11-03
> **Don Geddis said:**
> Thank you for the reply.  I tried running your query ... and discovered that I'm a total idiot.  I had forgotten that I had moved my mythtv backend to a completely different server than I originally set it up on.  I unfairly disparaged both mythtv and/or Debian in my original post.

In truth, my actual mythtv backend is running Ubuntu (Mythbuntu) 10.4, and surely all I need to do is upgrade to 10.10.

I apologize for wasting everybody's time.

No worries, you actually don't even need to upgrade to 10.10. You can activate autobuilds and select 0.23.1 on 10.04

[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

