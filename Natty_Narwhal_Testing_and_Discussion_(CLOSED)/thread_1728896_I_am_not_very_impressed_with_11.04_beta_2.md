---
title: "I am not very impressed with 11.04 beta 2"
date: 2011-04-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by irv on 2011-04-14
I know this will be the last beta before the final release of 11.04.
First: I downloaded the beta 2 release this morning, I have tried beta 1 and some of the earlier releases but I have to be honest with you I am not impressed with this release and here is why.

I feel I have lost control of quick changes. Take for example the panel. I have two of them in 10.10, and I have them setup to do different things. The top panel is for Applications and things I have running at boot up. The bottom panel is for running apps, and quick start apps. Also I have my workspace switching and the daily temp indicator.

With the new release I lose all of this. I know that it is new, and one must get use to it but I really like Gnome just the way it is.

Second thing: In every other release of Ubuntu I was able to boot with the live OS and setup my wireless card by installing the driver from the additional driver utility. In this release I can do the same, but it tell me I need to restart to activate it. When you do this in the live OS you lose the driver you just installed, so it make it impossible to test the live OS off a USB stick or CD and be able to be on a Network. Yes, I can plug in the wire and get on but there is no way to use my wireless.

I have made up my mind, I am going to stay with 10.04 on my server and 10.10 on my laptop, and when these releases die off I will be looking for other distros, unless I see some other DE that appeals to me.
By the way I do not like KDE, and I find XFce somewhat useful but not like Gnome. Gnome 2.35.0 is very nice to use and it is going to be hard to leave it.

Thanks for hearing me out.

---

### Post by nothingspecial on 2011-04-14
Irv, I felt just like you.

Thing is gnome is moving to gnome3 which is similar to the new Ubuntu unity interface and are going to stop working on it. So you're a little stuck whatever you do.

xfce4.8 has really come on, give it a look.

I am _**slowly**_ warming to gnome-shell.

---

### Post by kansasnoob on 2011-04-14
Are you aware that you can switch to either the Classic or Classic w/o effects desktop at login?

Also I made some rather sloppy notes about other things in Natty in posts #1 and #2 here:

[http://ubuntuforums.org/showthread.php?t=1718631](http://ubuntuforums.org/showthread.php?t=1718631)

---

### Post by sgage on 2011-04-14
> **nothingspecial said:**
> Thing is gnome is moving to gnome3 which is similar to the new Ubuntu unity interface and are going to stop working on it. So you're a little stuck whatever you do.

Does anyone know definitively what the Gnome people have planned for "panels". I've read a lot of different statements on this.

I saw a posting in some dev list a couple of weeks ago that seemed to indicate that the panels were going to be rewritten for Gnome 3 and maintained for some indeterminate time. I.e., you could run the Gnome 3 stack and still have panels.

I've also heard that they're ditching the panels altogether after another cycle. 

Does anyone know?

Meanwhile, I'm trying to work with Unity, but I have the "Classic" panel-y interface to fall back on, at least until Oneiric.

I have tried XFCE recently, and it still doesn't do it for me. As far as KDE goes, I've tried very hard to get into it over the months and years, but it always leaves me cold. I prefer Unity to KDE.

I've played with Gnome Shell quite a bit over the last few months, compiling it myself on a Lucid system. I'm not sure it's any better than Unity, but they're both moving targets, so we'll see...

---

### Post by mc4man on 2011-04-14
> Second thing: In every other release of Ubuntu I was able to boot with the live OS and setup my wireless card by installing the driver from the additional driver utility. In this release I can do the same, but it tell me I need to restart to activate it. When you do this in the live OS you lose the driver you just installed, so it make it impossible to test the live OS off a USB stick or CD and be able to be on a Network. Yes, I can plug in the wire and get on but there is no way to use my wireless.

You may or may not (my wireless works fine OOTB) be able to test on live cd by doing a logout/in after installing the drivers (login ubuntu, no password

It does work with the nouveau 3d drivers, so maybe it will with  wireless drivers also

---

### Post by kansasnoob on 2011-04-14
> **sgage said:**
> **[COLOR="Red"]Does anyone know definitively what the Gnome people have planned for "panels". [/COLOR]**I've read a lot of different statements on this.

I saw a posting in some dev list a couple of weeks ago that seemed to indicate that the panels were going to be rewritten for Gnome 3 and maintained for some indeterminate time. I.e., you could run the Gnome 3 stack and still have panels.

I've also heard that they're ditching the panels altogether after another cycle. 

Does anyone know?

Meanwhile, I'm trying to work with Unity, but I have the "Classic" panel-y interface to fall back on, at least until Oneiric.

I have tried XFCE recently, and it still doesn't do it for me. As far as KDE goes, I've tried very hard to get into it over the months and years, but it always leaves me cold. I prefer Unity to KDE.

I've played with Gnome Shell quite a bit over the last few months, compiling it myself on a Lucid system. I'm not sure it's any better than Unity, but they're both moving targets, so we'll see...

Not definitively, no, but this comes from the Gnome folks themselves:

[http://live.gnome.org/GNOME3Myths#GNOME_won.27t_support_the_current_panel_and_window_manager_anymore](http://live.gnome.org/GNOME3Myths#GNOME_won.27t_support_the_current_panel_and_window_manager_anymore)


> While it is true that the GNOME 3 experience will not include the panel as it was in GNOME 2, the window manager used in GNOME 3 will use a window manager that behaves consistently with the GNOME 2 window manager (metacity). This is because it uses most of the same code.

It is important to emphasize that **GNOME 2 technologies will still be available through the usual channels [COLOR="Red"]for some time[/COLOR].**

**Downstream distributions such as** Fedora, openSUSE and **Ubuntu will have the option to include them in their distribution. **

Some of us were concerned enough about how Unity would play into this we began the UGR project:

[http://ugr.teampr0xy.net/](http://ugr.teampr0xy.net/)

It's in it's infancy so **[COLOR="Red"]only advanced testers should participate ATM[/COLOR]**, but I doubt the gnome-panel technology will die altogether any time soon.

---

### Post by hexion on 2011-04-14
I feel like the submitter.

I have given Unity a try. I didn't like it. Then another try... still the same. After several attempts I just decided it is not for me. I can live with bugs (specially in not finished products), but in this case it's the design that I don't like.

Gnome-shell, although more useful and polished than Unity, doesn't appeal me either. And given the direction it took I don't think it will be looking better to me in newer releases.

I have been playing around with XFCE+Compiz and it _could_ be a possible solution for me, but I would need to solve a good deal of glitches first.


As a consequence, it looks like I'll be switching to either Xubuntu if I can get used to XFCE, or otherwise I'll switch to another distro. Even if that's what will finally happen, I really enjoyed using Ubuntu for so many years so no bad feelings ;)

---

### Post by kansasnoob on 2011-04-14
> **hexion said:**
> I feel like the submitter.

I have given Unity a try. I didn't like it. Then another try... still the same. After several attempts I just decided it is not for me. I can live with bugs (specially in not finished products), but in this case it's the design that I don't like.

Gnome-shell, although more useful and polished than Unity, doesn't appeal me either. And given the direction it took I don't think it will be looking better to me in newer releases.

I have been playing around with XFCE+Compiz and it _could_ be a possible solution for me, but I would need to solve a good deal of glitches first.


As a consequence, it looks like I'll be switching to either Xubuntu if I can get used to XFCE, or otherwise I'll switch to another distro. Even if that's what will finally happen, I really enjoyed using Ubuntu for so many years so no bad feelings ;)

Did you read my post #3?

You can still get the true "classic" Gnome look and feel in Natty!

Oneiric is not here yet so we'll have to wait and see, but my bet is that we'll be able to get real close to a "classic" look and feel with Gnome3 in Ubuntu.

Where there's a will, there's a way :D

---

### Post by sgage on 2011-04-14
> **kansasnoob said:**
> Not definitively, no, but this comes from the Gnome folks themselves:

[http://live.gnome.org/GNOME3Myths#GNOME_won.27t_support_the_current_panel_and_window_manager_anymore](http://live.gnome.org/GNOME3Myths#GNOME_won.27t_support_the_current_panel_and_window_manager_anymore)




Some of us were concerned enough about how Unity would play into this we began the UGR project:

[http://ugr.teampr0xy.net/](http://ugr.teampr0xy.net/)

It's in it's infancy so **[COLOR="Red"]only advanced testers should participate ATM[/COLOR]**, but I doubt the gnome-panel technology will die altogether any time soon.

Still pretty vague. As I wrote above, I have been playing with Gnome Shell all along, compiling it weekly to see how it's coming. But I think what I'm going to do is wait until the UGR project has an iso available. Until then, and through the final release of Natty, I'm going to try to stick with Unity, knowing that I have panel-y goodness to fall back on. For now.

We live in interesting times :KS

---

### Post by kansasnoob on 2011-04-14
> **sgage said:**
> **[COLOR="Red"]Still pretty vague[/COLOR]**. As I wrote above, I have been playing with Gnome Shell all along, compiling it weekly to see how it's coming. But I think what I'm going to do is wait until the UGR project has an iso available. Until then, and through the final release of Natty, I'm going to try to stick with Unity, knowing that I have panel-y goodness to fall back on. For now.

We live in interesting times :KS

How are we vague?

Did you read the "visions" page:

[http://ugr.teampr0xy.net/vision](http://ugr.teampr0xy.net/vision)

> The Ubuntu Gnome Remix will be a mix of the best of GNOME and Ubuntu. It's GNOME and open source roots will be very apparent.

**Compatability for** both **classic GNOME** (what Ubuntu has used for years) and GNOME3 (a brand new interface that is made of awesome) **will be maintained.**

One day, we hope this will become an official Ubuntu distribution

How well we manage to carry through with that depends on the level of participation by developers, testers, etc :D

EDIT: I deliberately left out the bit about going for the name "Gubuntu" so early in the game. I was not consulted and I think that was premature. I'm old enough to know that overreach can kill a project before it even gets out of the chute. I certainly hope that will not be the case here.

---

### Post by cariboo on 2011-04-14
Here's a link to a blog post from the gnome panel developer, about the changes he has made to align them with the way they look in gnome-shell:

[http://www.vuntz.net/journal/post/2011/04/13/gnome-panel-is-dead%2C-long-live-gnome-panel%21](http://www.vuntz.net/journal/post/2011/04/13/gnome-panel-is-dead%2C-long-live-gnome-panel%21)

---

### Post by irv on 2011-04-14
> **mc4man said:**
> You may or may not (my wireless works fine OOTB) be able to test on live cd by doing a logout/in after installing the drivers (login ubuntu, no password

It does work with the nouveau 3d drivers, so maybe it will with  wireless drivers also

I tried this and it still tells me I need to reboot to activate. I am using a Broadcom STA wireless dirver on my Dell Inspiron laptop and it works great. In 10.10 was able to install it with the live OS but not so in 11.04. I don't know what they changed but it was not a good change.

---

### Post by sgage on 2011-04-14
> **kansasnoob said:**
> How are we vague?

Only in the sense that it's not clear what the plan is for panels.

I'm all for the remix project, and like I said, will be checking it out when an iso is ready.

I think one thing that is critically important is to make the distinction between "Gnome 3" and "Gnome Shell". On the various threads regarding these issues in the forum there is a very confusing conflation of the two.

Gnome 3, and Gnome 2 before it, are software stacks that allow various GUI shells to be presented. The panels, and now Gnome Shell, are two such shells. So is Unity. To be sure, the "official" shell for Gnome 3 is Gnome Shell, in the same way that the "official" shell for Gnome 2 was the Panels.

As of now, I think most people think that Gnome Shell IS Gnome 3 and vice-versa.

---

### Post by mc4man on 2011-04-14
> **irv said:**
> I tried this and it still tells me I need to reboot to activate. I am using a Broadcom STA wireless dirver on my Dell Inspiron laptop and it works great. In 10.10 was able to install it with the live OS but not so in 11.04. I don't know what they changed but it was not a good change.

That is unfortunate, if one of the purposes of "try me" is to ck . hardware compatibility then newly installled drivers should be able to be loaded.
In the case of the nouveau 3d the restart notifier will stay active(red), but the drivers are loaded

While I haven't ck.ed in a while nvidia-current couldn't be used on the live-cd either  thru a logout/in when in the past they could.
*though in this case the past may have been karmic or lucid, I forget

---

### Post by irv on 2011-04-14
> **mc4man said:**
> That is unfortunate, if one of the purposes of "try me" is to ck . hardware compatibility then newly installled drivers should be able to be loaded.
In the case of the nouveau 3d the restart notifier will stay active(red), but the drivers are loaded

While I haven't ck.ed in a while nvidia-current couldn't be used on the live-cd either  thru a logout/in when in the past they could.
*though in this case the past may have been karmic or lucid, I forget
I am thinking that the wireless driver will work with 11.04 on finial install, but you are right, there is no way to tell if the hardware will work without trying it before installing. What ever changed it needs to be fixed not only in this release but in the future.

---

### Post by beew on 2011-04-14
> **mc4man said:**
> That is unfortunate, if one of the purposes of "try me" is to ck . hardware compatibility then newly installled drivers should be able to be loaded.
In the case of the nouveau 3d the restart notifier will stay active(red), but the drivers are loaded

While I haven't ck.ed in a while nvidia-current couldn't be used on the live-cd either  thru a logout/in when in the past they could.
*though in this case the past may have been karmic or lucid, I forget

I have never been able to install proprietary graphic card with live usb (10.04 and 10.10) Everytime I tried it broke the live usb. I was led to believe that live usb doesn't support installation of proprietary graphic driver, but are you saying that it does support it?

I have had no problem with installing WIFI drivers though. Don't remember whether I need to reboot (since I did that only once or twice, most time WIFI works out of the box so there is no need to install anything) But if I use my small dell netbook for testing I need to reboot anyway since the internal WIFI card is not working (neither in Windows nor Linux) and I have to use a usb wifi card, which would not work unless I blacklist the driver for the internal card and reboot first.  

Live usb with persistence should solve the OP's problem.

I don't test with live usb anymore, nowadays I prefer to test with a full install in an external drive.

P.S. Will try your advice for installing emerald again tonight when I go home. Thanks

---

### Post by cariboo on 2011-04-14
You don't have to do a restart if you install the STA driver, just make sure the wl module is loaded, and restart networking. Ubuntu has made us do things the Windows way when new modules are loaded, and many don't know that a restart isn't needed.

---

### Post by irv on 2011-04-14
First I want to say, this thread has been very informational. I gained more knowledge from many of the post here. Thanks to all for your input.

As I was reading through the post a thought came to me. It is an allegory.
My wife bought me a new pair of shoes. and they are nice, but I hate to break in new shoes. My old ones are so comfortable. So what I have been doing is trying not to ware the old ones, like today I have on the new ones. They don't feel that bad, but there are not my old one. The problem is my wife will one day throw my old one out when I am not looking and I will have to ware the new one. Maybe by then I will have broken in the new ones to the point that they will feel like the old ones.
I think you get the point.

---

### Post by 23dornot23d on 2011-04-14
Very good ...... but I once had a new set of shoes that were made of very hard leather

and they never did break in ........ lets hope that this leather is not so hard ......

That it does soften and break in as we would like it to ...... :)

Things always change for the better ...... I think .... :confused:

---

### Post by mc4man on 2011-04-14
> **beew said:**
> I have never been able to install proprietary graphic card with live usb (10.04 and 10.10)
Then it may have been karmic was the last that allowed the nvidia restricted drivers to be run from the livecd. (no persistence 
At least now you can load the mesa 3d  (experimental drivers) and test unity from the live cd with nvidia (or see if your adapter will at least work

Edit: I'm going to try nvidia-current again tonight, though as of a few weeks ago it would not work on the livecd

---

### Post by sgage on 2011-04-14
> **irv said:**
> First I want to say, this thread has been very informational. I gained more knowledge from many of the post here. Thanks to all for your input.

As I was reading through the post a thought came to me. It is an allegory.
My wife bought me a new pair of shoes. and they are nice, but I hate to break in new shoes. My old ones are so comfortable. So what I have been doing is trying not to ware the old ones, like today I have on the new ones. They don't feel that bad, but there are not my old one. The problem is my wife will one day throw my old one out when I am not looking and I will have to ware the new one. Maybe by then I will have broken in the new ones to the point that they will feel like the old ones.
I think you get the point.

I totally get the point: You must hide your old shoes so your wife doesn't throw them out :KS

---

### Post by Chris180775 on 2011-04-14
> **kansasnoob said:**
> Did you read my post #3?

You can still get the true "classic" Gnome look and feel in Natty!

Oneiric is not here yet so we'll have to wait and see, but my bet is that we'll be able to get real close to a "classic" look and feel with Gnome3 in Ubuntu.

Where there's a will, there's a way :D

I logged for the first time in classic mode and is different from what I've seen some time ago: it's like 10.10 :o
Thanks! :D

---

### Post by kansasnoob on 2011-04-14
> **irv said:**
> First I want to say, this thread has been very informational. I gained more knowledge from many of the post here. Thanks to all for your input.

As I was reading through the post a thought came to me. It is an allegory.
My wife bought me a new pair of shoes. and they are nice, but I hate to break in new shoes. My old ones are so comfortable. So what I have been doing is trying not to ware the old ones, like today I have on the new ones. They don't feel that bad, but there are not my old one. The problem is my wife will one day throw my old one out when I am not looking and I will have to ware the new one. Maybe by then I will have broken in the new ones to the point that they will feel like the old ones.
I think you get the point.

That was my purpose in post #3. Adequate options exist!

I'd be very, very surprised it adequate options don't exist in Oneiric.

Those who find Unity just not suitable are suffering, at least on some level, from panic :shock:

I can assure you that there is no need to panic!

---

### Post by beew on 2011-04-14
> **mc4man said:**
> Then it may have been karmic was the last that allowed the nvidia restricted drivers to be run from the livecd. (no persistence 
At least now you can load the mesa 3d  (experimental drivers) and test unity from the live cd with nvidia (or see if your adapter will at least work




Now I have Natty fully installed on a 10G partition on an external drive (not a live casper install with persistence) and I can install and test anything. :) I am not installing proprietary graphic cards just because I want to keep it portable.

---

### Post by kansasnoob on 2011-04-14
> **Chris180775 said:**
> I logged for the first time in classic mode and is different from what I've seen some time ago: it's like 10.10 :o
Thanks! :D

Be sure and pay attention to the bits about the global menu and the overlay scroll-bars :D

---

### Post by kansasnoob on 2011-04-14
I have other tasks to attend to ATM, and I would not be angry if someone beat me to the punch on this, but I'm thinking when the actual Beta 2 is released, if the Release Notes don't adequately mention how to revert to the typical Gnome DE, a new bug report should be filed.

It should be very clear to everyone that options are available, and if they follow the correct procedure they can still wear those "new shoes" only when they wish :D

I like the "new shoes" comparison :guitar:

---

### Post by irv on 2011-04-14
> **kansasnoob said:**
> Are you aware that you can switch to either the Classic or Classic w/o effects desktop at login?

Also I made some rather sloppy notes about other things in Natty in posts #1 and #2 here:

[http://ubuntuforums.org/showthread.php?t=1718631](http://ubuntuforums.org/showthread.php?t=1718631)

This is another thing you can not do with the live OS from the USB or CD. I can get to a login screen, and I get the option to switch to the Classic and Classic w/o effects, but as soon as I login it comes right back to Unity.

This just seem like another thing you can not test with the live OS from media.

---

### Post by beew on 2011-04-14
> **irv said:**
> This is another thing you can not do with the live OS from the USB or CD. I can get to a login screen, and I get the option to switch to the Classic and Classic w/o effects, but as soon as I login it comes right back to Unity.

This just seem like another thing you can not test with the live OS from media.

What if you make a live usb with persistence? That should solve your problem with wifi driver should installing it require rebooting.

---

### Post by irv on 2011-04-14
> **cariboo907 said:**
> You don't have to do a restart if you install the STA driver, just make sure the wl module is loaded, and restart networking. Ubuntu has made us do things the Windows way when new modules are loaded, and many don't know that a restart isn't needed.

I will try this when I get home I am on the road and in a coffee shop right now. I need to plug in the wire to get the driver and then I will make sure the module is loaded. Is there a quick command I can type at the terminal to restart the network: like: sudo restart networkmanager, or something like that?

---

### Post by irv on 2011-04-14
> **beew said:**
> What if you make a live usb with persistence? That should solve your problem with wifi driver should installing it require rebooting.

I guess I am not sure what you mean by persistence? Do you mean installing on a USB and booting from there? If this is what you mean then I am not sure how to do this outside of going through the install and not on the HD but on the USB.

---

### Post by beew on 2011-04-14
> **irv said:**
> I guess I am not sure what you mean by persistence? Do you mean installing on a USB and booting from there? If this is what you mean then I am not sure how to do this outside of going through the install and not on the HD but on the USB.

You can create a live usb in such a way that it saves the settings and data when you switch off, so you don't lose anything you install or any customization when you boot up next time. This is called persistence.

If you create the usb stck with the Ubuntu startup disk creator that option would be available. But unetbootin doesn't support persistence. In Ubuntu you can also create live usb with persistence using multisystem [http://liveusb.info/dotclear/](http://liveusb.info/dotclear/) (it supports multiboot live usb and a long list of distros including Ubuntu, the actual program is in English even though the webpage is in French)


**Edited:** No, a live usb with persistence is not a full installation into a usb stick, it is exactly what you have except you can save things without losing them on reboot.

---

### Post by msrinath80 on 2011-04-14
> **kansasnoob said:**
> Did you read my post #3?

You can still get the true "classic" Gnome look and feel in Natty!

Oneiric is not here yet so we'll have to wait and see, but my bet is that we'll be able to get real close to a "classic" look and feel with Gnome3 in Ubuntu.

Where there's a will, there's a way :D

I have to appreciate your efforts in trying to keep people around and within Ubuntu. Not criticizing.

However, I think the bigger and more touchy concern with most people isn't whether or not the Classic interface can be used in Natty. It's actually the fact that the Classic interface will be removed after a release or two.

While some folks are comfortable with what they get `right here' and `right now', many like the reassuring feel of future security. In other words, knowing that something you like and are very "used to" will remain in place for the foreseeable future is important to some folks.

Unity and 'Gnome shell' are both major steps away from the "comfort zone" most folks are used to. A crude analogy: It's like telling people in the real world that 'Cars' are not going to be manufactured anymore with steering wheels or brake/acceleration controls. Instead most functions of the car are going to be handled by an AI specifically designed to maximize comfort and fuel economy. How many folks do you think will simply put up with a change like this? To add an option for added functionality is one thing, and to restrict options in the name of (misguided) "simplicity" is a whole other thing :)

---

### Post by mc4man on 2011-04-14
> **irv said:**
> This is another thing you can not do with the live OS from the USB or CD. I can get to a login screen, and I get the option to switch to the Classic and Classic w/o effects, but as soon as I login it comes right back to Unity.

This just seem like another thing you can not test with the live OS from media.
I find that with nvidia can test all 3
It fairly obvious as far as classic - with effects has a 2x2 workspaces, without effects defaults to 1x4, though one could ck. with ps for compiz or metacity.

---

### Post by kansasnoob on 2011-04-14
> **irv said:**
> This is another thing you can not do with the live OS from the USB or CD. I can get to a login screen, and I get the option to switch to the Classic and Classic w/o effects, but as soon as I login it comes right back to Unity.

This just seem like another thing you can not test with the live OS from media.

YES! You can. I've done it a bunch of times while testing.

Simply press Alt + SysReq + K, then use the user name "ubuntu", select the preferred session, and leave the password blank :)

I swear it works :D

I've done it literally dozens (maybe a hundred) times performing ubiquity testing - really :)

---

### Post by seeker5528 on 2011-04-14
> **msrinath80 said:**
> While some folks are comfortable with what they get `right here' and `right now', many like the reassuring feel of future security. In other words, knowing that something you like and are very "used to" will remain in place for the foreseeable future is important to some folks.

From a user standpoint, if you stick with desktop releases, the foreseeable future is 1 to 3 years, more or less, correct?

The only thing that is guaranteed is change.

Having said that, Gnome needs a fallback for the people who can't run Gnome Shell and may not be able to run Mutter either, so I think it is probably reasonably safe to say metacity and gnome-panel will be around and maintained for at least a few years. And I expect will probably continue to be maintained if the Gnome developers drop them from Gnome proper, but that's less clear.

Having said that, metacity is just a window manage, it's make less difference to the overall experience than some of the other stuff, and while the traditional panel in Gnome 3 still looks more or less like it has, it has seen changes for Gnome 3. Even if you choose to stick with metacity+gnome-panel the non window manager, non panel, non shell parts of Gnome will continue to change, which factors in to the equation as well. 

While Gnome 2 had a good run, I think one of the things that was determined while the developers were discussing whether they wanted to do a Gnome 3 release or not and really looking at the history of Gnome 2 was that, yeah, the Gnome development platform shouldn't be a constantly moving target that developers always have to stay on top of and adapt to, but never dropping anything for the sake of backward compatibility is a little too extreme in the other direction and there needs to be a more balanced approach that falls somewhere in the middle. On one level, I expect going forward that will be a factor as well, on another level it's not like Gnome stuff never suffered from incompatibilities so some occasional deprecations and removals may not turn out to be all that big of a factor. 

Later, Seeker

---

### Post by yaji on 2011-04-14
> **msrinath80 said:**
> Unity and 'Gnome shell' are both major steps away from the "comfort zone" most folks are used to. A crude analogy: It's like telling people in the real world that 'Cars' are not going to be manufactured anymore with steering wheels or brake/acceleration controls. Instead most functions of the car are going to be handled by an AI specifically designed to maximize comfort and fuel economy.

Well I think its more like:

[img]http://img848.imageshack.us/img848/2096/southparkit.gif[/img]

---

### Post by 23dornot23d on 2011-04-14
What are the real advantages of Gnome 3 over Gnome 2 then .....  ?

I am finding it hard to understand at the moment what benefits we will see ?

But I do like progress ..... as long as it make things better for us all ......

---

### Post by cariboo on 2011-04-14
> **irv said:**
> I will try this when I get home I am on the road and in a coffee shop right now. I need to plug in the wire to get the driver and then I will make sure the module is loaded. Is there a quick command I can type at the terminal to restart the network: like: sudo restart networkmanager, or something like that?

```
sudo service networking restart 
```

has always worked for me.

---

### Post by cariboo on 2011-04-14
> **23dornot23d said:**
> What are the real advantages of Gnome 3 over Gnome 2 then .....  ?

I am finding it hard to understand at the moment what benefits we will see ?

But I do like progress ..... as long as it make things better for us all ......

Have a look at this page:

[http://library.gnome.org/misc/release-notes/3.0/](http://library.gnome.org/misc/release-notes/3.0/)

pay attention to What's New for Developers.

---

### Post by 23dornot23d on 2011-04-14
Ok cheers for that link - it looks very interesting ........ ty


particularly like this bit ...

**Modern Graphics**

          GTK+, the GNOME graphical toolkit, has made a clean break from          antiquated drawing APIs. This has allowed it to be consolidated around          modern graphics facilities, making it faster and more portable.

---

### Post by akand074 on 2011-04-14
I don't know about as a desktop experience, I'll wait for the full release to put it on my main machine, but Ubuntu 11.04 on my laptop is amazing. It actually makes it a lot more usable and efficient, I even really liked the global menus that I thought I'd hate (I may dislike it on my desktop) but I think 11.04 is a great laptop release. Personally I think the OP is being a little quick to judge personally. I mean your gnome-shell setup seems to run perfectly well for you customized in a way that makes your work more efficient, but tell me, I'm sure you didn't install and use Ubuntu (or any other distribution with gnome 2) for the first time and boom, immediately customized it and used it in such a matter? Maybe you did. But the point is, given a chance, you might even be able to come up with a neat idea that is just as efficient for you if not more. Perhaps use a dock? Have your dock for one thing and the Unity side panel for another thing (kind of like the way you used the two panels). If you still don't like it or can't find a good way for it to work for you, well then obviously Unity is not for you and you should use another interface. There won't be one interface that works for everyone. 

That aside. I love Ubuntu and Unity on my laptop. Unity is still brand new, I mean even in 11.04 it's still really in development. I think Ubuntu 11.10 is going to be a fantastic release when they update and add functionality to Unity and implement gnome 3 well too. That will be a fantastic OS. I'm excited to try it on my desktop, see if I like it on there as well.

---

### Post by irv on 2011-04-14
> **beew said:**
> You can create a live usb in such a way that it saves the settings and data when you switch off, so you don't lose anything you install or any customization when you boot up next time. This is called persistence.

If you create the usb stck with the Ubuntu startup disk creator that option would be available. But unetbootin doesn't support persistence. In Ubuntu you can also create live usb with persistence using multisystem [http://liveusb.info/dotclear/](http://liveusb.info/dotclear/) (it supports multiboot live usb and a long list of distros including Ubuntu, the actual program is in English even though the webpage is in French)


**Edited:** No, a live usb with persistence is not a full installation into a usb stick, it is exactly what you have except you can save things without losing them on reboot.

Thanks for the tip. I did this and it works. One thing I saw was the one I created with unetbootin boots much faster then the one I created with Ubuntu startup disk creator. But at least I can save my setting. I am now able to use Gnome with the panel, but I will still have to wait until I get home to try loading the wireless driver. Still on the road.

---

### Post by irv on 2011-04-14
> **cariboo907 said:**
> ```
sudo service networking restart 
```

has always worked for me.

Thanks,
 I used this before, but I had a senior moment or a brain freeze.

---

### Post by william_nbg on 2011-04-14
I think, one of the biggest reasons I've been using Ubuntu since 5.04 live, and not Windows is ...

I *LOVE* getting new stuff to play with every six months. People using Windows are using the same desktop since '95 - that's 16 years. :P

I don't think I've ever been able to wait for a release to go stable before upgrading - I just have to see the new stuff! Although, it is a production machine, I could get into trouble with my work if I broke it f''' around with beta stuff.

I upgraded one day ago to 11.04. And, yes, it does feel strange, some things feel out of place, but it's NEW STUFF. Sorry, maybe I shouldn't have had that second glass of wine.

Maybe I'll give Gnome Shell another try, but I think I'm gonna hang out in Unity for a while.

Toast! To new Stuff!

---

### Post by aljazek on 2011-04-14
After few days of testing I finally decided that I prefer Unity to Gnome 3 (I really don't like KDE :-)). But I still found some major bugs in beta 2 -> compiz crashing and icons in applications menu are still invisible until you cross them over with cursor. I think I'll wait for 11.10. :)

---

### Post by Visceral Monkey on 2011-04-14
I really had a hard time getting Unity to "flow" when I used it. Things seemed misplaced and the whole experience felt awkward.  Switching to Gnome 3 was like a world of difference when it comes to usability, everything was easier to access, things "flowed" and overall usability was much improved. They might looks alike on the surface, but that's about where it ends.

As for the old gnome look, well, it will still be there but it's pretty much headed to the dust-bin of history. KDE, Unity and Gnome 3 are going to be the "big" 3 now it seems. KDE is yesterdays OS interface with the bling piled on, Unity and Gnome 3 are where things are probably headed. Just can't use Unity right now, it's not ready.

As for compiz, I don't miss it, at all. Loads and loads of visual garbage that did little more than distract most people. It was an interesting idea when it came out, but it quickly got tacky.

As for under the hood, 11.04 detected everything I have and set it up properly on the first go, so no complaints there at all. Technically, excellent.

---

### Post by cariboo on 2011-04-14
> **irv said:**
> Thanks,
 I used this before, but I had a senior moment or a brain freeze.

I take that back, I just tried it, and I had to log out and back in again to get wireless to work :)

---

### Post by irv on 2011-04-14
> **cariboo907 said:**
> I take that back, I just tried it, and I had to log out and back in again to get wireless to work :)

That's OK, I have a live USB now that will save my driver and I will be able to reboot and see is it works with my wireless. If it does, I am changing my mind. After all I read here I am going to install 11.04 when the finial release comes out and I am going to try and run Gnome 3. From all I have read and seen it sounds like I will like it. Again thanks for all the great post on this thread.

---

### Post by rburkartjo on 2011-04-14
ref beta2 i really like unity but beta2 seems to be crashing more than b1

---

### Post by Ichtyandr on 2011-04-14
beta 2 did not crash or give any error so far, beta 1 was giving crash reports every minute or so. use 64bit with latest nvidia blob 270.41.03 (on geforce 8400GS ) and unity 3d works wonderfully

---

### Post by irv on 2011-04-14
Well I am home now, and I install the wireless card driver and restarted. I now have the driver activated, but it will not work well with my wireless card. It does not find any wireless network and I have 3 of them in my area and that includes my own. This has been the worst release in beta that I have try to test on my Dell inspiron 1521 laptop. The wire network works fine but the wireless is a no go. I am back in 10.10. I am going to wait until the finial release on the 28th, and If I can't get that one to work with my wireless I guess I will have to wait until there is a fix or I will be done with Ubuntu until it plays well with my hardware. 
This has happen before a few years ago. I don't remember the versions, but the older ones worked with out any problem, then when new release came out I had to use windows drivers to get my wireless to work, And then when 10.04 and 10.10 came out all I had to do is use the additional drivers utility and it worked flawless. I know it is hard to make Ubuntu work with all hardware, but it seem like this version is going backward and not forward but before I speak to loud I will wait until the finial release.

---

### Post by mc4man on 2011-04-14
Don't know if this is your model or not, also there are several threads in this subforum concerning various broadcom wifi, some show workarounds
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677)

[http://ubuntuforums.org/showthread.php?t=1729262](http://ubuntuforums.org/showthread.php?t=1729262)
and several more

---

### Post by pony-tail on 2011-04-14
I too have just installed beta 2 ( had beta 1 prior to that ) I have done a reformat / clean install .
I am 14 days into battling with the unity interface and still despising it .
Is it possible to have an Enlightenment style right click menu or a pull down menu from the top bar on the Unity interface as this would negate 80% of my issues with Unity - That way I would not have to deal with their unintuitive desktop interface . I could just ignore it and get on with what I have to do .

---

### Post by Ichtyandr on 2011-04-15
I have exactly the same setup on natty as I had before on maverick and before that on lucid
actually new ubuntu system does work very well for me, updated apps and great choices
I am actually rather impressed by this beta. on beta 1 I still had issues with nvidia blob

---

### Post by kansasnoob on 2011-04-15
> **pony-tail said:**
> I too have just installed beta 2 ( had beta 1 prior to that ) I have done a reformat / clean install .
I am 14 days into battling with the unity interface and still despising it .
Is it possible to have an Enlightenment style right click menu or a pull down menu from the top bar on the Unity interface as this would negate 80% of my issues with Unity - That way I would not have to deal with their unintuitive desktop interface . I could just ignore it and get on with what I have to do .

Did you see my post #3 about using the classic DE?

---

### Post by pony-tail on 2011-04-15
Yes i did !
Classic has some of the functionality , but very little of the configurability of Panels on gnome 2.xx - Further it will to my understanding not be on 11.10 so dropping back to classic is at best a stop gap . It is difficult for me to put into words how much I loathe 11.04 - I have been using it now for a fortnight and will persevere for a few more weeks to see if it is just my issues with adapting to a new interface but I very much doubt it - this is the first version of Ubuntu since their first version that I just cannot take to . I have been on this forum for quite a while but do not that often post but this version has me so annoyed that I felt that I had to speak up .

---

### Post by Visceral Monkey on 2011-04-15
> **pony-tail said:**
> Yes i did !
Classic has some of the functionality , but very little of the configurability of Panels on gnome 2.xx - Further it will to my understanding not be on 11.10 so dropping back to classic is at best a stop gap . It is difficult for me to put into words how much I loathe 11.04 - I have been using it now for a fortnight and will persevere for a few more weeks to see if it is just my issues with adapting to a new interface but I very much doubt it - this is the first version of Ubuntu since their first version that I just cannot take to . I have been on this forum for quite a while but do not that often post but this version has me so annoyed that I felt that I had to speak up .

It's an interesting moment in time for Linux Desktop environments. Unity and Gnome 3 have effectively split the old Gnome community but even further than that, you have some Distro's like mint that plan to use gnome 3 but *not* the Gnome 3 shell, further splitting down the Gnome 3 shell user base.

Mint: Gnome 3 but not the Gnome 3 shell
SuSe: Gnome 3 Shell
Fedora: Gnome 3 Shell
Debian: Whatever was stable 4 years ago, I'm sure.
Ubuntu: Unity (are they using gnome 3 under the hood? Not sure).

Ubuntu is the big guy on the block for Linux on the Desktop right now so it's interesting to see quite a few people talking about ditching it for other distro's. In the short term at least, I think it's pretty obvious that Unity is going to cause a decrease in mind-share for Ubuntu as we knew it. Gnome in the meantime loses Ubuntu *and* Mint for being the default DE.

My guess is that you'll see further splitting along usability lines in the near future with some re-coalescing later down the line. I would *not* expect mint, SuSe, Fedora or Debian to ever accept Unity as the default UI..I think it's going to be a Ubuntu only thing.

Do *any* distro's use KDE as the default anymore? Seems like more of a backup DE these days.

---

### Post by Harry33 on 2011-04-15
> **Visceral Monkey said:**
> 
...
Mint: Gnome 3 but not the Gnome 3 shell
SuSe: Gnome 3 Shell
Fedora: Gnome 3 Shell
Debian: Whatever was stable 4 years ago, I'm sure.
Ubuntu: Unity (are they using gnome 3 under the hood? Not sure).
...


That is an interesting comparison there.
And even more complicated one, when you add the mockups you get from using PPA's.
For example
Ubuntu: Gnome3 Shell from Gnome3 PPA (with Unity, Compiz and Gnome-panel2 uninstalled). :p

---

### Post by Visceral Monkey on 2011-04-15
> **Harry33 said:**
> That is an interesting comparison there.
And even more complicated one, when you add the mockups you get from using PPA's.
For example
Ubuntu: Gnome3 Shell from Gnome3 PPA (with Unity, Compiz and Gnome-panel2 uninstalled). :p

True, but the the sake of argument, I'm pointing out what ships as default. In any case, the Unity/Gnome 3 "split" is only going to further dilute things. The real winner here appears to be XFCE as the knee-jerk reaction from parties disgusted with both Unity and Gnome 3.

Of course the problem with desktop environments is, even if you get it right, you have to turn around and tear it down again and start over..what else are those guys going to do?

---

### Post by pony-tail on 2011-04-15
Gnome 3 / Gnome shell and unity have been the most divisive additions to Linux I have seen for years .
Fortunately If I need to I can build ( Linux From Scratch ) my own spin on Linux - but that is very very time consuming and I would prefer not to have to ( I have a life to live ) . At present I am doing a "wait and see" 
The Linux community have made mis steps before and have managed to get past them .

---

### Post by kansasnoob on 2011-04-15
> **pony-tail said:**
> Yes i did !
Classic has some of the functionality , but very little of the configurability of Panels on gnome 2.xx - Further it will to my understanding not be on 11.10 so dropping back to classic is at best a stop gap . It is difficult for me to put into words how much I loathe 11.04 - I have been using it now for a fortnight and will persevere for a few more weeks to see if it is just my issues with adapting to a new interface but I very much doubt it - this is the first version of Ubuntu since their first version that I just cannot take to . I have been on this forum for quite a while but do not that often post but this version has me so annoyed that I felt that I had to speak up .

Natty is still using gnome 2.32, not gnome3. So you can make the classic desktop, including the panels, look identical to Maverick or Lucid.

Once we have a truly stable gnome3 base to work with we'll have to see just how easy it is to customize the "fallback" panels. I have already figured out how to force the fallback mode. (There is already a gui to do so but it doesn't work).

As I said earlier, PANIC is the real killer here!

---

### Post by pony-tail on 2011-04-15
For me it is not a case of panic - I have changed interfaces many times ( I started in Apple IIe and pro Dos days ) Most changes have been improvements - but not all .

---

### Post by dino99 on 2011-04-15
As i've followed lot of releases i must say i'm impressed by all the quality we get now with the last 3 ones, getting better every time: even with the alpha & beta, its rare to be locked with breakage(s), in fact i'm frustated as i've not had breakage this time, even with those too bleeding edge canonical choice(s). 

So only one word devs: congrat :)

---

### Post by rburkartjo on 2011-04-15
i agree with dino i havent got beta2 to completely crash yet and of course that is good. only problem so far is that top toolbar and unity tool bar do periodically disappear. however if i wait they come back

---

### Post by irv on 2011-04-15
After reading what everyone is saying out here, not only is my head spinning, but I forgot what direction I was going. So I came to a screeching halt, got my bearing and am going to start fresh.
I order a new 500 gig HD for my Dell laptop and I will install Win7 64 bit on it, and then Ubuntu 11.04 64 bit, and just play around with it with Unity, Gnome 3, Gnome shell, KDE, XFce, and what ever else I find. Oh I might even install mint on it. The point being If nothing I see satisfies me, I will just pop it back out and put my old drive back in and go about my business. Maybe by the the time I get the new drive and Ubuntu 11.04 is released everything will just work fine.
Maybe I am in a dream world. Oh well!

---

### Post by dino99 on 2011-04-15
some fresh air may help too :)

---

### Post by irv on 2011-04-15
> **dino99 said:**
> some fresh air may help too :)

You might not believe this, but I just went out side to take a walk, It is only 37 degrees out but the wind is blowing so hard it feel like 10 degrees. Little to say I only walked one block and turn around and came home. Enough of the fresh air.

---

### Post by 23dornot23d on 2011-04-15
> **irv said:**
> After reading what everyone is saying out here, not only is my head spinning, but I forgot what direction I was going. So I came to a screeching halt, got my bearing and am going to start fresh.
I order a new [COLOR=Red]**500 gig HD**[/COLOR] for my Dell laptop and I will install Win7 64 bit on it, and then Ubuntu 11.04 64 bit, and just play around with it with Unity, Gnome 3, Gnome shell, KDE, XFce, and what ever else I find. Oh I might even install mint on it. The point being If nothing I see satisfies me, I will just pop it back out and put my old drive back in and go about my business. Maybe by the the time [COLOR=Red]**I get the new drive**[/COLOR] and Ubuntu 11.04 is released everything will just work fine.
Maybe I am in a dream world. Oh well!


This is a great way to test and swap between different desktops .... 

I have a laptop as well as a desktop machine ...... and the quickest and simplest way for me to swap OS's is with [COLOR=Red]**USB hard drives**[/COLOR] ..... so simple to swap from computer to computer ....... and if friends get problems ...... I just unplug one and take it with me
to go sort out things ..... with my own familiar desktop at my fingertips.

The reason I keep investing in USB drives as they are reasonably priced ...... have 4 now .... western digital seem to work the best for me with my Acer aspire Laptop .....

The USB leads .... all sit at one side of my laptop ..... 

I do a shutdown and can choose which lead or leads to plug in ....... so quick and so simple.

Just thought I would add this for information - in-case anyone else wondered about it .....
as some people say the USB drives are slow ..... but I do not notice it ...... :)

Fresh air is good now and again lols .... ;)  
sleep >>> computer >>> sleep >>> computer >>> eat >>>
sleep >>> computer >>> sleep >>> computer >>> eat >>>
sleep >>> computer >>> sleep >>> eat >>> toilet >>>
 fresh air ...... weekend

---

### Post by dino99 on 2011-04-15
> **irv said:**
> You might not believe this, but I just went out side to take a walk, It is only 37 degrees out but the wind is blowing so hard it feel like 10 degrees. Little to say I only walked one block and turn around and came home. Enough of the fresh air.

ah sorry its around 24 C° here, makes a difference indeed :(

---

### Post by kansasnoob on 2011-04-15
> **irv said:**
> After reading what everyone is saying out here, not only is my head spinning, but I forgot what direction I was going. So I came to a screeching halt, got my bearing and am going to start fresh.
I order a new 500 gig HD for my Dell laptop and I will install Win7 64 bit on it, and then Ubuntu 11.04 64 bit, and just play around with it with Unity, Gnome 3, Gnome shell, KDE, XFce, and what ever else I find. Oh I might even install mint on it. The point being If nothing I see satisfies me, I will just pop it back out and put my old drive back in and go about my business. Maybe by the the time I get the new drive and Ubuntu 11.04 is released everything will just work fine.
Maybe I am in a dream world. Oh well!

Why stop with only three operating systems:

[ATTACH]189119[/ATTACH]

I'll grant you that's major overkill but I like to try things, and I also do upgrade testing - that accounts for those MM to NN* and HH to LL partitions.

Two of the Natty's are being used for gnome3 testing (different ppa's), to compare notes so to speak, neither works incredibly well.

Anyway, it's all great fun to me, and if I jack one OS up to the point of no return I just reformat that one partition and use it for the next fresh install :lolflag:

---

### Post by kansasnoob on 2011-04-15
> Fresh air is good now and again lols ....
sleep >>> computer >>> sleep >>> computer >>> eat >>>
sleep >>> computer >>> sleep >>> computer >>> eat >>>
sleep >>> computer >>> sleep >>> eat >>> toilet >>>
fresh air ...... weekend

I'm old, my itinerary includes many more toilet breaks :D

---

### Post by 23dornot23d on 2011-04-15
Lols .....  :lolflag:   here is my main drive on the laptop not as clean and tidy as yours 

I have 4 USBs .... 2 x 1 terra a 500 Gig and a 300 Gig  


[IMG]http://img402.imageshack.us/img402/9784/75483858.jpg[/IMG]

[IMG]http://img691.imageshack.us/img691/2343/21287166.jpg[/IMG]


and this is my Main Drive for working on >>>>>> [LINK]("http://img816.imageshack.us/img816/5687/81768403.jpg") >>>> the other two are downstairs on the desktop machine .....

Keeps my head spinning trying to remember where everything is ...... ;)

Once UNITY comes out properly I might find a space for it .......

Days left to New Release - [LINK]("http://ubuntu.touchlay.com/urb/11.04")

---

### Post by irv on 2011-04-15
I am getting totally discussed with 11.04. I have all kind of things I want to try to see how it works. And I keep striking out. I had it on a USB stick, and I couldn't get any programs to run on it, so I put it on a 60 Gig USB drive. I did this by removing the internal drive from my laptop and installed 11.04 beta 2 from a CD to the 60 Gig USB drive. Worked great.
I booted with that drive and it came up somewhat fast. Now I have another problem. It does not find my network with the wire or the wireless now. I have no way of installing anything. I am really getting fed up with this beta release. If the finial release is this bad I am going to flat out refuse to install it.
I have been installing and using Ubuntu for many years now, and I have never had this much trouble. Like this title of this thread says, I am not very impressed with 11.04 not only because of Unity, but all the bugs this release has. I know it is beta, but find I can work around bug, but this one I am giving up on.

---

### Post by 23dornot23d on 2011-04-15
Try this page - for setting wireless up via the command line ..... [LINK]("http://www.wikihow.com/Set-up-a-Wireless-Network-in-Linux-Via-the-Command-Line")

---

### Post by ivanovnegro on 2011-04-15
> **Visceral Monkey said:**
> It's an interesting moment in time for Linux Desktop environments. Unity and Gnome 3 have effectively split the old Gnome community but even further than that, you have some Distro's like mint that plan to use gnome 3 but *not* the Gnome 3 shell, further splitting down the Gnome 3 shell user base.

Mint: Gnome 3 but not the Gnome 3 shell
SuSe: Gnome 3 Shell
Fedora: Gnome 3 Shell
Debian: Whatever was stable 4 years ago, I'm sure.
Ubuntu: Unity (are they using gnome 3 under the hood? Not sure).

Ubuntu is the big guy on the block for Linux on the Desktop right now so it's interesting to see quite a few people talking about ditching it for other distro's. In the short term at least, I think it's pretty obvious that Unity is going to cause a decrease in mind-share for Ubuntu as we knew it. Gnome in the meantime loses Ubuntu *and* Mint for being the default DE.

My guess is that you'll see further splitting along usability lines in the near future with some re-coalescing later down the line. I would *not* expect mint, SuSe, Fedora or Debian to ever accept Unity as the default UI..I think it's going to be a Ubuntu only thing.

Do *any* distro's use KDE as the default anymore? Seems like more of a backup DE these days.

There are some distros using KDE as default a part from Suse; PCLinuxOS and Sabayon maybe, also there are Mandriva/Mageia and Chakra. Ok, maybe they are not the big players but also not bad.

> **irv said:**
> I am getting totally discussed with 11.04. I have all kind of things I want to try to see how it works. And I keep striking out. I had it on a USB stick, and I couldn't get any programs to run on it, so I put it on a 60 Gig USB drive. I did this by removing the internal drive from my laptop and installed 11.04 beta 2 from a CD to the 60 Gig USB drive. Worked great.
I booted with that drive and it came up somewhat fast. Now I have another problem. It does not find my network with the wire or the wireless now. I have no way of installing anything. I am really getting fed up with this beta release. If the finial release is this bad I am going to flat out refuse to install it.
I have been installing and using Ubuntu for many years now, and I have never had this much trouble. Like this title of this thread says, I am not very impressed with 11.04 not only because of Unity, but all the bugs this release has. I know it is beta, but find I can work around bug, but this one I am giving up on.

I have to admit, first not a fan of Unity, but I always obligated me to test and use it.
No go for me, Beta 1 and Beta 2 refused to use my Wireless card, that was the first time for me that Ubuntu failed. I will see the final but Im yet very comfortable with KDE, what I never could believe, but I made the same thing, I obligated me to get used to it and it worked but with Unity still not.

---

### Post by xx58 on 2011-04-15
:rolleyes:I don't like it, but I will go with it, because there are not choice..... Will see what future will bring ....

---

### Post by ivanovnegro on 2011-04-15
> **xx58 said:**
> :rolleyes:I don't like it, but I will go with it, because there are not choice..... Will see what future will bring ....

Dont worry, there are many choices in Linux, even to stay with other spins of Ubuntu. ;)

---

### Post by barisurum on 2011-04-15
Canonical should not use a new ubuntu release as a testing ground for immature new stuff. If its not ready (and it seems to be) then unity must be optional, not the well tested and well received classic gnome UI. A serious mistake that may result in userbase loss.

---

### Post by seeker5528 on 2011-04-15
> **pony-tail said:**
> Yes i did !
Classic has some of the functionality , but very little of the configurability of Panels on gnome 2.xx - Further it will to my understanding not be on 11.10 so dropping back to classic is at best a stop gap .

Won't be on the CD, it will still be in the repositories. 

There looks to be an effort to create a *buntu that uses Gnome shell by default, and there is an option in Gnome 3 shell to tell it to always use the fallback mode. Remains to be seen if this effort will sink or swim, but I'm expect some way or another we will see a *buntu that uses Gnome Shell.

The gnome-session in Debian unstable+experimental also doesn't provide a fallback option since it's *supposed* to fall back automatically if you can't run Gnome Shell.

As for the less configurable panels, I think we are stuck with those at least in the short term.

Later, Seeker

---

### Post by kansasnoob on 2011-04-16
> **seeker5528 said:**
> Won't be on the CD, it will still be in the repositories. 

There looks to be an effort to create a *buntu that uses Gnome shell by default, and there is an option in Gnome 3 shell to tell it to always use the fallback mode. Remains to be seen if this effort will sink or swim, but I'm expect some way or another we will see a *buntu that uses Gnome Shell.

The gnome-session in Debian unstable+experimental also doesn't provide a fallback option since it's *supposed* to fall back automatically if you can't run Gnome Shell.

As for the less configurable panels, I think we are stuck with those at least in the short term.

Later, Seeker

I know using the old panels in gnome3 is possible, I did this earlier today with a fresh/mixed install of packages from two ppa's beginning with Lubuntu:

[ATTACH]189178[/ATTACH]

Very ugly for sure but I have my desired one panel ;)

ATM all known gnome3 ppa's (2 or 3) have some problems, all can be worked around, but why bother?

I'm just waiting for the next testing call for UGR:

[http://ugr.teampr0xy.net/](http://ugr.teampr0xy.net/)

I doubt the owner would bother with such an elaborate website if this were a fluke :D

*[COLOR="DarkOrange"]BTW, I did that just for fun while sipping my morning coffee.[/COLOR]* I just had that half broken Lubuntu and I thought .........

---

### Post by 23dornot23d on 2011-04-16
I like that idea -_*[COLOR=Blue][ will try it out too  ]("http://img193.imageshack.us/img193/7647/screenshot37v.png")[/COLOR]*_.....   [_Screenshot_]("http://img593.imageshack.us/img593/3108/screenshot36n.png")

For people that like panels and Gnome Shell its a good solution ..... IMHO ..... and it
can possibly be done while the two things developed side by side without creating too much of a fork ..... that looks good to me ..... for a 5 minute challenge while having breakfast and a coffee ;).

I just had Unity running inside kde ..... also installed the latest kernel and the latest Nvidia driver ..... and all works well .....

[This is getting to be fun]("http://img844.imageshack.us/img844/5796/screenshot41o.png") ..... with a lot of ideas being thrown up in this section it is interesting to see [what will run with what now]("http://www.youtube.com/watch?v=0OYeXE85QuM") ......

Lots of choices .... we can do whatever we want with Linux ..... not many restrictions other than technical ones ......

[Lubuntu - Gnome-shell - cairo-dock]("http://img706.imageshack.us/img706/2648/screenshot53h.png") >>> nice combination too .... ;)

---

### Post by hornedfiend on 2011-04-16
After solving my video card issues, I must say Natty is really growing into my heart. I think it only took me 10 minutes to get used to the new unity interface and so far, although it has its limitations, I really like it and it's something new and worth getting used to.
The overall os speed is faster than 10.10, even  in the beta stage. 
For me it's a definite keep as a primary os.

---

### Post by seeker5528 on 2011-04-16
> **kansasnoob said:**
> I know using the old panels in gnome3 is possible, I did this earlier today with a fresh/mixed install of packages from two ppa's beginning with Lubuntu:

[ATTACH]189178[/ATTACH]

Very ugly for sure but I have my desired one panel ;)

Gnome-panel in Natty is the old one, don't know if it works with updated-for-Gnome-3 gnome-panel. I have not been following the PPA stuff so don't know if it includes the newer one or not.

I could try it in my Debian installation when I get home, but I don't think it works, based on the fact that typing 'gnome-panel --replace' in a terminal window produces an error message indicating a panel is already running.

At least that was better than the result I got when typing 'mutter --replace'.

It had been stated in the past that you would be able to type 'gnome-panel --replace' to get the old interface, which I assume would have been mutter+gnome-panel, don't know why that changed, *I* would have preferred that, since telling it to always fall back sticks you with metacity.

Later, Seeker

---

