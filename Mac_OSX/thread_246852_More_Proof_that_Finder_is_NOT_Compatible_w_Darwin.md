---
title: "More Proof that Finder is NOT Compatible w/ Darwin"
date: 2006-08-29
forum: Mac OSX
---

### Post by AlphaMack on 2006-08-29
Try this on for size from OS X's Finder:

See if you can go to /dev or /.vol.  What happens?

[Apple and the Myth of UNIX](http://www.rixstep.com/2/20060828,00.shtml)

I was able to replicate this phenomenon under 10.4.7.

It's bad enough that the Finder suffers from performance issues (hence, the cries to 'FTFF').  It's nice to know that it won't know what to do with some directories either.  For the record, these directories are wholly accessible from the CLI. ](*,)

---

### Post by simonn on 2006-08-29
What would you do with /dev and /.vol if they were accessible from finder?

---

### Post by Rick 1 on 2006-08-30
Spoken like a true fanboy.

You ARE aware that somebody has to go in there, Einstein? Or otherwise there'd be nothing there?

You ARE aware that every other bloody Unix distro on the planet has a GUI based file manager which has no qualms protecting the children from such awesome dangers?

You ARE aware that no other Unix distro is so totally fscked up so it trips over its own hind legs when it tries to navigate its own bloody file system?

You ARE aware that engineers working with any other Unix distro would be ASHAMED to have an issue like this - and ashamed for your manner of comment? 

You ARE aware that no one on any other platform would ever ask such a doobit question as you just have, probably because no one on any other platform would ever conceive of tying on semtex to protect the leader of the colony?

There are enough 'IT' issues in the world for us to take care of. Don't add sociological issues to the mix.

---

### Post by hizaguchi on 2006-08-30
I've gotta agree with simonn.  Finder isn't designed to be a file manager for system administrators.  Yes, some people might ocassionally have a reason to mess around in /dev, but then again those people are probably capable of using the CLI or installing a different file manager.

The vast majority of OSX users would just be confused by the Unixy file structure.  Remember, Apple needs to capture Windows market share to grow, and /dev is foreign to a Windows user.  Hiding stuff that 99% of users will never need to see is just another part of making the interface seem friendlier and more simple, which is a huge portion of the Mac appeal.

---

### Post by hizaguchi on 2006-08-30
I followed the link from the original post, and continued to read some of the articles on that site.  The whole thing reads like a loosely strung together series of broken-logic arguments that can basically be summarized like this:

1. The OSX filesystem is different from other Unix filesystems
2. Finder isn't an administrative tool.
3. OSX isn't all open source (which is evidently a prerequisite of being Unix, just ask Sun).
4. Due to 1, 2, and 3, OSX must not be Unix.
5. I have noticed some odd design choices, in Spotlight for example.
6. Due to 4 and 5, OSX is inferior/bad/the devil.

I don't have the technical knowledge or the time to analyze every point made on the site, but a little common sense revels that a good portion of it is just crap.

---

### Post by simonn on 2006-08-30
Hey, P^HRick 1, why not answer the question then?

What would you do with /dev and /.vol if they were accessible from finder?

---

### Post by mdmunoz on 2006-08-30
Gasp! Someone actually decided to make a file manager for end users!

That must mean that macs are not Unix, and are, in fact, an arm of microsoft and tools of proprietary software overlords that are trying to steal our civil rights and suck out our brains.

Seriously, there are many more file managers for OS X. Sometimes, people make software that isn't 100% open-source to pay their developers. It's still Unix. Get over it.

---

### Post by mike3k on 2006-09-12
That's why you have the terminal & X11. The Finder is an easy to use, familiar GUI for the average user. For administrative tasks, use the terminal.

---

### Post by kragen on 2006-09-14
> Gasp! Someone actually decided to make a file manager for end users!

+1 - The finder is a fantastic tool for users wanting to use their computer, TBH I wish there were more file managers that took the same line - when I'm trying to actualy do some work, I couldnt care less about system files and folders, they clutter my working enviroment & make the things I'm actualy intrested in more difficult to find.

If you ask me you need two file managers - an administrative file manager, and a document file manager.

---

### Post by siriusfox on 2006-10-15
> **kragen said:**
> If you ask me you need two file managers - an administrative file manager, and a document file manager.[http://www.apple.com/feedback/](http://www.apple.com/feedback/)

---

### Post by Ptero-4 on 2006-10-28
That's why I use thunar in "show hidden files" mode and Nautilus together.

---

### Post by wgscott on 2006-12-03
> **Rick 1 said:**
> Spoken like a true fanboy.

You ARE aware that somebody has to go in there, Einstein? Or otherwise there'd be nothing there?

You ARE aware that every other bloody Unix distro on the planet has a GUI based file manager which has no qualms protecting the children from such awesome dangers?

You ARE aware that no other Unix distro is so totally fscked up so it trips over its own hind legs when it tries to navigate its own bloody file system?

You ARE aware that engineers working with any other Unix distro would be ASHAMED to have an issue like this - and ashamed for your manner of comment? 

You ARE aware that no one on any other platform would ever ask such a doobit question as you just have, probably because no one on any other platform would ever conceive of tying on semtex to protect the leader of the colony?

There are enough 'IT' issues in the world for us to take care of. Don't add sociological issues to the mix.



I would happily pay for a RixStep finder drop-in replacement that really is a seamless replacement, even if you make it open-source.  Please write it.  I confess enjoying reading your website rants, but this would be a FAR more subversive way of straightening those clowns out than debating yourself on the internet.  Please consider it.

---

### Post by AlphaMack on 2006-12-04
He does have a Finder drop-in replacement called Xfile, although it's not freeware (part of the ACP package).  It's pretty lightweight for what it does.

---

### Post by wgscott on 2006-12-04
$72 (more than the academic price on OS X) and if you do the comparison test he suggests -- opening /usr/share/man/man3, Finder instantly does what he claims it can't do.  (The screenshot looks like Jaguar -- quite possibly they've improved finder).  The Finder does a lot of other things in addition to file browsing, including mounting networked devices and so forth.  It is hard to get away from it.  I rarely use a filebrowser since I am more comfortable in the unix shell of choice (which for me is zsh).

The Finder is an anachronistic buggy piece of junk and Apple needs to toss it into the fire and start over.

---

### Post by NyteGeek on 2007-04-23
> **Rick 1 said:**
> Spoken like a true fanboy.

You ARE aware that somebody has to go in there, Einstein? Or otherwise there'd be nothing there?

You ARE aware that every other bloody Unix distro on the planet has a GUI based file manager which has no qualms protecting the children from such awesome dangers?

You ARE aware that no other Unix distro is so totally fscked up so it trips over its own hind legs when it tries to navigate its own bloody file system?

You ARE aware that engineers working with any other Unix distro would be ASHAMED to have an issue like this - and ashamed for your manner of comment? 

You ARE aware that no one on any other platform would ever ask such a doobit question as you just have, probably because no one on any other platform would ever conceive of tying on semtex to protect the leader of the colony?

There are enough 'IT' issues in the world for us to take care of. Don't add sociological issues to the mix.

You ARE aware that you can make a point without being a pompous  insulting jack-animal  aren't you?

---

### Post by 3rdalbum on 2007-04-23
I agree with the original poster. I'm an end user, and I find it useful to look at /dev in Nautilus. It's a lot easier on the eye than going "cd /dev && ls | less" and having to determine what is what by names alone.

If Mac and Windows users are confused by the /dev directory, then they won't go into it more than once. It's not like they can use the Finder to do any damage to it.

---

### Post by simonn on 2007-04-23
> **NyteGeek said:**
> You ARE aware that you can make a point without being a pompous  insulting jack-animal  aren't you?

He has no point to make, he is simply advertising the software he is selling.

> **3rdalbum said:**
> I agree with the original poster. I'm an end user, and I find it useful to look at /dev in Nautilus. It's a lot easier on the eye than going "cd /dev && ls | less" and having to determine what is what by names alone.

What do you, personally, look at /dev for in OSX (not linux, OSX)?

> If Mac and Windows users are confused by the /dev directory, then they won't go into it more than once. It's not like they can use the Finder to do any damage to it.

They will go in to it and it will be one more thing they do not understand, so perhaps fear. It is an unnecessary distraction for someone who does not want to know. Anybody who needs or wants do do something in /dev can do it with a terminal so it is not like anyone is denied anything like the OP, advertising his commercial software, tries to make out.

Note, I am not an Mac/OSX fan boy. Macs have their niche which they fill very well, but are not without flaws e.g. sleeping without ejecting external drives on my iBook kills our camera's and ipod's flash ram and requires it to be reinitialized. I just think the OP's arguments are bogus and that, once more, he is simply trying to sell his software.

---

### Post by 3rdalbum on 2007-04-24
> **simonn said:**
> 
What do you, personally, look at /dev for in OSX (not linux, OSX)?

I don't use OS X these days - it always annoyed the heck out of me. /dev is especially handy for looking at block devices - seeing what and how many partitions are available to your computer whether they are mounted or not. I imagine that since OS X doesn't read many filesystem types, there would be increased need for this.

When using open-source software that's been written for a Unix or Linux target, being able to graphically look at /dev would also make things easier - you could see what device file name to pass to the software if it needs low-level access.

> They will go in to it and it will be one more thing they do not understand, so perhaps fear. It is an unnecessary distraction for someone who does not want to know.

I've helped my share of green Windows users before, who have just stayed away from the C:\windows\system32 folder rather than get afraid about its contents. Not to mention that Windows has many many settings that nobody understands :-)

> sleeping without ejecting external drives on my iBook kills our camera's and ipod's flash ram and requires it to be reinitialized.

lol, iPods corrupt their own internal memory/HD by themselves without needing your sleeping iBook to do the job :-P

---

### Post by AlphaMack on 2007-04-24
I don't sell software.

---

### Post by Rick 1 on 2007-04-29
> **hizaguchi said:**
> I've gotta agree with simonn.  Finder isn't designed to be a file manager for system administrators.  Yes, some people might ocassionally have a reason to mess around in /dev, but then again those people are probably capable of using the CLI or installing a different file manager.

The vast majority of OSX users would just be confused by the Unixy file structure.  Remember, Apple needs to capture Windows market share to grow, and /dev is foreign to a Windows user.  Hiding stuff that 99% of users will never need to see is just another part of making the interface seem friendlier and more simple, which is a huge portion of the Mac appeal.
The sad facts of the matter are that Apple do not provide a professional file management tool (hence the need to write one's own, something unheard of on other Unix platforms) and that Apple can for this precise reason not attract the professional crowd and that until Apple break ground as of old in the professional sectors their platform, once so popular with Wall Street, WorldCom, Dell, and other major enterprises, will remain the domain of the Birkenstock/batik shirt crowd who congregate outside Apple churches on the eve of a grand opening to pick up single copies of an OS upgrade and perhaps a new iPod nano. Yes Apple are selling hardware like never before but the platform itself should have long ago reached the tipping point in the market and today it's not even close - perhaps further away than ever. And for goodness sake you don't see Windows falling all over its own feet when it comes to file management. There may be prompts to not go where no man has gone before but if you want in you have to go in. After all, the fact that these directories exist and contain files is proof someone had to go there. And those someones would of course prefer to do things graphically. Claiming there's always the CLI is not only lame - it's complacent rationalisation: a desire to see one's object of adulation as being totally perfect. It's vacuous at best - and embarrassingly so.

But in your complacent rationalisation you're missing the bigger overall point - the 'big picture'. And it's that the dubious team of dubious chops what put together what most likely is the worst file manager on any platform anywhere ever **have absolutely NFC** how Unix and Unix file systems work. The issue isn't that ordinary users won't want to go into /.vol and /dev - it's that F*NDER is so p*ss poor it can't!

---

### Post by Alfa989 on 2007-04-30
> **Rick 1 said:**
> But in your complacent rationalisation you're missing the bigger overall point - the 'big picture'. And it's that the dubious team of dubious chops what put together what most likely is the worst file manager on any platform anywhere ever **have absolutely NFC** how Unix and Unix file systems work. The issue isn't that ordinary users won't want to go into /.vol and /dev - it's that F*NDER is so p*ss poor it can't!

"Ordinary Users" don't want or need to go to the bloody /.vol or /dev for god's sake!!
And that doesn't make the Finder inferior... Finder's only issue is networking (a bit slow)...
I've seen worst ones...

---

### Post by Demio on 2007-05-02
What? Finder is great for day to day use. 

If you're hardcore you won't even need a file managers. The terminal has all the power you need.

But if you THINK you're hardcore and want a "file manager than can access /dev", just get one that allows you to do it.

But stop whining about Finder. It makes you look stupid, and it gives your prodcuts a bad image.

---

### Post by Chrisj303 on 2007-05-03
> **Demio said:**
> What? Finder is great for day to day use. 

If you're hardcore you won't even need a file managers. The terminal has all the power you need.

But if you THINK you're hardcore and want a "file manager than can access /dev", just get one that allows you to do it.

But stop whining about Finder. It makes you look stupid, and it gives your prodcuts a bad image.

Agreed - well said.

---

### Post by 3rdalbum on 2007-05-05
This thread hasn't died already? How bizarre.

---

### Post by ButteBlues on 2007-05-06
I'm an end-user and I like to see those directories.

But, hey, I'm glad that others are so knowledgeable about a platform as to tell me what I do and do not expect out of a file manager - namely the ability to see and manage _all_ files regardless of their location on the FS.

---

### Post by Demio on 2007-05-06
> **ButteBlues said:**
> I'm an end-user and I like to see those directories.

But, hey, I'm glad that others are so knowledgeable about a platform as to tell me what I do and do not expect out of a file manager - namely the ability to see and manage _all_ files regardless of their location on the FS.

Applications->Utilities->Terminal.app

$cd /dev
$ls -la 

Presto. :mad:

Bottom line: if you want to do stuff in /dev and don't know how to use the console then you should stay the hell away from /dev. Period.

---

### Post by ButteBlues on 2007-05-06
> **Demio said:**
> Applications->Utilities->Terminal.app

$cd /dev
$ls -la 

Presto. :mad:

Bottom line: if you want to do stuff in /dev and don't know how to use the console then you should stay the hell away from /dev. Period.
Bottom line is that I should be more than able to use a graphical file manager if I want to.

Or, maybe in the future, when I give support to my Linux-using friends, I'll just start telling them to not even bother installing a desktop environment or window manager. They should know how to use the console, right?

---

### Post by Demio on 2007-05-06
> **ButteBlues said:**
> Bottom line is that I should be more than able to use a graphical file manager if I want to.

Or, maybe in the future, when I give support to my Linux-using friends, I'll just start telling them to not even bother installing a desktop environment or window manager. They should know how to use the console, right?

That's a totally different situation, you're comparing apples to oranges. 

One thing is an advanced Mac OS X user complaining that the File Manager sucks because he can't access /dev (a newbie shouldn't be fiddling with /dev). Besides, Mac OS X was made in such manner you won't ever need to access /dev.

A totally different thing is a linux newbie who probably needs help installing some stuff, or configuring some package (in linux you need access to all system directories).

Apples (Mac OS X :P), Oranges (Linux).

Different OSes for different needs and different persons. Comparing them in this case is just borderline absurd.


Edit: Besides, why the hell would you want to access /dev in a file manager!? /dev is for devices, not files... There is where you find the devices that are connected to the computer, please give me a good reason of why you would like to access /dev from a FILE manager? :S

---

### Post by ButteBlues on 2007-05-06
> **Demio said:**
> That's a totally different situation, you're comparing apples to oranges. 

One thing is an advanced Mac OS X user complaining that the File Manager sucks because he can't access /dev (a newbie shouldn't be fiddling with /dev). Besides, Mac OS X was made in such manner you won't ever need to access /dev.

A totally different thing is a linux newbie who probably needs help installing some stuff, or configuring some package (in linux you need access to all system directories).


One of my friends in question, who, asks me advice fairly often:

(A), in Ruby on Rails, _not_ using that silly tutorial, hand-coded (in Emacs nonetheless) his own fully-featured blogging platform. It took him about 6 hours' actual coding time including taking care of CSS issues, etc.

(B) Just finished writing [this](http://nex3.leeweiz.net/posts/3) little gem


There are advanced users and noobs on _every_ platform, so denying either demographic the features they deem necessary to be productive is stupid at best..


> Different OSes for different needs and different persons. Comparing them in this case is just borderline absurd.

Basic file management capabilities for both groups should be available regardless of platform.

Again, look at Windows - it might have a little warning message, but it will let you browse those sort of directories. Why can't Finder do the same?

---

### Post by Demio on 2007-05-06
> **Demio said:**
> Besides, why the hell would you want to access /dev in a file manager!? /dev is for devices, not files... There is where you find the devices that are connected to the computer, please give me a good reason of why you would like to access /dev from a FILE manager? :S

If you haven't noticed, the only 2 things Finder can't access are /dev and /.vol.

Give me two good reasons on why you would want to access them with a file manager in the first place.

---

### Post by ButteBlues on 2007-05-06
> **Demio said:**
> If you haven't noticed, the only 2 things Finder can't access are /dev and /.vol.

Give me two good reasons on why you would want to access them with a file manager in the first place.
Such reasons are necessary.

The fact that there are **many** complaints out in the wild from system administrators of OSX is testament enough that it is a feature that they need to complete their task.

End of story.

Anyone who continues to try and tell system administrators what they do and do not need out of a platform is not only hypocritical, but based upon what amounts to the antithesis of logic.

---

### Post by Demio on 2007-05-06
> **ButteBlues said:**
> Such reasons are necessary.

The fact that there are **many** complaints out in the wild from system administrators of OSX is testament enough that it is a feature that they need to complete their task.

End of story.

Anyone who continues to try and tell system administrators what they do and do not need out of a platform is not only hypocritical, but based upon what amounts to the antithesis of logic.

Who in the what now?

Many complaints from system administrators you say? I've only seen a couple of them and only in this particular thread. Besides, a competent system administrator doesn't need a freaking file manager to administer /dev. The console is all that he needs.

I administer several boxes, and I only ever needed the trustworthy console. 

So why would they need a file manager for /dev? Give me a good reason :confused: 

/dev is for FREAKING DEVICES. NOT FILES. != FILEMANAGER.

---

### Post by ButteBlues on 2007-05-07
> **Demio said:**
> Who in the what now?

Many complaints from system administrators you say? I've only seen a couple of them and only in this particular thread. Besides, a competent system administrator doesn't need a freaking file manager to administer /dev. The console is all that he needs.

I administer several boxes, and I only ever needed the trustworthy console. 

So why would they need a file manager for /dev? Give me a good reason :confused: 

/dev is for FREAKING DEVICES. NOT FILES. != FILEMANAGER.
You prefer to use the Terminal. Good for you. By all means - have a cookie.


But since you're all up in arms about any file manager having the ability to access /dev, why don't I see mobs of people actively campaigning against _every other UNIX file manager in existence_ for being able to do so?

Or is that just a one-way street?

---

### Post by ThinkBuntu on 2007-05-07
Until I started getting into Unix, I never knew those folders were there. Now that I know they're there, I seldom if ever need to touch them. They would just confuse the hell out of a new user, in my opinion. Application, System, Library, is far more manageable AND understandable, in my opinion.

---

### Post by rai4shu2 on 2007-05-08
I don't really see people itching to complain the moment Nautilus or Konqueror stop showing you /dev or /media. It would just be another quirk that no one would notice for about a year or two.

---

