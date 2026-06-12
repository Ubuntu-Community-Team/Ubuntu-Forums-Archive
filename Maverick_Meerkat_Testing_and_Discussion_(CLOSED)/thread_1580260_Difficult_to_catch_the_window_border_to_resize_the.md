---
title: "Difficult to catch the window border to resize the window"
date: 2010-09-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kahumba on 2010-09-23
Hi,
it's true for me, especially compared to windows ( 7), sometimes it takes me up to 10 seconds and gets annoying.

---

### Post by Giantmundo on 2010-09-23
Yes I agree it can be.  I suggest that you just go for the corners.  They are easy.

---

### Post by andreselsuave on 2010-09-23
there is a nice shortcut: alt + drag with right click. this way you can pull from everywhere inside the window to resize. no need to pull from the corner

---

### Post by kerry_s on 2010-09-23
alt+f8
or
right click the title bar-> resize

---

### Post by mcduck on 2010-09-23
...or just use a Metacity theme that has wider window borders. If I remember right there are some already installed by default, and you'll easily find hundreds more from [http://gnome-look.org/]("http://gnome-look.org/")

Also note that most themes have a slightly larger area intended for easy resizing, located in the bottom right corner of windows.

---

### Post by qamelian on 2010-09-23
It should be easier after yesterday's updates which included an update to the light-themes package that makes the resize handle a bit larger.

---

### Post by kahumba on 2010-09-23
> **Giantmundo said:**
> Yes I agree it can be.  I suggest that you just go for the corners.  They are easy.
Thanks all, but still:
1) There are no "special corners" if the window has no status bar or so (see screenshot)
2) The keyboard shortcuts are really workarounds rather than problem solvers.
3) The default Ubuntu settings with the default theme should allow for an easy (side) window resize.
4) I think it doesn't qualify as a paper cut hence unfortunately I can't report this minor but somewhat annoying issue.
5) It was suggested the updates fixed this - they didn't, at least for the theme that I'm using which is the default one.

---

### Post by kerry_s on 2010-09-23
is that the file manager?

---

### Post by kahumba on 2010-09-23
It's another file manager, but the issue not only about file managers, it's about all application windows in general that choose not to have a status bar (along with the other points mentioned in post #7)

---

### Post by kerry_s on 2010-09-23
> **kahumba said:**
> It's another file manager, but the issue not only about file managers, it's about all application windows in general that choose not to have a status bar (along with the other points mentioned in post #7)

i guess you'll just have to file bugs against what ever programs your using that don't follow gnome specs. the problems not gnome or ubuntu.

---

### Post by teachop on 2010-09-23
Glad to see this topic covered here.  I will sign on your bug if you start it.  This drives me nuts.  Trying to grab the left side of windows with the mouse is not user friendly at all.

---

### Post by kahumba on 2010-09-23
Problem is, I don't know where this issue belongs, is it Gtk, is it Gnome, is it the theme, is it the X server or anything else..

---

### Post by mcduck on 2010-09-23
Actually you can't really report it as a bug at all. (Things working as designed is never a bug, not even if the original design itself might be flawed).

You'd have to file a *feature request* about wider borders for default theme.

[http://brainstorm.ubuntu.com/]("http://brainstorm.ubuntu.com/")

---

### Post by recluce on 2010-09-23
I agree, it is difficult to grab the borders for a resize, a problem that was introduced in Lucid, IIRC.

If the OP files a bug or feature request, I will surely sign it!

@kerry_s: you missed the point. The individual apps have NOTHING to do with this problem, it is a theme-related thing.

---

### Post by oldsoundguy on 2010-09-23
System> Preferences> Mouse>  dial down the sensitivity.  Worked for me.

---

### Post by kahumba on 2010-09-23
> **oldsoundguy said:**
> System> Preferences> Mouse>  dial down the sensitivity.  Worked for me.
I doubt, it has nothing to do with what we're discussing, but I still tried it to make sure I'm right - it didn't help.

As to submitting to brainstorm, their site says:
> Are you reporting something that is not working as it should be? Brainstorm is **not** the right place for it! You should file a bug report on Launchpad, the Ubuntu bug tracker. Thus I think it should be submitted as a feature request to launch-pad, but I don't know what domain this request  belongs to (as earlier suggested it could be the X Server, gtk, gnome, theme etc..). Anyone knows?

---

### Post by mc4man on 2010-09-23
Take your pick
[https://bugs.edge.launchpad.net/ubuntu/+source/metacity/+bug/160311](https://bugs.edge.launchpad.net/ubuntu/+source/metacity/+bug/160311)

---

### Post by kahumba on 2010-09-23
Thanks, judging by how old the report is (2007) and how many folks are interested into solving it, looks like it's more difficult to solve than creating an AI.

---

### Post by VinDSL on 2010-09-23
> **kahumba said:**
> Problem is, I don't know where this issue belongs, is it Gtk, is it Gnome, is it the theme, is it the X server or anything else..First of all, this is NOT a bug!  It's a function of *metacity*, and it's a matter of style vs practicality.

Big borders are fugly, but they're easy to grab.  Small borders look fly, but they're hard to grab...  :)

For frustrated mousers, the "problem" is the various border widths, in whatever theme you're using.

You can 'fix' the 'problem' yourself, if you don't mind doing a little coding.

_Example_:  I'm using a customized theme -- a hybrid -- if you will.  For the window borders, I'm using Ambiance.

If I don't like trying to grab a 1-pixel wide border, the task becomes rewriting portions of the Ambiance XML file.

Here's my path...

[IMG]http://vindsl.com/images/ambience-xml-path.png[/IMG]

And, here's my file...

[IMG]http://vindsl.com/images/ambience-mxl-content.png[/IMG]

Personally, I don't think it's worth the effort.  I'd rather waste my time tweaking Conky!

But, if you're into this kind of stuff, that's the cure...  8-)

---

### Post by 23meg on 2010-09-23
> **mcduck said:**
> Actually you can't really report it as a bug at all. (Things working as designed is never a bug, not even if the original design itself might be flawed).

> **VinDSL]First of all, this is NOT a bug! It's a function of metacity, and it's a matter of style vs practicality.[/QUOTE]

These statements go by a very engineering-oriented definition of a bug, which, while it can be valid in other contexts, doesn't really reflect how bugs are currently handled in Ubuntu. If a user interface element is misdesigned to the point that it gives a significant number of people severe problems in daily use, that's treated a bug, and there are initiatives ([One Hundred Papercuts]("https://launchpad.net/hundredpapercuts"), [Ayatana Design]("https://bugs.edge.launchpad.net/ayatana-design")) that deal specifically with such issues.

[QUOTE=mcduck said:**
> You'd have to file a *feature request* about wider borders for default theme.

[http://brainstorm.ubuntu.com/]("http://brainstorm.ubuntu.com/")

Ubuntu Brainstorm is not a good place to file feature requests. The best place to file feature requests is the bug tracker or mailing list of the relevant upstream project.

---

### Post by VinDSL on 2010-09-23
> **mgunes said:**
> If a user interface element is misdesigned to the point that it gives a significant number of people severe problems in daily use, that's treated a bug[...]Understood, but there are multiple ways of resizing a window.

Is it a bug, if someone decides to use the most difficult method?!?!?  :confused:

<snip>

---

### Post by libssd on 2010-09-23
The bug report describes how to "fix" the problem. Although I haven't started playing with Maverick yet, I assume that window geometry is defined in the same basic way as in Lucid.

**Summary:**

Some themes (*e.g*., Dust) already come with wider borders; this should be obvious when you play around with different themes in Appearances. But if you don't like one of these themes, you can change the window border dimensions by editing the xml configuration file for a theme that you otherwise like. For illustration, let's say Clearlooks.

Themes are installed by default in /usr/share/themes:

```
libssd@libssd-AA1:/usr/share/themes$ ls
AgingGorilla       Industrial          Murrine-Gray
Albatross          Inverted            Murrine-Light
Amaranth           Kiwi                MurrineRounded
Ambiance           Lush                MurrineRoundedIcon
Atlanta            Metabox             MurrineRoundedLessFramed
Bright             Mist                MurrineRoundedLessFramedIcon
**Clearlooks**        MurrinaAquaIsh      Murrine-Sky
ClearlooksClassic  MurrinaAzul         New Wave
Crux               MurrinaBleu         New Wave Dark Menus
Custom             MurrinaBlu          NOX
Darklooks          MurrinaBlue         Nuvola
```

A theme's window attributes are defined in an xml file that is usually in the metacity-1 directory for the theme:

```
libssd@libssd-AA1:/usr/share/themes/Clearlooks$ ls -l metacity-1 
total 48
-rw-r--r-- 1 root root 47228 2010-06-11 10:50 metacity-theme-1.xml

``` 

Since this file is owned by root, you need to use (gk)sudo when editing it (before making any changes, it's a good idea to make a backup copy, so that you can revert if you get lost, or something just doesn't work). 

Look for the "GEOMETRY" section of the xml file, and change the width and height values to ones that work for you. Then save, and you have wider borders that are easier to grab. For me, 5 points was big enough to grab and small enough that it didn't get ugly, but YMMV. 

```
$ gksudo gedit /usr/share/themes/Clearlooks/metacity-1/metacity-theme-1.xml

<!-- ::: GEOMETRY ::: -->
<frame_geometry name="normal" rounded_top_left="true" 
rounded_top_right="true" rounded_bottom_left="false" 
rounded_bottom_right="false">
   <distance name="left_width" value="**5**"/>
   <distance name="right_width" value="**5**"/>
   <distance name="bottom_height" value="**5**"/>
```
**More information:** 
[LIST]
[*][http://blogs.gnome.org/metacity/2008/05/30/themes/](http://blogs.gnome.org/metacity/2008/05/30/themes/)
[*][http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html](http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html)
[/LIST]
Have fun! :P

---

### Post by 23meg on 2010-09-23
> **VinDSL said:**
> Understood, but there are multiple ways of resizing a window.

Is it a bug, if someone decides to use the most difficult method?!?!?  :confused:

It's a bug if the globally most common method (not just in Ubuntu or free software, but WIMP interfaces in general) is particularly difficult to use in Ubuntu.

---

### Post by VinDSL on 2010-09-23
> **mgunes said:**
> It's a bug if the globally most common method (not just in Ubuntu or free software, but WIMP interfaces in general) is particularly difficult to use in Ubuntu.The other side of the story is...

With borders wider, everyone will complain about *accidently* dragging the borders.

For instance: "WTF?  Every time I use the scroll bar, the window size changes!!!"  :)

---

### Post by 23meg on 2010-09-23
> **VinDSL said:**
> The other side of the story is...

With borders wider, everyone will complain about *accidently* dragging the borders.

For instance: "WTF?  Every time I use the scroll bar, the window size changes!!!"  :)

You just summed up how tackling "simple" design and usability problems such as this, and picking defaults that work for large percentages of users can be harder than creating an AI.

---

### Post by ktp on 2010-09-23
> **mgunes said:**
> You just summed up how tackling "simple" design and usability problems such as this, and picking defaults that work for large percentages of users can be harder than creating an AI.

that is so true!!!

---

### Post by libssd on 2010-09-23
> **mgunes said:**
> These statements go by a very engineering-oriented definition of a bug, which, while it can be valid in other contexts, doesn't really reflect how bugs are currently handled in Ubuntu. If a user interface element is misdesigned to the point that it gives a significant number of people severe problems in daily use, that's treated a bug, and there are initiatives ([One Hundred Papercuts]("https://launchpad.net/hundredpapercuts"), [Ayatana Design]("https://bugs.edge.launchpad.net/ayatana-design")) that deal specifically with such issues.
Agreed -- this is a cultural problem where the engineers believe they have the "right" answer, users be damned.

Fortunately, it's Linux, so you can fix your own borders, but not easily (as is the case, in -- dare I say -- Windows). It shouldn't be that hard to provide an appearance option that allows the user to directly manipulate the width of the border (a la Windows) without having to resort to tracking down metacity xml files and tweaking them.

---

### Post by libssd on 2010-09-23
> **mgunes said:**
> You just summed up how tackling "simple" design and usability problems such as this, and picking defaults that work for large percentages of users can be harder than creating an AI.
True enough, but why not give users a tool to let *them* set their own choices? It doesn't have to be as hard as editing a metacity xml file. The first thing I did when I set up XP was to increase the thickness of the window borders because I kept missing them; this is a standard option in customizing the desktop -- it's even fairly intuitive! 

Apple has a different solution (which I don't like either): allow users to grow/shrink a window only from the bottom right corner, thus avoiding the entire dilemma of easy to grab vs easy to look at. It's always great fun watching a Windows user trying to figure out how to resize a damned window on OS X. 

It pains me to say so, but this is one of the few areas where the Windows UI has always been superior to both OS X and Linux.

---

### Post by 23meg on 2010-09-23
> **libssd said:**
> True enough, but why not give users a tool to let *them* set their own choices? It doesn't have to be as hard as editing a metacity xml file. 

It doesn't have to be as hard as finding a graphical tool that deals with the strange concept of "window borders", and tweaking things until they actually work, either. It should just work by default, and not need tweaking. You shouldn't expect most users to have a concept of "window borders", let alone "window border thickness", and let alone be interested in tweaking such thickness.

It would be a nice thing to have in a "tweaks" application, such as [the upcoming one in GNOME]("http://www.hadess.net/2010/02/were-removing-settings-again.html"), or a dedicated "theme tweaking" one, for those interested in tweaking it.

---

### Post by libssd on 2010-09-23
It's not a strange concept, and as others have pointed out, there are difficult design tradeoffs to be made between thick and thin. The point is that one size doesn't fit all, so the user should be able to adjust things to his/her preferences -- perhaps even to create a window with only a crippled Mac-style bottom-right corner grow/shrink area, if that is preferred.

---

### Post by 23meg on 2010-09-24
> **libssd said:**
> It's not a strange concept, and as others have pointed out, there are difficult design tradeoffs to be made between thick and thin.

It's a strange, alien concept, unless your understanding of how computers work is based on technical implementation specifics such as :

[list][*]What I'm seeing is an xlib + GTK+ window
[*] This window is surrounded by a frame and decorations drawn by a window manager 
[*] My particular window manager is Metacity
[*] Metacity has themes 
[*] The default Metacity theme that Ubuntu ships has thin borders, so it's sometimes difficult to resize windows
[*] Metacity themes are basically XML files
[*] Now, by editing those files I can have thicker window borders and YAY! Problem fixed.[/list]

Once you've learned those specifics, it can be very hard to understand the position of those who aren't aware of them. But most people simply aren't, and they don't think like you. Non-technical users tend to think of the way computers work through [mental models]("http://www.uxmag.com/design/the-secret-to-designing-an-intuitive-user-experience") that they construct based on past experience and feedback from the software, not through technical implementation specifics. Here's an approximation of how a new user with weak motor skills and intermediate familiarity with common operations in the WIMP paradigm will think when faced with the problem of a hard to catch window border:

[list][*] I'm using this web browser to send an email, and now I need to fit another window into this screen so that I can easily copy and paste a piece of text
[*] If I hold the window on its edge or corner, press down the mouse button and move my mouse, it should shrink; that's how my previous computer worked
[*] Let me try; but there's no arrow when I point to the corner?
[*] Oh wait, it's there for a moment, but disappears! Perhaps I'm doing something wrong..
[*] Maybe if I move my pointer slowly enough, I can catch it 
[*] There! Oh, but my hand slipped off the mouse while dragging, and it's too small now.. too large this time.. too small.. again..
[*] [2 minutes later] Finally I resized the window to fit another on the screen, but I have an aching wrist, it took two minutes, and it made me feel stupid and incapable. This should be easier.[/list]

[QUOTE=libssd]The point is that one size doesn't fit all, so the user should be able to adjust things to his/her preferences -- perhaps even to create a window with only a crippled Mac-style bottom-right corner grow/shrink area, if that is preferred.[/QUOTE]

I disagree. With something so mundane, obvious yet essential as window operations, the default should work for more than 90% of users, and should be survivable for the remaining less than 10% (they should be able to continue using the system, albeit with some suffering). Technical users who are so inclined to have a perfectly fitting system have the means to do so, and the somewhat less technical who don't want to tweak configuration files can continue have easier means through "tweak" applications and the like. But non-technical users who are new to computing will not be interested in having a fine-tuned experience; they want defaults that work well enough for them to perform their tasks and reach their goals. Giving them broken defaults or bad design, along with ways to remedy those, will not make them happy.

---

### Post by VinDSL on 2010-09-24
I was just playing around with different themes, and "Aging Gorilla" has nice fat borders (that are easy to grab).  

Rather ironic, when you think about it...  :-\"

---

### Post by xzero1 on 2010-09-24
If they were selling Ubuntu for *profit*, do you think they would allow such an annoyance to most users? When I choose a different theme, why should I expect the functionality to differ?

---

### Post by kahumba on 2010-09-24
Thanks anyone, especially to [libssd]("http://ubuntuforums.org/member.php?u=865837") (post #22) that helped fix the issue for me. The solution creates vertical lines along the window borders that don't look too well with the default theme, but it's a welcome trade-off, besides it could probably be easily fixed if the default theme takes care of this scenario too.

---

### Post by recluce on 2010-09-24
> **libssd said:**
> The bug report describes how to "fix" the problem. Although I haven't started playing with Maverick yet, I assume that window geometry is defined in the same basic way as in Lucid.

**Summary:**

Some themes (*e.g*., Dust) already come with wider borders; this should be obvious when you play around with different themes in Appearances. But if you don't like one of these themes, you can change the window border dimensions by editing the xml configuration file for a theme that you otherwise like. For illustration, let's say Clearlooks.



Thanks, that worked for me! The aesthetic trade-off is small and the usability is much better. I have applied the modification on my Lucid system and will do it on Maverick later today.

---

### Post by seeker5528 on 2010-09-24
> **mgunes said:**
> It's a strange, alien concept, unless your understanding of how computers work is based on technical implementation specifics such as :

[list][*]What I'm seeing is an xlib + GTK+ window
[*] This window is surrounded by a frame and decorations drawn by a window manager 
[*] My particular window manager is Metacity
[*] Metacity has themes 
[*] The default Metacity theme that Ubuntu ships has thin borders, so it's sometimes difficult to resize windows
[*] Metacity themes are basically XML files
[*] Now, by editing those files I can have thicker window borders and YAY! Problem fixed.[/list]

Once you've learned those specifics, it can be very hard to understand the position of those who aren't aware of them.

It seems to me the real question is.... Why is the active area for grabbing the window boarder defined by the thickness of the window border?

Later, Seeker

---

### Post by 23meg on 2010-09-24
> **seeker5528 said:**
> It seems to me the real question is.... Why is the active area for grabbing the window boarder defined by the thickness of the window border?

Probably because of "Module Territory Syndrome", which is often an unfortunate trait of modular systems developed in a distributed manner - that is: the task of resizing windows is delegated to the window manager, and the area of responsibility of the window manager is limited to the confines of the window decoration it draws. The window manager cannot "reach out", so to speak, a few pixels inside or outside its dedicated area to provide a better user experience if needed.

On the upside, there are important signs of this being amended recently by the introduction of design thinking into development processes of user-facing products such as desktop environments, thanks to which people are starting to converge around use cases, scenarios and goals, as opposed to "That's not the responsibility of my module so I don't have to think about it" kind of thinking. 

On the more technical side, platforms are getting rid of artificial territorial constraints like these in favor of more flexible components. Case in point: CSD, the new GTK theming API, the Clutterification going on in projects such as MeeGo and GNOME Shell.

---

### Post by TBerk on 2010-09-24
The default is too thin.

(Can't they make the visible part esthetically pleasing and add a functional few more pixels to the thin line?)

I found **Clearlooks With a Cherry on Top**    decent enough theme to default to, for now, until i find something better.


TBerk

---

### Post by mc4man on 2010-09-25
While slightly off the topic what is seen here with compiz/nvidia is a rather 'odd' way of resizing windows
The window itself isn't initially resized, instead the window frame is (white lines 
And at times the white 'frame' or part of can be left behind.

This and some other things point to the relatively sad state of compiz in 10.10
(the recent update to compiz made things even worse (title bar), though a patch has been proposed there

(after removing all compiz packages and setting metacity as compositing manager performance is noticably better all around

---

### Post by dkjMusic on 2010-09-25
I agree with those that think this a problem and opened a thread requesting that someone help create a modified Radiance metacity with wider borders.

Anyway, I ran across the following this morning:

[http://blogs.gnome.org/metacity/2010/01/20/border-widths-under-user-control/](http://blogs.gnome.org/metacity/2010/01/20/border-widths-under-user-control/)

The patch described therein would suit me just fine if it works as claimed.

How do I apply this patch to test it? Is it something that someone new to Ubuntu can do? I don't want to have to recompile the kernel or some such.:)

---

### Post by Rashkae on 2010-09-25
> **kerry_s said:**
> i guess you'll just have to file bugs against what ever programs your using that don't follow gnome specs. the problems not gnome or ubuntu.

You mean, such as Gnome Terminal? (to start)

---

### Post by VinDSL on 2010-09-25
> **dkjMusic said:**
> Anyway, I ran across the following this morning:

[http://blogs.gnome.org/metacity/2010/01/20/border-widths-under-user-control/](http://blogs.gnome.org/metacity/2010/01/20/border-widths-under-user-control/)Interesting comment (on that page)...

> Using Alt+middle click seems to accomplish something similar, but for resizing.[...] It&#8217;s definitely my preferred way to resize a window.I'll have to remember that one.

Beats right-clicking the title bar and choosing 'resize', and/or grabbing/dragging the frames!

Just navigate to the side of the screen you want to resize, then Alt+middle click...

---

### Post by 23dornot23d on 2010-09-25
Nice one .... I like that Alt + Middle click ..... :)

---

### Post by mc4man on 2010-09-25
> The patch described therein would suit me just fine if it works as claimed
It does work though ...
> How do I apply this patch to test it? Is it something that someone new to Ubuntu can do?

You would need to rebuild the metacity source wuth the patch applied, considering it (the patch) won't apply cleanly it's a little bit of work.
Screen shows setting, - the xml edit previously mentioned may be easier

(personally I have and use the corner

---

### Post by MarkieB on 2010-09-26
no longer participating in ubuntuforums.org

---

### Post by sdowney717 on 2010-09-26
why not, when mousing over the window border, the border gets thicker?

---

### Post by libssd on 2010-09-26
I don't know, patching Metacity sounds like more work than just editing the theme's XML file.

However, I really liked suggestion #3 from the Metacity blog:

> A third suggestion, not made on either bug, is that the clickable area of a border should be a few pixels wider than its visible area.
If technically feasible, this sounds like the best of both worlds.

I still don't consider this a "bug"; rather it's a case of deafness on the part of developers. Paraphrasing a business slogan, "The user is not always right, but he **is** always the user."

---

### Post by seeker5528 on 2010-09-27
> **sdowney717 said:**
> why not, when mousing over the window border, the border gets thicker?

I would be happy if it was only thicker on the corners, often I am grabbing a corner anyway.

Later, Seeker

---

### Post by DanaG on 2010-09-27
This is particularly fun on my laptop display, where 1 pixel is a mere 0.1728 millimeters.

---

### Post by MarkieB on 2010-09-28
no longer participating in ubuntuforums.org

---

### Post by 23meg on 2010-10-09
And [here]("http://blogs.fedoraproject.org/wp/mclasen/2010/10/09/getting-a-grip/") it is, solved The Right Way™.

---

### Post by libssd on 2010-10-09
> **mgunes said:**
> And [here]("http://blogs.fedoraproject.org/wp/mclasen/2010/10/09/getting-a-grip/") it is, solved The Right Way™.
Nice. I like the understatement of the poster: "This is just a small thing, but I really like how it has turned out." I guess it's time for me to take a look at Meerkat.

---

### Post by 23meg on 2010-10-09
> **libssd said:**
> Nice. I like the understatement of the poster: "This is just a small thing, but I really like how it has turned out." I guess it's time for me to take a look at Meerkat.

This is a GTK+ 3 change that has only landed in git master yesterday. It's not part of Maverick, and needs modifications in applications to be taken advantage of.

---

### Post by libssd on 2010-10-09
After reading through the MM release notes, I was afraid that might be the case.

---

### Post by cariboo on 2010-10-09
I noticed today that some apps have a resize handle in the lower right corner, so far Firefox, gedit, deluge and nautilus have them. See the screenshot of gedit.

---

### Post by 23meg on 2010-10-09
> **cariboo907 said:**
> I noticed today that some apps have a resize handle in the lower right corner, so far Firefox, gedit, deluge and nautilus have them. See the screenshot of gedit.

Those are the old handles that are specific to the status bar, which not every application uses. The blog post I linked to details the advantages of the new implementation.

---

