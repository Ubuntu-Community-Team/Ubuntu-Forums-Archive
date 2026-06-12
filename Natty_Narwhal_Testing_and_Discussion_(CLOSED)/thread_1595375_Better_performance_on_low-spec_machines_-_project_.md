---
title: "Better performance on low-spec machines - project Hog Skinner"
date: 2010-10-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by knarf on 2010-10-13
I'm not giving up yet, even though I've spelled out this preference for  Maverick, Lucid, Karmic, Jaunty and probably earlier releases as well.

Not everybody has the money to buy a new machine every few years. Some  people just don't see the need to replace perfectly functioning hardware  just to be able to run the latest and greatest. "OK, but then just  don't run the latest and greatest" you say? That is of course an option  but it is not ideal in many ways. It should also not be necessary which  is why I keep on coming back to this issue.

In the earlier stages of the Maverick test cycle performance on my  Thinkpad T23 machines was quite bad. Memory consumption went through the  roof - not something you want on a machine with 768 MB, less even on  the one with 'only' 384 MB. Just booting the thing to the desktop used  up more than half of the available memory. This has gotten better lately  but it can and in my opinion should be improved even further.

Why? If your box has 4 GB you might not see any reason to put effort in  reducing memory footprint. But... wait a few years and that 4GB will  seem as cramped as my 768 MB does at the moment. When simple panel  applets start using 256 MB because they are written in some all-singing  and dancing object relational prototype actor framework reflective  introspective genuflective language on rails or with wings for all I  care you will start to wonder where that memory went. Or maybe you won't  because by then you will have bought a new box with 64 GB so who  cares...

Well, I care.[INDENT][SIZE=3][COLOR=Silver]**<p class="getoffmylawn">**[/COLOR][/SIZE][SIZE=3]I  learned to ride a bicycle on something which closely resembles the one I  ride now. The Model A Ford in my father's garage is not that dissimilar  from what I see on the road every day. My Ural motorbike may look  old-fashioned but it is not that different from more modern bikes. The computer I'm using right now - one of those T23s - is much faster  and has much more memory than the Commodore 64 I bought in the early  80's... but in many ways it is not *that* different.[/SIZE][SIZE=3][COLOR=Silver]**</p>**[/COLOR][/SIZE]
[/INDENT]That 64 KB which seemed like a lot when the C64 was new is now more than  gobbled up by the stack of a simple applet to adjust sound volume:

> bfe8b000-bfeac000 rw-p 00000000 00:00 0          [stack]
Size:                136 kB
...Of course that old machine was mostly programmed in assembly which was  less than ideal. Fortunately we have alternatives to this now, from C  (structured assembly :) and its offspring all the way to Haskell and  beyond. Using these in lieu of assembly does use more resources but that  does not matter as we have more.

That does not mean those resources should be wasted though... How?

By not using memory hogs in the base install. By avoiding the use of  continuously running interpreted code - if it needs to be running all  the time use a compiled language when feasible. By going over the  current code base and looking for ways in which it can be made more  efficient, possibly by combining disparate applets in one code base. It  should not take several megabytes to display a small icon in a toolbar!  My whole window manager ([Xmonad]("http://xmonad.org/")) takes half the amount of memory compared to the Network-Manager applet!

Just stating a preference does not make things happen. I therefore propose a project to see if we can tame the hogs:

[SIZE=5]**[Project Hog Skinner]("https://launchpad.net/hog")**[/SIZE]

**Aim**: to reduce resource consumption of the base install of one or more Ubuntu flavours.
**Who can participate**: anyone who has the required knowledge and experience to identify and resolve resource hogs in the base install.
**How**: contributors can 'adopt' a program, range of programs or  package. This adoption is not exclusive, more than one contributor can  work on a single program. Three months before release we try to combine  the efforts of all contributors.
**Timeline**: starting NOW

---

### Post by jerrylamos on 2010-10-13
> **knarf said:**
> I'm not giving up yet, even though I've spelled out this preference for  Maverick, Lucid, Karmic, Jaunty and probably earlier releases as well.

Check out Lubuntu based on Ubuntu and intended for smaller older machines.  Developed by some of the top-notch Ubuntu developers.  Runs just fine on two of my older machines less resources nice and fast.

Desktop uses LXDE instead of Gnome desktop saves a lot of disk and memory space and runs noticeably faster.
File manager is pcmanfm instead of nautilus.  Much faster but I'm missing a couple of functions that used to be in pcman.
Internet browser Chromium.  A bit of a learning curve here.  Faster than Firefox 3.x and Firefox 4.0.  I'm using it now.

I expect to crank up a Lubuntu natty shortly, just do the Lubuntu maverick and then the usual sources.list change.

For more detail on Lubuntu see:
[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

There's also another effort based on Lubuntu called Quelitu
[http://wavesofthefuture.net/computers/quelitu-lubuntu-guide-increase-speed-windows-computer.shtml](http://wavesofthefuture.net/computers/quelitu-lubuntu-guide-increase-speed-windows-computer.shtml)

which is an interesting read.  It's based on Lubuntu and runs the same way but with some other developers twists.

They both run CD Live.

Enjoy.

Jerry

---

### Post by knarf on 2010-10-13
> **jerrylamos said:**
> Check out Lubuntu based on Ubuntu and intended for smaller older machines.  Developed by some of the top-notch Ubuntu developers.  Runs just fine on two of my older machines less resources nice and fast.
Thanks for the suggestion but that is not really what I am getting at.

I know, and have run, more or less all Ubuntu-flavours. While some of these do better on resource use - and some actually seem to be worse - the main issue is that resource use does not seem to be high on the radar for the main Ubuntu flavours (Ubuntu-desktop and Kubuntu-desktop). The problem is not limited nor in many ways directly caused by Ubuntu as the main desktop environments are quite hungry to begin with. What I aim to do is find out where the fat can be cut, from senseless CoolTechnologyOfTheMinute resource hogs to memory leaks to useless duplication of data to... well, you get it.

Lubuntu is a fine desktop but it is not the main focus for Ubuntu. Fixing Lubuntu - where it needs fixing as it is already better than the others where it comes to resource use - does not give as large a payoff as fixing the main flavours does.

I realize older hardware will not run all the flash and bling which seems to be the current rage. It does not need to do this to be functional though, as long as it can run the useful bits - minus bling. It is those useful bits which I want to put on a diet, not the glitz.

Tackling Libre/OpenOffice.org, Firefox or Thunderbird is not the main focus as those are momentous tasks which deserve their own projects - preferably run by the main developers.

Just look at what is running once a clean install has finished booting. It is those programs which are first in line to be 'skinned'.

---

### Post by Speed_arg on 2010-10-13
+100
ubuntu is slowwww and for no reason. Look at USC, its insanely slow and is something that my old cellphone can do.

---

### Post by cariboo on 2010-10-13
> **Speed_arg said:**
> +100
ubuntu is slowwww and for no reason. Look at USC, its insanely slow and is something that my old cellphone can do.

Have you submitted a bug? And if so bug #?

---

### Post by Speed_arg on 2010-10-13
> **cariboo907 said:**
> Have you submitted a bug? And if so bug #?

[Yes]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/657523")

---

### Post by cariboo on 2010-10-13
> **Speed_arg said:**
> [Yes]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/657523")

You aren't going to get any results by generalizing like that, I have a Compaq Mini 110 with the same specs as your EEPC, Unity runs well on it, and I don't see any slow down, running the software center. So for me your bug is invalid.

---

### Post by kansasnoob on 2010-10-13
I don't have time to go into great detail but I agree.

I'd like to see both a "pure Gnome" and a "Gnome lite" option for Ubuntu. I don't think either would have to be "official" releases like U, K, X, L, etc.

I've had almost no time to play since March of this year but I had, for some time, been trying to do a "Pure Gnome" version for my own use. (gnome-stracciatella-session is not pure enough for me)

But I love the general idea. The key is to find someone (or a group of someones) to pursue the whole thing.

However I don't think we should expect Canonical to start such branches, however if the aforementioned "group" came up with something popular I'm almost sure that Canonical would show some interest.

It's FOSS, we can do as we wish :D

OTOH I was impressed that Puppy produced the LuPu version. Lucid Puppy .............. who'd have imagined :rolleyes:

---

### Post by kansasnoob on 2010-10-13
> **cariboo907 said:**
> You aren't going to get any results by generalizing like that, I have a Compaq Mini 110 with the same specs as your EEPC, Unity runs well on it, and I don't see any slow down, running the software center. So for me your bug is invalid.

+1!

I have a stripped down Ubuntu (minimal install) w/IceWM and seamonkey-browser running quite well on an old PII 333MHZ w/128MB of RAM.

There's very little that can't be done with the *buntu family :)

---

### Post by k3lt01 on 2010-10-13
Count me in with my [old Acer Extensa 2300]("https://wiki.ubuntu.com/LaptopTestingTeam/Old/AcerExtensa2300").

---

### Post by Speed_arg on 2010-10-13
> **cariboo907 said:**
> You aren't going to get any results by generalizing like that, I have a Compaq Mini 110 with the same specs as your EEPC, Unity runs well on it, and I don't see any slow down, running the software center. So for me your bug is invalid.

Then than a bug does not affect all netbooks means that it doesn't exist?

It's weird, all machines I have tried (and are netbook-like specs) run it very slow. This is

1005HA
1000HA
Pentium 4 (don't know the model, 2004 though)
Sempron (don't know the model, 2004 though)

---

### Post by cariboo on 2010-10-13
> **Speed_arg said:**
> Then than a bug does not affect all netbooks means that it doesn't exist?

It's weird, all machines I have tried (and are netbook-like specs) run it very slow. This is

1005HA
1000HA
Pentium 4 (don't know the model, 2004 though)
Sempron (don't know the model, 2004 though)

I didn't say your bug didn't exist, I just said it wasn't valid for me.

One of the people that answered the bug asked for computer specs, I would suggest you add the specs for all your systems that are affected. Use the lshw command.

I've seen other people that were having problems with their eepcs in the maverick forum, and I've seen that they are having problems getting [Aurora]("http://www.auroraos.org/") to run on some models. So there may be something there

---

### Post by seeker5528 on 2010-10-13
> **knarf said:**
> I'm not giving up yet, even though I've spelled out this preference for  Maverick, Lucid, Karmic, Jaunty and probably earlier releases as well.

Not everybody has the money to buy a new machine every few years. Some  people just don't see the need to replace perfectly functioning hardware  just to be able to run the latest and greatest. "OK, but then just  don't run the latest and greatest" you say? That is of course an option  but it is not ideal in many ways. It should also not be necessary which  is why I keep on coming back to this issue.

It's the natural evolution that as machines get faster, come with more memory, etc.... the software is adapted to take advantage of that. 

I think complaining that Ubuntu/Kubuntu won't run well on older slower machines and/or machines with less memory is a 'spitting into the wind' type of exercise.

It's getting to the point where if you have such a machine you have to accept the fact that it's limited and either upgrade, customize the installation, or go with the variant that is targeted at maintaining compatibility with these older machines (Lubuntu).

Even with Lubuntu you will have issues with Firefox or other additional software you might wish to install if you have less than 768 MB of RAM.

Later, Seeker

---

### Post by Ozitraveller on 2010-10-13
I'm do this on a PII/400 with 489MB ram and it's fine.

HowTo Achieve "Ubuntu-Desktop-Minimal"
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

---

### Post by ranch hand on 2010-10-13
> **seeker5528 said:**
> It's the natural evolution that as machines get faster, come with more memory, etc.... the software is adapted to take advantage of that. 

I think complaining that Ubuntu/Kubuntu won't run well on older slower machines and/or machines with less memory is a 'spitting into the wind' type of exercise.

It's getting to the point where if you have such a machine you have to accept the fact that it's limited and either upgrade, customize the installation, or go with the variant that is targeted at maintaining compatibility with these older machines (Lubuntu).

Even with Lubuntu you will have issues with Firefox or other additional software you might wish to install if you have less than 768 MB of RAM.

Later, Seeker
Spitting?  That is not exactly the word I have heard used.

---

### Post by seeker5528 on 2010-10-13
> **ranch hand said:**
> Spitting?  That is not exactly the word I have heard used.

Yeah, yeah, yeah.... I've heard the other thing too, but it's always:

> You don't tug on Superman's cape
You don't spit into the wind
You don't pull the mask off the old Lone Ranger
And you don't mess around with Jim

That stands out in my mind. :)

Later, Seeker

---

### Post by k3lt01 on 2010-10-13
> **seeker5528 said:**
> Even with Lubuntu you will have issues with Firefox or other additional software you might wish to install if you have less than 768 MB of RAM.That is just so incorrect it isn't funny. My laptop has 256mg RAM and runs FF and other applications without any difficulty. Applications like Skype, Google Earth, Pitivi, and VLC are no problem. The trick is to have a good SWAP size and not to allow resource hogs (ureadahead used to be in the bad list until quite a few of us worked together to find what it was doing).

I'd say if your not willing or able to help that's fine but at least don't go putting the kybosh on others for positive actions.

---

### Post by seeker5528 on 2010-10-15
> **k3lt01 said:**
> That is just so incorrect it isn't funny. My laptop has 256mg RAM and runs FF and other applications without any difficulty.

Forgive me if I remain a skeptic, but then again I guess much depends on how you define 'runs FF and other applications without any difficulty' and how much thumb twiddling is acceptable to you while you wait for things to load or switch between tabs/applications.

If you can't upgrade your RAM, that's one thing, you make due with what you have and tweak things to get as close to acceptable as you can or you move on.

But if the RAM is available to you and you can spend $35-55US and go from crap to marginally acceptable or from crap/marginally acceptable to OK, why would you spend your time tweaking settings and changing installed software, unless you have somebody telling you, 'XXX RAM will work fine.

I see the parallel situations with Windows XP where I can install RAM in a machine and spend 2-3 hours testing the RAM and get my stuff done quickly or run the system with the amount of RAM it came in with and maybe be done in 2, 3, or 4 days. 

CPU can be a factor as well. Some generations of Celerons were exceptionally bad, so bad in some cases that you could put in a regular Pentium 4 chip of similar generation but lower GHz, maybe even lower bus speed in some cases, and still have it run circles around the Celeron.

Later, Seeker

---

### Post by jerrylamos on 2010-10-15
> **seeker5528 said:**
> Forgive me if I remain a skeptic, but then again I guess much depends on how you define 'runs FF and other applications without any difficulty' and how much thumb twiddling is acceptable to you while you wait for things to load or switch between tabs/applications.


Thinkpad R31 tops out at 512 mb, note some is used for the infamous intel video graphics i830 chip so there's about 500 k left (where k=1024).

1 gHz Celeron.  This Thinkpad is circa 2001.

At email, internet browse & downloads, office, ... runs just fine.  The small videos that BBC, ABC, Sydney Morning Herald (I'm in the U.S.A.), etc. run O.K., perfectly usable.  Full screen video is jerky and no fun.

Note screen is relatively big compared to a netbook.  It could use a new battery at $50 but sits on a chair next to the dining table.

Now FF is a little sluggish so I frequently use Lubuntu with Chromium and LXDE.  I do run Maverick 10.10 Firefox, even Firefox 4.0, and will likely try Natty on it soon - looking for bugs.

I've got 4 test pc's primarily differentiated in finding Ubuntu bugs by the video graphics, namely i830, i845G, Radeon Xpress 200, Radeon Mobility 7500.

Jerry

---

### Post by seeker5528 on 2010-10-15
> **k3lt01 said:**
> I'd say if your not willing or able to help that's fine but at least don't go putting the kybosh on others for positive actions.

Not discouraging work in this area, just saying it's already being done with Lubuntu, but even then experience will vary depending on the software you run, assuming you don't just stick with the Lubuntu defaults.

People used to suggest Damn Small Linux for the light weight machines, but I never could tell any significant difference performance wise between DSL and a stock Debian installed with the Gnome desktop.

Later, Seeker

---

### Post by Reiger on 2010-10-15
Up to some point, yes. But I find things kind of change when you combine low ram, with poor hard disk and hamster powered CPUs.

At that point there's definitely a difference between something like Puppy Linux and Ubuntu (where the machine will not even run the live CD).
Puppy Linux is not exactly a secure setup though.

---

### Post by k3lt01 on 2010-10-15
> **seeker5528 said:**
> Forgive me if I remain a skeptic, but then again I guess much depends on how you define 'runs FF and other applications without any difficulty' and how much thumb twiddling is acceptable to you while you wait for things to load or switch between tabs/applications.I think its the other way round actually. How much do you expect from a lightweight machine. I click the FF icon etc and the program starts within a few seconds. This same laptop with Windows XP and IE cannot do it in 15 seconds. Seriously if you think anyone and everyone can afford to go and upgrade their RAM you are sadly mistaken. I'd love to, really I would but in this day and age with little or no job security luxuries like that are simply not an option. I'm sitting with an 8 year old Laptop working with a full blown Ubuntu install and a couple of tweaks that are easily found in these forums are all that I need to do to make a perfectly acceptable machine.

> **seeker5528 said:**
> Not discouraging work in this area, just saying it's already being done with Lubuntu, but even then experience will vary depending on the software you run, assuming you don't just stick with the Lubuntu defaults.I fail to see how working on Ubuntu (Gnome) has already been done with Lubuntu (LXDE). If you want to use Lubuntu go ahead I wont stop you nor put you down for using your freedom of choice. I, and others like me, prefer Ubuntu and can see great benefit in working on making it usable on lightweight machines like it once was.

I suppose what I am saying to you is, whatever floats your boat is fine for you, don't knock others for wanting to have the same freedom of choice and working towards that.

---

### Post by seeker5528 on 2010-10-15
> **k3lt01 said:**
> I fail to see how working on Ubuntu (Gnome) has already been done with Lubuntu (LXDE).

I thought the comment about spitting into the wind already covered that.:wink:

> If you want to use Lubuntu go ahead I wont stop you nor put you down for using your freedom of choice.

Starting with something where the upstream already has similar goals seems much more productive.

[qoute]I, and others like me, prefer Ubuntu and can see great benefit in working on making it usable on lightweight machines like it once was.[/QUOTE]

Upstream is not going to stay stagnant so keeping it 'usable on lightweight machines like it once was' is going to keep becoming more difficult and require recompiling/repackaging more things to eliminate some of the optional but installed/enabled by default parts of the software.

If you are less concerned about that and just want a minimal Gnome session, you can't do much better than creating a .xsession file with some contents like:

```
gnome-settings-daemon &
gnome-panel &
exec metacity
```

Then eliminate any extra panel applets and/or startup items you don't want.

If the session stuff is still borked, you might need to create a default.desktop file in '/usr/share/xsessions/' with the some contents like:

```
[Desktop Entry]
Name=Default Xsession
Comment=This runs ~/.xsession
Exec=/etc/X11/Xsession
```

to give you something you can select in the display manager.

Later, Seeker

---

### Post by k3lt01 on 2010-10-15
> **seeker5528 said:**
> I thought the comment about spitting into the wind already covered that.:wink:You know what thinking did don't you? :P

> **seeker5528 said:**
> Starting with something where the upstream already has similar goals seems much more productive.In your opinion which has been noted, yet you seem to be ignoring the opinions of others.

---

### Post by seeker5528 on 2010-10-16
> **k3lt01 said:**
> yet you seem to be ignoring the opinions of others.

I'm all for a leaner meaner Gnome option, but as you start to fall into the more significantly limited category, you gotta start thinking about 'What is the right tool for the job?'.

I don't use a chisel when I need a hole punch, if I can help it.

So, you didn't think 

> **seeker5528 said:**
> just want a minimal Gnome session, you can't do much better than creating a .xsession file with some contents like:

```
gnome-settings-daemon &
gnome-panel &
exec metacity
```

Then eliminate any extra panel applets and/or startup items you don't want.

If the session stuff is still borked, you might need to create a default.desktop file in '/usr/share/xsessions/' with the some contents like:

```
[Desktop Entry]
Name=Default Xsession
Comment=This runs ~/.xsession
Exec=/etc/X11/Xsession
```

to give you something you can select in the display manager.

was helpful then? :)

Uninstalling pulseaudio should make some difference as well.

To help keep things lean, using Synaptic and going to 'Settings --> preferences --> general' and unchecking the box to treat recommends as dependencies can be helpful. You can always right click a package in Synaptic's list of packages and select recommended/suggested packages off the context menu on an individual basis.

Later, Seeker

---

### Post by k3lt01 on 2010-10-16
@ Seeker, at no stage did I suggest what you have posted is not helpful. Much of it has absolutely nothing to do with the topic at hand but it is helpful in the right context.

If you want a debate I am willing to give you one but if you want to make suggestions about what I think or don't think you will need to be a bit smarter than the average bear.I am not the only person here so please post your suggestions for everyone's benefit not mine only. Having a deep and meaningful with me only, and you are otherwise you wouldn't be quoting only me, isn't helpful to the wider community.

Now back to our regular programming.

---

### Post by knarf on 2010-10-16
> **seeker5528 said:**
> Upstream is not going to stay stagnant so keeping it 'usable on lightweight machines like it once was' is going to keep becoming more difficult and require recompiling/repackaging more things to eliminate some of the optional but installed/enabled by default parts of the software.
Upstream can adopt any changes we come up with, that way everybody wins.

---

### Post by jerrylamos on 2010-10-16
Want to try to speed up response with your existing Ubuntu?  If you've got some disk space, go into Synaptic and install LXDE desktop and Chromium internet browser.  

Chromium will show up on Applications Internet so you can right click on it to add it to the top panel.  By default it picks up some Firefox settings and importantly for me bookmarks.  There was a learning curve on tools (looks like a wrench on right side) I've got it behaving O.K.

LXDE is a login choice, so boot up, select the power switch, log out then when logging in select LXDE at the center bottom of the screen.

So you can run either or both as you see fit.

It uses more space than Lubuntu and is probably not as fast, however it's easy to do and undo.

Have fun, Jerry

---

### Post by plun on 2010-10-16
> **jerrylamos said:**
> Want to try to speed up response with your existing Ubuntu?  If you've got some disk space, go into Synaptic and install LXDE desktop and Chromium internet browser.  



Yup... its really great !!

A Ubuntu/Gnome user can also install the **lubuntu-desktop** meta package.

Just to logout and change session to Lubuntu or LXDE.... 

I am running an i3 processor and everything is extremely speedy..:)

---

### Post by cariboo on 2010-10-16
I noticed on one of my Maverick installs, there was an option in the session menu to start a gnome session without ubuntu enhancements. It isn't on either of the two installs on the system I'm using now, or my netbook, so it must be on one of my office systems. I'll check on Monday to see where the option came from.

---

### Post by k3lt01 on 2010-10-16
I find Chromium slows my machine down. I only have it for 1 email address but it is much slower than FF and causes a real drain on my RAM which then causes issues with Pidgin and Skype. I have no such issues with FF.

---

### Post by jerrylamos on 2010-10-16
> **k3lt01 said:**
> I find Chromium slows my machine down. I only have it for 1 email address but it is much slower than FF and causes a real drain on my RAM which then causes issues with Pidgin and Skype. I have no such issues with FF.
Just for giggles I tried Firefox & Chromium on Ubuntu Maverick>Natty using the System Monitor displaying a BBC video of the French riots - I'm in New Hampshire, U.S.A.  This is a 3.3 gHz Celeron my fastest test pc.  Video was smooth on the small window.  I didn't try full screen.

Firefox 3.6 ran about 52% cpu with periodic pulses to 84%.

Chromium ran about 50% cpu flat.  no pulses.

Firefox 3.6 was using 303 mb out of 1.7 gb memory.

Chromium used 272 mb.

Not a great difference by that measure.  I'll try on one of my slower processors.

I could try both on LXDE if I get around to it.

Jerry

---

### Post by cariboo on 2010-10-16
I've found that Opera works much better than Firefox on low resource systems.

---

### Post by ubername on 2010-10-17
[http://my.opera.com/desktopteam/blog/2010/10/15/font-fixes-for-nix-the-last-10-70-build](http://my.opera.com/desktopteam/blog/2010/10/15/font-fixes-for-nix-the-last-10-70-build)

New build of opera which claims to make fonts better in *nix. Looks good on my Ubuntu (but so did the previous version!)

Sorry if this is off topic.

---

### Post by ronacc on 2010-10-17
I have found that if you run Opera with plugins ( at least flash ) turned off its mem usage stays really low , if you leave flash on and a page that serves lots of slash ads open mem  usage creaps up rather badly  , not really an Opera problem but a flash one , HTML5 where are you ?

---

### Post by xebian on 2010-10-17
> **Speed_arg said:**
> +100
ubuntu is slowwww and for no reason. Look at USC, its insanely slow and is something that my old cellphone can do.

Then don't use it, or much better get rid of it.  It's not required for all you know.  That's 1 big easy step to get to your goals.

---

### Post by jerrylamos on 2010-10-17
> **ubername said:**
> [http://my.opera.com/desktopteam/blog/2010/10/15/font-fixes-for-nix-the-last-10-70-build](http://my.opera.com/desktopteam/blog/2010/10/15/font-fixes-for-nix-the-last-10-70-build)

New build of opera which claims to make fonts better in *nix. Looks good on my Ubuntu (but so did the previous version!)

Sorry if this is off topic.

"Simple question" how do I import bookmarks from Firefox into Opera?  I've got maybe 200.  Chromium finds Firefox bookmarks all by itself.  On different Ubuntu installs I export bookmarks from one firefox and import into the next.

Opera seems to have this little toy speed dial panel, no way I can get 200 bookmarks onto that.

I tried Opera wiki and didn't get anywhere.

?

Thanks, Jerry

---

### Post by ronacc on 2010-10-17
open Opera left click <file> then <import export> a dialog opens with choices of what to import .

---

### Post by ronacc on 2010-10-17
or if you dont have the menu bar showing , click <menu> then <settings> then <import export> .

---

### Post by Half-Left on 2010-10-18
Sometimes it's just not possible to make software run on as low end machines. Lubuntu is fine but in no way would it be a flagship product for the desktop. It lacks a lot of functionality, features and integration.

I doubt Canonical would do any major profiling of GNOME to make it more light weigh and faster.

---

### Post by jerrylamos on 2010-10-18
> **Half-Left said:**
> Sometimes it's just not possible to make software run on as low end machines. Lubuntu is fine but in no way would it be a flagship product for the desktop. It lacks a lot of functionality, features and integration.

I doubt Canonical would do any major profiling of GNOME to make it more light weigh and faster.
Hey,

There's Edubuntu Kubuntu Xubuntu Mythbuntu Ubuntu Studio Edition Ubuntu Sever edition Netbook 64bit you name it I must have missed some.  Then there's third party Ubuntu variants like Super OS 10.10, CrunchBang, ... Very definitely not "one size fits all".  That's the beauty of linux and ubuntu in particular.

Lubuntu is a part-time project by a few developers which some of us find useful.  Either get it from Lubuntu or else do a minimal install and choose lubuntu-desktop.  It's on synaptic.

So this thread is about choices for low spec machines without each of us having to try them all....

Jerry

p.s. I've got fast pc's running straight Ubuntu and a couple older pc's running mostly a lighter weight version of ubuntu - it's all about finding bugs anyway.

---

### Post by hype on 2010-10-18
I'd like to give an exemple:
i just upgraded from Lucid to Maverick on my parents pc.
The rather old Nvidia MX400 was detected as such under lucid: the graphic driver was installed and i had hardware acceleration.
 On Maverick, it's not event detected.
I litterally have just installed it a few hours ago, didnt have time to find a solution "by hand", but i was actually surprised as i thought would be the same that on Lucid for that matter.

---

### Post by jerrylamos on 2010-10-18
> **hype said:**
> I'd like to give an exemple:
i just upgraded from Lucid to Maverick on my parents pc.
The rather old Nvidia MX400 was detected as such under lucid: the graphic driver was installed and i had hardware acceleration.
 On Maverick, it's not event detected.
I litterally have just installed it a few hours ago, didnt have time to find a solution "by hand", but i was actually surprised as i thought would be the same that on Lucid for that matter.
Well,

Lucid is LTS to be supported for longer than Maverick anyway.

Jerry

---

### Post by Half-Left on 2010-10-18
> **jerrylamos said:**
> Hey,

There's Edubuntu Kubuntu Xubuntu Mythbuntu Ubuntu Studio Edition Ubuntu Sever edition Netbook 64bit you name it I must have missed some.  Then there's third party Ubuntu variants like Super OS 10.10, CrunchBang, ... Very definitely not "one size fits all".  That's the beauty of linux and ubuntu in particular.

Lubuntu is a part-time project by a few developers which some of us find useful.  Either get it from Lubuntu or else do a minimal install and choose lubuntu-desktop.  It's on synaptic.

So this thread is about choices for low spec machines without each of us having to try them all....

Jerry

p.s. I've got fast pc's running straight Ubuntu and a couple older pc's running mostly a lighter weight version of ubuntu - it's all about finding bugs anyway.

Well yes of course that's the freedom of Linux but Canonical picked GNOME default for a reason, for the rest of the world these others just lack functionality out of the box.

---

### Post by cariboo on 2010-10-18
> **hype said:**
> I'd like to give an exemple:
i just upgraded from Lucid to Maverick on my parents pc.
The rather old Nvidia MX400 was detected as such under lucid: the graphic driver was installed and i had hardware acceleration.
 On Maverick, it's not event detected.
I litterally have just installed it a few hours ago, didnt have time to find a solution "by hand", but i was actually surprised as i thought would be the same that on Lucid for that matter.

I don't think nvidia has created drivers that support Xorg 1.9 for that particular graphics card. The nouveau drivers with libgl1-mesa-dri-experimental for 3D should work well for you.   libgl1-mesa-dri-experimental is in the repositories.

---

### Post by seeker5528 on 2010-10-18
> **Half-Left said:**
> Sometimes it's just not possible to make software run on as low end machines. Lubuntu is fine but in no way would it be a flagship product for the desktop. It lacks a lot of functionality, features and integration.

How many people actually use the me menu and some of that other stuff anyway?

Personally, if I can change the wallpaper, mouse cursors, icon themes, etc..., change firewall settings, it recognizes my flash drive and offers to open it in the file manager, I don't consider it to be lacking features. Lubuntu does these things fine. What is on the preferences section of the menu will change depending on what's installed. 

Whether you have a low end machine or not is, to some extent, orthogonal. If you are looking for a light version, you are looking for something with a more basic set of features/options. 

The question isn't if it is lacking features, but if it includes the features you really need.

Later, Seeker

---

### Post by trulan on 2010-10-18
I'm all for Lubuntu (One of my machines is a 2001 era Celeron with 256Mb ram, still going strong, Lubuntu all the way) but I think that is missing the point of this thread.  It reminds me of when somebody bragged that Chromiun could start faster than gcalctool (it was true at the time).  There are definitely plenty of applications that use resources poorly.  What are some specific apps in every Ubuntu install that could benefit from some cleaning up, some streamlining?

Looking at my currently running Ubuntu Maverick, (2.4Ghz AMD, 2Gb Ram) the top five memory hogs are:
1. Firefox, at 95 MiB - but that's for Mozilla to fix, not Ubuntu
2. Xorg, at 84 MiB - but that's because of everything running under it, or so I am told.
3. Nautilus, at 82 MiB - that I don't understad.
4. Compiz, at 38 MiB - desktop effects enabled so that's justifiable
5. Skype, at 28MiB - but that's their problem, not Ubuntu's.

One other notable offender is System Monitor.  Why on earth does it consume between 15% and 60% of my CPU?  That is positively awful!  How is the average user supposed to get any useful information about their system's performance what System Monitor about kills the system all by itself?

---

### Post by k3lt01 on 2010-10-19
> **trulan said:**
> One other notable offender is System Monitor.  Why on earth does it consume between 15% and 60% of my CPU?  That is positively awful!  How is the average user supposed to get any useful information about their system's performance what System Monitor about kills the system all by itself?My laptop is similar to yours (check the link in my signature for details) and I am looking at system monitor and my CPU is running at approximately 10% with this page loaded on Firefox and Pidgin running so FF and Pidgin must be using part of that 10% as well! Methinks you have another issue somewhere.

---

### Post by Kazade on 2010-10-19
I think a good rule of thumb should be that background/indicator applications (e.g the panel, IM, Email, Broadcast app (e.g. Gwibber), Music Player, services) should be as streamlined as possible.

Looking at "top" right now the following apps are in my opinion using too much memory:

gwibber
rhythmbox
ubuntuone

and Xorg but I think that's a special case because everything is using it. 

Gwibber seems to be a real resource hog for what it does (92M + 44M for gwibber-service). I'm Python's biggest fan, but I'm pretty sure it's the reason it's so memory hungry.

I've no issue with foreground apps using memory, or tray apps using a large amount of memory when their windows are open. But I really think that if something isn't being used it should be as slim as it can be so the memory can be used on what you are actually doing.

---

### Post by jerrylamos on 2010-10-19
> **trulan said:**
> I'm all for Lubuntu (One of my machines is a 2001 era Celeron with 256Mb ram, still going strong, Lubuntu all the way) but I think that is missing the point of this thread. 
Looking at my currently running Ubuntu Maverick, (2.4Ghz AMD, 2Gb Ram) the top five memory hogs are:
1. Firefox, at 95 MiB - but that's for Mozilla to fix, not Ubuntu
...
3. Nautilus, at 82 MiB - that I don't understad.
4. Compiz, at 38 MiB - desktop effects enabled so that's justifiable
...
You've got some choices.  
#4 I'm running full screen internet so Compiz wouldn't do anything even if it did run on i830 video graphics so I always turn it off.
#1 Firefox.  There's Chromium & Opera among others.  I haven't done a memory hog test on them.
#3 Nautilus.  There's pcmanfm noticeably faster.  I don't know the memory usage.  

Ubuntu is all about customer choice.

Jerry

---

### Post by snowpine on 2010-10-19
> **trulan said:**
> Looking at my currently running Ubuntu Maverick, (2.4Ghz AMD, 2Gb Ram) the top five memory hogs are:
1. Firefox, at 95 MiB - but that's for Mozilla to fix, not Ubuntu
2. Xorg, at 84 MiB - but that's because of everything running under it, or so I am told.
3. Nautilus, at 82 MiB - that I don't understad.
4. Compiz, at 38 MiB - desktop effects enabled so that's justifiable
5. Skype, at 28MiB - but that's their problem, not Ubuntu's.

To put things in perspective, none of these applications is using more than 0.5% of your RAM. What is an acceptable % of RAM that an application should be "allowed" to use, in your opinion, before it is considered a "hog"?

---

### Post by Reiger on 2010-10-19
Ehh, compare that with an aforementioned 256Mb machine, presumably one with graphics that eat from main RAM as well (typical of Intel chippery). So Firefox using about ~95Mb works out as about 37% of RAM gone right there.

---

### Post by MacUntu on 2010-10-19
Finding wasted memory is a task for experienced programmers (ideally ones already familiar with the target package). I'm not sure you'll find lots of those in here.

---

### Post by snowpine on 2010-10-19
> **Reiger said:**
> Ehh, compare that with an aforementioned 256Mb machine, presumably one with graphics that eat from main RAM as well (typical of Intel chippery). So Firefox using about ~95Mb works out as about 37% of RAM gone right there.

You are assuming that Linux is not capable of adapting itself to available resources. Take a Live CD and boot it on several computers with varying amounts of RAM, and you will find that, generally speaking, RAM usage is higher on computers with more RAM, and lower on computers with less RAM, even though they are running the same, identical Live CD.

Anyways, it is a moot point. Ubuntu simply does not support systems with only 256mb of RAM. The [recommended minimum]("https://help.ubuntu.com/community/Installation/SystemRequirements") RAM for Ubuntu is 1GB; in your scenario, assuming Firefox uses 95mb, which is still less than 1% of 1GB. 

So I repeat the question, what *percentage* (not fixed number of mb) of RAM used is acceptable to you?

---

### Post by Reiger on 2010-10-19
> **snowpine said:**
> You are assuming that Linux is not capable of adapting itself to available resources.
Eh, where? But read on:
>  Take a Live CD and boot it on several computers with varying amounts of RAM, and you will find that, generally speaking, RAM usage is higher on computers with more RAM, and lower on computers with less RAM, even though they are running the same, identical Live CD.

Completely irrelevant to something like Firefox. Firefox is demonstrably not capable of scaling its resource usage. So 95MB on Firefox is 95MB of Firefox induced RAM consumption. The Linux kernel is not going to constrain Firefox to using 95MB of RAM if there is that much of memory in RAM+swap; Firefox is simply going to push other apps into swap.


> Anyways, it is a moot point. Ubuntu simply does not support systems with only 256mb of RAM.
It does, or rather this “system requirements” is little more than a random figure pulled out of thin air or the proverbial behind when you consider that a cut down subset of it will run on such low spec machines just fine. Not fine for developing large code bases with, but fine for having a few “big” apps open at the same time and running some background services to provide technical gadgets (like avahi).

> So I repeat the question, what *percentage* (not fixed number of mb) of RAM used is acceptable to you?

To me? Depends on the machine: if I have 8GB to work with a Firefox eating 1GB of that is “okay” even if I might need to change its name into Firepig. If I have only 256MB, 50Mb is rather hefty. You will note that percentage wise that in one case I'm happy if somewhat condescending to give the fox 25% of RAM, but in the other case I'm rather hesitant to hand out 20%.

The reason for that is Firefox is not the only thing on the machine. In the first my heavy web browser is unfortunate but it is really unlikely that the other apps will need anywhere near that amount of RAM together so I'll probably be having plenty of free RAM whatever I do. In the second case however I might be able to fit in Writer, but it will get quite tricky to add in even an xterm. So Firefox consuming a lot of RAM equals in me having to wait minutes rather than <1sec between application switches once I've pushed a couple of things to swap.

---

### Post by ronacc on 2010-10-19
programs that are wasteful of resources in one area ( ram , cpu cycles , disk space ) are very likely wasteful in other areas also . It is never a good thing and always a sign of careless and sloppy programing . Even on a machine with plenty of juice , waste hurts , it may not be as visible but it is still there .

---

### Post by k3lt01 on 2010-10-19
> **snowpine said:**
> Anyways, it is a moot point. Ubuntu simply does not support systems with only 256mb of RAM. The [recommended minimum]("https://help.ubuntu.com/community/Installation/SystemRequirements") RAM for Ubuntu is 1GB; in your scenario, assuming Firefox uses 95mb, which is still less than 1% of 1GB.WRONG! My laptop has 256MB of RAM and it runs **Ubuntu** not Lubuntu or Kubuntu or Xubuntu but **Ubuntu** and it runs it perfectly well with a minimum of work. All you guys who think it wont work are more than free to come to my place and check it out for yourself.

Edit: check the attached screenshot and you will even see the effective RAM is 227MiB.

---

### Post by juancarlospaco on 2010-10-19
This is interesting, i got a metapackage to install over a Ubuntu-Minimal CD,
i think that NOT using GTK/QT does the trick..., 
Wx or Tk apps are lightining fast and with no big resource ungry.

---

### Post by scradock on 2010-10-19
> **snowpine said:**
> 
Anyways, it is a moot point. Ubuntu simply does not support systems with only 256mb of RAM. The [recommended minimum]("https://help.ubuntu.com/community/Installation/SystemRequirements") RAM for Ubuntu is 1GB; in your scenario, assuming Firefox uses 95mb, which is still less than 1% of 1GB. 

So I repeat the question, what *percentage* (not fixed number of mb) of RAM used is acceptable to you?

I don't get your point - to me 95MB is 9.5% of 1GB, not less than 1% - as far as I can see all your percentages are out by a factor of 10. So adding 95MB + 76MB +..... can easily use hundreds of MB, as others have said. Any one app using 10% of available RAM is hogging; if it's an always-on systray applet or something it's obscene.

---

### Post by snowpine on 2010-10-20
> **scradock said:**
> I don't get your point - to me 95MB is 9.5% of 1GB, not less than 1% - as far as I can see all your percentages are out by a factor of 10.

D'oh! :(

---

### Post by NightwishFan on 2010-10-20
I am quite impressed with a modern OS booting using only 200mb of RAM like Ubuntu and Debian. On 64-bit usually it is higher. I agree perhaps it is heavier than it should be, especially considering how much of Gnome is written in C. Applications like Shotwell that are written in GTK+/Vala seem quite promising as the software was written quickly, improves and performs well, is multi-threaded, and very light on resources.

What was said before about using less memory when less is available is true as well, and further gains can be found using vm.swappiness=100. Though I agree some things need to be reviewed to find where gains can be found. Not "cutting corners" of course, just a nice trim down. I am sure users would be happy to see this in the next Ubuntu release notes:

"Improved Performance And Reduced Memory Usage"

As for solutions right now that probably will not be as the default, the only ones I know are:

[LIST]
[*]Disable or uninstall unneeded startup programs and services.
[*]Blacklist unneeded proprietary kernel modules.
[*]Use vm.swappiness=100
[*]Disable compositing, and run metacity in reduced resource mode.
[*]Use a simpler gtk+ theme.
[*]Disable Nautilus and use a lighter program to draw the desktop and browse files.
[*]Enable compcache for compressed RAM swap.
[*]Use a lighter window manager and applications.
[*]Apt-get source and patch and compile programs with options that cut memory usage (advanced).
[/LIST]

As I said obviously few of those would be take into consideration. Though a nice review into improving performance and reduce the time the disk needs to work to open programs etc would be nice for everyone.

---

### Post by papangul on 2010-10-20
Anyone worried about ram usage should first eliminate gwibber.:mad: We can talk about the rest later, when we have time to spare.

btw, opera latest version uses three times more ram at startup compared to version 10.1(last qt version).

---

### Post by Reiger on 2010-10-20
> **juancarlospaco said:**
> This is interesting, i got a metapackage to install over a Ubuntu-Minimal CD,
i think that NOT using GTK/QT does the trick..., 
Wx or Tk apps are lightining fast and with no big resource ungry.
AFAIK, Wx is just a wrapper API on top of the actual toolkit, such as Gtk, Qt, Win32 (ui controls), or Quartz?

So it makes no sense for a GTK/Qt app to be inherently more hoggy/slow than an app written with Wx which under the hood uses the exact same GTK/Qt controls?

---

### Post by seeker5528 on 2010-10-20
> **trulan said:**
> I'm all for Lubuntu (One of my machines is a 2001 era Celeron with 256Mb ram, still going strong, Lubuntu all the way) but I think that is missing the point of this thread.

Lubuntu has the best OOBE on systems with limited RAM or CPU. So if the idea is to create an OOBE that is competitive with Lubuntu but using Gnome, how could comparisons with Lubuntu be missing the point?

I would agree that Lubuntu is not quite as warm and fuzzy, but it's progressing and it's got the right range of features/included software, so makes a good comparison. In some cases it's using the same software as the stock Ubuntu install and at least some of the other stuff is worth considering for a lite version of Ubuntu.

Later, Seeker

---

### Post by juancarlospaco on 2010-10-20
> **Reiger said:**
> AFAIK, Wx is just a wrapper API on top of the actual toolkit, such as Gtk, Qt, Win32 (ui controls), or Quartz?

So it makes no sense for a GTK/Qt app to be inherently more hoggy/slow than an app written with Wx which under the hood uses the exact same GTK/Qt controls?

Yes i know that, but all the gnome stuff that need to be bundled with GTK apps.

Also the most fast UI toolkit i see is Tk, 
the problem is that people say that it does not have a lot of things, and is not true!,
i got Notebook, Wizards, ToolTips, Drag'n'Drop, HTML widget, even GTK themes using only Tk.

Creating a working button on Tk is one-liner.

---

### Post by k3lt01 on 2010-10-20
> **seeker5528 said:**
> Lubuntu has the best OOBE on systems with limited RAM or CPU. So if the idea is to create an OOBE that is competitive with Lubuntu but using Gnome, how could comparisons with Lubuntu be missing the point?

First sentence is extremely debatable.For the 2nd sentence 3 things come to mind.

1. This topic is about making Ubuntu lighter. To me that makes it rather obvious that discussing Lubuntu as an alternative is missing the point. Lubuntu has a different program list to Ubuntu.

2. Lubuntu has NOT received official recognition yet. It may happen it may not happen we don't know.

3. Many people here don't want to use Lubuntu they want to use Ubuntu therefore they are willing to put in the time and effort to help make Ubuntu, and its associated programs (not Lubuntu's programs) a little bit lighter. We use Ubuntu because we like Ubuntu and its features.

---

### Post by ranch hand on 2010-10-20
> **k3lt01 said:**
> First sentence is extremely debatable.For the 2nd sentence 3 things come to mind.

1. This topic is about making Ubuntu lighter. To me that makes it rather obvious that discussing Lubuntu as an alternative is missing the point. Lubuntu has a different program list to Ubuntu.

2. Lubuntu has NOT received official recognition yet. It may happen it may not happen we don't know.

3. Many people here don't want to use Lubuntu they want to use Ubuntu therefore they are willing to put in the time and effort to help make Ubuntu, and its associated programs (not Lubuntu's programs) a little bit lighter. We use Ubuntu because we like Ubuntu and its features.
Just to further discuss Lubuntu on an Ubuntu thread, I hope that it gets recognized as an official member of the Ubuntu Family.

At least as long as it does not become over bloated like Xubuntu which really has no advantage over Ubuntu in the light department.

Lubuntu really is light.  And works well with a lot of added stuff if you are running a box like mine that doesn't need a light distro.

More on topic I had a Ubuntu netboot install last round with the Gnome Desktop meta package as opposed to the Ubuntu  Desktop.  It was a lot lighter but I forget how much difference in ram usage there was.  It was noticable on my 3Gb of ram.  I was running most of the same stuff that is on the ubuntu Desktop including FF.

---

### Post by BwackNinja on 2010-10-21
Sounds like something I'd be interested in messing with.

I can convert python to c no problem, whether the gains are minimal or great. Having a python-free desktop at startup sounds like a nice idea. It would also be cool to see where the biggest performance problems are for the default set of applications.

I'd like to see at least a 50MB drop in boot up RAM usage without needing to turning off or replace any programs. I'm not on a low-spec machine, but I'm always a little obsessive over my resource usage and have a love/hate relationship with python.

(Oh, and I think Lubuntu is awesome too, I hope it becomes official this release)

---

### Post by k3lt01 on 2010-10-21
@ RH and Ninja. I hope Lubuntu gains official recognition as well. It will add another level of choice that people can use and still have official support. Linux is about choice afterall.

---

### Post by seeker5528 on 2010-10-22
> **k3lt01 said:**
> First sentence is extremely debatable.

I have 2 machines I am running at work, currently both have 768 MB RAM, both not fast by todays standards but reasonable CPUs Athlon 2800+ in one and a 2200+ in the other. 

The 2800+ I use for some types of hardware testing, virus scanning, data recovery, these types of things, the difference in performance is not so great that it would necessarily be the deciding factor in choosing the better performance of Lubunu over the extra features of Ubuntu. But there is a pretty noticeable difference, so I didn't even install the Gnome stuff on that machine the last time I reinstalled.

On the 2200+ I never compared the OOBE and I do have a tendency to prefer Gnome so at 768 MB of RAM I will start a Gnome session more than Lubuntu. It's not the most lean install either, I dumped pulse audio, most of the indicator applets, Ubuntu One, but added the unified menu and use kmix as my mixer. Kmix is in my applications to start up so it's automatically started and available in the tray area in both Gnome and Lubuntu.

Up until a few months ago I had 512 MB on the 2200+ no kmix or other mixer/volume related things on the panel, no indicator applet, no network manager, no pulse audio, limited the things that were in the applications to start up. I would switch back and forth between Lubuntu and Gnome using Lubuntu about 75% of the time because the difference was much more significant relative to the amount of time waiting for things to be swapped between RAM and swap space. 

> For the 2nd sentence 3 things come to mind.

1. This topic is about making Ubuntu lighter. To me that makes it rather obvious that discussing Lubuntu as an alternative is missing the point. Lubuntu has a different program list to Ubuntu.

I can't disagree with the 'as an alternative is missing the point' part of that statement. But as a comparison to something that is already lite and you probably want to be competitive with, Lubuntu uses much of the same base, some of the same applications. 

If you are not willing to discuss using different applications, then yes I don't know what the point of this thread is. How can you have a 'lite' version if you include the same list of stuff?

It all goes back to....

If you are looking for lite, you are probably only expecting some core elements of the full version, not necessarily all of the applications, and desktop stuff and not necessarily limiting itself to being a strict subset of the full version, since it is targeted at machines that are more limited in resources.

That's not to say the list of stuff in a lite version that wouldn't be in the stock Ubuntu should vary much, but the applications that are in Lubuntu were selected for a reason.

I'm not a developer, so you can take this with a grain of salt if you wish. 

I am a believer in 'those that do the work should make the final decisions', but I was under the impression that no decisions had been made yet.

If somebody had said this is what I am doing, the long term goal, the short term goal, the focus of the work currently in progress, it probably would have been a different thread.

Later, Seeker

---

### Post by cariboo on 2010-10-22
I've got a really low spec system, that I play with light versions on. The system has a 400Mhz Celeron with 512Mb ram. I have run Maverick on it, after doing an upgrade from Hardy to Lucid..

I did a cli install and added both the Lubuntu desktop and the Gnome desktop environment. There isn't much difference in resource usage between the two, and to me the Gnome desktop just feels better.

---

### Post by ronacc on 2010-10-22
I think there is a good case that can be made for bringing lubuntu into the family as an "official" version . There are still many perfectly good and usefull boxes out there that are rather strained running a modern "full blown" desktop and Ubuntu should not turn their backs on them if the desire to be everybody's linux . There are also those who even though they have well endowed hardware , just don't want or need the baggage that Gnome or KDE carry with them and "unbundling" them can be problematic .

---

### Post by k3lt01 on 2010-10-23
> **seeker5528 said:**
> I have 2 machines I am running at work, currently both have 768 MB RAM, both not fast by todays standards but reasonable CPUs Athlon 2800+ in one and a 2200+ in the other.Your point is?

I just don't understand what exactly you are trying to do and I'm sorry but I don't really care either. This thread is about making Ubuntu lighter on machines. Regardless of your last post, which doesn't actually explain much, I just don't see why you don't understand that.

Check my signature and see what my laptop specs are. I know Ubuntu is capable of running quite well on lightweight machines with a small amount of work. You want to use what you use, others, just like me, want to keep using Gnome. Please respect our choice to help Gnome continue to work well on our machines.

---

### Post by knarf on 2010-10-25
> **MacUntu said:**
> Finding wasted memory is a task for experienced programmers (ideally ones already familiar with the target package). I'm not sure you'll find lots of those in here.
This thread is a good place to discuss things. You'll find that quite a few experienced programmers also read - or at least skim - the forum as that is a good place to find out what users think about their endeavours.
The real work - if any - will be done through the launchpad project which I linked to in the first post in this thread.

---

### Post by knarf on 2010-10-25
> **BwackNinja said:**
> Sounds like something I'd be interested in messing with.

I can convert python to c no problem, whether the gains are minimal or great. Having a python-free desktop at startup sounds like a nice idea. It would also be cool to see where the biggest performance problems are for the default set of applications.

I'd like to see at least a 50MB drop in boot up RAM usage without needing to turning off or replace any programs. I'm not on a low-spec machine, but I'm always a little obsessive over my resource usage and have a love/hate relationship with python.

(Oh, and I think Lubuntu is awesome too, I hope it becomes official this release)
If you have the ability, time and drive to complete a project like that I'd say go for it. It helps if you actually use the program you're working on so you can eat your own dogfood. Contact the upstream project to see if they have anything to add - they might have noticed that their program is a tad obese - and get hacking!

---

### Post by seeker5528 on 2010-10-25
> **k3lt01 said:**
> Your point is?

I just don't understand what exactly you are trying to do and I'm sorry but I don't really care either. This thread is about making Ubuntu lighter on machines. Regardless of your last post, which doesn't actually explain much, I just don't see why you don't understand that.

Yeah, sometimes it's better just to say you don't care about X or Y instead of saying X is wrong or Y is irrelevant.

After re-reading the OP's first post, it appears I (and not just me) were fooled by the thread title into thinking there might be openness in the thread for more generalized discussion of issues with configurations and selection of software running on low spec machines, as opposed to just making the default offerings work better.

It would have probably been better to leave the 'on low-spec machines' part out of the thread title and/or squash discussion of other stuff right away by indicating they are outside the intended scope of project Hog Skinner as defined in the first post and other discussion should take place in another thread. And it might be good to edit the first post with a note including some words to that effect, assuming additional people will see this thread and potential add their own brand of confusion. :P

Later, Seeker

---

### Post by mörgæs on 2010-10-25
Great idea to trim the fat. In our part of the world we can buy more or less the hardware we want, but in an international perspective it is important to think of Ubuntu running on old gear.

In addition to refactoring / optimising applications, an easy step would be having an option of **installing Ubuntu from a menu**. I would happily let go of Compiz, Software Centre, the social web stuff, games, wireless applications (since I am on a stationary), Bluetooth and the like. 

I know that I can install a minimal Ubuntu (and I often do), but most users neither know of nor dare trying this process.

---

### Post by MadsRH on 2010-10-26
Awesome project! I'm not a tech-person so I really can't contribute, but I'm really looking forward to seeing this project mature. Perhaps some work might even float back up-stream ;)

---

### Post by knarf on 2010-11-24
I made a big step towards speeding up my system today. It was very simple and quite effective.
```
sudo apt-get autoremove --purge software-center
```As to the why you might want to read the [bug report]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/446498/comments/3") I just made. In short, it took 21 minutes to install a package using the command line. 20 of those minutes were spent by '/usr/bin/python /usr/sbin/update-software-center'. If ever there was an example of why basic infrastructure should not be built on top of a prototyping language this is it.
I realise that this is probably a bug in software-center and that this is what you get running a pre-release distribution. That is why I run this stuff, to test. In this case the conclusion from the test is that software-center in its current incarnation is not fit to be used as the centerpiece of the number one Linux distribution.
Of course the former 'solution' to this problem is not a real solution. Assuming that Ubuntu wants to keep software-center it will need some tender love and care in the meatgrinder. Maybe the developers should have a look [Vala]("http://en.wikipedia.org/wiki/Vala_%28programming_language%29") or [Genie]("http://en.wikipedia.org/wiki/Genie_%28programming_language%29"), both compiled languages with more 'modern' syntax than plain C. Genie even looks like the illegal offspring of python so they should feel right at home, white-space indentation and all.

---

### Post by zika on 2010-11-24
> **knarf said:**
> I made a big step towards speeding up my system today. It was very simple and quite effective.
```
sudo apt-get autoremove --purge software-center
```As to the why you might want to read the [bug report]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/446498/comments/3") I just made. In short, it took 21 minutes to install a package using the command line. 20 of those minutes were spent by '/usr/bin/python /usr/sbin/update-software-center'. If ever there was an example of why basic infrastructure should not be built on top of a prototyping language this is it.
I realise that this is probably a bug in software-center and that this is what you get running a pre-release distribution. That is why I run this stuff, to test. In this case the conclusion from the test is that software-center in its current incarnation is not fit to be used as the centerpiece of the number one Linux distribution.
Of course the former 'solution' to this problem is not a real solution. Assuming that Ubuntu wants to keep software-center it will need some tender love and care in the meatgrinder. Maybe the developers should have a look [Vala]("http://en.wikipedia.org/wiki/Vala_%28programming_language%29") or [Genie]("http://en.wikipedia.org/wiki/Genie_%28programming_language%29"), both compiled languages with more 'modern' syntax than plain C. Genie even looks like the illegal offspring of python so they should feel right at home, white-space indentation and all.
Yes, I was just one &#8222;Enter&#8220; far from doing the same this Sunday while upgrade-ing Opera... I thought something was severely wrong, but, luckily, I went to lunch with my family, leaving SC to grind... After that, next Opera upgrade was also very slow, but I was a bit wiser (if possible)...
Now that You've mentioned this, I'm tempted, again...
The only thing that stopped me is removal of ubuntu-desktop, dummy package, but...

---

### Post by VMC on 2010-11-24
I'd be curious to know how your Thinkpad T23 handles Natty.
 As of right now, I have a 64-bit machine and daily-live takes a lot of hacking to get it installed. Even then, Compiz crashes. I'm fearing for the worse, but need to wait until after alpha arrives before I make any decisions.

---

### Post by knarf on 2010-11-24
> **VMC said:**
> I'd be curious to know how your Thinkpad T23 handles Natty.
 As of right now, I have a 64-bit machine and daily-live takes a lot of hacking to get it installed. Even then, Compiz crashes. I'm fearing for the worse, but need to wait until after alpha arrives before I make any decisions.
It handles *those bits of Natty which I allow in* just fine. This means:

[LIST]
[*]no software-center, apt-get and aptitude are fine
[*]no standard gnome session - [Xmonad]("http://xmonad.org/") and friends are where Unity and Gnome Shell hope to get in a few years IMnsHO (minus the glitz of course)
[*]no always-on python code, if I see it I kill it and - if necessary - find an alternative
[*]no always-on mono code, same as above
[*]No deskbar applet, notification applet, kitchen sink applet, etc. I revived the old mini-commander for my Gnome needs (on other systems), in Xmonad this functionality is built-in.
[*]No tracker or similar 'I´ll just eat your drives, thanks' surprises
[*]No evolution, I use [Seamonkey]("http://www.seamonkey-project.org/community") or - lately - my web mail server (based on [roundcube]("http://roundcube.net/"))
[/LIST]
Every now - after an upgrade - I test the default session as installed the way Ubuntu does it. Every then I return to my Xmonad session, amazed by the speed this old box still manages when fed the right software.

---

### Post by dino99 on 2010-11-24
Have had the same idea some times ago, but devs has given me a no go :(

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/540798](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/540798)

---

### Post by knarf on 2010-11-24
> **dino99 said:**
> Have had the same idea some times ago, but devs has given me a no go :(

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/540798](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/540798)
One thing you can do to avoid getting unwanted packages installed is to dpkg-hold them before running an upgrade. This only works for packages you know the exact name of and you have to do it every time before an upgrade as this information seems to get lost between them. As an example say that you really don't want to have tomboy, evolution and software-center and that they are currently not installed:
```
sudo apt-get update
sudo dpkg-hold tomboy evolution software-center
sudo apt-get dist-upgrade
```This will keep apt-get from installing those three packages.

A thought... it would be feasible to create a front-end or extension to apt which prompts the user when new (currently uninstalled) packages are to be pulled in by metapackages. If the user says 'no' those packages end up on a blacklist (/etc/apt/blacklist) which gets the dpkg-hold treatment before every upgrade.

Another option is to use the apt Pin: feature. This is normally used to 'pin' a package to a certain version, or to change the preference order for package sources and versions. If the 'Pin-Priority' has a negative value the package will never be installed automatically. It can even remove such packages in some cases - not all though. I experimented a bit with this feature and it seems to offer the potential to keep known unwanted packages away from your system. It does have its rough edges, such as the missing wildcard feature (for which a feature request was made about 10 years ago). It has the advantage that the blacklist mechanism is built into apt-get. My experimental blacklist is meant to keep out the apache webserver as I use lighttpd, all unneeded X servers plus some miscellaneous unwanted packages to exercise the blacklist feature.  
```
$ cat /etc/apt/preferences.d/blacklist
Explanation: Do not install any of the following blacklisted packages
Package: software-center evolution tomboy smartdimmer apache2.2-bin apache2.2-common apache2-mpm-itk apache2-mpm-prefork libapache2-mod-php5 xserver-xorg-video-ark xserver-xorg-video-chips xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-openchrome xserver-xorg-video-r128 xserver-xorg-video-s3virge xserver-xorg-video-sis xserver-xorg-video-tdfx
Pin: release o=Ubuntu
Pin-Priority: -100
```
It does seem to work - evolution was kicked off the system when I ran a dist-upgrade. Maintaining such a blacklist would be a pain in the *** though so it would really be much better if there was a more flexible way to keep unwanted stuff from being installed.

---

### Post by Chris Edgell on 2011-01-15
I must say I LOVED this thread...

Even the spirit of argument allowed so many more points-of-view and facts therein to come out.

I saw how the initial post WOULD cause people who knew from THEIR experience how to conserve resources to bring it.  I like a little back and forth, it never got down to vile lack of decent manners; for that I commend you all.  

The reason I liked the divergence into a little off-topic discourse is because I always am working with little, old computers... but I myself can see how the big-deal would not be catering to me.  But I also see THE MAIN POINT ... how to keep the big-deal from getting bloated.  Like, just because you become the CEO of a company that is bigger than most countries, doesn't mean you should become a fat hog just because you can.  But again you see, big shots seldom remember to stay lean...with yes-men and all, things can get out of control, may lose focus - just because they can...and not to digress too far and long with my analogy, with world economics as they are today, it would have been nice if there had been more people worrying about the fat in high places.  You don't HAVE TO be lean and mean; you can be lean and clean.  (But just like here, we can ask, "Are you listening big boys?"  If you WANT IT to shine, you must polish it.

So thank you all, for so many great insights and pointers , and for letting me see how much so many of you know...it's comforting to someone like me who knows so little that there are those above me spending time giving and caring -- and patiently sharing...and even keeping it real.

---

### Post by jerrylamos on 2011-01-15
Lo spec?  Not sure what that means.  I run Natty on a Thinkpad R31 which has 512 mb of storage actually a bit less the video buffer which is taken out, on a 1 gHz Intel Celeron.  Works O.K. except internet video too jerky.

On the same laptop I've also got tiny core.  Runs in memory entirely so is pretty fast.  It is somewhat of a do-it-yourself kit, so I have installed Minefield which is a Mozilla Firefox trimmed down, flashplugin, nano.  Likely runs as fast as this laptop would go.

There are three Ubuntu's in the 20 gb of hard drive ( actually 18 ) so when the Alpha or Beta won't run I've another partition that will - Lubuntu Lucid, Lucid, Natty.  What breaks is X windows usually.  Unity won't run because of "eye candy" compiz uses for "3D".  There's some promise of a Unity 2D which might run on the integrated intel video graphics.

BTW, tiny core has very unity like menu symbols which squirm and enlarge and add titles as the mouse goes over, reminding me much of Apple.  Autohide of course.  Full screen really means full screen.  Nothing reserved for a panel.  And runs on old hardware.  So if Ubuntu wanted they could do a Unity like desktop without shading and exploding selections.  All in 11 mb including the kernel and system utilities.

Anyway I mostly run Ubuntu because I like the forums, and learn a lot of linux dealing with Alpha & Beta & RC bugs.

Jerry

---

### Post by k3lt01 on 2011-01-15
Well, after a long hiatus from the forums and testing various different forms of Ubuntu, Debian and even Mint, I have found on my poor old little Acer Debian Sid/Experimental minus some bloat is the best for my little machine.

Why I am using Sid/Experimental? Well I like testing things and Squeeze which is brilliant is at least 1 version of Gnome and Kernel behind everyone else hasn't got some of the functionality that I would like. With Sid/Experimental I get Firefox (Iceweasel) 4, Gnome 3 (+ Gnome Shell) will be available again shortly, LibreOffice (OpenOffice has had some developer difficulty), along with the latest versions of many other applications. I also use the Liquorix kernel.

All this on an 8 year old machine that has 256MB of RAM (I do occasionally use another RAM stick boosting it to 512MB) most of the time and a 1.3 GhZ Celeron.

Will I try Unity? Probably not. Why? simple really, I don't like the idea of a Linux distribution having so much material that is copyrighted and not under a full GPL. It leaves very little room for personalization and community improvement

---

### Post by cariboo on 2011-01-15
Unity has a gpl 3 license, what's the problem?

---

### Post by k3lt01 on 2011-01-15
> **cariboo907 said:**
> Unity has a gpl 3 license, what's the problem?Everything else that Canonical wont give a full GPL license to.

---

### Post by jerrylamos on 2011-01-15
> **seeker5528 said:**
> 
People used to suggest Damn Small Linux for the light weight machines, but I never could tell any significant difference performance wise between DSL and a stock Debian installed with the Gnome desktop.

Later, Seeker
For slower pc's I'd recommend tiny core.  runs entirely in memory.  The basic kernel & system utilities filemanager apple-like ( Unity type with autohide ) application selector etc. is 11 mb.  I have it installed as a directory (with a few subdirectories) on Lucid's partition.  I added Minefield ( based on firefox ), flashplugin, nano.  Logging off you have the choice of saving changes. You do need some linux experience and as usual there are many many applications that can be added if you like example abiword etc.  The forums are fairly active and the Q's & A's are very helpful.

Interesting to me that a unity type desktop can be done with a lot less fuss and old hardware if you don't demand shading and exploding mouse clicks.

Jerry

---

### Post by jerrylamos on 2011-01-15
> **seeker5528 said:**
> 
People used to suggest Damn Small Linux for the light weight machines, but I never could tell any significant difference performance wise between DSL and a stock Debian installed with the Gnome desktop.

Later, Seeker
For slower pc's I'd recommend tiny core.  runs entirely in memory.  The basic kernel & system utilities filemanager apple-like ( Unity type with autohide ) application selector etc. is 11 mb.  I have it installed as a directory (with a few subdirectories) on Lucid's partition.  I added Minefield ( based on firefox ), flashplugin, nano.  Logging off you have the choice of saving changes. You do need some linux experience and as usual there are many many applications that can be added if you like example abiword etc.  The forums are fairly active and the Q's & A's are very helpful.

Interesting to me that a unity type desktop can be done with a lot less fuss and old hardware if you don't demand shading and exploding mouse clicks.

Jerry

---

### Post by knarf on 2011-01-15
Our current stable of two T23's and one Medion (but really Acer) 'Titanium' with from 384 to 768 MB of memory and 1.12/1.2 GHz PIII-m to 2 GHz P4 processors still runs Ubuntu in its various guises, from Intrepid (on the 1.12 GHz T23) via Maverick (on the 2 GHz P4) to Natty (on the 1.2 GHz T23). The smoothest running version is Maverick on the P4 but it has to be said that it did run even better with Lucid which means I will revert the 'upgrade' when I find time to do so. The biggest slug is, no surprise again, the 1.12 GHz T23 running Intrepid. The T23 with Natty runs only just OK when using 'full' Natty (minus Unity as that refuses to run with the 'SuperSavage' driver because of a lack of features ***[SIZE=1][COLOR=Gray]1[/COLOR][/SIZE]***) but quite snappy when running the afore mentioned bowdlerized incarnation of Natty. This machine also happens to be my main workstation so it does receive a fair bit of attention.

Would I recommend anyone to run a current Ubuntu distribution on this type of hardware? The answer to that is unfortunately 'no' because of the ever increasing resource demands which are not offset by radically increased functionality or ease of use.

On the other hand something does surprise me time and time again when I help clients, friends and neighbours with their newly purchased hardware which in theory should be miles ahead of my aging machine park. Every time I get to configure their Windows 7 blahblah edition I am disappointed by the performance of these machines. Sporting dual core processors or better running at higher clock speeds than my T23's (which usually run at around 800 MHz (2/3 of their rated clock speed) due to a lack of demand for processor power) and several gigabytes of memory these machines manage to keep me waiting for menus to appear, programs to load, updates to be installed, files to be found and images to be put on the screen. This happens literally every time.

Would these machines fare better when running a lighter load than Microsoft's latest heavyweight? Yes, they would. The question though is whether the added performance would offset the monetary expense and physical waste of a new and old computer.

This is why I run older hardware. It works just fine when treated right, when given the chance. Most of Debian - which is where Ubuntu comes from - treats this hardware right. More and more of Ubuntu does not, unfortunately.  Whether it is memory and processor hogs like all those bits of Python code showing up in the base configuration or 'exotic' requirements like hardware accelerated compositing as needed by Unity does not really matter. The base Ubuntu install is less and less usable on older hardware. The base Debian install does not suffer a similar degradation.

I could just move the remaining bits of hardware to Debian but that would mean giving up. I don't feel like giving up just yet so I'll keep on skinning them hogs for now.

[SIZE=1][COLOR=Gray] [1] I have hacked the savage driver to implement rudimentary NPOT texture support (and other missing features) and got an older version of Unity to 'run' that way - if by 'run' you mean show parts of windows, no legible text and slower than molasses.[/COLOR][/SIZE]

---

### Post by knarf on 2011-01-16
There is a new thread on the forum about a [2-D version of Unity]("http://ubuntuforums.org/showthread.php?t=1668156") which could be relevant in the context of this thread. Given its heritage as a netbook shell, Unity should in theory be tailored to lower-spec hardware found on those machines. The current 3-D incarnation does not fit this description at all, it will be interesting to see whether the 2-D version lives up to its original intended purpose.

---

### Post by teh603 on 2011-01-16
> **knarf said:**
> There is a new thread on the forum about a [2-D version of Unity]("http://ubuntuforums.org/showthread.php?t=1668156") which could be relevant in the context of this thread. Given its heritage as a netbook shell, Unity should in theory be tailored to lower-spec hardware found on those machines. The current 3-D incarnation does not fit this description at all, it will be interesting to see whether the 2-D version lives up to its original intended purpose.I still think that a better version would be to replace Unity and the Netbook shell with something that actually looks like it was designed for serious business use. What you get right now looks like a child's toy computer or an overpriced palm pilot.

---

### Post by cariboo on 2011-01-16
> **teh603 said:**
> I still think that a better version would be to replace Unity and the Netbook shell with something that actually looks like it was designed for serious business use. What you get right now looks like a child's toy computer or an overpriced palm pilot.

I think you're missing the point, the Unity 2-D interface was designed for **arm** powered devices, that it works so well on other devices, is just a bonus. I can't see serious business using arm powered devices on the desktop.

If this is just your opinion, please post it in one of the many Unity threads in Recurring Discussions.

---

### Post by mörgæs on 2011-01-16
> **k3lt01 said:**
> Everything else that Canonical wont give a full GPL license to.

Doesn't Canonical release software under GPL (or a similar license)? If that is the case, I have lost a lot of faith. Please elaborate.

---

### Post by NightwishFan on 2011-01-16
They are talking about this I think:
[http://en.wikipedia.org/wiki/Canonical%27s_contributor_agreement](http://en.wikipedia.org/wiki/Canonical%27s_contributor_agreement)

It doesn't bother me any.

---

### Post by cariboo on 2011-01-16
Even though some of the rights are signed over to Canonical, it is still released under the GPL.

---

### Post by knarf on 2011-01-16
> **teh603 said:**
> I still think that a better version would be to replace Unity and the Netbook shell with something that actually looks like it was designed for serious business use. What you get right now looks like a child's toy computer or an overpriced palm pilot.
While I'm [not to thrilled]("http://ubuntuforums.org/showpost.php?p=10157902&postcount=82") by Unity and its relatives myself I do think it would be a Good Thing**™** if there were a possibility to use the same - or mostly the same - interface on low and high spec hardware. A good (and lightweight) 2D-version of Unity would allow this to be realized and thus remove the chasm which threatens to grow between the 'have-hardware-compositors' and the 'have-no-such-thingamabobs'. It would really fit [Ubuntu]("http://en.wikipedia.org/wiki/Ubuntu_%28philosophy%29") as explained by the [usual]("http://en.wikipedia.org/wiki/Desmond_Tutu") [suspects]("http://en.wikipedia.org/wiki/Nelson_Mandela")...

---

### Post by NightwishFan on 2011-01-16
> **knarf said:**
> While I'm [not to thrilled]("http://ubuntuforums.org/showpost.php?p=10157902&postcount=82") by Unity and its relatives myself I do think it would be a Good Thing**™** if there were a possibility to use the same - or mostly the same - interface on low and high spec hardware. A good (and lightweight) 2D-version of Unity would allow this to be realized and thus remove the chasm which threatens to grow between the 'have-hardware-compositors' and the 'have-no-such-thingamabobs'. It would really fit [Ubuntu]("http://en.wikipedia.org/wiki/Ubuntu_%28philosophy%29") as explained by the [usual]("http://en.wikipedia.org/wiki/Desmond_Tutu") [suspects]("http://en.wikipedia.org/wiki/Nelson_Mandela")...

[http://ubuntuforums.org/showthread.php?p=10366061](http://ubuntuforums.org/showthread.php?p=10366061)

---

### Post by k3lt01 on 2011-01-16
> **mörgæs said:**
> Doesn't Canonical release software under GPL (or a similar license)? If that is the case, I have lost a lot of faith. Please elaborate.
Nightwish has mentioned part of it, Canonical has, at times, had to be dragged kicking and screaming into releasing some of their software under a full GPL. Launchpad was closed source until late 2009, and was only made Open Source due to external pressure, ven then they were going to keep parts of it closed.

While I don't have a problem with organisations protecting their investment I do have a problem with organisations insisting private contributions be copyrighted to them. To me private Intellectual Property Rights outweigh Canonicals right. I also have a problem with Open Source groups using Open Source ideals to expand their Closed Source and organisational copyrights.

I have made my point, I don't expect anyone to agree with me but at least try to understand where I am coming from. People may think its all ok and that is their right I myself have some issues with it. That is my last comment on this matter.

---

### Post by NightwishFan on 2011-01-16
Trust me I hear you. Though to be honest I have invested too much time and effort in Ubuntu to start to mistrust them on a whim (not that your reasons are a whim of course). Mark Shuttleworth has himself donated to organizations such as KDE.

---

### Post by k3lt01 on 2011-01-16
> **NightwishFan said:**
> Trust me I hear you. Though to be honest I have invested too much time and effort in Ubuntu to start to mistrust them on a whim (not that your reasons are a whim of course).I can totally understand your feelings. I've been using Ubuntu for nearly 4 years and it is only a few things that caused my move to Debian. I'll still be around Ubuntu because I give people options on what they can use (heck if they want Windows I'll help them out, I won't like it but I will help them). It is about personal choice after all.

> **NightwishFan said:**
> Mark Shuttleworth has himself donated to organizations such as KDE.I know and I admire him for his work. I like to see self made wo/men do well for themselves.

---

### Post by knarf on 2011-01-17
> **NightwishFan said:**
> [http://ubuntuforums.org/showthread.php?p=10366061](http://ubuntuforums.org/showthread.php?p=10366061)
[http://ubuntuforums.org/showpost.php?p=10363613&postcount=92](http://ubuntuforums.org/showpost.php?p=10363613&postcount=92)

---

### Post by NightwishFan on 2011-01-17
> **knarf said:**
> [http://ubuntuforums.org/showpost.php?p=10363613&postcount=92](http://ubuntuforums.org/showpost.php?p=10363613&postcount=92)

Sorry. I didn't read back that far. :D

---

### Post by wnelson on 2011-01-17
I'm not sure it this is the direction you may want to checkout -- Try lubuntu-netbook, it is available with lubuntu. It has a 2-D style menu system.

---

### Post by mörgæs on 2011-04-17
Today I tried a live boot of 11.04. Everything looked fine, but to my discomfort I saw that the system was eating 400 MB (!) just sitting idle. 

I hope a real installation is not that greedy. Could someone please post the output of **free -m** ?

---

### Post by NightwishFan on 2011-04-17
400mb is not really a high number for a modern Gnome desktop.

---

### Post by dino99 on 2011-04-17
hi guys & gals,

very interesting thread. To me the latest release(s) are too fatty since Jaunty: 
has been added: ureadahead, plymouth, heavy themes, too much useless/unwanted crossed dependencies, kernels getting obese, shell & lot of eye candy stuff, and of course those insane metapackages.

i post a nice blog to bookmark:

[http://linux.koolsolutions.com/](http://linux.koolsolutions.com/)

and a howto about modules:
[http://linux.koolsolutions.com/2009/10/11/howto-blacklisting-kernel-module-from-auto-loading-in-debian/](http://linux.koolsolutions.com/2009/10/11/howto-blacklisting-kernel-module-from-auto-loading-in-debian/)

---

### Post by lucazade on 2011-04-17
> **dino99 said:**
> hi guys & gals,

very interesting thread. To me the latest release(s) are too fatty since Jaunty: 
has been added: ureadahead, plymouth, heavy themes, too much useless/unwanted crossed dependencies, kernels getting obese, shell & lot of eye candy stuff, and of course those insane metapackages.

i post a nice blog to bookmark:

[http://linux.koolsolutions.com/](http://linux.koolsolutions.com/)

and a howto about modules:
[http://linux.koolsolutions.com/2009/10/11/howto-blacklisting-kernel-module-from-auto-loading-in-debian/](http://linux.koolsolutions.com/2009/10/11/howto-blacklisting-kernel-module-from-auto-loading-in-debian/)

Sincerly I don't see how Ubuntu became "fatty" because of plymouth, ureadahead, light-themes, dependencies and metapackages. I can understand about the kernel  like Linus said (even if most drivers are not in use), but the rest seems to me unrelated.
Even if you remove and uninstall this stuff (I use the minimal iso and only selected packages) there are no major improvements and speedups.
Do you have some benchmarks or other infos to say that?

---

### Post by wizard10000 on 2011-04-17
> **cariboo907 said:**
> You aren't going to get any results by generalizing like that, I have a Compaq Mini 110 with the same specs as your EEPC, Unity runs well on it, and I don't see any slow down, running the software center. So for me your bug is invalid.

I also have a Compaq Mini 110 running Kubuntu Natty and the machine uses a bit more than 170mb of memory at idle.  See attached screenshot - this is a plasma desktop with effects enabled and system monitor and ksnapshot running on  my netbook.  system monitor shows RAM usage at 184mb but as I said, system monitor and ksnapshot were running  :)

My KDE desktop uses maybe 40mb more RAM than an LXDE or XFCE install with considerably more functionality.  For me it's a fair trade.

---

### Post by rbrick49 on 2011-04-17
yes when Linus Torvalds designed or invented linux it was designed to run on any machine is that not true

---

### Post by lucazade on 2011-04-17
> **rbrick49 said:**
> yes when Linus Torvalds designed or invented linux it was designed to run on any machine is that not true

:)

1991 - Linux  v0.01 - 10,000 lines of code
2011 - Linux 2.6.38 - 14,294,439 lines of code

natural evolution... if we count only the lines, yes it is obese..

---

### Post by rbrick49 on 2011-04-17
> **lucazade said:**
> :)

1991 - Linux  v0.01 - 10,000 lines of code
2011 - Linux 2.6.38 - 14,294,439 lines of code

natural evolution... if we count only the lines, yes it is obese..
omg what a jump thank you luca

---

### Post by mörgæs on 2011-04-18
> **NightwishFan said:**
> 400mb is not really a high number for a modern Gnome desktop.

400 MB is way beyond acceptable, and I hope it is due to the live boot.

I have three machines with Ubuntu. **free -m** gives

9.10 desktop with LAMP: 139 MB
10.04 desktop with LAMP: 188 MB
10.10 desktop: 136 MB


Anyway, I'll halt my complaining for now until I have done some more thorough testing.

---

### Post by NightwishFan on 2011-04-18
Ah, I am used to 64-bit which is never that low. To be honest I would not complain if modern desktop operating systems continued to be usable on 256mb machines though. :)

---

### Post by screaminj3sus on 2011-04-18
> **mörgæs said:**
> 400 MB is way beyond acceptable, and I hope it is due to the live boot.

I have three machines with Ubuntu. **free -m** gives

9.10 desktop with LAMP: 139 MB
10.04 desktop with LAMP: 188 MB
10.10 desktop: 136 MB


Anyway, I'll halt my complaining for now until I have done some more thorough testing.

saying 400mb is beyond acceptable is simply absurd. For a modern desktop like the latest gnome or kde that's quite low...

If your machine is that low on memory you shouldn't expect miracles out of the heavier de's like gnome and kde and perhaps should look into lxde or xfce.

---

### Post by rbrick49 on 2011-04-18
ron@ron:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          8001        962       7039          0         44        281
-/+ buffers/cache:        636       7365
Swap:         8189          0       8189
ron@ron:~$

---

### Post by NightwishFan on 2011-04-18
Similar to mine. I am running Debian 6 with Gnome Shell though. I have Iceweasel 4, Rhythmbox, Pidgin, Evolution and a terminal up. (64-bit) So I suppose Debian is not terrible on mem usage. With a swap file 512mb of RAM would run all of this.
```
-/+ buffers/cache:        620       2363
```

I wonder if it would help to compile some key apps with -Os instead of -O2. I know Firefox already does that on both Ubuntu and Debian though.

---

### Post by jerrylamos on 2011-04-18
> **screaminj3sus said:**
> saying 400mb is beyond acceptable is simply absurd. For a modern desktop like the latest gnome or kde that's quite low...

If your machine is that low on memory you shouldn't expect miracles out of the heavier de's like gnome and kde and perhaps should look into lxde or xfce.
I'm on vacation in Australia or I'd try free -m on Unity 3D with big fat slow Compiz compared to Unity 2D which doesn't use Compiz.  

After install, do Synaptic refresh then select Unity 2D and install.  On boot, select Unity 2D desktop then try the free -m.

Jerry

---

### Post by lucazade on 2011-04-18
> **jerrylamos said:**
> I'm on vacation in Australia or I'd try free -m on Unity 3D with big fat slow Compiz compared to Unity 2D which doesn't use Compiz.  

After install, do Synaptic refresh then select Unity 2D and install.  On boot, select Unity 2D desktop then try the free -m.

Jerry

classic session (without effects):
                     total       used       free     shared    buffers     cached
Mem:          1001        337        664          0         45        147
-/+ buffers/cache:        144        856
Swap:          765          0        765


unity2d:
                     total       used       free     shared    buffers     cached
Mem:          1001        365        635          0         45        171
-/+ buffers/cache:        148        852
Swap:          765          0        765


unity3d:
                     total       used       free     shared    buffers     cached
Mem:          1001        379        621          0         45        168
-/+ buffers/cache:        165        836
Swap:          765          0        765


really, really close one to another.

---

### Post by mörgæs on 2011-04-18
That was good news :-) Thanks for posting.

---

