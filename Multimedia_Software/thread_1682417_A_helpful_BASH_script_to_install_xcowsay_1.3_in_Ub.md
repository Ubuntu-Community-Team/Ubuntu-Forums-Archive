---
title: "A helpful BASH script to install xcowsay 1.3 in Ubuntu"
date: 2011-02-05
forum: Multimedia Software
---

### Post by clockworkpc on 2011-02-05
Xcowsay is a great little program that brings the joy of a talking cow to your desktop.
Sadly, the newest version is not in the repositories even in Ubuntu Maverick, and I haven't found a PPA either.

Luckily, we're using Linux here, so we can compile it ourselves.

The following is a BASH script I wrote to take care of it for you.

To use it:

[LIST=1]```

```
[*]Download the tarball of xcowsay and save it to your desktop
[*]Copy and paste the following code into gedit or your favourite text editor:

```

#!/bin/bash

#       Copyright 2011 Clockwork PC (www.clockworkpc.com.au)
#       
#       This program is free software; you can redistribute it and/or modify
#       it under the terms of the GNU General Public License as published by
#       the Free Software Foundation; either version 2 of the License, or
#       (at your option) any later version.
#       
#       This program is distributed in the hope that it will be useful,
#       but WITHOUT ANY WARRANTY; without even the implied warranty of
#       MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#       GNU General Public License for more details.
#       
#       You should have received a copy of the GNU General Public License
#       along with this program; if not, write to the Free Software
#       Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
#       MA 02110-1301, USA.
#       
#   

### Step 3: Compile xcowsay ###

echo "Now let's install the newest version of xcowsay (1.3)"

echo "3"
sleep 1
echo "2"
sleep 1
echo "1"
sleep 1

sudo cp ~/Desktop/xcowsay-1.3.tar.gz /usr/local/src/xcowsay-1.3.tar.gz
sudo apt-get install libgtk2.0-dev
cd /usr/local/src/ && 
sudo tar zxvf /usr/local/src/xcowsay-1.3.tar.gz &&
sudo /bin/bash /usr/local/src/xcowsay-1.3/configure && 
sudo make && 
sudo make install

echo "That's it, it's all installed."
(gnome-terminal -x xcowsay --monitor=0 --cow-size=large "That's it, it's all installed." &);(gnome-terminal -x mplayer ~/Videos/Sound_effects/moo.wav) &&

echo "5"
sleep 1
echo "4"
sleep 1
echo "3"
sleep 1
echo "2"
sleep 1
echo "1"
sleep 1


```
[*]Save the file as to your desktop as xcowsay_install.sh
[*]then open a terminal and type the following:
[/LIST]

```
cd ~/Desktop
chmod +x xcowsay_install.sh
./xcowsay_install.sh

```
And that's it!

Try it out by typing in the terminal:
```
xcowsay "hello world"
```

---

