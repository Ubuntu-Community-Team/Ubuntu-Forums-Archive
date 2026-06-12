---
title: "Global Menus - doomed to be unreliable?"
date: 2011-02-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by 3rdalbum on 2011-02-06
I don't mind the global menus in general, but I fear that it might be impossible to cleanly implement them in Ubuntu without modifying every program.

In Unity, if a program opens up a dialog box, this stops the global menubar from showing all the program's menus; it then just shows File > Quit in the menubar. Confusing. Somehow Unity will need to know when a dialog should not override its parent's menus.

If programs crash, they can leave the menubar in an inconsistent state, in my experience. And if they stop responding, the menubar goes grey and then seems to be inconsistent afterwards.

Add to this programs like Firefox that cannot use the global menubar because they are not really GTK, and you end off with a bit of a mess.

Does the Ubuntu team have any ideas on how to fix these problems? Or are they design problems with Linux architecture?

---

### Post by chrisccoulson on 2011-02-07
> **3rdalbum said:**
> I don't mind the global menus in general, but I fear that it might be impossible to cleanly implement them in Ubuntu without modifying every program.

In Unity, if a program opens up a dialog box, this stops the global menubar from showing all the program's menus; it then just shows File > Quit in the menubar. Confusing. Somehow Unity will need to know when a dialog should not override its parent's menus.

If programs crash, they can leave the menubar in an inconsistent state, in my experience. And if they stop responding, the menubar goes grey and then seems to be inconsistent afterwards.

Add to this programs like Firefox that cannot use the global menubar because they are not really GTK, and you end off with a bit of a mess.

Does the Ubuntu team have any ideas on how to fix these problems? Or are they design problems with Linux architecture?

For the firefox problem: [https://launchpad.net/~chrisccoulson/+archive/ppa]("https://launchpad.net/~chrisccoulson/+archive/ppa"). Please test! (and report bugs)

---

### Post by Kazade on 2011-02-07
I'm not sold on the whole Global Menu *idea* let alone the implementation...

I'm using the global menu on my vertically challenged laptop, and it seems a good fit there, but it doesn't fit at all on any of my desktops - especially where I have dual monitors connected. 

Also, this whole hiding the menu behind the title means the menu is pretty much undiscoverable - I can't see how it's an improvement in usability. 

I would have preferred it if there was no top panel, and the application name in the title bar of each window became a drop down menu containing File, Edit etc. That way you get the vertical space saving without the issues inherent in global menus.

---

### Post by ronacc on 2011-02-07
the whole idea of a global menu seems flawed to me for a multitasking system . To have to leave the window you are working in in order to access its menu is both unintuitive and leads to inconsistencies that only serve to slowdown workflow rather than enhance it . The only scenario where it might prove slightly useful by providing a FEW more pixels for the content of the window is a netbook not a desktop .And before anyone mentions OSX I'll say that I have a MAC and love it and plan to buy another one but the global menu thing is probably my most disliked thing about OSX. Heres a scenario to illustrate the insanity of a global menu . I have both a monitor and my 42" lcdtv hooked up to my MAC and drag safari over to the tv to watch Hulu ( or what ever ) the controls for hulu are on the tv screen and the menu for safari is over on the monitor and this type of problem will occur with any dual monitor setup. And what about the inconsistencies caused by the fact that the same menu choices do not apply to all applications , this leads to the menu changing depending on which is active and with multiple windows that you are constantly moving between and using, with a single menu for all this leads to confusion or at least disorientation.

---

### Post by philinux on 2011-02-07
On my Acer 1410 I just set the top panel to autohide. Seems to me to be an excellent space saver.

I'll try unity again but not till alpha 3.

I dont think Unity will ever be used on my desktops.

---

### Post by Simian Man on 2011-02-07
The thing is that Linux programs have used local menus forever, so every Linux toolkit and application has conformed to this standard.  There is no conceivable way to implement a global menu cleanly across *all* programs.

But that won't stop Ubuntu from trying to ape OSX.

---

### Post by ELD on 2011-02-07
> **ronacc said:**
> the whole idea of a global menu seems flawed to me for a multitasking system . To have to leave the window you are working in in order to access its menu is both unintuitive and leads to inconsistencies that only serve to slowdown workflow rather than enhance it . The only scenario where it might prove slightly useful by providing a FEW more pixels for the content of the window is a netbook not a desktop .And before anyone mentions OSX I'll say that I have a MAC and love it and plan to buy another one but the global menu thing is probably my most disliked thing about OSX. Heres a scenario to illustrate the insanity of a global menu . I have both a monitor and my 42" lcdtv hooked up to my MAC and drag safari over to the tv to watch Hulu ( or what ever ) the controls for hulu are on the tv screen and the menu for safari is over on the monitor and this type of problem will occur with any dual monitor setup. And what about the inconsistencies caused by the fact that the same menu choices do not apply to all applications , this leads to the menu changing depending on which is active and with multiple windows that you are constantly moving between and using, with a single menu for all this leads to confusion or at least disorientation.

Agreed I really do fail to see how making me move further away from the application to the top of the screen just to use it's menu, then selecting the other application and then going to the top of the screen again for that programs menu is at all a good thing.

---

### Post by teachop on 2011-02-07
What I cannot understand yet is why do Global Menus cause problems for people that are not using them.  I am logging into Natty Classic mode, and have removed the panel applet for the global menus, and yet eclipse has no menu bar in the application (unless I do a funny add/remove dance with the panel applet).  I think if it is not Unity, and the panel applet isn't there, it should revert to the standard behavior.  Hope it will when all the bugs are squashed.

---

### Post by cariboo on 2011-02-07
Check to see if eclipse has created a launcher in /usr/share/applications, if it hasn't, you can create one yourself, It may be an idea to create a bug report about the problem.

---

### Post by seeker5528 on 2011-02-07
> **3rdalbum said:**
> In Unity, if a program opens up a dialog box, this stops the global menubar from showing all the program's menus; it then just shows File > Quit in the menubar. Confusing. Somehow Unity will need to know when a dialog should not override its parent's menus.

And how many programs actually let you access an item on the menu when there is a dialog window open? If you can't access them, it doesn't matter whether they are shown to you or not.

I would say that in the shorter term there are bigger fish to fry so it's probably not that big of a priority, in the longer term probably something that should be resolved.

I would think a higher priority item that should be resolved first is to insure that dialog boxes never open full screen, at least with the desktop profile.

> **ronacc said:**
> the whole idea of a global menu seems flawed to me for a multitasking system . To have to leave the window you are working in in order to access its menu is both unintuitive and leads to inconsistencies that only serve to slowdown workflow rather than enhance it .

Unless you are using a window manager that allows you to access the menus of a window in the background without bringing the application to the foreground, I don't see how it really makes that much difference.

If you are using a laptop with a track pad instead of a mouse, I can see a little more reason to argue the point.

Window placement may also factor in, but for my personal use, the area I would click when the menu is inside the window is rarely more than one third of the screen distance away in any direction from where it shows up in the global menu, and at least with the mouse, I often find it quicker to move to the top of the screen and down to the menu I want, then to hit the menu I want in a non-maximized window that is not at the top of the screen.

Later, Seeker

---

### Post by mpt on 2011-02-08
> **3rdalbum said:**
> In Unity, if a program opens up a dialog box, this stops the global menubar from showing all the program's menus; it then just shows File > Quit in the menubar. Confusing. Somehow Unity will need to know when a dialog should not override its parent's menus.

It&#8217;s already possible for a dialog to [detect whether the unified menu bar is being used,]("https://wiki.ubuntu.com/MenuBar#detecting") and if so, to reuse the menus of its parent window. As far as I know, no programs do that yet.

Meanwhile, though, the menu bar itself can be much smarter than it is.

The next step is to show a working &#8220;Edit&#8221; menu with &#8220;Undo&#8221;, &#8220;Redo&#8221;, &#8220;Cut&#8221;, &#8220;Copy&#8221;, &#8220;Paste&#8221;, etc for dialogs that contain native text fields.

The next step beyond that is to examine the menus of a dialog&#8217;s parent window, to see if they contain the relevant [stock items]("http://library.gnome.org/devel/gtk/stable/gtk-Stock-Items.html") for those editing commands. If they do, reuse those menus, making every other menu and menu item temporarily insensitive, instead of switching to a completely separate set of menus.

(If you&#8217;re willing and able to help out with either of those, please do [dive in]("https://code.launchpad.net/appmenu-gtk").)

> *If programs crash, they can leave the menubar in an inconsistent state, in my experience. And if they stop responding, the menubar goes grey and then seems to be inconsistent afterwards.*

Those are just bugs, not intractable problems. [Reporting them]("https://bugs.launchpad.net/indicator-appmenu"), with minimal testcases, would help a lot. Thanks!

---

### Post by ronacc on 2011-02-08
ah the simple joys of reinventing the wheel and having it come out square .At least its egalitarian all roads are equally bumpy .

---

### Post by mc4man on 2011-02-08
I don't have a big issue w/ the global menu but there are clearly some app windows where having a disconnected menu makes no sense and is quite unwieldy. (distance makes no difference

While atm it is a simple edit to individually  config apps to use GM or keep their menu's, it would be nice if a tool to do so was provided.

(personally, which matters not at all, I'd rather that apps only use the GM when maximized, when not then retain their menus in the app window.

---

### Post by hugmenot on 2011-02-08
I’m a fan of global menu for the simple reason that I rarely ever use menus. It just saves space and makes apps look much cleaner.
Really happy with how it turned out.

Out of all of Ayatana output I only use indicator-messages, indicator-applications and indicator-appmenu. Nothing else.

Any remaining kinks in appmenu will be ironed out hopefully.

---

### Post by ranch hand on 2011-02-09
> **ronacc said:**
> ah the simple joys of reinventing the wheel and having it come out square .At least its egalitarian all roads are equally bumpy .
Some of the roads I am using would probably feel smoother with a square wheel.

That is not to say that I see any reason for the Global Menu.  Sounds like a food joint with an ego problem.

---

### Post by sneax on 2011-02-09
Programs itself should have another layout. Why not have the program title, the close buttons AND the menu all on the same top menubar on the program itself? A bit like google chrome does. They dont waste space.

This has best of both worlds.

The only fixed desktop thing on your screen would be the dock on the left, this is logical with all the widescreens being used now. The full vertical place will be available to programs. And those programs will not waste space with empty title bars and half filled menu bars.

This is for me the best solution. I dont like windows 7 which has a great dock but wastes space with title bars. I dont like the standard gnome desktop because it has 2 panels AND each program has a titlebar AND a menu. Loads of loss of vertical space. I dont like unity because of the global menu, it loses the point of having multiple windows on screen which can be dragged around. I dont like osx because the dock is just a waste of space (to the left and right of the dock is always a lot of empty space and it is too big) and it also has this global menu.

I have the best solution! But I am not a dev :(

---

### Post by ronacc on 2011-02-09
off topic: Hi RH glad to see you back from the wilds , at least for awhile .

---

### Post by MacUntu on 2011-02-09
It's cycle two for the global menu - give it some time to mature.

---

### Post by ronacc on 2011-02-09
> **MacUntu said:**
> It's cycle two for the global menu - give it some time to mature.

you mean its going to get worse ?

---

### Post by psusi on 2011-02-09
I really enjoyed the global menu in 10.04 netbook edition.  I really do NOT like it so far in Natty.  I think it is because it makes sense when all windows are maximized, but when a window is not maximized, it should not use the global menu.

As for dialog boxes, they don't use the parent window's menu because they aren't the parent window.  Without the global menu, the dialog does not have its own menu, so why would you expect it to when using a global menu?  If the dialog box is not a modal one, then you can switch back to the parent window and THEN use its menu.

---

### Post by vmonkey on 2011-02-09
I think it would be best to save space just by using global-menus in the application border... Img just created by GIMP.
[http://2i.cz/2i/i/4d52ffd1/f7f2bdb5b2f1f43d6896afc536e0ab90/db316b4192.f.png](http://2i.cz/2i/i/4d52ffd1/f7f2bdb5b2f1f43d6896afc536e0ab90/db316b4192.f.png)

EDIT - used in window-border when not maximized

---

### Post by psusi on 2011-02-09
> **vmonkey said:**
> I think it would be best to save space just use global-menus in the application border... Img just created by GIMP.
[http://2i.cz/2i/i/4d52ffd1/f7f2bdb5b2f1f43d6896afc536e0ab90/db316b4192.f.png](http://2i.cz/2i/i/4d52ffd1/f7f2bdb5b2f1f43d6896afc536e0ab90/db316b4192.f.png)

Huh?

---

### Post by Anutesyn on 2011-02-10
> **sneax said:**
> I dont like the standard gnome desktop because it has 2 panels AND each program has a titlebar AND a menu. Loads of loss of vertical space. I dont like unity because of the global menu, it loses the point of having multiple windows on screen which can be dragged around. I dont like osx because the dock is just a waste of space (to the left and right of the dock is always a lot of empty space and it is too big) and it also has this global menu.

I'm with you on this one; I too have issues with the clutter of the standard Gnome layout. Being used to sitting on OSX I can sometimes get frustrated with all the menus and panels etc. 

Obviously I'm a global menu fan, if it is implemented fully. Also off-topic: The OSX dock has an auto hide option Cmd+Alt+D, also there's no empty space on the sides of my dock since it's filled up with apps :P

---

### Post by kklimonda on 2011-02-11
I disagree with the opinion that the global menu (or unity, or some unity APIs) are doomed (to be unreliable, to not be used by anyone etc.) only because that's the current situation. If Ubuntu gets enough traction then developers will focus to make sure that those features are well supported in their applications. If it doesn't then the global menu will be the least of our problems anyway.

---

### Post by rburkartjo on 2011-02-11
it is still only alpha2 and too early imho to make a judgement

---

### Post by Simian Man on 2011-02-11
> **kklimonda said:**
> I disagree with the opinion that the global menu (or unity, or some unity APIs) are doomed (to be unreliable, to not be used by anyone etc.) only because that's the current situation. If Ubuntu gets enough traction then developers will focus to make sure that those features are well supported in their applications. If it doesn't then the global menu will be the least of our problems anyway.

But the thing is that, currently, Ubuntu is just one of several Linux distros that are all pretty much the same.  I don't use Ubuntu, but programs I write on other Unix-based OSs work on Ubuntu just fine.

By changing things like this, Ubuntu is breaking compatibility with existing projects that care nothing for Ubuntu's conventions.  OSX can do that because they are a separate platform.  Asking Linux developers to specially prepare their programs for a particular distro is unreasonable, and having Ubuntu packagers do it themselves is unmaintainable.

---

### Post by ronacc on 2011-02-11
> **kklimonda said:**
> I disagree with the opinion that the global menu (or unity, or some unity APIs) are doomed (to be unreliable, to not be used by anyone etc.) only because that's the current situation. If Ubuntu gets enough traction then developers will focus to make sure that those features are well supported in their applications. If it doesn't then the global menu will be the least of our problems anyway.

It is not that unity is currently not perfect that we object to it , after all this is the development forum , we understand what goes on while things are in constant flux .It is much deeper than that , Simian Man has a very good point , ubuntu is poking their finger in the eye not only of other distros but also at its own foundation , Gnome . as for my feelings on the matter see post # 4 this thread .

---

### Post by castrojo on 2011-02-11
> **Simian Man said:**
> Asking Linux developers to specially prepare their programs for a particular distro is unreasonable, and having Ubuntu packagers do it themselves is unmaintainable.

I don't get this, if you use GTK or Qt, then your app will work, other than some edge cases where apps dynamically do something fancy with a menu, which is fixable.

... and the work is in the process of being accepted into upstream Qt.

---

### Post by Mr. Picklesworth on 2011-02-11
I'm pretty concerned about this as well. I think it would be cool if someone (peacefully) maintained a Unity branch without the global menu (and various fixes that are possible without it) just to have that available. I would love to do it myself, but I have enough things I need to finish :p

In my opinion, the biggest problem with the global menu stuff right now is when one has a maximized window with a modal dialog in front of it. If our user wants to move that maximized window, he will try grabbing its title bar (the top panel) only to realise that it *isn't* the title bar of the maximized window: it's a proxy for the modal dialog. In fact, because the dialog is modal, there is No Way to move the maximized window.

In between trying that and figuring out what is going on, our user is confused and frustrated. This is an illusion: we have a visual metaphor (top panel=title bar) that *doesn't make sense*, where the only way to make sense of it is to read stuff and process that information thoroughly. (&#8220;This says Preferences, but the window I want to move was called Scribes, so this isn't actually its title bar&#8230;&#8221;).

That top panel has to solve two distinct, occasionally contrary problems: it has to turn into the titlebar of a maximized window, and it has to serve the title and window menu for any other window. Unless somebody can find a really innovative solution here, I think the best plan is to pick one for the time being and figure out the other one later. Perhaps when all the new toys (GTK3 with GApplication Actions) have landed.

Having said that, it is of course not finished yet so I'm hoping it improves. Having a distinct design for the top panel that does not look like a window title bar could help&#8230;

> **mpt said:**
> The next step beyond that is to examine the menus of a dialog&#8217;s parent window, to see if they contain the relevant [stock items]("http://library.gnome.org/devel/gtk/stable/gtk-Stock-Items.html") for those editing commands. If they do, reuse those menus, making every other menu and menu item temporarily insensitive, instead of switching to a completely separate set of menus.
Frankly, that sounds like jamming a square peg into a round hole.

---

### Post by mc4man on 2011-02-11
> **Mr. Picklesworth said:**
> 

In my opinion, the biggest problem with this global menu stuff is when one has a maximized window with a modal dialog in front of it. If our user wants to move that maximized window, he will try grabbing its title bar 
Being prone to confusion at times myself I have to say your post is more confusing than anything I've seen w/ GM in 12+ wk.s
Why would anyone try to move a maximized window? (maybe that's a trick I've never learned
And if there is a modal dialog open then won't the user need to deal w. it first, then it would be gone.
Actually see no issue at all w. global menu's in maximized windows, atm the use in unmaximized windows is less than ideal in some (many) instances

---

### Post by ronacc on 2011-02-11
[QUOTE=mc4man;10449761]
Why would anyone try to move a maximized window? (maybe that's a trick I've never learned
QUOTE]

I can think of several scenarios where one might need/want to move a maximized window , the most obvious being to move it from one monitor to the other in a multi-screen setup.

---

### Post by rg4w on 2011-02-11
> **Mr. Picklesworth said:**
> In my opinion, the biggest problem with the global menu stuff right now is when one has a maximized window with a modal dialog in front of it. If our user wants to move that maximized window, he will try grabbing its title bar (the top panel) only to realise that it *isn't* the title bar of the maximized window: it's a proxy for the modal dialog. In fact, because the dialog is modal, there is No Way to move the maximized window.

In between trying that and figuring out what is going on, our user is confused and frustrated. This is an illusion: we have a visual metaphor (top panel=title bar) that *doesn't make sense*, where the only way to make sense of it is to read stuff and process that information thoroughly. (“This says Preferences, but the window I want to move was called Scribes, so this isn't actually its title bar…”).

That top panel has to solve two distinct, occasionally contrary problems: it has to turn into the titlebar of a maximized window, and it has to serve the title and window menu for any other window. Unless somebody can find a really innovative solution here, I think the best plan is to pick one for the time being and figure out the other one later. Perhaps when all the new toys (GTK3 with GApplication Actions) have landed.
All good points.

Has the team posted their usability research methods that led to this solution?

I trust (hope) a change this big is based on something more than a mere guess....

---

### Post by seeker5528 on 2011-02-11
> **Mr. Picklesworth said:**
> In my opinion, the biggest problem with this global menu stuff is when one has a maximized window with a modal dialog in front of it. If our user wants to move that maximized window, he will try grabbing its title bar (the top panel) only to realise that it *isn't* the title bar of the maximized window: it's a proxy for the modal dialog. In fact, because the dialog is modal, there is No Way to move the maximized window.

What about 'Alt'+'Mouse 1 Drag' in some area belonging to the maximized window?

Is there a relatively easy way to determine if a dialog box is modal and proxy the boarder/menu stuff from the parent instead, without having to do application specific stuff? Or maybe as an alternative is there a way to tie these together in a relative way, so moving the child moves the parent?

Just throwin' spaghetti at the wall to see if anything sticks. ;)

Later, Seeker

---

### Post by mc4man on 2011-02-11
> **ronacc said:**
> [QUOTE=mc4man;10449761]
Why would anyone try to move a maximized window? (maybe that's a trick I've never learned
QUOTE]

I can think of several scenarios where one might need/want to move a maximized window , the most obvious being to move it from one monitor to the other in a multi-screen setup.

I guess I should have been a bit more specific, though the quoted area said
"If our user wants to move that maximized window, he will try _grabbing its title bar"_
Being a normal plain user like I thought was being referred to, why would I try to grab the title bar of a maximized window in an attempt to move it?
(I'm sitting here on my son's default, unmodified 10.10 install - you can not grab and move a maximized window.

What is missing with the global menu is the r. click on title bar move options, but that wasn't mentioned

---

### Post by seeker5528 on 2011-02-11
> **mc4man said:**
> Why would anyone try to move a maximized window?

I wondered that too in relation to modal dialog boxes. The only reason I can think of would be to see something behind that is displaying some information relevant to what the dialog box is asking for.

But more generally, relative to Unity, dragging to/from the top panel changes a window to/from it's maximized state, double clicking works to if all you actually care about is maximizing/unmaximizing and not window placement placement.

Later, Seeker

---

### Post by seeker5528 on 2011-02-11
> **mc4man said:**
> What is missing with the global menu is the r. click on title bar move options, but that wasn't mentioned

Clicking the workspace switcher and dragging the desired window from one desktop to another seems to work whether the window is maximized or not.

Later, Seeker

---

### Post by mc4man on 2011-02-11
> Clicking the workspace switcher and dragging ...
That works just fine.
Had expo inadvertently disabled here, actually use 'unfold' instead.

Hopefully at some point changing/editing some plugins in ccsm will stop crashing compiz and in some cases unsetting all the default enabled plugins, ( though some of them are not really needed

---

### Post by Mr. Picklesworth on 2011-02-11
> **mc4man said:**
> 
I guess I should have been a bit more specific, though the quoted area said
"If our user wants to move that maximized window, he will try _grabbing its title bar"_
Being a normal plain user like I thought was being referred to, why would I try to grab the title bar of a maximized window in an attempt to move it?
(I'm sitting here on my son's default, unmodified 10.10 install - you can not grab and move a maximized window.

What is missing with the global menu is the r. click on title bar move options, but that wasn't mentioned

*I* should have been more specific!
So, what I meant was more as an example. This also affects being able to close or minimize a window, for example (or anything else where you would use its title bar). And it isn't just modal or child windows; it's the same deal for any kind of unmaximized window above a maximized window. The case with a modal dialog is just particularly unpleasant.

It still isn't a hugely common thing, but when it happens it's very frustrating. And I think it's the sort of thing that happens a lot for some use cases and not at all for others. I think people using GIMP, for example, will bump into this fairly often.

Come to think of it, there's a funky workaround that could suffice: treat the panel as the title bar for the front-most maximized window regardless of what the global menu is referring to.

Edit: Filed [bug report #717496]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/717496") for that specific issue. Hopefully we can figure out the individual bits that are upsetting and figure this out with no further thoughts of the abrasive choice I kind of suggested earlier.

Hope I'm not seeming too grouchy here. I love Unity! I just really want this to be as amazing as possible, and I have a particularly strong knee-jerk reaction against anything that could possibly lead to cruft &#8212; real or imagined :)

---

### Post by mc4man on 2011-02-11
> **Mr. Picklesworth said:**
> 
So, what I meant was more as an example. ...

That makes more sense (after reading your bug report
It's probable that the Gm will always present some user case issue, though I don't think your idea is all that bad.
Myself, as things are ATM, would be quite happy if only maximized windows used the GM and unmaxed retained their menus. (if there were no 
maxed windows the GM would stay on the desktop.
Though this is just best use for me and quite unlikely to happen
> 
I love Unity! I just really want this to be as amazing as possible,
+1
i also think it's got great potential and hopefully ubuntu will stay the course even when it's not totally realized in natty.

from LP
> One solution is for the top panel to maintain the window controls (and _draggable titlebar-esque_ area) of the front-most maximized window

I, for the life of me still can't see how one does that (drag a maxed window),  - no matter

---

### Post by seeker5528 on 2011-02-11
> **Mr. Picklesworth said:**
> *I* should have been more specific!
So, what I meant was more as an example. This also affects being able to close or minimize a window, for example (or anything else where you would use its title bar). And it isn't just modal or child windows; it's the same deal for any kind of unmaximized window above a maximized window. The case with a modal dialog is just particularly unpleasant.

Windows with modal child dialogs are a special case because you can't bring the parent window to the foreground.

> It still isn't a hugely common thing, but when it happens it's very frustrating. And I think it's the sort of thing that happens a lot for some use cases and not at all for others. I think people using GIMP, for example, will bump into this fairly often.

For these other cases I'm finding it hard to view it as a problem since you can just click on the icon of the desired app in the dock to bring it to the foreground and if it has multiple windows click it again to choose a window to bring to the foreground. I might argue that clicking an icon in the dock of an application that has multiple windows should go directly to showing you that apps open windows to let you choose which to bring to the foreground without a second click, but it's a trade off either way, for MDI applications it would be preferred to bring all the windows to the foreground at once.

> Come to think of it, there's a funky workaround that could suffice: treat the panel as the title bar for the front-most maximized window regardless of what the global menu is referring to.

And it doesn't sound more confusing to you than the current situation to have title bar stuff from one window/application and menu stuff from a different window/application displayed together?

Hmmmmm. :-k Funky indeed. :P

Later, Seeker

---

