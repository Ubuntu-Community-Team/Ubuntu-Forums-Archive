---
title: "Mythweb issues post-Karmic-upgrade"
date: 2009-12-01
forum: Multimedia Software
---

### Post by toganet on 2009-12-01
As a long-time Ubuntu and Mythtv user, I am used to running into issues with upgrades and having to dig through forums and google searches until I find answers.  I expected problems with this upgrade, so I waited a month and then did a dist-upgrade on my mythtv box.  All seemed to go well, until I tried to use mythweb, at which point I was greeted with the following error (truncated for brevity):

```
    errornum:  256
  error type:  User Error
error string:  MasterServerIP or MasterServerPort not found! You mayneed to check your settings.php file or re-run mythtv-setup
    filename:  /usr/share/mythtv/mythweb/classes/MythBackend.php
  error line:  45

```

I have found a corresponding bug report at mythtv, but it does not seem to be receiving any attention.  Everything else is working as far as I can tell -- back and front ends are performing as expected, recording works, even my remote works now, which did not before.

As far as troubleshooting, I have done the following:

[LIST]
[*]Verified that MasterServerIP and MasterServerPort are configured and correct in the database.
[*]Re-ran mythtv-setup
[*]Checked every instance of config.xml and mysql.txt on the box (why so many??)
[*]Verified that the bind_address setting was correct in my.cnf (thanks Update for messing this up even though I told you to keep my version).
[*]Removed and reinstalled mythweb (including using --purge and deleting the leftover files and caches).
[*]Fiddled around with various permutations of security (via mythbuntu-control-center and dpkg-reconfigure mythweb)
[/LIST]
Beyond this point I am not sure what to do beyond starting to read the code.  And as I say at work, when it gets to the point where *I* am reading the code trying to fix things, something is *very wrong*.

I hate to cross-post, but I feel like this won't get attention unless I do so.

Does anyone have an idea where mythweb draws its database connection information from?  Is there anything in the changes from 9.04 -> 9.10 that would change the way it interacts with MySQL?

---

