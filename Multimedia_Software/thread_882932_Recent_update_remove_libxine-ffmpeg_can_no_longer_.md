---
title: "Recent update remove libxine-ffmpeg can no longer play mp3s in amarok"
date: 2008-08-07
forum: Multimedia Software
---

### Post by pormogo on 2008-08-07
So I did a dist-upgrade yesterday and noticed that libxine had a whole bunch of package updates. I went ahead and did them all, however it also appears that those package updates removed libxine-ffmpeg. When I try to install it after making the upgrade I get the following error.

[i]apt-get -y install libxine1-ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxine1-ffmpeg: Depends: libxine1-bin (= 1.1.11.1-1ubuntu3) but 1.1.11.1-1ubuntu3.1 is to be installed
E: Broken packages
[/i]

:confused: What's the deal? I've tried setting --force-yes and that doesn't even seem to want to install the package. I noticed this didn't happen on my kubuntu desktop machine. It can install libxine1-ffmpeg without issue. Just my laptop is having the problem. Right now I'm using a gstreamer based mp3 player (exaile) and it sucks. Any help on this would be most appreciated.

The only difference in the 2 machines is that my laptop has the mediubuntu repository added and the desktop does not. I tried removing the conf file for mediubuntu from /etc/apt/sources.list.d and then updating again but that didn't seem to make any difference...

---

### Post by pormogo on 2008-08-07
Looks like there was an update to libxine1 in hardy-security that broke dependencies with libxine1-ffmpeg in normal hardy. Ahh the difference a .1 makes. I reverted back to the old package version until hardy-securty gets a version of libxine1-ffmpeg up.

---

### Post by larpon on 2008-08-08
> **pormogo said:**
> Looks like there was an update to libxine1 in hardy-security that broke dependencies with libxine1-ffmpeg in normal hardy. Ahh the difference a .1 makes. I reverted back to the old package version until hardy-securty gets a version of libxine1-ffmpeg up.

hehe.. with what commands/actions did you revert it?
I got the same problem :)

---

### Post by usaar33 on 2008-08-12
Is this going to be fixed anytime soon?  It is clearly a major problem.

---

### Post by 3p1ph4ny on 2008-08-13
Well, I just downloaded the older build's packages from launchpad and installed them all (thus reverting me to the older version until a new libxine1-ffmpeg package hits hardy security), as was suggested above.

This may or may not be the right way to do it, but it certianly works.

Here's the a link to launchpad:

[https://launchpad.net/ubuntu/hardy/+source/xine-lib/1.1.11.1-1ubuntu3](https://launchpad.net/ubuntu/hardy/+source/xine-lib/1.1.11.1-1ubuntu3)

On the right under "Builds", click on your architecture (for me, amd64). Then, under "Resulting Binaries" download each of the packages and do:

```
sudo dpkg -i PACKAGE_NAME.deb
```

dpkg should warn you about the fact that you're downgrading, but it should install the packages.

After that, do

```
sudo apt-get install libxine1-ffmpeg
```

and you should be able to play MPEG stuff again.

---

### Post by chezzo on 2008-08-16
I don't see why more people aren't complaining about this! It urgently needs to be fixed!

---

### Post by Fafnir on 2008-08-17
I had exactly the same problem yesterday and managed to figure out a solution on my own. It's a whole mess of issues working together. Basically, the new version of amarok no longer supports gstreamer (the default multimedia framework) - it uses xine instead. That means you need the xine plugin for mp3 playback, namely libxine1-ffmpeg. Installing it from within AmaroK doesn't work because AmaroK is actually a KDE application, so it tries to use the KDE package manager rather than apt-get.

As for why you can't install it using Synaptic, you've got the newest version of xine installed and you're trying to install an outdated version of the mp3 plugin on top, which Synaptic doesn't like for obvious reasons. The reason you don't have access to the newest version of the mp3 plugin is that your security repositories have been disabled and the latest update to certain xine plugins is classified as a security update.

Why your security repositories are disabled I have no idea - I think it might be an artifact of the upgrade process as I'm pretty sure mine were enabled before I upgraded... :confused:

The upshot is that you don't need to downgrade xine or anything like that - you can fix it by doing the following:

1. Open Synaptic and go to Settings -> Repositories -> Updates.
2. "Important security updates (hardy-security)" will have a horizontal line through its checkbox rather than being checked or unchecked - check it.
3. Hit Close, then hit the Reload button near the menu bar.
4. Install the libxine1-ffmpeg package as normal.
5. Restart AmaroK.

---

### Post by chezzo on 2008-08-17
woah you're right! thank you!
(it's not just a problem with amarok though, i was using totem-xine)
what does the horizontal line mean? i'd seen it before and thought it was a "check" as both of the top two boxes had it, and the bottom two were blank
i've no idea how it could have got that way, but after actually checking the boxes i discovered about 10 updates that were previously not available to me, along with all the xine ones

---

### Post by nemarona on 2008-08-24
Guys, you rock! This is why I like Ubuntu/Linux so much! :)
Fafnir is absolutely right about the security repositories not being enabled for some reason. Re-enabling them (and installing libxine1-ffmpeg, which is not included in kubuntu-restricted-extras) solved the problem.
Thanks!

---

### Post by ShadowWraith on 2008-08-26
Thank you so much, this problem has been plaguing me for days! The repository managers should really resolve it though, it's a pretty huge slip. However, Fanfir's post didn't really help, since I have the security repositories enabled, and still could not install libxine1-ffmpeg. So I just googled it and found the new one in launchpad. You don't have to go through installing all those old files, even if Fafnir's way doesnt work. Just get:
[https://launchpad.net/ubuntu/hardy/+package/libxine1-ffmpeg](https://launchpad.net/ubuntu/hardy/+package/libxine1-ffmpeg)
Select your architecture, install using dpkg, and you've got it.

---

### Post by jsundqui on 2008-09-07
I had same problem.  Just did the 7.10 > 8.04 upgrade finally (had to before 8.10 came out!).

ShadowWraith's solution worked great.

---

### Post by pormogo on 2008-10-16
After tons of time simply doing apt-get upgrade in order to update my system I took a look at the suggestion in this thread found that it was correct and fixed it. I don't know why the hell this was happening though!?

I checked and I had the security repositories added in my sources.list file

[i]## Security Repository
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted[/i]

I think that flipping the switch in synaptic changed something in /var/lib/apt/lists because I got this error when doing and apt-get update earlier.

[i]W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
[/i]

Pretty lame bug considering the true root cause of the issue is that my security and updates repositories have been silently disabled for the entire length of the 8.04 release :(

Either way many many thanks for the fix. To bad it took me so long to check back on this =P

---

