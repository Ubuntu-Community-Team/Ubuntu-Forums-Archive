---
title: "Netflix - Ubuntu - w/ new Netflix Mac support"
date: 2008-12-04
forum: Multimedia Software
---

### Post by Maxszy on 2008-12-04
I admit that I am quite new to Linux. Specifically Ubuntu. I am using it on new netbook (and loving it btw!) which is my first experience with Linux. 

Everything is going well, however I would love the ability stream Netflix "Watch Now" movies on it. The netbook is so small and portable, it would be great for it. I have done some research on these forums as I realize there are numerous posts on this topic already. 

However, Netflix just rolled out their "Watch Now" support for Mac users. I know that it is using MS Silverlight technology. So I did some more research and found: [http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page) which seems to be replicating Silverlight in the form of Moonlight for use on the Linux Platform. 

So my question is essentially, with the latest support now out for Mac using the Silverlight technology, is there anyway to use moonlight in conjunction with Netflix "Watch Now"? Whether by tricking the web browser or anything else? Since now with the Silverlight Tech as a foundation, directx is out of the picture when it comes to obstacles in the process of getting it working on Ubuntu.

Any help would be great! Thanks.

---

### Post by wolfen69 on 2008-12-04
i just read an article (don't remember the link) where they said as soon as moonlight is finished, linux users should be able to view netflix movies. but for now it is a no go.

but please don't leave linux because of this! you can always dualboot in the meantime if it that important to you.

---

### Post by sc3252 on 2008-12-04
I am at school right now so I cant try it out, but I just read this.
[http://www.download.com/8301-2007_4-10113049-12.html](http://www.download.com/8301-2007_4-10113049-12.html)
It says that Boxee supports streaming for netflix now.  So it might be that ubuntu can stream netflix movies.

---

### Post by dsauter on 2008-12-06
I just got an invite to Boxee (a kind stranger sent me one), although it just happened.  If you send me a private message, I'll try to send you an invitation to try it out.

In spite of all the news reports, it doesn't appear that Netflix is working on the Linux version of Boxee yet.

"also there is no Netflix for Ubuntu, yet"  [http://blog.boxee.tv/2008/12/04/boxee/]("http://blog.boxee.tv/2008/12/04/boxee/")

That aside, it still looks promising.

---

### Post by directhex on 2008-12-06
> **Maxszy said:**
> So my question is essentially, with the latest support now out for Mac using the Silverlight technology, is there anyway to use moonlight in conjunction with Netflix "Watch Now"?

Not yet.

Currently, Moonlight supports Silverlight 1.0 - which basically offers a XAML renderer (a type of vector format like SVG) and codecs.

Netflix use Silverlight 2.0, which adds: widgets (i.e. common things like buttons rather than each app needing to draw its own from scratch), .NET-based programing (SL1.0 uses your browser's Javascript engine), and (most importantly for Netflix), DRM.

Moonlight WILL gain the above features (the widgets are already Free Software, so Moonlight can just reuse them from Silverlight; the CLI backend is in the earliest stages), but you will need to wait a few months

---

### Post by homerhomer on 2008-12-07
Honestly, I feel that Netflix is being held hostage my Microsoft.  I felt the same way about the same Olympics too.

---

### Post by Maxszy on 2008-12-22
Thanks for all the replies everyone! Sorry it took me awhile to get back to all of you.

No I am not going to be leaving Ubuntu just because of this :P loving it thus far beside the no netflix thing but it isnt that big of deal. 

Anyway I do appreciate all the kind and detailed help you gave me regarding this issue. Looks like probably in just a few months it should be up and going. So i'll just have a little more patience :) 

Thanks all ill be keeping an eye on here!

---

### Post by fatbuttlarry on 2009-03-01
Has anyone tried [http://boxee.tv/](http://boxee.tv/) yet?

Here's the instructions from their website:

[LIST=1]
[*]Go to System > Administration > Software Sources.
[*]In Sources Software dialogue, select Third-Party Software tab, click Add, and enter:
          * for Hardy:
```
deb http://apt.boxee.tv hardy main
```
          * for Intrepid: 
```
deb http://apt.boxee.tv intrepid main
```
   [*] After closing this dialogue you can either use Synaptics and select Boxee for download, or use a terminal window, and enter sudo apt-get install boxee.
[/LIST] 


-Tres

---

### Post by fatbuttlarry on 2009-05-05
[IMG]http://4.bp.blogspot.com/_9hmP3Ho0t14/Sf-ah-prNKI/AAAAAAAAANg/ie7CCRThqsQ/s1600/moonlight_netflix.png[/IMG]

```
"*Player Startup Error* -  There is a problem with your player.  Please call Netflix technical support at: ErrorCode: 8001"
```

I've been [tracking the Moonlight progress]("http://fatbuttlarry.blogspot.com/2009/02/netflix-ubuntu.html"), and it appears a version [2.0 preview]("http://go-mono.com/moonlight-preview/") is out.

I've installed this on a live CD of [Ubuntu 8.04]("http://www.ubuntu.com/getubuntu/download") and it seems to work OK. (At the time of posting this, my desktop is at 9.04 currently unsupported by Moonlight)

Other distros: Fedora, OpenSuSE have [Moonlight 2.0 preview]("http://go-mono.com/moonlight-preview/") support as well.

I've managed to [trick Netflix's web site into loading the applet]("http://1.bp.blogspot.com/_9hmP3Ho0t14/Sf-30Pun_VI/AAAAAAAAANw/Sle4VBJy5qQ/s1600-h/snapshot2.png") by telling the site I'm running Windows XP using the plug-in "Firefox [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/59")".

My results are a [failure for now]("http://4.bp.blogspot.com/_9hmP3Ho0t14/Sf-ah-prNKI/AAAAAAAAANg/ie7CCRThqsQ/s1600/moonlight_netflix.png"), but it's [further than I got with Moonlight 1.0]("http://img11.imageshack.us/img11/1430/screenshotfa6.png").  It's difficult to determine the cause of the video load failure, so any insight is helpful!

-Tres

---

### Post by ace214 on 2009-05-11
Got a similar result using the Preview 2 with a user agent line I copied from Firefox in Wine, on Jaunty.

When I use the IE entry in User Agent Switcher, I seem to get farther- it just wants ActiveX support, which as far as I know can't happen in Linux. Here's a screenshot of this.

---

### Post by Chronon on 2009-05-12
As far as I have read Moonlight doesn't have the necessary DRM functionality yet.  You may get the player to load up but the license checking will never authenticate and you won't be able to watch any movies.

---

### Post by directhex on 2009-05-12
> **Chronon said:**
> As far as I have read Moonlight doesn't have the necessary DRM functionality yet.  You may get the player to load up but the license checking will never authenticate and you won't be able to watch any movies.

[http://silverlight.net/forums/p/94992/217612.aspx](http://silverlight.net/forums/p/94992/217612.aspx)

---

### Post by Dngrsone on 2009-06-11
Moonlight 2.0 is out, but no DRM as of yet... still waiting.

---

### Post by directhex on 2009-06-11
> **Dngrsone said:**
> Moonlight 2.0 is out, but no DRM as of yet... still waiting.

Early pre-alphas are out. And for the DRM, moan to Microsoft, since they're the ones who need to make it available

---

### Post by sirjoebob on 2009-06-11
Can't wait till this is finally cracked so I can sit back and enjoy my netflix movies without going to virtual box. :popcorn:

---

### Post by willz06jw on 2009-07-20
Anyluck with Silverlight 2.0 DRM functionality (AKA Getting Netflix Watch Now to work?)

---

### Post by directhex on 2009-07-20
> **willz06jw said:**
> Anyluck with Silverlight 2.0 DRM functionality (AKA Getting Netflix Watch Now to work?)

Sadly, that's still down to Microsoft. What I understand of the politics involved, it doesn't look too promising right now - and it's not the Silverlight team blocking it

---

### Post by janz84 on 2009-07-20
This is one of the big things thats keeping me AFL (away from linux). Would be back on my laptop full time if i could watch flix on the mocha

---

### Post by aysiu on 2009-07-21
> **janz84 said:**
> This is one of the big things thats keeping me AFL (away from linux). Would be back on my laptop full time if i could watch flix on the mocha
So threaten Netflix with a cancelled or minimized subscription. Money talks. It isn't up to Linux to get Watch Now working on Linux. It's up to Netflix to do it.

---

### Post by directhex on 2009-07-21
> **aysiu said:**
> So threaten Netflix with a cancelled or minimized subscription. Money talks. It isn't up to Linux to get Watch Now working on Linux. It's up to Netflix to do it.

Well... It's up to large Microsoft DRM customers like Netflix. They're in a better position to bust heads - or drop DRM - wither of which could resolve the issue

---

### Post by aysiu on 2009-07-21
> **directhex said:**
> Well... It's up to large Microsoft DRM customers like Netflix. They're in a better position to bust heads - or drop DRM - wither of which could resolve the issue
If Netflix thinks they will lose money by not supporting Linux, they will find a way to support Linux.

---

### Post by rgb1701 on 2009-07-21
> **aysiu said:**
> So threaten Netflix with a cancelled or minimized subscription. Money talks. It isn't up to Linux to get Watch Now working on Linux. It's up to Netflix to do it.

Agreed.

It makes me furious and disgusted when people say "I would use Linux except for XXX"

when XXX = a DRM'd game or DRM'd media source (streaming or physical).

DRM is a BIG social, political issue, a battleground for the fundamental rights of consumers and individual freedoms.

Yeah, yeah, roll your eyes, but this IP/copyright/DRM cold war will be documented in the history books for future generations just like the battle for civil rights, women's suffrage, and the war for independence of the States.

Only now, the oppressor is not a political entity like a government across an ocean, but rather corporate abusers of IP/copyright/patents.

"Voting for justice is as ineffective as wishing for justice; what you need to do is to actually be just. This is not to say that you have an obligation to devote your life to fighting for justice, but you do have an obligation not to commit injustice and not to give injustice your practical support."

"In a constitutional republic like the United States, people often think that the proper response to an unjust law is to try to use the political process to change the law, but to obey and respect the law until it is changed. But if the law is itself clearly unjust, and the lawmaking process is not designed to quickly obliterate such unjust laws, then the law deserves no respect and it should be broken."

- Henry David Thoreau

[http://en.wikipedia.org/wiki/Civil_Disobedience_(Thoreau](http://en.wikipedia.org/wiki/Civil_Disobedience_(Thoreau))

It is an injustice to society to support/partake in DRM'd media.  Don't support companies that support DRM.

---

### Post by aysiu on 2009-07-21
I also get tired of people saying "I don't care about freedom. I just want things to work."

The two are not always at odds with each other. Did the Palm Pre "just work" with the new iTunes update? Did Orwell's *1984* "just work" with the Amazon Kindle? No.

If you don't have freedom, you are relying on someone else to tell you whether it's okay or not to use *what you have already purchased*. At any time, that someone else (usually a corporation) can revoke your rights to have things "just work." And this isn't right.

---

### Post by willz06jw on 2009-07-21
I told them I'm downgrading my Netflix account to 1 a day until they support ubuntu

---

### Post by WIGGMPk on 2009-07-21
> **aysiu said:**
> I also get tired of people saying "I don't care about freedom. I just want things to work."

The two are not always at odds with each other. Did the Palm Pre "just work" with the new iTunes update? Did Orwell's *1984* "just work" with the Amazon Kindle? No.

If you don't have freedom, you are relying on someone else to tell you whether it's okay or not to use *what you have already purchased*. At any time, that someone else (usually a corporation) can revoke your rights to have things "just work." And this isn't right.

100% agree with the above....


Its ashame people are held hostage by corporations.. Another example is ASUS Express Gate + Windows Only Compatability.. Like what exactly happened there?

The DRM is just getting out of hand these days. I personally have to stream my Netflix through a virtual machine of a not so legal copy of Tiny XP.

---

### Post by directhex on 2009-07-21
> **willz06jw said:**
> I told them I'm downgrading my Netflix account to 1 a day until they support ubuntu

Hm, I thought I'd replied to this.

What I said was:

Be sure to tell them what you actually want from them, that is within their grasp. For Netflix to work on Linux requires one of two things:

1) Microsoft need to port, or subcontract porting, PlayReady DRM for use on platforms supported by Moonlight (the way they already offer their binary codec pack). It can be done - if Mac OS X has a copy in their Silverlight, then Moonlight could too. This is the more "sure" option as it would accommodate other sites - but also makes the biggest concessions to Freedom given it would be perpetuating DRM. Netflix are a large enough Microsoft customer that they could demand action.

2) Get them to drop the DRM. DRM doesn't work, everyone knows that. And all it's doing is preventing Moonlight from doing its job (when it could do it quite fine otherwise).

Before suggestions of <video> or Flash happen, bear in mind that transitioning their files to a non-wmv format would cost THOUSANDS in time, manpower, storage, etc - and not necessarily guarantee working any better.

---

### Post by willz06jw on 2009-07-22
The watch now movies are a bit scarce to begin with.  The problem is that the studios that make the movies are wary of a new technology that would speed up the death of DVDs.  They are barely holding on to the Netflix model at all.  The death of DRM is unrealistic because the studios need to be paid for their work, and it would prevent the Netflix watch now business model.  It may be reasonable to expect a DRMless media when we buy... But not when we rent.

---

### Post by sirjoebob on 2009-07-22
> **aysiu said:**
> I also get tired of people saying "I don't care about freedom. I just want things to work."

That is the biggest annoyance to me. Benjamin Franklin once said:
"They who can give up essential liberty to obtain a little temporary safety, deserve neither liberty nor safety."

---

### Post by directhex on 2009-07-22
> **directhex said:**
> Before suggestions of <video> or Flash happen, bear in mind that transitioning their files to a non-wmv format would cost THOUSANDS in time, manpower, storage, etc - and not necessarily guarantee working any better.

Oh, and to pre-empt an argument I've heard, When the Major League baseball folks dropped Silverlight and "moved to Flash", they did not, in fact, move to Flash. They moved to a plug-in on top of Flash, a Windows & Mac only plugin, for adding WMV support to Flash, in order to avoid recoding their existing content. This plug-in for the Flash plug-in works way worse than SL ever did for Mac/Windows people - and will never be ported to Linux. Assuming MLB don't use PlayReady, then watching baseball in Ubuntu would have been eventually possible if they'd stuck with Silverlight - but will never be possible with their "move to Flash".

A relevant note on the competition.

---

