---
title: "My first day on Ubuntu: I can't play avi files!??"
date: 2009-12-16
forum: Multimedia Software
---

### Post by karmi on 2009-12-16
This is my first day to try ubuntu, my OS is Ubuntu 9.10 - amd 64.. and when I try to play avi video files it gives me errors! after seraching the forums I found that there is a package called (Ubuntu Restricted Formats) that they say I must install, but the problem is that when I click on the link it gives me a dialog box saying:

[COLOR=Red]**This link needs to be opened with an application. send to:**[/COLOR]

So what am I supposed to do next? or is there another way to play .avi files?
This is the link where I tried to install the restricted formats:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Any help would be appreciated indeed!

---

### Post by bluelamp999 on 2009-12-16
Hi there,

Go to *Applications>Ubuntu Software Centre* and type 'restricted' in the search box.

The top option returned will be 'Ubuntu Restricted Extras', install this and you should be good...

---

### Post by wojox on 2009-12-16
Even better open a terminal ( Applications > Accessories > Terminal ) and type or copy and paste:

```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

---

### Post by slakkie on 2009-12-16
Or use this script:

```

#!/usr/bin/env bash

# Check if we are on Ubuntu
if [ "$(lsb_release -is)" != "Ubuntu" ] ; then
    echo "This script is only intended to run on Ubuntu"
    exit 255
fi

# Check if we are root
if [ $UID -ne 0 ] ; then
    echo "Please run this as root!"
    exit 255
fi


# Get distro
distro=$(lsb_release -cs)

# Check if medibuntu repo is already present
src=/etc/apt/sources.list

grep -v "^#" $src | grep "packages.medibuntu.org" &>/dev/null
if [ $? -ne 0 ] ; then
    # Add them if not and update
    echo "" >> $src
    echo "## Medibuntu repositories, visit http://www.medibuntu.org/ for more details" >> $src
    echo "deb http://packages.medibuntu.org/ $distro free non-free" >> $src
    wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | apt-key add -
    aptitude update
fi

# Finally, install all the packages
aptitude install gstreamer0.10-ffmpeg ubuntu-restricted-extras vlc mplayer mozilla-plugin-vlc mozilla-mplayer libdvdcss2 non-free-codecs

```

---

### Post by karmi on 2009-12-16
Hello Bluelamp,
I did what you told me but I get a message saying:

[B]Not available in the current data
Canonical does not provide updates for ubuntu restricted extras. some updates may be provided by the ubuntu community.[/B]

So what should I do next?

---

### Post by munkymac on 2009-12-16
There's two ways to do this. 

Way 1: Open a terminal and paste in the following (Paste in the terminal is 'Ctrl-Shift-V')

```
sudo apt-get install ubuntu-restricted-extras
```

Then just enter your password, hit 'Y' when prompted, and you are good to go

Way 2: (If you aren't comfortable with the terminal)

1. Go to System>Administration>Synaptic Package Manager
2. Enter your password when prompted
3. Click Software>Repositories, and make sure that 'Software restricted by copyright or legal issues (multiverse)' is checked
4. Click 'Close', then 'Reload' (if prompted)
5. Search for ubuntu-restricted-extras (in the Quick Search box)
6. Mark the file for installation, then click 'Apply'

you should be up and running. If you are still having problems, try opening the file with VLC Media Player.

---

### Post by bluelamp999 on 2009-12-16
> **slakkie said:**
> Or use this script:

```

#!/usr/bin/env bash

# Check if we are on Ubuntu
if [ "$(lsb_release -is)" != "Ubuntu" ] ; then
    echo "This script is only intended to run on Ubuntu"
    exit 255
fi

# Check if we are root
if [ $UID -ne 0 ] ; then
    echo "Please run this as root!"
    exit 255
fi


# Get distro
distro=$(lsb_release -cs)

# Check if medibuntu repo is already present
src=/etc/apt/sources.list

grep -v "^#" $src | grep "packages.medibuntu.org" &>/dev/null
if [ $? -ne 0 ] ; then
    # Add them if not and update
    echo "" >> $src
    echo "## Medibuntu repositories, visit http://www.medibuntu.org/ for more details" >> $src
    echo "deb http://packages.medibuntu.org/ $distro free non-free" >> $src
    wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | apt-key add -
    aptitude update
fi

# Finally, install all the packages
aptitude install gstreamer0.10-ffmpeg ubuntu-restricted-extras vlc mplayer mozilla-plugin-vlc mozilla-mplayer libdvdcss2 non-free-codecs

```

I'm sorry but are you being sarcastic? It's their *first day* on Ubuntu for God's sake! A big scary-looking script is hardly the ideal introduction...

---

### Post by slakkie on 2009-12-16
> **bluelamp999 said:**
> I'm sorry but are you being sarcastic? It's their *first day* on Ubuntu for God's sake! A big scary-looking script is hardly the ideal introduction...

First day on Ubuntu != First day on Linux. I don't know and cannot know how experienced he is. If he knows Fedora or whatever distro he might be familiar with scripts. This is not posted in Absolute beginners.

---

### Post by bluelamp999 on 2009-12-16
> **slakkie said:**
> First day on Ubuntu != First day on Linux. I don't know and cannot know how experienced he is. If he knows Fedora or whatever distro he might be familiar with scripts. This is not posted in Absolute beginners.

Very true and I absolutely meant no disrespect.

---

