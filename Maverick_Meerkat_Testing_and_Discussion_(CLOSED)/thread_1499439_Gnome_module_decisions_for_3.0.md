---
title: "Gnome module decisions for 3.0"
date: 2010-06-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by zombiepig on 2010-06-01
The new module decisions for gnome 3.0 have been announced:
[http://mail.gnome.org/archives/devel-announce-list/2010-June/msg00001.html](http://mail.gnome.org/archives/devel-announce-list/2010-June/msg00001.html)

While this doesn't directly affect ubuntu and mean these modules will be part of a default ubuntu install (eg, packagekit got accepted a few releases back, but still isn't part of ubuntu), it does give a good indication of the direction gnome is heading and what technologies will be part of future releases.

Interesting parts (for me anyway) are:

gnome-color-manager accepted: It's great to see this accepted, better integration of color management on the desktop is definitely a good thing!

rygel accepted: rygel is a upnp server, and it'll be good to have easy & robust media sharing on the gnome desktop

libfolks as external dependency: when this is fully integrated it should allow contact merging in empathy and across the whole desktop (eg, starting a im conversation from evolution :D)

gnome-shell accepted: for better or worse :P

deja dup not accepted: this is a shame, a highly integrated backup app would have been a good addition

gnome activity journal/zeitgest not accepted: hopefully we'll see this in the next release after it's been developed a bit further

---

### Post by 23meg on 2010-06-02
[QUOTE=zombiepig]deja dup not accepted: this is a shame, a highly integrated backup app would have been a good addition[/QUOTE]

It (rightly) got a "no decision needed", not rejection.

I'm particularly unhappy about libappindicator; I'm not satisfied by the details given about its rejection, which I'll investigate further.

In other news, [some]("http://permalink.gmane.org/gmane.comp.gnome.devel.announce/100") [reorganization]("http://lucasr.org/2010/06/02/gnome-and-modulesets/") of modulesets was also proposed.

---

### Post by Mblackwell on 2010-06-02
Makes some sense though, applets are not used in Gnome Shell, and Shell has its own Notification system (in progress).

---

### Post by vkontakte on 2010-06-02
> **Mblackwell said:**
> Makes some sense though, applets are not used in Gnome Shell, and Shell has its own Notification system (in progress).
And I found it better than indicators: it doesn't break consistency of notification area like indicators do (no common way to open apps), but provides good indication of new messages.

---

### Post by kostkon on 2010-06-02
Everything's good, except Gnome Shell, of course.

---

### Post by gnomeuser on 2010-06-03
> **23meg said:**
> 
I'm particularly unhappy about libappindicator; I'm not satisfied by the details given about its rejection, which I'll investigate further.

I remember that when it was debated on d-d-l the initial reaction was negative due to the copyright assignment that Canonical enforces on the project.

A general recommendation on the issue of copyright assigment was supposed to be coming from the board but I haven't seen it posted on d-d-l.

Canonical hasn't moved an inch either on the matter of their unpopular project contribution requirements.

Regardless since gnome-shell was "proposed", even it was really just rubberstamping. The whole proposal process is rather arcanic and.. fallable. Thus gnome-shells requirements and its desires to reinvent the wheel (in theory correctly) comes first. It was felt that libindicate wasn't compatible enough with these needs.

It's the worst of all worlds. Yay, nobody wins.

---

### Post by zekopeko on 2010-06-03
> **gnomeuser said:**
> I remember that when it was debated on d-d-l the initial reaction was negative due to the copyright assignment that Canonical enforces on the project.

A general recommendation on the issue of copyright assigment was supposed to be coming from the board but I haven't seen it posted on d-d-l.

Canonical hasn't moved an inch either on the matter of their unpopular project contribution requirements.

Regardless since gnome-shell was "proposed", even it was really just rubberstamping. The whole proposal process is rather arcanic and.. fallable. Thus gnome-shells requirements and its desires to reinvent the wheel (in theory correctly) comes first. It was felt that libindicate wasn't compatible enough with these needs.

It's the worst of all worlds. Yay, nobody wins.

Which is funny since they built GS on Clutter which also has a copyright policy similar to Canonical's. So they have no problem including GS but without clutter-core which you need to run it. It's like creating a car and leaving the engine out.

On a related note, Gnome-Shell still sucks. I do hope Ubuntu devs create something nice from it.

---

### Post by vkontakte on 2010-06-03
> **zekopeko said:**
> On a related note, Gnome-Shell still sucks. I do hope Ubuntu devs create something nice from it.
I agree about "sucking", but highly doubt about canonical devs. IMHO both upstream gnome with their gnome-shell and canonical using their indicators as panacea are moving wrong direction. At least, in ubuntu before 10.04 I didn't change default settings but only add mine ones. Today I forced to change them: buttons, terminal background, lighter theme, change rhythmbox, tomboy and weather icons to upstream ones (what <not very smart person> made the sun black?). Recompile rhythmbox without ubuntu patches, etc.

---

### Post by screaminj3sus on 2010-06-03
I think ubuntus app indicators are a huge step int he right direction, the current gnome notification area is a friggin mess, in ubuntu its MUCH more stramlines and consistant looking.

---

### Post by vkontakte on 2010-06-03
> **screaminj3sus said:**
> I think ubuntus app indicators are a huge step int he right direction, the current gnome notification area is a friggin mess, in ubuntu its MUCH more stramlines and consistant **looking**.
That's the key. It looks slightly more consistent (although they could achieve same result just by improving apps rather than reinventing the [s]wheel[/s]notification system), but it feels and acts less consistent than before. It's OK with messaging menu (I love it). Me menu is ugly and really unusable IMO -- it's just overcomplicated with such a huge list, icons would be very useful in it. I would like to have global download menu, and indicator approach suits this task the best. But ... I can't realize what task indicators suits well with the exception of messaging and downloading. On the other hand, it brough huge inconsistency when it uses for holding apps like Rhythmbox, Transmission, etc. Is there any consistent way to open the app? With old notification area I could just click the icon, and the app window would appear. The small inconsistency in "view" is just nothing compared to this huge regression in usability. I wonder why they decided to refuse from notification area having such an obvious regression.
Apps "indicators" are very different from messaging/downloading/me indicators with their purposes. They acts completely different. For things like messaging/downloading/me I need indicator itself. For apps I don't need indicator at all in most cases. I need the app, but current approach doesn't let me perform this task efficiently.
Another thing: why being so monotonous? I catch myself moving through indicators trying to catch the one I need (rhythmbox). Unified look only prevent me to perform this task easily, it's hard to distinguish between them. I know, they were very impressed with MacOSX and tried to be very similar. But MacOSX notification system doesn't work with apps, apps are hold by dock. So, I found these latest changes to be too inconsistent, and it really disturbs me.

---

### Post by gnomeuser on 2010-06-03
> **zekopeko said:**
> Which is funny since they built GS on Clutter which also has a copyright policy similar to Canonical's. So they have no problem including GS but without clutter-core which you need to run it. It's like creating a car and leaving the engine out.

On a related note, Gnome-Shell still sucks. I do hope Ubuntu devs create something nice from it.

The Clutter thing is indeed hilarious, I mean I loath copyright assignments as much as the next man. Though they do have their place, e.g. Mono has such requirements and it results in a very clear use of the privilages on part of Novell as well as very measurable improvements to the project.

It's all in the use, personally I have thought about it carefully and I can't find a place where Clutter nor libindicate benefits from it. 

Also I believe now with MeeGo the copyright assignment will go away for Clutter. At least I remember going over the site and noticing statements along the lines of not requiring such things for MeeGo.

---

### Post by NightwishFan on 2010-06-03
Interesting, thanks for the link. As for the shell, I am curious about your opinions. Does it 'suck' (in your opinion) because of it's current state or because of its underlying technology?

---

### Post by gnomeuser on 2010-06-03
> **NightwishFan said:**
> Interesting, thanks for the link. As for the shell, I am curious about your opinions. Does it 'suck' (in your opinion) because of it's current state or because of its underlying technology?

It's suckage is sided 3.

First it is poorly reasoned, it is to me designed to bring the way traditional hackers have been productive using desktops for years to the user rather than actually improving the experience. There is nothing new in gnome-shell except a fetish like delight in workspaces. Looking at their demos and hearing them talk every time they mention "then open another workspace" I have to stop myself from screaming "Why? What is your reasoning?, why would the user do that? why? why? why?".

Instead of actually doing something to address the problems we have, we ensure that they will scale their badness according to how many workspaces you can also control at once. It seems to me that they went in with the solution being workspaces and tried to construct a problem around that. 

Secondly, Javascript why? It's slow, has a history of insecurity and being defacto non-standardized and.. it's frikkin javascript. And because it's frikkin javascript there also somehow arose the need to reimplement everything. Also why is it seen as a plus that javascript is familiar to web developers, because there are lots of them? Another thing is the specific choice that annoys me, since javascript isn't standardized, one cannot just replace the toolings underneath meaning because the g-s developers like the gecko based flavor they use that, and other parts of gnome (gnome-games) uses the webkit flavored Seed. Now we depend on two separate tools for the same job and the g-s guys really didn't see that as a problem. Finally I don't find Javascript readable but that part is just personal preference.

Finally, it doesn't introduce anything significantly better. It's just a worse way to do the exact thing we do today. There is no boldness in GNOME 3, no long term vision. They didn't even have the guts to actually depend on well established technologies like Tracker. It is still basically a computer like we have used them since pixels first graced our screens. True innovation isn't impossible, look to MeeGo, Android, Unity. It's also on this front not because they lacked interesting interaction concepts to be inspired by, some even very detailed and well thoughtout. 

On top of this no migration path is considered for the applet experience. Instead one can extend the shell itself.. but only using in-process javascript which sounds both limiting and daft.

In adopting gnome-shell I also think GNOME went in the wrong direction. We had a chance to define a core set of functionality with different UI experiences depending on the deployment.. a bit like MeeGo is doing now (though MeeGo are wrong and doomed for other reasons this they got right). Instead we have one experience available and we lost much reuse and coordination for Linux everywhere. It's a limiting view that murders innovation and makes us miss markets as well as marketshare.

---

### Post by screaminj3sus on 2010-06-03
> **gnomeuser said:**
> It's suckage is sided 3.

First it is poorly reasoned, it is to me designed to bring the way traditional hackers have been productive using desktops for years to the user rather than actually improving the experience. There is nothing new in gnome-shell except a fetish like delight in workspaces. Looking at their demos and hearing them talk every time they mention "then open another workspace" I have to stop myself from screaming "Why? What is your reasoning?, why would the user do that? why? why? why?".

Instead of actually doing something to address the problems we have, we ensure that they will scale their badness according to how many workspaces you can also control at once. It seems to me that they went in with the solution being workspaces and tried to construct a problem around that. 

Secondly, Javascript why? It's slow, has a history of insecurity and being defacto non-standardized and.. it's frikkin javascript. And because it's frikkin javascript there also somehow arose the need to reimplement everything. Also why is it seen as a plus that javascript is familiar to web developers, because there are lots of them? Another thing is the specific choice that annoys me, since javascript isn't standardized, one cannot just replace the toolings underneath meaning because the g-s developers like the gecko based flavor they use that, and other parts of gnome (gnome-games) uses the webkit flavored Seed. Now we depend on two separate tools for the same job and the g-s guys really didn't see that as a problem. Finally I don't find Javascript readable but that part is just personal preference.

Finally, it doesn't introduce anything significantly better. It's just a worse way to do the exact thing we do today. There is no boldness in GNOME 3, no long term vision. They didn't even have the guts to actually depend on well established technologies like Tracker. It is still basically a computer like we have used them since pixels first graced our screens. True innovation isn't impossible, look to MeeGo, Android, Unity. It's also on this front not because they lacked interesting interaction concepts to be inspired by, some even very detailed and well thoughtout. 

On top of this no migration path is considered for the applet experience. Instead one can extend the shell itself.. but only using in-process javascript which sounds both limiting and daft.

In adopting gnome-shell I also think GNOME went in the wrong direction. We had a chance to define a core set of functionality with different UI experiences depending on the deployment.. a bit like MeeGo is doing now (though MeeGo are wrong and doomed for other reasons this they got right). Instead we have one experience available and we lost much reuse and coordination for Linux everywhere. It's a limiting view that murders innovation and makes us miss markets as well as marketshare.

Yeah when gnome shell becomes the standard I may look at switching to xfce or kde.

---

### Post by gnomeuser on 2010-06-03
> **screaminj3sus said:**
> Yeah when gnome shell becomes the standard I may look at switching to xfce or kde.

The underlying technological improvements in GTK and our stack as a whole which come as part of GNOME 3 are very good. There are also companion technologies such as tracker, telepathy and zeitgeist which can bring unmentionable improvements. We have barely scratched the surface of what they can do for us, I am confident other options will arise that take advantage of these and bring us something remarkable. MeeGo e.g. have expressed interest in regular desktops as well as their already wide target range.

I am pretty sure we will see the GNOME 2 experience be taken in many different directions. The future might simply not be GNOME 3 as defined by GNOME. The near future seems to look like GNOME 2 evolved (as we see it today in Ubuntu, future improvements will include Windicators, global menus and so on). Also this is likely to involve a move to the GNOME 3 infrastructure core which will be a win for everyone. Long term I think this approach is likely to evolve a better but very different product and vision than what GNOME has presented with GNOME 3. 

There are also sure to be surprise candidates, nobody e.g. really expected Moblin 2 to be such a fresh approach and when it arrived everything changed. Maemo has continued to adopt technology at an impressive rate, and they are seeing it pay off, people are much more vibrant and useful part of the Maemo and media just works. I wouldn't be surprised if someone is working on something now that will wow us at a future date.

---

### Post by NightwishFan on 2010-06-03
Thanks for taking the time to post that Gnomeuser, it was a good read, and well thought out. I have nothing much to answer that since I am not much of a developer.

---

### Post by ranch hand on 2010-06-03
@gnomeuser
I find your comments on workspaces very interesting.

I use, on the current version of Gnome, 6 workspaces.  Why?  It is how I like it is the best answer.

Gnome Shell I have not tried for a couple months now.  When I did, though, one of the things I did not like was the fact that workspaces are a pain in the posterior to use with GS.

If they are trying to encourage the use of workspaces, I have no problem with that idea, they sure are doing it the wrong way.

---

### Post by zombiepig on 2010-06-03
> **gnomeuser said:**
> 
I am pretty sure we will see the GNOME 2 experience be taken in many different directions. The future might simply not be GNOME 3 as defined by GNOME. The near future seems to look like GNOME 2 evolved (as we see it today in Ubuntu, future improvements will include Windicators, global menus and so on). Also this is likely to involve a move to the GNOME 3 infrastructure core which will be a win for everyone. Long term I think this approach is likely to evolve a better but very different product and vision than what GNOME has presented with GNOME 3. 


This is the direction I'm hoping (and expecting) Ubuntu to head towards, with a UNE or xubuntu type respin for gnome shell.

---

### Post by screaminj3sus on 2010-06-03
> **ranch hand said:**
> @gnomeuser
I find your comments on workspaces very interesting.

I use, on the current version of Gnome, 6 workspaces.  Why?  It is how I like it is the best answer.

Gnome Shell I have not tried for a couple months now.  When I did, though, one of the things I did not like was the fact that workspaces are a pain in the posterior to use with GS.

If they are trying to encourage the use of workspaces, I have no problem with that idea, they sure are doing it the wrong way.

Yeah but there is tons of people who dont use workspaces or dont use them enough to want a shell completely designed around them. Currently gnome works great for people who like workspaces and people who do not, gnome-shell is forcing it upon people and as you said right now it is implemented rather poorly.

---

### Post by Merk42 on 2010-06-03
> **zombiepig said:**
> This is the direction I'm hoping (and expecting) Ubuntu to head towards, with a UNE or xubuntu type respin for gnome shell.

I would not be surprised at all if Unity were default for the desktop in a future version of Ubuntu

---

### Post by gnomeuser on 2010-06-04
> **ranch hand said:**
> @gnomeuser
I find your comments on workspaces very interesting.

I use, on the current version of Gnome, 6 workspaces.  Why?  It is how I like it is the best answer.

Gnome Shell I have not tried for a couple months now.  When I did, though, one of the things I did not like was the fact that workspaces are a pain in the posterior to use with GS.

If they are trying to encourage the use of workspaces, I have no problem with that idea, they sure are doing it the wrong way.

The one good thing they did with regards to workspaces was the amount of workspaces dynamic in a real way.. the rest is pretty much just wrong.

My problem mainly is that they seems to have gone in with a solution rather than a problem (no, make more people use workspaces isn't a good problem, it is, probably, a fairly good means of torture but not a problem). Doing that in any situation is plain wrong.

To me workspaces should only be used to enhance things such as work separation. Each could even provide it's own customizable interface, akin to what something like Android offers in the form of home screens and widgets. I certainly don't use workspaces on my desktop, I never found them remotely useful, in fact I find them directly harmful to my ability to overview everything I do. However on my phone I use them rather consistently, one screen for calendar tasks, one for messages and email, one for media, the main screen for communications and time/date/alarms as well as a summary of calendar tasks.

---

### Post by vkontakte on 2010-06-04
> **gnomeuser said:**
> I certainly don't use workspaces on my desktop, I never found them remotely useful, in fact I find them directly harmful to my ability to overview everything I do. However on my phone I use them rather consistently, one screen for calendar tasks, one for messages and email, one for media, the main screen for communications and time/date/alarms as well as a summary of calendar tasks.
Well, I do. But gnome-shell workspaces are just annoying. For me they are very static: I know where my apps are to get them quickly. Gnome-shell suppose workspaces are very dynamic. I don't need this! I'm very doubt anyone needs this. Most people don't use workspaces at all, most people who use workspaces do this "statically". So, gnome-shell is just like application indicators: first they invented a problem, then their solution make the problem appear in the reality, not just in their minds.

---

### Post by zekopeko on 2010-06-04
> **gnomeuser said:**
> It's suckage is sided 3.

First it is poorly reasoned, it is to me designed to bring the way traditional hackers have been productive using desktops for years to the user rather than actually improving the experience. There is nothing new in gnome-shell except a fetish like delight in workspaces. Looking at their demos and hearing them talk every time they mention "then open another workspace" I have to stop myself from screaming "Why? What is your reasoning?, why would the user do that? why? why? why?".

Instead of actually doing something to address the problems we have, we ensure that they will scale their badness according to how many workspaces you can also control at once. It seems to me that they went in with the solution being workspaces and tried to construct a problem around that.

Just to demonstrate how badly they defined their concept of workspace centric shell: on one of the first pages created for GS on Gnome Live they mentioned the number of workspaces various distros are shipping by default, as if that is reflective of actual usage.

You really hit the nail on the head. They are trying to create a shiny "for hackers" desktop.

> Secondly, Javascript why? It's slow, has a history of insecurity and being defacto non-standardized and.. it's frikkin javascript. And because it's frikkin javascript there also somehow arose the need to reimplement everything. Also why is it seen as a plus that javascript is familiar to web developers, because there are lots of them? Another thing is the specific choice that annoys me, since javascript isn't standardized, one cannot just replace the toolings underneath meaning because the g-s developers like the gecko based flavor they use that, and other parts of gnome (gnome-games) uses the webkit flavored Seed. Now we depend on two separate tools for the same job and the g-s guys really didn't see that as a problem. Finally I don't find Javascript readable but that part is just personal preference.

Didn't know about the JS situation. That is just stupid if one of their main arguments is "web developers use JS and there are a lot of them".

> Finally, it doesn't introduce anything significantly better. It's just a worse way to do the exact thing we do today. There is no boldness in GNOME 3, no long term vision. They didn't even have the guts to actually depend on well established technologies like Tracker. It is still basically a computer like we have used them since pixels first graced our screens. True innovation isn't impossible, look to MeeGo, Android, Unity. It's also on this front not because they lacked interesting interaction concepts to be inspired by, some even very detailed and well thoughtout.

I totally agree with you on the lack of long term vision. Tracker and Zeitgeist could have easily propelled the platform into the 21st century.

> On top of this no migration path is considered for the applet experience. Instead one can extend the shell itself.. but only using in-process javascript which sounds both limiting and daft.

There is no migration path for applets. Heck there isn't even a widget overlay or anything similar. We are still going to depend on third party solutions for that one.

> In adopting gnome-shell I also think GNOME went in the wrong direction. We had a chance to define a core set of functionality with different UI experiences depending on the deployment.. a bit like MeeGo is doing now (though MeeGo are wrong and doomed for other reasons this they got right). Instead we have one experience available and we lost much reuse and coordination for Linux everywhere. It's a limiting view that murders innovation and makes us miss markets as well as marketshare.

Completely agree on the [core + UI per form factor]. Using the same core tech on various platforms is a huge plus but I don't want the same UI if I'm working on a 24" inch screen or a 6" one.

---

### Post by zombiepig on 2010-06-04
> **gnomeuser said:**
> 
(though MeeGo are wrong and doomed for other reasons this they got right). 

Hey gnomeuser - I'm interested to hear your opinions behind this comment.

---

### Post by gnomeuser on 2010-06-04
> **zombiepig said:**
> Hey gnomeuser - I'm interested to hear your opinions behind this comment.

I am hopefully about MeeGo, I own an N900 which runs Maemo and my netbook currently runs MeeGo 1.0. It has lots of potential sadly they have elected to target the exact same markets as Google has with Android and ChromeOS. 

They are not going to beat Android. Android is a fairly mature platform already, it has been revved a couple of times. Functionality continues to grow. Android is developed in a documented API with a modern language (Java). MeeGo in return has just thrown away much of the platform API they gathered in Maemo and Moblin in favor of a longterm QT vision. They have nice technology underneath but they aren't using it, they sadly don't have the number one technology that makes Android great - cloud account storage.

I don't believe MeeGo can win an arms race with Android. They made multiple choices that positioned them poorly to do so. Yet every single target they outline is also an Android or a ChromeOS target: phones, tablets, netbooks, tvs, gps.

I see lots of potential for MeeGo but it's to little, to late and done using last centuries tools.

---

### Post by cabez0n on 2010-06-07
> **vkontakte said:**
> Well, I do. But gnome-shell workspaces are just annoying. For me they are very static: I know where my apps are to get them quickly. Gnome-shell suppose workspaces are very dynamic. I don't need this! I'm very doubt anyone needs this. Most people don't use workspaces at all, most people who use workspaces do this "statically". So, gnome-shell is just like application indicators: first they invented a problem, then their solution make the problem appear in the reality, not just in their minds.

I really agree with you point. I also give workspaces a good use, and I find myself jailed in enviromentos with just one Workspace (such as Windows)
I also tend to separate the apps i run on each workspace, for instance I always have the mail app and 4th workspace. 

I always use the Browser on the first and Eclipse on the second to fastly preview my changes on a webapp on teh first desktop. 
I constantly use workspace switching and arranging and couldn't work without them. 

I find that using various workspaces makes me get things done faster instead of spending time arranging windows on the screen...

Also don't mind the idea of dinamically adding workspaces, is just that I wouldn't use (...yet).

---

### Post by ranch hand on 2010-06-07
Yup, I set mine for 6 and generally use them all.  Each dedicated to one thing.

When I did try GS I found it easier to just use 1 and have everything piled on there in a mess that you have to alt tab around in all the f ing time.

The panels is where I will be staying for the time being.  GS, if it ever takes the place of what we are using now completely, will have me using Lubuntu in a hurry.

---

### Post by seeker5528 on 2010-06-07
Personally, I think the dynamic handling of workspaces is one of the good things about Gnome Shell. Why have extra desktops hanging around that your not actually using?
 
Yes, initially it's looking like there will be some limitations, but it seems there are some ideas floating around out there to add a task based element to it.

I'm sure I remember something about being able to create launchers that could launch an application on a workspace by workspace name, but at the moment I'm not finding it, but this 'desktop folder'/project idea sounds interesting.....

[http://live.gnome.org/GnomeShell/DesignerPlayground/MultiDesktop](http://live.gnome.org/GnomeShell/DesignerPlayground/MultiDesktop)

The biggest thing I have against Gnome-Shell is stemming mainly from the fact that they did it as a plug-in to Mutter instead of as a seperate entity.

I don't understand the logic of tying the desktop to a specific Window manager instead of letting the Window manager handle window FX (wobbly windows and what not) and let the desktop stuff do their FX in a window manager independent way.

Docky and some of the other things the require compositing don't care what is providing it, just that it is enabled. Why should it be any different for the desktop stuff?

If it was independent, then you could run your window manager of choice, then just add gnome-shell to the list of things to autostart, in the same way that you can run you window manager of choice and add plasma-desktop to your list of things to autostart.

Later, Seeker

---

