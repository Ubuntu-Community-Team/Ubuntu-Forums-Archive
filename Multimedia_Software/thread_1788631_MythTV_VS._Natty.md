---
title: "MythTV VS. Natty"
date: 2011-06-22
forum: Multimedia Software
---

### Post by ModernDayCaesar on 2011-06-22
Hello All,

   I am new to Linux. I started with the 11.04 Natty. Heard good things about MythTV so decided to try it out. Installed with no issues.. when trying to watch live TV and playback recorded media, I have absolutely no sound.

After quite a bit of research, I've received some mixed information. First I hear that the default kernel (2.6.38) doesn't support V4L so I upgraded to 2.6.39 and still have the same issue.

Then I've heard that I need to compile MythTV with V4L support which I'm completely clueless on even after google'ing for hours.

I'm kinda hoping someone could just give me a straight forward answer on how to get MythTV running on my machine because it's kind of a deal breaker for me with Natty. I really didn't want to but I will install Meerkat or MythBuntu if I have to.

Thanks

---

### Post by BicyclerBoy on 2011-06-22
The newer kernel would have v4l2 & I believe v4l(1) as well.

You can force the v4l(1) compatibility mode if required for some applications.

Why do you need a specific v4l version with MythTV ?

The audio problem would have nothing to do with v4l-dvb module unless you are using some analogue recording card with external set top box.

The first thing you do with new install/upgrade of MythTV, after running backend settings, is rescan the audio devices in the frontend.

---

### Post by ModernDayCaesar on 2011-06-22
After the research I've done.. I've gained that MythTV is still dependent on V4L(1) and that the newer kernels have dropped V4L(1) and have moved on to V4L(2).

Sorry I didn't explain more in the original post. I'm trying to use MythTV in conjunction with my Cable Box and a HD-PVR. I've tried multiple settings and they all end up producing no sound but I can see video with no issue.

This is the error I receive within MythTV:

ERROR, Compile with V4L support to query audio inputs

---

### Post by BicyclerBoy on 2011-06-22
The v4l 1 vs 2 changes in MythTV date back to 2005.

I found what you are on about....
[FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]You are running the 2.6.38 kernel.  The 2.6.38 kernel removed the V4L1  
ioctls, and more importantly the V4L1 headers which **MythTV** used to fall  
back on with old tuners that had not yet been updated to the V4L2 interface.[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

If you build from 0.24+fixes it could be resolved, master 0.25 has been fixed.
[http://www.gossamer-threads.com/lists/mythtv/users/481095](http://www.gossamer-threads.com/lists/mythtv/users/481095)
[http://www.mythtv.org/pipermail/mythtv-users/2011-May/315606.html](http://www.mythtv.org/pipermail/mythtv-users/2011-May/315606.html)

You can always roll back your kernel & lock it for couple months..

Are you compiling from source (git) ?
If you do you need to configure the build options for ubuntu path & module options etc..

What version of MythTV ?

What model HD-PVR ?
I have to admit to never having used a capture card only dvb-t.

---

### Post by ModernDayCaesar on 2011-06-22
> Are you compiling from source (git) ?
If you are you need to configure the build options for ubuntu path & module options etc..

I'm sorry, I'm quite new to Linux so I'm not used to this type of terminology coming from a Win7 machine.

> What version of MythTV ?

I'm using the version that's in the Ubuntu Software Installer.

> Your HD-PVR streams mpeg2-ts to the filesystem basically..so the audio must be missing between your set-top-box & HD-PVR else the HD-PVR has some audio input capture options..

Is it these input capture options you are trying to control ?

I have no software for the HD-PVR on my Linux Distro besides the MythTV app. And there is no way to toggle and options on the hardware itself. I'm not quite sure which options I'm trying to control.. I just would like to hear some sound from it. I'll check through my cable box menu for any audio out options.

> What model HD-PVR ?

49001 LF Rev E1

---

### Post by BicyclerBoy on 2011-06-22
We cross posted...

I suggest rolling back the kernel..see previous post

What's a 49001...my age in hours..or the capture cards ?

Kalamazoo=49001

Are you using HDMI input ?
This not likely to ever work without HDCP..

---

### Post by ModernDayCaesar on 2011-06-22
From my understanding.. There is only 1 HD-PVR

[HD-PVR]("http://goo.gl/aTwE4")

I'm not using HDMI.. I'm using Composite RCA jacks.

> You are running the 2.6.38 kernel. The 2.6.38 kernel removed the V4L1 
ioctls, and more importantly the V4L1 headers which MythTV used to fall 
back on with old tuners that had not yet been updated to the V4L2 interface.

If you build from 0.24+fixes it could be resolved, master 0.25 has been fixed.
[http://www.gossamer-threads.com/list...v/users/481095](http://www.gossamer-threads.com/list...v/users/481095)
[http://www.mythtv.org/pipermail/myth...ay/315606.html](http://www.mythtv.org/pipermail/myth...ay/315606.html)

You can always roll back your kernel & lock it for couple months..

I'm currently running the 2.6.39 kernel because this issue tempted me to upgrade to see if it was fixed.

I did install a package with the fixes but still have the issue. But I did an overwrite and not a clean install of the program. Maybe I should try that.

Are there any types of issues that can come from rolling back a kernel previous to 2.6.38 because I would love to try that just don't wanna risk my stability.

Thanks

---

### Post by BicyclerBoy on 2011-06-23
It took me some time to find what a 49001 looks like..

Now I see it is just a analogue video capture with h264 encoder & streams mpeg2-ts container files.
I had thought it might have been the new HDMI capture card..

Just roll the kernel back in GRUB startup menu if you can.
But if you are running a fresh install there may not be any to choose from?
Grub maintains a list of all local kernel images & you can just pick from the list..

If you have no other kernel versions to choose then you can install via synaptic package manager the exact kernel version.

If you search  (synaptic package manager) for linux kernel you should find you have (2) linux kernel packages installed. One is a meta-package for the latest kernel & the other will be the real package.
You should install the version you want & un-install the meta-package to prevent upgrades.
Synaptic manager should sort it all out..
You can always re-install the kernel meta-package at any time.

There should not be any problems running any 2.6.xx kernel.
I have run natty kernels with 10.04 ..

The problem will likely be that kernel 2.6.27 will not be in the natty repos...
You may have to add the kernel ppa for lucid just to get a kernel.

Easier to just to give up on natty & install 10.04 or 10.10.
Get the latest MythTV from mythbuntu or some other ppa.

Note that old kernel will have HDMI audio problems unless you build the alsa kernel module..

---

### Post by ModernDayCaesar on 2011-06-23
Do you think I would have this same issue in MythBuntu 11.04 because I would choose to do that before going to 10.10. But If I would have the same issues in MythBuntu then I will just go straight to Meerkat or Lucid Lynx.

How do I add the PPA for Lucid Lynx because I wouldn't mind keeping my machine the way it is now and just swap the kernel out.

Don't let me lose you on this next one.

Are you saying that if I was utilizing hdmi on my current setup then I wouldn't be experiencing this issue and if I rollback the kernel to where the standard composites work, then the hdmi will have issues.

---

### Post by BicyclerBoy on 2011-06-23
I was just thinking about mythbuntu as a solution...
Because finding the kernel you need is not going to be easy & the solution lies in moving forwards...

If you were to add the mythbuntu nightly builds ppa you could get the latest 0.25 MythTV packages.
I am not sure if mythbuntu 11.04 will cut it..

The HDMI issue that I mentioned relates to HD audio over HDMI connected TVs & monitors.

You can utilize the mythbuntu packages for MythTV without the whole mythbuntu thing.
[http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)
[Install the Mythbuntu-repos package]("http://www.mythbuntu.org/repos#")
and read
[Common uses for Mythbuntu-repos]("http://www.mythbuntu.org/repos#")

sudo dpkg-reconfigure mythbuntu-repos
 
Mythbuntu tries to hide everything & uses some other tools to configure which repos you get i.e. release testing or bleeding

---

### Post by ModernDayCaesar on 2011-06-23
Fixed the repos and installed .25

seems as though everything including sound is now working. And I might add that ver .25 looks way better by default.

Anyways, big thanks BicyclerBoy.. I appreciate the quick response and sticking with me this long.

---

### Post by BicyclerBoy on 2011-06-23
No problem at all..
I should have thought of mythbuntu repos sooner but now you know all the grim details..
And I did not know about the v4l2 issues with analogue capture.

---

