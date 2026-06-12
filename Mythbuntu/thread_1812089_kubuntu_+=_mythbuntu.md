---
title: "kubuntu += mythbuntu?"
date: 2011-07-25
forum: Mythbuntu
---

### Post by bs27975 on 2011-07-25
Are there any links to hints, tips, best practices, etc., regarding adding mythbuntu to kubuntu? [Haven't built the machine yet, reading this from firefox / win xp.]

[Presumably there are many advantages to mythbuntu over mythtv, mythbuntu being a media (?) superset + more than mythtv?]

Searching the forum revealed nothing useful. The wiki only has [http://www.mythbuntu.org/existing-ubuntu](http://www.mythbuntu.org/existing-ubuntu), titled "Add to Ubuntu", but then goes on to instruct, it seems, the download of an iso and fresh installing mythbuntu.

I have seen in the past, for example, IIRC, k/ubuntu will have kubuntu/ubuntu/xubuntu- and/or gnome/kde- desktop packages, so I suppose there's a mythbuntu-desktop equivalent. However I'm not looking to replace the kde desktop, but incorporate the mythbuntu 'coherent application whole' within it. [Unless I could log in to the monitor via kde, and the tv via mythbuntu, same computer/graphics card, intel hd3000.] Different X sessions? (Which seems more complex than needed - simple kde desktop on the monitor with a mythbuntu app (?) running on the tv hdmi connector?)

Hints, tips, guides, pointers, links?

Thanks.

Edit:

Bah. Just found this:
> **tgm4883 said:**
> If you are starting with a Kubuntu install, just install mythbuntu-control-centre then configure from there. It will install what it needs.

Presumably the mythbuntu install docs can then be followed, from the point of first entry into the control center.

If there are other gotchas, considerations, best practices to mythbuntu on top of kubuntu, please post.

Thanks.

---

### Post by uteck on 2011-07-27
I do this all the time.  You can use the software center or apt-get to install mythtv and that should be all you need.  I would recomend you first install the mythbuntu PPA repo, [http://mythbuntu.org/repos](http://mythbuntu.org/repos), to ensure you get the latest version.

My current setup is Ubuntu Studio with KDE, and when I want Myth, I just launch the frontend.  Nothing else needs to be done other then point the frontend at the backend.

---

### Post by bs27975 on 2011-07-27
> **uteck said:**
> I do this all the time.  You can use the software center or apt-get to install mythtv and that should be all you need.  I would recomend you first install the mythbuntu PPA repo, [http://mythbuntu.org/repos](http://mythbuntu.org/repos), to ensure you get the latest version.

My current setup is Ubuntu Studio with KDE, and when I want Myth, I just launch the frontend.  Nothing else needs to be done other then point the frontend at the backend.

Thank you very much.

You install mythtv, not mythbuntu-control-centre?

Does mythbuntu not bring with it a greater richness of functionality / coordination / ease of coordinated configuration over mythtv alone? Such as voip, caller id, im, audio, and so on and so forth?

I'll try saying that again - as I understand it, to get 'all that one can get' requires quite a number of applications beyond mythtv itself, and getting them all to play nice together can be challenging. My impression of mythbuntu was it bundles all those applications together (in a repository / making it easier to download a group of compatible applications), and makes the job of configuring them all (consistently) a little easier.

Am I misunderstanding anything?

Is there a link or comparison around that describes the differences between mythbuntu, and mythtv alone?

Thanks for any insights.

---

### Post by thatguruguy on 2011-07-27
> **bs27975 said:**
> Thank you very much.

You install mythtv, not mythbuntu-control-centre?

Does mythbuntu not bring with it a greater richness of functionality / coordination / ease of coordinated configuration over mythtv alone? Such as voip, caller id, im, audio, and so on and so forth?

I'll try saying that again - as I understand it, to get 'all that one can get' requires quite a number of applications beyond mythtv itself, and getting them all to play nice together can be challenging. My impression of mythbuntu was it bundles all those applications together (in a repository / making it easier to download a group of compatible applications), and makes the job of configuring them all (consistently) a little easier.

Am I misunderstanding anything?

Is there a link or comparison around that describes the differences between mythbuntu, and mythtv alone?

Thanks for any insights.

Mythbuntu is a MythTV frontend and backend system running on a somewhat stripped-down version of Xubuntu, which is the lightest officially-supported DM running on Ubuntu (until Lubuntu officially becomes part of the Ubuntu family).  It doesn't include any office applications, for instance, because it is intended to act as a pvr/media center. However, you can install anything you want on it, since it has access to all the Ubuntu repositories.  The question is, why would you want to?  Do you really want to do spreadsheets on your TV?

Kubuntu is the "heaviest" of all the ubuntu releases, in terms of memory usage, etc.  Since the MythTV frontend already has its own 10-foot UI, there really isn't any advantage to running a resource-heavy DM on the box that serves as your MythTV backend.

Here's the solution I use in my home.  I have Mythbuntu on a computer connected to my TV.  It works as a DVR, DVD player, and also has several hundred videos stored on it.  I also have various game emulators (for NES, SNES, PlayStation, Game Cube, etc.) plus various classic games to play on those emulators, as well as some Windows games with good Wine compatibility and several good Linux-native games.  I also have XBMC (for the excellent content available through Navi-X and other XBMC plugins) and Hulu installed on that computer.  It's an all-around entertainment center.

The other computers in my house run Ubuntu Natty, and have the Myth-frontend on them.  I can stream videos, recordings, or live TV to those computers as needed.  I can also stream videos to my tablet pc through upnp when I want to hide in my room from my kids.

And yes, you want to install the mythbuntu control center on any computer running MythTV.  It's the easiest way to control plugins, etc.

---

### Post by nickrout on 2011-07-27
> **bs27975 said:**
> Thank you very much.

You install mythtv, not mythbuntu-control-centre? install the control centre and from there set what functionality you want (frontend, backend whatever) and the right packages will be installed. > 

Does mythbuntu not bring with it a greater richness of functionality / coordination / ease of coordinated configuration over mythtv alone? Such as voip, caller id, im, audio, and so on and so forth?No> 

I'll try saying that again - as I understand it, to get 'all that one can get' requires quite a number of applications beyond mythtv itself, and getting them all to play nice together can be challenging. My impression of mythbuntu was it bundles all those applications together (in a repository / making it easier to download a group of compatible applications), and makes the job of configuring them all (consistently) a little easier.

Am I misunderstanding anything?

Is there a link or comparison around that describes the differences between mythbuntu, and mythtv alone?

Thanks for any insights.

I think that you presume that mythbuntu holds more than it really does. If you want the entire mythbuntu experience, grab an old machine (or use a virtual box) and install it to see. If you want the entire mythbuntu experience on your existing kubuntu box then ```
sudo aptitude install mythbuntu-desktop
``` will do it for you.

PS see here for the defunct SIP phone plugin:

[http://www.mythtv.org/wiki/MythPhone](http://www.mythtv.org/wiki/MythPhone)

---

### Post by thatguruguy on 2011-07-27
> **nickrout said:**
> I think that you presume that mythbuntu holds more than it really does.

My Mythbuntu box just made me a nice sandwich.  However, it always uses too much mayonnaise, which is clearly a bug.

---

### Post by bs27975 on 2011-07-27
Thank you nickrout for the excellent clarity of your message.

And following and expanding on it: Add the mythbuntu control center to my kubuntu, get happy, see what's what, then virtual box the mythbuntu iso, see what's what, and see if dedicating yet another piece of hardware in the living room suits me. In the meantime, add the mythbuntu control center to any other computers in the house, and enjoy the richness of that functionality, too.

Thanks again for the clarity.

---

### Post by bs27975 on 2011-07-27
> **thatguruguy said:**
> My Mythbuntu box just made me a nice sandwich.  However, it always uses too much mayonnaise, which is clearly a bug.

Why do you waste our time?

---

### Post by thatguruguy on 2011-07-27
> **bs27975 said:**
> Why do you waste our time?

Did you even read my earlier post?  I answered every question you had.

---

### Post by bs27975 on 2011-07-27
> **nickrout said:**
> PS see here for the defunct SIP phone plugin:

[http://www.mythtv.org/wiki/MythPhone](http://www.mythtv.org/wiki/MythPhone)

Thanks for that reminder.

I now remember reading some time ago that the 'show the caller id on the tv when a call comes in' functionality is available in a number of other ways now. This getting into a whole other range of (nifty)(network) notification functionality. e.g. TV or not, the caller id coming up on all displays in the house.

The idea of a videophone over Myth / via the TV, never being particularly attractive to me. Although it probably is to others.

---

### Post by bs27975 on 2011-07-27
> **thatguruguy said:**
> Did you even read my earlier post?  I answered every question you had.

I read it, haven't had a chance to respond to it. In a moment.

Wasn't referring to that post but to the 'bug report'.

---

### Post by bs27975 on 2011-07-27
> **nickrout said:**
> [QUOTE=bs27975]Does mythbuntu not bring with it a greater richness of functionality / coordination / ease of coordinated configuration over mythtv alone? Such as voip, caller id, im, audio, and so on and so forth?
No
[QUOTE=bs27975]I'll try saying that again - as I understand it, to get 'all that one can get' requires quite a number of applications beyond mythtv itself, and getting them all to play nice together can be challenging. My impression of mythbuntu was it bundles all those applications together (in a repository / making it easier to download a group of compatible applications), and makes the job of configuring them all (consistently) a little easier.

Am I misunderstanding anything?[/quote]

I think that you presume that mythbuntu holds more than it really does.[/quote]

(Or mythtv itself, for that matter, presumably, then.)

Thank you for this - so, in essence mythtv package + plugin control user interface friendliness = mythbuntu.

Help me out here then, please - it is my impression that the myth ecosystem, tying together a number of applications / functionality (convergence) is much greater / larger than mythtv (the application) itself. [And from what you say here, then, mythbuntu does not delve into that larger ecosystem.]

There is a lot of (documentary) stuff out there. One can wander around the mythtv or voip-info forums for days, and still not come out with a coherent whole.

Are there any good links out there that simplify the explanation / description of this myth ecosystem? Perhaps from a top down (what are the elements and nature of this beastie / pack of animals) perspective branching out to details, rather than a bottom up (this is all the technical details of this particular very small piece, and there are > 4k more other such beasties, not all of which play together nicely) perspective?

The myth ecosystem, not just the mythtv application itself.

Thanks for any clarity or insights on this.

---

### Post by nickrout on 2011-07-27
If you have the CID info on a computer (eg using asterix somewhere in the house) you can use mythosd to display a message.

[http://www.mythtv.org/wiki/Little_Gems#mythtvosd](http://www.mythtv.org/wiki/Little_Gems#mythtvosd)

I use it for messages like "get off the TV and get into the kitchen for dinner|do your homework" etc

---

### Post by bs27975 on 2011-07-27
> **nickrout said:**
> If you have the CID info on a computer (eg using asterix somewhere in the house) you can use mythosd to display a message.

[http://www.mythtv.org/wiki/Little_Gems#mythtvosd](http://www.mythtv.org/wiki/Little_Gems#mythtvosd)

I use it for messages like "get off the TV and get into the kitchen for dinner|do your homework" etc

Cool. Presumably the kids hate you.

Supper's ready, router going down in 5 ... 4 ... <save your game> ... 3 ... <oops, too late>

---

### Post by bs27975 on 2011-07-27
> **thatguruguy said:**
> Mythbuntu is a MythTV frontend and backend system running on a somewhat stripped-down version of Xubuntu, which is the lightest officially-supported DM running on Ubuntu (until Lubuntu officially becomes part of the Ubuntu family).  It doesn't include any office applications, for instance, because it is intended to act as a pvr/media center.

Yep, get that. Wasn't talking about the distro, but the add-on. Apologies if I'm misusing or abusing the terms (e.g. 'Mythbuntu'), there's so much here / flexibility, and this Mythbuntu forum talks not only about the distro, but about add-ons too.

> **thatguruguy said:**
> However, you can install anything you want on it, since it has access to all the Ubuntu repositories.

And the reverse, too, install a *buntu distro, such as kubuntu, and add on mythbuntu. Which is the premise of my question / this thread.


> **thatguruguy said:**
> The question is, why would you want to?  Do you really want to do spreadsheets on your TV?

Think bigger. Not all are coming from your perspective.

- I do not need YAMTM, Yet Another Machine To Maintain. I already have a computer near the TV, VGA to monitor, HDMI to 1080p TV, P4 2.8, working just fine. XP, with VLC.
- I do not need the additional expense. (Let alone, YATTB - Yet *Another* Thing To Back Up, requiring yet more redundant disk space elsewhere in the place.)
- I'm good with walking to the corner, doing computer things there, be it web, e-mail, open office, vnc, or anything else I might be inclined towards, then back to the couch, grabbing the remote, and playing a blu-ray or .avi. Works for me.
- One computer, two display outputs, who could ask for more?

> **thatguruguy said:**
> Kubuntu is the "heaviest" of all the ubuntu releases, in terms of memory usage, etc.

Yep. Thank goodness it has all that rich functionality up front and center. Great, isn't it!

- Remember, from original post, computer coming in is an i7-2600k (quad cpu w/ht), 3.4GHz automatically overclocking at least +4 steps, HD3000 video on board, 8GB memory, minimum, with all the associated goodness that comes with such a system, such as 6Gbps SATA drives. If I have to worry about horsepower at this point, I'm packing it in and going back to smoke signals.

> **thatguruguy said:**
> Since the MythTV frontend already has its own 10-foot UI, there really isn't any advantage to running a resource-heavy DM on the box that serves as your MythTV backend.

Course there is. Although, perhaps not for you, as you say. But you're not me, and I don't suspect I'm alone.

Sit there, do computer things on the monitor, sit there, do entertainment things from the couch. One computer - two displays.

[I should add / have added - I don't do gaming. So, for example, the HD3000 video should do me fine. If not, I can add a 2nd video card in later.]

> **thatguruguy said:**
> Here's the solution I use in my home.  I have Mythbuntu on a computer connected to my TV.  It works as a DVR, DVD player, and also has several hundred videos stored on it.  I also have various game emulators (for NES, SNES, PlayStation, Game Cube, etc.) plus various classic games to play on those emulators, as well as some Windows games with good Wine compatibility and several good Linux-native games.  I also have XBMC (for the excellent content available through Navi-X and other XBMC plugins) and Hulu installed on that computer.  It's an all-around entertainment center.

I'm glad this works for you. But it's not what I'm pursuing at the moment, nor is it what I asked about.

> **thatguruguy said:**
> The other computers in my house run Ubuntu Natty, and have the Myth-frontend on them.  I can stream videos, recordings, or live TV to those computers as needed.  I can also stream videos to my tablet pc through upnp when I want to hide in my room from my kids.

Good to know. Thanks. What are you using for a gateway - OpenWRT?

> **thatguruguy said:**
> And yes, you want to install the mythbuntu control center on any computer running MythTV.  It's the easiest way to control plugins, etc.

Thanks, I'm getting that. Bonus. But got to get this coming box up and going first. You remind me, here, that I've been mentally focusing on establishing a hybrid back/front end, but never actually said that in any of my questions.

First, however, I have to get my head around the nature of this beastie / ecosystem, know all the elements in play, and figure out a plan and order of attack. Evidently I have to do some mental expectation shifting and phase in to the reality of what's present, too.

Thus this thread, and these questions.

---

### Post by thatguruguy on 2011-07-28
If you have no interest in streaming to other computers, there are much easier solutions than doing a mythtv install.

For instance, you may want to consider XBMC, with an installation of tvheadend to act as the DVR portion.

---

### Post by declanmullen on 2011-07-31
I've read in several posts that to add mythbuntu to an existing kubuntu system; install the mythbuntu control center and use it to add in the extra mythbuntu/mythtv bits that are wanted. However it hasn't worked that smoothly for me. The following is what I did and the issues I encounted. Should I have done something different ?

What I did:

Installed a fresh Kubuntu 11.04 (x86 32bit, Alternative CD). 

Made sure system packages were all up to date. 

Installed the control center 
```
apt-get install mythbuntu-control-centre
```

Started the control center and sucessfully used it to install the proprietary codecs (ie libdvdcss2). :D

Then tried to use the control center to install the ssh service. On hitting Apply, the control center window greyed and the mouse pointer changed to the animated 'processing' pointer, however after 10 mins it never completed. I closed the control center and installed the ssh serer via apt-get and it did it within 2 mins. I then tried to use the control center to install the mythtv frontend and backend, however it never completed either. :( 

I then tried to use the control center to launch the restricted drivers manager, however clicking that button did nothing. However launching the drivers manager directly from KDE worked fine. :(

Has anyone else seen these types of issues with trying to use the control center from within a KDE desktop system ?

Thanks.

---

### Post by tgm4883 on 2011-07-31
> **declanmullen said:**
> I've read in several posts that to add mythbuntu to an existing kubuntu system; install the mythbuntu control center and use it to add in the extra mythbuntu/mythtv bits that are wanted. However it hasn't worked that smoothly for me. The following is what I did and the issues I encounted. Should I have done something different ?

What I did:

Installed a fresh Kubuntu 11.04 (x86 32bit, Alternative CD). 

Made sure system packages were all up to date. 

Installed the control center 
```
apt-get install mythbuntu-control-centre
```

Started the control center and sucessfully used it to install the proprietary codecs (ie libdvdcss2). :D

Then tried to use the control center to install the ssh service. On hitting Apply, the control center window greyed and the mouse pointer changed to the animated 'processing' pointer, however after 10 mins it never completed. I closed the control center and installed the ssh serer via apt-get and it did it within 2 mins. I then tried to use the control center to install the mythtv frontend and backend, however it never completed either. :( 

I then tried to use the control center to launch the restricted drivers manager, however clicking that button did nothing. However launching the drivers manager directly from KDE worked fine. :(

Has anyone else seen these types of issues with trying to use the control center from within a KDE desktop system ?

Thanks.

start mythbuntu-control-centre from the command line and see if it's spitting out errors

---

### Post by declanmullen on 2011-08-02
> **declanmullen said:**
> I've read in several posts that to add mythbuntu to an existing kubuntu system; install the mythbuntu control center and use it to add in the extra mythbuntu/mythtv bits that are wanted. However it hasn't worked that smoothly for me. 

I resolved the issues by installing the mythbuntu-desktop and now the control center works fine from either a KDE session or a mythbuntu session :

```
apt-get install mythbuntu-desktop
```

Though I suggest one doesn't do the install while a KDE session is running, because my first attempt to do that was done from within a KDE session and the install hung half way thru. Logging out of the KDE session and reattempting the install from the console worked fine.

---

### Post by declanmullen on 2012-05-07
Did a fresh install of kubuntu 12.04 32bit.
Installed the mythbuntu-control-centre package
Ensured system has all its packages upgraded to the latest (ie apt-get update; apt-get upgrade).

On running mythbuntu-control-centre I've noticed that it cannot install packges. When I ask it to install a package the mouse pointer changes to the animated "processing" pointer but it never completes. I've re-run it from the command line, so I can capture any error messages, ie
```
root@pvr:~# mythbuntu-control-centre
```
Here's what happens when I try to get it to install LIRC:

I go to the Infrared tasks and click on "USM & Serial Remote support via LIRC" and then click Apply and Apply again (ie to install the lirc package). This produces the following error output:
```
Traceback (most recent call last):
  File "/usr/bin/mythbuntu-control-centre", line 238, in summaryApply
    self.commit(self.install, self.remove, self.request_unauth_install)
  File "/usr/bin/mythbuntu-control-centre", line 297, in commit
    self._run_transaction(t)
  File "/usr/bin/mythbuntu-control-centre", line 303, in _run_transaction
    apt_dialog.set_icon(icon = theme.load_icon("update-manager", 16, 0))
glib.GError: Icon 'update-manager' not present in theme
```

If I install "mythbuntu-desktop" the issue is fixed. However I'ld prefer to fix the problem without installing the whole mythbuntu-desktop because I don't want all its XFCE tools.

Is there a way to fix the above issue without installing the whole mythbuntu-desktop ?

Thanks,
Declan

---

### Post by tgm4883 on 2012-05-07
> **declanmullen said:**
> Did a fresh install of kubuntu 12.04 32bit.
Installed the mythbuntu-control-centre package
Ensured system has all its packages upgraded to the latest (ie apt-get update; apt-get upgrade).

On running mythbuntu-control-centre I've noticed that it cannot install packges. When I ask it to install a package the mouse pointer changes to the animated "processing" pointer but it never completes. I've re-run it from the command line, so I can capture any error messages, ie
```
root@pvr:~# mythbuntu-control-centre
```
Here's what happens when I try to get it to install LIRC:

I go to the Infrared tasks and click on "USM & Serial Remote support via LIRC" and then click Apply and Apply again (ie to install the lirc package). This produces the following error output:
```
Traceback (most recent call last):
  File "/usr/bin/mythbuntu-control-centre", line 238, in summaryApply
    self.commit(self.install, self.remove, self.request_unauth_install)
  File "/usr/bin/mythbuntu-control-centre", line 297, in commit
    self._run_transaction(t)
  File "/usr/bin/mythbuntu-control-centre", line 303, in _run_transaction
    apt_dialog.set_icon(icon = theme.load_icon("update-manager", 16, 0))
glib.GError: Icon 'update-manager' not present in theme
```

If I install "mythbuntu-desktop" the issue is fixed. However I'ld prefer to fix the problem without installing the whole mythbuntu-desktop because I don't want all its XFCE tools.

Is there a way to fix the above issue without installing the whole mythbuntu-desktop ?

Thanks,
Declan

Can you file a bug at [https://bugs.launchpad.net/mythbuntu](https://bugs.launchpad.net/mythbuntu) so we can take a look at that?

---

### Post by declanmullen on 2012-05-08
[https://bugs.launchpad.net/mythbuntu/+bug/996591]("https://bugs.launchpad.net/mythbuntu/+bug/996591")

---

