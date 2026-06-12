---
title: "Should I click &quot;yes&quot; to upgrade to 11.04?"
date: 2011-05-02
forum: Mythbuntu
---

### Post by drjenk on 2011-05-02
Hi,
I'm running mythbuntu 10.10.  I got a prompt to upgrade Ubuntu to 11.04.  Now this is not "mythbuntu", but "ubuntu" that is being prompted for upgrade.  How do I go about upgrading mythtv from 0.23, to 0.24 included in mythbuntu 11.04?  Is it safe to do outside of doing a fresh install?

Thanks
David J.

---

### Post by LowSky on 2011-05-02
first download and run this
[http://www.mythbuntu.org/files/mythbuntu-repos.deb](http://www.mythbuntu.org/files/mythbuntu-repos.deb)... more infor here, [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)

then do a regular update so that .24 is installed with its fixes.

then upgrade to 11.04

---

### Post by Mad-Halfling on 2011-05-02
I did this and it seems to have broken my system - if I run mythbackend --version I get "mythbackend: error while loading shared libraries: libmythtv-0.23.1.so.0: cannot open shared object file: No such file or directory" - any ideas how I can revert to 0.23?

---

### Post by JamesNorris on 2011-05-02
If you have a broken install, I would do as the post above says and install the autobuilds. This will get you the most stable up-to-date myth packages, they supersede the ones from ubuntu.

---

### Post by Mad-Halfling on 2011-05-02
Installing that is what broke it =8/  This is my problem - I installed the deb from there, told it to update to 0.24 and now it's screwed.  I'd be happy to reinstall mythtv and go back to version 0.23 but removing mythtv-backend and installing it again gives me the same problem

---

### Post by Mad-Halfling on 2011-05-02
I've run the control center and enabled the package repos up to 0.23.1, I noticed that mythtv-database was still at 0.24 and so have removed and installed that - it's at 0.23 now and dpkg -l myth* shows everything at 0.23 again but running mythbackend --version still give the error "mythbackend: error while loading shared libraries: libmythtv-0.23.1.so.0: cannot open shared object file: No such file or directory"
- help.....
Is there a way I can reinstall mythtv on my mybuntu box (preferably via the command line as the server is headless) completely without having to grab the box out of it's cupboard, connect it up to a monitor and keyboard and reinstall the whole OS?

---

### Post by drjenk on 2011-05-02
> **Mad-Halfling said:**
> Installing that is what broke it =8/  This is my problem - I installed the deb from there, told it to update to 0.24 and now it's screwed.  I'd be happy to reinstall mythtv and go back to version 0.23 but removing mythtv-backend and installing it again gives me the same problem

Please elaborate, do you mean you installed 11.04 first, or did you do as the previous poster suggested, to get your system in a screwed state?  That is, did  you upgrade to mythtv .24 first, then 11.04, or the other way around?

---

### Post by superm1 on 2011-05-02
If for some reason your libraries are busted after the upgrade, just re-enable auto-builds and re-update those myth* packages from autobuilds.

---

### Post by nickrout on 2011-05-03
My advice: based on the number of screwups referrred to in this forum, do NOT upgrade to 11.04.

BUT do upgrade to 0.24-fixes using mythbuntu-repos.

---

### Post by drjenk on 2011-05-03
I plan to upgrade to mythtv 0.24 via the repos link in this thread, thanks.
But I'll hold off on the 11.04 upgrade.

But I have one more question.  In the release notes for .24, it says

"As the full release notes say, all users upgrading from a previous version of MythTV to 0.24 are **required**  to rescan for audio devices on their frontends (in the audio settings  menu) after upgrading due to the rewritten audio framework which can  conflict with legacy settings".

Does it mean audio settings in mythtv?  I see where the audio setting are, under settings/general, but I don't see a "rescan" button.  Does the action of going to these menus initiate a rescan?  Just checking this out beforehand.  Maybe the new .24 version has a rescan option?

Thanks
David J.

---

### Post by uteck on 2011-05-03
11.04 (actually kernel 2.6.38 ) seems to have problems with MS media centre remotes, so it you have one hold off.

---

### Post by superm1 on 2011-05-03
> **uteck said:**
> 11.04 (actually kernel 2.6.38 ) seems to have problems with MS media centre remotes, so it you have one hold off.

That should be fixed with the lirc in natty-updates.

---

### Post by nickrout on 2011-05-03
> **drjenk said:**
> I plan to upgrade to mythtv 0.24 via the repos link in this thread, thanks.
But I'll hold off on the 11.04 upgrade.

But I have one more question.  In the release notes for .24, it says

"As the full release notes say, all users upgrading from a previous version of MythTV to 0.24 are **required**  to rescan for audio devices on their frontends (in the audio settings  menu) after upgrading due to the rewritten audio framework which can  conflict with legacy settings".

Does it mean audio settings in mythtv?  I see where the audio setting are, under settings/general, but I don't see a "rescan" button.  Does the action of going to these menus initiate a rescan?  Just checking this out beforehand.  Maybe the new .24 version has a rescan option?

Thanks
David J.

0.24 has a scan for audio devices button in the audio setup page. You have the right setting page, but in 0.24 it will have a scan button right at the top.

---

### Post by dheianevans on 2011-05-04
Would you recommend "pinning" to 10.10 right now in /etc/apt/preferences to hold off on 11.04 until the mythtv issues have been resolved?

---

### Post by nickrout on 2011-05-04
just don't upgrade.

---

### Post by dheianevans on 2011-05-05
> **nickrout said:**
> just don't upgrade.

Just going back to the point I made on the MythTV list: I still want to be able to grab mythtv fixes, security fixes for utils (I use my mythbox to grab downloads from my webserver), etc.

I'm just looking for an automatic way to ignore the OS upgrade so I don't accidentally move to 11.04.

In YUM, I'd just tell it to ignore kernel upgrades or something like that. Just curious what I need to do to stop synaptic package manager or upgrade-manager from moving to 11.04 if I (or more likely, someone else in the house) hits the upgrade button if we drop down to the desktop. I agree with what you've said about this being an appliance in other threads. I just want to make sure I can upgrade the toast without upgrading the toaster. :-)

---

### Post by superm1 on 2011-05-05
> **dheianevans said:**
> Just going back to the point I made on the MythTV list: I still want to be able to grab mythtv fixes, security fixes for utils (I use my mythbox to grab downloads from my webserver), etc.

I'm just looking for an automatic way to ignore the OS upgrade so I don't accidentally move to 11.04.

In YUM, I'd just tell it to ignore kernel upgrades or something like that. Just curious what I need to do to stop synaptic package manager or upgrade-manager from moving to 11.04 if I (or more likely, someone else in the house) hits the upgrade button if we drop down to the desktop. I agree with what you've said about this being an appliance in other threads. I just want to make sure I can upgrade the toast without upgrading the toaster. :-)

It won't move to 11.04 accidentally doing updates.  You'll have to click a couple of buttons to get there.

Starting with the next LTS we're planning on only doing Mythbuntu ISOs for the LTS releases and LTSs are by default set to only jump to the next LTS.  People who want to do it in between will be able to still, but we'll focus on making the LTSes great instead.

---

### Post by uteck on 2011-05-08
> **superm1 said:**
> That should be fixed with the lirc in natty-updates.

Thanks, I just saw this update on my machine today and now my remote works again. :)

---

