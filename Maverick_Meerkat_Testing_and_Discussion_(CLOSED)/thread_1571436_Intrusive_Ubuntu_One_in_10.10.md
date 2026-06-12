---
title: "Intrusive Ubuntu One in 10.10"
date: 2010-09-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by therobspecial on 2010-09-09
I just updated to the 10.10 beta and things are more or less moving smoothly thus far.  The only thing that is really distracting is that in my main folders (Documents, Pictures & Downloads) there is an ugly pink bar with a check box to sync with Ubuntu One.  I don't use Ubuntu One and I want this bar removed, but I can't figure out how to remove it.  There doesn't seem to be a setting in the Ubuntu One control panel, and I don't even have an account linked to it.  Can anyone help me out with removing this bar?  Thanks.

---

### Post by Joeb454 on 2010-09-09
*Thread moved to **Maverick Meerkat Testing and Discussion***

I think you can go to System > Administration > Startup Programs (or something similar to that name, I'm not near an Ubuntu machine at the minute), and disable Ubuntu One from starting.

I seem to remember reading somewhere that this will stop it prompting you in the directories you mentioned :)

---

### Post by ranch hand on 2010-09-09
> **therobspecial said:**
> I just updated to the 10.10 beta and things are more or less moving smoothly thus far.  The only thing that is really distracting is that in my main folders (Documents, Pictures & Downloads) there is an ugly pink bar with a check box to sync with Ubuntu One.  I don't use Ubuntu One and I want this bar removed, but I can't figure out how to remove it.  There doesn't seem to be a setting in the Ubuntu One control panel, and I don't even have an account linked to it.  Can anyone help me out with removing this bar?  Thanks.
```

apt-get purge ubuntuone-client

```

---

### Post by teachop on 2010-09-09
In Nautilus there is a menu something like:  File>Ubuntu One>Show Ribbon...

---

### Post by howefield on 2010-09-10
> **teachop said:**
> In Nautilus there is a menu something like:  File>Ubuntu One>Show Ribbon...

There is, only it is called Hide Ribbon :)

It becomes File > Ubuntu One > Show Ribbon in Some Folders after you choose the Hide option. 

Just to say, that this will do only that - hide the ribbon, the ubuntuone-syncdaemon will still be running.

---

### Post by kahumba on 2010-09-10
Ubuntu One reminds me of Vista UAC in that both are (well the UAC "was") intrusive, overrated and underused.

---

### Post by kansasnoob on 2010-09-10
> **ranch hand said:**
> ```

apt-get purge ubuntuone-client

```

+1! At least for now ;)

I expect them at some point to do with ubuntuone packages what they've done in the past basically making it a "hard" dependency. But most recently I used Synaptic and did this:

> Commit Log for Sun Sep  5 21:30:55 2010


Removed the following packages:
libsyncdaemon-1.0-1
python-ubuntuone-client
python-ubuntuone-storageprotocol
tomboy
ubuntuone-client

So far so good :D

This is one of the reasons I keep looking at a "pure Gnome" conversion for Ubuntu, but my greatest concern is security, and I've not yet convinced myself that it's totally safe to do it!

I've also had little time to experiment lately but if anyone else cares to give it a whirl I simply install my *buntu of choice and then basically do like it says here in the **Playing Around** section:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Except I substitute the package "gnome-desktop-environment" for whatever package is listed at the end of those commands. For instance if I had Ubuntu installed I could look here:

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

Only at the end of that command I'd substitute "&& sudo apt-get install xubuntu-desktop" with "&& sudo apt-get install gnome-desktop-environment".

But **there are many caveats!** **[COLOR="Red"]I'm far from being at a point where I'd recommend it![/COLOR]**

Then again if someone wants a more "pure" Gnome they could just use Debian, but I love Ubuntu other than some of the Ubuntu specific "tweaks" :D

I must add though that the real beauty of Ubuntu is the 6 month release cycle. Currently Hardy is still good for several months, Jaunty has about one month, Karmic 6 months longer than Jaunty, and Lucid's rocking for another 2 1/2 years!

Should someone not be able to get any current Ubuntu to run on their hardware there are sooooooooooo many more distros:

[http://distrowatch.com/](http://distrowatch.com/)

I sometimes have to use a different distro on specific hardware, lately I've used Puppy's new "lupu" (aka: Lucid Puppy) on a few machines and it rocks.

So even Puppy benefited from Ubuntu :D

---

### Post by ranch hand on 2010-09-10
The only reason that I recommended that is that he plainly stated that he did not and will not be using Ubuntuone.  There is no purpose in leaving it on there.

As for the reasoning that we are testing and should therefore leave it, I find it lacking.

We need to test the OS as we will use it.  The OP has no interest in using this feature.  Will removing it cause other problems?  Are we to leave this until after the Final to find out?  That is not a good option.

I have no intention of using it either.  I have it on some of my installs but not the 2 I use most.  The only difference I see is that I am not wasting the space on those 2 that I am on others.  To date, that is the only difference.

---

### Post by 23meg on 2010-09-10
> **kansasnoob said:**
> 
I expect them at some point to do with ubuntuone packages what they've done in the past basically making it a "hard" dependency.

Of what? When was that the case? 

[QUOTE=kansasnoob]This is one of the reasons I keep looking at a "pure Gnome" conversion for Ubuntu,

...
<snip>[/QUOTE]

```
sudo apt-get install gnome-stracciatella-session
```

---

### Post by kansasnoob on 2010-09-10
> **23meg said:**
> Of what? When was that the case? 



```
sudo apt-get install gnome-stracciatella-session
```

Most recently "gdebi", therefore there's no reason to think Synaptic will work properly after it's fazed out.

Another instance is "pulseaudio". Should someone need to revert to pure alsa it can be nearly impossible.

And plymouth has been a nightmare for quite a few people.

I hope they don't make "ubuntuone" a hard dependency but can you assure me that they won't?

BTW "gnome-stracciatella-session" currently only deals with "notify-osd" and it's not been updated since Dec. 2009:

> stracciatella-session (0.0.3) lucid; urgency=low

  * remove wrapper (uneeded with new GDM as GDMSESSION is exported by
    it) and install from Makefile
  * gnome-stracciatella.desktop.in: call gnome-session instead of wrapper

 -- Didier Roche <didrocks@ubuntu.com>  Mon, 07 Dec 2009 19:52:02 +0100

stracciatella-session (0.0.2) jaunty; urgency=low

  * debian/control: Version the notification-daemon release, so that
    it won't get satisfied by notify-osd's Provides:.

 -- Martin Pitt <martin.pitt@ubuntu.com>  Thu, 19 Feb 2009 18:04:38 +0100

stracciatella-session (0.0.1) jaunty; urgency=low

  * Initial release. (See UbuntuSpec:stracciatella-session)

 -- Martin Pitt <martin.pitt@ubuntu.com>  Wed, 18 Feb 2009 20:28:59 +0100


And I would not waste Martin Pitt's time requesting changes to that unless I'd tested the changes myself.

But, why are my comments in question?

Mark Shuttleworth said this just the other day:

> 

As David said, we prefer to avoid "Advanced" option sets and questions.
They create alternative code paths that are inevitably poorly tested,
and compounded by one another. [B][COLOR="Red"]We are very fortunate to benefit from the
amazing Debian installer[/COLOR][/B] on the alternative install CD that provides
very precise control over the install. That's our "Advanced" install :-)

Mark


[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087/comments/38](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087/comments/38)

We're not in competition but rather we compliment each other :D

I just complimented Ubuntu on it's addition to Puppy :D

Everyone should give lupu a test drive. Best Puppy ever - because of Ubuntu!

What's wrong with saying that?

I see all of Linux benefiting from each distros successes and failures. IMHO Ubuntu so far does the best at learning from the same ;)

But why should that deter me from seeking my own personal "spin" on Ubuntu?

The greatest thing about open source is that we can all tweak as we wish :D

And I highlighted the fact that I was worried about security.

---

### Post by 23meg on 2010-09-10
You seem to think that certain default desktop components are arbitrarily made "hard dependencies" (which most of your examples actually aren't, of any essential components, but anyway) without a particular reason, and build [slippery slope arguments]("http://en.wikipedia.org/wiki/Slippery_slope") on top of that. I'm not sure where you get that idea, but it's just wrong.

> **kansasnoob said:**
> Most recently "gdebi", therefore there's no reason to think Synaptic will work properly after it's fazed out.

There's no reason *not* to; Synaptic doesn't depend on GDebi. It's completely irrelevant.

> **kansasnoob]Another instance is "pulseaudio". Should someone need to revert to pure alsa it can be nearly impossible.[/QUOTE]

Not only is it [very much possible]("http://ubuntuforums.org/showthread.php?p=7821384&highlight=disable#post7821384") to entirely disable PulseAudio, but you don't even have to remove the package from your system to do it (which you can if you want to said:**
> And plymouth has been a nightmare for quite a few people.

There's [a reason]("https://launchpad.net/ubuntu/+source/plymouth/0.8.0~-8") why Plymouth is a dependency of mountall, and again, [you don't have to remove Plymouth]("http://ubuntuforums.org/showpost.php?p=9056696&postcount=569") in order not to have a splash screen.

You want a 20-second boot on a three-year old machine without an SSD, with a modern init system to boot (forgive the pun)? Then you need this kind of integration. If not, and the ability to remove every single package without "hard dependencies" matters more for some reason, there are other distributions whose packages you can install and remove more liberally. That's just not Ubuntu's top priority.

> **kansasnoob]I hope they don't make "ubuntuone" a hard dependency but can you assure me that they won't?[/QUOTE]

Why would I have to assure you? It's you who's raising the slippery slope argument, so the onus is on you to come up with a good reasoning as to why it can possibly be a "hard dependency" (and *of what*, I still keep wondering). As you can see above, your arguments so far don't hold much water  said:**
> BTW "gnome-stracciatella-session" currently only deals with "notify-osd" and it's not been updated since Dec. 2009:

That's [not]("http://www.piware.de/2009/02/the-stracciatella-gnome-session/") [exactly true]("https://wiki.ubuntu.com/DesktopTeam/Specs/Jaunty/StracciatellaSession").

> **kansasnoob]And I would not waste Martin Pitt's time requesting changes to that unless I'd tested the changes myself.[/QUOTE]

I thought you wanted an easy way to use "vanilla GNOME" to the greatest extent practical said:**
> But, why are my comments in question?

Because they can be misleading to people who aren't informed well enough about the issues you raise.

---

### Post by kansasnoob on 2010-09-10
Well, regarding "slippery slopes" here was one:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628087)

I filed that bug report and read the first reply:

> I believe this was intentionally removed as part of the installer redesign ............

Look at Mark's comment #14:

> 

I think there are two separate issues:

 1. we need an effective way to rename a machine post-install.
 2. we need to take a view on how important it is to expose the name during install, and how visible to make the option to change it.

If name conflicts are a problem, then [1] is just as important as [2], since we can't put all our eggs in the basket of "getting it right at install time".

I'm subscribing Michael Forrest, who's the designer responsible, for comment on the rationale for having dropped it.

Mark


It took me getting involved at Ayatana to get Mark involved in that, so I think I can say I work fairly hard at trying to make Ubuntu better.

Most importantly, and back to the "slippery slope", Mark's #1 is :

> we need an effective way to rename a machine post-install.

Well ,we still could in Hardy, maybe Intrepid, I don't quite remember when it changed but it certainly has been gone for quite a while!

So there have been times that we truly have gone down that slippery slope and no one paid attention!

Furthermore I was very clear, and even highlighted my doubts, about pursuing my "experiment".

Must I now never share an opinion again?

---

### Post by 23meg on 2010-09-10
> **kansasnoob said:**
> It took me getting involved at Ayatana to get Mark involved in that, so I think I can say I work fairly hard at trying to make Ubuntu better.

Mark tends to comment on "celebrity bug reports" of this sort in any case, but I wasn't arguing that you aren't.

[QUOTE=kansasnoob]Well ,we still could in Hardy, maybe Intrepid, I don't quite remember when it changed but it certainly has been gone for quite a while!

So there have been times that we truly have gone down that slippery slope and no one paid attention![/QUOTE]

And what was your alternative to removing gnome-network-admin back then? Keeping a configuration tool that's redundant with Network Manager, letting people easily screw up their networking?

At the time, a graphical option to change the computer name wasn't absolutely needed, since it could be done at install time, so "There will be no way left to name a computer with a graphical interface" wasn't a strong argument against the removal of gnome-network-admin. It's now that the new installer doesn't present such a way that the need arises.

[quote=kansasnoob]Must I now never share an opinion again?[/QUOTE]

You're welcome to, but note that that's not the main purpose of this forum, and mixing unsubstantiated opinion with assistance / advice does not really contribute to the quality of discourse.

---

### Post by ranch hand on 2010-09-10
Well, we learn new things all the time.

I thought this was the  [Maverick Meerkat Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=385") forum.

My mistake.

---

### Post by 23meg on 2010-09-10
> **ranch hand said:**
> Well, we learn new things all the time.

I thought this was the  [Maverick Meerkat Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=385") forum.

My mistake.

Right; it's not [Community Cafe]("http://ubuntuforums.org/forumdisplay.php?f=11"), or [Recurring Discussions]("http://ubuntuforums.org/forumdisplay.php?f=302").

---

### Post by zekopeko on 2010-09-10
Wouldn't it be simpler to add an icon in the toolbar for UbuntuOne related features? They seriously need a better way to display U1 folder features then the ribbon provides.

---

