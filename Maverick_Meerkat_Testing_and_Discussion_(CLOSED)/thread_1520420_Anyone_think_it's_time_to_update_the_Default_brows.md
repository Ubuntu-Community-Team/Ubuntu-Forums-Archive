---
title: "Anyone think it's time to update the Default browser links in Firefox"
date: 2010-06-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by philinux on 2010-06-29
[B][COLOR="SeaGreen"][EDIT]
Ok lets forget the Desktop idea and focus on the default livecd and installed browser bookmarks.

Anybody got thoughts on links that should be included.
[/COLOR][/B]

Examples

[http://medibuntu.org/](http://medibuntu.org/)

and

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by taavikko on 2010-06-29
Think that only the restricted one should be mentioned and that could be done in the installer...

---

### Post by 23meg on 2010-06-29
No.

[list][*] Putting stuff on the desktop should generally be avoided; a clean desktop is much more attractive to first time users in that it presents the image of a clean operating environment that isn't filled with unnecessary "stuff" by default, and is worth striving for just for that.


[*] Once you've put links to those documents, you can't justify *not* putting links to other documents regarding other technical basics that are of equal importance. Why not, for example, a link to [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware), or [https://help.ubuntu.com/community/RootSudo?](https://help.ubuntu.com/community/RootSudo?) You can easily fill up a desktop with such helpful links, yet the added benefit would be debatable. Better places to expose users to the basics of how the system works and documentation are the browser start page, and the installation slideshow.


[*] Directing people who aren't normally inclined to read documentation in order to reach their goals in daily computing to doing so is usually not a good way to help them. The most common use cases for restricted formats are covered by the codec auto-installer, and if there are important ones that are missing, the way to fix that is to *actually fix it*, to the extent allowed by legal restrictions. 
[/list]

---

### Post by abdulapopoola on 2010-06-29
Yes, I do think so too, there should be two browsers.

---

### Post by philinux on 2010-06-29
@23meg,

Thanks for reply. How about the same links mentioned in the installer slideshow.

 We get a lot of recurring threads based on these.

---

### Post by cariboo on 2010-06-29
I too agree with 23meg, back when the examples folder was on the desktop, it was one of the first things to remove. I still like a clean desktop, with the only things on it being drive icons.

---

### Post by zekopeko on 2010-06-29
> **philinux said:**
> @23meg,

Thanks for reply. How about the same links mentioned in the installer slideshow.

 We get a lot of recurring threads based on these.

The new installer will have the option of installing non-free software by default (I think it would apt-get restricted-extras, maybe even DVD support).

I haven't used a completely fresh install for a while now so I'm wondering what is the problem with the restricted formats. I remember there being a dialog asking you to install codec if you needed them to play the file.

---

### Post by ronacc on 2010-06-29
how about 2 bookmarks in the default browser .

---

### Post by zekopeko on 2010-06-29
> **ronacc said:**
> how about 2 bookmarks in the default browser .

To those two pages as they are now? God no! They are technical and involve the terminal.

I still fail to see where exactly is the problem. You should get the dialog to install the codec if you need them.

---

### Post by mc4man on 2010-06-29
> 
I still fail to see where exactly is the problem. You should get the dialog to install the codec if you need them. 

There really isn't that much of an issue, the codec install takes care of the basic gstreamer plugins quite well (bad, ugly, ffmpeg ) for decoding.

From an encoding side (gstreamer), it's up to the user to add the multiverse plugins, I don't believe the installer deals with that.

Small repetitive issues with no prompts are libdvdcss2 and aac encoding.

While a script is included in libdvdread  to dl and install libdvdss2 from medibuntu, it's existence is far from obvious. (installed w/ bad plugin)

aac encoding (faac), has been removed from ubuntu - medibuntu provides that with it's extra builds of the ffmpeg libs.

xine engine apps tend not to prompt properly to install libxine1-ffmpeg so that's also left up to the user to figure out

I'm not sure if the totem-mozila plugin is installed by default - if not it probably should be.

For flash there is no prompt but most people figure out to go to adobe and install the plugin based on website prompt and link

---

### Post by castrojo on 2010-06-29
> **zekopeko said:**
> The new installer will have the option of installing non-free software by default (I think it would apt-get restricted-extras, maybe even DVD support).


Spec for that is here: 
[https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-installer-redesign](https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-installer-redesign)

---

### Post by dagrump on 2010-06-29
I really hate icons on the desktop, & remove everything I can. I unmount extra drives just so they don't clutter the desktop, as soon as I get done with them.
Add bookmarks in the browser if they feel it's needed, but don't add cruft to a nice clean desktop, let the user clutter it up with garbage they want.
Oh, why are we supposed not let the noobs be exposed to the terminal again, sorry I just keep forgetting the reasoning. It's the fastest way to do some things & doesn't care what DE you're using.

---

### Post by mc4man on 2010-06-29
> Spec for that 

multimedia wise is going to use u-r-e (or k,l,x), which is fine. Atm u-r-e has been pared down a bit since karmic where it remains mis-configured, so it should work ok.

The only possible issue with using u-r-e is it sometimes fails on the ttf-mscorefonts-installer which isn't a good thing..

---

### Post by castrojo on 2010-06-29
> **mc4man said:**
> The only possible issue with using u-r-e is it sometimes fails on the ttf-mscorefonts-installer which isn't a good thing..

I wonder why we don't use ttf-liberation in place of the MS fonts, there's probably a bug about that somewhere...

---

### Post by mc4man on 2010-06-29
> I wonder why we don't use ttf-liberation in place of the MS fonts

I believe ttf-liberation is installed by default but have to admit I pay no att. at all in this area. (and sometimes install the MS fonts, sometimes don't, oblivious in either case.

As far as the error installing it seems to be a corner case thing, only happens to some once and a while 
So while there are numerous bug reports, most languish or get [lumped into here ]("https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/349469")

But just the possibility has prevented me from ever suggesting u-r-e when a few simple commands will suffice.

I wouldn't consider it being removed from u-r-e the worst thing..


( as far as web fonts this seemed [a decent suggestion]("https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/409101") that went nowhere - maybe rightly so, maybe not

Edit: if it's true that the msfonts 'override' the the ttf-liberation ones then consideration should be given to not using the msfonts installer in u-r-e (don't know here

---

### Post by philinux on 2010-06-30
> **ronacc said:**
> how about 2 bookmarks in the default browser .

+1 better than on Desktop then from posts made so far. Maybe the pages need improving.

A link to these forums would be nice in the browser.

---

### Post by philinux on 2010-06-30
> **zekopeko said:**
> To those two pages as they are now? God no! They are technical and involve the terminal.

I still fail to see where exactly is the problem. You should get the dialog to install the codec if you need them.

Installing a brand new OS is technical to start with.

I'm not trying to start a heated debate here. Just thinking about how we help newbies.

I've just been into the live cd and the default bookmarks could really do with a makeover.
Including a link to these forums would be a step forward.

[edit]
The current bookmarks for ubuntu are.
1. ubuntulinux.org
2. ubuntulinux.org/wiki/frontpage
3. answers.launchpad
4. debian.org

---

### Post by ronacc on 2010-06-30
> **zekopeko said:**
> To those two pages as they are now? God no! They are technical and involve the terminal.

I still fail to see where exactly is the problem. You should get the dialog to install the codec if you need them.

have we sunk to the point that even a bookmark in a browser that points at a page that mentions the terminal will drive off prospective users ? If that is the case , then we might as well give up now because we are doomed .

---

### Post by ranch hand on 2010-06-30
> **ronacc said:**
> have we sunk to the point that even a bookmark in a browser that points at a page that mentions the terminal will drive off prospective users ? If that is the case , then we might as well give up now because we are doomed .
I think the terminal thing is over blown.  I started with MSDOS and though that one of the bad things on W98 was the more hidden CLI.

One of the main things that got me to switch was the handy terminal in Linux.  I am really a gui user for the most part.  Prefer it.   There are just some things that are too handy and too fast in the CLI not to just love it.

We need, in my opinion, to push the strengths of Linux in general, and Ubuntu in particular, not the ability to be a free copy of crappy MS OS'.  The terminal is one of the main strengths as it makes it possible  to do things fast and easy with just a few commands needing to be learned.

If folks are to simple to learn a few commands they probably should not be running any OS or, for that matter, a toaster.

---

### Post by LiquidMeson on 2010-06-30
"a toaster"
what about chrome os?

---

### Post by ronacc on 2010-06-30
> **LiquidMeson said:**
> "a toaster"
what about chrome os?

I believe you misunderstood , I think he was implying that anyone that could not master a few simple cmds , wouldn't be able to operate complex things like wheelbarrows and shovels .

---

### Post by ranch hand on 2010-06-30
> **ronacc said:**
> I believe you misunderstood , I think he was implying that anyone that could not master a few simple cmds , wouldn't be able to operate complex things like wheelbarrows and shovels .
Couldn't have said it better.

Heck, if it were hard I sure couldn't do it.

---

### Post by fedexnman on 2010-06-30
i think a 1 page only quick start guide on the desktop  would do the trick, including, 1. ubuntu restricted extras, and 2. dvd playback instructions (medibuntu) :confused:

---

### Post by zekopeko on 2010-06-30
> **ronacc said:**
> have we sunk to the point that even a bookmark in a browser that points at a page that mentions the terminal will drive off prospective users ? If that is the case , then we might as well give up now because we are doomed .

Having bookmarks to pages that aren't really designed for your average computer user is a bad idea. I expect simpler instructions then cryptic commands.

> **ranch hand said:**
> I think the terminal thing is over blown.  I started with MSDOS and though that one of the bad things on W98 was the more hidden CLI.

One of the main things that got me to switch was the handy terminal in Linux.  I am really a gui user for the most part.  Prefer it.   There are just some things that are too handy and too fast in the CLI not to just love it.

The majority of user shouldn't need to input commands into a terminal to be able to play a movie. If you need them to do that then something is seriously lacking in the OS.

> We need, in my opinion, to push the strengths of Linux in general, and Ubuntu in particular, not the ability to be a free copy of crappy MS OS'.  The terminal is one of the main strengths as it makes it possible  to do things fast and easy with just a few commands needing to be learned.

The command line isn't a strength that your average computer user wants or needs. If I need the command line to get a video file to play your OS suck. I expect the computer to do and suggest things I can do. Hunting commands to play a movie isn't what is expected in the 21st century.

> If folks are to simple to learn a few commands they probably should not be running any OS or, for that matter, a toaster.

This reeks of elitism that was always the bane of the Linux community.

---

### Post by ronacc on 2010-06-30
I obviously have a higher opinion of my fellow man (person for the politically correct ) man than you do .

---

### Post by zekopeko on 2010-06-30
> **philinux said:**
> Installing a brand new OS is technical to start with.

If you make it easy and bulletproof it shouldn't be more complex then installing an app.

> I'm not trying to start a heated debate here. Just thinking about how we help newbies.

The problem is that when people usually do that they go for the easiest path. Next thing you know you have 10 links on the desktop for problems that should have been fixed differently. This is one such problem. The computer should direct the user to the codecs when they want to play the movie not pester their nice looking desktop with cruft.

The easiest way is to show the user a nicely designed dialog when they want to play a movie/song and give them simple options: "To play this file Ubuntu needs to install some extra software. Would you like to install extra software?" [Install][Cancel].

End of story. It show only when it's needed unlike the link that are always on the desktop. "But you can delete them!". What happens if the user isn't sure if they will need that info later and they simply leave them there because they don't know if the info is going to be available if they delete it?

> I've just been into the live cd and the default bookmarks could really do with a makeover.
Including a link to these forums would be a step forward.

[edit]
The current bookmarks for ubuntu are.
1. ubuntulinux.org
2. ubuntulinux.org/wiki/frontpage
3. answers.launchpad
4. debian.org

The bookmarks should certainly be refreshed. File a bug. One entry point is the start page which already has links to various resources.

---

### Post by zekopeko on 2010-06-30
> **ronacc said:**
> I obviously have a higher opinion of my fellow man (person for the politically correct ) man than you do .

And I value the time of my fellow man. Computer are tools for most people. Forcing them to read a bunch of manual that is only tangentially related to what they want to do is ridiculous.

Please stop implying that I think the majority of people are stupid. Just because the majority of us don't want to spend 6 hours reading manuals before using our products doesn't make us stupid. It just makes the product badly designed.

---

### Post by philinux on 2010-06-30
Ok lets forget the Desktop idea and focus on the default livecd and installed browser bookmarks.

Anybody got thoughts on links. Also what the heck package do I bug. Firefox ubiquity or what?

And substitute new convert from another OS for newbie.

---

### Post by 23meg on 2010-06-30
> **philinux said:**
> Ok lets forget the Desktop idea and focus on the default livecd and installed browser bookmarks.

Anybody got thoughts on links. Also what the heck package do I bug. Firefox ubiquity or what?

A bug report isn't a good way to bring this up; better places to go would be the ayatana or ubuntu-devel-discuss mailing lists. Remember to do a few searches; I recall this coming up not long ago.

---

### Post by philinux on 2010-06-30
Ok Murat I'll do some digging. Cheers.

---

### Post by ronacc on 2010-06-30
> **zekopeko said:**
> And I value the time of my fellow man. Computer are tools for most people. Forcing them to read a bunch of manual that is only tangentially related to what they want to do is ridiculous.

Please stop implying that I think the majority of people are stupid. Just because the majority of us don't want to spend 6 hours reading manuals before using our products doesn't make us stupid. It just makes the product badly designed.

How are a couple of links in the bookmarks of the default browser going to FORCE anyone to "spend 6 hours " reading something that they are not interested in ? I happen to think that the "average" user is smart enough to decide whether they wish to continue reading in something more like 6 seconds . Or do you contend that having followed the link to a page they are slavishly compelled to purse it to the bitter end . 

I am not implying anything about what you think of the majority of users , you make that plain with every post .

---

### Post by mc4man on 2010-06-30
Don't quite get what the issue is here on either side of the coin.
Most users are only concerned about decoding which is handled quite well for the most part by the codec installer. (and with advances in gstreamer and ffmpeg covers most common types.

Internet wise there are prompts that are fairly obvious, if not the user can find the info quite easily.

The only obscure common thing is encrypted dvd playback and the ubuntu  help contains all the needed info.

There is no great need for medibuntu, though it could be mentioned in the help page(s) as could a line or 2 about flash, ect.

---

### Post by zekopeko on 2010-06-30
> **ronacc said:**
> How are a couple of links in the bookmarks of the default browser going to FORCE anyone to "spend 6 hours " reading something that they are not interested in ? I happen to think that the "average" user is smart enough to decide whether they wish to continue reading in something more like 6 seconds . Or do you contend that having followed the link to a page they are slavishly compelled to purse it to the bitter end .

Please explain to me WHY are those bookmarks needed? All of the scenarios should be covered with the codec installer. Adding two completely unneeded bookmarks just clutters the UI (not that the currennt bookmarks shouldn't be refreshed with something new and nice).

> I am not implying anything about what you think of the majority of users , you make that plain with every post .

And what do I think about the majority of users in your opinion?

---

### Post by VMC on 2010-06-30
This is one of those threads where someone has to get the last word in regardless. Too much bickering...


I understand philinux concerns, and I think the suggestion about adding a browser link would be the best solution. And besides, if someone is not familiar with using the terminal, then will just pass over any reference to it.

---

### Post by ronacc on 2010-06-30
> **zekopeko said:**
> Please explain to me WHY are those bookmarks needed? All of the scenarios should be covered with the codec installer. Adding two completely unneeded bookmarks just clutters the UI (not that the currennt bookmarks shouldn't be refreshed with something new and nice).



And what do I think about the majority of users in your opinion?

I hardly think that 2 bookmarks in the bookmarks folder of the default browser ( note that I say in the browser not on the desktop as suggested by the OP .)is cluttering up the UI , since most people rapidly collect several hundred of their own , 2 more is paltry clutter and easily deleted if the user finds them too offensive. As to why those 2 ,the one to one of  Ubuntus own help pages is merely a convenience to save having to wade through the help menu , and the one to medibuntu is needed for more than codecs ( think googleearth among other things ) .

Since I am not inside your skull I cannot say for certain what you think ,but you convey the impression that you believe that the majority of users either 

A: live in mortal fear of having to type something on the cmd line .

or 

B: are too inept to do so if A does not apply .

---

### Post by ronacc on 2010-06-30
> **philinux said:**
> Ok lets forget the Desktop idea and focus on the default livecd and installed browser bookmarks.

Anybody got thoughts on links. Also what the heck package do I bug. Firefox ubiquity or what?

And substitute new convert from another OS for newbie.


sorry to have participated in hijacking your thread , here are a couple of links that people may find handy . maybe instead of a bug report a brainstorm might be a better place for this idea . And maybe collect useful links into their own folder within the bookmarks folder ( call it handy links or whatever ).

[http://gnome-look.org/](http://gnome-look.org/)

[http://kde-look.org/](http://kde-look.org/)

---

### Post by LiquidMeson on 2010-06-30
"The easiest way is to show the user a nicely designed dialog when they want to play a movie/song and give them simple options: "To play this file Ubuntu needs to install some extra software. Would you like to install extra software?" [Install][Cancel]."
-isn't this already in ubuntu?

Concerning the live cd, most people imo wouldn't care about it until they go to play the file.

As long as installing codecs requires any human interaction this will be a problem. Simplest is to push webm and ogg. Concerning audio tho, aren't there opensource mp3 encoders and decoders that could be included by default?

---

### Post by zekopeko on 2010-06-30
> **LiquidMeson said:**
> "The easiest way is to show the user a nicely designed dialog when they want to play a movie/song and give them simple options: "To play this file Ubuntu needs to install some extra software. Would you like to install extra software?" [Install][Cancel]."
-isn't this already in ubuntu?

Yes, but it is cumbersome (at least the last time I saw the dialog). Instead of offering one dialog that would pop-up the password dialog for installation it instead searches for codecs and then offers cryptic names such as gstreamer-plugins-bad/ugly etc. Don't we have mime-types and other methods to see which codecs are needed and simply install them? It also doesn't support DVD playback. You have to go to the terminal for that one.

> Concerning the live cd, most people imo wouldn't care about it until they go to play the file.

As long as installing codecs requires any human interaction this will be a problem. Simplest is to push webm and ogg. Concerning audio tho, aren't there opensource mp3 encoders and decoders that could be included by default?

I think that mp3 can't be installed by default because of patents. You can install it for personal use though. So it needs to be installed by the user.

---

### Post by LiquidMeson on 2010-06-30
"I think that mp3 can't be installed by default because of patents. You can install it for personal use though. So it needs to be installed by the user."

Can't be included? or can't be installed? Because technically the user is installing the os? I'd say find a loop hole to get it installed with the system.

---

### Post by arpanaut on 2010-06-30
@LiquidMeson  Read the first paragraph in the link below, It's an ethical, moral and legal decision by Ubuntu not to distribute non-free patent encumbered software.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Ibidem on 2010-06-30
And Medibuntu has stuff that might get Canonical in trouble just for mentioning it.  Encrypted dvd support and the like may be considered illegal in some areas (yes, I am referring to the US policies).
Medibuntu is stuff that cannot be distributed in multiverse; mp3 support is multiverse.

But really, the Puppy start page seems like a good example (don't have a link handy, I'm in Lucid Lynx not Lucid Puppy).

Google Earth? There's a package (in the repos, I believe) to make that into a deb, automatically.  That's what I used.

Scripts/commands can always be given GUIs, it's not that complex (refer to: whiptail, zenity, kdialog, wish, pygtk, xmessage etc.); if you have a script + GUI where they can download, rightclick/properties/make executable, run, O.K. & give password, that shouldn't be too hard.

Sample script w/gui (won't run just yet, it needs the variables defined):
```
#!/bin/bash
xmessage -buttons "All","Only multiverse","Cancel" \
"                                                       Would you like to install additional codecs?\n \
Some codecs (multiverse) are subject to patent restrictions that obstruct inclusion in the primary repository,\n \
                                     while others have licensing that may make them illegal in certain areas \n\
                                                     or otherwise prevent any official redistribution.\n\
                 You will need to provide your password for installation to proceed."
VAL=$?
if [ $VAL -eq 103 ]; then exit 1; fi
if [ $VAL -eq 1 ]; then exit 2; fi
if [ $VAL -eq 101 ]; then gksu apt-add-repository $MEDIBUNTU; gksu apt-get update; gksu apt-get install $MEDI_PACKAGES; VAL=102; fi
if [ $VAL -eq 101 ]; then gksu apt-add-repository $multiverse; gksu apt-get update;gksu apt-get install $MULTIVERSE_PACKAGES; fi
exit 0
```

---

### Post by LiquidMeson on 2010-07-01
putting video codecs aside, I'd like to say a large portion of people use mp3 cus it works with their apple products, right? Hdd space for the most part is a non issue so maybe "Apple Lossless" could be pushed as a default? in the music store etc.

Edit: android phones also support it with Andless

---

### Post by ranch hand on 2010-07-01
> **zekopeko said:**
> Having bookmarks to pages that aren't really designed for your average computer user is a bad idea. I expect simpler instructions then cryptic commands.



The majority of user shouldn't need to input commands into a terminal to be able to play a movie. If you need them to do that then something is seriously lacking in the OS.



The command line isn't a strength that your average computer user wants or needs. If I need the command line to get a video file to play your OS suck. I expect the computer to do and suggest things I can do. Hunting commands to play a movie isn't what is expected in the 21st century.



This reeks of elitism that was always the bane of the Linux community.
I have not replied to this as I have been busy with other things.  Severe Weather Warning, power outage, loss of internet.  All while trying to do ISO testing.  FUN

I am, or was a short time ago, the average user switching from MS to Linux.  I did not change because I am too cheap to pay for an OS.  I did not change to be cool.  I changed because I wanted something different.

I was fed up with an inferior product.  Inferior to what?  Inferior to my expectations.

Now I here that I  am being elitist because I think people make a choice to switch because they have considered the options and chosen the one that is best for them.

The elitism that I am becoming tired of is the MS elitism seen in these forums.  Ubuntu should do this or that because MS does.  Why?  So that we can have a Linux distr othat is as crappy as MS?

No, it is because folks switch and then want the new OS to be the same as the old OS.  Yes I would say that is elitism.  I would also say it is damned silly.

There is a real easy way to have things that way.  Use an MS OS.  Simple as that.

Now, let us consider another case.  I bought my wife, who is no geek and has no interest in the guts of her OS, a Sys76 laptop wit h9.10 preinstalled on it.  Se has had it for about 6 months and loves it.

I just got done asking her a few questions.

She has never opened the terminal.

She has, of her own free will read the documentation on some accounting program that the Sys76 folks appear to have installed.  I do not even know the name of it.  She runs her business with it.

When we used MS OS' we had to read pages of help files and other documentation for every program we used.  I see no difference, and more importantly my wife sees no difference, in the use of the OS re documentation.

Us elitists that use a computer as a tool not a play toy with eye candy and games just want it to work.  It does not have to work like some other OS at all.  We can learn something new.

Some of us even enjoy the process in spite of being older users.  I think some of you youngsters need to find out that different is not all that bad.  Now there is an elitist statement from a grumpy geezer.  I can now claim to be a member of the geezer elite.

---

### Post by ranch hand on 2010-07-01
> **LiquidMeson said:**
> putting video codecs aside, I'd like to say a large portion of people use mp3 cus it works with their apple products, right? Hdd space for the most part is a non issue so maybe "Apple Lossless" could be pushed as a default? in the music store etc.

Edit: android phones also support it with Andless
You also have to remember that Canonical has an agreement with Debian t ogo by their phylosophy of OSS.  There are some things, like ethics, that can not be decided on by lawyers and ploliticians.

There is also the fact that some of the things offered by medibuntu is out and out illegal in some countries.  This is a world wide distro.  Not just in one or two countries or regions and certainly not in one or two political systems.

Between the ethics and the varying laws this is a very complex issue that I think Ubuntu does a good job of dealing with.  It is certainly better than a lot of other Linux distros that I have tried.

Speaking of other ways to deal with the restricted stuff.  Long live the Penguin Liberation Front.

---

### Post by LiquidMeson on 2010-07-01
Apple Losses has been reverse engineered as open source.
[http://en.wikipedia.org/wiki/Alac](http://en.wikipedia.org/wiki/Alac)
It is included in the libavcodec
[http://en.wikipedia.org/wiki/Libavcodec](http://en.wikipedia.org/wiki/Libavcodec)

Why not push this codec? This would support apple devices and android phones alike! Plus its lossless.

Edit: It may not be the preferred codec, but its better quality then mp3, open source, and works.

Edit2: In other news, [http://www.wired.com/wiredscience/2010/06/early-multicellularity/](http://www.wired.com/wiredscience/2010/06/early-multicellularity/)

---

### Post by ranch hand on 2010-07-01
> **LiquidMeson said:**
> Apple Losses has been reverse engineered as open source.
[http://en.wikipedia.org/wiki/Alac](http://en.wikipedia.org/wiki/Alac)
It is included in the libavcodec
[http://en.wikipedia.org/wiki/Libavcodec](http://en.wikipedia.org/wiki/Libavcodec)

Why not push this codec? This would support apple devices and android phones alike! Plus its lossless.

Edit: It may not be the preferred codec, but its better quality then mp3, open source, and works.

Edit2: In other news, [http://www.wired.com/wiredscience/2010/06/early-multicellularity/](http://www.wired.com/wiredscience/2010/06/early-multicellularity/)
All I can say is that Edit2 is just one of the neatest things I have read for some time.  Wow.

Thanks.

---

### Post by philinux on 2010-07-01
After chatting to the mozilla team I'm closing this thread and starting afresh. Cheers for contributions.

---

