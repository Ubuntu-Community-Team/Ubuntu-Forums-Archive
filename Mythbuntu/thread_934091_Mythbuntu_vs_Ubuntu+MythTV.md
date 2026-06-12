---
title: "Mythbuntu vs Ubuntu+MythTV"
date: 2008-09-30
forum: Mythbuntu
---

### Post by davidw89 on 2008-09-30
I want to install x64 version. Both have.

What's the difference between installing Mythbuntu OR use my existing Ubuntu CD and then installing MythTV?

---

### Post by Caps18 on 2008-09-30
I've only used Mythbuntu, but I think it has a control panel that helps a little.  Everything is already to go with Mythbuntu, you just need to configure it. 

If you are going to have a stand-alone system, I like Mythbuntu.  It's as small as it can be, but still give the user enough capabilities.  If you want to tinker with things or want to use the computer as well as MythTV, then it's probably better to have the whole OS there, along with some other programs.

---

### Post by managementboy on 2008-09-30
> **davidw89 said:**
> I want to install x64 version. Both have.

What's the difference between installing Mythbuntu OR use my existing Ubuntu CD and then installing MythTV?

I would start with mythbuntu and then use the nice gui to upgrade to kubuntu/ubuntu after MythTV is working fine

---

### Post by newlinux on 2008-09-30
I personally install ubuntu first (most of my machines I also at least occasionally use as a desktop and I prefer Gnome) and then install mythbunbu-control-centre ("the nice gui"/"control panel") and do most of the configuring from there. I'd do whatever you are more comfortable with. Mythbuntu-control-centre makes it easier either way.

---

### Post by the Goat on 2008-09-30
Install bug standard ubuntu then use apt-get to install mythtv.  Stay far away from Mythbuntu control center.  It only creates problems.

---

### Post by netslacker on 2008-09-30
I can only re-iterate what the last two posters said, I tried mythbuntu x64 and could not get a stable system AT ALL.  I tried for 6 weeks to stabilize it and wasted many hours (backend crashed daily along w/ frontend every couple of days). 

I then started fresh with Ubuntu 8.04 and used apt-get or the GUI tool to install mythtv and my crashes have vanished and my system is now rock solid.  Using monit to monitor backend and it shows that the myth process has been running for 21 days 14 hours, the same for mysql and all other monitored processes... (this was the last time I restarted the box).

I would not use mythbuntu.  Using apt-get you can install EVERY piece that mythbuntu offers and even avoid some of the bugs associated with that distro, it is not worth your time to try and debug problems, trust me, it sucks.

---

### Post by tgm4883 on 2008-09-30
> **the Goat said:**
> Install bug standard ubuntu then use apt-get to install mythtv.  Stay far away from Mythbuntu control center.  It only creates problems.

Problems like what?

---

### Post by the Goat on 2008-09-30
> **tgm4883 said:**
> Problems like what?

The largest problem is the mythbuntu guys change default config settings and locations for no reason.  Then if you try to adjust settings or try to follow directions from a website, it is a lot harder to accomplish on mythbuntu.

I realize I am a "power user", but basically every thing mythbuntu set up for me was not how I wanted it setup.  So it actually took a great deal longer for me to setup mythbuntu then installing mythtv myself.

Also I only like switching from CLI (command line interface) to GUI if there is an advantage (speed or ease of use or more options, etc).  Mythbuntu control center offered no advantage at all.

Also I hate programs (like Mythbuntu control center) that are just shell interfaces and behind the scene call another program to do the real work.  I would rather directly interface with the program Mythbuntu control center gives the task to.

---

### Post by laga on 2008-09-30
> **the Goat said:**
> The largest problem is the mythbuntu guys change default config settings and locations for no reason.

Can you give me some examples where Mythbuntu (MCC) is different from Ubuntu + MythTV?

---

### Post by the Goat on 2008-09-30
> **laga said:**
> Can you give me some examples where Mythbuntu (MCC) is different from Ubuntu + MythTV?

Uhh yea, everything MCC does that Ubuntu + MythTV does not do.

For instance:
incorrectly setting up nfs,
incorrectly setting up samba,
incorrectly installing codecs,
incorrectly changing the startup & shutdown splash pages,
incorrectly configuring an ir blaster,
incorrectly configuring a lirc remote contol,
incorrectly setting up mysql,
incorrectly configuring remote frontends,
etc.,
etc. . .

It has been about a year since I last used MCC so I don't remember all the "features."

---

### Post by superm1 on 2008-09-30
> **the Goat said:**
> Uhh yea, everything MCC does that Ubuntu + MythTV does not do.

For instance:
incorrectly setting up nfs,
incorrectly setting up samba,
incorrectly installing codecs,
incorrectly changing the startup & shutdown splash pages,
incorrectly configuring an ir blaster,
incorrectly configuring a lirc remote contol,
incorrectly setting up mysql,
incorrectly configuring remote frontends,
etc.,
etc. . .

It has been about a year since I last used MCC so I don't remember all the "features."
Have you filed bugs on all of these issues you've ran into?

---

### Post by Caps18 on 2008-09-30
I'll agree with you on the NFS/Samba thing.  It needs to be easier at least.

But besides the OP wanting to use 64 bit for some reason (and posting on this forum).  I don't know if he is a power user that knows what he is doing, or some one who just wants a HTPC.

---

### Post by DemonBob on 2008-09-30
> **the Goat said:**
> 
It has been about a year since I last used MCC so I don't remember all the "features."

A year.... Then how can you specifically comment on the current MCC if it's been a year since you used it. A year ago means you was using MCC in 7.04....It's now 8.04/8.10 thats 2/3 revisions.... 

Also did you file bugs when you did?

---

### Post by tgm4883 on 2008-09-30
> **DemonBob said:**
> A year.... Then how can you specifically comment on the current MCC if it's been a year since you used it. A year ago means you was using MCC in 7.04....It's now 8.04/8.10 thats 2/3 revisions.... 

Also did you file bugs when you did?

It's probably also of note that MCC wasn't in 7.04, so he is probably talking about 7.10 release, perhaps pre-release.

---

### Post by the Goat on 2008-09-30
> **DemonBob said:**
> A year.... Then how can you specifically comment on the current MCC if it's been a year since you used it. A year ago means you was using MCC in 7.04....It's now 8.04/8.10 thats 2/3 revisions.... 

Also did you file bugs when you did?

Yes I did file a couple of bug reports (one was x64 codecs not installing I think and I forget the other).  But honestly I so no reward in helping develop a program that makes setting up mythtv harder and take longer.

A lot of the issues I have are personal preference of how I want packages/features to be configured.  So if MCC correctly set up stuff to my liking, somebody else would say it was wrong.  Also choosing "the most common" setting to be the default is not correct either.  The default should be the way apt-get installs the package, nothing more nothing less.  (i.e. the NFS/samba/lirc/mysql package maintainer dictates the default settings not MCC)

I fundamentally see a graphical setup program (MCC) as a bad idea.  I think it is bad for all users: power users like me and for new users also.

---

### Post by the Goat on 2008-09-30
> **tgm4883 said:**
> It's probably also of note that MCC wasn't in 7.04, so he is probably talking about 7.10 release, perhaps pre-release.

It was about a year ago (more like 10-11 months I guess).  It was 7.10

---

### Post by majoridiot on 2008-09-30
i can not comment on the nfs/samba complaints, but i will say that the 8.04/8.10 i386 and x64 installs i have done
were mostly hassle-free.  the problems i did encounter were not due to mythbuntu doing anything "non-standard".
the MCC interface provides a *mostly* hassle-free way for users to config mythtv settings and- at least in my experiences, 
works very well and improves with each release.

whichever way you go- ubuntu+mythtv or mythbuntu, i would definitely recommend installing and using MCC-
unless you enjoy poking around in a terminal to config things.  i'm quite comfortable with a terminal and doing
configs by hand and still use MCC whenever possible as a quick-fix solution to 99% of problems.

---

### Post by laga on 2008-09-30
> **the Goat said:**
> The default should be the way apt-get installs the package, nothing more nothing less.  (i.e. the NFS/samba/lirc/mysql package maintainer dictates the default settings not MCC)


Do you realize that MCC mostly is just a frontend to apt-get? For example, the codecs are simply pulled from Medibuntu. Although there were some issues with x64 codecs showing up on i386 boxes, AFAIK. Nothing serious.

Do you also realize that MCC is just a frontend for the Lirc maintainer scripts, using debconf to interact with them? (As of 8.04, but 7.10 was close enough).

MCC also does not mess with the configuration of mysqld unless you explicitly tell it to do so (filed away under "advanced options") or something. Regarding mysql.txt, that's also handled through debconf.

NFS and Samba could be a bit smarter, but it should work unless you change the default directories for recordings/video/music. Granted, that's a silly assumption.

Anyways, I'm not going to tell you what app to use to configure your system. I just had to clarify a few things...

*edit:* And of course, I can't take complaints about some old version of MCC seriously when you didn't even bother to report those issues.

---

### Post by newlinux on 2008-09-30
I consider myself a power user and MCC was fine for me. I had hesitations because I like to tinker, but it worked well. I did go back and do my own SAMBA configurations and modified default locations and modified the lirc config, but I would have had to do these without MCC too...

It was okay for me, certainly made getting 80% of the way really trivial and fast for me. It may get others closer to 90-100% of the way...

---

### Post by the Goat on 2008-09-30
> **laga said:**
> Do you realize that MCC mostly is just a frontend to apt-get? 

. . .

Do you also realize that MCC is just a frontend for the Lirc maintainer scripts, using debconf to interact with them?


Since the fact that MCC is simply a frontend that dumps the work onto other programs is **something I explicitly complained about** (see my posts above), it is a safe assumption that I did in fact realize that.

> **laga said:**
> And of course, I can't take complaints about some old version of MCC serious when you didn't even bother to report those issues.

As I have already said I think the issue is the idea behind the MCC program itself.  What is the phrase Obama used?  "You can put lipstick on a pig.  but in the end you still have a pig."

---

### Post by larsolav on 2008-09-30
> **the Goat said:**
> Since the fact that MCC is simply a frontend that dumps the work onto other programs is **something I explicitly complained about** (see my posts above), it is a safe assumption that I did in fact realize that.

As I have already said I think the issue is the idea behind the MCC program itself.  What is the phrase Obama used?  "You can put lipstick on a pig.  but in the end you still have a pig."

If MCC is just a frontend that dumps the work onto other programs, then isn't MCC the lipstick? The MCC makes things a lot easier for us non-power users.

Isn't the idea behind Mythbuntu to make it an easier experience to install and use MythTV, so that people with little or no experience with Linux can do it? The first time I installed MythTV was on 6.10, and I struggled having not used any Linux or Unix before except for PINE for email and a few run ins on analytical instruments in chem grad school way back when. It took me for ever to set up the graphics and remote. I had to have help from a linux guru friend...

But then I tried Mythbuntu and everything was easier, such as setting up the remote. OK, I had to tweak the file with the button codes (don't remember the name of it) but that I would have to do anyway! And I haven't even upgraded to 8.04...

---

### Post by anonymousdog on 2008-09-30
Goat, you sure do seem to be hell bent on arrogantly asserting that your preferences dictate the needs of everyone else and tools that might meet those needs.  I'm a pretty hard core, professional geek who cut his 'nix teeth on the CLI, but I can certainly see the value of the MCC.  It makes Mythbuntu accessible to the average user, and I'm pretty impressed with it's ability to configure most of the system within a highly discoverable UI.

Your aversion to the MCC seems based on geek elitism of the first order; because you like to configure your systems manually, because you reap the benefits of that and find them valuable, because you so value those benefits that you have invoked the "one true scottsman" logical fallacy and concluded that manual configuration is the "right" way, you have concluded that all users should adapt to your "right" way (no matter how steep the learning curve might be or how inaccessible that might make the technology).

> **the Goat said:**
> The largest problem is the mythbuntu guys change default config settings and locations for no reason.
I don't think you've backed this up.  Laga clearly states that package maintenance in the MCC is just a front-end to apt-get and dpkg; so, what you get is what the repo maintainers want.  Now, Mythbuntu does some strange things with lircd modules and such, but that's hardly a reason for the average Mythbuntu user to abandon the MCC.  For that average user, deviating from the standard way (things are done in Mythbuntu) yields a non-standard (from vanilla Mythbuntu) configuration and makes it more difficult for that average user to get peer support in forums like this.

> **the Goat said:**
> Also I hate programs (like Mythbuntu control center) that are just shell interfaces and behind the scene call another program to do the real work.  I would rather directly interface with the program Mythbuntu control center gives the task to.

This is the heart of your discontent, and it's an unsupported piece of emotional reasoning (because you've offered no logical underpinning).  There might be logical arguments to be made about the relative worth of GUI frontends to CLI tools, but you haven't made any.  All you've said is that you prefer to use CLI tools and hate GUI frontends; that's a "religious" argument that doesn't belong in a scientific field.

Your assertion could likely be reframed as such, "I dislike the MCC because it allows those with out specific, developed skills to do some of the cool things I've fought hard to learn to do on my own.  I feel so superior for having developed specific skills in that area that I devalue those who don't have them and any tools they might therefore require to overcome their lack of skills.  In fact, I actually resent the tools they use because those tools reduce the value of the oh-so-hard-won skills I so proudly possess."

---

### Post by foxbuntu on 2008-09-30
> **anonymousdog said:**
> Goat, you sure do seem to be hell bent on arrogantly asserting that your preferences dictate the needs of everyone else and tools that might meet those needs.  I'm a pretty hard core, professional geek who cut his 'nix teeth on the CLI, but I can certainly see the value of the MCC.  It makes Mythbuntu accessible to the average user, and I'm pretty impressed with it's ability to configure most of the system within a highly discoverable UI.

Your aversion to the MCC seems based on geek elitism of the first order; because you like to configure your systems manually, because you reap the benefits of that and find them valuable, because you so value those benefits that you have invoked the "one true scottsman" logical fallacy and concluded that manual configuration is the "right" way, you have concluded that all users should adapt to your "right" way (no matter how steep the learning curve might be or how inaccessible that might make the technology).


I don't think you've backed this up.  Laga clearly states that package maintenance in the MCC is just a front-end to apt-get and dpkg; so, what you get is what the repo maintainers want.  Now, Mythbuntu does some strange things with lircd modules and such, but that's hardly a reason for the average Mythbuntu user to abandon the MCC.  For that average user, deviating from the standard way (things are done in Mythbuntu) yields a non-standard (from vanilla Mythbuntu) configuration and makes it more difficult for that average user to get peer support in forums like this.



This is the heart of your discontent, and it's an unsupported piece of emotional reasoning (because you've offered no logical underpinning).  There might be logical arguments to be made about the relative worth of GUI frontends to CLI tools, but you haven't made any.  All you've said is that you prefer to use CLI tools and hate GUI frontends; that's a "religious" argument that doesn't belong in a scientific field.

Your assertion could likely be reframed as such, "I dislike the MCC because it allows those with out specific, developed skills to do some of the cool things I've fought hard to learn to do on my own.  I feel so superior for having developed specific skills in that area that I devalue those who don't have them and any tools they might therefore require to overcome their lack of skills.  In fact, I actually resent the tools they use because those tools reduce the value of the oh-so-hard-won skills I so proudly possess."

Well put. 

As far as MCC just being a Shell Frontend..I would have to refer you to the source code that many of the developers have had a hand in, including myself, that spans several custom packages that never existed prior to MCC and the several thousand lines of code that make it up. There are features that a running other applications, however many of the features of Mythbuntu Control Centre are custom to Mythbuntu. 

One last statement to close this thread up and make sure any other like it has no basis:

The developers are not paid, we work on our own appreciation for all the community provides to the improvement and technological advancement even outside the community. If you find fault, or error in a published application feel free to change it, report it (in a socially acceptable method, ranting/raving/baseless accusations/generally acting like a child are not of these methods), ask questions why things were done the way they have been. Developers are always glad to hear new ideas. If you feel the need to not abide to any of this, feel free to try paid software with paid support, it might be a better fit for you.

---

### Post by the Goat on 2008-10-01
> **anonymousdog said:**
> Your aversion to the MCC seems based on geek elitism of the first order; because you like to configure your systems manually, because you reap the benefits of that and find them valuable, because you so value those benefits that you have invoked the "one true scottsman" logical fallacy and concluded that manual configuration is the "right" way, you have concluded that all users should adapt to your "right" way (no matter how steep the learning curve might be or how inaccessible that might make the technology).

. . .

Your assertion could likely be reframed as such, "I dislike the MCC because it allows those with out specific, developed skills to do some of the cool things I've fought hard to learn to do on my own.  I feel so superior for having developed specific skills in that area that I devalue those who don't have them and any tools they might therefore require to overcome their lack of skills.  In fact, I actually resent the tools they use because those tools reduce the value of the oh-so-hard-won skills I so proudly possess."

Your analysis could not be further from the truth.  The best I will explain my view is with the old saying about, "Give a man a fish and you feed him for a day.  Teach a man to fish and you feed him for a lifetime."  I whole heartedly think that by providing MCC you are "giving a man a fish."

Furthermore I think MCC actually prevents people from "learning to fish" or at least makes it a lot harder to learn.  I understand that MCC is there to help people.  But it really creates a mass of users who don't have the skills to help them selves when something outside the box happens.

In my case this is not theory.  When I fist started using MythTV I installed Knoppmyth.  At first I thought it was great.  But after a while I realized I was 100% dependent on the knoppmyth user forum.  If anything broke on my MythTV setup (usually because I didn't know what I was doing) the only thing I could do was post a description of the problem and hope somebody would post a solution.

I was at the mercy of whoever was on the other side of the forum.  Luckily there were people kind enough to help me.  But several times my MythTV setup would be down completely for days until somebody would figure out the problem I posted about.  Even so my system would still lock up or reboot once or twice a week.

Needless to say I think that situation was not ideal.  Learning how to help myself setup/configure MythTV after using knoppmyth was ten times harder then it should have been had I had just learned correctly in the first place.  I think MCC will result in users being enslaved to forums for problem diagnosis and how to instructions for fixes.  I think it is irresponsible for the community to enable this to happen to new users.  My views are based on personal experience and observations.

---

### Post by the Goat on 2008-10-01
> **foxbuntu said:**
> Well put. 

As far as MCC just being a Shell Frontend..I would have to refer you to the source code that many of the developers have had a hand in, including myself, that spans several custom packages that never existed prior to MCC and the several thousand lines of code that make it up. There are features that a running other applications, however many of the features of Mythbuntu Control Centre are custom to Mythbuntu. 

One last statement to close this thread up and make sure any other like it has no basis:

The developers are not paid, we work on our own appreciation for all the community provides to the improvement and technological advancement even outside the community. If you find fault, or error in a published application feel free to change it, report it (in a socially acceptable method, ranting/raving/baseless accusations/generally acting like a child are not of these methods), ask questions why things were done the way they have been. Developers are always glad to hear new ideas. If you feel the need to not abide to any of this, feel free to try paid software with paid support, it might be a better fit for you.

The fact that developers are not paid has nothing to do with this discussion.  As I have stated above, I think providing mythbuntu and MCC is a [_disservice_](http://www.wordreference.com/definition/disservice) to the user base.  If you support MCC then by all means knock yourself out programing it.  But don't expect me to pull my punches if somebody asks for my opinion on the subject (like the original poster in this thread).

---

### Post by anonymousdog on 2008-10-01
> **the Goat said:**
> As I have stated above, I think providing mythbuntu and MCC is a [_disservice_](http://www.wordreference.com/definition/disservice) to the user base.  If you support MCC then by all means knock yourself out programing it.  But don't expect me to pull my punches if somebody asks for my opinion on the subject (like the original poster in this thread).Aside from newlinux's suggestion that the poster use the MCC to accomplish configuration (s)he found difficult, yours was the first reference to the MCC in this thread; so, it's pretty hard to see that as an open invitation to baselessly criticize the MCC.  Besides, you haven't offered any non-emotional criticisms of the MCC yet.  

Your personal anecdote only reinforces my point that you so highly value your hard won skills that you now eschew tools that shortcut that steep learning curve for that average user.  The MCC (like many GUI configuration tools) can actually be of assistance in learning to perform manual configurations because a learning user can do config X in the GUI, check what that does to the file system, and learn what (developers more experienced in these areas than they) thought was a reasonable approach to configuration X.  I say, "what about the guy who just wants a fish (but doesn't really WANT to learn to fish)?"

---

### Post by ReddogOne on 2008-10-06
> **the Goat said:**
> Your analysis could not be further from the truth.  The best I will explain my view is with the old saying about, "Give a man a fish and you feed him for a day.  Teach a man to fish and you feed him for a lifetime."  I whole heartedly think that by providing MCC you are "giving a man a fish."

Could I extend the saying just so it applies to most of us, "Give a man a fish and you feed him for a day.  Teach a man to fish and you feed him for a lifetime. Give a man a tin of Tuna because he's been working all #@#%$£" day and just wants to eat some *&%$&^% fish!"

Seeing as it works for 99% of people seems to me a bit daft to make everyone do is the hard way and make the success rate a whole lot lower and lose users as most will give up on the first problem. 

Bit like moaning that cars are supplied with the wiring loom as if each customer fitted it themselves they would be better at changing the oil. How many people do you think would buy a car without the wiring.

> **the Goat said:**
> Furthermore I think MCC actually prevents people from "learning to fish" or at least makes it a lot harder to learn.  I understand that MCC is there to help people.  But it really creates a mass of users who don't have the skills to help them selves when something outside the box happens.

Well because of the people who have developed the MCC (thumbs up from me) not a lot does go wrong outside the box so who cares.

When it does go wrong. Then they can learn that bit. Having something like the MCC will also allow people to help easier because they will have more 'knowns' about the system the user is describing.

> **the Goat said:**
> In my case this is not theory.  When I fist started using MythTV I installed Knoppmyth.  At first I thought it was great.  But after a while I realized I was 100% dependent on the knoppmyth user forum.  If anything broke on my MythTV setup (usually because I didn't know what I was doing) the only thing I could do was post a description of the problem and hope somebody would post a solution.

If you had two days in the terminal typing in other people commands (and only if you was lucky you would have found good ones) you still wouldn't actually have known a great deal, probably made a few typos, and been just as dependant on the forums as before. What's the difference?

> **the Goat said:**
> <Plenty Snips>  I think MCC will result in users being enslaved to forums for problem diagnosis and how to instructions for fixes.  I think it is irresponsible for the community to enable this to happen to new users.  My views are based on personal experience and observations.

I think MCC means 99.9% of users won't have to give a monkey!

---

### Post by boushley on 2008-10-11
Well in my personal experience, I'm going to have to go with Ubuntu+MythTV.  I had mythbuntu up and running, except that none of the usb ports worked.  I have a usb mouse and it doesn't even get power from the port...  And under ubuntu everything works great.  I was wanting to install some other programs to run on my myth tv box, and so I will be running ubuntu+mythtv.

---

### Post by superm1 on 2008-10-11
> **boushley said:**
> Well in my personal experience, I'm going to have to go with Ubuntu+MythTV.  I had mythbuntu up and running, except that none of the usb ports worked.  I have a usb mouse and it doesn't even get power from the port...  And under ubuntu everything works great.  I was wanting to install some other programs to run on my myth tv box, and so I will be running ubuntu+mythtv.
This is a very odd situation.  It's the same kernel and drivers in both....

---

### Post by Lexicon101 on 2008-10-11
> **the Goat said:**
> Your analysis could not be further from the truth.  The best I will explain my view is with the old saying about, "Give a man a fish and you feed him for a day.  Teach a man to fish and you feed him for a lifetime."  I whole heartedly think that by providing MCC you are "giving a man a fish."

Furthermore I think MCC actually prevents people from "learning to fish" or at least makes it a lot harder to learn.  I understand that MCC is there to help people.  But it really creates a mass of users who don't have the skills to help them selves when something outside the box happens.

In my case this is not theory.  When I fist started using MythTV I installed Knoppmyth.  At first I thought it was great.  But after a while I realized I was 100% dependent on the knoppmyth user forum.  If anything broke on my MythTV setup (usually because I didn't know what I was doing) the only thing I could do was post a description of the problem and hope somebody would post a solution.

I was at the mercy of whoever was on the other side of the forum.  Luckily there were people kind enough to help me.  But several times my MythTV setup would be down completely for days until somebody would figure out the problem I posted about.  Even so my system would still lock up or reboot once or twice a week.

Needless to say I think that situation was not ideal.  Learning how to help myself setup/configure MythTV after using knoppmyth was ten times harder then it should have been had I had just learned correctly in the first place.  I think MCC will result in users being enslaved to forums for problem diagnosis and how to instructions for fixes.  I think it is irresponsible for the community to enable this to happen to new users.  My views are based on personal experience and observations.

You don't like how the other man fishes? Has he given you the wrong fish? If there's a machine to fish for you, why should you fish? You could be doing something productive elsewhere, instead of FSCKing around with a fishing rod, trying to figure out the best way to re-wind the spool.

You could build a house with your hands. By the end you would know a whole lot about building houses. You could rip and tear things to get stuff done.. But wouldn't it be easier to get an axe to do that, then fix what you need to with your hands?

You can say whatever you like about.. (well, anything, but in particular..) being enslaved to the forums.. But that's what they're there for. Imagine finding all your hard-earned answers without the forums.

Just because you don't like GUIs doesn't mean they have no use, and just because you found bugs in some program 10 months ago doesn't mean there's anything wrong with it today. In fact, try it and you might like it. Of course, I have no dealings with mythTV, but.. The way you think irritates me, and it doesn't make sense to do things the hard way, when the easy way gets them done better, faster. Of course, if the easy way doesn't get them done well, do it the hard way. But what's wrong with the easy way when you could spend your effort on something else?

---

### Post by Slate8 on 2008-10-13
For what its worth I installed and setup the 64 bit Mythbuntu version this week and have had no issues.

I use it as both a back and frontend and found that all hardware just worked after install including my MCE remote.

I then installed the 32 bit version as a frontend on another machine and all is well with that setup too·

So, I would say the advantage over installing Ubuntu + MythTv is that the install wizard helps you quickly get your remote and gpu drivers going. It also helps you choose which plugins you want installed and themes etc. I'm sure there's more to it than that (setup of mythtv user etc?) but all is good in my hood.

---

### Post by newlinux on 2008-10-13
> **Slate8 said:**
> For what its worth I installed and setup the 64 bit Mythbuntu version this week and have had no issues.

I use it as both a back and frontend and found that all hardware just worked after install including my MCE remote.

I then installed the 32 bit version as a frontend on another machine and all is well with that setup too·

So, I would say the advantage over installing Ubuntu + MythTv is that the install wizard helps you quickly get your remote and gpu drivers going. It also helps you choose which plugins you want installed and themes etc. I'm sure there's more to it than that (setup of mythtv user etc?) but all is good in my hood.

Also, FWIW, if you install ubuntu and then install myth using mythbuntu-control-centre, you can get the plugins, themes, GPU and remote configuration done point and click if that is what you want - as well as a lot of other functions. So it makes things easier like the mythbuntu install wizard.

---

### Post by NautiusMaximus on 2008-11-02
Hi Folks

A very specific question related to this thread:

I'm going to be building a system based on a Silverstone GD02 MT case, which has an iMon LCD touchscreen. As far as I can tell, it's the same one as in the Zalman HD160 XT case. Looking at the instructions for getting the touch screen to work in that at [http://www.mythtv.org/wiki/index.php/Zalman_HD160XT](http://www.mythtv.org/wiki/index.php/Zalman_HD160XT) suggests that I'll need to start with Ubuntu, get the touchscreen working, and then install MythTV if I want the thing to work at all.

Am I missing anything, or is that correct?

Thanks
NM

---

### Post by DutchLoki on 2008-11-02
...

---

### Post by jacksonz123z on 2008-11-07
Absolutely right. I tried installing Mythbuntu Hardy and Intrepid versions, I could not even get past the backend configuration stage!  I could not easily follow the forum (?)solutions.  Documentation did not help.  Xubuntu + Mythbuntu control centre worked really well.  I wasted so much time on Mythbuntu.

---

### Post by spoky99 on 2008-11-09
> **laga said:**
> Can you give me some examples where Mythbuntu (MCC) is different from Ubuntu + MythTV?

For me are like egual, the difference is in some configuration script and folder for wakeup recording schedules :D
Is a light distro but you could install all the package you need like.
- ntfs tool
- startup manager (for change the default grub selections, splash image and more other thing)
- codec
and many other thing :D
the only problem is that you could make yourself, but... also whit other solution you could make yourself, the difference is that whit the other solution, in some case, you could't have information, tool or... you could't resolve aniting ;) a nobody can help you.

---

### Post by broncosis on 2012-03-24
well as a mythbuntu user 
I have recently chnaged to the 64 bit version 
on the same hardware found the polish on the install not quite 
as polished as the 32 bit one for some reson but there 
was a improvement in performance 

also having started with mythdora I found mythbuntu 10
less buggy and way faster and less hassle to setup 
granted i  use webmin to setup nfs and samba though 
and I don't use samba for enything 

I am still not a super advanced user
but i do more  than most and I have manged to replace 
all of my windows machined with some flavor of debain 
and I have a centos asterisk machine too 
and everything seems to work 

the MCC works pretty well 
no mythtv install I have ever used has gotten my ati remote wonder to work very well

oddly I guess I don't have many issuses I noticed I on have 4 posts here 
thanks again for a soild instal 

I cast my vote for mythbuntu not for full install then myth tv   unless your using it as a desktop aswell

---

### Post by Chris Musampa on 2012-03-26
It was Ubuntu then add Mythbuntu for me, not by choice though.  I've tried every Mythbuntu live cd between 10.04 and 11.10, none of them would boot (all fail at different points), I've checked the MD5 of the downloads and of the subsequently burnt discs (checked in the very drive they were intended to boot from), all apparently good but no joy.

---

