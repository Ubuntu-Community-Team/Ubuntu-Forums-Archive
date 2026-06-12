---
title: "Dell Dimension 4550 Not Working With Sound"
date: 2011-04-27
forum: Multimedia Software
---

### Post by TheSingingCoyote on 2011-04-27
I have working speakers that I am trying to attach to my Ubuntu Dell computer. It's an older computer, and only has 512 ram, and a 20 gig hard drive right now. When I hooked up the speakers, and everything and try to play a youtube music video, the music plays at a very sped-up rate. The speakers are Altec Lansing speakers. 

I have tried to find the answer to this problem with no luck. Do I need to do any coding in the terminal? Or is there another problem?


Thanks,
-Mallory

---

### Post by lidex on 2011-04-27
A little info please. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by TheSingingCoyote on 2011-04-28
Says, "Command not found"...It says the -0 is an invalid option...

EDIT: Read that wrong! 

It said it couldn't connect to alsa project, basically. Said it was unknown. I tried to copy and paste, but couldn't, so I can't easily show you the code...but that's really the gist of it.

---

### Post by lidex on 2011-04-28
Copy and paste the command and it will work.

---

### Post by TheSingingCoyote on 2011-04-28
See, that's the problem. I am having trouble with copying and pasting.

EDIT: Okay, I retyped it, and I got it working. What do I do now?

---

### Post by lidex on 2011-04-28
> **TheSingingCoyote said:**
> See, that's the problem. I am having trouble with copying and pasting.

EDIT: Okay, I retyped it, and I got it working. What do I do now?

Post the link to the output.

---

### Post by TheSingingCoyote on 2011-04-28
I am not quite sure what you mean, but this is what I got:

```
#!/bin/bash

SCRIPT_VERSION=0.4.60
CHANGELOG="http://www.alsa-project.org/alsa-info.sh.changelog"

#################################################################################
#Copyright (C) 2007 Free Software Foundation.

#This program is free software; you can redistribute it and/or modify
#it under the terms of the GNU General Public License as published by
#the Free Software Foundation; either version 2 of the License, or
#(at your option) any later version.

#This program is distributed in the hope that it will be useful,
#but WITHOUT ANY WARRANTY; without even the implied warranty of
#MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#GNU General Public License for more details.

#You should have received a copy of the GNU General Public License
#along with this program; if not, write to the Free Software
#Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.

##################################################################################

#The script was written for 2 main reasons:
# 1. Remove the need for the devs/helpers to ask several questions before we can easily help the user.
# 2. Allow newer/inexperienced ALSA users to give us all the info we need to help them.

#Set the locale (this may or may not be a good idea.. let me know)
export LC_ALL=C

#Change the PATH variable, so we can run lspci (needed for some distros)
PATH=$PATH:/bin:/sbin:/usr/bin:/usr/sbin
BGTITLE="ALSA-Info v $SCRIPT_VERSION"
PASTEBINKEY="C9cRIO8m/9y8Cs0nVs0FraRx7U0pHsuc"
#Define some simple functions

pbcheck(){
	[[ $UPLOAD = "no" ]] && return

	if [[ -z $PASTEBIN ]]; then
		[[ $(ping -c1 www.alsa-project.org) ]] || KEEP_FILES="yes" UPLOAD="no" PBERROR="yes"
	else
		[[ $(ping -c1 www.pastebin.ca) ]] || KEEP_FILES="yes" UPLOAD="no" PBERROR="yes"
	fi
}
```

---

### Post by TheSingingCoyote on 2011-04-28
Okay, I also tried firefox, and uninstalling and reinstalling flash. No luck. Same thing....Anyone? It seems like a simple problem. Not sure why I am hardly getting any replies :/

---

### Post by lidex on 2011-04-28
It can be simple; it can be complex. It's hard to know without some system info.
When you run the alsa-info script, the terminal will ask if you want to upload the output. 
Press the <Y> key and hit <enter> and wait for the terminal to output the location. Include that url in your next post.

---

