---
title: "request clarification on patches vs auto builds"
date: 2010-06-19
forum: Mythbuntu
---

### Post by SMANN on 2010-06-19
I have the DVD/.iso playback issue.  Clean install of 10.04 on 2 separate boxes,  neither will play .iso's and neither will play a DVD inserted into the  drive, both will freeze up and report "video frame buffering failed too  many times...."

In another thread it is suggested to enable auto builds and users report this fixes the issue.

I was hoping someone could clarify something about bug fixes and auto  builds with Mythbuntu.  Is the only way to fix this particular problem  going to be updating to an entirely new upstream version of mythbuntu or  will a patch eventually be released for this?  

I may just be confused but the idea of auto builds suggest to me that I  might fix this issue but break something else with newer code, not be able to revert and then have people give me blank stares because I am using some non-release, intermediate version of myth.  My ideal scenario is to get the core functionality of 10.04 LTS all working and then leave it alone for a couple years save applying official critical updates w/ the update manager.

As optical disk handling is a default core component of Mythbuntu and seems to be entirely broken in the default install it seems there should be a patch released to address this single issue but I'm not sure how Mythbuntu handles these things.

Should I:

1. Wait for a patch for this single issue?
2. Activate auto builds then deactivate it once I get this issue fixed?  Any caveats to this?
3. Something else I haven't considered?

---

### Post by tgm4883 on 2010-06-19
> **SMANN said:**
> I have the DVD/.iso playback issue.  Clean install of 10.04 on 2 separate boxes,  neither will play .iso's and neither will play a DVD inserted into the  drive, both will freeze up and report "video frame buffering failed too  many times...."

In another thread it is suggested to enable auto builds and users report this fixes the issue.

I was hoping someone could clarify something about bug fixes and auto  builds with Mythbuntu.  Is the only way to fix this particular problem  going to be updating to an entirely new upstream version of mythbuntu or  will a patch eventually be released for this?  

I may just be confused but the idea of auto builds suggest to me that I  might fix this issue but break something else with newer code, not be able to revert and then have people give me blank stares because I am using some non-release, intermediate version of myth.  My ideal scenario is to get the core functionality of 10.04 LTS all working and then leave it alone for a couple years save applying official critical updates w/ the update manager.

As optical disk handling is a default core component of Mythbuntu and seems to be entirely broken in the default install it seems there should be a patch released to address this single issue but I'm not sure how Mythbuntu handles these things.

Should I:

1. Wait for a patch for this single issue?
2. Activate auto builds then deactivate it once I get this issue fixed?  Any caveats to this?
3. Something else I haven't considered?

Upgrade to auto-builds. Select the version of MythTV that you are on. What gave you the idea that

> the idea of auto builds suggest to me that I  might fix this issue but break something else with newer code, not be able to revert and then have people give me blank stares because I am using some non-release, intermediate version of myth.

---

### Post by SMANN on 2010-06-20
> **tgm4883 said:**
>  What gave you the idea that

Well, a couple of things:

1. That the updates for Myth, presumably the central reason for installing Mythbuntu, are not enabled by default.  You have to locate the auto-build page, download and install the deb, etc.  There is also nothing w/in Mythbuntu Control Center that leads one down the path of applying updates for Myth I'd guess there is a reason for this but I'm not sure what it is.  It kind of suggests that auto-builds are an advanced user, proceed w/ caution thing.

2. That they are automatic daily builds.  From a user's perspective all I see is a given number of updates available in the update manager and none of them have any documentation letting me know what has been changed.  The suggestion is given to look at [http://svn.mythtv.org/trac/timeline](http://svn.mythtv.org/trac/timeline) but this seems a terribly laborious method if you are just interested in solving a specific problem and trying to find out which update you want.

I guess I'm just used to the normal Ubuntu updates where a specific problem is found and an update is pushed out to fix that issue along with a changelog.  Auto-builds seems more like constantly upgrading everything in hope that your specific issue is caught in the dragnet.  This seems particularly precarious if you are concerned about system stability.

Or am I misinterpreting how this works?

---

### Post by tgm4883 on 2010-06-20
> **SMANN said:**
> Well, a couple of things:

1. That the updates for Myth, presumably the central reason for installing Mythbuntu, are not enabled by default.  You have to locate the auto-build page, download and install the deb, etc.  There is also nothing w/in Mythbuntu Control Center that leads one down the path of applying updates for Myth I'd guess there is a reason for this but I'm not sure what it is.  It kind of suggests that auto-builds are an advanced user, proceed w/ caution thing.

Can't do that for policy reasons. There might be a resolution for that in Maverick.


> **SMANN said:**
> 
2. That they are automatic daily builds.  From a user's perspective all I see is a given number of updates available in the update manager and none of them have any documentation letting me know what has been changed.  The suggestion is given to look at [http://svn.mythtv.org/trac/timeline](http://svn.mythtv.org/trac/timeline) but this seems a terribly laborious method if you are just interested in solving a specific problem and trying to find out which update you want.

I guess I'm just used to the normal Ubuntu updates where a specific problem is found and an update is pushed out to fix that issue along with a changelog.  Auto-builds seems more like constantly upgrading everything in hope that your specific issue is caught in the dragnet.  This seems particularly precarious if you are concerned about system stability.

Or am I misinterpreting how this works?

You are overestimating the manpower that the Mythbuntu team has. They are auto-builds, and AFAIK there isn't an easy way to pull whats changed between each build. You can assume that if you select the version that you are currently running, that the builds are pulled from the upstream -fixes branch. 

Patches are accepted though if you want to edit the build script so that it contains more information visable to the user.

---

