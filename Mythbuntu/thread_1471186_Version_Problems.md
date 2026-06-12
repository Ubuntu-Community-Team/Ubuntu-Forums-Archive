---
title: "Version Problems"
date: 2010-05-03
forum: Mythbuntu
---

### Post by Tteddo on 2010-05-03
I just upgraded my office machine to 10.04 and the MythTV version installed is .23. It won't access the machine in my living room that is Mythbuntu 8.04 and I think MythTV .19 because it is too old. I am planning to upgrade the older one this summer after I get a digital Hauppage card and better equipment. 
My question is as follows: Is there a way to force an upgrade of just MythTV to .23 on the old machine (preferable) or a way to force a downgrade of the office machine so it will play nice with the other machine?
I couldn't think of a way to search for that question in the forums.

---

### Post by tgm4883 on 2010-05-03
Unfortunatly not. The highest version supported on 8.04 is Mythtv 0.21, the lowest on 10.04 is 0.23. You could try to download the 8.04 packages for 8.04 and install them on the 10.04 machine

---

### Post by dannyboy79 on 2010-05-03
it wouldn't take much to upgrade 8.04 to 10.04, just keep doing 
sudo apt-get update
sudo update-manager -d

and upgrade your ubuntu versions all the way up to 10.04. i would say you'd have a library and dependency mess if you tried to do it any other way.

easiest would be to run a live cd of mythbuntu 10.04 saving changes to a memory stick

---

### Post by tgm4883 on 2010-05-03
> **dannyboy79 said:**
> it wouldn't take much to upgrade 8.04 to 10.04, just keep doing 
sudo apt-get update
sudo update-manager -d

and upgrade your ubuntu versions all the way up to 10.04. i would say you'd have a library and dependency mess if you tried to do it any other way.

easiest would be to run a live cd of mythbuntu 10.04 saving changes to a memory stick

Please stop telling people to use update-manager -d if you don't know what it does.

To help you out
```
thomas@earth:~$ update-manager --help
Usage: update-manager [options]

Options:
  -h, --help            show this help message and exit
  -V, --version         Show version and exit
  --data-dir=DATA_DIR   Directory that contains the data files
  -c, --check-dist-upgrades
                        Check if a new Ubuntu release is available
  -d, --devel-release   Check if upgrading to the latest devel release is
                        possible
  -p, --proposed        Upgrade using the latest proposed version of the
                        release upgrader
  --no-focus-on-map     Do not focus on map when starting
  --dist-upgrade        Try to run a dist-upgrade
  -s, --sandbox         Test upgrade with a sandbox aufs overlay
thomas@earth:~$ 

```

-d is to upgrade to the development release

-c is to check for a new regular release

---

### Post by klc5555 on 2010-05-03
> **Tteddo said:**
> I just upgraded my office machine to 10.04 and the MythTV version installed is .23. It won't access the machine in my living room that is Mythbuntu 8.04 and I think MythTV .19 because it it too old. I am planning to upgrade the older one this summer after I get a digital Hauppage card and better equipment. 
My question is as follows: Is there a way to force an upgrade of just MythTV to .23 on the old machine (preferable) or a way to force a downgrade of the office machine so it will play nice with the other machine?
I couldn't think of a way to search for that question in the forums.

Was the 8.04 Mythtv installation a mostly default Mythbuntu 8.04 installation? If so, it should have Mythtv 0.21 on it rather than 0.19. 

Now if this is the case, it is known that the Mythtv 0.21 packages from the more recent 9.04 (plus a few dependencies)would run on 9.10 (which was by default 0.22) It is possible they will still run on 10.04. Nobody's tried it.

You would need to download the 9.04 mythtv-common, mythtv-backend, and mythtv-frontend (0.21)packages (for starters) from packages.ubuntu.com You would need to uninstall all the mythtv packages on your 10.04 office machine. You'd then need to use gdebi (or similar) to install the above packages (going back to packages.ubuntu.com for whatever dependency packages the above three might want to drag along with them, according to gdebi)

If the packages install on your office machine, run mythtv-setup and see whether you can configure it without it blowing up. If it's OK, then you may be set until such time as you're ready to upgrade the 8.04 machine over the summer. If not, then not.

If the older mythtv packages work, you'll need to lock them in Synaptic, so that the machine doesn't try to upgrade them to current every few hours.

---

### Post by Tteddo on 2010-05-03
> **dannyboy79 said:**
> it wouldn't take much to upgrade 8.04 to 10.04, just keep doing 
sudo apt-get update
sudo update-manager -d

and upgrade your ubuntu versions all the way up to 10.04. i would say you'd have a library and dependency mess if you tried to do it any other way.

easiest would be to run a live cd of mythbuntu 10.04 saving changes to a memory stick

This is my 2nd install of MythBuntu in the living room, and both times I had major problems running the updates like I do on my other Ubuntu machines, so I leave it as is because it works. Maybe it's different now. I am planning on a full upgrade this summer including trying to save the database.

---

### Post by Tteddo on 2010-05-03
> **klc5555 said:**
> Was the 8.04 Mythtv installation a mostly default Mythbuntu 8.04 installation? If so, it should have Mythtv 0.21 on it rather than 0.19. 

Now if this is the case, it is known that the Mythtv 0.21 packages from the more recent 9.04 (plus a few dependencies)would run on 9.10 (which was by default 0.22) It is possible they will still run on 10.04. Nobody's tried it.

You would need to download the 9.04 mythtv-common, mythtv-backend, and mythtv-frontend (0.21)packages (for starters) from packages.ubuntu.com You would need to uninstall all the mythtv packages on your 10.04 office machine. You'd then need to use gdebi (or similar) to install the above packages (going back to packages.ubuntu.com for whatever dependency packages the above three might want to drag along with them, according to gdebi)

If the packages install on your office machine, run mythtv-setup and see whether you can configure it without it blowing up. If it's OK, then you may be set until such time as you're ready to upgrade the 8.04 machine over the summer. If not, then not.

If the older mythtv packages work, you'll need to lock them in Synaptic, so that the machine doesn't try to upgrade them to current every few hours.

You are correct, it is .21. I think I'll try downgrading the office machine like you say. I don't want to risk breaking the living room machine before the recording season is over.

---

### Post by Tteddo on 2010-05-03
I don't believe it, it worked! Thanks klc5555! It even picked up all my settings from my old home folder. All I needed was mythtv-common and mythtv-frontend (and the dependencies- there were 3) since the backend is on the other machine.
Here's betting that it takes me 2 hours to remember to unlock those in Synaptic this summer. ;)

---

### Post by klc5555 on 2010-05-03
And thank you for being the world's first test subject for Myth 0.21 on Ubuntu 10.04! 

Your success eases a worry of my own, as I have a couple of 9.04 machines that I'd like to upgrade to the hardware/driver/app support of Ubuntu 10.04, but I don't find Mythtv 0.22 itself (to say nothing of 0.23) to be a particularly compelling upgrade. Especially for my non-Ubuntu machines that all happily run 0.21.

---

### Post by Tteddo on 2010-05-04
I know what you mean. That machine is only an Athlon 3200+ and it won't quite do HD content so loading it up with something new was not something I was looking to do.
It's funny, it actually works better across my network now with the audio and video sync than with my old machine which was no slacker itself.
Thanks again!

---

### Post by tgm4883 on 2010-05-04
> **Tteddo said:**
> I know what you mean. That machine is only an Athlon 3200+ and it won't quite do HD content so loading it up with something new was not something I was looking to do.
It's funny, it actually works better across my network now with the audio and video sync than with my old machine which was no slacker itself.
Thanks again!

I don't see why a Athlon 3200+ won't do HD

---

### Post by Tteddo on 2010-05-04
Might be the video card (Radeon 9550). It's was a great ATI card at the time. It just stutters a lot even with HD content right from the hard drive. Won't play the HULU desktop either but I think that's more of a flash thing. I don't really have any HD sources really so it wasn't much of an issue.

---

### Post by gdbutcher on 2010-06-05
I can't thank you enough klc5555 for you advice on installing MythTV 0.21 on Ubuntu 10.04 x64. :D 

Here are the steps that I took just in case anyone else wants to install Myth 0.21 on Ubuntu 10.04 x64. It may seem a little long winded but believe me this was nothing compared to the number of hours that I have spent trying to get MythTV 0.22 and 0.23 to stay working!  

**Step 1.** Go to [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") and use the 'Search package directories' to download and install the following packages:

[LIST]
[*]libfaad0_2.6.1-3.1_amd64.deb
[*]libmyth-0.21-0_0.21.0+fixes19961-0ubuntu8_amd64.deb
[*]libmyth-perl_0.21.0+fixes19961-0ubuntu8_all.deb
[*]libraw1394-8_1.3.0-4ubuntu1_amd64.deb
[*]mythplugins_0.21.0+fixes19556-0ubuntu8_all.deb
[*]mythtv_0.21.0+fixes19961-0ubuntu8_all.deb
[*]mythtv-backend_0.21.0+fixes19961-0ubuntu8_amd64.deb
[*]mythtv-common_0.21.0+fixes19961-0ubuntu8_all.deb
[*]mythtv-database_0.21.0+fixes19961-0ubuntu8_all.deb
[*]mythtv-frontend_0.21.0+fixes19961-0ubuntu8_amd64.deb
[*]mythtv-transcode-utils_0.21.0+fixes19961-0ubuntu8_amd64.deb
[/LIST]

Unfortunately I cannot remember which order I installed the packages in, but your package installer will tell you what exactly which packages are needed before the current one can be installed.

**Step 2.** 

I ran into some problems with my mythconverg database. So basically I deleted it and started over. To delete mythconverg run the following command in the terminal (Applications Menu >Acessories > Terminal):-

```

mysql -u root -p
drop database mythconverg;
exit;

```
 
**Step 3.**

Follow the Post Install Tasks on this page: [http://www.mythtv.org/wiki/User_Manual:Initial_Installation#Creating_the_mythtv_user]("http://www.mythtv.org/wiki/User_Manual:Initial_Installation#Creating_the_mythtv_user")

Remember to change you passwords as appropriate.

**Step 4 - Final Step** 

Go to System Menu > Administration > Synaptic Package Manager

Use the Quick Search and type in "Myth"
Press and hold the Ctrl key and select the following packages:

[LIST]
[*]mythtv-frontend
[*]mythtv-backend
[*]mythtv-database
[*]mythtv
[*]mythtv-common
[*]myth-plugins
[*]mythtv-transcode-utils 
[*]libmyth-perl
[/LIST]

Go to Package menu and click on 'Lock Version'. This prevents Mythtv 0.21 being upgraded to 0.23.

Thats it. Hope it works as well for you as it has for me.

---

### Post by kcox5342 on 2010-07-13
I recently upgraded both my laptops to 10.04, but the mythtv-backend is still 8.04 and 0.21.  I actually tried a test install of .23 on a separate HD, but my main reason for staying with 0.21 right now is that the Mac (PowerPC) Myth frontend for 0.23 wouldn't play transcoded videos, and that's the only way I can watch 1080i content on the older Mac.  So I'm back at 0.21, and trying to figure out how to run it on 10.04.

The guide is very helpful, although I do have one question about the packages listed - if all I'm running is a remote frontend, which packages do I need?  

But my main problem is something the netbook, under 10.04, does for both 0.21 and 0.23 versions of the frontend - namely, not start at all.  If I run it in a terminal, all I get is:

```

2010-07-13 05:46:28.486 Using runtime prefix = /usr
2010-07-13 05:46:29.300 XScreenSaver support enabled
2010-07-13 05:46:29.301 DPMS is active.
2010-07-13 05:46:29.304 Empty LocalHostName.
2010-07-13 05:46:29.304 Using localhost value of mini
2010-07-13 05:46:29.331 New DB connection, total: 1

```

And then it just sits there patiently waiting for me to force-quit it.  I'm running Ubuntu 10.04 netbook edition.

---

### Post by Tteddo on 2010-07-13
> **kcox5342 said:**
> I recently upgraded both my laptops to 10.04, but the mythtv-backend is still 8.04 and 0.21.  I actually tried a test install of .23 on a separate HD, but my main reason for staying with 0.21 right now is that the Mac (PowerPC) Myth frontend for 0.23 wouldn't play transcoded videos, and that's the only way I can watch 1080i content on the older Mac.  So I'm back at 0.21, and trying to figure out how to run it on 10.04.

The guide is very helpful, although I do have one question about the packages listed - if all I'm running is a remote frontend, which packages do I need?  

But my main problem is something the netbook, under 10.04, does for both 0.21 and 0.23 versions of the frontend - namely, not start at all.  If I run it in a terminal, all I get is:

```

2010-07-13 05:46:28.486 Using runtime prefix = /usr
2010-07-13 05:46:29.300 XScreenSaver support enabled
2010-07-13 05:46:29.301 DPMS is active.
2010-07-13 05:46:29.304 Empty LocalHostName.
2010-07-13 05:46:29.304 Using localhost value of mini
2010-07-13 05:46:29.331 New DB connection, total: 1

```

And then it just sits there patiently waiting for me to force-quit it.  I'm running Ubuntu 10.04 netbook edition.

The next step in mine is:> 2010-07-13 10:37:59.985 Connected to database 'mythconverg' at host: 192.168.0.146

So I imagine you might have something wrong with the username/password connecting to the remote backend.

---

### Post by madrivereric on 2010-08-29
Thank You!  I need to do exactly the same thing, but for slightly different reasons:  I'm upgrading my machine from 8.10 to 10.04 and rudely found out Myth dropped support for my PVR-350's TV out...  Since we are watching recorded programs on our analog tv via the PVR-350's TV out this was a show stopper.  I'll give it a try during the next gap in recordings.

---

### Post by dannyboy79 on 2010-08-31
> **madrivereric said:**
> rudely found out Myth dropped support for my PVR-350's TV out...  Since we are watching recorded programs on our analog tv via the PVR-350's TV out this was a show stopper. 
statements like this aren't appreciated by the devs I can imagine. you want the support in there in a more recent version, put it in yourself. if you're just an end user then beggers can't be choosers. pvr-350 tv out was never really polished anyway, and with the focus of mythtv on HD primarily, it does the dev's no good to keep analog output on an old tuner card supported. just saying.......

---

### Post by Tteddo on 2010-08-31
> **dannyboy79 said:**
> statements like this aren't appreciated by the devs I can imagine. you want the support in there in a more recent version, put it in yourself. if you're just an end user then beggers can't be choosers. pvr-350 tv out was never really polished anyway, and with the focus of mythtv on HD primarily, it does the dev's no good to keep analog output on an old tuner card supported. just saying.......

While I agree with your point, I am curious. Why do they remove support for things? I mean once the code is in there and already written why not just leave it?

---

### Post by Tteddo on 2010-08-31
> **madrivereric said:**
> Thank You!  I need to do exactly the same thing, but for slightly different reasons:  I'm upgrading my machine from 8.10 to 10.04 and rudely found out Myth dropped support for my PVR-350's TV out...  Since we are watching recorded programs on our analog tv via the PVR-350's TV out this was a show stopper.  I'll give it a try during the next gap in recordings.

FYI- My original setup in 2004 had what's called a converter to go from VGA to S-Video/cable/composite to the TV. I believe you can still get those.

---

### Post by dannyboy79 on 2010-08-31
they drop support because of new code for the newer mythtv functional versions, sometimes they can't just update code but have to rewrite it to be better, which would then result in having to update the old code for the pvr-350 tv-out to work with the new code, as hardware gets older and has less chance for end user use, they drop the code out. that's my quess anyway.

weird, it says here: ([http://www.mythtv.org/wiki/Hauppauge_PVR-350](http://www.mythtv.org/wiki/Hauppauge_PVR-350))
With MythTV 0.23 and later, the ivtv Xorg/Xv driver is required for TV output using this card.

---

### Post by Tteddo on 2010-08-31
> **dannyboy79 said:**
> they drop support because of new code for the newer mythtv functional versions, sometimes they can't just update code but have to rewrite it to be better, which would then result in having to update the old code for the pvr-350 tv-out to work with the new code, as hardware gets older and has less chance for end user use, they drop the code out. that's my quess anyway.

Ahh, that makes sense. Thanks!

---

