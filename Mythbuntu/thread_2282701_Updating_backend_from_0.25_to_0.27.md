---
title: "Updating backend from 0.25 to 0.27"
date: 2015-06-16
forum: Mythbuntu
---

### Post by el_Paraguayo on 2015-06-16
I have also posted this on the MythTV and MythTVTalk forums but those seem to be less active than this one. Depending on where an answer is posted I will update the other posts accordingly.
--------------------------------------------------------------------------------


My setup is running Mythbuntu 12.04 using XBMC as a frontend.

I need to update to Kodi but I think the myth protocol functionality has been removed from Kodi in favour of using the PVR addons. This means I need to upgrade mythtv to at least 0.27.

Given that I don't use the frontend, am I correct in thinking I can just upgrade the mythtv-backend package or are there other packages that need to be upgraded to?

I currently have 0.25 installed (see below).

```
elParaguayo@HTPC:~$ apt-cache policy mythtv-backend
mythtv-backend:
  Installed: 2:0.25.2+fixes.20120802.46cab93-0ubuntu1
  Candidate: 2:0.25.2+fixes.20120802.46cab93-0ubuntu1
  Version table:
 *** 2:0.25.2+fixes.20120802.46cab93-0ubuntu1 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/multiverse i386 Packages
        100 /var/lib/dpkg/status
     2:0.25.0+fixes.20120410.1f5962a-0ubuntu1 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/multiverse i386 Packages

```My plan was to just add the 0.27 repository and upgrade the single package (rather than do a full dist-upgrade as I've no idea what else that will do!). I'll back up the database before the upgrade.

---

### Post by aelfric55 on 2015-06-16
Before you get to the business of upgrading mythtv versions, while you still have a working 0.25 setup, add support for the new mysql time zone tables that went into use in 0.26 and above. [https://www.mythtv.org/wiki/MySQL_Time_Zone_Tables](https://www.mythtv.org/wiki/MySQL_Time_Zone_Tables) 

The presence of the new tables doesn't affect 0.25 at all, but a freshly upgraded 0.26+ (0.27) master backend won't start without the tables having been upgraded.

The first time the freshly upgraded-above-0.25  master backend is started manually, it will take a  _very_  long time to upgrade the database schema: 20 minutes to over an hour in my experience. If you're not expecting it you might think the process had hung at some point. But it's just really slow.

For my own use, I've found the Kodi (and before this XBMC's) native PVR support to be so buggy as to be absolutely worthless for mythtv. For example, my mythconverg usually runs about 2400 recordings at any given time, and uncompressed comsumes about 1.4 Gb. In startup, Kodi PVR support almost always hangs or crashes about 2/3 of the way through trying to load the DB, after working at it for 3-5 minutes or so. Useless. 

What does work for me is to make sure my master mythtv backend is compiled with UPnP support enabled, and then add the mythtv UPnP server as a UPnP video source in Videos. This allows me to find and watch all prerecorded content from my mythtv backends --the only disadvantages are that there is no mythfrontend functionality for scheduling new recordings, and recordings-in-progress can't be watched in their entirety until after they've completed recording.

---

### Post by el_Paraguayo on 2015-06-16
Thanks that's very helpful advice. 

I assume that my suggested approach of just updating mythth-backend (after adding timezone tables) is the right way to go?

It's a shame to hear about your experiences with the Kodi PVR addon. I might try it once to see how painful it is but thanks for managing my expectations!

UPnP may well be the way to go as you suggest. I'm not concerned about scheduling recordings (done via MythWeb) and watching in-progress recordings (never used that feature).

---

### Post by aelfric55 on 2015-06-16
I'm not sure whether mythtv 0.27.x is supported prior to Ubuntu 14.04. Someone else will need to answer that.  

Also Ubuntu should (I believe) add the tables automatically as part of the package upgrade process, but the table upgrade process was so simple to do that I did it some months before I actually got around to upgrading mythtv from 0.25.

Maybe try Kodi as a UPnP viewer with your current 0.25 setup if your mythtv 0.25 is UPnP functional? Assuming it works as it should, no need to upgrade the mythtv/mythbuntu end of your setup at all for the present.

---

### Post by el_Paraguayo on 2015-06-16
Ah. I don't really fancy upgrading to 14.04 (but I could if necessary)! Hopefully it works on 12.04!

---

### Post by aelfric55 on 2015-06-16
I was editing above while you were replying (!) But try Kodi as UPnP viewer with your current Myth 0.25 setup. If it works as it should, no need to further upgrade anything for the moment.

---

### Post by el_Paraguayo on 2015-06-16
Well MythTV 0.25 is working fine with XBMC. What's not working is the Youtube plugin which makes my son sad! The easiest fix is to upgrade to Kodi and use the latest youtube addon as, I think, the development on the old one has stopped.

What I'm trying to work out is which packages I need to update without running a dist-upgrade command (that always makes me uncomfortable). I can't tell if it's just mythtv-backend or also mythtv-database.

---

### Post by aelfric55 on 2015-06-16
Just upgrade Kodi. Then you can install your new Kodi youtube addon. Try using Kodi as a UPnP player for your current mythtv 0.25 setup. You do not have to go through the old routine of enabling myth protocol, the way things used to be done back in the XBMC Eden 11.0 days. Just add source and browse for UPnP under types of sources. Mythtv has been UPnP server capable since 0.20. It's just a question of whether it's enabled in your setup.

But regarding the package issue, I suspect that if the packages actually exist for 12.04, then an upgraded mythtv-backend plus mythtv-common (and mythweb in your case) would be sufficient ...plus all the dependencies they drag along.  mythtv-database is not a dependency of mythtv-backend.

---

### Post by el_Paraguayo on 2015-06-16
Ha ha. I'm now feeling a little bit stupid! 

You're completely right, if the UPnP works then there's no need to upgrade MythTV at all.

Thanks for all your help. Really appreciate it.

---

### Post by el_Paraguayo on 2015-06-16
Ok. so this is weird...

Installed Kodi on my laptop and can't see MythTV on UPnP (it finds other UPnP servers, just not MythTV). Installed VLC and it can see the UPnP server. My HTPC (running XBMC) can see the UPnP server...

Not inclined to upgrade my HTPC to Kodi until I can figure this out.

---

### Post by tgm4883 on 2015-06-16
The graphic here will always show what versions of MythTV are available for what versions of Ubuntu [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)

You would need to upgrade all of the mythtv related packages. Easiest way to see what mythtv packages are installed is to do

```

dpkg -l | grep myth

```

---

### Post by Lester_Burnham on 2015-06-16
Hi,
Just posting a couple of things to watch out for when jumping from 0.25 to 0.27

I think it's best to jump to 0.26 first for the change from mysql.txt to config.xml and database tables as mentioned earlier. I spent ages looking for the problem of why database upgrades wouldn't take, but I think it was the two issues combining causing the problem.

Make sure you have a working config.xml in your ~/.mythtv/ directory.

Lester

---

### Post by el_Paraguayo on 2015-06-17
Thank you very much. That's really useful info (especially the dpkg bit - wouldn't have got that myself!).

---

### Post by aelfric55 on 2015-06-17
Perhaps try shutting down all other UPnP servers on your network for a bit and see if Kodi finds the Mythtv UPnP then. There's some documentation out there about Myth UPnP servers and XBMC/Kodi UPnP servers in particular interfering with one another on a network (e.g. here: [http://blog.andrewmarconi.com/2014/10/mythtv-upnp-conflicts-xbmc/](http://blog.andrewmarconi.com/2014/10/mythtv-upnp-conflicts-xbmc/) )

---

### Post by el_Paraguayo on 2015-06-18
Thanks. Will take a look. I'm sure you're right, just upgrading to Kodi must be the best solution for me.

---

### Post by aelfric55 on 2015-06-18
Since you already have Kodi installed on your laptop, you may wish to confirm that it can't, in fact, connect to your 0.25 master backend the old-fashioned way, by specifying myth protocol. Assuming that the master backend is network connectable and not on localhost. Kodi still has myth protocol listed as a specified option in the "other" menu for connecting video file sources. I tried it last night on my setup and failed, but that only proves it doesn't connect with the current myth protocol in 0.27. It may be that connecting with 0.25 is still possible.

---

### Post by el_Paraguayo on 2015-06-18
Yes. Got it working on Kodi on the laptop. Myth protocol needed to include the port number in the address and seems to work. What a relief!

---

### Post by el_Paraguayo on 2015-07-26
Sadly, Isengard has removed the MythTV protocol support "[COLOR=#000000][FONT=sans-serif]in favour of its external PVR Client Addons"... 

That's probably going to mean that I have to upgrade now.[/FONT][/COLOR]

---

### Post by Lester_Burnham on 2015-07-27
> **el_Paraguayo said:**
> Sadly, Isengard has removed the MythTV protocol support "[COLOR=#000000][FONT=sans-serif]in favour of its external PVR Client Addons"... 

That's probably going to mean that I have to upgrade now.[/FONT][/COLOR]

Hi,

Probably so, because you can't install Kodi Isengard on 12.04 from the PPA.
If you're already up to mythtv 0.27 on 12.04, it shouldn't be to much of a problem going up to 14.04.2 via a dist upgrade.

I did pretty much the above yesterday, because of Isengard, but I haven't tested the PVR ad don yet.

Lester

Edit: I just installed the mythtv PVR add-on and it's working fine. Nice and snappy too.

---

### Post by aelfric55 on 2015-07-29
> **el_Paraguayo said:**
> Sadly, Isengard has removed the MythTV protocol support "[COLOR=#000000][FONT=sans-serif]in favour of its external PVR Client Addons"... 

That's probably going to mean that I have to upgrade now.[/FONT][/COLOR]

If you need Isengard, and it can't be directly installed from binaries on 12.4 (and you don't want to compile your own), then it probably really is time to upgrade everything. At least the mythtv 0.25-0.27 portion of the upgrade should be smooth, allowing for the exceptional amount of time consumed in the schema upgrade the first time the new mythbackend runs with UTC support added. And 0.27 is quite a bit better than 0.25 was, except for fairly unreliable liveTV support, a feature you don't use anyway. 

Depending on how you feel about the myth frontend addon in Isengard after you try it, you can always try running Mythfrontend itself and run Kodi as a menu item in it for your other video needs, rather than doing your mythtv from inside Kodi. Or debug your Kodi machine's UPnP issue with mythbackend's UPnP server.

---

