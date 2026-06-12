---
title: "F-Spot would be excluded? Good news."
date: 2010-06-14
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by vkontakte on 2010-06-14
[http://www.techdrivein.com/2010/06/meet-shotwell-f-spot-replacement-for.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+techdrivein+(Tech+Drive-in](http://www.techdrivein.com/2010/06/meet-shotwell-f-spot-replacement-for.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+techdrivein+(Tech+Drive-in))

---

### Post by bruno9779 on 2010-06-14
It was time.

F-spot is so buggy it drives me insane

---

### Post by bruno9779 on 2010-06-14
One less app using mono

:popcorn:

---

### Post by ibuclaw on 2010-06-14
> **bruno9779 said:**
> One less app using mono

:popcorn:

Does that make Tomboy the only application depending on Mono now in the default install?

Nothing against it, am just thinking of [this thread]("http://ubuntuforums.org/showthread.php?t=1506025"). Where aptitude has been announced to be removed to save 2MB of space.

Removing all mono applications + runtime will save 60MB of space.

---

### Post by Reiger on 2010-06-14
I think so. Unless Banshee becomes default?

---

### Post by zekopeko on 2010-06-14
> **ibuclaw said:**
> Does that make Tomboy the only application depending on Mono now in the default install?

Nothing against it, am just thinking of [this thread]("http://ubuntuforums.org/showthread.php?t=1506025"). Where aptitude has been announced to be removed to save 2MB of space.

Removing all mono applications + runtime will save 60MB of space.

Gbrainy uses Mono.

---

### Post by kahumba on 2010-06-14
> **bruno9779 said:**
> One less app using mono

:popcorn:
+1

@zekopeko
Gbrainy is unimportant and those who want it can still install it. For tomboy we got Gnote which starts up faster and uses less memory. A win-win situation for all except for mono devs and m$ apologists. Period.

---

### Post by kahumba on 2010-06-14
> **ibuclaw said:**
> Does that make Tomboy the only application depending on Mono now in the default install?

Nothing against it, am just thinking of [this thread]("http://ubuntuforums.org/showthread.php?t=1506025"). Where aptitude has been announced to be removed to save 2MB of space.

Removing all mono applications + runtime will save 60MB of space.
I agree, here's more people thinking about it, see comment by gweaver:
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-maverick-shotwell](https://blueprints.launchpad.net/ubuntu/+spec/desktop-maverick-shotwell)

---

### Post by vkontakte on 2010-06-14
> **zekopeko said:**
> Gbrainy uses Mono.
Gbrainy is a nonsense. Using number1, number2, number3 notion in equations is ever stupid idea. This application is pointless and an excellent candidate for exclusion.

---

### Post by zekopeko on 2010-06-14
> **kahumba said:**
> +1

@zekopeko
Gbrainy is unimportant and those who want it can still install it. For tomboy we got Gnote which starts up faster and uses less memory. A win-win situation for all except for mono devs and m$ apologists. Period.

Gbrainy is installed by default. It is going to rock once RB is replaced with Banshee and hopefully Pinta gets added to the default install.

---

### Post by kahumba on 2010-06-14
> **zekopeko said:**
> Gbrainy is installed by default. 
Who cares about this unimportant crap except you? Rhetoric question.
> **zekopeko said:**
> 
It is going to rock once RB is replaced with Banshee and hopefully Pinta  gets added to the default install.

Give me a break with Banshee, there we have a mono lobbyist right here. Has Canonical **confirmed** your dreams about more mono crap like pinta and banshee or is it based on "someone said it somewhere" that is, based on the "wisdom" of the crowd?

---

### Post by philinux on 2010-06-14
Ok, lets keep the mono debate off the agenda in this forum.

Final warning.

---

### Post by vkontakte on 2010-06-14
> **zekopeko said:**
> Gbrainy is installed by default. It is going to rock once RB is replaced with Banshee and hopefully Pinta gets added to the default install.
Luckily, in most cases Canonical just follows Debian. The Debian itself follows GNOME Foundation. And there is the trend in G.F. of exclusion of mono apps. So, it's highly unlikely is going to happen for pinta to be included. On the other hand, Banshee most probably won't be default in Ubuntu, because it's more a thing to fun for its devs than a player and suffers from many minor glitches and general slowness. In addition it has no major advances over the RB. Moreover, its roadmap promises it will be too overbloated to be a default **audio player** soon.

---

### Post by taavikko on 2010-06-14
> **vkontakte said:**
> Gbrainy is a nonsense. Using number1, number2, number3 notion in equations is ever stupid idea. This application is pointless and an excellent candidate for exclusion.

Have to agree on this, this particular game, is a load of bullocks.
If I want a brain teaser, I'll just try to remember what I ate for breakfast.

But for topic, shotwell is showing potential on my use cases.
Few crashes here and there, but so far looking good.

Don't really care the debacle on should mono be annihilated from default install, but if the only things depending on it is gbrainy and tomboy.....

---

### Post by MacUntu on 2010-06-14
About time. I don't need an app that changes my files without asking me first (the rotate function directly writes metadata to the file).

---

### Post by gnomeuser on 2010-06-14
Shotwell currently don't migrate data from F-Spot afaik which is going to be a major pain. additionally since F-spot just got a new maintainer as well as a fairly active development tree moving away from it now seems like a silly gamble.

We are talking a completely new user experience and non migration of existing data. Moving to very new code in a language that isn't even stable yet (correct me if I am wrong here but I recall it being developed in Vala). This alone sounds kinds sketchy.

Personally I will continue to use F-Spot it is by far the best photomanager I have ever used and I trust its new maintainer to continue to drive important improvements.

I think replacing it will prove to be a mistake.

---

### Post by gnomeuser on 2010-06-14
> **vkontakte said:**
> Luckily, in most cases Canonical just follows Debian. The Debian itself follows GNOME Foundation. And there is the trend in G.F. of exclusion of mono apps. So, it's highly unlikely is going to happen for pinta to be included. On the other hand, Banshee most probably won't be default in Ubuntu, because it's more a thing to fun for its devs than a player and suffers from many minor glitches and general slowness. In addition it has no major advances over the RB. Moreover, its roadmap promises it will be too overbloated to be a default **audio player** soon.

For a toy it sure has a lot of support, e.g. Moovida just moved their code to use Banshee since that data handling is so good.

It has also been made the default mediaplayer in MeeGo (currently for the netbook ux but potentially others as well). 

We already addressed every single complaint we had for making it default in Karmic. It was debated at UDS but so far nobody has given the Banshee community a new list of complaints to address. I know that iPod/iPhone support is needed and Alan McGovern added that support this week (to land in respective upstreams next week). I see no blockers anymore, in addition you get all kinds of wonderful support.

Banshee is a highly mature _mediaplayer_ with an active community and a good track record both for delivering features and bugfixes.

If you have reproducable bugs please do file them so we can fix them.

---

### Post by 23meg on 2010-06-14
> **gnomeuser said:**
> Shotwell currently don't migrate data from F-Spot afaik which is going to be a major pain.

[QUOTE=gnomeuser]and non migration of existing data[/QUOTE]

It's [being worked on]("https://bugs.launchpad.net/ubuntu/+source/shotwell/+bug/579803/comments/3") [upstream]("http://trac.yorba.org/ticket/139").

---

### Post by zekopeko on 2010-06-14
> **vkontakte said:**
> Luckily, in most cases Canonical just follows Debian. The Debian itself follows GNOME Foundation. And there is the trend in G.F. of exclusion of mono apps.

I don't quite follow. Just the other day you were expressing how displeased you are with indicators which are an Ubuntu-only thing for now.

> So, it's highly unlikely is going to happen for pinta to be included. On the other hand, Banshee most probably won't be default in Ubuntu, because it's more a thing to fun for its devs than a player and suffers from many minor glitches and general slowness. In addition it has no major advances over the RB. Moreover, its roadmap promises it will be too overbloated to be a default **audio player** soon.

Actually I believe you are wrong. What Banshee has and RB doesn't is support from two companies, Novell and Fluendo. Both are using it in their products. Further more Banshee is the default player in Meego. 

But I agree with you that Banshee is more then an audio player. It's a media player. So if they include it they can drop Totem. And include Pinta since it's such a small application but with great functionality (it's only 0.5 MB!). Heck they could write a simple interface to Banshee that would look exactly like Totem. And you know what is even more cool? F-spot is being re-based on parts of Banshee so it will consume even less space! Win-win! Isn't FOSS amazing?

---

### Post by vkontakte on 2010-06-14
> **gnomeuser said:**
> We already addressed every single complaint we had for making it default in Karmic. It was debated at UDS but so far nobody has given the Banshee community a new list of complaints to address. I know that iPod/iPhone support is needed and Alan McGovern added that support this week (to land in respective upstreams next week). I see no blockers anymore, in addition you get all kinds of wonderful support.
Last time they said my bug was a feature. I don't want to waste my time anymore on filling bugs that are really "features".
> Banshee is a highly mature _mediaplayer_ with an active community and a good track record both for delivering features and bugfixes.
"Mediaplayer" based on gstreamer? You must be joking!
Gstreamer is horribly slow and lack of essential features like interlacing support, vdpau support, etc.
So, the video mode is pointless but still take additional memory.

[http://arstechnica.com/open-source/news/2009/07/netbook-ui-photo-management-coming-to-banshee-media-player.ars](http://arstechnica.com/open-source/news/2009/07/netbook-ui-photo-management-coming-to-banshee-media-player.ars)

The interface :mrgreen:
Canonical insists they are like being "consistent". I would be very amazed if they let such a "consistency" app being the default. 

BTW. Does Banshee have essential an audio-playback feature RB doesn't have? I can't find anyone. As I said the Banshee is a toi for its developers, not the app that could be the default media player. They always break things in it, always add useless things like F-Spot features integration, etc. I'm sure canonical won't include it in the default set.

---

### Post by vkontakte on 2010-06-14
> **zekopeko said:**
> But I agree with you that Banshee is more then an audio player. It's a media player. So if they include it they can drop Totem. And include Pinta since it's such a small application but with great functionality (it's only 0.5 MB!). Heck they could write a simple interface to Banshee that would look exactly like Totem. And you know what is even more cool? F-spot is being re-based on parts of Banshee so it will consume even less space! **Win-win!** Isn't FOSS amazing?

I would call this
> Bloat-Bloat!
:mrgreen:
Even the fact of such excess of features is the reason to exclude banshee from anywhere. Do they really believe they can support this bunch of code?

MeeGo? It's initially abortive product with no future.
But even in the case I'm wrong (although I'm sure I'm right) it wouldn't be default for long time, it eats too much resources for the target devices and would be replaced by some Qt-based player.

---

### Post by zekopeko on 2010-06-14
> **vkontakte said:**
> "Mediaplayer" based on gstreamer? You must be joking!
Gstreamer is horribly slow and lack of essential features like interlacing support, vdpau support, etc.
So, the video mode is pointless but still take additional memory.

Now you don't make sense. RB and Totem both use gstreamer as their backend for media playback. So does Pitivi Video Editor. So you have 3 applications in the default install that use gstreamer for media playback.

> [http://arstechnica.com/open-source/news/2009/07/netbook-ui-photo-management-coming-to-banshee-media-player.ars](http://arstechnica.com/open-source/news/2009/07/netbook-ui-photo-management-coming-to-banshee-media-player.ars)

The interface
Canonical insists they are like being "consistent". I would be very amazed if they let such a "consistency" app being the default.

You do understand that the Cubano interface was targeted at netbooks?

> BTW. Does Banshee have essential an audio-playback feature RB doesn't have? I can't find anyone. As I said the Banshee is a toi for its developers, not the app that could be the default media player. They always break things in it, always add useless things like F-Spot features integration, etc. I'm sure canonical won't include it in the default set.

Well for a "toy" it sure is being used in commercial products such as Moovida and Meego. Guess companies that like to make money consider it good enough. I would say they are in a better position to judge it then you.

---

### Post by zekopeko on 2010-06-14
> **vkontakte said:**
> I would call this

One man's bloat is another man's feature :lolflag:

> Even the fact of such excess of features is the reason to exclude banshee from anywhere.

Another great thing about Banshee is that most features are actually plugins so you can disable them. Isn't that amazing?

> Do they really believe they can support this bunch of code?

Well as was said a few times now, Banshee has paid developers working on it. So you have Novell and Fluendo developers working on it plus Banshee and F-Spot community. Looks like supporting such a code base isn't a problem.

---

### Post by meho_r on 2010-06-14
I thought this thread was about F-Spot, not Banshee. However, in the current state F-Spot has some serious issues which I hope will get solved in near future (e.g. it's pretty heavy, importing large amount of pictures takes forever to complete and preview of images is awful–loading every single pic every time with a second or two of "focus time", I mean, seriously...).

---

### Post by 23meg on 2010-06-14
[QUOTE=meho_r]I thought this thread was about F-Spot, not Banshee.[/QUOTE]

You're right; any further derailing and it will be closed.

---

### Post by ibuclaw on 2010-06-14
> **meho_r said:**
> I thought this thread was about F-Spot, not Banshee. However, in the current state F-Spot has some serious issues which I hope will get solved in near future (e.g. it's pretty heavy, importing large amount of pictures takes forever to complete and preview of images is awful–loading every single pic every time with a second or two of "focus time", I mean, seriously...).

Banshee version 2.0 may be introducing support for photo management, or as the lead developer behind Banshee put it, the core functionality of the F-Spot photo manager will be integrated into Banshee's infrastructure.

That is how Banshee ties in with F-Spot. Though admittedly, you are all a good year too soon to start talking about this. ;)

---

### Post by zekopeko on 2010-06-14
> **meho_r said:**
> I thought this thread was about F-Spot, not Banshee. However, in the current state F-Spot has some serious issues which I hope will get solved in near future (e.g. it's pretty heavy, importing large amount of pictures takes forever to complete and preview of images is awful–loading every single pic every time with a second or two of "focus time", I mean, seriously...).

Well Banshee is related to F-Spot's future. It is being re-based on Banshee's foundations so that they can share code. For example this would allow F-spot to plug in to Banshee's media features so you could have video clips imported into F-spot from your camera. Or Banshee could have a simple Pictures plugin to facilitate syncing with mobile devices etc.

---

### Post by BeRA on 2010-06-14
I installed shotwell a few weeks ago... and I was impressed... simple and effective... glad to hear it's gonna be default in maverick :D

---

### Post by gnomeuser on 2010-06-14
> **ibuclaw said:**
> Banshee version 2.0 may be introducing support for photo management, or as the lead developer behind Banshee put it, the core functionality of the F-Spot photo manager will be integrated into Banshee's infrastructure.

That is how Banshee ties in with F-Spot. Though admittedly, you are all a good year too soon to start talking about this. ;)

I was very excited when they started talking about this but so far nothing has really happened on this front. I suspect we will see more work on F-Spot now that MeeGo is out of the door and F-Spot has a new maintainer.

That being said, while Banshee is great at managing media I find that the database and SQLite occasionally gives some problems especially with performance. It also seems that we could hand that job off to Tracker and having those problems of how to use SQL optimally solved in one place. Given that Tracker is a core MeeGo component could see a push in that direction coming. Additionally with the writeback module one might see moving some non-media features out of Banshee which sounds useful.

Still I have yet to see the list of bugs hindering Banshee from being default, all I hear is "it was discussed at UDS" which doesn't cut it for me. At least I would like to know where we can improve, currently we are at least more featureful and present a more vibrant community with a better supported codebase.

I am glad to see that upstream is considering migration seriously, it has always been one of my favorite things in Banshee that it considers other media players important sources of data (I believe we currently support iTunes, RB and Amarok). That is one complaint I will happily retract. Still I am concerned about the maturity of the project and how upstream will be able to handle what is sure to be a dramatic increase in bugreports and how Vala will hold up long term as it to is young.

---

### Post by vkontakte on 2010-06-14
> **zekopeko said:**
> Now you don't make sense. RB and Totem both use gstreamer as their backend for media playback. So does Pitivi Video Editor. So you have 3 applications in the default install that use gstreamer for media playback.
And they do this bad ;)
> You do understand that the Cubano interface was targeted at netbooks?
Yes, netbooks has no future. Sooner or later MS will introduce netbook-specific interface and MeeGo became pointless
> Well for a "toy" it sure is being used in commercial products such as Moovida and Meego. Guess companies that like to make money consider it good enough. I would say they are in a better position to judge it then you.
Moodiva is so incredibly slow :)
MeeGo isn't look like successful commercial product from the begining. Android will eat them on the smartphones, netbook market is too small to develop new OS for it.

---

### Post by ibuclaw on 2010-06-14
> **vkontakte said:**
> Yes, netbooks has no future.

I'm sorry, but that is complete utter blasphemy. And if you owned one, you'd know why. :)

Lightweight and Powerful is the future. And never again am I carrying a 5lb laptop on my shoulders again!

---

### Post by gnomeuser on 2010-06-14
> **ibuclaw said:**
> I'm sorry, but that is complete utter blasphemy. And if you owned one, you'd know why. :)

Lightweight and Powerful is the future. And never again am I carrying a 5lb laptop on my shoulders again!

I second this fine gentlemans point.

I used to own a Core 2 Duo ~15" laptop. It was so heavy and so power hungry that I never used it as a laptop. It's large formfactor also aided greatly in the fact that the number of times it left the house being countable on a hand.

My netbook however I love taking with me, it fits into the smallest pocket in my bag easily and leaves plenty of space. I find that I love going to a little cafe or restaurant to have lunch and do some writing. I am far more productive and creative thanks to it.

It also have plenty of power to run most applications and keep me going for a good couple of hours.

Netbooks are fantastic, though they have been slightly ruined by the addition of high capacity rotating storage devices and every increasing size/features. I would actually prefer something with a small SSD and ARM processor and a 3G module (provided I could use the same connection I pay for on my phone, this however seems like a cellco problem, mainly them accepting they are nothing but bitpushers to me nor should they be anything else).

For application testing netbooks are also fantastic, I have found a near uncountable number of UI problems merely by running them on a device with small screen and it inspired me to think about innovative ways to work with computers.

I think it would be a mistake to discount the platform, interfaces can't scale effectively and the only solution that will work is doing what Banshee does in providing differently focused interface experiences for different devices. 

I am hoping that any photomanager or other applications we select for our defaults would support this kind of separation of core and ui precisely to cater to the multiple use cases and deployments.

Another advantage of this approach is that it lets one cater to several different kind of users and it lets developers experiment with new user interfaces without disrupting the stable experience.

---

### Post by zekopeko on 2010-06-14
> **vkontakte said:**
> And they do this bad

Yes, netbooks has no future. Sooner or later MS will introduce netbook-specific interface and MeeGo became pointless

Moodiva is so incredibly slow
MeeGo isn't look like successful commercial product from the begining. Android will eat them on the smartphones, netbook market is too small to develop new OS for it.

You must be a troll that has very little knowledge of anything. "Netbooks have no future"? Hahahahahahahahahahaha!!!
Thanks for making me laugh. :lolflag:

---

### Post by vkontakte on 2010-06-14
> **zekopeko said:**
> You must be a troll that has very little knowledge of anything. "Netbooks have no future"? Hahahahahahahahahahaha!!!
Thanks for making me laugh. :lolflag:
LOL
You seem to be really narrow. Netbooks are only popular amongst computer geeks. Common people uses normal-sized devices. But nobody prevents you from hurting your eyes with netbooks, of course :)

---

### Post by ranch hand on 2010-06-14
Now then, let us play nicely together.

---

### Post by zekopeko on 2010-06-14
> **vkontakte said:**
> LOL
You seem to be really narrow. Netbooks are only popular amongst computer geeks. Common people uses normal-sized devices. But nobody prevents you from hurting your eyes with netbooks, of course :)

Then computer geeks must really be a huge part of the market since netbooks account for 20% of all laptop sales[1]. And that was almost a year ago.

[1] [http://techcrunch.com/2009/08/31/report-netbooks-now-a-fifth-of-all-portable-computer-shipments/](http://techcrunch.com/2009/08/31/report-netbooks-now-a-fifth-of-all-portable-computer-shipments/)

---

### Post by cariboo on 2010-06-14
This thread has really fallen off topic. Closed.

---

