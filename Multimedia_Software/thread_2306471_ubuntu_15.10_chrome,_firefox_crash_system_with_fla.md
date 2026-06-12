---
title: "ubuntu 15.10 chrome, firefox crash system with flash player"
date: 2015-12-15
forum: Multimedia Software
---

### Post by Ed_Redman on 2015-12-15
I am not sure what the problem is but when my wife runs chrome or firefox with flash player system randomly chrashes.
Only way to restart with a cold restart.

The same computer when playing chrome or firefox on windows 10 works without any crashes.

I have tried everything. I have reinstalled flash. Tried to use html5 instead (but facebook says she needs flash)

I have change her video drivers (intel). Disabled screensaver, change screen settings. Nothing fixes the problem.

I have looked for a solution. None found that fixes the problem. It is frustrating seeing the computer sail through the same programs on windows yet cannot fix in ubuntu. 

Her computer is a Acer Aspire X with 4 gigs memory and intel processor and intel onboard graphics.

I am really stuck on what I should be checking. Any help would be appreciated. 
thanks

---

### Post by deepakdeshp on 2015-12-18
Please try

[SIZE=4]sudo apt-get install gstreamer1.0-*
[/SIZE][COLOR=#111111][FONT=Ubuntu][SIZE=4]Downloads and installs a bunch of gstreamer libraries, now everything works fine again.[/SIZE][/FONT][/COLOR]

---

