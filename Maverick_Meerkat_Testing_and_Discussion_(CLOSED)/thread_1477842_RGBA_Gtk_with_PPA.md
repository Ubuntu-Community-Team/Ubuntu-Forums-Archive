---
title: "RGBA Gtk with PPA"
date: 2010-05-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by plun on 2010-05-09
Another feature for Maverick which can be tested from a ppa

Please follow and read carefully.

[https://wiki.ubuntu.com/DesktopTeam/RgbaGtkWithPPA/](https://wiki.ubuntu.com/DesktopTeam/RgbaGtkWithPPA/)

[[img]http://ubuntu-pics.de/thumb/59736/snapshot20_4HtIUK.png[/img]](http://ubuntu-pics.de/bild/59736/snapshot20_4HtIUK.png)

:)



----

---

### Post by MacUntu on 2010-05-09
> **plun said:**
> feature

Gimmick! :P

---

### Post by go7Ul1ai on 2010-05-09
It's a tad slow on my laptop, then again it is running on an Intel chipset ^_^

---

### Post by plun on 2010-05-09
Works just fine with my PC....I3 and nVidia

I lost my icons but it was easily fixed.
```

gconf-editor
```

/apps/nautilus/preferences/show_desktop

uncheck and check and they are back....


--

---

### Post by plun on 2010-05-09
> **MacUntu said:**
> Gimmick! :P

Nope.... feature....:popcorn:

[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/491521/](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/491521/)

:)

---

### Post by Merk42 on 2010-05-09
So we're implementing a feature/gimmick that makes the windows hard to read that won't even work in the most popular applications?

Good job...

---

### Post by plun on 2010-05-09
> **Merk42 said:**
> So we're implementing a feature/gimmick that makes the windows hard to read that won't even work in the most popular applications?

Good job...

Well. works just fine for nearly all apps.....

Also beats Windoooze 7 and transparency...:guitar:

---

### Post by Merk42 on 2010-05-09
> **plun said:**
> Well. works just fine for nearly all apps.....

Also beats Windoooze 7 and transparency...:guitar:

Except for the big ones that get marketed, Firefox and OpenOffice.org (as well as others)

How exactly does it beat Windows 7's Aero?  I've used that and the transparency is subtle and doesn't make things like the buttons transparent.

---

### Post by plun on 2010-05-09
> **Merk42 said:**
> Except for the big ones that get marketed, Firefox and OpenOffice.org (as well as others)

How exactly does it beat Windows 7's Aero?  I've used that and the transparency is subtle and doesn't make things like the buttons transparent.

I just like RGBA more then Aero.....just my opinion.

Also that its a good idea to use RGBA with Maverick.

---

### Post by zekopeko on 2010-05-09
> **Merk42 said:**
> So we're implementing a feature/gimmick that makes the windows hard to read that won't even work in the most popular applications?

Good job...

You are jumping to conclusions again. The transparency is one side effect of RGBA. [Here is what is possible with RGBA-enabled GTK+]("https://wiki.ubuntu.com/DesktopTeam/Specs/SpitAndPolish")

---

### Post by Merk42 on 2010-05-09
> **zekopeko said:**
> You are jumping to conclusions again. The transparency is one side effect of RGBA. [Here is what is possible with RGBA-enabled GTK+]("https://wiki.ubuntu.com/DesktopTeam/Specs/SpitAndPolish")

I totally forgot about the cleaner GTK+ widgets when this was first brought up 6months ago.
I guess it doesn't help that the OPs screenshots were a terrible example.


Though the other thing I pointed out, that it won't work in popular applications like Firefox and OO.org is still true, right?

---

### Post by zekopeko on 2010-05-09
> **plun said:**
> Well. works just fine for nearly all apps.....

Also beats Windoooze 7 and transparency...:guitar:

No, no it doesn't. Windows 7 Aero doesn't use transparency in such a  tacky way. Transparency is a usability nightmare if you don't have blurring enabled for transparency. Another problem is text on transparent surface. Aero fixes that by drawing a white gradient outline around and behind text.

Not to mention that Aero looks pretty but that is subjective.

---

### Post by zekopeko on 2010-05-09
> **Merk42 said:**
> I totally forgot about the cleaner GTK+ widgets when this was first brought up 6months ago.
I guess it doesn't help that the OPs screenshots were a terrible example.


Though the other thing I pointed out, that it won't work in popular applications like Firefox and OO.org is still true, right?

I think you are correct on that. But that doesn't mean they can't be patched. I would wager that Firefox is in a better position since they are planning to use Aero more extensively (ala Chrome) and there are hacks to make Firefox transparent completely.

---

### Post by plun on 2010-05-09
> **zekopeko said:**
> No, no it doesn't. Windows 7 Aero doesn't use transparency in such a  tacky way. Transparency is a usability nightmare if you don't have blurring enabled for transparency. Another problem is text on transparent surface. Aero fixes that by drawing a white gradient outline around and behind text.

Not to mention that Aero looks pretty but that is subjective.

Ok, blur is a optional feature also discussed within the wiki

Also found this.. I don't know if Cimi still is working with Murrine ?

[http://www.cimitan.com/murrine/node/204](http://www.cimitan.com/murrine/node/204)

To make it adjustable must be preferred.

I still likes RGBA...:wink:

---

### Post by ranch hand on 2010-05-09
I don't think I want to have something that looks even close to that on my box at all.

I fixed the transparent background on the terminal screen on all but one 10.04-testing installs the first time I pulled it up.  The one I left only made it a week.  That is just irritating as it can be.  Just absolutely hated it.

EDIT

Just looked at all the pictures in the mock up again.  There is no way.  I am now, officially. in love with things with square corners.

---

### Post by BwackNinja on 2010-05-09
RGBA is a nice feature, but nothing we want enabled by default. It would be especially nice and not too obnoxious if used with the new feature in KWin (which I wouldn't be surprised if it comes to compiz soon, now that 0.9 will have a reparenting window decorator). Window decorations can be painted behind translucent windows, giving more of the vista/7 style transparency.

source: [http://blog.martin-graesslin.com/blog/2009/11/window-decoration-behind-translucent-windows/](http://blog.martin-graesslin.com/blog/2009/11/window-decoration-behind-translucent-windows/)

---

### Post by plun on 2010-05-09
Ok... Compiz 0.9 can also be tested now...

[http://forum.compiz.org/viewtopic.php?f=112&t=12565](http://forum.compiz.org/viewtopic.php?f=112&t=12565)

but in the higher software division...:)

---

### Post by plun on 2010-05-09
Found a severe bug with the rgba ppa if a user wants to use Gnome-shell

gtk2-module-rgba breaks Gnome shell

EDIT mail sent to Erik !

---

### Post by zekopeko on 2010-05-09
> **BwackNinja said:**
> RGBA is a nice feature, but nothing we want enabled by default. It would be especially nice and not too obnoxious if used with the new feature in KWin (which I wouldn't be surprised if it comes to compiz soon, now that 0.9 will have a reparenting window decorator). Window decorations can be painted behind translucent windows, giving more of the vista/7 style transparency.

source: [http://blog.martin-graesslin.com/blog/2009/11/window-decoration-behind-translucent-windows/](http://blog.martin-graesslin.com/blog/2009/11/window-decoration-behind-translucent-windows/)

RGBA will be enabled by default (at least that is the plan). And no the transparent windows aren't the only feature of RGBA. They are probably the least important.

---

### Post by BwackNinja on 2010-05-09
> **zekopeko said:**
> RGBA will be enabled by default (at least that is the plan). And no the transparent windows aren't the only feature of RGBA. They are probably the least important.

Right, but windows being able to look good (consistent, no weird corners) transparent means that it works well. All widgets need to be able to be rendered offscreen well (which is a goal of GTK+3), and engines need to be patched to take advantage of this. Not even murrine with an RGBA-enabled theme assumes offscreen widget rendering, and actually uses color and transparency of the background to repaint it behind widgets. This fact is especially annoying with stuff like webkit in which murrine actually had a bug clearing the right part of the screen to the background, and with rgba enabled, parts with forms are see-through, but still have borders around the widgets. Offscreen rendering fixes this, and allows murrine to work a little better there.

This is why I never complain about the theme, but only complain about the technologies behind it. GTK+ is getting cleaner and more full-featured, however it has lots of parts that will need to be changed in many applications and things that depend on it like the engines. This is why it is so great that there can be a big break like the break to GTK+3. Splitting off gtkNotebook into the options-dialog style and tabbed MDI window style is a possibility, and that would make gedit, epiphany, midori all look a little less hacky and more consistent with not having to abuse gtkNotebook.

As far as I see, the jump to GNOME3 and GTK+3 are much different than the jump to KDE4. All that I see is mostly cleanup of the platform and some new features added like zeitgeist and gnome-shell. It is universally good.

---

### Post by MCVenom on 2010-05-09
Couldn't use the PPA on my Maverick VM, got this error: 

```
W: Failed to fetch http://ppa.launchpad.net/erik-b-andersen/rgba-gtk/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by MacUntu on 2010-05-10
That's because there are no maverick packages yet: [http://ppa.launchpad.net/erik-b-andersen/rgba-gtk/ubuntu/dists/](http://ppa.launchpad.net/erik-b-andersen/rgba-gtk/ubuntu/dists/) :P

---

### Post by Starks on 2010-05-10
> **BlackOtaku said:**
> Couldn't use the PPA on my Maverick VM, got this error: 

```
W: Failed to fetch [http://ppa.launchpad.net/erik-b-andersen/rgba-gtk/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/erik-b-andersen/rgba-gtk/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```
Change the maverick to lucid in your Software Sources.

---

### Post by plun on 2010-05-10
Gnome-Shell crash is fixed.... mutter disabled as RGBA app.

> Changelog

gtk2-module-rgba (0.2-0ubuntu4~lucid7) lucid; urgency=low

  * Added mutter to list of programs to run without Gtk RGBA so that
    gnome-shell won't crash.
 -- (Erik B. Andersen)   Sun, 09 May 2010 16:11:32 -0700


But now I cannot enable RGBA ....:^o


Sending a mail to Erik again and asks....

---

### Post by MCVenom on 2010-05-10
> **Starks said:**
> Change the maverick to lucid in your Software Sources.
I did and it works now, thanks :D

---

### Post by Mr. Picklesworth on 2010-05-12
> **Merk42 said:**
> So we're implementing a feature/gimmick that makes the windows hard to read that won't even work in the most popular applications?

Good job...

This feature is just guaranteeing an alpha channel for drawing operations. It isn't the patch's problem that themes abuse it horrifically :)

---

### Post by null_pointer_us on 2010-05-12
> **zekopeko said:**
> [Here is what is possible with RGBA-enabled GTK+]("https://wiki.ubuntu.com/DesktopTeam/Specs/SpitAndPolish")
:-s :-k :shock: [-o<

If this is coming in 10.10, I'm sure some great themes will follow.


EDIT: The other major theme-related issue I'd like to see cleared up for 10.10 is the icon sets. I installed a bunch of themes (40?) from the standard repositories in 10.04, and icon set quality is all over the map. Some won't load even when the requested package IS installed. Most icon sets only cover a few of the icons in the gnome panel menu widget. Some icon sets only have one folder icon (e.g. in Home, every folder looks identical).

---

### Post by plun on 2010-05-12
Well, its even better with Gnome-shell running...

[[img]http://ubuntu-pics.de/thumb/61465/snapshot24_2syuky.png[/img]](http://ubuntu-pics.de/bild/61465/snapshot24_2syuky.png)

Likes it...

---

### Post by zekopeko on 2010-05-13
> **plun said:**
> Well, its even better with Gnome-shell running...

[[img]http://ubuntu-pics.de/thumb/61465/snapshot24_2syuky.png[/img]](http://ubuntu-pics.de/bild/61465/snapshot24_2syuky.png)

Likes it...

Now enable blur.

Also, client side decoration should solve the problem of "no transpareny on window borders".

---

### Post by screaminj3sus on 2010-05-13
> **plun said:**
> Well. works just fine for nearly all apps.....

Also beats Windoooze 7 and transparency...:guitar:

Im gonna have to disagree here, I dont like transparency like this just for transparency sake, having the whole window transparent is just pointless, aero at least has a design philosophy and is usable. Aero was designed to keep focus on the application/content rather then the window border. Having a whole window transparent is just silly.

EDIT:
> **zekopeko said:**
> You are jumping to conclusions again. The transparency is one side effect of RGBA. [Here is what is possible with RGBA-enabled GTK+]("https://wiki.ubuntu.com/DesktopTeam/Specs/SpitAndPolish")

With some polish like this it would look nice though and i would support it.

---

### Post by BobCFC on 2010-05-17
> **screaminj3sus said:**
> Im gonna have to disagree here, I dont like transparency like this just for transparency sake, having the whole window transparent is just pointless, aero at least has a design philosophy and is usable. Aero was designed to keep focus on the application/content rather then the window border. Having a whole window transparent is just silly.

EDIT:


With some polish like this it would look nice though and i would support it.


Does anyone know if it will ever be possible to have the gtk transparent without affecting the fonts?  Is this a limitation of the engine or GTK itself?

We have been able to make menus and dialogs transparent for years with compiz but nobody does because it's unreadable.

---

### Post by benjamimgois on 2010-05-17
> **zekopeko said:**
> You are jumping to conclusions again. The transparency is one side effect of RGBA. [Here is what is possible with RGBA-enabled GTK+]("https://wiki.ubuntu.com/DesktopTeam/Specs/SpitAndPolish")

Looking at this screenshots it's quite nice, but in the current state it's almost unusable, i tried it here and remove it after 5min.

---

### Post by go7Ul1ai on 2010-05-17
> **BobCFC said:**
> Does anyone know if it will ever be possible to have the gtk transparent without affecting the fonts?  Is this a limitation of the engine or GTK itself?

We have been able to make menus and dialogs transparent for years with compiz but nobody does because it's unreadable.

It's pretty readable to me..

[[IMG]http://imgur.com/oxuqo.png[/IMG]](http://imgur.com/oxuqo.png)

---

### Post by null_pointer_us on 2010-05-17
That transparency screenshot looks very nice.

In past releases (including 9.10), font smoothing did not seem to be alpha-aware, resulting in ugly/frail fonts when drawn on any dark backgrounds.

I suppose that was fixed in 10.04, given the default theme has dark panels and menus.

EDIT: How are you getting the blur behind translucent windows? Is it a Compiz plugin, or is it specific to the RGBA GTK PPA? My Compiz Blur Windows plugin seems to blur randomly, w/o respecting its own window-matching rules.

---

### Post by ranch hand on 2010-05-17
> **lee.jarratt said:**
> It's pretty readable to me..

[[IMG]http://imgur.com/oxuqo.png[/IMG]]("http://imgur.com/oxuqo.png")
It certainly looks readable to me.

It also looks absolutely horrid but that is just my lack of good taste I am sure.

---

### Post by screaminj3sus on 2010-05-17
> **null_pointer_us said:**
> That transparency screenshot looks very nice.

In past releases (including 9.10), font smoothing did not seem to be alpha-aware, resulting in ugly/frail fonts when drawn on any dark backgrounds.

I suppose that was fixed in 10.04, given the default theme has dark panels and menus.

EDIT: How are you getting the blur behind translucent windows? Is it a Compiz plugin, or is it specific to the RGBA GTK PPA? My Compiz Blur Windows plugin seems to blur randomly, w/o respecting its own window-matching rules.
Compiz blur doesnt even work at all for me because of the oss radeon drivers.

---

### Post by zekopeko on 2010-05-17
> **lee.jarratt said:**
> It's pretty readable to me..

[[IMG]http://imgur.com/oxuqo.png[/IMG]](http://imgur.com/oxuqo.png)

Don't cheat :P 

Disable blurring.

---

### Post by go7Ul1ai on 2010-05-17
> **zekopeko said:**
> Don't cheat :P 

Disable blurring.

Disabled blurring but I can still pretty much read the text quite fine.

[IMG]http://imgur.com/Vuf31.png[/IMG]

---

### Post by BobCFC on 2010-05-17
> **lee.jarratt said:**
> Disabled blurring but I can still pretty much read the text quite fine.

[IMG]http://imgur.com/Vuf31.png[/IMG]

That is white text on a dark menu.  Most GTK windows are light colours with black text that turns grey when transparent.  If you have other pages of text underneath it compounds the problem.

Also, the outline of the buttons and other window controls goes faint which is not the desired effect

---

### Post by Mr. Picklesworth on 2010-05-17
> **BobCFC said:**
> That is white text on a dark menu.  Most GTK windows are light colours with black text that turns grey when transparent.  If you have other pages of text underneath it compounds the problem.

Also, the outline of the buttons and other window controls goes faint which is not the desired effect

I don't understand what we're arguing here. That is full transparency of a toplevel window implemented from the window manager specifically. RGBA allows for fine-grained transparency specified from the client up. In the transparent menu example, the background could be semi-transparent but the text could be fully opaque, maybe with an added drop shadow for readability.

It really isn't about that, though. It's about having smooth corners, and widgets that fit together in a kludge-free fashion.

---

### Post by Merk42 on 2010-05-17
> **Mr. Picklesworth said:**
> I don't understand what we're arguing here. That is full transparency of a toplevel window implemented from the window manager specifically. RGBA allows for fine-grained transparency specified from the client up. In the transparent menu example, the background could be semi-transparent but the text could be fully opaque, maybe with an added drop shadow for readability.

It really isn't about that, though. It's about having smooth corners, and widgets that fit together in a kludge-free fashion.
Too bad I feel we'll see more 'designers' focus on the former rather than the latter.

---

### Post by screaminj3sus on 2010-05-17
If 10.10 doesnt ship with anti aliased corners I'll eat my mouse

---

### Post by zekopeko on 2010-05-18
> **screaminj3sus said:**
> If 10.10 doesnt ship with anti aliased corners I'll eat my mouse

I think that is metacity not supporting RGBA.

---

### Post by benjamimgois on 2010-05-18
> **screaminj3sus said:**
> If 10.10 doesnt ship with anti aliased corners I'll eat my mouse


???? 

kkkkk... I'm laughing here. :)

---

### Post by zekopeko on 2010-05-18
> **benjamimgois said:**
> ???? 

kkkkk... I'm laughing here. :)

He's talking about window border corners. They are jagged because there is no alpha transparency.

---

### Post by benjamimgois on 2010-05-18
> **zekopeko said:**
> He's talking about window border corners. They are jagged because there is no alpha transparency.

Yeah, i know. It just sound funny.

---

### Post by screaminj3sus on 2010-05-18
> **zekopeko said:**
> I think that is metacity not supporting RGBA.
Yes which in turn causes the corners to be aliased or "jaggy"

Got a lot of captain obvious in this thread. :)

---

### Post by zekopeko on 2010-05-18
> **screaminj3sus said:**
> Yes which in turn causes the corners to be aliased or "jaggy"

Got a lot of captain obvious in this thread. :)

I meant that metacity HAS to support RGBA for those jaggy corners to disappear. Including RGBA support in GTK+ won't fix that. I suggest you find or file a bug for this in upstream bugzilla and launchpad and link them. I would love to finally have nice AA borders.

---

### Post by vkontakte on 2010-05-18
> **zekopeko said:**
> I meant that metacity HAS to support RGBA for those jaggy corners to disappear. Including RGBA support in GTK+ won't fix that. I suggest you find or file a bug for this in upstream bugzilla and launchpad and link them. I would love to finally have nice AA borders.
and that's why they want to use client side decorations

---

### Post by Speed_arg on 2010-05-18
But thats just for metacity, with compiz we already have all that stuff don't we?

---

### Post by zekopeko on 2010-05-18
> **Speed_arg said:**
> But thats just for metacity, with compiz we already have all that stuff don't we?

No.

---

### Post by Speed_arg on 2010-05-18
> **zekopeko said:**
> No.

And why when dragging windows it looks transparent, and corners look fine?

PD: Will RGBA affect perfonmance? Ubuntu is already pretty slow.

---

### Post by go7Ul1ai on 2010-05-19
> **Speed_arg said:**
> And why when dragging windows it looks transparent, and corners look fine?

PD: Will RGBA affect perfonmance? Ubuntu is already pretty slow.

I tested this technology under a week ago, it certainly affected performance on my machine.

---

### Post by zekopeko on 2010-05-19
> **Speed_arg said:**
> And why when dragging windows it looks transparent, and corners look fine?

PD: Will RGBA affect perfonmance? Ubuntu is already pretty slow.

Because it's cheating. It is making the whole window transparent without regard to the content. Try making your panel transparent and blurred. It won't work as it does in Windows or OSX because it will blur the panel (including text and icons on it) not the background.

Try taking a screenshot of any theme with curved corners and examining it under magnification in GIMP or any other viewer/editor. You will see jagged corners.

---

### Post by BobCFC on 2010-05-19
> **Mr. Picklesworth said:**
> the background could be semi-transparent but the text could be fully opaque, maybe with an added drop shadow for readability


That was my original question :)  I asked if it is possible because every time I have tried it and in every screenshot I have seen the font and outline of the controls go faint


Nothing would make me happier than to have a Gaussian blurred bezel around chromium like chrome does on windows

---

### Post by dxxvi on 2010-08-09
In summary, can we use rgba in maverick? I just want to have the drop down menu transparent (don't need a blur border right now). If the answer is yes, how could I enable it and make the drop down menu transparent?

Thanks.

---

### Post by ranch hand on 2010-08-09
And if we get transparent menus by default how do we disable this redicullus loking piece of eye strain?

---

### Post by go7Ul1ai on 2010-08-10
> **dxxvi said:**
> In summary, can we use rgba in maverick? I just want to have the drop down menu transparent (don't need a blur border right now). If the answer is yes, how could I enable it and make the drop down menu transparent?

Thanks.

I just use Ubuntu Tweak and the Advanced Compiz Settings Manager for that ^_^

---

### Post by Merk42 on 2010-08-10
> **ranch hand said:**
> And if we get transparent menus by default how do we disable this redicullus loking piece of eye strain?I'm going to guess "use a different theme".

---

### Post by autocrosser on 2010-08-11
Or try Fluxbox or one of the alternate window managers....In all reality---the traditional Gnome will be around for the next couple of years or so & I would hope for a gconf key to turn off RGBA---So there "should" be alternatives for some time to come...........

---

