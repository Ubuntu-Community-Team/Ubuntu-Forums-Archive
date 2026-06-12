---
title: "Unity Q&amp;A Updated 12/30/2010"
date: 2010-11-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cariboo on 2010-11-01
There have been a lot of questions about Unity since the announcement last week. I'll try to answer as many questions as possible in this post.


**Is Ubuntu getting rid of GNOME**

 - Unity is a shell for gnome, just like gnome-shell. Ubuntu is still a gnome platform, Natty will ship with all the components needed so that gnome applications will run out of the box. All the gnome apps you use every day will still be in the repositories. The only change will be that Unity is the default shell. ubuntu is not forking or moving away from gnome, jus using a different desktop environment

**Will Unity run on my system **

- If your graphics hardware supporrts 3D, Unity should run with no problems. If your graphics adapter doesn't support 3D, the desktop will fall back to the 2 panel desktop currently used on previous versions.

**Unity runs poorly on my system**

 - performance problems will be resolved by changing the Unity backend from clutter/mutter to compiz. In demos on hardware that was having problems, performance has improved greatly.

**When will we see Unity packages in the repository**

 - We should start seeing packages land in the repositories around the 25th of November so that they can be available for alpha 1. There will be a Maverick ppa for those that haven't upgraded to Natty.

**Will the Unity launcher auto-hide**

 - There will be an auto-hide option, to keep up with the status, keep an eye on bug #639814

**New**  Autohide is now available by starting CompizConfig Settings Manager, and clicking on the Unity icon, you should see a choice to Autohide Launcher and Float Launcher

**Will Unity work on multi-monitor systems**

 - from personal experience it does, but it is hardware dependent, and pretty basic. Subscribe to bug# 661450 to keep up with the changes.

**Will Unity use the global menu**

 - Yes the desktop version of Unity will use the global menu by default.

**How do I add Programs to the Unity launcher?**

 - The option is there just not obvious. With the program you want to stay in the launcher open, right click its icon in the launcher and select 'Keep in Launcher'

**Will there be a difference between Unity &#8220;Desktop&#8221; and Unity &#8220;Netbook&#8221; interface?**

 - Unity will be the same code in desktop and netbook, but some configurable defaults will vary between the two, like whether or not applications are started maximised by default, and whether or not the Launcher is locked in view by default.

**How do I start a second instance of a program from Unity's launcher?**

 - At the moment, the only possibility to start a second instance, is using the Applications view, in the Ubuntu logo at the top.

**Will there be possibility in Unity to change default file manager?** 

- You can already change the default file manager in GNOME, although the setting is hidden. Open gconf-editor using a terminal, then you then need to edit the /desktop/gnome/applications/component_viewer/exec key to the command for the new file manager.

**Will it be possible to run unity compiz in virtual box or another virtual machine?**

 - Unfortunately up to today I have not seen any reports of running Unity in Virtual Box successfully. The virtual 3D function provided by VBox seems not to be accepted as a valid driver by Unity/Compiz. Hopefully this will change in future release of VBox as developers need a running test-system to adapt their software to the major changes with 11.04.

**Update** With the release of Virtualbox 4.0, Unity now works in a vm. 

**Windows Manger/Compiz not repsonding**

 - This is a bug, I have the same problem on all five of the installations I have running

**No panels on intial startup**

 - To solve this problem, pres Ctrl-Alt-T to start a terminal, then type **gnome-panel &** to start the panels, **Note:** If you close the terminal the panels will disappear. Once you have installed the drivers needed for 3D you shouldn't have to do this anymore

**Pressing enter at the login screen doesn't work**

- This work around works for me, press tab first, then enter.


I'll add more questions and answers as I run into them

---

### Post by kansasnoob on 2010-11-02
> Will Unity run on my system - If your graphics hardware supporrts 3D, Unity should run with no problems. If your graphics adapter doesn't support 3D, the desktop will fall back to the 2 panel desktop currently used on previous versions.

That's good to know because I maintain about 30 machines with VIA UniChrome P4M800 chipsets and 3D is not well supported.

Due to poor visual acuity I always revert to no effects anyway, even with my Intel i945, so I'm wondering what option will be best for me.

No worries, both 10.04 and 10.10 work great for me so I have tons of time to figure it out :)

---

### Post by cariboo on 2010-11-02
Improving accessibility is one of the goals of this release. High and low contrast themes will be available. I don't know if they help with your particular vision problem, but it will be helpful to some people.

---

### Post by teh603 on 2010-11-03
Does this affect KDE users at all?

---

### Post by cariboo on 2010-11-03
Unity and KDE are two separate projects, that have nothing to do with each other.

You can of course still run KDE programs in Unity and gnome programs on KDE.

---

### Post by Writh on 2010-11-03
I think he meant to ask if Kubuntu will adopt a netbook-centric UI by default, too, or will they stick with the basic KDE desktop.

---

### Post by teh603 on 2010-11-04
> **Writh said:**
> I think he meant to ask if Kubuntu will adopt a netbook-centric UI by default, too, or will they stick with the basic KDE desktop.Yes, exactly. I've never seen any reason why we should have a PDA-style interface thrust upon us, which is why I refuse to do anything with NBR or Moblin. I'd rather not see the desktop editions be forced to look like a child's toy computer, like NBR users are.

---

### Post by cariboo on 2010-11-04
As far as I know Kubuntu will stay as it is. As I stated previously, they are 2 separate projects, with very little if any crossover.

---

### Post by VMC on 2010-11-04
There's still a lot of confusion about Unity and its role. I got a "Howto Geek" poll about Unity vs Gnome. It should be about Gnome Shell vs Unity.

It appears folks think Ubuntu is abandoning Gnome, and that's not the case.

---

### Post by cariboo on 2010-11-04
I have to agree, when it was announced that gnome-shell would be the default desktop for gnome 3, there was talk of forking gnome, and now the same talk is going around concerning Unity, only now it's about forking Ubuntu.

We try to keep the users informed, but there always seems to be someone that hasn't gotten the news yet, and of course it's always easier to create another post/thread, than it is to check things out for themselves.

---

### Post by ndefontenay on 2010-11-06
The world clock that's present in the gnome 2D desktop has disappeared in Unity.

If Unity is meant for netbooks, and netbooks meant for mobile people, then the world clock should be present in Unity as well.

I've lived in a few countries, I got friends and family around the world. Checking the time before I give a call to make sure I don't wake up someone at 04:00 am is pretty useful. Changing the clock with just a "set" button when I move to another place is pretty cool as well.

Any chance this will go into Unity as well? I know there's a gworldclock app (using it right now) but it's not quite the same.

---

### Post by Framli on 2010-11-06
Here are the specs for indicator-datetime, the clock in Unity :
[https://wiki.ubuntu.com/TimeAndDate](https://wiki.ubuntu.com/TimeAndDate)

Mock-up for the menu :
[IMG]https://wiki.ubuntu.com/TimeAndDate?action=AttachFile&do=get&target=clock-menu.jpg[/IMG]

---

### Post by cariboo on 2010-11-06
Due to the shortened development time during the last cycle there were quite a few things that didn't make it into Unity, a proper date/time applet was one of them.

---

### Post by rajeev1204 on 2010-11-08
I read that Unity is for desktop environment also and not just netbooks.

Wow, looks nice and iam excited now. Had no idea even desktops will be using unity in 11.04.

Is it coming with alpha 1 ?

---

### Post by cariboo on 2010-11-09
There should be a ppa showing up in the next week or two, and It should be showing up in the repositories around the 25th of November.

---

### Post by forcecore on 2010-11-11
Developers developers developers... please make sure that unity can run on 2D mode as well because some occasions 2D is better if 3D fails or causes errors, like Metacity had.

---

### Post by cariboo on 2010-11-11
Unity will not run in 2D mode because it uses compiz for a windows manager. If your system is not capable of running 3D it will install the gnome desktop in place of Unity. You will also be able to install gnome-desktop after the initial installation.

---

### Post by kahping on 2010-11-13
> **cariboo907 said:**
> Unity will not run in 2D mode because it uses compiz for a windows manager. If your system is not capable of running 3D it will install the gnome desktop in place of Unity. You will also be able to install gnome-desktop after the initial installation.

"Install"? I thought it will be installed regardless of 3D support on the machine? If Unity can't run, then 2D mode will be used instead... or, have I been misunderstanding the recent news?

---

### Post by cariboo on 2010-11-13
From everything I've seen so far, if your system isn't capable of doing 3D, Unity won''t be installed. That is more than likely subject to change.

---

### Post by Bou on 2010-11-14
> **cariboo907 said:**
> From everything I've seen so far, if your system isn't capable of doing 3D, Unity won''t be installed. That is more than likely subject to change.

So, what would happen if the computer doesn't support 3d out of the box, but it does after installing the drivers?

---

### Post by cariboo on 2010-11-14
> **Bou said:**
> So, what would happen if the computer doesn't support 3d out of the box, but it does after installing the drivers?

I haven't been able to find a solid answer yet. The nouveau drivers will do 3D with  libgl1-mesa-dri-experimental installed, but from personal experience it is kind of buggy so far.

---

### Post by dext on 2010-11-15
there is no real 3D yet with the Opensource Nvidia driver. [http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/) **Any 3D functionality that might exist is still unsupported. Do not ask for instructions to try it. But you can read GalliumHowto in case you are brave enough. **

---

### Post by cariboo on 2010-11-15
> **dext said:**
> there is no real 3D yet with the Opensource Nvidia driver. [http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/) **Any 3D functionality that might exist is still unsupported. Do not ask for instructions to try it. But you can read GalliumHowto in case you are brave enough. **

I know from personal experience that 3D/compisiting works using  libgl1-mesa-dri-experimental, note the name of the library. I'd suggest you give it a try yourself. After all we're here to test out new stuff. :)

---

### Post by dext on 2010-11-15
> **cariboo907 said:**
> I know from personal experience that 3D/compisiting works using  libgl1-mesa-dri-experimental, note the name of the library. I'd suggest you give it a try yourself. After all we're here to test out new stuff. :)its not supported as of yet. the only real 3D your gonna get is from installing Blob drivers ATI/Nvidia even the opeensource drivers dont work for me in Fedora14 when i try an load GS

the opensource drivers only support some 3D. not all

---

### Post by Bou on 2010-11-15
> **dext said:**
> its not supported as of yet. the only real 3D your gonna get is from installing Blob drivers ATI/Nvidia even the opeensource drivers dont work for me in Fedora14 when i try an load GS

the opensource drivers only support some 3D. not all

They work fine for the 3D desktop experience, though. At least that has been my experience: no bugs, smoother effects than ever. Should be enough for Unity but, then again, they're not gonna be installed by default so the question stands. Or are they?

---

### Post by VMC on 2010-11-15
> **cariboo907 said:**
> 
[list]
[*] **Will Unity run on my system** - If your graphics hardware supporrts 3D, Unity should run with no problems. If your graphics adapter doesn't support 3D, the desktop will fall back to the 2 panel desktop currently used on previous versions[/list]



How can I know it my video supports 3D? Is there a test somewhere. I checked with nvidia and can't determine if it does:

```
GeForce 6150SE nForce 430
```.

---

### Post by dext on 2010-11-15
> **Bou said:**
> They work fine for the 3D desktop experience, though. At least that has been my experience: no bugs, smoother effects than ever. Should be enough for Unity but, then again, they're not gonna be installed by default so the question stands. Or are they?

they dont work for Everyone, my Nvidia card is pretty up to date. the opensource drivers dont work for me in F14 when i try to Open GS. i expect the same to happen to users with Unity, i still see a fair amount using the blob drivers than the opensource ones. i wonder why? plus the opensource Nvidia driver does not have any Power Management to it yet, so it would be a waste of time making the opensource drivers default install for 11.04

---

### Post by cariboo on 2010-11-15
> **VMC said:**
> How can I know it my video supports 3D? Is there a test somewhere. I checked with nvidia and can't determine if it does:

```
GeForce 6150SE nForce 430
```.

I've got a couple of motherboards with the same graphics chipset. The last time I tried one of them without a graphics card, I have to start in nomodeset, but once at the desktop nvidia-current was installed (back in Lucid development) and ran with no problems.

---

### Post by cariboo on 2010-11-15
On different systems I have a 6600GT,  8400GS,  9400GT and  210GT, I've run nouveau drivers on all of the, with the experimental library, and only had problems with the 210GT where the system went into a hard lockup once a day.

---

### Post by mixmaster on 2010-11-16
OK, this may sound luddite but ...

I am quite happy with the existing desktop, which I run with all desktop effects disabled.  I know exactly where everything is and what everything does.  I don't want to have to learn a new shell so I really don't want Unity or gnome-shell.  Will I be able to keep the current desktop on Natty or should I start migrating back to Xubuntu now?

---

### Post by cariboo on 2010-11-16
Using Linux is about choice, you won't be forced to use Unity or Gnome-shell, you will still be able to use the desktop you use now. Eventually Gnome 2.X will no longer be supported, so change is inevitable.

---

### Post by Yes_It's_Me on 2010-11-17
> **kansasnoob said:**
> That's good to know because I maintain about 30 machines with VIA UniChrome P4M800 chipsets and 3D is not well supported.

Due to poor visual acuity I always revert to no effects anyway, even with my Intel i945, so I'm wondering what option will be best for me.

No worries, both 10.04 and 10.10 work great for me so I have tons of time to figure it out :)

I don't know if this may help but I have very poor vision and one thing that is absolutely awesome that I could not live without is the compiz enhanced zoom plugin (that's installed by default but not enabled). Whoever wrote that originally deserves a beer.

---

### Post by cariboo on 2010-11-23
Yes the global menu will be implemented in Unity, you can see parts of it there already. There is a lot of work for the devs to do, it isn't a simple process. They are trying to get as much done as possible for the Alpha 1 release.

---

### Post by Finalfantasykid on 2010-11-25
Will there be an option to disable the global menu?  I prefer having the menus belong to their respective windows.

---

### Post by cariboo on 2010-11-25
You can remove [indicator-appmenu]("http://packages.ubuntu.com/natty/indicator-appmenu") to get the old-style normal menus back.

---

### Post by geirknappen on 2010-11-26
What pros and cons compared to gnome, kde?
Will it be possible to switch titlebar comtrols from left to rigth, maybe an option to have no titlebar at all?

---

### Post by cariboo on 2010-11-27
> **geirknappen said:**
> What pros and cons compared to gnome, kde?
Will it be possible to switch titlebar comtrols from left to rigth, maybe an option to have no titlebar at all?

I'm not sure what you mean, Unity is a shell on top of gnome, all your favorite gnome applications will still run, you'll be able to run kde apps in gnome just like you do now.

If they devs stick to the way Unity works in the UNE, the top panel will be the same as the title bar now. the global menu will be hard coded with the buttons on the left.

---

### Post by cpatrick08 on 2010-12-01
when i go to the login screen i can select a session called ubuntu  classic desktop which looks like the previous versions of ubuntu with  the global menu

---

### Post by cariboo on 2010-12-01
All choosing the Classic Desktop does is turn of the Compiz Unity plugin, you should get the standard gnome-panels and menus though.

---

### Post by geirknappen on 2010-12-01
> **cariboo907 said:**
> I'm not sure what you mean, Unity is a shell on top of gnome, all your favorite gnome applications will still run, you'll be able to run kde apps in gnome just like you do now.


So Unity is like gnome pluss more? When I read about Unity on the Internet, I interpret it as something that will be competition to gnome and kde.

---

### Post by terry_gardener on 2010-12-01
> **geirknappen said:**
> So Unity is like gnome pluss more? When I read about Unity on the Internet, I interpret it as something that will be competition to gnome and kde.

correct. unity is just a shell on top of gnome and still uses gnome components,

[http://www.youtube.com/watch?v=2c9Xbvss-tw](http://www.youtube.com/watch?v=2c9Xbvss-tw)

---

### Post by cariboo on 2010-12-01
Unfortunately, it is easier to find mis-information, than it it is to find the truth. People have their own agendas, and stick with them even when they are provided the facts to dispute their ideas.

---

### Post by cariboo on 2010-12-01
Sorry, I won't do it again. :) :) :)

---

### Post by Elfy on 2010-12-02
I'm watching you ;)

---

### Post by ratcheer on 2010-12-03
Can someone point me to some usage info (docs, tutorials, etc) on the latest incarnations of Unity DE? I am having trouble understanding how everything fits together and is to be used.

For example, Just today I was told to look for some application menus in the top panel instead of in the top of the application window. LOL, I never saw them or thought to look for them there.

Also, is there a way to add new launchers to the left sidebar instead of the main desktop window? And, how can I get the correct icon for an app launcher, instead of the generic board on a spring icon?

I am perfectly willing to read up on this stuff for myself, but I have looked all over and don't know where to find it.

Thanks,
Tim

---

### Post by cariboo on 2010-12-03
> **ratcheer said:**
> Can someone point me to some usage info (docs, tutorials, etc) on the latest incarnations of Unity DE? I am having trouble understanding how everything fits together and is to be used.

For example, Just today I was told to look for some application menus in the top panel instead of in the top of the application window. LOL, I never saw them or thought to look for them there.

Also, is there a way to add new launchers to the left sidebar instead of the main desktop window? And, how can I get the correct icon for an app launcher, instead of the generic board on a spring icon?

I am perfectly willing to read up on this stuff for myself, but I have looked all over and don't know where to find it.

Thanks,
Tim

There isn't any documentation for Unity at this time, except what you can glean from this sub-forum. The only thing I can suggest is to keep an eye on the Unity technical thread.

You can create a launcher in the panel by starting an application and then right-click the icon and select Pin to Launcher. See the screen shot

---

### Post by Guitar John on 2010-12-03
> **cariboo907 said:**
> Unity will not run in 2D mode because it uses compiz for a windows manager. If your system is not capable of running 3D it will install the gnome desktop in place of Unity. You will also be able to install gnome-desktop after the initial installation.

If my system supports 3D but I just prefer the old style desktop, is gnome-desktop the option for me then?

---

### Post by cariboo on 2010-12-03
You can select the Classic Desktop from the login screen, which gives you the two panel desktop. You should be aware that compiz is a bit buggy though.

---

### Post by cecilpierce on 2010-12-03
I can't get rid of the gnome-panel. I tried pkill and it goes away for a few seconds and comes back ???

---

### Post by ratcheer on 2010-12-03
> **cariboo907 said:**
> There isn't any documentation for Unity at this time, except what you can glean from this sub-forum. The only thing I can suggest is to keep an eye on the Unity technical thread.

You can create a launcher in the panel by starting an application and then right-click the icon and select Pin to Launcher. See the screen shot

Thanks very much.

Tim

---

### Post by kyleabaker on 2010-12-04
> **cariboo907 said:**
> If they devs stick to the way Unity works in the UNE, the top panel will be the same as the title bar now. the global menu will be hard coded with the buttons on the left.

So Unity DE will be merging the application title bars into the top panel like in the netbook edition? Or did I misunderstand that? I like the application close buttons where they are in the title bar.

---

### Post by cariboo on 2010-12-04
I can't find any exact information on what the menu will be like, but it looks like there won't be a separate versions for the netbook and the desktop, so for now we can assume that the global menu will be similar to what is available on the Maverick netbook edition.

---

### Post by kyleabaker on 2010-12-06
> **cariboo907 said:**
> I can't find any exact information on what the menu will be like, but it looks like there won't be a separate versions for the netbook and the desktop, so for now we can assume that the global menu will be similar to what is available on the Maverick netbook edition.

Just to follow up to this..
[Windows controls will show in Unity panel for maximised]("http://www.omgubuntu.co.uk/2010/12/windows-controls-will-show-in-unity-panel-for-maximised-apps/")

---

### Post by cariboo on 2010-12-06
Thanks for the link kylebaker, I usually don't pay to much attention to OMGUbuntu, because they have their own agenda and often misquote, or only show specific parts of a quote to further it.

---

### Post by loukingjr on 2010-12-07
Please bare with me...

I am running both Ubuntu 11.04 Alpha and Oz Unity 1.0 Debut in VirtualBox. The Oz version seem to have both a 3D and a 2D version of Unity available. I can't as you mentioned earlier log into the 3D environment in either version. However, I can log into the 2D version of Oz with Compiz running. Will you have a 2D version of Unity also?

thanks.

I'm including a couple of screenshots...

[IMG]http://lh5.ggpht.com/_sA9c938TUEU/TPzrrV9_klI/AAAAAAAAEx8/L5vpEjzZ0kg/s640/screenshot_01.jpg[/IMG][IMG]http://lh6.ggpht.com/_sA9c938TUEU/TPlPy-uF2VI/AAAAAAAAEuw/ZTmHvD0fDME/s640/screenshot_01.jpg[/IMG]

---

### Post by Framli on 2010-12-07
"Oz Unity" is mostly a re-themed 10.04 UNR and as very few in common with the actual Unity that has been introduced in 10.10 UNR or the one that is being tested around here and will land in 11.04. Unity is and will be 3D only.

---

### Post by loukingjr on 2010-12-07
> **Framli said:**
> "Oz Unity" is mostly a re-themed 10.04 UNR and as very few in common with the actual Unity that has been introduced in 10.10 UNR or the one that is being tested around here and will land in 11.04. Unity is and will be 3D only.

okay thanks. looks like I'm stuck for awhile. not sure VirtualBox has any plans to support Unity 3D. Not from the responses from their moderators.

I guess I could go back to triple-booting my Mac :lolflag:

---

### Post by geirknappen on 2010-12-08
> **terry_gardener said:**
> correct. unity is just a shell on top of gnome and still uses gnome components,

[http://www.youtube.com/watch?v=2c9Xbvss-tw](http://www.youtube.com/watch?v=2c9Xbvss-tw)

Nice to know. Whatever it is, when is available... All I really care about is that it isn't regression in some way: too many bugs, something like that.

---

### Post by VeeDubb on 2010-12-09
> **geirknappen said:**
> Nice to know. Whatever it is, when is available... All I really care about is that it isn't regression in some way: too many bugs, something like that.

If Unity for netbook edition 10.10 was any indication, it will not be any level of regression by the time we get to stable release.  At the moment, because of the early development state, it's a huge regression but improving quickly.

Most importantly, because it is a shell that sits on top of gnome, it's use is 100% optional.  It will be the default in the same way that 2 gnome panels is currently the default.  It will show up the first time you log into a new user account, and never show up again if you chose to disable it.

---

### Post by MandiriPatnaBihar on 2010-12-12
First of all, I simply loved the screen shots of Unity for Natty (See post number #57 in this thread by lockingjr) and would love to have it on my system. However there may be a bump ahead for me (guessed after reading the other 60 posts of this thread).

Most important background for the discussion is that ** Unity needs a hardware accelerated 3D Graphics ** I am a newbee to this 3D thing!

(1) How do I know if my system has the minimum needed for the Unity to start? I mean I am sure I don't have a dedicated Graphics/Video Card but only an inbuilt one that comes with the motherboard. If "glxinfo | grep rendering" says "Yes", then does it mean, I have what is needed?

(2) I have an Intel i845GVSR motherboard and no external/dedicated ATI/Nvidia or whatever card. The Natty-alpha-1 installation was a breeze and successful but the Unity could not be started. What can I do to get the Unity started?

(3) Will Unity ever work (say in the final NN 11.04 release) on my system which is old [i845GV - 512MB Ram - 80GB] without a dedicated graphics card? Will boosting the RAM to 1GB be of any use?

Thanks in advance

---

### Post by go7Ul1ai on 2010-12-12
> **MandiriPatnaBihar said:**
> First of all, I simply loved the screen shots of Unity for Natty (See post number #57 in this thread by lockingjr) and would love to have it on my system.


The screenshots you're talking about isn't the Unity interface, rather the old netbook interface from 10.04.

---

### Post by kyleabaker on 2010-12-17
> **lee.jarratt said:**
> The screenshots you're talking about isn't the Unity interface, rather the old netbook interface from 10.04.

The old Netbook interface makes me gag. The current Unity interface looks nice in my opinion, but its not a breath-taker like Windows 7 or Mac OS X Dock. Still some gui-fication hacking needed to make it really "wow" us/me. :-k

---

### Post by jerrylamos on 2010-12-19
> **kyleabaker said:**
> The old Netbook interface makes me gag. The current Unity interface looks nice in my opinion, but its not a breath-taker like Windows 7 or Mac OS X Dock. Still some gui-fication hacking needed to make it really "wow" us/me. :-k

To each his/her own.

With "Unity", "full screen applications" aren't on Alpha 1.  An inch stripe on the left of the screen is lost to hieroglyphics which have nothing to do with using the internet or open office or digital photography or any other application I use.  I prefer to fill up the screen with what I'm doing.

Rumor is Alpha 2 may have an "autohide" feature (more code!) so the applications overlay the unity hieroglyphics (wishful thinking?).  Tiny little Tiny Core has hieroglyphics but as soon as I fire up Firefox it gets the whole screen if I want.

To each his own, which is a stated Ubuntu theme.

Jerry

---

### Post by cariboo on 2010-12-19
Like has been said several time before, autohide is already available now, you don't need to wait for Alpha 2.

---

### Post by jerrylamos on 2010-12-22
CD Live boot choosing "classic" isn't listed on the help screens - I think it would speed up boot, aside from "Unity" being broken on IBM Thinkpad T40 ati radeon.

Also, there's an annoying message about "no 3D support" for all of the pc's that are blacklisted from Unity example myriad integrated intel video graphics.

Would there be a way to do a "poll" to see how many people are interested in booting in classic to boot faster and save extra message?

Thanks, Jerry

---

### Post by lucazade on 2010-12-22
> **jerrylamos said:**
> CD Live boot choosing "classic" isn't listed on the help screens - I think it would speed up boot, aside from "Unity" being broken on IBM Thinkpad T40 ati radeon.

Also, there's an annoying message about "no 3D support" for all of the pc's that are blacklisted from Unity example myriad integrated intel video graphics.

Would there be a way to do a "poll" to see how many people are interested in booting in classic to boot faster and save extra message?

Thanks, Jerry

There is no need to introduce a "classic" option to cdlive boot.. it should be handled automatically with a fallback routine for blacklisted pci.
Anyway Unity and Natty are not released so this issue will be likely fixed during release development so a poll now is not useful.

---

### Post by fernando.a.martin on 2010-12-22
I feel a bit curious about trying Unity, but just as second option, like people who have KDE and GNOME in the same system do.
When I upgraded from 10.04 to 10.10 my Gnome desktop continued exactly the same, with the same icons, wallpapers, panel, configurations and so on. I would like that when I upgrade to 11.04 my gnome desktop would continue the same as well. Will Unity mess with my desktop settings? Or will I be able to login to my current desktop appearance and configuration and login to Unity at wish?

---

### Post by lucazade on 2010-12-22
> **fernando.a.martin said:**
> I feel a bit curious about trying Unity, but just as second option, like people who have KDE and GNOME in the same system do.
When I upgraded from 10.04 to 10.10 my Gnome desktop continued exactly the same, with the same icons, wallpapers, panel, configurations and so on. I would like that when I upgrade to 11.04 my gnome desktop would continue the same as well. Will Unity mess with my desktop settings? Or will I be able to login to my current desktop appearance and configuration and login to Unity at wish?

Unity will not mess your present desktop configuration.
In Natty there are two session type you can choose at login page:
Classic edition (your current desktop appereance) and Desktop edition (Unity)
You can switch between them without problems.

---

### Post by jerrylamos on 2010-12-22
> **lucazade said:**
> Unity will not mess your present desktop configuration.
In Natty there are two session type you can choose at login page:
Classic edition (your current desktop appereance) and Desktop edition (Unity)
You can switch between them without problems.

Unity takes an inch stripe off the left side of my screen so it does mess up my screen which is full screen full of applications internet, office, picasa.  I've heard there's an extra step to "autohide" but don't know how to do it.

On install I select "automatic" since there's only one user and one account on this pc.  Then I have to log out/in and set up classic.  Better case for me would be to boot classic in the first place.  

BTW, this pc has integrated intel video graphics and Compiz is blacklisted as it has been since Intrepid.

Switching between Classic and Unity on the one of my four test PC's where Unity works, have to stop all my applications, log off and back in again, and restart applications.  Is there an easier way?

Hmmm.  I haven't noticed that "Unity" makes my applications run any better.  

Jerry

---

### Post by lucazade on 2010-12-22
> **jerrylamos said:**
> Unity takes an inch stripe off the left side of my screen so it does mess up my screen which is full screen full of applications internet, office, picasa.  I've heard there's an extra step to "autohide" but don't know how to do it.

Autohide is already implemented:

alt+f2
ccsm
unity plugin
autohide setting


> **jerrylamos said:**
> On install I select "automatic" since there's only one user and one account on this pc.  Then I have to log out/in and set up classic.  Better case for me would be to boot classic in the first place.  .

Try Natty with an alternative installation (alternative iso or minicd) at this moment.

Or during livecd switch to tty (ctrl+alt+f1)
killall nautilus
swicth back to X (ctrl+alt+f7)
right-click on desktop
create new launcher  with command "gnome-terminal"
launch new gnome-teminal icon from desktop
metacity --replace &
gnome-panel &

and you'll get a working dekstop to install Natty.


> **jerrylamos said:**
> BTW, this pc has integrated intel video graphics and Compiz is blacklisted as it has been since Intrepid.

Switching between Classic and Unity on the one of my four test PC's where Unity works, have to log off and back in again.

This should be done automatically with a fallback for known pci don't fit Unity hardware requirements.


> **jerrylamos said:**
> Hmmm.  I haven't noticed that "Unity" makes my applications run any better.  

Jerry

Maybe because Unity is still in development.

---

### Post by lucazade on 2010-12-22
Added some info in previous post to get livecd working with an Ati radeon 7500 card.
Unity is broken at the moment, no panel or other UI is visible at startup.

---

### Post by ratcheer on 2010-12-22
I just upgraded to all the latest updates, including the new kernel 2.6.37-11.

Yesterday, Unity was working fine. Now, after login, I am back to the unresponsive Unity screen. It has all the persistent icons and the top panel applets on the right, but none of them respond to mouse clicks. "compiz --replace &" fixes it.

Is this still happening to everyone else?

Tim

---

### Post by VMC on 2010-12-22
> **ratcheer said:**
> I just upgraded to all the latest updates, including the new kernel 2.6.37-11.

Yesterday, Unity was working fine. Now, after login, I am back to the unresponsive Unity screen. It has all the persistent icons and the top panel applets on the right, but none of them respond to mouse clicks. "compiz --replace &" fixes it.

Is this still happening to everyone else?

Tim

The only problem I have it the top panel of Unity doesn't respond to mouse clicks. I see it depresses the text but nothing happens. If I right-click on desktop to change background then I can use the top panel. Weird.

---

### Post by cariboo on 2010-12-22
I've noticed the same thing, if a click doesn't work, just right-click anywhere on the desktop and after that things work OK.

---

### Post by mc4man on 2010-12-22
> If I right-click on desktop to change background then I can use the top panel. Weird.

If exposing a context menu doesn't work then opening a dir. in the desktop usually will also.
This is all related to an open bug that also affects drop down menus behind windows and several other possible unity misbehaviours of various sorts. 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/690461](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/690461)

There is also turning out to be a difference between a Desktop login to unity and a Classic login to unity with the Classic login less likely atm  to have issues, either at launch or during use. (The reason for that isn't quite clear
One of several examples, off shoot of above
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/691561](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/691561)

---

### Post by VMC on 2010-12-22
> **mc4man said:**
> If exposing a context menu doesn't work then opening a dir. in the desktop usually will also.
This is all related to an open bug that also affects drop down menus behind windows and several other possible unity misbehaviours of various sorts. 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/690461](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/690461)

There is also turning out to be a difference between a Desktop login to unity and a Classic login to unity with the Classic login less likely atm  to have issues, either at launch or during use. (The reason for that isn't quite clear
One of several examples, off shoot of above
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/691561](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/691561)
Thank you for the bug report. I will have a look-see. I didn't want to create a bug yet not knowing if I was the only one with that behavior thinking it was my implementation of nvidia driver.

---

### Post by mc4man on 2010-12-22
> for the bug report (s)

Another nvidia of some interest, at least to see if it's hardware specific or not.
Atm can demonstrate here on 2 fairly different hardwares though only affecting the Desktop > unity login w/ 100% repeatability.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/692677](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/692677)

And a sort of low interest one that may be mis-named and in play elsewhere
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/692391](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/692391)

---

### Post by jerrylamos on 2010-12-23
> 
Or during livecd switch to tty (ctrl+alt+f1)
killall nautilus
switch back to X (ctrl+alt+f7)
right-click on desktop
create new launcher  with command "gnome-terminal"
launch new gnome-teminal icon from desktop
metacity --replace &
gnome-panel &

and you'll get a working desktop to install Natty.


Thanks, but doesn't work for the panel on this IBM Thinkpad T40.  The wallpaper (purple blotch) shifts down a line as if to make space for the Gnome top panel line, then the wallpaper shifts right back up again which covers any panel that gnome would have been trying to put up.

I can start firefox from the terminal session, but pretty crippled without "Applications Places System".  I don't know how to get to the login screen to log out and log back in with "classic".

Well, sometimes Compiz problems are fixed by Release Code time, sometimes not.

Thanks anyway, Jerry

---

### Post by cariboo on 2010-12-23
You can get to the login screen, by removing /etc/gdm/custom.conf

---

### Post by jerrylamos on 2010-12-23
> **cariboo907 said:**
> You can get to the login screen, by removing /etc/gdm/custom.conf
cariboo, that gets to the same login screen as Ctrl-Alt-F1.  No choice of unity or classic.

tried sudo service gdm start

which got wallpaper and cursor but still no panel.

In /etc/gdm/custom.conf there wasn't a line saying:
DefaultSession=gnome-classic
so I put that in.  

No luck yet, I think there's some other bug because the cursor switches between arrow and twirly rapidly.

I'll try tomorrows update.

Natty is running with classic panel on IBM ThinkCentre A30 intel integraded video if I do: 

#! /bin/bash
echo "See natty forum No Gnome-panel"
gconftool-2 --shutdown
rm -rf ~.gconf/apps/panel
pkill gnome-panel
exit #

on every boot.

On Compaq Presario ati radeon xpress 200 classic is running.  I have run Unity on the original Alpha 1 but haven't tried autohide on it yet so I can get full screen for applications (applications are why I run linux, besides testing).

Thanks, Jerry

---

### Post by cariboo on 2010-12-23
All removing /etc/custom.conf does is disable auto-login. If gdm isn't working properly, that is a completely different problem. You may want to re-install gdm to see if that makes a difference

---

### Post by jerrylamos on 2010-12-24
> **cariboo907 said:**
> You may want to re-install gdm to see if that makes a difference

I'm trying each daily build as it comes out, so gdm gets re-installed with everything else.

Dec 24 daily build still no panel, no Alt-F2, no Ctrl-Alt-T on the IBM Thinkpad T40 ati radeon modeset 7500. Only thing that works is Ctrl-Alt-F1 and the command line.

Oh, well, there's always Ubuntu 10.04 LTS.  And tiny core with its default autohide.

Jerry

---

### Post by cecilpierce on 2010-12-24
Any body know what happen to 'weather' in the clock applet ?

Thanks Cecil

---

### Post by cariboo on 2010-12-24
Nothing happened to it, as there never was the option. There is an new date-time indicator coming.

---

### Post by cecilpierce on 2010-12-24
> **cariboo907 said:**
> Nothing happened to it, as there never was the option. There is an new date-time indicator coming.

I guess it was just in the classic edition clock applet, thanks

---

### Post by tyroiusrtmaonm on 2010-12-27
Is there a way to add more than just programs to the launcher? Is it possible to add folders or web links?

---

### Post by avada on 2010-12-27
Hi!
Compiz has this very annoying limitation, I experience when I enable desktop effects.  If I understand correctly unity uses compiz, so it should be affected. I'm talking about the inability to switch to a different window with alt+tab when dragging an item from the current one.
There is a metacity(ubuntu) bug for it ([Bug #111939 ]("https://bugs.edge.launchpad.net/ubuntu/+source/metacity/+bug/111939") ) and its fixed in metacity an mutter. Compiz is referenced but there is no bug number for it.
Will this be fixed in Compiz/Unity for Natty?

---

### Post by jerrylamos on 2010-12-27
> **jerrylamos said:**
> Dec 24 daily build still no panel, no Alt-F2, no Ctrl-Alt-T on the IBM Thinkpad T40 ati radeon modeset 7500. Only thing that works is Ctrl-Alt-F1 and the command line.Jerry

Finally got Natty Narwhal running on CD Live and on install:  
1. On grub boot linux line add:
radeon.modeset=0 single
which boots to recovery mode menu.  Select root prompt then:
sudo nano /etc/X11/xorg.conf
Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSection
Ctrl-o
Ctrl-x
sudo service gdm start

Comes up in "classic" mode, running fine for an Alpha 1.

Still have to do the no kms (radeon.modeset=0), recovery mode, sudo service gdm start even on the 27 December build.  I check every day to see if there's been a Compiz fix.

Since Ubuntu developers know that Compiz does not work on ati radeon mobility 7500 I'd appreciate them blacklisting Compiz on this hardware just like they already blacklist Intel video graphics on two of my other test pc's. 

On the Intel video pc's Natty is running fine for me (for an Alpha 1) since the "eye candy" Unity isn't needed for any of my applications and internet.  Oh, yes, on every boot I have to get the panels running by doing 
Ctrl-Alt-t
gconftool-2 --shutdown
rm -rf ~.gconf/apps/panel
pkill gnome-panel

thanks to the Natty thread "No Gnome-panel"

Cheers, Jerry

---

### Post by castrojo on 2010-12-27
> **cecilpierce said:**
> I guess it was just in the classic edition clock applet, thanks

Check out indicator weather: [https://launchpad.net/weather-indicator](https://launchpad.net/weather-indicator)

---

### Post by bluebyt on 2010-12-28
Is it planned to change the icon of the launcher easily?

I know that you can change the icon of the launcher in usr\share\applications but this is not convenient.

Some applications like nautilus or rhythmbox if you change the icon for a png, the applications refuse to start. Also when the applications is updated you need to change the icon again.

---

### Post by jerrylamos on 2010-12-29
IBM Thinkpad T40 ati radeon mobility 7500 finally running Natty installed and CD Live.
Installed required:
sudo nano /etc/X11/xorg.conf
Section "Device"
Identifier "Configured Video Device"
Driver "radeon"
EndSection
Ctrl-o
Ctrl-x
Then booting up results wallpaper & cursor and no panels.
Right select create a launcher with command
gnome-terminal
select the gnome-terminal and enter
gnome-panel &
which gets classic mode.  Yay, something runs!
Subsequent boots the launcher may still be there, still needs to enter
gnome-panel &
Note, Alt-F2 and Ctrl-Alt-T don't work.
Driver ati doesn't work.  Driver vesa will work but I'm using radeon now.

CD Live is a bit more complicated in that the boot line required:
radeon.modeset=0 single
which turns off kms and boots to recovery mode.
Need to select root prompt and create the xorg.conf as above then
sudo service gdm start

On CD Live as downloaded the problem is xorg fails to select the radeon driver and tries to use fbdevhw which doesn't work.  I tried an 
ubuntu-bug xorg
which doesn't do any good since the gdm won't run it can't send the report, and since it is CD Live I don't know how to save the /tmp file.  Might be a way to mount another partition to save the file but I don't want to screw up the three multiboot partitions.

Jerry

---

### Post by Merk42 on 2010-12-30
What exactly is the reasoning for hiding the global menu and only making it viewable upon hover?

> **castrojo said:**
> Check out indicator weather: [https://launchpad.net/weather-indicator](https://launchpad.net/weather-indicator)Ugh, don't get me started on that useless indicator...


On topic, Unity will work as of Virtualbox 4.0, so maybe you should update that part of the OP cariboo907.

---

### Post by cariboo on 2010-12-30
> **Merk42 said:**
> What exactly is the reasoning for hiding the global menu and only making it viewable upon hover?

Ugh, don't get me started on that useless indicator...


On topic, Unity will work as of Virtualbox 4.0, so maybe you should update that part of the OP cariboo907.

Thanks Merk42, I've update the post.

---

### Post by scradock on 2011-01-02
> **Merk42 said:**
> What exactly is the reasoning for hiding the global menu and only making it viewable upon hover?



Where is the global menu? I haven't seen it yet - where does one hover?

---

### Post by cariboo on 2011-01-02
The global menu is partially here depending on the program, not all programs have been converted yet. Just hover your mouse pointer to the right of the program name. See the screenshot.

---

### Post by marrabld on 2011-01-02
I cannot find the autohide feature in CCSM, it simply isn't there.  I am using 10.10 and installed by apt-get which gives me unity 2.46.  Am I supposed to have auto-hide? or do I have to compile from source to get a later version?  (or use Natty of course)

Thanks

---

### Post by cariboo on 2011-01-02
Click on the Unity icon, an you should be take to the Unity sub-page. See the screenshots.

---

### Post by marrabld on 2011-01-02
Thanks but I don't even have that option.

---

### Post by mc4man on 2011-01-02
> **marrabld said:**
> I cannot find the autohide feature in CCSM, it simply isn't there.  **I am using 10.10 and installed by apt-get which gives me unity 2.46.**  Am I supposed to have auto-hide? or do I have to compile from source to get a later version?  (**or use Natty** of course)

Thanks

You answered your own question

---

### Post by marrabld on 2011-01-02
That answer isn't very helpful.  A straight answer would be best.  

I know I can have it if I use Natty but it is in alpha so I don't want to.  And I am not sure I am up for compiling all of the compiz stuff atm to make it work in Maverick.  

I would like to know if autohide is a feature of the version I have -- but not working for some reason. Maybe missing a compiz addon or something. OR if it is simply impossible for the version I have.

Furthermore, if it is not a feature, is it possible to gain this feature in 10.10 with out compiling.   Maybe a PPA or .deb ?

Thanks

---

### Post by cariboo on 2011-01-03
The answer to both your questions is no, there isn't any devlopment work being done on the Maverick version, and there never was autohide functionality. 

I guess we could consider the Maverick version of Unity to be an orphan. :(

---

### Post by marrabld on 2011-01-03
Great, thanks.

That is a shame.  I quite like it and would use it if it had auto0hide.  Looks like I'll have to be more patient.

Cheers

---

### Post by scradock on 2011-01-04
> **cariboo907 said:**
> The global menu is partially here depending on the program, not all programs have been converted yet. Just hover your mouse pointer to the right of the program name. See the screenshot.

Ah, that's what it is. I was (naively) thinking that a global menu would be a way to access all and any programs and settings that are not in the lefthand task bar, rather like the (Applications | Places | System) menu in Classic Desktop, or the Windows Start button.

I have to say that until that shows up in some way I shall continue to run a hybrid desktop, with a (short) Gnome Panel containing the old version on top of the Unity display. In which case, why bother with Unity?

I do hope that someone is working on getting past the "Open /usr/share/applications folder" kludge........

---

### Post by lin73 on 2011-01-06
Well, my question about "Unity" is: What makes it different from another dock application like docky?
From a technical pov, my question my be irrelevant, I don't know, but in terms of usability what's exactly the difference. I currently have docky installed, and it seems to do the same thing as the unity sidebar is expected to do, except that I have docky in the bottom of the screen with the autohide option. With all the fuss about unity, and the difference with the new gnome shell, there seems to be something more than a simple dock issue, but I still can't figure out what that is.

---

### Post by Merk42 on 2011-01-06
> **lin73 said:**
> Well, my question about "Unity" is: What makes it different from another dock application like docky?
From a technical pov, my question my be irrelevant, I don't know, but in terms of usability what's exactly the difference. I currently have docky installed, and it seems to do the same thing as the unity sidebar is expected to do, except that I have docky in the bottom of the screen with the autohide option. With all the fuss about unity, and the difference with the new gnome shell, there seems to be something more than a simple dock issue, but I still can't figure out what that is.

It's not just a dock, it's also the top bar.
Even the 'dock' on the left hand side does behave differently than other docks out there.

If you haven't used Unity and have a strong enough computer, you can install Natty in Virtualbox 4.0 and try it out that way.

When comparing with GNOME Shell, one other difference is GNOME Shell's notifications are interactive, Unity's not so.

---

### Post by ratcheer on 2011-01-07
Here is an excellent article on Unity that I found via Ubuntu News:

[http://www.h-online.com/open/features/Ubuntu-and-the-price-of-Unity-1156110.html](http://www.h-online.com/open/features/Ubuntu-and-the-price-of-Unity-1156110.html)

Tim

---

### Post by jerrylamos on 2011-01-07
> **ratcheer said:**
> Here is an excellent article on Unity that I found via Ubuntu News:

[http://www.h-online.com/open/features/Ubuntu-and-the-price-of-Unity-1156110.html](http://www.h-online.com/open/features/Ubuntu-and-the-price-of-Unity-1156110.html)

Tim

Thanks for the link to: "Ubuntu and the price of Unity"

What a price!  

Unity runs on one of my four test pc's.  That's a 25% success rate at admittedly Alpha 1.

This IBM Thinkpad T40 may or may not ever run Unity since Unity & Compiz are coded to do something the ati radeon mobility 7500 will never do.  Launchpad bug written, no action.

Two other pc's have have integrated intel video graphics.  Compiz broke on these on Intrepid and was blacklisted.

Now Microsoft wanted to blur the division between the internet and the local pc, which LET IN LEGIONS OF HACKERS!  They have yet to plug in all the "Windows" they opened to the internet with it's nefarious hackers.

In the quoted article: "A well designed tool or interface is about simplicity, responsiveness, and a minimum of keystrokes."  So far, trying Unity on my one pc that will run it, I can reach more function that I do with less keystrokes and less mouse pointers with "classic".

Now if you want to have "fancy eye candy" to attract "pure Newbies" on the "latest and fastest 3D" pc's, go ahead.

My problem with the Developer's is the default is Unity whether Unity will run or not, with no ability to select "classic" on boot that I've found.  Oh, select "classic" on login?  In the interests of fast boot and less keystrokes I do automatic login.  And CD Live also does automatic login to "Unity" whether it will run or not.  Follows much struggle with command lines to get a panel up far enough to log out and then select "classic".  No Ubuntu boot option to "classic" except of course Lucid 10.04 LTS.  For a limited time.  Or another distro.

Oh, well, there's always Ubuntu 10.04 LTS.  For a while.

Jerry

---

### Post by amano on 2011-01-09
> **jerrylamos said:**
> 

Oh, well, there's always Ubuntu 10.04 LTS.  For a while.

Jerry

There will be the Classic Gnome fallback as well. Ignoring that is spreading FUD.

---

### Post by Harry33 on 2011-01-10
> **amano said:**
> There will be the Classic Gnome fallback as well. Ignoring that is spreading FUD.

Well Classic-Gnome or Gnome-Panel will be there for Natty. But at the same time it should be noted that Gnome-Panel is not developed any further by Gnome.org. And it will be eventually dropped.
That might happen with Natty+1, who knows.

---

### Post by NickyJ101 on 2011-01-10
I'm not sure if this is the right forum to be posting this in but here goes. I have been using Ubuntu for about 3 years now and love it but I use it on my second hand Samaung X30 laptop which was nippy 7 years ago. It has 10.10 on there now, but I was wondering is the Unity upgrade on the desktop side compulsory? I tried to put the net book version on there once since it looked really good and seemed easier to use but being such an old laptop it does not have the greatest gpu (nVidia GeForce GO 5200fx) or CPU (Intel Celeron 1.6GHz). With the current Ubuntu it has been perfectly fine and sometimes quicker than my main desktop pc which is quite new.

But back to the main q... Is Unity definate or will there be an alternative install option to allow for Gnome to be used either 3 or 2.30 (I think that's the current one). 

Thanks

---

### Post by Harry33 on 2011-01-10
> **NickyJ101 said:**
> I'm not sure if this is the right forum to be posting this in but here goes. I have been using Ubuntu for about 3 years now and love it but I use it on my second hand Samaung X30 laptop which was nippy 7 years ago. It has 10.10 on there now, but I was wondering is the Unity upgrade on the desktop side compulsory? I tried to put the net book version on there once since it looked really good and seemed easier to use but being such an old laptop it does not have the greatest gpu (nVidia GeForce GO 5200fx) or CPU (Intel Celeron 1.6GHz). With the current Ubuntu it has been perfectly fine and sometimes quicker than my main desktop pc which is quite new.

But back to the main q... Is Unity definate or will there be an alternative install option to allow for Gnome to be used either 3 or 2.30 (I think that's the current one). 

Thanks

No one knows how definite Unity or Gnome-shell will be in future.
But if you mean Natty Narwhal (11.04), then you will have two options for Gnome desktop:

1) Unity (default)
2) Gnome-Classic (or Gnome-Panel) (option)

Both of those are based on GTK+2.0 (Gimp Tool Kit).
There will not (most likely) be any UIs based on GTK+3.0 in Natty yet.

---

### Post by jerrylamos on 2011-01-10
> **amano said:**
> There will be the Classic Gnome fallback as well. Ignoring that is spreading FUD.

Amano, 

Admittedly this is Alpha 1 but it is a fight to get "classic" running on my three test pc's that can't run "Unity".  See the thread "No Gnome panel" for some of our experiences.  

After daily updates they boot only to wallpaper and cursor even after specifying "classic" on login.  Alt-F2 will work on two of them (yea) so I issue three command lines to get the gnome-panel up. Hopefully this is an Alpha 1 problem that may be alleviated.  

Intrepid shipped with a Compiz failure on this Thinkpad that had a launchpad bug issued months before and not fixed until an update after final release.  This is part of the reason I'm sqwaking now.

Jerry

---

### Post by KegHead on 2011-01-10
Hi!

For what it's worth, the update to tweak is supposed to be able to disable Unity.

Anyone w/luck doing this?

KegHead

---

### Post by seeker5528 on 2011-01-10
> **Harry33 said:**
> Well Classic-Gnome or Gnome-Panel will be there for Natty. But at the same time it should be noted that Gnome-Panel is not developed any further by Gnome.org. And it will be eventually dropped.
That might happen with Natty+1, who knows.

How do you define undeveloped and how do you know being dropped is a bad thing?

Sawfish was dropped as the Gnome window manager years ago and it still gets worked on.

In the mean time I'm assuming the Gnome 3.0 blocker Report is a list of things that are considered necessary to complete before Gnome 3 is released and between metacity, the panel and the panel applets there are a few things listed.

[http://mail.gnome.org/archives/desktop-devel-list/2011-January/msg00078.html](http://mail.gnome.org/archives/desktop-devel-list/2011-January/msg00078.html)

It's not like Metacity, the panel, and the panel applets got huge amounts of work anyway, so while I am not holding my breath, it is conceivable that being dropped as official Gnome components could lead to some new blood coming in and doing as much or more for their development than the original developers. Development seemed to be shifting towards Mutter and away from Metacity independently of Gnome 3, so it could be that we see Mutter+Panel continue while Metacity bit rots into obscurity.

I am assuming that if the official instructions are to do "gnome-panel --repalace" if you want the panel instead of GS, this will give you mutter+panel and that many people, maybe most people, will find this works for them, but some percentage of people who don't have the hardware support for Mutter will still have to switch to metacity or some other window manager to have a functioning desktop.

It's just one of those things where we'll have to wait and see how things shake out.

Later, Seeker

---

### Post by Harry33 on 2011-01-11
> **seeker5528 said:**
> How do you define undeveloped and how do you know being dropped is a bad thing?
'''
Later, Seeker

Please read again my post.
Where did I say being dropped is a bad thing?
Where did I use the word undeveloped?

To be more clear.
Gnome.org will not develop gnome-panel further. It will not be based on GTK+3.0.
I do not intend to stay with Gnome-Panel, so it certainly is not a bad thing to me.
I will very likely find my solution among the options that are based on GTK+3.0.
Only Gnome-shell is there right now.

---

### Post by jennybrew on 2011-01-11
That sounds reasonable position to me. However, isnt it the case that Gnome keeps postponing its release dates? This must make it a nightmare for anyone building and maintaining a distro or, like yourself, planning a personalised direction.
How on earth is anyone supposed to know where or when Gnome is going?
Edit: Isnt that the reason Ubuntu has turned in the direction it has done with Unity?

---

### Post by cariboo on 2011-01-11
Canonical as a sponsor works closely with gnome, so they have some idea where development is going, and how it is progressing. It was felt at UDS-N that gnome 3 wasn't going to be ready in time for the Natty release, and that plus a few other things led to the decision to forge ahead with Unity.

---

### Post by kyleabaker on 2011-01-11
We're almost to Alpha 2 and I haven't seen any impressive Unity improvements in a long while. Places is supposed to be pushed out this Thursday, but I'd much rather see vast improvements to the Dock/panel memory usage and what we can do with icons in the dock.

It just seems like we ought to already be able to drag and drop files in the trash already and have a simple menu for the trash icon. Also, icons on the desktop still don't align with a padding properly when the dock is set to autohide, so the dock sometimes partially covers them. I'm sure these issues are being worked on, but its a lot slower pace than I'd expected.

First impressions are a very important part of the success or failure of a product, so I really hope they get a lot more accomplished in the next few months!

---

### Post by cariboo on 2011-01-11
According to [Jorge]("http://castrojo.tumblr.com/post/2703625422/unity-bitesize-bug-report-for-11-january"), the devs have been fixing bugs, and there will be a Unity update on Thursday.

---

### Post by kyleabaker on 2011-01-11
> **cariboo907 said:**
> According to [Jorge]("http://castrojo.tumblr.com/post/2703625422/unity-bitesize-bug-report-for-11-january"), the devs have been fixing bugs, and there will be a Unity update on Thursday.

Ah, just the kind of great news I was hoping for. :grin:

Looks like they are covering a few problems with the Trash icon! Too bad they aren't adding the feature where the trash Nautilus window auto-closes when you clear trash from the button in the window (as OS X does). This seems really smooth, and I'm not sure why you would want the trash window open after you empty it anyway. Does that qualify as a paper-cut?

---

### Post by VeeDubb on 2011-01-12
One simple reason to keep it open is that there's no reason to open it just to empty the trash, so someone who has opened it may being moving files around and doing some clean up where they want to switch back to the trash periodically to check for things that shouldn't be deleted.

For run of the mill trash emptying, there's no reason to even look inside.

Granted, I'm probably a bit biased since I haven't used a "Trash" on any desktop I've worked on since I discovered that shift-delete would actually DELETE a file back in my Windows 98 days.



As far as the Thursday updates, I'm really looking forward to it.  I watched the development of netbook unity very closely with 10.10, and desktop unity seems to be following roughly the same development path in terms of the order features were added.  This update should be a pretty huge one if that holds true.

---

### Post by ratcheer on 2011-01-12
> **VeeDubb said:**
> 
Granted, I'm probably a bit biased since I haven't used a "Trash" on any desktop I've worked on since I discovered that shift-delete would actually DELETE a file back in my Windows 98 days.


That's what I usually do, too. Or, in Ubuntu, use rm from the shell.

Tim

---

### Post by kyleabaker on 2011-01-12
> **VeeDubb said:**
> One simple reason to keep it open is that there's no reason to open it just to empty the trash, so someone who has opened it may being moving files around and doing some clean up where they want to switch back to the trash periodically to check for things that shouldn't be deleted.

For run of the mill trash emptying, there's no reason to even look inside.

I agree, usually you wouldn't just open the trash view to empty it rather than right clicking on the icon to empty, but I bet it happens quite often. The case that the user might be working with organizing files, thus not wanting it to auto-close, is the only instance I could think of where this should be done though. Also, (its irrelevant whether you like them or not, but) I'm sure Apple has put a great deal of thought behind their approach of auto-closing the window after empty.

> **VeeDubb said:**
> Granted, I'm probably a bit biased since I haven't used a "Trash" on any desktop I've worked on since I discovered that shift-delete would actually DELETE a file back in my Windows 98 days.

Yes, I use this from time to time, typically only when I delete a large number of files at a time when I'm positive I'm not making a mistake. :D

> **VeeDubb said:**
> This update should be a pretty huge one if that holds true.

/me hopes! :cool:

---

### Post by cariboo on 2011-01-12
I enable the delete in Nautilus->Edit->Preferences. I would like to be able to get rid of the trash icon completely.

---

### Post by kyleabaker on 2011-01-12
Server problems, please delete..

---

### Post by kyleabaker on 2011-01-12
Server problems, please delete..

---

### Post by castrojo on 2011-01-12
> **kyleabaker said:**
> This seems really smooth, and I'm not sure why you would want the trash window open after you empty it anyway. Does that qualify as a paper-cut?

Please file a wishlist bug in Unity and tag it "bitesize".

---

### Post by kyleabaker on 2011-01-12
Server problems, please delete..

---

### Post by kyleabaker on 2011-01-12
> **castrojo said:**
> Please file a wishlist bug in Unity and tag it "bitesize".

Thanks, I've filed it here:
[https://bugs.launchpad.net/unity/+bug/701989](https://bugs.launchpad.net/unity/+bug/701989)

---

### Post by seeker5528 on 2011-01-12
> **Harry33 said:**
> Please read again my post.
Where did I say being dropped is a bad thing?
Where did I use the word undeveloped?

To be more clear.
Gnome.org will not develop gnome-panel further. It will not be based on GTK+3.0.

I don't know where you heard that.

I know there was some debate in the early Gnome 3 planning as to whether to supply gnome-panel or force people to some other alternative if they didn't want GS, but I have not seen anything since then indicated a projected time frame to kill off gnome-panel.

As far as not being ported to GTK3, the bug reports indicate that it is.

[https://bugzilla.gnome.org/show_bug.cgi?id=627455](https://bugzilla.gnome.org/show_bug.cgi?id=627455)

otherwise why have a gtk3 branch.

Later, Seeker

---

### Post by Harry33 on 2011-01-13
> **seeker5528 said:**
> I don't know where you heard that.

I know there was some debate in the early Gnome 3 planning as to whether to supply gnome-panel or force people to some other alternative if they didn't want GS, but I have not seen anything since then indicated a projected time frame to kill off gnome-panel.

As far as not being ported to GTK3, the bug reports indicate that it is.

[https://bugzilla.gnome.org/show_bug.cgi?id=627455](https://bugzilla.gnome.org/show_bug.cgi?id=627455)

otherwise why have a gtk3 branch.

Later, Seeker

Now that is new to me.
It really seems that Gnome.org is trying to build gnome-panel package based on GTK+3.0.

So now the point really is that Canonical does not believe Gnome3 will be ready early enough.
That is why Ubuntu 11.04 will stay in GTK+2.0 Gnome-Panel and GTK+2.0 Unity.

An interesting issue is, that when Gnome-Panel-GTK3 is ready, where do we need Unity, even if it were Unity-GTK3. In gnome-panel it is so easy to set a side-panel with all applets and set it autohiding too.

---

### Post by lucazade on 2011-01-13
> **Harry33 said:**
> Now that is new to me.
It really seems that Gnome.org is trying to build gnome-panel package based on GTK+3.0.

So now the point really is that Canonical does not believe Gnome3 will be ready early enough.
That is why Ubuntu 11.04 will stay in GTK+2.0 Gnome-Panel and GTK+2.0 Unity.

An interesting issue is, that when Gnome-Panel-GTK3 is ready, where do we need Unity, even if it were Unity-GTK3. In gnome-panel it is so easy to set a side-panel with all applets and set it autohiding too.

Is Unity using Nux OpenGL toolkit that mimic GTK widgets?
[http://askubuntu.com/questions/18413/what-is-nux-and-whats-it-used-for](http://askubuntu.com/questions/18413/what-is-nux-and-whats-it-used-for)

---

### Post by VeeDubb on 2011-01-13
> **Harry33 said:**
> So now the point really is that Canonical does not believe Gnome3 will be ready early enough.
That is why Ubuntu 11.04 will stay in GTK+2.0 Gnome-Panel and GTK+2.0 Unity.

I really think there may be more to it than that.  I've used gnome shell a number of times.  It's so locked down and restrictive that it makes the original release of OSX look really customizable.  There are a TON of things that simply don't work.

Yet, it has a HUGE community of developers behind it.  I understand that Ubuntu has a HUGE community as well (duh) but the development of GS has been painfully slow.  In fact, I've seen a lot of things switch back and forth.  One week it the overview changes to something radically different, the next week it changes back.


On the other hand, I watched the development of Unity for netbooks very closely, and the only thing I could think was, "if Ubuntu can make this much progress in less than a year, imagine what this thing might look like on a desktop a few releases from now."  

I LOVE the idea of open source.  I love the idea of a huge mass of people collaborating to build a great product.  However, you need clear leadership and a strong sense of direction that I just haven't seen in the development of GS.  Because of that, even if GS would be ready for 11.04, I would still be happy to see Unity coming to the Ubuntu desktop.

You may not always like Shuttleworth's direction, but at least he has a clear direction.

---

### Post by kyleabaker on 2011-01-13
I'm still waiting for that new batch of Unity updates to land today. Currently there is a partial upgrade offerred that wants to remove several important things. I still haven't seen any of the mentioned Unity updates listed yet, but I'll be waiting until the partial upgrade passes anyway before I install the updates.

---

### Post by seeker5528 on 2011-01-13
> **Harry33 said:**
> An interesting issue is, that when Gnome-Panel-GTK3 is ready, where do we need Unity, even if it were Unity-GTK3. In gnome-panel it is so easy to set a side-panel with all applets and set it autohiding too.

Deficiencies in the gnome-panel design and applet handling is a whole other discussion.

Dropping the use of deprecated stuff in favor of the newer equivalents is one thing, but really updating the panel to feel more integrated with the desktop is another thing.

But there does seem to be some ideas for it....

[http://live.gnome.org/GnomePanel/Future](http://live.gnome.org/GnomePanel/Future)

I think for Gnome-Shell and Unity it's a case of not wanting to wait to see how things develop with gnome-panel and having different ideas the developers want to explore about how to provide a more integrated overall experience.

Later, Seeker

---

### Post by ratcheer on 2011-01-14
Well, after patiently waiting all day yesterday for the promised new release of Unity, I got up happily this morning to install it. But, its still not there.....

Tim

---

### Post by go7Ul1ai on 2011-01-14
> **ratcheer said:**
> Well, after patiently waiting all day yesterday for the promised new release of Unity, I got up happily this morning to install it. But, its still not there.....

Tim

Our thoughts are one.

---

### Post by ratcheer on 2011-01-14
Well, it shows as released in the Natty changes digest that I received at 8:12 PM CST, last night.

 **[ubuntu/natty] unity 3.2.8-0ubuntu2 (Accepted) (Didier Roche)**

That was 13 hours ago. I wonder what's taking it so long?

Tim

---

### Post by mc4man on 2011-01-14
> I wonder what's taking it so long
That particular build [is waiting for an updated library]("https://launchpad.net/ubuntu/+source/unity/3.2.8-0ubuntu2/+build/2150343") (libdbusmenu-glib-dev

It, when done, will allow updating compiz though I'm not too sure it includes the other unity updates you may have been looking for
cl
> unity (3.2.8-0ubuntu2) natty; urgency=low

  * src/unityshell.cpp:
    - backport a fix for WindowCompizid
  * debian/control:
    - ABI break in compiz, rebuild against latest version
  * CMakeLists.txt, libunity/CMakeLists.txt:
    - don't build some vala stuff
  * debian/libunity3.symbols:
    - refresh the symbols regarding to previous changes
  * backport dbusmenu transition:
    - debian/control: build-dep on the new package
    - backport the commits

 -- Didier Roche <didrocks@ubuntu.com>  Fri, 14 Jan 2011 01:22:00 +0100

---

### Post by go7Ul1ai on 2011-01-14
I was led to believe that Places would be landing in the next Unity update.. I was wrong? :(

---

### Post by castrojo on 2011-01-14
We're working on it as we speak (and we were up quite late trying to release yesterday) but unfortunately due to some compiz bugs that weren't sorted we weren't able to finish.

Expect it to land sometime today. Places will likely not land today unfortunately, probably next week.

---

### Post by madjr on 2011-01-14
> **castrojo said:**
> We're working on it as we speak (and we were up quite late trying to release yesterday) but unfortunately due to some compiz bugs that weren't sorted we weren't able to finish.

Expect it to land sometime today. Places will likely not land today unfortunately, probably next week.

awwwww :( , well ok thx

---

### Post by ratcheer on 2011-01-14
> **castrojo said:**
> We're working on it as we speak (and we were up quite late trying to release yesterday) but unfortunately due to some compiz bugs that weren't sorted we weren't able to finish.

Expect it to land sometime today. Places will likely not land today unfortunately, probably next week.

Thank you. I know it isn't easy.

BTW, I just received another notice that Unity is released at 10:45 AM CST. Maybe it will arrive, soon.

[ubuntu/natty] unity 3.2.8-0ubuntu3 (Accepted) (Didier Roche)

Tim

---

### Post by ratcheer on 2011-01-14
> **castrojo said:**
> We're working on it as we speak (and we were up quite late trying to release yesterday) but unfortunately due to some compiz bugs that weren't sorted we weren't able to finish.

Expect it to land sometime today. Places will likely not land today unfortunately, probably next week.

Thank you. I know it isn't easy.

BTW, I just received another notice that Unity is released at 10:45 AM CST. Maybe it will arrive, soon.

[ubuntu/natty] unity 3.2.8-0ubuntu3 (Accepted) (Didier Roche)

Tim

---

### Post by ratcheer on 2011-01-14
> **castrojo said:**
> We're working on it as we speak (and we were up quite late trying to release yesterday) but unfortunately due to some compiz bugs that weren't sorted we weren't able to finish.

Expect it to land sometime today. Places will likely not land today unfortunately, probably next week.

Thank you. I know it isn't easy.

BTW, I just received another notice that Unity is released at 10:45 AM CST. Maybe it will arrive, soon.

[ubuntu/natty] unity 3.2.8-0ubuntu3 (Accepted) (Didier Roche)

Tim

---

### Post by ratcheer on 2011-01-14
> **castrojo said:**
> We're working on it as we speak (and we were up  quite late trying to release yesterday) but unfortunately due to some  compiz bugs that weren't sorted we weren't able to finish.

Expect it to land sometime today. Places will likely not land today unfortunately, probably next week.

Thank you. I know it isn't easy.

BTW, I just received another notice that Unity is released at 10:45 AM CST. Maybe it will arrive, soon.

[ubuntu/natty] unity 3.2.8-0ubuntu3 (Accepted) (Didier Roche)

Tim

---

### Post by ratcheer on 2011-01-14
Sorry, again. The website is continually failing to respond to my posts, then it posts all my attempts at once.

Tim

---

### Post by castrojo on 2011-01-14
> **ratcheer said:**
> Thank you. I know it isn't easy.
[ubuntu/natty] unity 3.2.8-0ubuntu3 (Accepted) (Didier Roche)


You'll probably see uploads like this today to rebuild it for different libraries. The one you're looking for will say "new upstream release" in the changelog and it will be long. :)

---

### Post by ratcheer on 2011-01-14
Ok, it looks like it is here:

unity (3.2.12-0ubuntu1) natty; urgency=low

  * New upstream release.

Tim

---

### Post by ratcheer on 2011-01-14
Ok, it looks like it is here:

unity (3.2.12-0ubuntu1) natty; urgency=low

  * New upstream release.

Tim

---

### Post by ratcheer on 2011-01-17
The current incarnation of Unity/Natty is very broken for me, right now. I do see that a new, minor release of Unity is coming very soon.

It is almost totally invulnerable to right-clicks. Nothing at all happens if I right-click on the desktop or in Firefox 4 b9. Firefox menus are unresponsive. Dropdown controls in Firefox are unresponsive.

I cannot even get a response to the top panel far right button to logout, shutdown, restart, etc.

On the plus side, Unity is now starting up very fast (it used to take 10 seconds or so) and it looks wonderful. But, very disfunctional. I hope today's release fixes some of this mess.

Tim

---

### Post by castrojo on 2011-01-17
If right clicks break then something died, usually a "unity --reset" in a terminal works for me.

---

### Post by ratcheer on 2011-01-17
I installed today's unity updates and now everything seems to be working without intervention.

Tim

---

### Post by mc4man on 2011-01-17
> I installed today's unity updates and now everything seems to be working without intervention.
Don't be surprised if you get some occasional misbehavior with menus, ect. Until some underlying compiz issues are fixed it's likely to happen at times.

You may also find this issue happening at times
[https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/703689](https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/703689)

..

---

### Post by Finalfantasykid on 2011-01-17
cariboo posted a screenshot of the top panel today, and there was no shadow under it.  Will the final version of unity have the top panel with a shadow or without?

---

### Post by jerrylamos on 2011-01-18
> **Finalfantasykid said:**
> cariboo posted a screenshot of the top panel today, and there was no shadow under it.  Will the final version of unity have the top panel with a shadow or without?

The "old" spirit of Ubuntu would be whatever you prefer.  I'm trying Unity-2D without shadows and other "eye" candy effects and my impression BAM is it fast compared to Unity-3D when I can even get Unity-3D to run.

All those "effects" I feel are behind Compiz having trouble running on a variety of machines.  That would be O.K. under the "old" spirit of Ubuntu, tailor linux to what you want, however CD Live currently is Unity-3D and not running or hardly running on the two of my pc's who should be able to run it, and there is no login option on CD Live.

Well, it's Alpha time, and the Compiz people have a lot of work to do, mentioned on one of their blogs.  Yes, I've got a Compiz bug entered on ati radeon xpress 200.  Crashes in Unity-3D, crashes in gnome-panel with effects turned on, and does NOT crash in the new option gnome panel "no-effects".  Yay!  Three cheers for the new option!

By the way, "tiny core" in 11 MB has a apple type launcher where the thumbnails enlarge and squirm and add titles as the cursor goes over, and is totally auto-hide - the applications really do get "full screen".  Also runs on old and new hardware.  No, no shading or transitory exploding selections.  It just runs.  I'm hoping "Unity-2D will do the same.

Spent a couple hours trying with everything I could think of to get updated Unity to boot last night on ati radeon xpress 200.  It finally did, and the launcher had an automatic autohide.  Which meant I could ignore it and it got out of the way.  

Now selecting the top left applet brought up screens full of icons which looked like Preferences and Applications and System all in a huge set page after page thankfully sorted by name so I was eventually able to find "login".  I ran out of time to see if I could make a list without the screen eating icons.

Progress!

Jerry

---

### Post by Skara Brae on 2011-01-19
I am reading/skimming through this interesting thread.

From what I see on screencaptures/pictures, I believe that I am not going to like "Unity"...

When one can work with Windows 95 (that is 15 years ago), then one can also work with Windows XP, because the UI looks the same.
When one switches to Vista/Win7, then one has to start from scratch... I am now and then still searching where MS put what. I "hate" Vista/Win7 (among others, pun intended :P) because of the complete overhaul of the UI that they did. Vista/7 is the proof of how Microsoft ruined a good UI.

If Gnome would ever be completely discarded from Ubuntu (a big "IF", I know), then I would have to switch to another distro that would still use Gnome (Would probably be Debian).

-oo-

For over 3 years, I have always been extremely pleased about Ubuntu. I do hope that will stay.

---

### Post by madjr on 2011-01-19
> **Skara Brae said:**
> I am reading/skimming through this interesting thread.

From what I see on screencaptures/pictures, I believe that I am not going to like "Unity"...

When one can work with Windows 95 (that is 15 years ago), then one can also work with Windows XP, because the UI looks the same.
When one switches to Vista/Win7, then one has to start from scratch... I am now and then still searching where MS put what. I "hate" Vista/Win7 (among others, pun intended :P) because of the complete overhaul of the UI that they did. Vista/7 is the proof of how Microsoft ruined a good UI.

If Gnome would ever be completely discarded from Ubuntu (a big "IF", I know), then I would have to switch to another distro that would still use Gnome (Would probably be Debian).

-oo-

For over 3 years, I have always been extremely pleased about Ubuntu. I do hope that will stay.

unity has a lot of improvements, specially in usability, easier program/file search and desktop space saving (by getting out of the way of your work/media) not present in normal gnome, as well as making it more modern and competitive, while still being light weight.

the best thing is they've taken the time to include **classic gnome** to ease the transition and is just one log-out away.

You can't start saying "now" that you wont like it till you try it in april, or your **subconscious** will indeed have a harder time getting used to the idea. So don't do that to yourself.

---

### Post by jerrylamos on 2011-01-19
> **madjr said:**
> unity has a lot of improvements, specially in usability, easier program/file search and desktop space saving (by getting out of the way of your work/media) not present in normal gnome, as well as making it more modern and competitive, while still being light weight

Jury is still out for me.  When Unity will run on the one of my four pc's that it chooses to (this is Alpha time), it requires me more keystrokes and windows to do what I usually do with my applications.  Applications are why I run linux, not eye candy.

At the moment, Unity-2D is BAM fast compared to admittedly Alpha level Unity-3D, this on 3.3 GHZ.  However Unity-2D is behind on development and may/may not ever be a mainstream choice.

Oh, why doesn't Unity run on the other three?  Compiz.

---

### Post by VMC on 2011-01-19
Unity is just now getting attention. Remember there are other programs, files that need attention. Maybe before Unity can preform well. In the past two ISO's , I've seen much better results using Unity.

At least wait until Natty release before passing judgment, which I was guilty of in the beginning.

---

### Post by VMC on 2011-01-19
Unity is just now getting attention. Remember there are other programs, files that need attention. Maybe before Unity can preform well. In the past two ISO's , I've seen much better results using Unity.

At least wait until Natty release before passing judgment, which I was guilty of in the beginning.

---

### Post by VMC on 2011-01-19
Unity is just now getting attention. Remember there are other programs,  files that need attention. Maybe before Unity can preform well. In the  past two ISO's , I've seen much better results using Unity.

At least wait until Natty release before passing judgment, which I was guilty of in the beginning.

---

### Post by VMC on 2011-01-19
test

---

### Post by VMC on 2011-01-19
test

---

### Post by VMC on 2011-01-19
test

---

### Post by cariboo on 2011-01-19
> **jerrylamos said:**
> Jury is still out for me.  When Unity will run on the one of my four pc's that it chooses to (this is Alpha time), it requires me more keystrokes and windows to do what I usually do with my applications.  Applications are why I run linux, not eye candy.

At the moment, Unity-2D is BAM fast compared to admittedly Alpha level Unity-3D, this on 3.3 GHZ.  However Unity-2D is behind on development and may/may not ever be a mainstream choice.

Oh, why doesn't Unity run on the other three?  Compiz.


As has been stated several time before, if your system are not capable of doing 3D Unity won't run on them. You can't expect new features to be supported on older hardware for ever.

---

### Post by kyleabaker on 2011-01-19
If the places view is going to land this week, it will be released in a [few hours](https://launchpad.net/unity/+milestone/3.2.14). However, at the moment it is still marked as "in progress". There are several other interesting changes that may make it with this update as well.

---

### Post by kyleabaker on 2011-01-19
(I wish these server problems could be fixed soon)

---

### Post by SushiR on 2011-01-19
I just got used to Unity so quickly, I almost can't believe. :-) It's really getting out of the way and it's there, when you need it. It runs smooth and snappy on my netbook (Samsung N150). I'm looking forward to the places updates and other interesting things yet to come.

Btw. interesting interview with Neil Partel on OMG!: [http://www.omgubuntu.co.uk/2011/01/exclusive-interview-with-unitys-technical-lead-neil-patel-this-is-a-must-read-folks/](http://www.omgubuntu.co.uk/2011/01/exclusive-interview-with-unitys-technical-lead-neil-patel-this-is-a-must-read-folks/)

---

### Post by jerrylamos on 2011-01-19
Just installed today's CD Daily update 20110119 and Unity 3D is running.  At this stage.  More stable than Natty updated from the initial Alpha 1.

Simple question, on Unity 3D with firefox, how do I select Edit?  View?  Bookmarks?  I'm not getting anywhere with left click....or double click....or click then enter....

Thanks, Jerry

---

### Post by jerrylamos on 2011-01-19
Just installed today's CD Daily update 20110119 and Unity 3D is running.  At this stage.  More stable than Natty updated from the initial Alpha 1.

Simple question, on Unity 3D with firefox, how do I select Edit?  View?  Bookmarks?  I'm not getting anywhere with left click....or double click....or click then enter....

Thanks, Jerry

---

### Post by jerrylamos on 2011-01-19
Just installed today's CD Daily update 20110119 and Unity 3D is running.  At this stage.  More stable than Natty updated from the initial Alpha 1.

Simple question, on Unity 3D with firefox, how do I select Edit?  View?  Bookmarks?  I'm not getting anywhere with left click....or double click....or click then enter....

Thanks, Jerry

---

### Post by VeeDubb on 2011-01-19
> **jerrylamos said:**
> Just installed today's CD Daily update 20110119 and Unity 3D is running.  At this stage.  More stable than Natty updated from the initial Alpha 1.

Simple question, on Unity 3D with firefox, how do I select Edit?  View?  Bookmarks?  I'm not getting anywhere with left click....or double click....or click then enter....

Thanks, Jerry

You just click like always.

The problem is that the drop down menus are either not being drawn, or are being drawn under the unity shell so you can't see them.

It's a bug.

---

### Post by ratcheer on 2011-01-19
> **jerrylamos said:**
> 

Simple question, on Unity 3D with firefox, how do I select Edit?  View?  Bookmarks?  I'm not getting anywhere with left click....or double click....or click then enter....


I was having the same problem a couple of days ago, but more updates cleared it up.

Tim

---

### Post by kyleabaker on 2011-01-19
> **ratcheer said:**
> I was having the same problem a couple of days ago, but more updates cleared it up.

Tim

[This]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/695638") bug is still upen, but will hopefully be put to rest with the [Unity 3.2.14]("https://launchpad.net/unity/+milestone/3.2.14") update that is expected in 2 hours. :popcorn:

---

### Post by mc4man on 2011-01-19
There was just an update to dconf-tools (dconf-editor from cli), that stops the segfaults and is slowly adding some settings
Not that much in there yet, some of interest, worth keeping eye on.
(looks like there is still a small mem.leak in compiz, though on a slightly older install it's severe and the install will have to be abandoned

---

### Post by SushiR on 2011-01-20
Any news about Unity places and files "dashboards"? I remember someone saying that it'll hit Natty this week...

---

### Post by ratcheer on 2011-01-20
> **SushiR said:**
> Any news about Unity places and files "dashboards"? I remember someone saying that it'll hit Natty this week...

In fact, there is a new Unity upstream release today. Here is one of the fixes mentioned in the changelog:

 unity (3.2.14-0ubuntu1) natty; urgency=low
...
- Places tile view (LP: #697687)

Tim

---

### Post by ratcheer on 2011-01-20
> **SushiR said:**
> Any news about Unity places and files  "dashboards"? I remember someone saying that it'll hit Natty this  week...

In fact, there is a new Unity upstream release today. Here is one of the fixes mentioned in the changelog:

 unity (3.2.14-0ubuntu1) natty; urgency=low
...
- Places tile view (LP: #697687)

Tim

---

### Post by go7Ul1ai on 2011-01-20
> **ratcheer said:**
> In fact, there is a new Unity upstream release today. Here is one of the fixes mentioned in the changelog:

 unity (3.2.14-0ubuntu1) natty; urgency=low
...
- Places tile view (LP: #697687)

Tim

When will this land in Natty? and could you post a full changelog please? :)

---

### Post by SushiR on 2011-01-20
unity-places-* isn't installable right now, if I'm right. Really looking forward though.

---

### Post by terry_gardener on 2011-01-20
unity (3.2.14-0ubuntu1) natty; urgency=low

  * New upstream release:
    - Use a padding of 6px for the appmenu and 3px for the other indicators.
      (LP: #684114)
    - appmenu doesn't correspond to currently focused application (LP: #69806)
    - Places tile view (LP: #697687)
  * remove inline patch to build tests against
  * debian/control:
    - recommends ubuntuone-control-panel-gtk
    - removed libunity*: seperate source now
    - bump libnux requirement
  * removed debian/libunity*
  * debian/source_unity.py:
    - enhance apport hook to report compiz (and xorg) information only on
      graphical bugs (the report can take time and would upload too many data for
      just a weird quick behavior bug for instance)
 -- Didier Roche <didrocks@ubuntu.com>   Thu, 20 Jan 2011 19:24:47 +0100

---

### Post by mc4man on 2011-01-20
this is the current changelog from source - may or may not be the released package
> unity (3.2.14-0ubuntu1) natty; urgency=low

  * New upstream release:
    - Use a padding of 6px for the appmenu and 3px for the other indicators.
      (LP: #684114)
    - appmenu doesn't correspond to currently focused application (LP: #69806)
    - Places tile view (LP: #697687)
  * remove inline patch to build tests against
  * debian/control:
    - recommends ubuntuone-control-panel-gtk
    - removed libunity*: seperate source now
    - bump libnux requirement
  * removed debian/libunity*
  * debian/source_unity.py:
    - enhance apport hook to report compiz (and xorg) information only on
     graphical bugs (the report can take time and would upload too many data for
      just a weird quick behavior bug for instance)
 -- Didier Roche <didrocks@ubuntu.com>  Thu, 20 Jan 2011 19:24:47 +0100



to bad it doesn't scale to display size

---

### Post by webme on 2011-01-20
> **lee.jarratt said:**
> When will this land in Natty? and could you post a full changelog please? :)

the dash is , starting a couple of minutes ago, in Natty, but it's kinda ugly and different

take a look at this [http://iloveubuntu.net/dash-has-landed-natty-narwhal](http://iloveubuntu.net/dash-has-landed-natty-narwhal)   for an image with the Dash in action

---

### Post by kyleabaker on 2011-01-20
This isn't what the Places view is actually going to look like is it?
[[IMG]http://img132.imageshack.us/img132/8650/screenshot2tj.png[/IMG]]("http://img155.imageshack.us/img155/8409/screenshotzo.png")

---

### Post by go7Ul1ai on 2011-01-20
> **kyleabaker said:**
> This isn't what the Places view is actually going to look like is it?
[[IMG]http://img132.imageshack.us/img132/8650/screenshot2tj.png[/IMG]]("http://img155.imageshack.us/img155/8409/screenshotzo.png")

We're not even at Alpha 2 yet, it's a work in progress, it will develop :)

---

### Post by kyleabaker on 2011-01-20
> **lee.jarratt said:**
> We're not even at Alpha 2 yet, it's a work in progress, it will develop :)

Yea, I'm just hoping it eventually scales the full screen and that they don't leave it only partially filling.

---

### Post by kyleabaker on 2011-01-20
Few questions:
1. Is anyone seeing their real name displayed by the MeMenu in Unity (rather than the username). This was [reported to of changed]("http://www.omgubuntu.co.uk/2010/12/memenu-now-displays-full-user-name-in-natty/"), but I never saw any changes (my still shows the username).

@lee.jarratt
Does yours still display the real name?

2. What happened to the avatar being placed at the top of the MeMenu? Is it planned to come back?

My messaging indicator menu is adding additional entries for "Chat" and "Broadcast" when I open Empathy and Gwibber. Maybe its time for a fresh install with a newer cd. :D

---

### Post by futureal2032 on 2011-01-21
I have a simple Question...

I have nothing against Unity.. infact i like when efforts are made to create something new and improved in a forward direction..

thing is i dont like the "Panels" look of Unity.. feels like cell phone to me..

Can i configure Unity to look like (or nearest to) a simple desktop with menu bar (tasbar with application launchers) and a nice wallpaper for my desktop/netbook screen and some launcher i cons on my desktop..(like any classic windows/linux/gnome/kde/mac) desktop GUI ???????

---

### Post by go7Ul1ai on 2011-01-21
> **kyleabaker said:**
> Few questions:
1. Is anyone seeing their real name displayed by the MeMenu in Unity (rather than the username). This was [reported to of changed]("http://www.omgubuntu.co.uk/2010/12/memenu-now-displays-full-user-name-in-natty/"), but I never saw any changes (my still shows the username).

@lee.jarratt
Does yours still display the real name?

2. What happened to the avatar being placed at the top of the MeMenu? Is it planned to come back?

My messaging indicator menu is adding additional entries for "Chat" and "Broadcast" when I open Empathy and Gwibber. Maybe its time for a fresh install with a newer cd. :D

No, it had changed back a long time ago. Quite sad really as it was a welcome change by me and some others.

---

### Post by SushiR on 2011-01-21
> **futureal2032 said:**
> I have a simple Question...

I have nothing against Unity.. infact i like when efforts are made to create something new and improved in a forward direction..

thing is i dont like the "Panels" look of Unity.. feels like cell phone to me..

Can i configure Unity to look like (or nearest to) a simple desktop with menu bar (tasbar with application launchers) and a nice wallpaper for my desktop/netbook screen and some launcher i cons on my desktop..(like any classic windows/linux/gnome/kde/mac) desktop GUI ???????
You can choose any wallpaper you like and put as many icons on your desk, as you want. There are very few config options for the "panel", but this may change before release.

---

### Post by anders_c_ on 2011-01-21
Not much functionality yet but at least it's there:D
I personally think it looks hideous when it only takes up one fourth of the screen, fullscreen would look so much nicer.

---

### Post by Simian Man on 2011-01-21
So first Ubuntu names their new 3D interface after a 3D game engine, then names their new file browser after a shell (which comes on Ubuntu already).  How about some creativity in naming?

---

### Post by Merk42 on 2011-01-21
> **Simian Man said:**
> So first Ubuntu names their new 3D interface after a 3D game engine, then names their new file browser after a shell (which comes on Ubuntu already).  How about some creativity in naming?Then you either get programs with "free" or "open" in the name, or something that's confusing to pronounce because it's a reference to some work of sci-fi or fantasy.
I'm not sure which of those 3 options are the worst.

---

### Post by madjr on 2011-01-24
> **anders_c_ said:**
> Not much functionality yet but at least it's there:D
I personally think it looks hideous when it only takes up one fourth of the screen, fullscreen would look so much nicer.

nice you're using latest ubuntu-tweak to remove the username from the me-menu indicator. I like it better like that and uses less space

---

### Post by Wobblybob on 2011-01-26
"Pressing enter at the login screen doesn't work"

Since I updated on 25th Jan it works now in Xubuntu, well done that man:p

---

### Post by webme on 2011-01-27
Unity 3.2.16 is out, the dash has search entry now and Unity dock has places group view.

For pictures take a look at [http://iloveubuntu.net/places-group-view-and-search-entry-have-landed-ubuntu-1104-alpha-1-natty-narwhal-unity-3216](http://iloveubuntu.net/places-group-view-and-search-entry-have-landed-ubuntu-1104-alpha-1-natty-narwhal-unity-3216)

---

### Post by forcecore on 2011-01-28
Do 11.04 can use Unity 2D out of box because lot of laptops and computers do not support 3D or has broken 3D (very buggy).

---

### Post by VeeDubb on 2011-01-28
> **forcecore said:**
> Do 11.04 can use Unity 2D out of box because lot of laptops and computers do not support 3D or has broken 3D (very buggy).

Right now, no.  The default is for the system to revert to the "classic" desktop, which means Gnome 2.

---

### Post by jerrylamos on 2011-01-28
> **VeeDubb said:**
> Right now, no.  The default is for the system to revert to the "classic" desktop, which means Gnome 2.

?  CD Live tries its best, i.e.defaults, to Unity 3D whether it will run or not.  There is a message about "change user session" which as of last week didn't work on three of my four test systems.  The fourth will run Natty for 5 to 10 minutes until Compiz hangs, unless I'm running "classic no effects" which works fine.

I'll try CD live again next week.  Right now I'm visiting, using Aspire one netbook which does do Unity 3D, or at least as much of it as is functional.

Jerry

---

### Post by forcecore on 2011-01-28
I hope they change to unity 2D when released...

---

### Post by cariboo on 2011-01-28
The classic desktop is the fallback if your system can't run Unity. The Unity 2D interface is designed to run on arm processors, and will be available in the repositories.

---

### Post by KegHead on 2011-01-28
Hi!

How about my Atom based desktop?

KegHead

---

### Post by zekopeko on 2011-01-28
> **cariboo907 said:**
> The Unity 2D interface is designed to run on arm processors, and will be available in the repositories.

This isn't entirely correct. Unity 2D was designed for systems that don't have proper 3D acceleration. ARM is only a small subset of that.
In 11.10 it will most likely be a fallback when Unity 3D can't run, supplanting the regular Gnome 2 session that is the current fallback. This  will in turn bring consistency to the desktop.

---

### Post by jerrylamos on 2011-01-29
> **KegHead said:**
> Hi!

How about my Atom based desktop?

KegHead

This Atom N455 on Aspire one D255E netbook is running Unity 3D to the level that is functional on Alpha 1.  We'll see about Alpha 2....

Jerry

---

### Post by VeeDubb on 2011-01-29
> **cariboo907 said:**
> The classic desktop is the fallback if your system can't run Unity. The Unity 2D interface is designed to run on arm processors, and will be available in the repositories.

Wait, ARM?  As in cell phones and $100 ebay Chinese netbooks?  I didn't even realize there was an ARM version of Ubuntu.

---

### Post by KegHead on 2011-01-29
Hi!

My desktop is an Atom 330.

Any thoughts?

KegHead

---

### Post by castrojo on 2011-01-29
> **VeeDubb said:**
> Wait, ARM?  As in cell phones and $100 ebay Chinese netbooks?  I didn't even realize there was an ARM version of Ubuntu.

For years now: [https://wiki.ubuntu.com/ARM](https://wiki.ubuntu.com/ARM)

---

### Post by MacUntu on 2011-01-30
From [http://irclogs.ubuntu.com/2011/01/30/%23ubuntu-classroom.txt](http://irclogs.ubuntu.com/2011/01/30/%23ubuntu-classroom.txt)

> [03:50] <jcastro> for 11.04 will we be able to switch to a light theme like Radiance?
[03:50] <DBO> probably not
[03:51] <DBO> if not in 11.04, for sure in 11.10

:(

[[img]http://img.xrmb2.net/459801.jpg[/img]](http://img.xrmb2.net/images/459801.png)

---

### Post by webme on 2011-01-31
Unity 3.4 is out and quite hot. 
The search is now functional and the places are back(files and folders, applications).
For a picture take a look @ [http://iloveubuntu.net/unity-34-out-bringing-places-back-search-improved-functionality-and-bug-fixes](http://iloveubuntu.net/unity-34-out-bringing-places-back-search-improved-functionality-and-bug-fixes)

---

### Post by KegHead on 2011-01-31
Hi!

I'll give it a try (Alpha 2)on my Atom desktop.

KegHead

---

### Post by mc4man on 2011-01-31
> Unity 3.4 is out and quite hot.
It's an interesting update and quite full of possible issues..

---

### Post by KegHead on 2011-01-31
Hi!

It's going to take a lot for me to leave 10.10.

All my machines are running 10.10 even my Dell mini 9.

But, I'm willing to give Unity a fair shot.

KegHead

---

### Post by cecilpierce on 2011-01-31
> **webme said:**
> Unity 3.4 is out and quite hot. 
The search is now functional and the places are back(files and folders, applications).
For a picture take a look @ [http://iloveubuntu.net/unity-34-out-bringing-places-back-search-improved-functionality-and-bug-fixes](http://iloveubuntu.net/unity-34-out-bringing-places-back-search-improved-functionality-and-bug-fixes)

Hmmm! my places are empty, any body else or whats wrong with this picture? I have all the new updates.

---

### Post by Peter09 on 2011-01-31
Places empty - same here

---

### Post by cariboo on 2011-01-31
Click on the Applications or Files & Folders icon in the panel.

---

### Post by Astrotrain on 2011-01-31
There is one question I would like to ask, since I`ve not been able to find anyone discussing the matter so far. Namely, I am a heavy keyboard user. Maybe as high as 80-90 percent of all my computer activity is being conducted via keyboard, and all the information about Unity that I have been able to gather so far does not make much positive impression in that regard. I have done a little bit of testing myself, but only with UNR version and results have been very dissapointing considering my working habbits. 
So basically, my question is : **will Unity be keyboard friendly?**
Of course, when the time comes to use a touchscreen it will be a quite different story, but for me it is still a few years distant future, and in the meantime I would like to have the possibility to keep working mostly via keyboard and not touch the mouse too much.

---

### Post by cecilpierce on 2011-01-31
> **cariboo907 said:**
> Click on the Applications or Files & Folders icon in the panel.

I don see a Apps or Files folder, its just an empty box where is it suppose to be ?

---

### Post by cariboo on 2011-01-31
Jorge Castro said in last Saturday's Unity Q&A that he would be starting a wiki on that very subject, so give it some time,and we'll post a link when it's available.

---

### Post by castrojo on 2011-01-31
> **Astrotrain said:**
> So basically, my question is : **will Unity be keyboard friendly?**

Yes, however a bunch haven't been finished yet. I've started this page if anyone wants to help me write them down.

[https://wiki.ubuntu.com/Unity/KeyboardShortcuts](https://wiki.ubuntu.com/Unity/KeyboardShortcuts)

---

### Post by webme on 2011-01-31
> **cecilpierce said:**
> I don see a Apps or Files folder, its just an empty box where is it suppose to be ?

Click on the ? icons (when you hover the mouse over it, it says Files&Folders, Applications)

---

### Post by cariboo on 2011-01-31
> **castrojo said:**
> Yes, however a bunch haven't been finished yet. I've started this page if anyone wants to help me write them down.

[https://wiki.ubuntu.com/Unity/KeyboardShortcuts](https://wiki.ubuntu.com/Unity/KeyboardShortcuts)

Thanks Jorge

---

### Post by cecilpierce on 2011-01-31
> **webme said:**
> Click on the ? icons (when you hover the mouse over it, it says Files&Folders, Applications)

Wow I thought all those question marks were my other HD partitions, at least they were the other day. When I open the Applications folder it shows icons but won't scroll down but you can't have everything I guess, 
Thanks
Cec

---

### Post by mc4man on 2011-01-31
> i've started this page if anyone wants to help me write them down.
for mouse tricks you have scale on an app in  the launcher icon, was previously broken as far as retrieving from all workspaces - now works fine.
 (1 click brings to focus from current space, 2nd  pulls all to a display/choose screen.

---

### Post by Astrotrain on 2011-01-31
> **castrojo said:**
> Yes, however a bunch haven't been finished yet. I've started this page if anyone wants to help me write them down.

[https://wiki.ubuntu.com/Unity/KeyboardShortcuts](https://wiki.ubuntu.com/Unity/KeyboardShortcuts)

Oh great! Thank you! I`d like to pose a few more questions, and I apologize in advance for what might seem as a lack of clarity or knowledge, because I am neither a native English speaker, nor a computer expert, so please take that into consideration if my questions would happen to cause you any incoviniense. The questions are following:

1.Considering the fact that Unity is based on Compiz which shortcuts are highly customizable, is it presumable that Unitys` keyboard shortcuts are going to be customizable as well? 
 
2. Will it be possible to visually separate application launchers, from running programs indicators by means of separators as it is done in a dock (e.g. AWN)?

3. Will it be possible to turn off "side-launcher-panel" (or whatever it is called) and use a dock instead, or is it inseparably intertwined with the rest of the interface?

4. Will it be possible to implement an applet indicator and notification area inside a "side-launcher-panel" of Unity, like it is done in a AWN dock instead of doing it only inside a top panel?

Thanks in advance.

---

### Post by cariboo on 2011-01-31
> 3. Will it be possible to turn off "side-launcher-panel" (or whatever it is called) and use a dock instead, or is it inseparably intertwined with the rest of the interface?

You can select the Classic Desktop session from the login screen, whih gets you the gnome 2 panel interface.

I personally use docky2 with Unity.

---

### Post by castrojo on 2011-01-31
> **Astrotrain said:**
> on Compiz which shortcuts are highly customizable, is it presumable that Unitys` keyboard shortcuts are going to be customizable as well?

Yes, you just fire up ccsm and you can add/update/change whatever you'd like. For example I use the cube for my virtual desktops. 
 
> Will it be possible to visually separate application launchers, from running programs indicators by means of separators as it is done in a dock (e.g. AWN)?

No clue, but I'm leaning towards no since I can't find a bug report on it.

> Will it be possible to turn off "side-launcher-panel" (or whatever it is called) and use a dock instead, or is it inseparably intertwined with the rest of the interface?

It's all one thing. However Unity 2d has seperate components where you can mix and match, or just add it to the classic desktop.

> Will it be possible to implement an applet indicator and notification area inside a "side-launcher-panel" of Unity, like it is done in a AWN dock instead of doing it only inside a top panel?

Nope, what app authors will have instead is a set of APIs that they can use if they want to show things that people misuse application indicators for. Things like a number emblem for the amount of new mail, download progress bars, etc.

See this buglist: [https://bugs.launchpad.net/unity/+bugs?field.tag=udn-launcher](https://bugs.launchpad.net/unity/+bugs?field.tag=udn-launcher)

I expect for Natty+1 we'll add things to the API based on what app developers want.

---

### Post by seeker5528 on 2011-01-31
> **Astrotrain said:**
> 2. Will it be possible to visually separate application launchers, from running programs indicators by means of separators as it is done in a dock (e.g. AWN)?

Since the same icon is used either way with status indicators appearing next to the icons to show number of instances open and which app has the active window, what would be the point of seperation?  

Later, Seeker

---

### Post by kyleabaker on 2011-01-31
I hope I'm not the only one bothered by the appearance of a resizing window now that the invisible borders are there. Seems very misrepresentative visually of the actual window size. I think they could do away with the white resize border altogether.

[IMG]http://img21.imageshack.us/img21/5907/screenshotat.png[/IMG]

Maybe the resize border could be corrected to "hug" the visual border, but that still wouldn't fix another problem introduced by this invisible border where the autohide feature for the launcher bar is triggerd early.

[IMG]http://img89.imageshack.us/img89/975/screenshot1nk.png[/IMG]

That is as close as the window can get now without triggering an autohide and it doesn't look like the correct behavoir compared to how it used to behave.

---

### Post by mc4man on 2011-01-31
> bothered by the appearance of a resizing window ...

Personally doesn't bother me (what is it, about an 1/8 of in.) and in any event am using and plan to use 'true-hide' instead of intellihide.

Being it's a theme config, (light themes), if it doesn't shake out the way you like it can be adjusted
Currently focused windows are padded 7 (l,r,b,) unfocused are 2 (l,r,b

If 2 works better then adjust in /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml (or go less if inclined
just did here to see, now focused are the same as unfocused, though plan on restoring to orig. values

While I preferred the corner grab area many windows don't have it so this is an improvement

---

### Post by kyleabaker on 2011-02-01
> **mc4man said:**
> While I preferred the corner grab area many windows don't have it so this is an improvement

The extra area to "grab" the resize points is certainly beneficial, but I was referring to the white rectangle that appears when you resize the window. If you look closely, only the top is correctly represented while the other sides are showing the edge of the shadows and not the visual "edge" of the window.

If this isn't fixed by final release then I'm sure someone will make a corrected theme, but it'd be nice if they fixed it for final.

---

### Post by mc4man on 2011-02-01
> while the other sides are showing the edge of the shadows and not the visual "edge" of the window.
The white is showing the padding, not sure if that's incorrect, seems right.
If you feel 7 is too much for the sides then you could file a bug on, maybe a smaller value like 4 would be acceptable 

(I'm assuming some thought/reason went into having different values for focused and unfocused

---

### Post by MacUntu on 2011-02-01
> **mc4man said:**
> Personally doesn't bother me (what is it, about an 1/8 of in.) and in any event am using and plan to use 'true-hide' instead of intellihide.

Let's hope we'll get that in Natty. At first I was fond of Intellihide, but that quickly "wore off" and now I'd like to see the real autohide coming back.

It would also be nice to see options to disable special launchers:

[[img]http://img.xrmb2.net/images/t799848.jpeg[/img]](http://img.xrmb2.net/images/799848.png)

---

### Post by mc4man on 2011-02-01
> Let's hope we'll get that in Natty. At first I was fond of Intellihide ...

Here's a bug i had on that some time ago, somewhat hopeful though can see it may be a 'if time permits, ect.' ( and understandable considering all the work compiz/unity/gnome-panel have needed and still need

A few me too's wouldn't hurt though.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/688706](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/688706)

Atm it's still fairly simple to turn intelli-hide into true-hide, though in every upgrade a little more is added to the relevant section, hope it doesn't outgrow a little 'logical' editing

On my desktop (23"), I have come to only want true-hide (it's not a space thing at all...
> It would also be nice to see options to disable special launchers:
That would be nice (you had me ck.'ing ccsm..

---

### Post by Astrotrain on 2011-02-01
> **cariboo907 said:**
> You can select the Classic Desktop session from the login screen, whih gets you the gnome 2 panel interface.

I personally use docky2 with Unity.

Yes, I`ve read about that, but in my understanding, it will be only a transisional temporary option.
While thinking more thoroughly about **what is it really that bugs me so much** about the whole Unity concept, or to be more precise, the looks of Unity, I came to the conclusion that actually it comes down to **"unsymmetrical" look of Unity**. Whole that "left-and-top" concept is just not pleasant for my eyes.
Probably that is the main reason why I have asked so many questions about future possibilities and constraints of a new interface, trying to find some "middle-path". 
Since I see that, contrary to my taste, the "left-and-top" concept is considered by mr. Shuttleworth and Ubuntu developers one of the main strong points of Unity, I see no other option but to adjust or transfer to another window manager and desktop enviroment.

---

### Post by tjeremiah on 2011-02-01
> **MacUntu said:**
> 

It would also be nice to see options to disable special launchers:

[[img]http://img.xrmb2.net/images/t799848.jpeg[/img]](http://img.xrmb2.net/images/799848.png)

I hope more options like that pop up in the upcoming updates.

---

### Post by KegHead on 2011-02-01
Hi!

I agree w/MacUntu.

KegHead

---

### Post by Harry33 on 2011-02-01
People, a lot of people, here on the forum keep asking possibilities to change or adjust or even remove certain components of the Unity desktop.
That is very understandable from the users point of view.
I myself really want to stick to "freedom of choice".
I want to uninstall meta packages and applications I do not use, for instance.
I want to change the outlook of desktop.
But what do developers tell us. What do they say.
Unfortunately I can read too many "no no" answers.
Unfortunately I can see too much ignorance.

Please understand this - a good working desktop is both flexible and user friendly.

---

### Post by cariboo on 2011-02-01
There will be a lot of no answers until Unity matures,  much of Unity is still barely usable, I'd suggest we wait until this version is released, and make suggestions for added features at UDS-O. Give the devs time to implement planned features.

We still have choice, no-one says you have to use Unity, there are many other DEs in the repositories, if Unity doesn't fit the way you use your computer, choose a different desktop environment.

---

### Post by SushiR on 2011-02-01
> **Harry33 said:**
> People, a lot of people, here on the forum keep asking possibilities to change or adjust or even remove certain components of the Unity desktop.
That is very understandable from the users point of view.
I myself really want to stick to "freedom of choice".
I want to uninstall meta packages and applications I do not use, for instance.
I want to change the outlook of desktop.
But what do developers tell us. What do they say.
Unfortunately I can read too many "no no" answers.
Unfortunately I can see too much ignorance.

Please understand this - a good working desktop is both flexible and user friendly.

To a certain extent, I agree with you. But in fact I don't. You (as everyone else) is free to use the I'm-used-to-it Gnome desktop, as you were before. PLUS you're free to switch to another (Ubuntu-close) distro, that fits your needs the most. Mint is one of those, because they're very community orientated and very strict with packages. Which is just fine, because they offer a valid alternative to Ubuntu and will neither go Unity nor Gnome Shell with their next release. PLUS they offer an alternative for Debian lovers (LMDE). PLUS they offer various other flavors, too.

As for me, I love both worlds. I like Unity a great deal on my netbook, but I'm not sure if I will like it on my desktop...

---

### Post by lucazade on 2011-02-01
> **cariboo907 said:**
> There will be a lot of no answers until Unity matures,  much of Unity is still barely usable, I'd suggest we wait until this version is released, and make suggestions for added features at UDS-O. Give the devs time to implement planned features.

We still have choice, no-one says you have to use Unity, there are many other DEs in the repositories, if Unity doesn't fit the way you use your computer, choose a different desktop environment.

I agree with you completely..
.. and if out-of-the-box settings of Unity will be optimal I won't need any customization options.

---

### Post by Harry33 on 2011-02-01
> **SushiR said:**
> To a certain extent, I agree with you. But in fact I don't. You (as everyone else) is free to use the I'm-used-to-it Gnome desktop, as you were before. PLUS you're free to switch to another (Ubuntu-close) distro, that fits your needs the most. Mint is one of those, because they're very community orientated and very strict with packages. Which is just fine, because they offer a valid alternative to Ubuntu and will neither go Unity nor Gnome Shell with their next release. PLUS they offer an alternative for Debian lovers (LMDE). PLUS they offer various other flavors, too.

As for me, I love both worlds. I like Unity a great deal on my netbook, but I'm not sure if I will like it on my desktop...

Right, I already know all that. That is actually not full "freedom of choice".
What if I want to stay with Ubuntu, and would like to use a desktop with Compiz and perhaps themeable, adjustable Unity.

Have anyone else noticed Unity and Gnome-shell are moving to the same direction (when only outlook is evaluated).

---

### Post by jerrylamos on 2011-02-01
> **Harry33 said:**
> Please understand this - a good working desktop is both flexible and user friendly.

Harry33, as a tester I'm trying to run Unity like Ubuntu has it set up to look for bugs as an "ordinary user". Whether I like Unity or not.

Only two of my five test pc's will run Unity 3D.  And on one of the two that will run Unity, Compiz hangs every 5 to 10 minutes.

The one that will run as much Unity as is functional is an Aspire 1 netbook with intel N10 video graphics.

That's Alpha 1.

Now lets try Alpha 2.

Having said all that, it takes less keystrokes and less windows and less mouse actions for me to do more work using Ubunto 10.10 with classic Gnome 2.

O.K., there's more "eye candy" on Unity 3D, which I don't see because I run full screen applications internet browse, digital pictures, write, spreadsheet, internet email, home network, ... How much overhead does Compiz consume to find out the desktop isn't in view anyway?

Jerry

---

### Post by cariboo on 2011-02-01
Netbooks are what Unity was initially designed for, the ui gets out of the way when you run apps in full screen, but is still there when you need it. 

jerrylamos, you may want to  test drive some of the other netbooks versions out there, I tried Easy Peasy, Moblin (Meego) , Jolicloud and KDE before deciding on Ubuntu, there are several more available now.

---

### Post by jerrylamos on 2011-02-01
> **cariboo907 said:**
> Netbooks are what Unity was initially designed for, the ui gets out of the way when you run apps in full screen, but is still there when you need it. 

I just tried Ubuntu 10.10 netbook USB live edition briefly.  The big fat left column was there all the time and didn't get out of the way.  Now maybe there's some hide option I could try, but why bother, the regular Maverick Gnome classic desktop and Natty Unity 3D run fine on it.

Lately the only non-Ubuntu I run on occasion is tiny core.  Fast!  Easy, once you figure out how to install basic stuff.  Just uses a few directories on an existing Ubuntu install.  Unity like selection icons. Hides fine.  Runs on all the pc's because it doesn't have Compiz.

I've tried Fedora, Suzie, Debian CD live with LXDE, slitaz, Slax, ...

Jerry

---

### Post by sgage on 2011-02-01
There seems to be some sort of movement to have change for the sake of change, eye-candy because you can, usability be damned.

I'm not against progress in the UI and such, but there seems to be this random proliferation of interfaces that don't particularly enhance usability.

Oh, but we must have a "modern" look.

I'm not encouraged by the direction that Ubuntu is headed in.

---

### Post by lucazade on 2011-02-01
> **sgage said:**
> There seems to be some sort of movement to have change for the sake of change, eye-candy because you can, usability be damned.

I'm not against progress in the UI and such, but there seems to be this random proliferation of interfaces that don't particularly enhance usability.

Oh, but we must have a "modern" look.

I'm not encouraged by the direction that Ubuntu is headed in.

"Eye-candy" and "modern look" are not the reasons behind Unity although it could seem at first glance.
It is not all about appereance. :)

---

### Post by cariboo on 2011-02-01
> I just tried Ubuntu 10.10 netbook USB live edition briefly. The big fat left column was there all the time and didn't get out of the way. Now maybe there's some hide option I could try, but why bother, the regular Maverick Gnome classic desktop and Natty Unity 3D run fine on it.

Applications open up over top of the menu in 10.10 on some apps, you have to remember, that Unity in 10.10 is a sort of orphan, as there won't be anymore development on the the mutter version. You really should have a look at some of the other netbook offerings, as I'm sure you'll get tired of Win 7 starter edition fairly soon.

---

### Post by kyleabaker on 2011-02-01
> **lucazade said:**
> "Eye-candy" and "modern look" are not the reasons behind Unity although it could seem at first glance.
It is not all about appereance. :)

I agree. Sure, they are trying to make an elegant user interface at the same time while they are completely redesigning the layout, but its obvious by the intellihide and removal of the title bar on maximized windows and changes to the menu that they are working towards more usable screen real-estate and if a modest dose of eye-candy comes along with that then its fine with me.

Wow, that was a long run-on sentence. :lolflag:

---

### Post by jerrylamos on 2011-02-02
> **cariboo907 said:**
>  I'm sure you'll get tired of Win 7 starter edition fairly soon.
Cariboo,

I got tired of Win 7 starter immediately.  The only thing I use it for is Skype because Acer Win software has it set up for Acer's video hardware nicely.  On very rare occasions there are some web sites that need Internet Explorer. The 250 GB hard drive is split half for Ubuntu half for Win 7.

Natty is running on an external USB hard drive in hopes that the Alpha level code won't screw up the internal hard drive. I've had Alpha Ubuntu's trash things pretty good so on the external USB I hope I'm limiting the trash to the USB where I can re-install readily. 

Maverick is installed on the internal hard drive because of forum reports of Natty Grub 2 not picking up the Win 7 loader.  

Now for Alpha 2.  Hold my hat.  On the external USB hard drive.

Jerry

---

### Post by jerrylamos on 2011-02-02
> **lucazade said:**
> "Eye-candy" and "modern look" are not the reasons behind Unity although it could seem at first glance.
It is not all about appearance. :)

Lucazade,

What else is there in Unity 3D besides "appearance"?  Any pointers to forums or Wiki or whatever?

So far as an "ordinary user" tester I don't see anything Unity does better with my applications such as internet news & research, video, write, spreadsheet, internet email, digital picture processing & printing, home network, ... all those things I use the computer for.

On occasion navigating around my full screen page the Unity side bar pops up on top of what I'm doing and I have to shove it out of the way.  Tiny core has a Unity/Apple type application bar that never comes up unless I want it.  The tiny core icons enlarge & squirm & add titles as the mouse hovers over, runs on all the pc's, all this in 11 MB (plus more MB for applications of course).  No tiny core doesn't do "shadows".  Ubuntu Alpha 1 Compiz "eye candy shadows" crash regularly on my IBM Thinkpad T40.  

I do run Unity 3D on the one PC of my 5 test computers, the netbook, that it will run on reliably, just looking for bugs. Perhaps Alpha 2 will run on another one of them without Alpha 1 Compiz crashing.  Launchpad bugs are entered.  We'll see in a couple days.

Thanks, Jerry

---

### Post by lucazade on 2011-02-02
> **jerrylamos said:**
> Lucazade,

What else is there in Unity 3D besides "appearance"?  Any pointers to forums or Wiki or whatever?

So far as an "ordinary user" tester I don't see anything Unity does better with my applications such as internet news & research, video, write, spreadsheet, internet email, digital picture processing & printing, home network, ... all those things I use the computer for.

On occasion navigating around my full screen page the Unity side bar pops up on top of what I'm doing and I have to shove it out of the way.  Tiny core has a Unity/Apple type application bar that never comes up unless I want it.  The tiny core icons enlarge & squirm & add titles as the mouse hovers over, runs on all the pc's, all this in 11 MB (plus more MB for applications of course).  No tiny core doesn't do "shadows".  Ubuntu Alpha 1 Compiz "eye candy shadows" crash regularly on my IBM Thinkpad T40.  

I do run Unity 3D on the one PC of my 5 test computers, the netbook, that it will run on reliably, just looking for bugs. Perhaps Alpha 2 will run on another one of them without Alpha 1 Compiz crashing.  Launchpad bugs are entered.  We'll see in a couple days.

Thanks, Jerry

Jerry

I prefer to not repeat stuff has already been said a lot of time and open here a recurring discussion.
I've a Thinkpad T40 and gma500 netbook that doesn't support Unity3D so I understand your issues but I've also a Nvidia250 based pc and a Ati3200 notebook and Unity3D perform very well, provides a pleasant Desktop and with a good screen real estate.

These are Hw requirements for Unity3D
[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)

Unity2D is supported instead by almost all gfx cards, gnome-panel is always there.. to me this looks reasonable.

---

### Post by Astrotrain on 2011-02-02
> **lucazade said:**
> Jerry

Unity2D is supported instead by almost all gfx cards, gnome-panel is always there.. to me this looks reasonable.

   Well, not entirely true, at least for the "gnome-panel always  there" part. Gnome-panel will be there for 11.04, but probably not much  longer than that. Why? Simply because Gnome project itself has turned  into a Gnome Shell direction as we all know, so there will be no more  support for the Gnome panel. If this is not so, please correct me and make my day much happier.
   Let us put things into another  perspective. In a present typical desktop computer hardware  configuration Unity might seem fairly unnecessary, but I guess that its`  introduction is just the Ubuntu teams` way of dealing with inevitable  touch/small screen ongoing future in the most differing and unique way  possible. Ipad is already here for quite some time, and Win7 is very  touch capable.
  Last time I was checking, Canonical (through Ubuntu)  never gave up the ambition to make Ubuntu approachable to as wider  audience as possible, and so I see all of this as just one more step  towards that goal.
  Time will show if this is the proper way to do it.

---

### Post by lucazade on 2011-02-02
> **Astrotrain said:**
> Well, not entirely true, at least for the "gnome-panel always  there" part. Gnome-panel will be there for 11.04, but probably not much  longer than that. Why? Simply because Gnome project itself has turned  into a Gnome Shell direction as we all know, so there will be no more  support for the Gnome panel. If this is not so, please correct me and make my day much happier.
   Let us put things into another  perspective. In a present typical desktop computer hardware  configuration Unity might seem fairly unnecessary, but I guess that its`  introduction is just the Ubuntu teams` way of dealing with inevitable  touch/small screen ongoing future in the most differing and unique way  possible. Ipad is already here for quite some time, and Win7 is very  touch capable.
  Last time I was checking, Canonical (through Ubuntu)  never gave up the ambition to make Ubuntu approachable to as wider  audience as possible, and so I see all of this as just one more step  towards that goal.
  Time will show if this is the proper way to do it.

Gnome-panel will be *probably* ported to gtk3 so if Ubuntu will switch to gtk3 we'll still have a panel.

Unity scales well from a netbook to a wide screen, at least I find it usable with a 12' and a 24' screen, it is ready for touch devices (not completely.. menus are not usable atm) and it takes gain from all the latest ubuntu software (indicator, osd notification, global appmenu)... gnomeshell doesn't use these components, mutter is slow as hell, some months ago gnomeshell was everything but usable so unity was an obliged choice.

---

### Post by Zeppelin! on 2011-02-05
I just don't see why many of these things couldn't be abstracted out to modules, particularly since I can only see some of the features of Unity not making me want to kill someone.

Actually, I am now *really* curious why most of this couldn't have been modules for GNOME-Desktop - even if the reason was to reduce bloat and improve load times, I see little reason this couldn't be done with minimal loss, and with the bonus of avoiding hypothetical spaghetti code and having to get into a spat with the GNOME folks.

More to the actual usage side - are there plans to make it simple to adjust Unity by one feature at a time - even to the point of "removing" that feature (reasserting a gnome-desktop feel)?

Or, more to my immediate pleasure - any way to get that sound-musicplayer app combination without Unity?

I'm not against Unity entirely, just things like docks feel like clutter to me, and I always want an arbitrary arrangement menu to help me remember what I even have on this computer.

---

### Post by cariboo on 2011-02-05
> Or, more to my immediate pleasure - any way to get that sound-musicplayer app combination without Unity?

It is available when you select the Classic Desktop, from the session menu on the login screen.

---

### Post by VeeDubb on 2011-02-05
> **Zeppelin! said:**
> ....I always want an arbitrary arrangement menu to help me remember what I even have on this computer.

+1

That's been my one big enduring complaint about Gnome-Shell, Unity and even OSX on my fiance's macbook.  I have quite a bit of software installed on my desktop, and not having organized menus is a real pain.  Assuming the unity menu works more or less like the netbook version once it's complete, it will have some organization, but not nearly enough.  If I've got software that I installed from 3rd parties that doesn't go into one of the categories, then my only option is to sift through every piece of software on my system until I find it.

And before anybody points out the lovely search features, that doesn't help when it's a program you don't use on a daily basis, and can't remember the name of because it had some non-obvious name.

---

### Post by Astrotrain on 2011-02-05
Well maybe a good solution would be to implement a Gnome menu launcher or applet like the one already available for dock applications?

---

### Post by seeker5528 on 2011-02-05
> **VeeDubb said:**
> +1

That's been my one big enduring complaint about Gnome-Shell, Unity and even OSX on my fiance's macbook.  I have quite a bit of software installed on my desktop, and not having organized menus is a real pain. 

Organization sometimes leaves something to be desired, but usually the bigger issues for me are....

[list]A: Not showing the real name of an application in it's menu entry, so some times you might have 'Web Browser' 3 times instead of 'Web Browser (Firefox)', 'Web Browser (Chrome)', etc... or like with the media players sometimes they show with a name that is different from each other, but still doesn't include the actual name of the application.[/list]

[list]B: Instead of assuming that if you installed something you actually want to see it in the menus somewhere, Gnome hides some stuff from you, KDE hides some different stuff from you, etc...[/list]

What Gnome Shell and Unity do/will provide for this I wouldn't call a menu, but are an organized, if not complete, display of available apps. What options you get for customizing the organization, adding apps, or showing/hiding apps remains to be seen.

Later, Seeker

---

### Post by VeeDubb on 2011-02-08
> **Astrotrain said:**
> Well maybe a good solution would be to implement a Gnome menu launcher or applet like the one already available for dock applications?

The ability for people to develop other widgets/gadets/plugins (whatever you want to call them) for the Unity launcher would be a HUGE boon and seriously improve the utility and customizability of the interface.

---

### Post by jerrylamos on 2011-02-08
> **VeeDubb said:**
> The ability for people to develop other widgets/gadets/plugins (whatever you want to call them) for the Unity launcher would be a HUGE boon and seriously improve the utility and customizability of the interface.
On Gnome I've got a choo choo train of applets on the top panel for stuff I use a lot.  Gnome also sticks a few applets up there with stuff I have never and will never use, but Gnome is very poor about letting me delete selectively.  The bottom panel I delete right away.

So far I don't know how to do put applets on the Unity 3D top panel so I've lost a useful screen line.  

Shuttleworth thinks he can improve Ubuntu acceptance with Unity 3D, and he's paying the bills.  Only reason I use it at all is as a tester looking for bugs.

Really nice having classic "no effects".  Without "no effects" here I'll be running overlapping full screen applications and WHAM Compiz will seg fault.  I have no idea what Compiz was trying to do because nothing it could do would not even be visible.

Jerry

---

### Post by Astrotrain on 2011-02-08
> **jerrylamos said:**
> 
Shuttleworth thinks he can improve Ubuntu acceptance with Unity 3D, and he's paying the bills. 
Jerry

  This is the key point. He **thinks** he can improve Ubuntu acceptance with Unity 3D. But is his thinking correct? Well maybe he did some surveys or something, but (for now at least) I don`t see many people being overly enthusiastic about these changes that are going to take place.
  First thought that goes through my mind is : "It`s maybe too much too soon and too sudden."
  I hope I am wrong.
Main problem is forcing a typical tablet interface into a desktop world. Will people like it? I am not so convinced as Shuttleworth seems to be.

---

### Post by cariboo on 2011-02-08
From what I've seen elsewhere, there seems to be far more acceptance and excitement than here on the forums.

---

### Post by Zeppelin! on 2011-02-08
But, would you say a tech news outlet, for instance, has the same investment in ubuntu as, say, a regular forum poster?

Really, I wouldn't mind Unity so much if it weren't for compatibility. I love modularity. Even with Windows you can completely redesign the desktop to your liking without going into incompatibility (though you may have to do some things Microsoft most definitely didn't want you to), similarly, it seems most of Unity's features could be done without having to create a whole new shell for it.

I am deeply interested in why this wasn't so.

---

### Post by cariboo on 2011-02-08
The classic two panel gnome interface will gradually disappear, unless someone else steps up to keep it alive. Unity and Gnome-shell are replacements.

---

### Post by Merk42 on 2011-02-08
> **cariboo907 said:**
> The classic two panel gnome interface will gradually disappear, unless someone else steps up to keep it alive. Unity and Gnome-shell are replacements.
And more importantly, when it does disappear, it will be GNOME, not Ubuntu, to 'blame'.

---

### Post by forcecore on 2011-02-09
Until 2D is not correctly supported out of box then it is impossible to remove panels, millions of computers has conflicts or very buggy 3D. I have installed lot of Ubuntu-s and several computers had slow or buggy or non working 3D mode.

---

### Post by lucazade on 2011-02-09
> **forcecore said:**
> Until 2D is not correctly supported out of box
i'm able to get it working with intel, nvidia and ati cards without issues (also with inside virtual machines).

> **forcecore said:**
> then it is impossible to remove panels,
unity-2d-launcher and unity-2d-panel are separate processes and could be started or used separately.

> **forcecore said:**
> millions of computers has conflicts or very buggy 3D. 
only old gfx cards have issues with 3d.. unity-2d or gnome-panel are here also for this reason.

> **forcecore said:**
> I have installed lot of Ubuntu-s and several computers had slow or buggy or non working 3D mode.
this is your situation and  that doesn't reflects mine.

---

### Post by mc4man on 2011-02-09
> **MacUntu said:**
> Let's hope we'll get that in Natty. At first I was fond of Intellihide, but that quickly "wore off" and now I'd like to see the real autohide coming back.
[/url]
got an email that a fix was committed on this, maybe next unity release
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/688706](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/688706)

---

### Post by lucazade on 2011-02-09
> **mc4man said:**
> got an email that a fix was committed on this, maybe next unity release
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/688706](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/688706)

I believe this is the patch in action!
[http://www.youtube.com/watch?v=yODKjrdw-88&feature=player_embedded](http://www.youtube.com/watch?v=yODKjrdw-88&feature=player_embedded)

---

### Post by VMC on 2011-02-09
> **lucazade said:**
> i'm able to get it working with intel, **_nvidia_** and ati cards without issues (also with inside virtual machines).

How?

As soon as I start natty, I get scrambled display. Only after adding to start string "*nomodeset*" do I get a display , but that leaves out Unity.

---

### Post by lucazade on 2011-02-09
> **VMC said:**
> How?

As soon as I start natty, I get scrambled display. Only starting using added string*nomodeset* works, but that leaves out Unty.

Using xorg 1.9 and nvidia-current binary blob with a 250gts card :) 

nomodeset disables only kms feature (correct resolution for virtual terminals and plymouth splash) so I don't understand how this can affect your X session or Unity... mmh

---

### Post by mc4man on 2011-02-09
> **lucazade said:**
> I believe this is the patch in action!

Yep - that's 'true-hide', been using for quite some time, should make for an excellent option for some.

For the occasional times I wish the launcher to stay exposed I've bound a keystoke combo and for the moment a desktop launcher to a small 'toogle' script

---

### Post by VMC on 2011-02-09
> **forcecore said:**
> Until 2D is not correctly supported out of box then it is impossible to remove panels, millions of computers has conflicts or very buggy 3D. I have installed lot of Ubuntu-s and several computers had slow or buggy or non working 3D mode.

> **lucazade said:**
> i'm able to get it working with intel, nvidia and ati cards without issues (also with inside virtual machines).

This is what I'm referencing. @forecore states it doesn't work out of the box. You imply that it does. 

In reality you get it to work by downgrading to previous X.

---

### Post by lucazade on 2011-02-09
> **VMC said:**
> This is what I'm referencing. @forecore states it doesn't work out of the box. You imply that it does. 

In reality you get it to work by downgrading to previous X.

"Until 2D is not correctly supported out of box"

unity-2d works without downgrading xorg and with both nouveau and nvidia-current...
so it is out of the box.

unity-3d needs nvidia-current (here with a 250gts) and downgrade xorg.. but this is a working in progress and will be fixed in next weeks when nvidia will release a new xorg 1.10 compatible drivers.

---

### Post by mc4man on 2011-02-09
> unity-3d needs....
If you have an AGP nvidia card and wish to test from a fully updated install them quite likely nouveau 3d can serve as a temporary fix till nvidia drivers/xserver  are back in business.

(or if for some reason one liked nouveau 3d and current card will not work then keep an eye here
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/710588](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/710588)

---

### Post by lucazade on 2011-02-09
> **mc4man said:**
> If you have an AGP nvidia card and wish to test from a fully updated install them quite likely nouveau 3d can serve as a temporary fix till nvidia drivers/xserver  are back in business.

(or if for some reason one liked nouveau 3d and current card will not work then keep an eye here
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/710588](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/710588)

unfortunately my card didn't work well with nouveau + 3d support (xorg 1.9)
it was full of graphical artefacts and session usually freeze :/

thanks for pointing this bug out.. i've this issue! subscribed.

---

### Post by forcecore on 2011-02-10
Depending of people who has money to buy correct and modern hardware but as my case i had lot loooot of people who use cheaply builded pc-s and almost half of them did not work 3D correctly SO fact is that 2D desktop mode MUST have forever.

Almost 90% people who got Ubuntu had main target to use internet and multimedia(including friend stats too who installs Ubunsu-s). Most of them had cheap used pc-s with some old GeForce 2,4,titanium or ATI or some other unknown old cards AND second that some people hated 3D effects.

But i am glad there is UCK, at least i can fix most Ubuntu mistakes and flaws.

---

### Post by lucazade on 2011-02-10
> **forcecore said:**
> Depending of people who has money to buy correct and modern hardware but as my case i had lot loooot of people who use cheaply builded pc-s and almost half of them did not work 3D correctly SO fact is that 2D desktop mode MUST have forever.

Almost 90% people who got Ubuntu had main target to use internet and multimedia(including friend stats too who installs Ubunsu-s). Most of them had cheap used pc-s with some old GeForce 2,4,titanium or ATI or some other unknown old cards AND second that some people hated 3D effects.

But i am glad there is UCK, at least i can fix most Ubuntu mistakes and flaws.

I'm wondering what changed from Maverick.. everything, including gnome-panel and metacity, will be available in Natty.

Ubuntu *added* Unity-3D and Unity-2D (which works with non-accelerated graphics cards).
They *haven't removed anything*, so beside don't like graphical aspect of Unity-*D I really don't see the problem.

I could understand if something will be removed but this is not the case.
If the problem is gnome-panel that is no more developed this is not a issue derived from Ubuntu.

---

### Post by forcecore on 2011-02-10
I like Unity a lot and i like to see Unity to destroy panels but 2D mode is needed out of box in final .iso to eliminate panels so Unity 100%.

---

### Post by cariboo on 2011-02-10
As has been said in other places, Unity 2D will not be the fall back in Natty, we can always hope it is in Natty+1 (no name chosen for 11.10 yet).

---

### Post by mc4man on 2011-02-10
The unity 3.4.2 is out, well worth reading thru the changelog, many of the bugfixes are features added/fixed. 
excellent progress

While not listed 'autohide' is now the true type autohide
'Intelli-hide' is now 2 options - Dodge (all) and Dodge active only

Edit :
For those few that want the autohide (true) but may wish to occasionally expose the launcher other than thru Super or mouse trigger an adjusted toggle script, can be used with a Desktop launcher or bound to key comb (as of 3.4.2
```
#!/bin/bash
key_value=$(gconftool --get /apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode)
echo $key_value | grep "0"
if [[ $? -eq 0 ]] ; then
	gconftool --type Integer --set /apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode 1
else
	gconftool --type Integer --set /apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode 0
fi
```

the keys are
0 = none
1 = autohide
2 = Dodge
3 = Dodge active

---

### Post by webme on 2011-02-10
Like mc4man sais, Unity 3.4.2 is out, but Autohide is listed in Unity plugin by default.
There are many, neew interesting features like drag&drop into the dock, search is functional, if you want to see some pictures take a look at this article [http://iloveubuntu.net/natty-narwhal-unity-342-gets-awesome-ui-improvements-ubuntu-not-reinventing-wheel-building-aeroplane](http://iloveubuntu.net/natty-narwhal-unity-342-gets-awesome-ui-improvements-ubuntu-not-reinventing-wheel-building-aeroplane)

---

### Post by mc4man on 2011-02-10
> but Autohide is listed in Unity plugin by default.
Sorry, I meant in the changelog the bug fix for that wasn't listed, so wasn't sure if it (the 'new' autohide) was included in this update. - appears it was.
(though have noticed the potential for some 'odd' behavior w/ it, maybe just a temporary glitch, maybe not

---

### Post by webme on 2011-02-15
Super great news for Natty Narwhal!!!
This days (or by the end of the week), Natty will get systray support, panel gtk theming support (it will support Ambiance, too), panel opacity and blur.
What is the source of this info?
Neil J Patel, Unity main dev, says so on his Twitter account, he said that all this are already finished.

---

### Post by go7Ul1ai on 2011-02-15
> **webme said:**
> Super great news for Natty Narwhal!!!
This days (or by the end of the week), Natty will get systray support, panel gtk theming support (it will support Ambiance, too), panel opacity and blur.
What is the source of this info?
Neil J Patel, Unity main dev, says so on his Twitter account, he said that all this are already finished.

Exciting times :)

---

### Post by teh603 on 2011-02-16
Haven't been watching the thread that actively, but I just wanted to make sure that Unity isn't going to be coming to Kubuntu. I'm a little hesitant about downloading the .iso until the new X11 stack is out.

---

### Post by Harry33 on 2011-02-16
> **teh603 said:**
> Haven't been watching the thread that actively, but I just wanted to make sure that Unity isn't going to be coming to Kubuntu. I'm a little hesitant about downloading the .iso until the new X11 stack is out.

1) Unity is one shell type in Gnome. 
Originally Gnome.org is forwarding its own shell type (Gnome-shell) into Gnome3.
However, Canonical is of the opinion that Gnome3 will not be released early enough for Natty Narwhal. That being the case, Canonical wanted to present a special shell into Ubuntu (Unity).
For the time being Unity depends on GTK+2.0. Gnome-shell depends on GTK+3.0.

Of course it would be possible to somehow port Unity into K desktop too, but I haven't heard any plans into that direction. There simply is no need to.

2) Downloading Natty at this development phase demands skills to recover from bugs, some of which are true show stoppers. The xserver 1.10 works right now (but only with open source graphics drivers).

---

### Post by cariboo on 2011-02-16
The 2D version of Unity should work on Kubuntu, as it is written using QT libraries.

---

### Post by Harry33 on 2011-02-16
> **cariboo907 said:**
> The 2D version of Unity should work on Kubuntu, as it is written using QT libraries.

Thanks Cariboo, that is true.
Perhaps teh603 wanted to know if Unity will ever going to be default DE in K.

---

### Post by cariboo on 2011-02-16
> **Harry33 said:**
> Thanks Cariboo, that is true.
Perhaps teh603 wanted to know if Unity will ever going to be default DE in K.

That would be up to the kubuntu developers, as of now, it won't.

---

### Post by Starks on 2011-02-16
How do I get the search bar to work? I type and no programs shows up.

---

### Post by mc4man on 2011-02-16
If you are fully updated the it should work to some degree, have you tried typing just a few letters?
(the search in the dash seems to be somewhat nonsense

Just noticed some odd memory use (again) while using search in the places and dash. Will have to set up a pidstat, may be a return of memory leak seen previously in the dash, though smaller

Edit: definitely seeing small but noticeable leak from the places and probably dash (good thing is you use them enough compiz will likely crash anyway

---

### Post by syltty on 2011-02-17
[Usability Testing of Unity]("http://design.canonical.com/2010/11/usability-testing-of-unity/")

---

### Post by ikt on 2011-02-17
> **syltty said:**
> [Usability Testing of Unity]("http://design.canonical.com/2010/11/usability-testing-of-unity/")

Good to see.

---

### Post by teh603 on 2011-02-17
> **Harry33 said:**
> Thanks Cariboo, that is true.
Perhaps teh603 wanted to know if Unity will ever going to be default DE in K.Yes, that's what I wanted to know.

> **cariboo907 said:**
> That would be up to the kubuntu developers, as of now, it won't.Good. At least there's a few places where I can hide from it and still run Ubuntu.

---

### Post by tjeremiah on 2011-02-21
will we ever be able to minimize a window with the unity bar by simply clicking the icon with the program is open?

---

### Post by cariboo on 2011-02-21
> **tjeremiah said:**
> will we ever be able to minimize a window with the unity bar by simply clicking the icon with the program is open?

There is a feature freeze today, so I don't think we'll see it in this release

---

### Post by mc4man on 2011-02-21
> will we ever be able to minimize a window with the unity bar by simply clicking the icon with the program is open?
I would think at some point it could be added as a r. click option
Atm the l. click is used to return focus and if multiple windows of same app are open start scale

(a default option of scale will minimize 'pulled' windows to the launcher that are on the current workspace by clicking on an open area of the screen while in the 'pull' screen. Any windows pulled from other workspaces, if any, are returned to there orig. workspace

---

### Post by tjeremiah on 2011-02-21
> **cariboo907 said:**
> There is a feature freeze today, so I don't think we'll see it in this release
wow, time really is flying by fast.

---

### Post by castrojo on 2011-02-22
> **tjeremiah said:**
> will we ever be able to minimize a window with the unity bar by simply clicking the icon with the program is open?

Is there a bug report for this?

---

### Post by isaacahloe on 2011-02-22
> **castrojo said:**
> Is there a bug report for this?


I personally love the current behavior of clicking an icon while it's open. it displays all of the windows that app currently has open side by side, which for me was a huge workflow increaser.

---

### Post by vikktor91 on 2011-02-22
I didn't found bug report for this(maybe its not :confused:).So here's the situation:
For instance if I have one app with 2 windows(eg nautilus,skype...), and 1 of them if maximized and the other one minimized when I click the launcher it will focus only the maximized window.If I need the minimized, I need to minimize the maximized window and again click the launcher.It is realy annoying when there are 3-4-5 windows from 1 app.Is this a bug or not?

---

### Post by terry_gardener on 2011-02-22
> **cariboo907 said:**
> There is a feature freeze today, so I don't think we'll see it in this release

thought feature freeze was thursday 24/02/2011 and UI freeze next month.

thats what is says on the release schedule

2010/10/28 Developer Summit
2010/11/25 Feature Definition Freeze
2010/12/02 Alpha 1
2010/12/30 Debian Import Freeze
2011/02/03 Alpha 2
2011/02/24 Feature Freeze
2011/03/03 Alpha 3
2011/03/24 UI Freeze
2011/03/31 Beta 1
2011/04/14 Beta 2 & Final Freeze
2011/04/28 Ubuntu 11.04

---

### Post by cariboo on 2011-02-22
I was just going by email on the devel-announce mailing list.

---

### Post by mc4man on 2011-02-22
> **vikktor91 said:**
> I didn't found bug report for this(maybe its not :confused:).So here's the situation:
For instance if I have one app with 2 windows(eg nautilus,skype...), and 1 of them if maximized and the other one minimized when I click the launcher it will focus only the maximized window.If I need the minimized, I need to minimize the maximized window and again click the launcher.It is realy annoying when there are 3-4-5 windows from 1 app.Is this a bug or not?

for myself it is working fine for open and minimized windows, whether on 1 or multiple workspaces.
(The main reason when throwing minimized windows into the mix is I never use maxed windows.

In the scenario you've laid out, yes, it should probably be handled better - here it means, (your scenario) - 
 1 click in icon pulls the maxed window
Then a click anywhere outside of the pulled window minimizes that maxed window ('show desktop' option in scale
Then a 2nd click on icon opens all the windows minimized to the icon.

There is an open scale bug - I filed it when scale was not pulling from properly from multiple workspaces.
That has since been fixed, but the bug is still open so some other work is intended.
(selfishly I wish they'd leave as is, though as long as the current or bulk of current behavior is left I'd be ok.
You may wish to present your concerns w/ the maxed/minimized combo there

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/707214](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/707214)

---

### Post by webme on 2011-02-24
Unity has been updated to 3.4.6, brings some new interesting things (super shortcuts, bigger search area, partitions icons, etc).

If you want to see a picture take a look @ [http://iloveubuntu.net/unity-346-gets-super-shortcuts-bigger-search-area-and-consistent-behavior-ubuntu-1104](http://iloveubuntu.net/unity-346-gets-super-shortcuts-bigger-search-area-and-consistent-behavior-ubuntu-1104)

---

### Post by terry_gardener on 2011-02-25
are we going to see the ability to scroll through the apps and files in dash using the mouse wheel so we dont have to use the scroll bar constantly.

---

### Post by SushiR on 2011-02-25
> **terry_gardener said:**
> are we going to see the ability to scroll through the apps and files in dash using the mouse wheel so we dont have to use the scroll bar constantly.

That's one thing I'm missing, too.

---

### Post by webme on 2011-02-25
> **terry_gardener said:**
> are we going to see the ability to scroll through the apps and files in dash using the mouse wheel so we dont have to use the scroll bar constantly.

This are little things that really matters.
Hope we will see this soon!

---

### Post by webme on 2011-02-25
From what I've understand, Monday will be the "getting awesome" Unity day.

---

### Post by terry_gardener on 2011-02-25
should a bug be raised for this to be added. 

if so i can raise a bug report. 

i know it is only a little thing but can affect usability.

---

### Post by KegHead on 2011-02-25
Hi!

Awesome day?

KegHead

---

### Post by tjeremiah on 2011-02-25
> **webme said:**
> From what I've understand, Monday will be the "getting awesome" Unity day.
any hints as to what?

---

### Post by SushiR on 2011-02-25
Is it just me or is scrolling in Dash (with those scrollbars) horrible slow?

---

### Post by webme on 2011-02-25
> **tjeremiah said:**
> any hints as to what?

I don't know what exactly is going to happen, but Neil J Patel (Unity main dev) said that Unity 3.4.6 was about stability and usability and Monday we will see a sexy UI related Unity.

---

### Post by KegHead on 2011-02-25
Hi!

If it's true about sexy & stability I'm sold.

KegHead

---

### Post by SushiR on 2011-02-25
> **KegHead said:**
> Hi!

If it's true about sexy & stability I'm sold.

KegHead

Yeah, gimme more of that sexy stuff (as well as stability)

---

### Post by ratcheer on 2011-02-25
> **SushiR said:**
> Yeah, gimme more of that sexy stuff (as well as stability)

Right now, I would just like some stability, please. I am almost always running Natty in the Classic Desktop.

Tim

---

### Post by jerrylamos on 2011-02-25
I run Unity for testing purposes.  Currently I don't know what is supposed to be operational and what is not, so it's hard to write bugs.

If Natty gets mangled up when I'm doing copying internet to LibreOffice I just reboot Maverick.

And some things I haven't found out how to do.  So far for my use the top line in Gnome has a bunch of applets.  I think Unity will never do that.

Jerry

---

### Post by SushiR on 2011-02-26
Is there a way to assign other keyboard shortcuts to the Unity launcher for app dash etc.?

---

### Post by KegHead on 2011-02-26
Hi!

I really want Unity to work for me.

We'll see when Monday!

KegHead

---

### Post by Framli on 2011-02-28
Not monday.
[QUOTE=njpatel]Unity for A3 will slip 'till tomorrow morn. due to a big Compiz update. No matter, just more time to add features[/QUOTE]
[https://identi.ca/notice/65652978](https://identi.ca/notice/65652978)

---

### Post by tjeremiah on 2011-02-28
> **Framli said:**
> Not monday.

[https://identi.ca/notice/65652978](https://identi.ca/notice/65652978)

a bit off topic. In his posted screenshot I see he has STEAM. I thought STEAM doesnt work in linux:o

---

### Post by seeker5528 on 2011-02-28
> **tjeremiah said:**
> a bit off topic. In his posted screenshot I see he has STEAM. I thought STEAM doesnt work in linux:o

It's a bit quirky sometimes, but it has more or less been working for quite a while.

It theoretically should be easier to get working these days since certain fonts are included in the wine tree, instead of having to get them separately and since wine-gecko is packaged in the repositories now to provide some of the embedded browser functions that STEAM and some other programs expect.

Later, Seeker

---

### Post by Richard on 2011-03-01
Hello,

I get an issue on Classic Desktop, Unity (left) panel always start instead of the default Gnome global menu.
How can i restore classic session ?

---

### Post by KegHead on 2011-03-01
Hi!

I'm holding off 'til 03-03-11.

KegHead

---

### Post by tjeremiah on 2011-03-01
> **webme said:**
> I don't know what exactly is going to happen, but Neil J Patel (Unity main dev) said that Unity 3.4.6 was about stability and usability and Monday we will see a sexy UI related Unity.

well today is that day. Cant wait to see what the updates will bring later on.

---

### Post by Framli on 2011-03-01
It's building. :-$
[https://launchpad.net/ubuntu/+source/unity/3.6.0-0ubuntu1/+buildjob/2293479](https://launchpad.net/ubuntu/+source/unity/3.6.0-0ubuntu1/+buildjob/2293479)

---

### Post by tjeremiah on 2011-03-01
> **Framli said:**
> It's building. :-$
[https://launchpad.net/ubuntu/+source/unity/3.6.0-0ubuntu1/+buildjob/2293479](https://launchpad.net/ubuntu/+source/unity/3.6.0-0ubuntu1/+buildjob/2293479)

apparently, it just finished :o

---

### Post by Harry33 on 2011-03-01
> **Richard said:**
> Hello,

I get an issue on Classic Desktop, Unity (left) panel always start instead of the default Gnome global menu.
How can i restore classic session ?

Mixing things up?
Ubuntu Classic is the session with Gnome-panels, no Unity
Ubuntu Desktop is the session with Unity, no Gnome-panels

---

### Post by jeffrey.knight on 2011-03-01
Logout. On the login screen on the bottom choose Classic

---

### Post by nuzeb on 2011-03-01
> **Harry33 said:**
> Mixing things up?
Ubuntu Classic is the session with Gnome-panels, no Unity
Ubuntu Desktop is the session with Unity, no Gnome-panels

I think, I know what he means. Got the same problem here. I want to use Gnome Classic Desktop (without Unity) but I'm getting Unity, even though I chose "Gnome Classic Desktop". How do I get my Classic Desktop back?

Update:
OK. Problem seems to be solved with the newest update.

---

### Post by Harry33 on 2011-03-01
> **nuzeb said:**
> I think, I know what he means. Got the same problem here. I want to use Gnome Classic Desktop (without Unity) but I'm getting Unity, even though I chose "Gnome Classic Desktop". How do I get my Classic Desktop back?

Well any saved session may have mixed the setup.
I would delete the appropriate file from Home Folder.
If I remember correct it is here:
.gconf/desktop/gnome/session/saved-sessions

Then of course you might purge packages unity and nux.

---

### Post by Richard on 2011-03-01
Correct, I get Unity launched in Classic Gnome Desktop.
I didn't find the save session gconf key.

To solve this issue, i removed Unity package until the next Unity update.

---

### Post by rg4w on 2011-03-01
I've been anxious to test Natty, but so far I can only get the non-3d UI to show.  As soon as I install the proprietary NVidia drivers my system needs and reboot, I get errors so I've never been able to play with Unity yet.

I've seen some threads about NVidia support still being early days, so I figure these are known issues and I just need to be patient.

Anyone know when this is expected to be addressed? I tried just two days ago and still no go.

Sooooo looking forward to Unity.

---

### Post by Harry33 on 2011-03-01
> **rg4w said:**
> I've been anxious to test Natty, but so far I can only get the non-3d UI to show.  As soon as I install the proprietary NVidia drivers my system needs and reboot, I get errors so I've never been able to play with Unity yet.
I've seen some threads about NVidia support still being early days, so I figure these are known issues and I just need to be patient.
Anyone know when this is expected to be addressed? I tried just two days ago and still no go.
Sooooo looking forward to Unity.

Exactly what errors you get after a reboot with nvidia-current installed?
What is your graphics card?
What driver version are you using?
What additional PPA's are you using.
Did you run "sudo nvidia-xconfig" (after the installation of nvidia-current)?

---

### Post by webme on 2011-03-01
Great news, Unity 3,6 is out and sexyyyyyy (this yyy are for the new fullscreen option).
I f you want to see some pictures, take a look @ [http://iloveubuntu.net/natty-narwhals-dash-now-lovely-unity-36-ui-improvements](http://iloveubuntu.net/natty-narwhals-dash-now-lovely-unity-36-ui-improvements)

---

### Post by cariboo on 2011-03-01
Did you try:

```
sudo nvidia-xconfig
```

some video card/monitors won't work without it, if the monitors edid isn't working properly.

---

### Post by webme on 2011-03-01
> **rg4w said:**
> I've been anxious to test Natty, but so far I can only get the non-3d UI to show.  As soon as I install the proprietary NVidia drivers my system needs and reboot, I get errors so I've never been able to play with Unity yet.

I've seen some threads about NVidia support still being early days, so I figure these are known issues and I just need to be patient.

Anyone know when this is expected to be addressed? I tried just two days ago and still no go.

Sooooo looking forward to Unity.

Choose at log-in Ubuntu Classic, go to synaptic and install unity (check if libunity is installed too).
Reboot, choose Ubuntu Desktop Edition, and try unity --reset    in terminal.

If this isn't working, then, choose @ GRUB 2/6/38 recovery and check Resolve Deoendencies.
It seems to me that you have some broken/missing packages,
Nvidia is working great for me and others.

---

### Post by KegHead on 2011-03-01
Hi!

I'm missing all the fun!

Been at Panera Bread in a dumb meeting.

Still there!

KegHead

---

### Post by SushiR on 2011-03-01
Still missing scrolling on dash (NOT with those scrollbars)

---

### Post by terry_gardener on 2011-03-01
> **SushiR said:**
> Still missing scrolling on dash (NOT with those scrollbars)

very annoying that it doesn't have mouse wheel scrolling as i hate using scroll bars.

---

### Post by fflopes on 2011-03-01
After updating the packages today, I still have no Unity.  I login into the Ubuntu Desktop and nothing happens.  I get the notifications of wireless and Ubuntu One connections coming up, but no panels are loaded whatsoever.  I tried removing all packages with unity* and than reinstalling Unity.  APT-GET did download a new file (missing dependency?), but I got no success yet.  The Classic Desktop works fine.

I tried doing Unity --reset and got the following error:

```

flopes@ubuntu:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
compiz (core) - Error: Couldn't load plugin 'ccp'
unity-panel-service: no process found
compiz (core) - Error: Couldn't load plugin 'ccp'

```My video board is ATI HD3200.  Is it something I have to live with for now?

Thank you in advance,

Felipe

---

### Post by rg4w on 2011-03-01
> **webme said:**
> Choose at log-in Ubuntu Classic, go to synaptic and install unity (check if libunity is installed too).
Reboot, choose Ubuntu Desktop Edition, and try unity --reset    in terminal.

If this isn't working, then, choose @ GRUB 2/6/38 recovery and check Resolve Deoendencies.
It seems to me that you have some broken/missing packages,
Nvidia is working great for me and others.
Thanks for the tips.  I don't have that thumb drive with me right now, but looking forward to trying your suggestions as soon as I get home.  I'll report back how it goes.

---

### Post by VMC on 2011-03-01
> **fflopes said:**
> After updating the packages today, I still have no Unity.  I login into the Ubuntu Desktop and nothing happens.  I get the notifications of wireless and Ubuntu One connections coming up, but no panels are loaded whatsoever.  I tried removing all packages with unity* and than reinstalling Unity.  APT-GET did download a new file (missing dependency?), but I got no success yet.  The Classic Desktop works fine.

I tried doing Unity --reset and got the following error:

```

flopes@ubuntu:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
compiz (core) - Error: Couldn't load plugin 'ccp'
unity-panel-service: no process found
compiz (core) - Error: Couldn't load plugin 'ccp'

```My video board is ATI HD3200.  Is it something I have to live with for now?

Thank you in advance,

Felipe

I haven't been following ati much, but does the install additional drivers selection come up while your in classic. I needed to add the 3d for my nvidia to work with unity.

---

### Post by fflopes on 2011-03-01
I installed proprietary drivers but have removed them and installed the open source package...I have not been suggested to install additional drivers while in classic desktop.

I wonder if the dist-upgrades I did have not broken dependencies or anything...

---

### Post by cariboo on 2011-03-01
If your upgrade didn't complete, try:

```
sudo apt-get -f install
```

---

### Post by jerrylamos on 2011-03-02
> **cariboo907 said:**
> If your upgrade didn't complete, try:

```
sudo apt-get -f install
```

Last couple days "new install" Natty has run much better than just update from previous Natty.  I'd recommend "new install" for more functional results.  i don't like Unity 3D but I'm testing it anyway, and it is much easier to test when a lot more of it is functioning as desired.

I keep solid Meerkat 10.10 and even Lucid 10.04 partitions plus backups of all files around since Natty Alpha and even Beta could go bust any time.

Jerry

---

### Post by rg4w on 2011-03-02
Thanks for your help. Natty's now running here well - I'm typing this on it now. :)

One question about the menu bar design:  I see that when menus are exported to the common menu bar they aren't persistent; that is, they appear only when you bring the mouse over the menu bar.

Is this by design, or scheduled to be fixed before release?

As it is, it misses an opportunity to allow people to aim.

---

### Post by cariboo on 2011-03-02
> **rg4w said:**
> Thanks for your help. Natty's now running here well - I'm typing this on it now. :)

One question about the menu bar design:  I see that when menus are exported to the common menu bar they aren't persistent; that is, they appear only when you bring the mouse over the menu bar.

Is this by design, or scheduled to be fixed before release?

As it is, it misses an opportunity to allow people to aim.

That's by design,  it also changes to whatever window has focus. Menus are useless until you need them. :)

---

### Post by rg4w on 2011-03-02
> **cariboo907 said:**
> Menus are useless until you need them. :)
Menus can never become useful if you don't know they're there.

---

### Post by kyleabaker on 2011-03-02
Anyone know what the plan is for secondary monitors and the top panel? The way that I understood it, they wanted to make secondary monitors use a panel so menus were relative to the focused app on each screen, but the update last night change my panel from spanning both monitors to spanning only the primary.

[[IMG]http://img850.imageshack.us/img850/2595/screenshotd.th.png[/IMG]]("http://img850.imageshack.us/img850/2595/screenshotd.png")

I'd like to see this as an option to enable panels on other screens to handle app name and menu so a busy workspace isn't so painful to work in.

---

### Post by irishjay1 on 2011-03-02
Can somebody tell me a desktop recorder made for unity?

---

### Post by webme on 2011-03-02
> **irishjay1 said:**
> Can somebody tell me a desktop recorder made for unity?
GTK-Recordmydesktop is great, but at the moment it doesn't perform well on Natty (but if you're "desperate" is decent)..
I think we will have to wait to get the same GTK-Record quality as with Mavertick.

---

### Post by Framli on 2011-03-03
On my configuration, byzanz performs slightly better than gtk-Recordmydesktop.

---

### Post by rg4w on 2011-03-03
> **kyleabaker said:**
> Anyone know what the plan is for secondary monitors and the top panel?
I asked Ted Gould about this at the SoCal Linux Expo last weekend, and he said that the plan is to have the menu bar appear on both displays.

It would be ideal if there were a design document available so testers could know what the intended behaviors are.  Does anyone here have that URL?

---

### Post by castrojo on 2011-03-03
It's in a bug report: [https://bugs.launchpad.net/unity/+bug/683084](https://bugs.launchpad.net/unity/+bug/683084)

---

### Post by castrojo on 2011-03-03
Here's some finer tuned bug filing instructions.

[https://wiki.ubuntu.com/Unity/FilingBugs](https://wiki.ubuntu.com/Unity/FilingBugs)

---

### Post by webme on 2011-03-04
Firefox is now fully integrated in Appmenu and it looks great, no PPA required).

---

### Post by mechanic on 2011-03-06
This thread is far too long!

---

### Post by jerrylamos on 2011-03-06
> **mechanic said:**
> This thread is far too long!

"Search" is quite effective!  Lots of useful stuff here.

Jerry

---

### Post by ratcheer on 2011-03-08
Unity question:

When I have a maximized application window and I move my cursor to the upper left corner of the top panel to get the Unity task bar, the Unity task bar shows as a kind of ghost window. If I try to move my cursor down into the ghostlike Unity taskbar, it disappears.

If I un-maximize the application window, and move it to the right, the Unity task bar works just fine.

Is this by design, or is something wrong? If it is by design, I don't like it at all.

Thanks,
Tim

---

### Post by terry_gardener on 2011-03-08
i think it is by design. 

the further top right you go the less transparent it is. if you hit the top right corner the launcher will stay and let you move down and click the icons.

---

### Post by Polmac on 2011-03-08
The idea of searching to find anything in Unity is nice, but it could be improved.
I'm thinking on something like Gnome-Do. You press the Windows key, you type whatever in your search box, and instead of just showing the results, it selects one, that is opened if you push enter. If you want another one, you just select it manually, like you do now, or type more text so that there is only one match.

The system learns which applications you tend use more when you type certain things, and this way it gets faster for you with time.

This way, it would be really fast and useful, the concept of Gnome-Do (and similar programs) has been widely tested and lots of users like it; the code is out there, it just needs to be integrated.

What do you think?

---

### Post by ratcheer on 2011-03-08
> **terry_gardener said:**
> i think it is by design. 

the further top right you go the less transparent it is. if you hit the top right corner the launcher will stay and let you move down and click the icons.

Ok, but of what use is that to anyone? (I mean the ghostly taskbar that won't stay.)

Tim

---

### Post by wacked_up on 2011-03-08
> **Polmac said:**
> The idea of searching to find anything in Unity is nice, but it could be improved.
I'm thinking on something like Gnome-Do. You press the Windows key, you type whatever in your search box, and instead of just showing the results, it selects one, that is opened if you push enter. If you want another one, you just select it manually, like you do now, or type more text so that there is only one match.

The system learns which applications you tend use more when you type certain things, and this way it gets faster for you with time.

This way, it would be really fast and useful, the concept of Gnome-Do (and similar programs) has been widely tested and lots of users like it; the code is out there, it just needs to be integrated.

What do you think?

I strongly agree. The way it works now isn't as focused as it could be, and to me, that detracts a lot from the rest of the design, which does have this strong focus.

---

### Post by mc4man on 2011-03-08
> Ok, but of what use is that to anyone? (I mean the ghostly taskbar that won't stay.)
Not sure why the combo of fade and slide, basically there is in the mouse trigger a  point that 'locks' the launcher for a second or so  (about 2x2 px upper left corner.

you can turn off the fade or slide if desired in the unity plugin settings ( I use slide only.
The genesis of
[https://bugs.launchpad.net/unity-2d/+bug/706146](https://bugs.launchpad.net/unity-2d/+bug/706146)

The point I guess to to point people to the unseen lock point

---

### Post by cariboo on 2011-03-08
If you point at the Ubuntu logo in the top left hand corner, you get the transparent panel, when you move the mouse pointer into the corner of the screen the panel comes back to life, and is no longer a ghost of it's former self.

---

### Post by VMC on 2011-03-08
> **cariboo907 said:**
> If you point at the Ubuntu logo in the top left hand corner, you get the transparent panel, when you move the mouse pointer into the corner of the screen the panel comes back to life, and is no longer a ghost of it's former self.
Huh, your right. I always just clicked on the logo. Thanks for figuring this out.

---

### Post by ratcheer on 2011-03-09
I still cannot discern a purpose for this behavior. To me, it is just goofy and weird.

Tim

---

### Post by webme on 2011-03-09
> **ratcheer said:**
> I still cannot discern a purpose for this behavior. To me, it is just goofy and weird.

Tim

I think it's only for the bling, a nice bling.

---

### Post by tjeremiah on 2011-03-10
> **Polmac said:**
> The idea of searching to find anything in Unity is nice, but it could be improved.
I'm thinking on something like Gnome-Do. You press the Windows key, you type whatever in your search box, and instead of just showing the results, it selects one, that is opened if you push enter. If you want another one, you just select it manually, like you do now, or type more text so that there is only one match.

The system learns which applications you tend use more when you type certain things, and this way it gets faster for you with time.

This way, it would be really fast and useful, the concept of Gnome-Do (and similar programs) has been widely tested and lots of users like it; the code is out there, it just needs to be integrated.

What do you think?

it now acts like gnome-do in the way that you just press enter and the closest app will load.

---

### Post by terry_gardener on 2011-03-10
finally the scrolling by mouse wheel works...

---

### Post by fflopes on 2011-03-10
Still nothing for me.  No panels are loaded and when I force compiz --replace or unity --replace the error on loading the ccp plugin is returned.

Is there a way to upgrade to from alpha 2 to alpha 3 without doing a fresh install?

---

### Post by cariboo on 2011-03-10
> **fflopes said:**
> Still nothing for me.  No panels are loaded and when I force compiz --replace or unity --replace the error on loading the ccp plugin is returned.

Is there a way to upgrade to from alpha 2 to alpha 3 without doing a fresh install?

There are so many different ways to upgrade form alpha 2 to 3, the two that come to mind off of the top of my head are Synaptic Package Manager, click the status button on the lower left, reload, click **Mark All Upgrades**, then click Apply. Or open a terminal and type the following commands

```
sudo apt-get install aptitude
```

then

```
sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by fflopes on 2011-03-10
> **cariboo907 said:**
> There are so many different ways to upgrade form alpha 2 to 3, the two that come to mind off of the top of my head are Synaptic Package Manager, click the status button on the lower left, reload, click **Mark All Upgrades**, then click Apply. Or open a terminal and type the following commands

```
sudo apt-get install aptitude
```then

```
sudo aptitude update && sudo aptitude safe-upgrade
```

I've tried both ways and also update-manager -d.

```
flopes@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Natty (development branch)
Release:    11.04
Codename:    natty
```

Not sure how to get the alpha version though...

---

### Post by williejones on 2011-03-10
> Not sure how to get the alpha version though...

You are already in the alpha version by upgrading.
As long as you keep up to date with your upgrades 
you will be in the final release when it becomes available.

---

### Post by tjeremiah on 2011-03-10
can someone please explain to me what does the 'blur' option for Unity bar do.

---

### Post by fflopes on 2011-03-10
> **williejones said:**
> You are already in the alpha version by upgrading.
As long as you keep up to date with your upgrades 
you will be in the final release when it becomes available.

Thank you williejones.  I'm then assuming that not having Unity panels means that my ATI HD3200 is making things hard to Unity/Compiz at this stage.

---

### Post by SushiR on 2011-03-11
> **fflopes said:**
> Thank you williejones.  I'm then assuming that not having Unity panels means that my ATI HD3200 is making things hard to Unity/Compiz at this stage.
I have the same ATI, running fine here...

---

### Post by mc4man on 2011-03-11
> **tjeremiah said:**
> can someone please explain to me what does the 'blur' option for Unity bar do.
Well here it's blur on dash - I believe it will slightly blur the background behind the semi-transparent dash lens, though a bit hard to see depending on the background
And the transparency of the dash was lowered a bit which I prefer anyway so the effect is minimal.

---

### Post by jerrylamos on 2011-03-11
> **williejones said:**
> You are already in the alpha version by upgrading.
As long as you keep up to date with your upgrades 
you will be in the final release when it becomes available.

Not from my experience.

I had Alpha 2 installed on 3 pc's.  All updated frequently.  Unity was in screwy shape on the fastest pc.  Classic a bit clunky on the slower ones.

Installed Alpha 3 and Voila!  Unity all straightened out.  Magic!

Note, after endless updates, Ubuntu gets bigger and bigger as viewed by doing df from terminal.  New install, nice and trim again!

So I have multi partitions on each pc, certainly a Lucid or Maverick around to straighten out grub which Natty gets all fouled up.

Now the upgrade from Alpha 3 linux-image-2.6.38-5 to linux-image-38-6 has gone quite smoothly.  Example on this netbook Acer Aspire one, the external monitor support on 38-5 was crazy with mixed resolutions and a wild cursor.  On 38-6 it's running fine, using the external monitor at 1280x1024 with Unity.  Native screen is 1024x600.

So for testing Alpha/Beta/RC my experience is update, but then re-install as the un-coordinated updates gradually get in each other's way.

Enjoy.

Jerry

---

### Post by webme on 2011-03-11
We now have border-less theme in Natty and big shadows! Looking just great!!!

---

### Post by Harry33 on 2011-03-11
> **webme said:**
> We now have border-less theme in Natty and big shadows! Looking just great!!!

Yes, it it this update here:

light-themes (0.1.8.9) natty; urgency=low

 ```
 [Neil J. Patel]
  * {Amb,Rad}iance/metacity-1/metacity-theme-1.xml
    Make borders = 0
    - Invisible grip size = 5
    - Shadow = 45.0 radius and 0.75 opacity (LP: #733233)
```

---

### Post by tjeremiah on 2011-03-11
how do you stop Firefox from always opening up in maximized?

---

### Post by mc4man on 2011-03-11
> how do you stop Firefox from always opening up in maximized?
open firefox, resize and close
Make sure that when resizing to have at less than 75% of the screen size.
If you do that it will open to size you closed/set at, otherwise it will maximize.

---

### Post by tjeremiah on 2011-03-11
> **mc4man said:**
> open firefox, resize and close
Make sure that when resizing to have at less than 75% of the screen size.
If you do that it will open to size you closed/set at, otherwise it will maximize.

thanks, that seems to work.

---

### Post by xerosis on 2011-03-12
> **webme said:**
> We now have border-less theme in Natty and big shadows! Looking just great!!!

Might not be staying that way:

[quote=Mark Shuttleworth]Please revert to 1px borders, 0 px is too bland.[/quote]

[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/733233/comments/4](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/733233/comments/4)

---

### Post by tjeremiah on 2011-03-12
> **xerosis said:**
> Might not be staying that way:



[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/733233/comments/4](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/733233/comments/4)

:o

---

### Post by Harry33 on 2011-03-12
> **xerosis said:**
> Might not be staying that way:
...


Reverted already.
light-themes (0.1.8.10) natty; urgency=low

  ```
* {Amb,Rad}iance/metacity-1/metacity-theme-1.xml
    Revert borders to 1px (blandness, and issues with
    Metacity and Unity-2D).  (LP: #733431, #733233)
```

[https://launchpad.net/ubuntu/natty/+source/light-themes/0.1.8.10](https://launchpad.net/ubuntu/natty/+source/light-themes/0.1.8.10)

---

### Post by fflopes on 2011-03-12
> **jerrylamos said:**
> Not from my experience.

I had Alpha 2 installed on 3 pc's.  All updated frequently.  Unity was in screwy shape on the fastest pc.  Classic a bit clunky on the slower ones.

Installed Alpha 3 and Voila!  Unity all straightened out.  Magic!

Note, after endless updates, Ubuntu gets bigger and bigger as viewed by doing df from terminal.  New install, nice and trim again!

So I have multi partitions on each pc, certainly a Lucid or Maverick around to straighten out grub which Natty gets all fouled up.

Now the upgrade from Alpha 3 linux-image-2.6.38-5 to linux-image-38-6 has gone quite smoothly.  Example on this netbook Acer Aspire one, the external monitor support on 38-5 was crazy with mixed resolutions and a wild cursor.  On 38-6 it's running fine, using the external monitor at 1280x1024 with Unity.  Native screen is 1024x600.

So for testing Alpha/Beta/RC my experience is update, but then re-install as the un-coordinated updates gradually get in each other's way.

Enjoy.

Jerry

I have done a fresh install (through Wubi to 10.10 and than I upgraded to Natty Alpha 3) and Unity is now working.  Unity theme / style is crashing though and I get gray application menus / top panel.  In the Unity menu, sometimes the app search won't work.  I type but nothing shows up in the search field.  Apart of that, everything seems to be working fine.

---

### Post by tjeremiah on 2011-03-12
> **Harry33 said:**
> Reverted already.
light-themes (0.1.8.10) natty; urgency=low

  ```
* {Amb,Rad}iance/metacity-1/metacity-theme-1.xml
    Revert borders to 1px (blandness, and issues with
    Metacity and Unity-2D).  (LP: #733431, #733233)
```

[https://launchpad.net/ubuntu/natty/+source/light-themes/0.1.8.10](https://launchpad.net/ubuntu/natty/+source/light-themes/0.1.8.10)

well that sucks.

---

### Post by seeker5528 on 2011-03-12
> **jerrylamos said:**
> Note, after endless updates, Ubuntu gets bigger and bigger as viewed by doing df from terminal.  New install, nice and trim again!

Not cleaning out the apt cache will do that to you.

```
sudo apt-get clean
```

Or in Synaptic go to 'Settings --> preferences --> files' and click the 'Delete cached package files' button.

Later, Seeker

---

### Post by mc4man on 2011-03-12
> **tjeremiah said:**
> well that sucks.

How that ultimately shakes out who knows. Myself will always use 3d so put back no borders. Also not a fan of of the 45 shadow so readjusted that.

If you wanted to change it's in this .xml file

```
gksudo gedit /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml
```
The border values are right at the top, currently lines 14 - 16, just change the 1's  to 0's
[PHP]<!-- General window layout -->
<frame_geometry name="frame_geometry_normal" title_scale="medium" rounded_top_left="true" rounded_top_right="true"  rounded_bottom_left="false" rounded_bottom_right="false">
        <distance name="left_width" value="0"/>
        <distance name="right_width" value="0"/>
        <distance name="bottom_height" value="0"/>[/PHP]

The shadow value is set with this line in the <!-- FRAME STYLE --> section, currently line #426 (i edited the radius to 24
[PHP]	<shadow radius="24.0" opacity="0.75" color="#abde4f" x_offset="1" y_offset="4"/>
[/PHP]

if fooling with such set gedit to show line numbers, makes life easier (note that gedit and gksudo gedit have there own preferences as far as that

---

### Post by tjeremiah on 2011-03-12
> **mc4man said:**
> How that ultimately shakes out who knows. Myself will always use 3d so put back no borders. Also not a fan of of the 45 shadow so readjusted that.

If you wanted to change it's in this .xml file

```
gksudo gedit /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml
```
The border values are right at the top, currently lines 14 - 16, just change the 1's  to 0's
[PHP]<!-- General window layout -->
<frame_geometry name="frame_geometry_normal" title_scale="medium" rounded_top_left="true" rounded_top_right="true"  rounded_bottom_left="false" rounded_bottom_right="false">
        <distance name="left_width" value="0"/>
        <distance name="right_width" value="0"/>
        <distance name="bottom_height" value="0"/>[/PHP]

The shadow value is set with this line in the <!-- FRAME STYLE --> section, currently line #426 (i edited the radius to 24
[PHP]	<shadow radius="24.0" opacity="0.75" color="#abde4f" x_offset="1" y_offset="4"/>
[/PHP]

if fooling with such set gedit to show line numbers, makes life easierthanks for the info :)

---

### Post by zika on 2011-03-13
Even though I do have some conceptual resistance toward Unity it might be just because I have not tried it (really) yet in everyday work. The main reason for that is that it doesn't work properly on my ATI HD3650 card. Main problem is that it opens OK. But, if I try to do anything screen does not clean from that. Every chunk of screen that was changed in menu opening or app opening stays &#8222;occupied&#8220; even though menu or app were closed...
Any ideas?

---

### Post by KegHead on 2011-03-13
Hi!

Maybe this is my problem w/Unity.

"Even though I do have some conceptual resistance toward Unity it might be just because I have not tried it (really) yet in everyday work".

KegHead

---

### Post by zika on 2011-03-13
> **KegHead said:**
> Hi!

Maybe this is my problem w/Unity.

"Even though I do have some conceptual resistance toward Unity it might be just because I have not tried it (really) yet in everyday work".

KegHeadI would try it if I could surpass aforementioned obstacle...
I know, there is Unity-2d, but that is not the same, and all the effort would be fruitless I'm afraid...

---

### Post by webme on 2011-03-13
Mark agreed to revert back to 0px borders, yahoooooooo!!!!!
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/733233/comments/17](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/733233/comments/17)

---

### Post by jerrylamos on 2011-03-13
> **KegHead said:**
> Hi!

Maybe this is my problem w/Unity.

"Even though I do have some conceptual resistance toward Unity it might be just because I have not tried it (really) yet in everyday work".

KegHead
Every day to me is internet browsing, downloads, internet email, internet news, internet videos, office write, "Places", terminal for utilities, digital photos, and of course Ubuntu updates, synaptic installs & updates.  And of course Natty installs as the drivers come out.  Natty installs have been problematic lately.  They're busted altogether for my Acer Aspire netbook so I take the USB hard drive over to my desktop to do install from USB stick.

So on the two of my pc's that will run Unity 3D including the netbook Acer Aspire one I do Unity 3D.  I can do what I want to a bit more awkwardly than gnome - almost all the time Unity 3D panels & launcher & Compiz are hidden since I'm all about applications full screen.

Chasing the launcher panel around from full screen works for me, a bit slowly.

Now the crux is whether Unity 3D will increase Ubuntu penetration or not.  I've put up with a lot since command line DOS starting in 1982 and I do like the Ubuntu community & forums....

The first time a new user may be "hit" with Unity 3D is on CD Live install.  

I haven't the slightest idea if the new user will know how to get anything done when confronted with the launcher, on those pc's that Compiz will deign to run on.

Now there's a lot of "installer" debug going on so we'll see how Beta works out.

Jerry

---

### Post by scradock on 2011-03-13
Any hints on how to tell Unity NOT to list all my experimental (mounted) installs? It makes the launcher kind of long to have 8 extra drive icons.

Guess I could just not mount them, but I prefer to automount if only to check that they're all there....

I can clear them off the desktop by setting /apps/nautilus/desktop/show-mounted-volumes, or some-such, but that doesn't affect the unity launcher.

---

### Post by KegHead on 2011-03-14
Hi!

I know, I know.

I'm trying.

KegHead

---

### Post by coffeecat on 2011-03-14
> **scradock said:**
> Any hints on how to tell Unity NOT to list all my experimental (mounted) installs? It makes the launcher kind of long to have 8 extra drive icons.

They're not mounted. You have an icon for each mountable partition. They only mount if you click on them. I have nine. :) As far as I can see it's the same selection of partitions that appear in the Places left pane of Nautilus. Ditto, they are not actually mounted until you click on one.

---

### Post by cecilpierce on 2011-03-14
> **coffeecat said:**
> They're not mounted. You have an icon for each mountable partition. They only mount if you click on them. I have nine. :) As far as I can see it's the same selection of partitions that appear in the Places left pane of Nautilus. Ditto, they are not actually mounted until you click on one.

There not mounted but they take up alot of space in the launcher, can they be removed from it ?
Thanks

---

### Post by coffeecat on 2011-03-14
> **cecilpierce said:**
> There not mounted but they take up alot of space in the launcher, can they be removed from it ?

That I don't know, sorry. But it's a good question. Right-clicking doesn't reveal a 'Keep in launcher' that you can untick. And to mount a partition, all you have to do is to click on the File Manager icon at the top to open a Nautilus window, and then click on the partition in the Places pane. Two clicks instead of one, and the advantage of Places in Nautilus is that it tells you whether the partition is mounted or not. So the dock icons for partitions are a bit on the superfluous side.

Does anyone know where the configuration file for the dock is? The answer might be somewhere in this megathread but I haven't seen it. Editing a config file might be the answer.

---

### Post by cecilpierce on 2011-03-14
The conf's are all over the place ! I just edited /usr/share/compiz/unityshell.xml to get the cube back, I don't like the slider.
Some people have 20 or more partitions, with that you can't find the trash can  :confused:

---

### Post by scradock on 2011-03-14
> **coffeecat said:**
> They're not mounted. You have an icon for each mountable partition. They only mount if you click on them. I have nine. :) As far as I can see it's the same selection of partitions that appear in the Places left pane of Nautilus. Ditto, they are not actually mounted until you click on one.

Well, your mileage may differ, but mine are all marked as mounted in Nautilus. Opening one in Nautilus doesn't change its symbol, and doesn't bring up another item in the list. Could be something to do with "mountall" running in the boot sequence?

Anyway, no-one seems to know the answer, but several of us want one, so it was worth asking the question.....

EDIT: wow! just noticed - right-click now offers "safely remove" which removes the icon from the task bar. Now to find out how to make that persistent....

---

### Post by scradock on 2011-03-14
> **scradock said:**
> Well, your mileage may differ, but mine are all marked as mounted in Nautilus. Opening one in Nautilus doesn't change its symbol, and doesn't bring up another item in the list. Could be something to do with "mountall" running in the boot sequence?

Anyway, no-one seems to know the answer, but several of us want one, so it was worth asking the question.....

EDIT: wow! just noticed - right-click now offers "safely remove" which removes the icon from the task bar. Now to find out how to make that persistent....

Not so good - it's USB automount that brings them in, for the partitions on an external HD. Remove simply disconnects the external HD, so they can't be re-mounted until I unplug and re-connect.

I don't mind them being mounted, and available in Nautilus - that would be fine. I just don't see why they need to be taking up space in the Task Bar as well......

---

### Post by scradock on 2011-03-14
> **cecilpierce said:**
> The conf's are all over the place ! I just edited /usr/share/compiz/unityshell.xml to get the cube back, I don't like the slider.
Some people have 20 or more partitions, with that you can't find the trash can  :confused:

As you say, the conf's are all over - and there is NO documentation as far as I can see. Refer to the wiki - nothing. Search for Unity - get scads of references to the Community. Search for natty - get announcements that Natty Alpha 1 is to be released. Go to unity.ubuntu.com - ah! at last I've found it - even a link to the wiki about unity - links straight back to the "you don't belong here - this wiki is for developers" page at wiki.ubuntu.com.

Come on, we know you're busy creating cool code, but someone has to have some responsibility to let users at least know where to look for configuration options. Or are we still being treated like mushrooms - keep them in the dark and shovel horse-manure on them?

Some of us have been testing ubuntu releases for several years, and are not amused at the lack of information about what is presented as the most significant upgrade in a long time.

</rant>

---

### Post by castrojo on 2011-03-14
> **scradock said:**
> Come on, we know you're busy creating cool code, but someone has to have some responsibility to let users at least know where to look for configuration options. Or are we still being treated like mushrooms - keep them in the dark and shovel horse-manure on them?


Information won't exist if no one writes it, feel free to add on:

[http://askubuntu.com/questions/29553/how-can-i-configure-unity](http://askubuntu.com/questions/29553/how-can-i-configure-unity)

---

### Post by scradock on 2011-03-14
> **castrojo said:**
> Information won't exist if no one writes it, feel free to add on:

[http://askubuntu.com/questions/29553/how-can-i-configure-unity](http://askubuntu.com/questions/29553/how-can-i-configure-unity)

That would mean finding out what the information that I'm asking for actually is - which is currently non-trivially difficult.

Thanks for the askubuntu response - I had seen that and realized it addressed questions at the "what happens when I try to use the configuration options that are self-evidently available" level, rather than the "how do I do something a little bit more adventurous" level.

By definition, as testers of a (pre)-alpha experimental version some of us are interested in the more adventurous level, and would be happy to help by making suggestions and so on, if the interface was set up AND DOCUMENTED so that we could. As it I feel we are being kept locked out and (far too often) told "if you don't like it my way use another distro".

Anyway, those in charge will continue to do as they see fit, and other testers can respond as they wish.

---

### Post by castrojo on 2011-03-14
> **scradock said:**
> That would mean finding out what the information that I'm asking for actually is - which is currently non-trivially difficult.

Yep, this is hard. However, you seem to be under the assumption that we're purposely making it difficult. We're documenting features as they're being written. It's /hard/ to document how things work when things are being written, and sometimes rewritten right underneath you. That's just how things have been working lately, but now it's not so bad, we're past feature freeze and we have a general idea how things work, so NOW is the time to catch up and start figuring out how to make end-user things nicer than they have been.

> Thanks for the askubuntu response - I had seen that and realized it addressed questions at the "what happens when I try to use the configuration options that are self-evidently available" level, rather than the "how do I do something a little bit more adventurous" level.

Currently the 2 levels of adventure are "things that show up in CCSM because they get put in there programatically as features land" and "You need to look in the source code." There's not real middle ground right now, because no one's written it yet.

> As it I feel we are being kept locked out and (far too often) told "if you don't like it my way use another distro".

I'm sorry you feel this way, I've spent a great deal of time this cycle in this forum explaining how Unity works and how people can get involved contributing. 

Please don't assume that just because there are people with stop energy posting dumb things here that we ignore feedback from people, I assure you that that isn't true.

I don't recall anyone on the Unity team ever saying "go use another distro". If someone is saying that kind of crap then you need to ignore them. What we need is for people like you to dive in with me and making Unity and Ubuntu rock.

---

### Post by scradock on 2011-03-15
> **castrojo said:**
> 

I'm sorry you feel this way, I've spent a great deal of time this cycle in this forum explaining how Unity works and how people can get involved contributing. 

Please don't assume that just because there are people with stop energy posting dumb things here that we ignore feedback from people, I assure you that that isn't true.

I don't recall anyone on the Unity team ever saying "go use another distro". If someone is saying that kind of crap then you need to ignore them. What we need is for people like you to dive in with me and making Unity and Ubuntu rock.

You're right - I don't suppose it was a member of the Unity team; but someone did respond to me that way only a couple of days ago (in another thread). I do ignore that sort of comment, mostly, but I'm not at source-code level myself, and don't suppose I would be very useful mucking around in it. Just knowing which config files are affecting things, and how to deal with stuff that is in files but not yet implemented (how do I put "all" as the value for what's allowed in the Unity panel, for instance - instead of the ???default value 'Java...', 'Skype' and something else equally unlikely?) would be a start.

A couple of years ago I dove in and worked out where the configs for the new gdm were kept, tried out the available options, and followed along while they changed under us. I'd be happy to try to contribute at that level if I could on Unity. I do still think it's unnecessarily obscure to me, and presumably to other testers.

Anyway, thanks for the efforts you and others are making; I for one have not (yet) gone away, and will be bugging you until it's all perfect!

---

### Post by jerrylamos on 2011-03-15
> **castrojo said:**
> 
I don't recall anyone on the Unity team ever saying "go use another distro". 
Ubuntu has by FAR lots and lots of choices - right now I'm running Natty Unity 3D, Natty 2D, and Natty Classic.  There's also Lubuntu LXDE Natty Alpha 3, Xubuntu Natty Alpha 3, KDE Natty Alpha 3, I gather all with different desktop look and feel. 

The whole idea I would surmise for Unity 3D is to look a bit more fancy like Apple or whoever.  Whether that attracts any wider acceptance of Linux I don't know, but the only way to see is to try.  There are certainly lots of Natty choices for those of us who may like a different look and feel.

I'm fastest in function with Meerkat 10.10 or Lucid 10.04 both of which I multiboot on the Natty test pc's.  Primary use is to straighten out the mess Natty does with Grub boot options when updating.

Now I'm fumbling along with Unity 3D on my newest pc's and Unity 2D on the others.  Perhaps there's directions on "how to do ..." I haven't found it?

My biggest benefit is learning a lot of practical linux while working on bugs.

My biggest frustration is starting in late February Install has been all screwed up to the point of altering Grub boot options when I haven't even entered any "change" selections.  A dead Install is one sure one way to keep people from testing Natty and finding bugs.  Since I'm not a developer I have no idea why Ubuntu development doesn't choose to fix Install ASAP, and yes I'm following some of the many Install launchpad bugs.  Is anyone in charge?

Overall net is I'm having fun exploring Unity 2D and 3D, some features I like, some I don't, some I'm trying to learn how to use.

Jerry

---

### Post by webme on 2011-03-17
Our Natty has just received some bling, the Dash is auto-resizing when you search something.

---

### Post by reiv on 2011-03-19
There is something weird going on with transparency and some parts of the design, see the attachment for details.

1: the bar and the window has different transparency.
2: these work in different ways, and act differently on other UI elements.

Is this a bug or is some unification needed for unity :?:

Note the missing status bar, cropped window drawung, transparency issues.. And why is the margin between the bar and first row of icons so big?
currently


edit: something must be broken.. 

The menu really needs a different logic, since currently it is not clear what happens when you push the button. Just try to close the menu after first closing the searchbox by clicking on the desktop...

"opens menu" -> wants to close it "clicks on desktop" -> menu stays open but the window is gone -> wants to close the menu "cliks on button" -> opens the window.. *DOH* "tries clicking again" -> ONLY the window closes. "Tries again" -> WINDOW opens. "Clicks desktop in frustration" -> menu stays open. (At this point i was annoyed) "clicks again" -> WINDOW OPENS (*enraged and laughing at the same time*:P) "clicks again" --> finally they BOTH close...

 
-Currently when clicking on the search text or on the X after typing in something to search, the | goes away and the box stops accepting input but the Search text remains. So completely the opposite function of what i would expect :confused:

Remove the "Search" text along with the | marker when clicking on the box to indicate it is not possible to search if this is really the desired function of clicking the box or X

---

### Post by VMC on 2011-03-19
> **reiv said:**
> ...
"opens menu" -> wants to close it "clicks on desktop" -> menu stays open but the window is gone -> wants to close the menu "cliks on button" -> opens the window.. *DOH* "tries clicking again" -> ONLY the window closes. "Tries again" -> WINDOW opens. "Clicks desktop in frustration" -> menu stays open. (At this point i was annoyed) "clicks again" -> WINDOW OPENS (*enraged and laughing at the same time*:P) "clicks again" --> finally they BOTH close...

...
Try pushing the ***Esc*** key to see if that closes the menu.

---

### Post by rajeev1204 on 2011-03-21
Hi

Does anyone have this issue.

When you click on the top ubuntu logo, the menu opens up half screen, but when you try to grab the resizable handle at bottom right it just opens up full screen.Then i need to click on ubuntu logo again to make it disappear.Really strange behaviour.

---

### Post by WorfSOM on 2011-03-21
> **rajeev1204 said:**
> Hi

Does anyone have this issue.

When you click on the top ubuntu logo, the menu opens up half screen, but when you try to grab the resizable handle at bottom right it just opens up full screen.Then i need to click on ubuntu logo again to make it disappear.Really strange behaviour.

I believe that the "resizable handle" you mention is actually a maximise button, hence the full-screen dash.

---

### Post by rajeev1204 on 2011-03-21
> **WorfSOM said:**
> I believe that the "resizable handle" you mention is actually a maximise button, hence the full-screen dash.

Or atleast that is what it is doing.Its not really pleasant though.

---

### Post by scradock on 2011-03-21
> **rajeev1204 said:**
> Hi

Does anyone have this issue.

When you click on the top ubuntu logo, the menu opens up half screen, but when you try to grab the resizable handle at bottom right it just opens up full screen.Then i need to click on ubuntu logo again to make it disappear.Really strange behaviour.

Yes, that's what it does here too......

---

### Post by TunaCanTommy on 2011-03-21
Here's what the dash looks like on my ASUS EeePC 701 . . .

Not very useful ? ? ?  Any way to size the icons  ? ?


@webme  Thanks  . . . . ( I didn't notice the "upload" button.)

---

### Post by webme on 2011-03-21
> **TunaCanTommy said:**
> Here's what the dash looks like on my ASUS EeePC 701 . . .

Not very useful ? ? ?  Any way to size the icons  ? ?

[IMG]/tom/Desktop/snapshot.png[/IMG]

(Nevermind . . . I can't figure out how to attached a screenshot.)

Use this.

---

### Post by kansasnoob on 2011-03-21
IMHO it's time for a HowTo regarding just how to NOT use Unity! I think it includes purging unity and compiz ............... or maybe choosing Kubuntu, Xubuntu, or Lubuntu :)

---

### Post by cariboo on 2011-03-21
The Classic Desktop works quite well, there is nothing that says you have to use Unity. When the two panel interface is no longer available is when we'll start seeing a great deal of complaints.

---

### Post by KegHead on 2011-03-21
Hi!

I think I solved my Unity hang-up.

I tried Xubuntu on my mini 9 today and it looks like it solved most of my problems.

Stay tuned!

KegHead

---

### Post by dmbtimmyb212000 on 2011-03-21
Just installed Natty Alpha 3 x64 on my Dell Studio Laptop.  Much improvement from Alpha 1...Unity seems like it is coming along quite nicely.  Thanks to all developers/contributors in the Ubuntu community!  Keep up the good work and look forward to continued testing :D

~TimmyB

---

### Post by webme on 2011-03-22
UI freeze is in 2 days (March 24th) and the border-less GTK hasn't arrived yet, although Mark S agreed with it.

---

### Post by Framli on 2011-03-23
I guess that everything directly related to Unity look and feel is "freeze free" until at least Final Freeze (april 14th).

---

### Post by mc4man on 2011-03-23
> **webme said:**
> UI freeze is in 2 days (March 24th) and the border-less GTK hasn't arrived yet, although Mark S agreed with it.

You'll get the borderless shortly I'd think
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/740579](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/740579)

(not a big fan of the 45px shadow, but fortunately that is a user adjustable setting.

---

### Post by webme on 2011-03-23
> **mc4man said:**
> You'll get the borderless shortly I'd think
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/740579](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/740579)

(not a big fan of the 45px shadow, but fortunately that is a user adjustable setting.
Good news!

---

### Post by VMC on 2011-03-23
Since this topic is Unity Q&A, I have noticed that todays[Mar23rd] ISO once installed boots faster than any before it. I wonder if anyone that is testing ISO's have also noticed this?

Right after they fixed the Ubiquity errors and I was able to resume installing daily-live ISO's. I noticed that the time when I heard the bootup tune to desktop was delayed quite a long time. This had been going on for several ISO days. Until today. Very fast bootup. From 30+ seconds to now 20 seconds. Also Unity is much more stable.

I keep reading the natty changes logs, found [here]("https://lists.ubuntu.com/archives/natty-changes/"),  Every time I find natty improving or not, I go there to see what happed that day. Maybe there's somewhere else I need to look it.

---

### Post by mc4man on 2011-03-24
Giving the new unity 3.6.8 a test many little nagging issues with the launcher and dash/places have been fixed, Much better..

---

### Post by ngsupb on 2011-03-24
Someone knows if unity is going to have an ability to assign custom hot keys to the favorite applications in the launcher? 

The keys win+[6-0] something isn't easy to press without moving the right hand from the mouse :D

---

### Post by rajeev1204 on 2011-03-25
Hello.

When you press the super key to bring up the unity panel, it also shows the search for apps dash ,any idea how to disable this and just make the unity panel pop out?


Thanks.

---

### Post by VMC on 2011-03-25
> **rajeev1204 said:**
> Hello.

When you press the super key to bring up the unity panel, it also shows the search for apps dash ,any idea how to disable this and just make the unity panel pop out?


Thanks.

I'm not sure I understand the question, but if you hold the Super key then the panel pop up with the numbers.

---

### Post by terry_gardener on 2011-03-25
> **rajeev1204 said:**
> Hello.

When you press the super key to bring up the unity panel, it also shows the search for apps dash ,any idea how to disable this and just make the unity panel pop out?


Thanks.

cant you just use alt-f1

---

### Post by cariboo on 2011-03-25
There are several hot-keys available, you can check them out [here]("http://askubuntu.com/questions/28086/unity-keyboard-mouse-shortcuts").

As far as customizability, I haven't seen any plans yet, but if it is going to happen, it'll be discussed at UDS-O in May

---

### Post by VastOne on 2011-03-27
> **VMC said:**
> Since this topic is Unity Q&A, I have noticed that todays[Mar23rd] ISO once installed boots faster than any before it. I wonder if anyone that is testing ISO's have also noticed this?

Right after they fixed the Ubiquity errors and I was able to resume installing daily-live ISO's. I noticed that the time when I heard the bootup tune to desktop was delayed quite a long time. This had been going on for several ISO days. Until today. Very fast bootup. From 30+ seconds to now 20 seconds. Also Unity is much more stable.

I keep reading the natty changes logs, found [here]("https://lists.ubuntu.com/archives/natty-changes/"),  Every time I find natty improving or not, I go there to see what happed that day. Maybe there's somewhere else I need to look it.

Yes, I noticed it as faster and more responsive.  

That is until it gets to the very end at Installing System (2nd time it says this) and the install fails again... 

This has been going on for me since March 3, Alpha 3.. 

I can use the March 1 2011 daily and install fine...

The stack of DVD's I have tested and failed is sitting at 17 and this is the 4th week..

---

### Post by teh603 on 2011-03-27
> **kansasnoob said:**
> IMHO it's time for a HowTo regarding just how to NOT use Unity! I think it includes purging unity and compiz ............... or maybe choosing Kubuntu, Xubuntu, or Lubuntu :)Last time I checked, Kubuntu is just a matter of choosing a different ISO and doing a clean re-install, if you don't want to tinker with installing the kubuntu desktop meta-package.

---

### Post by sgage on 2011-03-28
> **VastOne said:**
> Yes, I noticed it as faster and more responsive.  

That is until it gets to the very end at Installing System (2nd time it says this) and the install fails again... 

This has been going on for me since March 3, Alpha 3.. 

I can use the March 1 2011 daily and install fine...

The stack of DVD's I have tested and failed is sitting at 17 and this is the 4th week..

Dude, cough up the $10 and get a 4GB USB stick! It removes all the irritation of burning useless CD's/DVD's.  :KS

---

### Post by VastOne on 2011-03-28
> **sgage said:**
> Dude, cough up the $10 and get a 4GB USB stick! It removes all the irritation of burning useless CD's/DVD's.  :KS

Dude I have 5 4 gig sticks... and can install that way

Not quite the point though as burning a cd/dvd is the most obvious and general way of installing, ergo testing

---

### Post by webme on 2011-03-28
> **VastOne said:**
> Dude I have 5 4 gig sticks... and can install that way

Not quite the point though as burning a cd/dvd is the most obvious and general way of installing, ergo testing
I personally use an 8GB  micro-sd to install Ubuntu, why should I waste a CD/DVD ?

---

### Post by VastOne on 2011-03-28
> **webme said:**
> I personally use an 8GB  micro-sd to install Ubuntu, why should I waste a CD/DVD ?

You should not have to nor do you have to...

For me this is an ends to a means, a problem that started that I want to see ended..

Basic Troubleshooting

---

### Post by sgage on 2011-03-28
> **VastOne said:**
> Dude I have 5 4 gig sticks... and can install that way

Not quite the point though as burning a cd/dvd is the most obvious and general way of installing, ergo testing

But Dude! This is a development situation. Surely (just don't call me Shirley!), if it installs from USB it will install from  CD - the problem is usually the other way. Why waste blanks? Think of the children! :KS

---

### Post by VastOne on 2011-03-28
> **sgage said:**
> But Dude! This is a development situation. Surely (just don't call me Shirley!), if it installs from USB it will install from  CD - the problem is usually the other way. Why waste blanks? Think of the children! :KS

:popcorn:

As you have no doubt read the post above yours... 

An end to a means for me.. I NEEEEED to see it resolved..

It is in my DNA  :(  :P

Thanks Surely!

---

### Post by jerrylamos on 2011-03-28
Just tried an up to date 28 March daily build install on Acer Aspire one netbook here running a long-ago Natty install updated.

Launchpad bug #744438, ubiquity hang at "Preparing to install Ubiquity" at the point where it should be finding the partitions.

Of course gparted has no trouble with sorting out the multiple partitions, neither does Ubuntu 10.10 uquity.

How many times have I seen this one before?

This is 28 March and Beta is due 31 March?

Jerry

p.s. The good news is Unity 3D running O.K. on this hardware, or at least as much of Unity 3D as is debugged.

---

### Post by cariboo on 2011-03-28
@jerrylamos, iso testing started today, have you been taking part?

---

### Post by jerrylamos on 2011-03-28
> **cariboo907 said:**
> @jerrylamos, iso testing started today, have you been taking part?

Yes, I did, made a USB stick which booted on Acer Aspire one netbook.  It's been running Natty Unity 3D to the level that Unity 3d is debugged.

I generated Ubuntu bug #744438 ubiquity hung on "Preparing to install Ubuntu".  Seems to be hung on trying to understand the partitions.  Maverick had no such trouble.

The Acer has a 250 GB hard drive multibooted with Maverick Windoze 7 starter and a 100 GB sata USB hard drive with Maverick & Natty on it and I used gparted to create a new partition to try to install the 28 March Daily build.  No go.

The .iso is too big to fit on CD for the IBM Thinkpad T40.  I tried booting the USB but it hangs on initramfs.  That T40 has a Natty on it from early March when Natty did fit on the CD and I've kept it updated.  This doesn't test a .iso install though.  The Natty bug the T40 has is wireless network won't connect, although it's fine on Maverick.  I don't have the bug # handy.

Jerry

---

### Post by jerrylamos on 2011-03-29
.iso images for 29 March were listed at 700.6 MB.  I thought I'd try anyway on CD.  No go.  Two burns using Lucid LTS, claimed successfully, both fail at initramfs with a squashfs error.

Jerry

---

### Post by VMC on 2011-03-29
> **jerrylamos said:**
> .iso images for 29 March were listed at 700.6 MB.  I thought I'd try anyway on CD.  No go.  Two burns using Lucid LTS, claimed successfully, both fail at initramfs with a squashfs error.

Jerry

I don't know what your looking at, but daily-live:
"natty-desktop-amd64.iso 29-Mar-2011 08:23  **_691M_**"

Edit: Also daily:
"natty-alternate-amd64.iso 29-Mar-2011 13:53 **_671M_**"

---

### Post by jerrylamos on 2011-03-29
> **VMC said:**
> I don't know what your looking at, but daily-live:
"natty-desktop-amd64.iso 29-Mar-2011 08:23  **_691M_**"

Things must be changing fast.  I just copied this line excerpt:

natty-desktop-i386.iso 29-Mar-2011 14:45  699M  Desktop CD for PC

from:

[http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/)

So I'll try again....

Jerry

---

### Post by VMC on 2011-03-29
> **jerrylamos said:**
> Things must be changing fast.  I just copied this line excerpt:

natty-desktop-i386.iso 29-Mar-2011 14:45  699M  Desktop CD for PC

from:

[http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/)

So I'll try again....

Jerry
I wasn't sure which arch you were referring to. Yes, i386 is 699M. amd64 is 691M.

---

### Post by jerrylamos on 2011-03-29
Trying again...wrote today's daily build which fit on CD:
1. Installed CD successfully on this 3.33 gHz Compaq.
2. USB stick fails on Acer Aspire one, hangs forever trying to read partition tables.  Updated launchpad bug.
3. Installed CD on IBM ThinkCentre A30 2.0 gHz Celeron, however got apt-clone error and had no /etc/apt/sources.list.  Pretty crippled, will try again tomorrow.  Wrote launchpad bug.
4. IBM Thinkpad T40 CD "Try Ubuntu" hung with cursor whirly going and going.  Am trying to do "Install" now.

Note all four have partitions with running Natty updated, from an install in early March when the .iso did fit and install worked.  1 & 2 run Unity 3D, 3 & 4 run Unity 2D.

Jerry

Update:

3. Re-installed - it took maybe 3 tries - now the ThinkCentre is up and running Unity 2D from synaptic.

4. For some reason the T40 won't do 29 March "Try before..." but Install did work so Natty Unity 2D is up and running.

Of my five test pc's, 29 March finally installed on three of them.  I'm still stuck on the Acer Aspire one.  I do run Unity 3D on it by installing onto a USB hard drive when it is plugged into the Compaq, then move it to the Aspire and run grub again.  I do have a fifth pc an older 1 gHz 512 MB IBM Thinkpad R31 which I'll try a Natty Unity 2D install when I get time and inclination.

---

### Post by lucazade on 2011-03-30
> **jerrylamos said:**
> Trying again...wrote today's daily build which fit on CD:
1. Installed CD successfully on this 3.33 gHz Compaq.
2. USB stick fails on Acer Aspire one, hangs forever trying to read partition tables.  Updated launchpad bug.
3. Installed CD on IBM ThinkCentre A30 2.0 gHz Celeron, however got apt-clone error and had no /etc/apt/sources.list.  Pretty crippled, will try again tomorrow.  Wrote launchpad bug.
4. IBM Thinkpad T40 CD "Try Ubuntu" hung with cursor whirly going and going.  Am trying to do "Install" now.

Note all four have partitions with running Natty updated, from an install in early March when the .iso did fit and install worked.  1 & 2 run Unity 3D, 3 & 4 run Unity 2D.

Jerry

Tried on thinkpad t40 and "try ubuntu" works well, the same is for compiz, really smooth. Don't know why your is different.

---

### Post by jerrylamos on 2011-03-30
> **lucazade said:**
> Tried on thinkpad t40 and "try ubuntu" works well, the same is for compiz, really smooth. Don't know why your is different.

I don't know why either.

Anyway the 29 March .iso "Install" worked after three tries and it's up running Unity 2D from synaptic.

Jerry

---

### Post by KegHead on 2011-03-30
Hi!

Xubuntu 11.04 works ok on a usb stick.

Keghead

---

### Post by ratcheer on 2011-04-05
Unity hung up badly on me, last night. My system was fully updated and I was enjoying just surfing around and actually doing some things in Natty. I had about three apps running and, when I made the task bar display itself by moving my mouse to the extreme upper left screen corner, then tried to switch to one of the running apps, nothing happened. Then, I discovered that I could not switch to any of the running apps. Finally, I discovered that I could not open the restart menu, so I reset the PC and went back to Maverick.

Tim

---

### Post by KegHead on 2011-04-05
Hi!

I'm using 11.04b/classic.

It's working perfectly for me.

I see no reason to use Unity.

KegHead

---

### Post by jerrylamos on 2011-04-05
> **ratcheer said:**
> Unity hung up badly on me, last night. My system was fully updated and I was enjoying just surfing around and actually doing some things in Natty. I had about three apps running and, when I made the task bar display itself by moving my mouse to the extreme upper left screen corner, then tried to switch to one of the running apps, nothing happened. Then, I discovered that I could not switch to any of the running apps. Finally, I discovered that I could not open the restart menu, so I reset the PC and went back to Maverick.

Tim
Me too.  All up to date and froze last night.  I didn't try Ctrl-Alt-F1 to see if I could do a sudo service gdm restart.

Given the history of Natty Compiz hangs, I always suspect Compiz.  I've got Natty Unity 2D on three older pc's and they don't hang, my belief because Unity 2D doesn't use Compiz.  The two newer pc's with Compiz & Unity 3D do hang randomly.

If you like, you can try Unity 2D by selecting Synaptic, do a reload, then search for and install Unity 2D.

Jerry

---

### Post by SushiR on 2011-04-05
Anybody else having the impression that 64bit Natty is a bit buggier than 32bit? I'm running both and my Netbook (which is able to run both, but has the 32bit install) seems to be more stable than my desktop computer.

---

### Post by cariboo on 2011-04-05
> **SushiR said:**
> Anybody else having the impression that 64bit Natty is a bit buggier than 32bit? I'm running both and my Netbook (which is able to run both, but has the 32bit install) seems to be more stable than my desktop computer.

I'm running the 64-bit version of two system, and the 32-bit on another two systems, I don't really notice any difference, even though one 32-bit system is running an nVidia graphics card with nouveau drivers and the other is Intel. I will say that over time Natty 32 on Intel suffered far less compiz crashes, than the other 3 systems, but even that hasn't been a problem over the last couple of days

---

### Post by SushiR on 2011-04-05
> **cariboo907 said:**
> I'm running the 64-bit version of two system, and the 32-bit on another two systems, I don't really notice any difference, even though one 32-bit system is running an nVidia graphics card with nouveau drivers and the other is Intel. I will say that over time Natty 32 on Intel suffered far less compiz crashes, than the other 3 systems, but even that hasn't been a problem over the last couple of days

My Netbook has a Intel Corporation N10 Family Integrated Graphics Controller, which runs just fine with Unity, compiz and all that. My desktop has - AFAIR - an onboard ATI HD3200. I'm using it with the default xorg drivers (no ATI drivers). It crashes more often (Unity, menus, graphics) or it just rebooted a couple of times.

Anyway, Natty's been the most responsive and overall pleasing experience of all times. I've been following Ubuntu since it's 5.x releases and been a full time users since 8.04. I was running Mint's Julia on both devices and was quite in love with it but Natty really blew it all away. I'm using it as default on my Netbook since the first Alpha. There still are glitches, but I can live with it. Nothing really serious so far.

I'm very impressed with what the Unity team archieved within the last months. They've implemented a LOT of users requests, they've done great things to stability, they've fixed a lot of tiny bugs or annoyances. To be honest, I almost can't wait until Oneiric testing begins.

---

### Post by bjarkih on 2011-04-05
Hi, I installed natty 11.04 beta yesterday, formated / and /boot but kept my /home.  Had 10.10 previously.

My problem is that a lot of the programs I had installed in 10.10 are gone :confused: since I'm rather new to the under-the-hood workings of ubuntu I don't know if that is normal.

But my main question at the moment is why I cant modify anything in unity/compiz, in fact there isn't anything in the system preferences for that (see pic)

---

### Post by howefield on 2011-04-05
> **bjarkih said:**
> But my main question at the moment is why I cant modify anything in unity/compiz, in fact there isn't anything in the system preferences for that (see pic)

Try installing compizconfig-settings-manager and you 'll find a Unity plugin in there that will enable you to configure some of the options.

---

### Post by ranch hand on 2011-04-05
> **bjarkih said:**
> Hi, I installed natty 11.04 beta yesterday, formated / and /boot but kept my /home.  Had 10.10 previously.

My problem is that a lot of the programs I had installed in 10.10 are gone :confused: since I'm rather new to the under-the-hood workings of ubuntu I don't know if that is normal.

But my main question at the moment is why I cant modify anything in unity/compiz, in fact there isn't anything in the system preferences for that (see pic)
All programs are installed on the system directories.  No matter how you install, one partition or two, these files are replaced.

That means that your programs are gone.

---

### Post by bjarkih on 2011-04-05
There is one tiny little detail that bugs me and that is the order of the close,minimize and un-maximize buttons at the left hand side of the top menu (see pic).  When the window is not maximized these buttons are in the order I'm used to and preset by the clearlooks theme at the right hand upper corner.  Is there a way to modify this?  

One note, I instsalled the weather application pointed out in a previous post but it is no good here in Iceland, it couldn't find my home town :(  but the one built into 10.10 had no problems.

---

### Post by drs305 on 2011-04-05
> **bjarkih said:**
> There is one tiny little detail that bugs me and that is the order of the close,minimize and un-maximize buttons at the left hand side of the top menu (see pic).  When the window is not maximized these buttons are in the order I'm used to and preset by the clearlooks theme at the right hand upper corner.  Is there a way to modify this?  


Does gconf-editor still set the order and side for you?  The : (start or end of the string) determines left or right side of the window, and your can rearrange the min,max,close order. Don't know about varying behaviors when maximized or not.

```
gconf-editor /apps/metacity/general/button_layout
```

---

### Post by bjarkih on 2011-04-05
> **drs305 said:**
> Does gconf-editor still set the order and side for you?  The : (start or end of the string) determines left or right side of the window, and your can rearrange the min,max,close order. Don't know about varying behaviors when maximized or not.

```
gconf-editor /apps/metacity/general/button_layout
```

Yes, but this is the order for a windows that is not maximized.  When a window is maximized I only get the buttons shown on the picture in the previous post.  It is a little bit uncomfortable to have two different orders in the same session.  

P.s. I ran into a bug when trying to run 
gconf-editor /apps/metacity/general/button_layout 
since I couldn't paste the command into the alt+F2 box I only got some binary signal (at least I think it is), see attached pic.

---

### Post by drs305 on 2011-04-05
> **bjarkih said:**
> Yes, but this is the order for a windows that is not maximized.  

Yes, I see now what you mean. I went ahead and adapted to having the controls on the left in Maverick. I remember the outcry about moving them, and I also remember the devs saying there was a reason for it (in the future).  Now we see what the reason was - to drive you crazy.  ;-)

This *should* be customizable and hopefully someone will tell you how to do it. However, when maximized, since the top panel's right side is taken up by the indicator, I can see where the conflict would arise in having the window controls over there. So driving you crazy may not have been the *only* reason...

---

### Post by mc4man on 2011-04-05
> **bjarkih said:**
> Yes, but this is the order for a windows that is not maximized.  When a window is maximized I only get the buttons shown on the picture in the previous post.  It is a little bit uncomfortable to have two different orders in the same session.  

P.s. I ran into a bug when trying to run 
gconf-editor /apps/metacity/general/button_layout 
since I couldn't paste the command into the alt+F2 box I only got some binary signal (at least I think it is), see attached pic.

When you maximize a window it 'intergrates' into the unity panel - there is no adjustment available for where things are placed in the panel (certainly not in natty

Atm the command (ALT+F2) and dash/.places don't accept paste, you'll need to type. (though commands are saved to a history for future use

and because you can edit that history in a file somewhere, it may be possible to 'populate' that file with commands you may want to use - will have to try (will have to remember where that file is

---

### Post by ratcheer on 2011-04-11
Right now, I am having a problem with the application bar not hiding. With Firefox 4 maximized, the app bar is semi-transparent and overlays the left side of the FF window. If I un-maximize FF and try to bump the app bar to hidden, it still does not hide and the FF window appears to slide under it.

Any fixes or workarounds?

Tim

---

### Post by ruffneck on 2011-04-12
> **ratcheer said:**
> Right now, I am having a problem with the application bar not hiding. With Firefox 4 maximized, the app bar is semi-transparent and overlays the left side of the FF window. If I un-maximize FF and try to bump the app bar to hidden, it still does not hide and the FF window appears to slide under it.

Any fixes or workarounds?

Tim

I experience this issue occasionally as well when programs are maximized. It does not occur all the time but when it does, moving the mouse mounter into the top left-hand corner seems to get it to hide again. You have to slide the mouse into the corner and back a few times sometimes.

---

### Post by mc4man on 2011-04-14
> **webme said:**
> UI freeze is in 2 days (March 24th) and the border-less GTK hasn't arrived yet, although Mark S agreed with it.
Not too sure you'll see that in the initial release - there was an recent update to light-themes that reverted a 0px specific patch and did some darkening of the border to help with certain windows.

If deciding to use borderless then the best light-theme match (if using) is the previous 0.1.8.11 package

(and I still think the 45px window shadow is too much, that won't change either, though again is user adjustable

---

### Post by webme on 2011-04-14
> **mc4man said:**
> Not too sure you'll see that in the initial release - there was an recent update to light-themes that reverted a 0px specific patch and did some darkening of the border to help with certain windows.

If deciding to use borderless then the best light-theme match (if using) is the previous 0.1.8.11 package

(and I still think the 45px window shadow is too much, that won't change either, though again is user adjustable
Yes, I know, the right decision (IMO) was to let border-less themes in Unity 3D  only, and Unity 2D to be postponed for Oneiric.

---

### Post by godhika on 2011-04-14
> **webme said:**
> Yes, I know, the right decision (IMO) was to let border-less themes in Unity 3D  only, and Unity 2D to be postponed for Oneiric.

It's not only Unity 2d (which isn't btw in the standard installation) it is also the classic mode with metacity which causes problems

---

### Post by webme on 2011-04-14
> **godhika said:**
> It's not only Unity 2d (which isn't btw in the standard installation) it is also the classic mode with metacity which causes problems

Hopefully, they will fix this bugs in Oneiric.

---

### Post by ratcheer on 2011-04-14
> **ruffneck said:**
> I experience this issue occasionally as well when programs are maximized. It does not occur all the time but when it does, moving the mouse mounter into the top left-hand corner seems to get it to hide again. You have to slide the mouse into the corner and back a few times sometimes.

I moved it there about 15 times, but the app bar is still unhidden and on top.

Tim

---

