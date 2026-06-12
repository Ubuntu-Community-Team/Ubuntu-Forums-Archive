---
title: "MythTV Backend Setup has closed unexpectedly"
date: 2015-10-10
forum: Mythbuntu
---

### Post by waynelivingstone on 2015-10-10
I have newly installed mythbuntu 14.04.2 and got everything working as desired. 
I use mythwelcome and have this BE/FE machine set to shutdown when idle. (Well this mostly works, but that is not the issue I'm posting about)

Very regularly I am getting an error popup saying "The application MythTV Backend Setup has closed unexpectedly"
If I select relaunch it will happen again soon after. If I select leave closed it seems to be fine until the text shutdown and wake, when it will appear again after an undetermined period. 

Should MythTV backend setup even be running during normal operation?

I'm not sure where to start looking to solve this issue.

---

### Post by blm-ubunet on 2015-10-11
mythtv-setup should not be running in normal operation.
I've never seen it start automatically.

Mythtv-setup is the preferred tool for allowing/performing database upgrades..
You are meant to run it **first** after any mythtv upgrade.

You have used it at least once?
Did you run it from MCC?

Possible the mythbuntu packaging post-install script tries to run it & this script has never run to completion.
dpkg-query -l mythtv*

Your desktop been configured to start it on login?
Your desktop is set to restart all programs running at exit/logout?

I guess that MCC handles all of the following/below..
When you do run mythtv setup it should be run as user "mythtv" (same as mythbackend).
Should stop all clients (kodi, mythweb) & stop all/any FEs & BEs.
Stop master BE service:
sudo initctl stop mythtv-backend
(your BE service could have a slightly diff name - use <TAB> key)
Run mythtv-setup:
sudo -H -u mythtv mythtv-setup

Be aware that mythbuntu packaging wraps the real executable (renamed *.real) in a script with name of original program.

---

### Post by jaktar on 2015-12-09
I recently did a clean install and ran into (what I believe to be) the same problem.  I believe that during the upgrade, my user was not added to the mythtv group.  I'm not an expert by any means, but my understanding is that my username needs to be in that group.  I did attempt to run mythtv-setup as -u mythtv, but it didn't work.  

What fixed the problem for me was:
[https://help.ubuntu.com/community/MythTV_mythtvsetup](https://help.ubuntu.com/community/MythTV_mythtvsetup)

Follow the section for starting mythtv-setup (below) and add your user to the mythtv group.  Logout and then login again.  Then run mythtv-setup again under your username.

```
Starting mythtv-setup
mythtv-setup must either be launched as a user that is in the mythtv group.

Next, add yourself and any other users that need MythTV acces to the mythtv group.  

To add users to the mythtv group, use this command:

# sudo usermod -a -G mythtv USERNAME
Where USERNAME is the name of the user you are adding to the mythtv group.
VERY IMPORTANT: If you do not add your main user account to the mythtv group, you will get the dreaded database errors when you run mythtv-setup! For the addition to the group to take effect, a fresh login needs to occur-- so log out of your current session and then log back in right now.

Once your are in the mythtv group and have logged out/in, you will be able to launch mythtv-setup.
mythtv-setup


```

---

