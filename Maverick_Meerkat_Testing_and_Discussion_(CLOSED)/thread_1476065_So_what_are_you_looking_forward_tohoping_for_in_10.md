---
title: "So what are you looking forward to/hoping for in 10.10-MM?"
date: 2010-05-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Slug71 on 2010-05-07
Me:
Full BTRFS support, Grub included
Delta-Debs
Packagekit as the backend to USC.
Banshee to replace Rhythmbox
The new Kernel

And i hope Xpslash is dropped too. No need for it since Plymouth can do it all.

Also looking for to seeing what Gnome-3 will be like.
And more of the dependency hell being sorted out.

---

### Post by Penguin Guy on 2010-05-07
Delta-debs, window notifications, plymouth.

---

### Post by Slug71 on 2010-05-07
> **Penguin Guy said:**
> Delta-debs, window notifications, plymouth.

Plymouth is already in? 
Then next Kernel has much better support for it though so it should make a lot of people happy.

---

### Post by ranch hand on 2010-05-07
I hope that they can straighten out the plymouth stuff real soon.  If not I hope they drop it and use something that works.

This freezing on boot up and the shut down taking almost 2 minutes is just crazy.

---

### Post by Slug71 on 2010-05-07
> **ranch hand said:**
> I hope that they can straighten out the plymouth stuff real soon.  If not I hope they drop it and use something that works.

This freezing on boot up and the shut down taking almost 2 minutes is just crazy.

I wonder if it hasnt got something to do with Xsplash with Plymouth.

---

### Post by ranch hand on 2010-05-07
> **Slug71 said:**
> I wonder if it hasnt got something to do with Xsplash with Plymouth.
I, personally, think that libplyouth2 is just bad.  I get a long bunch of messages, on all installs, at shutdown.

A message for each thing that is shut down.  This is, at least, 2 screens worth of stuff.

The only amusing thing is that all this takes place after a message that "all processes sut down in less than 2 seconds".

Less amusing is that the list takes about 1.45 minutes on all my upgraded OS'.  This is silly but not funny when you are trying to get from one test OS to another.

---

### Post by aceracer24 on 2010-05-07
I am hoping for better pulseaudio support for digitial/SPDIF. Pulseaudio seems to be one of the biggest thorns in peoples sides and it has certainly had me pulling out my hair.

---

### Post by Penguin Guy on 2010-05-07
> **Slug71 said:**
> Plymouth is already in?
No, that's just what I'm hoping for.

---

### Post by pferraro on 2010-05-07
> **Slug71 said:**
> I wonder if it hasnt got something to do with Xsplash with Plymouth.

I don't get it.  Xsplash isn't included in the default Lucid install.  Sounds like a holdover from your upgrade form Karmic.  Just remove the package.

---

### Post by ranch hand on 2010-05-07
> **Penguin Guy said:**
> No, that's just what I'm hoping for.
Plymouth is the very spotty performing boot message and splash provider in 10.04.

While it works for most, the rest of us have to fight with it just to boot and then hope it will shut down.

The best thing, I think, is to hope they come to their senses and loose that dog for just about anything else.

Either that or implement packagekit so that Ubuntu becomes to stupid to use.

---

### Post by cariboo on 2010-05-07
@ ranch hand, have you tried fedora, to see if plymouth works?

I tried Fedora 12 on my netbook with Intel graphics, and it just locked up the same way you're describing what happens with lucid.

---

### Post by MacUntu on 2010-05-07
Dead bugs.

---

### Post by mmcmonster on 2010-05-07
Move menus from individual apps to the upper panel. (More like on OS X.)

It saves vertical real estate.

---

### Post by ranch hand on 2010-05-07
> **cariboo907 said:**
> @ ranch hand, have you tried fedora, to see if plymouth works?

I tried Fedora 12 on my netbook with Intel graphics, and it just locked up the same way you're describing what happens with lucid.
I have not tried Fedora in the last 18 months.

Between, packagekit, plymouth and the installer that wants to use your whole drive (unless you are running an MS product) I doubt I will ever again.

Plymouth did not freeze on my box at that time.  It all appeared to be the theme part of it was not working.  Got the default ugly bar, a boot time of about a minute and a half and then had to update using the packagekit  package manager.

Hung on to it about a week an decided I had been abused enough and installed Mandriva for my token RPM OS.  I really like it except for the RPMs.

---

### Post by shafin on 2010-05-07
Looking forward to:
Windicators
Gnome Activity Journal
Global Menu for UNE (Will give it a run in the desktop version)
New mallard based documentation
Compiz 0.9 (Hopefully)
GDM Face Browser?
Nautilus Elementary becoming the default ?
Deja Dup backup tool?

and some surprises maybe.

---

### Post by gnomeuser on 2010-05-07
I hope to see Pinta in Maverick as a replacement for GIMP, less powerful but friendier, GIMP will still be available and remains a stunning example of what is possible with Open Source.

Banshee as the default media player, it has now addressed the complains from the Jaunty cycle and has made huge strides since. Additionally the project adopted the GNOME release cycle which aligns well for Ubuntu.

BtrFS support, it is the first release after an LTS we can begin major adventures. There are safe ways of ensuring the user understands that it is a technology preview.

The notification area disappearing, I will be highly interested in what will happen and what challenges we will met.

Proper integration of web applications such as GMail, so that the user is presented with notifications for new mails. mailto: links work, contacts and chat is setup. Options to use Google Docs added for approriate files.

Tracker and Zeitgeist deployed. The reason why Tracker hasn't catched on is that applications haven't used it. This is changing and with FSter we have a compelling demo in the form of properly updated and presented in a desirable (but configurable) fashion. This can piggybag on the existing gtkbookmarks interaction as well as the xdg_user_dir drives. An easy demo that would show where Tracker can take the desktop. Videos from various cool uses are practically overflowing. I think we can convince the user that it is worth investing in now.

Download-as-a-Service. I am tired of how poorly downloads are handled. They should be handled by a kit of some sort now. MonoTorrent is already dbus capable as I understand. Could it be prototyped in the Maverick timeframe. Perhaps, it sounds like a nice and unique feature that would set Ubuntu and the rest of Linux look innovative and impressive.

Newest Mono stack and applications. We are in store for good things. An LLVM backend, new garbage collector. Massive improvements across the board. Looking forward to this, just like the usual software rev, new kernels, drivers. 

Nouveau 3D support. It's already really good for a number of users. It would be in the spirit of Maverick to enable it to test it wider. Many users will still switch to the binary driver but it is still a strong showing of the power of out of the box of Ubuntu that all those pretty things work before they are reminded of Windows and driver cds. We could make the binary driver a recommended update with a little explanatory dialog.

Tasque in the default install, we miss a good todo list, but it definitely needs better integration. Usability studies would be valuable here to avoid obvious badness.

A MeeGo spin for the netbook deployments, hopes for eventual business to be had on mobile and other devices MeeGo targets. Possible future business to be had and people to bring awesome to.

Webcam support in MSN using telepathy, I don't need VoIP but I do need the webcam working. aMSN does this currently and while the app itself has a tendency towards 100% CPU usage while using the feature, it does have working webcam only mode. Just that would be great, I know reverse engineering the new p2p protocol for full VoIP will take time and effort. Not your bad, those proprietary protocols make the unfortunately highly requested hard.

---

### Post by Madspyman on 2010-05-07
Openshot as the default video editor instead of Pitivi.

More of the OS's design being done within Ubuntu instead of OSX, even if it means using Photoshop in Wine, it's still a step in the right direction. It shows that the developers have confidence in Ubuntu's ability.

Chromium as the default web browser.

More innovative design. Instead of just moving buttons or notifications around just to shake things up.

More courting of Adobe. Yeah this ones far fetched, but it'd be great to get Ubuntu/Linux native creative suite software.

DVD playback by default. Also far fetched.

---

### Post by bentrider1957 on 2010-05-07
> **Slug71 said:**
> Me:
Full BTRFS support, Grub included
Delta-Debs
Packagekit as the backend to USC.
Banshee to replace Rhythmbox
The new Kernel

And i hope Xpslash is dropped too. No need for it since Plymouth can do it all.

Also looking for to seeing what Gnome-3 will be like.
And more of the dependency hell being sorted out.

OMG, this Xsplash has been KILLING this release!!  That alone would be enough for me.

---

### Post by autocrosser on 2010-05-07
Delta Debs!!!!!

BTRFS support

(The one I'm going to hear boos & hisses about----)

GNOME SHELL!!!!!!

---

### Post by seeker5528 on 2010-05-07
I hope they fix [bug #448095](https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/448095) in resolvconf.

Later, Seeker

---

### Post by Merk42 on 2010-05-07
> **autocrosser said:**
> (The one I'm going to hear boos & hisses about----)

GNOME SHELL!!!!!!

OK OK I'll make the thread...

---

### Post by KdotJ on 2010-05-07
I'd like to see chromium as the default browser. As for Gnome3 (or gnome shell) I'd like to see it as an addon, but not as default as I don't think it will be up to par by then

---

### Post by glaze on 2010-05-07
* Ubuntu One for Kubuntu
* Faster and less buggy Intel driver/Mesa
* Kubuntu's default audio player something other than Amarok
* In the installer keyboard layout could be auto-selected depending on country, but of course it could be selected also manually as well if it's not good
* Ability to open Dolphin automatically when USB stick is inserted

---

### Post by descendent87 on 2010-05-07
> **glaze said:**
> 
* Kubuntu's default audio player something other than Amarok


Not going to happen, there is no other audio player for KDE anywhere near as feature full as amarok.

Anyway I'm looking forward to KDE SC 4.5 and more general improvements for Kubuntu

---

### Post by m.rankovic on 2010-05-07
> **autocrosser said:**
>  [...] GNOME SHELL!!!!!!

[QUOTE=sabdfl]the current release schedule puts Gnome Shell out of bounds for Maverick, but it will be packaged and available from universe.[/QUOTE]

[https://wiki.ubuntu.com/MeetingLogs/openweekLucid/AskMark](https://wiki.ubuntu.com/MeetingLogs/openweekLucid/AskMark)

---

### Post by nanog on 2010-05-07
+1 on delta debs. i'm meh about brtfs because most of my hard drives are unsupported  arrays. its basically a / only file system for me. 

i would love to see avant-window-navigator included by default.  i get rid of the bottom panel on every install and consider it a waste of space even without a dock.

i am really looking forward to more stable gallium/mesa for nvidia. the fedora 13 stack is very promising. 

i would also like to see a modern search tool. tracker is theoretically nice but is unstable in my experience. it also has an interface that only a mother (or developer) could love.

---

### Post by Arathorn on 2010-05-07
I'd like to see either a good KPackagekit replacement or a lot of development on KPackagekit. I know my way around with apt-get in Konsole, but I doubt any new users would understand any of it.

---

### Post by cariboo on 2010-05-07
I'd like to see dialup modem tools and drivers included on the Live CD. It can be a real pain to set up dialup without an internet connection.

I personally have high speed access, but I was trying to setup dialup access for a friend who lives out in the boonies.

---

### Post by ranch hand on 2010-05-07
> **cariboo907 said:**
> I'd like to see dialup modem tools and drivers included on the Live CD. It can be a real pain to set up dialup without an internet connection.

I personally have high speed access, but I was trying to setup dialup access for a friend who lives out in the boonies.
Just about every distro I have tried has better support for dial up than Ubuntu.  It is really my biggest complaint.

This is not something that needs to be tough.  It is easy in most and ones like PCLOS-gnome (I assume this still exists)  ask 4 questions during installation and you are up and running when you reboot into your new system.  Most KDE using distros do it pretty much that way (not Kubuntu).

This is something that ought to be a pretty easy copy/paste type fix (says the code impaired guy).

---

### Post by cariboo on 2010-05-07
I have to agree, kppp was my tool of choice when I was on dialup, it worked from KDE2 up until I stopped using KDE a couple of years back.

---

### Post by hikaricore on 2010-05-07
> **Arathorn said:**
> I'd like to see either a good KPackagekit replacement or a lot of development on KPackagekit. I know my way around with apt-get in Konsole, but I doubt any new users would understand any of it.

I never use anything but terminal and synaptic, adept was bad enough that I never even bothered with kpackage.

---

### Post by Slug71 on 2010-05-07
> **Arathorn said:**
> I'd like to see either a good KPackagekit replacement or a lot of development on KPackagekit. I know my way around with apt-get in Konsole, but I doubt any new users would understand any of it.

You should give the aptcc backend a try. A lot of new stuff coming in the 0.6.x series though.

---

### Post by Slug71 on 2010-05-07
> **pferraro said:**
> I don't get it.  Xsplash isn't included in the default Lucid install.  Sounds like a holdover from your upgrade form Karmic.  Just remove the package.

Huh? I though Usplash was dropped? I dont have that installed.

---

### Post by ranch hand on 2010-05-07
> **Slug71 said:**
> Huh? I though Usplash was dropped? I dont have that installed.
Xsplash is still on this install.  It is a 9.04>9.10?10.04>10.10 upgrade.

It is not on my clean install of 10.04.  I am not there so I can't check but I do not think it is in synaptic there either.

---

### Post by dagrump on 2010-05-08
I'm not looking forward to, or hoping for anything. That way I'm not disappointed & anything good is a bonus. One thing I've noticed over the years is that development here is like a bull in a china shop, it always leaves breakage in it's wake. No one is coming along to clean up afterwards either.
So I'm just here for the ride:):):)

---

### Post by Slug71 on 2010-05-08
> **ranch hand said:**
> Xsplash is still on this install.  It is a 9.04>9.10?10.04>10.10 upgrade.

It is not on my clean install of 10.04.  I am not there so I can't check but I do not think it is in synaptic there either.

Thanks.

---

### Post by lykwydchykyn on 2010-05-08
> **Slug71 said:**
> You should give the aptcc backend a try. A lot of new stuff coming in the 0.6.x series though.

I keep hearing this, but I've tried it and every other backend available and I can't see any difference.

I hope kpackagekit gets a serious overhaul and interface redesign along with feature-completion.

The other big glaring hole for Kubuntu IMHO is the browser, but whaddyagonndo?  Maybe by some miracle Konqueror will get rewritten for webkit (yes, I know there's a somewhat functional backend, I've used it), or rekonq will be ready, or firefox will be ported to Qt.

I can dream, at least.

---

### Post by ranch hand on 2010-05-08
Just install synaptic and for get it.  Package kit has been used for quite some time in other distros and is just no good.

Yes I know synaptic is a gnome app.  Adept or what ever it was called was a gnome app too.  It was replaced by synaptic a long time ago.

The depends you install along with it are well worth the price in space for a real package manager.

I am not compatible with KDE.  Probably a personality flaw.  I do try to have one on my loaner external for folks to try out.  The first thing I do when setting the bugger up is install synaptic.

This will, with apt for rpms (or what ever it is called), work with rpm distros.

If you hold your breath for packagekit to work worth a hoot you wil turn more than blue.

---

### Post by taavikko on 2010-05-08
Even better OOTB experience.

Indicator-apps evolving to something better.
Currently not something user-friendly per se.
((Hide/show with one click on indicator))

NM to work better with 3G modems, no double-clicking or zero-CD's popping on desktop.

And such... :)

---

### Post by dino99 on 2010-05-08
I'm waiting first to bugs fix:

- graphic drivers (intel, ati) better automatic detection and built-in multi-level fallback system (nouveau, previous release or vesa)

- a less complex start process: all our troubles have started with this silly idea "ubuntu need to boot faster", we can see the result now, real nightmare and amateurish design.

- a real power management: huge difference (50 %) with windoz 7
sensors detection, fans monitoring, not used services automaticaly desactivated, same thing with unused hardwares: wifi, bluetooth, webcam, ...)

---

### Post by moviemaniac on 2010-05-08
Definitely 2.6.35 for me. I'm very closely following the radeon-kms-powermanagement development right now and from that aspect -35 would be the best kernel to squash some of the radeon heat-problems we're seing in lucid.

---

### Post by JCoster on 2010-05-08
> **moviemaniac said:**
> Definitely 2.6.35 for me. I'm very closely following the radeon-kms-powermanagement development right now and from that aspect -35 would be the best kernel to squash some of the radeon heat-problems we're seing in lucid.

+1.  My battery life on Lucid is absolutely appalling (40 minutes at MOST).   With win7 lasts almost 2 hours.

(Sony Vaio fw31zj w/ radeon driver).

---

### Post by moviemaniac on 2010-05-08
@jcoster: If you want you can join in on the radeon-pm-testing fun. All you need to do is to compile the kernel from drm-radeon-testing with these patches on top: [http://people.freedesktop.org/~agd5f/pm-drt/](http://people.freedesktop.org/~agd5f/pm-drt/)
Read 0008-drm-radeon-kms-pm-rework-power-management.patch for instructions on how to use it (dynpm=1 in radeon-kms.conf has been replaced with controls via sysfs!)

---

### Post by Yofel on 2010-05-08
For me:
- U1 KDE client
- SSD TRIM support
- btrfs
- a sane way to configure upstart maybe?
- Software Center for Kubuntu ?

---

### Post by Speed_arg on 2010-05-08
[B]PLEASE

A MUCH FASTER SOFTWARE CENTER -IT IS REAAAALLLYYY SLOOOWWWW EVEN ON A VERY FAST MACHINE-[/B]

Then, fix all the bugs with software center :P

The nautilus-elementary, and please make it fast (nautilus has always been sooo slow. No change against PCMANFM)

A more hidden update manager (download them always silently in backround at low speed, when finished downloading a not-annoying pop-up saying "Updates have been downloaded, install?" And install them in backround (the same way as now but hide the box like in windows)

**DON'T KEEP CHANGING BOOT SCREEN MANAGER EVERY RELEASE. KEEP PLYMOUTH AND FIX THE BUGS, MAKE IT BETTER EACH VERSION.**

Chromium as default browser (firefox sux, chromium is 9999x better)

Manage all apt-get stuff in a queue. For example, you are installing 2 programs in software center, you download a .deb, you put install and it adds to the queue there, lets say you hit update system, it adds to the queue, or anything like that. Recieving the message apt-get is in use is annoying.

GDEBI is slow (or at least the interface makes it look really slow)

Integrated compiz-fusion configs. Like "No effects; normal; extra; custom"

Add a lot more options to customize system (for example add all the options ubuntu-tweak allows you to change)

9pt default font size

Overall perfonmance improvement (It is in many many cases much slower than win7)

---

### Post by rubenverweij on 2010-05-08
I hope for improvements in plymouth, gallium3d for nouveau and the windicators!
Though I do hope the windicators won't be the only new innovative feature we'll see this cycle...

---

### Post by Yofel on 2010-05-08
> **Speed_arg said:**
> [B]PLEASE

A MUCH FASTER SOFTWARE CENTER -IT IS REAAAALLLYYY SLOOOWWWW EVEN ON A VERY FAST MACHINE-[/B]



That might be this bug in dpkg/ext4 [https://bugs.edge.launchpad.net/ubuntu/+source/dpkg/+bug/537241](https://bugs.edge.launchpad.net/ubuntu/+source/dpkg/+bug/537241)

> 
Add a lot more options to customize system (for example add all the options ubuntu-tweak allows you to change)
Erm, you do know that gnome and ubuntu aim for simplicity and good default for everybody? If you like to configure a lot how about switching to Kubuntu? ;P

---

### Post by Speed_arg on 2010-05-08
> **Yofel said:**
> That might be this bug in dpkg/ext4 [https://bugs.edge.launchpad.net/ubuntu/+source/dpkg/+bug/537241](https://bugs.edge.launchpad.net/ubuntu/+source/dpkg/+bug/537241)

Erm, you do know that gnome and ubuntu aim for simplicity and good default for everybody? If you like to configure a lot how about switching to Kubuntu? ;P

No, its slow when scrolling, moving around menues. It happends on 2 different machines to me. Gotta report that bug, I saw many other people complaining about its CPU USAGE and slowness.

---

### Post by uRock on 2010-05-08
> **ranch hand said:**
> I hope that they can straighten out the plymouth stuff real soon.  If not I hope they drop it and use something that works.

This freezing on boot up and the shut down taking almost 2 minutes is just crazy.
Amen to that. I had to put Karmic back on my desktop machine to get it working. I still have Lucid on my netbook and I think they finally got wireless working better on it. I'll know for sure when I take it to school Monday.

I am looking forward to the product of the Ayatana team. Marks ideas look great on his latest blog.

If you guys are saying Banshee will be chasing off Rhythmbox, then I should give it a try and see how it works.

I'd like to see better support in the new kernel for the Atheros wireless in the asus netbooks.

---

### Post by MCVenom on 2010-05-08
Esfera, Windicators, KPackageKit not sucking, Plymouth not sucking, Banshee as the default music player, etc. :p

---

### Post by OlyPerson on 2010-05-08
I'd really like to see Chromium as the default browser as well as include something like Tasque which I just discovered today while reading through this thread.  Would also be nice to see a kernel that can handle trim support in addition to better Intel Core iX support.

Before replacing my old install of KK I would have said replace Rhythmbox with Banshee but I've been trying RB out for a while now and really like it besides it not having an equalizer (which I believe Banshee doesn't either, at least by default).

---

### Post by zekopeko on 2010-05-08
> **OlyPerson said:**
> I'd really like to see Chromium as the default browser as well as include something like Tasque which I just discovered today while reading through this thread.  Would also be nice to see a kernel that can handle trim support in addition to better Intel Core iX support.

Before replacing my old install of KK I would have said replace Rhythmbox with Banshee but I've been trying RB out for a while now and really like it besides it not having an equalizer (which I believe Banshee doesn't either, at least by default).

Banshee does have an equalizer by default.

---

### Post by Sam on 2010-05-08
> **OlyPerson said:**
> I've been trying RB out for a while now and really like it besides it not having an equalizer (which I believe Banshee doesn't either, at least by default).

Someone has created a system equalizer for pulseaudio. Sorry I'm too lazy right now to find the link but you should find it easily.

---

### Post by BwackNinja on 2010-05-08
I'm looking for a few of the usual suspects:

-Btrfs
-Compiz 0.9
-PCManFM2 to be done and still fast.
-pulseaudio with dbus support and equalizer (currently in pulseaudio, just not in the branch we are using now).
-Cleanup of the GNOME platform as GNOME3 comes along (its so wonderful to have old deprecated dependencies just disappear).
-HAL completely gone (I'm looking at you libhal1 and libhal-storage1).
-DConf/GSettings instead of GConf.
-Webkit2 web browsers starting to show up.
-Firefox handling multi-process tabs and plugins well and in a nice stable release.
-XServer 1.8.
-Blender 2.6

---

### Post by installshield on 2010-05-09
Here's what I have been hoping for, and I do realize in order to do these tedious tasks, it will be reinventing the wheel. Most new users are afraid of seeing a terminal window, like back in Win95 days people were scared of dos. :D Anyways...

1.  KernelModeX ---  (this is something I have been thinking of)make X run from a framebuffer in the kernel for booting, have the divers installed by user in an interactive way even jockey will work.  I remember back in Mandrake/Mandriva 8.0 days the bootsplash wouldn't show up with out a framebuffer.

2.  OEM Branding capabilities for the OEMS/Major OEM's such as in Gnome About below everything else there should be a line for "Manufacturer information".  Most OEMS, require that  you accept an EULA before you use the computer mostly warranty info and how to contact them if you are ever in need of assistance.(I am thinking of all of this for the n00b..

3.  A package manager in which all the user has to do is double click a file, enter passwd, accept EULA, pick dir, and install  even for Proprietary drivers and such thinkin mostly as far as "Oracle JavaVM".

4.  More support for .mp3 players, cell phones, and bluetooth devices, as well as Proprietary programs (Adobe Creative Suite, Autodesk products, etc...)

5. disallow any Malicious Commands in the terminal.

These are just some things that would impact a new user and make them want to switch,  from Windows/Mac. Most people are afraid of Linux because it's something new, They think just because it's expensive that it's better.  Let's show them a new way of thinking.  With all this said, I have recently showed a friend of mine, Linux and It's like he is in love with his computer like its his high school sweetheart.  He knows nothing of the Malicious commands...
   :guitar:   Rock On Ubuntu Team! 

~ Joseph

---

### Post by ToxicBurn on 2010-05-09
I was a windows user untill 9.10 
 
and one thing that i think really really needs to have some serious focus on is 
 
Video drivers from ati and nvidia 
 
I like how easy it is not to install the nvidia drivers but ATI really needs some love and also Ubuntu needs to watch both for driver updates because anyone who games in linux like myself when a new driver comes out I can not install it without a PHD in kernels and whatever..
 
I understand that things are diff in linux but why are things so hard just to install a driver update ?
 
and most important what can we do to make things easy for people to install these drivers.
 
Im looking forward to the next release and hope this is on ubuntus mind . 
 
and as a side note i really hope gnome does not go under with this UGLY as betty Gnome shell thing.
 
I also would like to see a color change from the browns and purple to a more fluid Blue and grey like Fedora its so easy on the eyes.
 
also fix plymouth with nvidia and ATI drivers.
 
just a few things i would like to see 
 
what about you all ?

---

### Post by ToxicBurn on 2010-05-09
sorry didnt see another topic started please delete this topic

---

### Post by ToxicBurn on 2010-05-09
I was a windows user untill 9.10 

and one thing that i think really really needs to have some serious focus on is 

Video drivers from ati and nvidia 

I like how easy it is not to install the nvidia drivers but ATI really needs some love and also Ubuntu needs to watch both for driver updates because anyone who games in linux like myself when a new driver comes out I can not install it without a PHD in kernels and whatever..

I understand that things are diff in linux but why are things so hard just to install a driver update ?

and most important what can we do to make things easy for people to install these drivers.

Im looking forward to the next release and hope this is on ubuntus mind . 

and as a side note i really hope gnome does not go under with this UGLY as betty Gnome shell thing.

I also would like to see a color change from the browns and purple to a more fluid Blue and grey like Fedora its so easy on the eyes.

also fix plymouth with nvidia and ATI drivers.

just a few things i would like to see 

what about you all ?

---

### Post by eyelessfade on 2010-05-09
* More focus on KDE
* Knetworkmanager (or whatever they call it now), not the hack it is today.
* Btrfs
* ZFS with gpl (yeah right)
* OSS4 back in the kernel
* Have plymouth be an optional package (exp for servers)
* Flash 64, drop nspluginwraper
* Have a java metapackage so if you install sun-java you would never get open-jdk, or any other implementations from pakages such as eclipse and netbeans. And visa versa. 
* More focus on stability then themes and look.

---

### Post by teachop on 2010-05-09
Return of hover tool-tips for the "systray", or an option to turn them on.

More configuration ability for tweaking in the touchpad.

---

### Post by plun on 2010-05-09
One question to you all.....

Debian import from unstable or testing  ?

My opinion is from unstable and experimental for a few packages  

What do you think ?

---

### Post by taavikko on 2010-05-09
> **plun said:**
> One question to you all.....

Debian import from unstable or testing  ?

My opinion is from unstable and experimental for a few packages  

What do you think ?

Unstable all the way :popcorn:

---

### Post by buzzmandt on 2010-05-09
in hardware drivers section, would like to see an 'activate' option for activating the open source 3d drivers so one could easily go from nvidia driver to nouveau (sp?) and back easily with mouse click

---

### Post by MCVenom on 2010-05-09
> **BlackOtaku said:**
> Esfera, Windicators, KPackageKit not sucking, Plymouth not sucking, Banshee as the default music player, etc. :p
I can't believe I forgot these! :eek::

-Btrfs
-Commercial programs in the Software Center
-More interest from OEMs
-Better Flash (works okay for me, but others don't like it), the Adobe Creative Suite (or at least Photoshop :p)
-Not really increased stability perse, as this is kind of a 'Go all out' release, but more old bugs fixed and hopefully less threads from people complaining about how their install or upgrade from x release was hell

-A upgrades section of USC, which allows you to install the newest stable versions of programs (or at least commonly used ones, like Firefox), but warns you that they may not be supported -- I find this very important, as a new user won't care or know about repos or PPAs (which may give him/her unstable or malicious packages) or GetDeb, the user just wants the newest version of Firefox, which as far as he's/she's concerned, is a breeze on Windows (download the installer, which will import from and replace the existing Firefox) and is available immediately; while on Ubuntu (especially if the user has taken to heart the 'repos keep us safe' lesson), he/she won't find it in the software center. And if the user goes to the official site and downloads it, they'll get a *.tar.* file. Now what on earth is that? :p

Don't laugh, I've seen Windows users not know what *.rar and *.zip files were, and when *I* downloaded the FF tar I thought I'd have to compile source or something. It was precompiled all along! :lolflag:

---

### Post by uRock on 2010-05-09
Why brtfs? I checked out the wiki and from what it say, it seems to be more for server applications. What would the pluses be for a desktop machine using it?

This is not a flame, just curious about the specifics.

---

### Post by cariboo on 2010-05-09
Something similar to aero snap in Windows 7.

---

### Post by kio_http on 2010-05-09
> **cariboo907 said:**
> Something similar to aero snap in Windows 7.

Already in Kubuntu lucid
Speaking of that I would love a fair chance for Kubuntu.

How about a mention of Kubuntu and Xubuntu in the installer slideshow.

---

### Post by ranch hand on 2010-05-09
> **kio_http said:**
> Already in Kubuntu lucid
Speaking of that I would love a fair chance for Kubuntu.

How about a mention of Kubuntu and Xubuntu in the installer slideshow.
This is something that has been bugging me for some time.  I am not trying to stir things up here, I would just like to know.

I feel that this is the place to ask because anyone on the testing forum at this time is probably nuts and somewhat thoughtful, if not real sensible.

What is with the "fair chance for Kubuntu" business about?  I keep reading different variations on this theme and it has me baffled.

Ubuntu is a gnome distro.  Recognized members of the Ubuntu family are Kubuntu and Xubuntu.  Lubuntu is kind of a foster member.

Those family members all have their own devs and so forth.

I do not read Xubuntu or Lubuntu (I am on their mailing list) folks making comments like this so I just really wonder what the deal is here.

I admit to not following things closely concerning Kubuntu as I am not compatible with KDE but  I don't follow Xubuntu things much closer.  Lubuntu I do follow fairly closely as I really like the bugger and its file manager.

Just asking, thanks.

---

### Post by Nightstrike2009 on 2010-05-09
I am looking forward to Gnome 3 (Gnome Shell) & Window Notifications, hopefully banshee replacing rythmnbox & the addition of openshot replacing pitvi, re-inclusion of gimp, (F-spot is rubbish in my opinion).  

I recently I seemed to have discovered that Ubuntu has no equivalent to M$ "Scandisk" for recovering corrupted memory cards (Formating in Ubuntu doesn't seem to work).

I would like an equivalent utility in Ubuntu 10.10 to M$ "Scandisk" so I can resolve these issues without having to resort to Dual-boot or a virtualised Windows just to get over this hurdle. :-)

---

### Post by crjackson on 2010-05-09
> **teachop said:**
> Return of hover tool-tips for the "systray", or an option to turn them on.

More configuration ability for tweaking in the touchpad.

I'll second both of these.  I can never get my wifes touchpad (or mine for that matter to a decent stat of usability.  In fact, my wife DETESTS using a mouse and this was a MAJOR issue when moving her from windows. It was a deal breaker for a full 2 years.  Finally when she had enough of virus and inability to use her email properly, I refused to clean up her windows install and she said "I've had it with Windows, PLEASE INSTALL UBUNTU".

Well, sill having to listen to major bitching about the touch pad. I would **PAY** to get this working properly.

---

### Post by crjackson on 2010-05-09
> **cariboo907 said:**
> Something similar to aero snap in Windows 7.

Okay, I don't do windows but I just watched a video on youtube. Is this the function that automatically sizes windows for the side by side viewing?

---

### Post by Nightstrike2009 on 2010-05-09
Yeah Crjackson,

Its the one where you have two windows you push them to the left or rightsides and they each position themselves on 50% of the screen side by side. (Currently a dual-booter, hopefully want to end this soon to become Ubuntu only) :-)

---

### Post by cariboo on 2010-05-09
I don't use Windows very often, but I saw aero snap in a video, and thought it was a cool feature. I have tried it myself and it is a cool feature.

---

### Post by rbmorse on 2010-05-09
I'll post another vote for a better user experience from ATI video drivers, especially for systems with an  HD5XXX series GPU.  

I know that Ubuntu can be made to mostly work with those cards, but video should work out of the box just like it does with those other two popularly used operating systems.  Any amount of monkey-motion (meerkat motion?) required of the user just to get a screen is too much.

---

### Post by shafin on 2010-05-09
> **Nightstrike2009 said:**
> Yeah Crjackson,

Its the one where you have two windows you push them to the left or rightsides and they each position themselves on 50% of the screen side by side. (Currently a dual-booter, hopefully want to end this soon to become Ubuntu only) :-)
You can do this right now using compiz. Check [this]("http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html").

---

### Post by Speed_arg on 2010-05-09
Please, a good remote desktop tool (like teamviewer). The one that comes is SOOOOOOOOOO bad that you need like a 50mb connection. It is like 1fps or less. Plus you need to open the ports if you use teamviewer.

Put a staright-forward one like teamviewer please.

---

### Post by uRock on 2010-05-09
> **Speed_arg said:**
> Please, a good remote desktop tool (like teamviewer). The one that comes is SOOOOOOOOOO bad that you need like a 50mb connection. It is like 1fps or less. Plus you need to open the ports if you use teamviewer.

Put a staright-forward one like teamviewer please.
Sounds like a network or GPU issue. I am able to watch my daughter play games over remote desktop.

I'd like to see a shortcut on the  desktop that opens a window and runs ```
sudo apt-get install gimp
``` because apparently everyone who uses ubuntu is an artist who needs it.

---

### Post by Neon Lights on 2010-05-09
> **BlackOtaku said:**
> 
-A upgrades section of USC, which allows you to install the newest stable versions of programs (or at least commonly used ones, like Firefox), but warns you that they may not be supported
Definitely! That would be awesome.

Delta debs, commercial apps in the USC, USC running faster :P
I hope Simple Scan gets extended a bit. I mean, I know it's Simple Scan, but it's a little too simple sometimes, and XSane's UI is a little INSane. :P

Elementary Nautilus would be awesome, and chrome/chromium as the default browser would be nice. It's been more stable than Firefox for me, and of course a helluva lot faster. ;)

---

### Post by uRock on 2010-05-09
> **Neon Lights said:**
>  chrome/chromium as the default browser would be nice. It's been more stable than Firefox for me, and of course a helluva lot faster. ;)
SOme sites are incompatible with Chrome/ium still.

---

### Post by ranch hand on 2010-05-09
> **rbmorse said:**
> I'll post another vote for a better user experience from ATI video drivers, especially for systems with an  HD5XXX series GPU.  

I know that Ubuntu can be made to mostly work with those cards, but video should work out of the box just like it does with those other two popularly used operating systems.  Any amount of monkey-motion (meerkat motion?) required of the user just to get a screen is too much.
You have never installed MS have you?

I have and have never had a video card or controller work except very poorly.  Then you can go search for the right driver and install it.  Then you can start over for the sound card or controller.  Then you can start over for any other hardware that you have hooked up.

Straight of the OEM CD all Linux distros I have tried work better than MS.

If you buy a preinstalled box, some one has all ready done this for you.  This is true of preinstalled Linux boxes just as it is with preinstalled MS boxes.

I have not said anything about Mac because I have never installed that OS.

---

### Post by MCVenom on 2010-05-09
> **uRock said:**
> Sounds like a network or GPU issue. I am able to watch my daughter play games over remote desktop.
The built-in viewer sucks for me too, I use XTightVNC, but it loses focus if I put it in fullscreen. :(

---

### Post by Yofel on 2010-05-09
In reply to a few posts:

A few newer (stable) graphics drivers are available at:
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates)
currently nvidia 195.36.24, intel 2.11 and fpit.

About audio: we have the constant pulse/alsa/oss4 discussion on devel-discuss again:
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2010-May/011312.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2010-May/011312.html)

If you don't like how application updates are handled go to:
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2010-May/011310.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2010-May/011310.html)

or just go to 
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2010-May/thread.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2010-May/thread.html)
and pick what you find interesting

About Kubuntu: sure, the Kubuntu devs will try to make it even better than lucid, some proposals are at [https://wiki.kubuntu.org/Kubuntu/10.10/Brainstorm](https://wiki.kubuntu.org/Kubuntu/10.10/Brainstorm) 
But Kubuntu is still only buntu + KDE and Canonical doesn't care about it that much.
(Harald Sitter is working on a Kubuntu Uone client though :D)

what else... trim support is in 2.6.33 so yes, maverick will have ssd trim support. we should auto sync from unstable again instead of testing, I doubt they will remove plymouth - but UDS-M starts tomorrow so we'll see.

Yofel

---

### Post by lykwydchykyn on 2010-05-09
> **ranch hand said:**
> 
What is with the "fair chance for Kubuntu" business about?  I keep reading different variations on this theme and it has me baffled.


I'm tempted to answer that in detail, but I'm afraid it might derail this thread too much.  Especially because there's no way to answer it without potentially starting a GNOME vs. KDE flamewar.

> **Yofel said:**
>  
But Kubuntu is still only buntu + KDE and Canonical doesn't care about it that much.
(Harald Sitter is working on a Kubuntu Uone client though :D)



Whatever happened to project Timelord or whatever?  It got my hopes up for better things in Lucid.

---

### Post by ranch hand on 2010-05-09
> **lykwydchykyn said:**
> I'm tempted to answer that in detail, but I'm afraid it might derail this thread too much.  Especially because there's no way to answer it without potentially starting a GNOME vs. KDE flamewar.
Feel free to send it as a PM, I would really like to know.

---

### Post by lykwydchykyn on 2010-05-09
> **ranch hand said:**
> Feel free to send it as a PM, I would really like to know.

It'd be more fun if we had a new thread on it. :)

---

### Post by kestal on 2010-05-10
- Fix Plymouth. Yes, it works for some, but others not.
- Nouveau 3d support with full compiz support (yes, I use it).
- BTRFS support
[COLOR="Red"]*****[/COLOR] Monitor Switching with Automatic Resolution stretching! Shown Here: [http://ubuntuforums.org/attachment.php?attachmentid=129089&d=1253377404]("http://ubuntuforums.org/attachment.php?attachmentid=129089&d=1253377404") (taken from: [http://ubuntuforums.org/showthread.php?t=1270326](http://ubuntuforums.org/showthread.php?t=1270326))
( Without the need to xrandr anything or subject yourself to 5-10 seconds of flickering :P )
- Delta-Debs
- Continuing to Brand Ubuntu to make it stand out more and be more appealing to the general user.
- Less random/blinking "-" at the beginning for 20s before showing plymouth.

---

### Post by applet3typod on 2010-05-10
Global Menu..... thats pretty much the top of my list. lol

---

### Post by v1ad on 2010-05-10
dvd version of ubuntu (Full)

also maybe create a way to port programs from gnome to kde and back.

---

### Post by Ozitraveller on 2010-05-10
tsclient is the show stopper for me, just doesn't allow me to login to work MS Vpn.

It would be nice if the 64bit was up to the same level as 32bit.

---

### Post by Johnsie on 2010-05-10
Usb-modeswitch by default so that my Internet dongle will be activated when it is plugged in. If I'm using a dongle it means that I cannot get online any other way. So obviously if Ubuntu wont detect my dongle then I cannot download usb-modeswitch

---

### Post by eyelessfade on 2010-05-10
> **cariboo907 said:**
> I don't use Windows very often, but I saw aero snap in a video, and thought it was a cool feature. I have tried it myself and it is a cool feature.

KDE already have this feature, and for quite a while I may add

---

### Post by rbmorse on 2010-05-10
> **ranch hand said:**
> You have never installed MS have you?

I have and have never had a video card or controller work except very poorly.  Then you can go search for the right driver and install it.  Then you can start over for the sound card or controller.  Then you can start over for any other hardware that you have hooked up.

Straight of the OEM CD all Linux distros I have tried work better than MS.

If you buy a preinstalled box, some one has all ready done this for you.  This is true of preinstalled Linux boxes just as it is with preinstalled MS boxes.

I have not said anything about Mac because I have never installed that OS.

Ranch Hand, I don't want to start a linux/windows war here, but I have Windows 7 installed on this very machine, dual-booting with Lucid.  The default Windows installation resulted in 100% working hardware. The default Lucid installation (from CD) resulted in no video (blank screen) and no internet connection (wireless driver).  

This is not good, even for experienced hobbyists like you and me, but it is unacceptable to give this experience to a new user or to someone who views a PC as just a tool with which they do other things (that, for the most part, they don't want to be doing in the first place).  

This should not have been a difficult install. The hardware is very  vanilla and of recent vintage, but by no means the latest, cutting edge stuff. It's a simple P45/Intel Core2/4GB/ATI HD5850 build. It's pretty much the same system Dell or HP or ASUS or Acer would sell you as a "mainstream" home PC with a "gamer" video card upgrade. 

It doesn't matter that getting both the video and wireless issues fixed was not particularly difficult for me (a simple chroot to install a replacement driver from repository in once  case,  and compile a vendor provided driver package in the other), but I started using Linux while Mandriva was still Mandrake. But I shouldn't even have had to do that. 

So, in reply to your question (rhetorical as it may have been) yes, I have installed MS.  On the same machine that resulted in a failed Lucid installation. It worked flawlessly.  I hope I'm able to say the same thing about the final release build of Ubuntu 10.10.

---

### Post by ranch hand on 2010-05-10
Well I am certainly glad that you have had good results installing MS products.  I do not think that this is the general experience.  I know it was not a couple of releases back.

Yes, I am disappointed with 10.04 at this time myself.  Most of this problem has to do with plymouth.  I have no idea what possessed them to use something that has been around for a long time and never worked right.  It works fine for some folks and not at all for others and has been that way for years in Fedora.

What I find interesting and disturbing is that all my installs are on this box on one drive.  Identical hardware.  No trouble installing, but, boot time is from 27 seconds (great in my opinion) to 1:54 minutes (really bad).  These are similar installs although the best ones are clean and the worst upgrades.

Shut down time is also poor on all but particularly bad with upgraded installs.  Ranges from about 30 seconds to 2 minutes.

When added to the spotty ATI support it does get depressing.  My card is actually better supported now than it ever has been.  The open driver is much better than the one from their site which, for this card, is pretty new.  3d rendering and everything works with the open driver.

This is pretty impressive to me.  It is spotty though and just depends on the card you have.

It also is something that the Ubuntu folks have little control over.  ATI needs to support their cards for Linux and, I think, they do better than any one else.  The open driver development is what needs a kick start some how.

Things seem to improve kernel to kernel so I hope that yours is better supported with what ever we end up with here in 10.10.

---

### Post by taavikko on 2010-05-10
As helping the n00bs, I would like to see something done to upgrades from previous releases.
Too often ~/.* are messed up and causing ill behaviour.
Inexperienced are too often resorting to clean install's.

---

### Post by Cavsfan on 2010-05-10
sorry wrong thread...

---

### Post by Sam on 2010-05-10
> **taavikko said:**
> Too often ~/.* are messed up and causing ill behaviour.

This is a GNOME goal: [XDG config folder implementation](http://live.gnome.org/GnomeGoals/XDGConfigFolders). Also there is a two year old [blueprint](https://blueprints.launchpad.net/ubuntu/+spec/correct-home-dir-clutter) but it seems dead.

---

### Post by Ozitraveller on 2010-05-10
> **Johnsie said:**
> Usb-modeswitch by default so that my Internet dongle will be activated when it is plugged in. If I'm using a dongle it means that I cannot get online any other way. So obviously if Ubuntu wont detect my dongle then I cannot download usb-modeswitch

Yep this would be very helpful!!!

---

### Post by uRock on 2010-05-10
> **Johnsie said:**
> Usb-modeswitch by default so that my Internet dongle will be activated when it is plugged in. If I'm using a dongle it means that I cannot get online any other way. So obviously if Ubuntu wont detect my dongle then I cannot download usb-modeswitch
So that is the culprit keeping Lucid off of my daughter's machine. Oh well, she is happy with Karmic.

---

### Post by Ibidem on 2010-05-11
For me, *everything* "just worked", with any recent/complete linux (barring slightly buggy wireless--AR5007); I haven't (re)installed Windows (as a comparison), but apparently 7 includes tons of drivers, including wireless.  The "out-of-box" experience with Windows 7 apparently is vastly better than all the previous versions, so it would be good (marketing) to try for a similar achievement.  

What I'd like--32-bit color from my Intel 945GME.  i915 does not support 32-bit color on hardware that can handle it, which leaves a complex choice:
i915 for accelerated graphics
OR
915resolution + UVESA + fbdev for 32-bit color with hardware alpha layer, no acceleration
(and 915resolution takes GRUB2, which boots too slow...)
Delta debs.

---

### Post by Glenn nl on 2010-05-11
Ubuntu:

-Xsplash default splash again
-Pinta default image editor
-Removal of F-spot
-Thunderbird default email app
-Removal of evolution
-Removal of Pitivi if it doesn´t get new features
-Openshot default video editor (if using a gnome-ish theme and if pitivi doesn´t get more features)
-Deja dup as a default backup tool
-Nautilus cleaning, like the mock up shown about a gazillion times on OMGubuntu
-Faster boot times
-Overall better performance
-Massive improvements on hardware compatibility 
-Removal of open office drawing
-Adding of me maker, for the social part of the ubuntu desktop, and memaker and memenu sounds pretty nice

[http://www.omgubuntu.co.uk/2010/03/memaker-waste-2-minutes-of-your-life.html](http://www.omgubuntu.co.uk/2010/03/memaker-waste-2-minutes-of-your-life.html)

Kubuntu:

Get your KDE thingy right, K?

Xubuntu:

-Remove all the bloat
-Question every app, use more lightweight ones
-Stand out of the crowd

Lubuntu:

-More apps default
-More standard LXDE default apps as default, like LXtask
-Better interface

---

### Post by x-shaney-x on 2010-05-11
I would like to see more features that are actually focused on meerkat and FINISHED for meerkat.
It seems everything I see are works in progress that MAY make it into +1 or +2 etc.

Although I do occasionally like to test alphas and betas and try out new things before they arrive, when it comes to final release I don't want to feel like I'm still using a beta.

---

### Post by kansasnoob on 2010-05-11
Top of the list for me is that I hope they drop that "non-interactive" boot from the Live CD:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172)

As it is you have maybe 3 seconds to hit a key or your chance to edit the boot parameters is gone. Then more time is wasted with an otherwise unnecessary reboot.

I've found Lucid to be stable enough otherwise to use it as a Live USB, especially since it's LTS, but if you so much as blink (or the phone rings, or you pause to pass gas) the option to press a key is gone :(

I'm actually considering a remaster for my Live USB. I think it would be easy if I started with Lubuntu.

Edit: I should also add that all they've actually done is move the "interactive" bit further into the boot process anyway. You still end up having to choose whether to run or install, but by then no other options are available.

---

### Post by ranch hand on 2010-05-11
> **kansasnoob said:**
> Top of the list for me is that I hope they drop that "non-interactive" boot from the Live CD:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172)

As it is you have maybe 3 seconds to hit a key or your chance to edit the boot parameters is gone. Then more time is wasted with an otherwise unnecessary reboot.

I've found Lucid to be stable enough otherwise to use it as a Live USB, especially since it's LTS, but if you so much as blink (or the phone rings, or you pause to pass gas) the option to press a key is gone :(

I'm actually considering a remaster for my Live USB. I think it would be easy if I started with Lubuntu.

Edit: I should also add that all they've actually done is move the "interactive" bit further into the boot process anyway. You still end up having to choose whether to run or install, but by then no other options are available.
+Lots

---

### Post by kansasnoob on 2010-05-11
I posted a question at Ayatana:

[https://answers.launchpad.net/ayatana-ubuntu/+question/110648](https://answers.launchpad.net/ayatana-ubuntu/+question/110648)

Since it involves a design change I felt that was a good place to start.

I mean all the complaining in the world will do no good here or on a bug thread that's been marked "fix released".

Design changes take some effort!

If I live long enough I'll figure it out :)

Please add your comments and remember to be polite! You catch more flies with honey than with vinegar :)

---

### Post by Glenn nl on 2010-05-12
> **Glenn nl said:**
> Ubuntu:

-Xsplash default splash again
-Pinta default image editor
-Removal of F-spot
-Thunderbird default email app
-Removal of evolution
-Removal of Pitivi if it doesn´t get new features
-Openshot default video editor (if using a gnome-ish theme and if pitivi doesn´t get more features)
-Deja dup as a default backup tool
-Nautilus cleaning, like the mock up shown about a gazillion times on OMGubuntu
-Faster boot times
-Overall better performance
-Massive improvements on hardware compatibility 
-Removal of open office drawing
-Adding of me maker, for the social part of the ubuntu desktop, and memaker and memenu sounds pretty nice

[http://www.omgubuntu.co.uk/2010/03/memaker-waste-2-minutes-of-your-life.html](http://www.omgubuntu.co.uk/2010/03/memaker-waste-2-minutes-of-your-life.html)



More things:

-Remove F-spot
-Include Shotwell
-Remove Tomboy
-Include Gnote
-Remove the entire mono system on Ubuntu, so the live CD is smaller and we can add more things :D

---

### Post by zekopeko on 2010-05-12
> **Glenn nl said:**
> More things:

-Remove F-spot
-Include Shotwell
-Remove Tomboy
-Include Gnote
-Remove the entire mono system on Ubuntu, so the live CD is smaller and we can add more things :D

Shotwell and Gnote don't have any dependencies?
Gnote also doesn't support note syncing with Ubuntu One.

---

### Post by xeddog on 2010-05-12
> 
You can do this right now using compiz. Check this.


I just tried this and lost my upper panel.

---

### Post by url on 2010-05-12
1) Removal of ubuntuone from the default install
2) Canonical to abandon indicator project, don't like its "improvements"
3) Removal of f-spot
4) Better application launcher for the gnome (gnome-shell ones is very good, but I don't like the shell itself). Gnome-do is not good one.
5) Refuse from ugly mono icons in the notification area, hate those weather ones, and they are hard to distinguish.

---

### Post by zekopeko on 2010-05-12
> **url said:**
> 1) Removal of ubuntuone from the default install
2) Canonical to abandon indicator project, don't like its "improvements"
3) Removal of f-spot
4) Better application launcher for the gnome (gnome-shell ones is very good, but I don't like the shell itself). Gnome-do is not good one.
5) Refuse from ugly mono icons in the notification area, hate those weather ones, and they are hard to distinguish.

I suggest you go find another distro for yourself. The indicators are here to stay. So is UbuntuOne.

---

### Post by mojo2012 on 2010-05-12
I'd love to see a globalemenu that works with GTK+ and QT, and maybe Openoffice and XUL too.
And I hope that pulseaudio get's fixed - surround on ALC850 ... not working (correctly) for me ;-(

---

### Post by benjamimgois on 2010-05-12
*Replace F-spot with Shotwell
*Replace Pitivi with Openshot
*Nautilus-elementary as default
*Remove Openoffice Draw
*Enhancements on intel graphics performance and Gallium3d
*Latest Kernel version
*Include a Wine script to install MSOffice in Software Center

---

### Post by davepoth on 2010-05-12
Just one thing for me - get Localepurge functionality built in. I have a very tiny HDD and the amount of space that foreign language helpfiles take up seems a bit pointless if I've only installed one language. If the functionality was built in the removal of the helpfiles wouldn't be so hacky and would be possible to revert if desired.

---

### Post by Slug71 on 2010-05-17
Also looking forward to Wayland. Though we might only have support for in in MM. Maybe default for 11.04??
I believe a clutter backend already exists for it too.

---

### Post by zekopeko on 2010-05-17
> **Slug71 said:**
> Also looking forward to Wayland. Though we might only have support for in in MM. Maybe default for 11.04??
I believe a clutter backend already exists for it too.

You are (too) optimistic. It's going to be years before Wayland is a viable option.

---

### Post by screaminj3sus on 2010-05-17
Nautilus-elementary default
ATI OSS driver improvements
Power management improvements
RGBA by default (please please, no more metacity jaggies!)

---

### Post by ghindo on 2010-05-17
> **Slug71 said:**
> Also looking forward to Wayland. Though we might only have support for in in MM. Maybe default for 11.04??
I believe a clutter backend already exists for it too.Why the excitement for Wayland?  I did some research and it looks like the project is still pre-alpha.  I'm not even sure if it's supposed to be a replacement for Xorg or what; as far as I can tell, it's supposed to be a very, very minimal display server for simple uses.

---

### Post by kansasnoob on 2010-05-17
I hope to do a better job of testing and bug reporting :)

I hope to consider what I'd have understood when I first tried Ubuntu while I'm testing :)

That would help eliminate bugs like this:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

That bug is partly my fault! I forgot to consider my level of understanding when I first discovered Ubuntu.

I look forward to making Ubuntu as awesome for newcomers as it was for me when I found Gutsy :)

---

### Post by Slug71 on 2010-05-17
> **ghindo said:**
> Why the excitement for Wayland?  I did some research and it looks like the project is still pre-alpha.  I'm not even sure if it's supposed to be a replacement for Xorg or what; as far as I can tell, it's supposed to be a very, very minimal display server for simple uses.

No its not meant to replace Xorg. At least so i think/understand. But excited due to the fact the display server will be getting some attention and hopefully improvement. I thinkwhen it come to display, Linux in general still has shortcomings.

---

### Post by Slug71 on 2010-05-17
> **zekopeko said:**
> You are (too) optimistic. It's going to be years before Wayland is a viable option.

Probably and could be. 

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-maverick-easy-wayland-testing](https://blueprints.launchpad.net/ubuntu/+spec/desktop-maverick-easy-wayland-testing)

Might be fun to play with.

---

### Post by philinux on 2010-05-19
[https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=slow+usb+transfer&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=slow+usb+transfer&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

More dups than you can shake a stick at and it's been a problem for ages.

---

