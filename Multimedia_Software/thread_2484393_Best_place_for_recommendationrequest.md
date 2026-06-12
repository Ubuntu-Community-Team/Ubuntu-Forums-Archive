---
title: "Best place for recommendation/request?"
date: 2023-02-24
forum: Multimedia Software
---

### Post by sparc343 on 2023-02-24
What would be the best place to make a recommendation or request specific to Ubuntu Studio? If this is an appropriate or acceptable place:

I was curious as to if it would be possible to include [Davinci Resolve]("https://www.blackmagicdesign.com/products/davinciresolve/") as an actual part of the default package(s)?

---

### Post by ian-weisser on 2023-02-24
The community volunteers who put together Ubuntu Studio generally ignore drive-by suggestions.

Such suggestions usually involve a lot of work without much improvement for most users.

The suggestions that get listened to come from folks who have contributed their time and labor and understand the development process. Somebody who has put in time and joined the team.

For example, let's start with the basics. Consider it your homework:

- Is the software license compatible with distribution via Ubuntu?
- Is the software Open Source? Is the source code freely available? 
- Has the software been packaged for Debian? Has the software been packaged in a Snap?
- If Debian, has Debian accepted the package?

There's also a huge difference between getting the software into Ubuntu (available via apt or snap) vs. adding an application to the stock ("default") install.

- How much extra download is required for *every* Ubuntu Studio image? (recall that few folks like huge downloads)
- Is the benefit of that extra download worthwhile? Or will too many folks consider it bloat?
- Does the software replace something else that is already part of the stock install?
- If a replacement is likely, are the data files compatible? Remember that you are changing everybody's default application and workflow.

---

### Post by sparc343 on 2023-02-25
> **ian-weisser said:**
> The community volunteers who put together Ubuntu Studio generally ignore drive-by suggestions.

Such suggestions usually involve a lot of work without much improvement for most users.

[B][COLOR=#ff0000]This [/COLOR][COLOR=#ff0000](seriously) [/COLOR][COLOR=#ff0000]makes a lot of sense![/COLOR]
[/B]
The suggestions that get listened to come from folks who have contributed their time and labor and understand the development process. Somebody who has put in time and joined the team.

For example, let's start with the basics. Consider it your homework:

- Is the software license compatible with distribution via Ubuntu?
[COLOR=#ff0000] 
[B] Not (yet) sure. There *is* a freeware distribution available though. Also not sure if the licensing (from either side) would allow for it to be "freely" distributed with a Linux distro such as Ubuntu Studio, or not...
[/B][/COLOR]
- Is the software Open Source? Is the source code freely available? 
[COLOR=#ff0000] 
[B] Gah, Sadly no; I do believe it is proprietary closed source :'(
[/B][/COLOR]
- Has the software been packaged for Debian? Has the software been packaged in a Snap?

[B][COLOR=#ff0000]No, I do not think so.
[/COLOR][/B]
- If Debian, has Debian accepted the package?

[B][COLOR=#ff0000]^
[/COLOR][/B]

There's also a huge difference between getting the software into Ubuntu (available via apt or snap) vs. adding an application to the stock ("default") install.

- How much extra download is required for *every* Ubuntu Studio image? (recall that few folks like huge downloads)

[B][COLOR=#ff0000]This was one thing I was initially thinking about, although slightly differently. I was thinking it may have been nice for the whole ISO to be within the single layer DVD limit of 4.7 GB. Though the image I'm currently downloading is 4.9GB so I was thinking such a good video editor (if could be added) would actually be pretty nominal (since either way 4.9GB means the requisite of a DL disc [if you're still using optical media {obviously it would still fit on USB easily}])...
[/COLOR][/B]
- Is the benefit of that extra download worthwhile? Or will too many folks consider it bloat?

[B][COLOR=#ff0000]I myself have to finish DLing Ubuntu Studio before I get to see it in it's full glory (I actually just learned about it, and am still DLing it as we speak). I do know, I used to be an Adobe Premiere user myself; who has recently switched to Davinci Resolve. I didn't see Resolve, or any other known video editor (to me) in the list of everything that Ubuntu Studio comes with... So, definitely more "homework" here on this one for me because, I have yet to see what it does/doesn't have. I would also have no idea as to what "others" would "think"... I would have to do research (maybe host a poll) to draw a conclusion on that aspect!
[/COLOR][/B]
- Does the software replace something else that is already part of the stock install?

[B][COLOR=#ff0000]Currently unknown (see above). All I do know is I didn't see any video editors (known to me) on the list of included software. I was really impressed to see pretty much everything else that I have used, do use, or would (like to) use (OBS studio, GIMP, Inkscape, Darktable, Blender, Audacity, ETC)
[/COLOR][/B]
- If a replacement is likely, are the data files compatible? Remember that you are changing everybody's default application and workflow.

[B][COLOR=#ff0000]True! Just because I am just learning of Ubuntu Studio doesn't take into account the "countless people" who may have been using it since it's inception!
[/COLOR][/B]


**[COLOR=#000000]I most certainly have some more homework to do on the matter, that's for sure! Let me start by completing the two downloads (I am DLing both "current" and current "LTS" versions) and take them for a spin for a while too![/COLOR]**

---

### Post by ian-weisser on 2023-02-25
+1 for your willingness to do the homework needed to move your idea forward!

In this community, that's the key to success.

Here's a bit of Extra Credit: It's the Ubuntu Studio developers mailing list discussion thread from the last time they reviewed what they include in a stock install. You can see their reasoning: [https://lists.ubuntu.com/archives/ubuntu-studio-devel/2020-May/009295.html](https://lists.ubuntu.com/archives/ubuntu-studio-devel/2020-May/009295.html) . These kinds of discussions are held in the open.

---

### Post by TheFu on 2023-02-25
> **sparc343 said:**
> **[COLOR=#000000]I most certainly have some more homework to do on the matter, that's for sure! Let me start by completing the two downloads (I am DLing both "current" and current "LTS" versions) and take them for a spin for a while too![/COLOR]**

Beware that Ubuntu Studio LTS version is 3 yrs from the release date.  Non-LTS versions have 9 months from the initial release supported.
[https://ubuntustudio.org/support/](https://ubuntustudio.org/support/)
> The currently supported Ubuntu Studio releases are:

    Jammy Jellyfish 22.04 LTS until April 2025 (release notes)
    Kinetic Kudu 22.10 until July 2023 (release notes)

Be certain to always, always, always, read the release notes for your flavor and perhaps the base OS release notes, since they will list known issues and work-arounds.

That link also provides information about where to get the best help and where they prefer to get it. Each project (aka program) usually will have a different preferred method to contact, get help, provide bugs.  Would you contact MSFT for an Adobe issue?  

Coming from the commercial software world, you have a big learning curve.  Being "free" isn't the same as being "F/LOSS". For some people, it doesn't matter, but for F/LOSS developers, it can matter greatly.

---

### Post by oldfred on 2023-02-25
I have never used a video editor.
But found there are several.

**Top 10 Best Free Video Editors for Ubuntu**

[LIST]
[*]OpenShot.
[*]OBS Studio.
[*]PiTiVi.
[*]Kdenlive.
[*]Shotcut.
[*]Lightworks.
[*]HitFilm Express.
[*]VLC.
[/LIST]

When I first moved from Windows to Ubuntu, there were several applications I wanted that were Windows only. It turned out several were actually better in Linux. And after a while found one or two that were not quite as good, but writing a bit of code and changing how I did things gave me most of what I wanted. Still have one app (tax software) that is only in Windows and not in Linux.

---

### Post by sparc343 on 2023-02-25
> **ian-weisser said:**
> +1 for your willingness to do the homework needed to move your idea forward!

In this community, that's the key to success.

Here's a bit of Extra Credit: It's the Ubuntu Studio developers mailing list discussion thread from the last time they reviewed what they include in a stock install. You can see their reasoning: [https://lists.ubuntu.com/archives/ubuntu-studio-devel/2020-May/009295.html](https://lists.ubuntu.com/archives/ubuntu-studio-devel/2020-May/009295.html) . These kinds of discussions are held in the open.

[COLOR=#000000]This makes *perfect* sense! I can see it will be KDEnlive, that will be the software I really desire to "check out"!
[/COLOR]
> **oldfred said:**
> I have never used a video editor.
But found there are several.

**Top 10 Best Free Video Editors for Ubuntu**

[LIST]
[*]OpenShot. 
[*]OBS Studio. 
[*]PiTiVi. 
[*]Kdenlive. 
[*]Shotcut. 
[*]Lightworks. 
[*]HitFilm Express. 
[*]VLC. 
[/LIST]

When I first moved from Windows to Ubuntu, there were several applications I wanted that were Windows only. It turned out several were actually better in Linux. And after a while found one or two that were not quite as good, but writing a bit of code and changing how I did things gave me most of what I wanted. Still have one app (tax software) that is only in Windows and not in Linux.

As described above ([https://lists.ubuntu.com/archives/ubuntu-studio-devel/2020-May/009295.html](https://lists.ubuntu.com/archives/ubuntu-studio-devel/2020-May/009295.html)) - it looks like KDEnlive would be my "best bet". OpenShot and pitivi may just not be adequately sufficient or "advanced" enough for my desires. At least as described by Erich Eickmeyer. I thought VLC was just a "media player", not a video editor... Although I never even gave it a chance, even when all my friends were using it (as a player), because I hated it's "traffic cone" icon!!! Most of the other ones on your list I'm also not familiar with (Shotcut, Lightworks, Hitfilm Express) but would also likely "rule them out" since Erich described KDEnlive as the "more feature-full" video editor! OBS Studio (IMHO) should not even be on a list of "video editors" because it's not really a video editor. It can be used to stream live video and or make recordings (screen capture)(not really "edit" them). OBS, to me, is a requisite on it's own as a video live streaming software!

Even Blender *can* be used to "edit video"; but it is *not* it's primary purpose... Just like Erich said, "it is primarily a 3D modeling and animation application, and video editing is not its default configuration". So even though I've heard you can use it (blender) to edit video, I've never even tried to because I've always used programs that have a primary purpose of editing video; Adobe Premiere and Davinci Resolve!

So I totally understand finding good Linux alternatives from Windows. Though sadly also being a "gamer" I will always have a "need" for at least ONE win machine (since most games are made for Win). I've noticed too though, many of these are also available for Win too! IE: GIMP > photoshop, inkscape > illustrator, darktable > lightroom, blender > maya, audacity > audition, OBS > wirecast/vmix/xsplit/etc, scribus > indesign, etc!

So, the only question that remains (although it can be somewhat subjective) is, is KDEnlive > Premiere? How about, is KDEnlive > Davinci Resolve? That is what I will be seeking to gain the answer to! Because although I will for the most part agree, that F&OSS is > closed source proprietary software, even if it's distributed for free. However, this isn't necessarily the case each and every time... .. .

ps) best of luck on locating adequate tax software!

---

### Post by TheFu on 2023-02-25
> **sparc343 said:**
>  
So, the only question that remains (although it can be somewhat subjective) is, is KDEnlive > Premiere? How about, is KDEnlive > Davinci Resolve? That is what I will be seeking to gain the answer to! Because although I will for the most part agree, that F&OSS is > closed source proprietary software, even if it's distributed for free. However, this isn't necessarily the case each and every time... .. .

ps) best of luck on locating adequate tax software!

With KDEnlive, it used to have major crashing issues, so be certain to save projects early and often.  I think Resolve is probably the best option, even if not F/LOSS.

I don't game much and have nearly zero interest in running current games.  I used to game a bunch in the mid-late 1990s ... so under Win95 and WinNT4.  Sadly, I was screwed by Win98.  Just booting it and never touching anything would result in a BSOD after a few hours. That pushed me towards Linux desktops. I'd been running Linux servers for some time by that point.

---

### Post by sparc343 on 2023-02-25
> **TheFu said:**
> With KDEnlive, it used to have major crashing issues, so be certain to save projects early and often.  I think Resolve is probably the best option, even if not F/LOSS.

I don't game much and have nearly zero interest in running current games.  I used to game a bunch in the mid-late 1990s ... so under Win95 and WinNT4.  Sadly, I was screwed by Win98.  Just booting it and never touching anything would result in a BSOD after a few hours. That pushed me towards Linux desktops. I'd been running Linux servers for some time by that point.

Every time I /think/ I'm going to get closer to completely eliminating "Win" from my life, another reason crops up that I "have" to keep it around. If not anything else, "gaming" is one of those reasons now. I do fancy my old school/classic/retro games as well (born in the early 80's here, so kind of the pinnacle of gaming years!); but I also like loading up my favorite flavor MMORPG once a while too. Currently that is Guild Wars II. And I'm pretty sure GWII is not available for Linux, though of course I could be wrong; because it does seem some of these developers and or studios and or distributors are finally getting the hint (that people <3 Llinux over Win)..! Although I have always had personal reservations about "steam" (rather buy a boxed product myself), even many Steam games I am noticing are "compatible" with Linux :D Though, some "classics" I enjoy from time to time, are strictly Win (The ORG: Hitman: Codename 47 for example)...

It would be nice to be able to "move" my entire "creative" workflow over to one OS; LINUX! Though I have already taken a keen liking to this Davinci Resolve - that may wind up being something (else) I "need" to keep a Win machine around for (I have been reading that Resolve is primarily for Win or CentOS (RPM) based distros [that installing on Ubuntu or DEB based distros may carry added 'problems' and or difficulties])..!

Oh well, I think for my next build (desktop) it's going to be a dual boot system, one drive with Win, one with Ubuntu Studio! Each to serve their own "needs"! Maybe I'll even just design and build two complete standalone systems next time around rather than dual boot! Only time will tell... .. . I too have been running Linux servers for quite some time. I ran, run, or will run; game servers for Counter Strike, MineCraft, Perfect World; all on ~ you guessed it, LINUX! Anyone in the I.T. "world" knows Linux is just a good server OS, and Server and Win(blows) should not even be said in the same sentence! 

But I was kind of afraid of this "answer"... I will still give KDEnlive a "chance" I think, but it's also not every day I do a video editing project. Guess I will have to go fly my drone some to get some new footage to give me a reason to edit something :D

---

