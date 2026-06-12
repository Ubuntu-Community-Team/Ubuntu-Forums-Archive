---
title: "auto-build 0.24-fixes"
date: 2010-10-21
forum: Mythbuntu
---

### Post by jbman on 2010-10-21
Hi guys,

I see there is a 0.24-fixes tread now for mythtv and I am wondering if I change my autobuilds to 0.24 from MCC will that be the new packages I will be using.

Or does changed to 0.24 move me to trunk? I am not sure how to choose between trunk and fixes for 0.24

Cheeers

---

### Post by sfp on 2010-10-21
I am running the 0.24 autobuilds and they are now built on the 0.24-fixes branch and not the truck branch.

---

### Post by jbman on 2010-10-23
Cheers,

I changed to 0.24, had to unmark the libmyth-0.23 as it wanted to update to a 0.24 trunk version and gave errors with the install.

All in all working well :)

---

### Post by tgm4883 on 2010-10-23
> **jbman said:**
> Hi guys,

I see there is a 0.24-fixes tread now for mythtv and I am wondering if I change my autobuilds to 0.24 from MCC will that be the new packages I will be using.

Or does changed to 0.24 move me to trunk? I am not sure how to choose between trunk and fixes for 0.24

Cheeers

Please note that I am only asking this for clarification so I can fix the page if necessary. 

Did you just not read the auto-builds page, or was it not-clear/confusing as to what would happen with the repo that was previously built from trunk?

---

### Post by jbman on 2010-10-25
Happy to give feedback.

I checked the autobuild forum thread and didn't find any info.

I looked on the mythbuntu website and didn't see all the info I saw when I checked today.

All i was looking for was a simple, if you pick xx version that is currently in trunk, when it moves to release you won't need to make any changes. As I wasn't sure if I picked 0.24 and it would keep my in trunk no matter what version it was.

Cheers

---

### Post by nickrout on 2010-10-25
This is what the autobuilds web page says as at the time of writing this:

> Auto-builds is a service provided by the Mythbuntu team for users who want to follow upstream MythTV code more closely.  Two builds are provided for each Mythbuntu release (ie. 0.23 and 0.24 for Lucid). The packaging used to create these builds is identical to that being used for MythTV content in the Ubuntu archive. They are built daily if there have been any changes upstream.

Selecting a version will only get you updates for that version, you will NEVER be automatically updated to the next version of MythTV UNLESS you manually reconfigure the auto builds package and select a different version. (ie. If you select 0.23, you will NEVER be automatically updated to 0.24 UNLESS you manually reconfigure the auto-builds package and select 0.24)

It DOESN'T say that 0.24 is tracking 0.24-fixes (which is a change I wasn't aware of, it used to track trunk).

It doesn't mention what the transition plan is once 0.24 is released. - Will 0.23-fixes still be tracked?

- Will it then be:

0.24 tracks 0.24-fixes
0.25 tracks trunk?

What the hell is 0.24-fixes anyway - 0.24 has not been released. Is 0.24-fixes the RC with fixes? will it transition to 0.24 when released?

---

### Post by tgm4883 on 2010-10-25
> **nickrout said:**
> This is what the autobuilds web page says as at the time of writing this:



It DOESN'T say that 0.24 is tracking 0.24-fixes (which is a change I wasn't aware of, it used to track trunk).

It doesn't mention what the transition plan is once 0.24 is released. - Will 0.23-fixes still be tracked?

- Will it then be:

0.24 tracks 0.24-fixes
0.25 tracks trunk?

What the hell is 0.24-fixes anyway - 0.24 has not been released. Is 0.24-fixes the RC with fixes? will it transition to 0.24 when released?

nickrout, correct. It doesn't say it is tracking 0.24-fixes. It doesn't say what it is tracking. Why should that matter to the user? If you want builds for 0.24, select 0.24 and trust you are getting builds for 0.24. [0.24-fixes]("http://svn.mythtv.org/trac/browser/branches/release-0-24-fixes") is a branch upstream. It is where bug fixes will happen for 0.24. When 0.24 gets released, it will simply be a checkout from that branch. If there is a 0.24.1 in the future, it will simply be another checkout from that branch.



Each mythbuntu repo is named after the final version it will offer. The 0.24 repo may go though a few different upstream branches, but the very last build it will get will be from the 0.24 fixes branch. From a user perspective, this means they select 0.24 and will eventually get builds from the 0.24 fixes branch without ever having to do anything but select 0.24. From a development point of view, the 0.24 repo initially pulls from the trunk branch. Once the 0.24 upstream branch gets cut, the 0.24 repo start building that. Once 0.24 gets released and there is a fixes branch, the 0.24 repo starts pulling from the 0.24 fixes branch. Builds will continue for 0.24 until upstream stops committing to that branch. 

So from a developer perspective, we change things in the background and everything gets uploaded to a single 0.24 repo. From the user perspective, no matter when they activate the 0.24 repo (whether it months ago and was pulling from trunk, or if they activated it a few days ago), if the user keeps updating they will end up with builds from 0.24 fixes. The user won't need to go in and reselect their repos, they simply need to keep doing regular system updates. 

It's done this way for a few reasons. It allows the user to select a version of mythtv (be it 0.23, 0.23.1, 0.24, etc) and get fixes for that particular release. The user doesn't need to worry about that version getting automatically updated to the next version of mythtv. The other reason is version compatibility between multiple systems. As long as a user selects the same version (eg. 0.24) on each system they should be compatible. 

Please ask questions if this is not clear. This isn't the only time I've tried to answer these questions and I'd like the webpage to get tweaked so it's clearer if necessary. If anyone has suggestions that would make the page clearer, please let me know and I will consider updating the page.

---

### Post by nickrout on 2010-10-25
OK I think I understand better now. Thanks for the explanation. 

Hard to make a generic statement on the web page that you don't have to keep changing as versions are released etc. But perhaps a little note on the autobuilds page that says:

"Right now, 0.23 is tracking xxx, 0.24 is tracking y" someone should be able to write a script that looks at the build parameters and has that updating automagically.

just a suggestion.

---

### Post by joshoekstra on 2010-10-27
Might have been watching to many presentation lately, but a nice course might be to list it in a little table with collums designating what state of development a version is in?

Like:
.......trunk.....stable.....Fixes
.23 ...........................x
.24 ....x

And so on?

---

### Post by tgm4883 on 2010-10-27
> **joshoekstra said:**
> Might have been watching to many presentation lately, but a nice course might be to list it in a little table with collums designating what state of development a version is in?

Like:
.......trunk.....stable.....Fixes
.23 ...........................x
.24 ....x

And so on?

The issue with that is it requires me to remember to update that page each time the status of a release changes. Ideally, I want to set it and forget it.

---

### Post by nickrout on 2010-10-27
That's why you write a script which looks at the build system and makes it's own deduction. set and forget.

---

