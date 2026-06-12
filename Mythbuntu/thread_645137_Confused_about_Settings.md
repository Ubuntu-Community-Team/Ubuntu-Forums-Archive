---
title: "Confused about Settings"
date: 2007-12-19
forum: Mythbuntu
---

### Post by geek_geek on 2007-12-19
I'm new to Mythbuntu, but an old hat with Mythtv.  I recently converted my box from home-grown Mepis with mythtv to Mythbuntu.  

A few things have confused me:

1) when logging in using the NX client, I see icons on the desktop but not when logged in to the box directly

2) I converted xscreensaver files to gnome-screensaver files. I can see these when logged in from an NX client (and they work) but cannot see them when logged into the box directly

3) In Mythtv, I like to see my recorded programs via category view. I set this, but when I exit Mythtv and restart it, it has reverted back to Titles Only.  All other settings appear to have been written to the the database but not this one.

4) Why are there two home directories (mythtv and ubuntu) but no users with those logins?

Any help in getting me familiar with the Mythbuntu configuration would be appreciated.  I have done a lot of searching but cannot find any answers.

---

### Post by geek_geek on 2007-12-21
I figured out how to see the installed screen savers. It seems that by using login session Mythbuntu, script /usr/share/mythbuntu/session.sh is executed (via /usr/share/xsessions/mythbuntu.desktop).  By editing the file and commenting out the following lines, I am now able to see the installed screensavers:
[INDENT]export XDG_CONFIG_DIRS=/etc/xdg/mythbuntu
export XDG_DATA_DIRS=/etc/xdg/mythbuntu
[/INDENT]

From what I found, this causes the system to use the user home directory setting files instead of those specified in the above paths.

This also allowed me to to see icons on the desktop.

Hope this helps others.

---

