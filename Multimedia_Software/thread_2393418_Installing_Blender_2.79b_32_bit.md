---
title: "Installing Blender 2.79b 32 bit"
date: 2018-06-03
forum: Multimedia Software
---

### Post by claus on 2018-06-03
Hi,

since I had rendering artifacts with the Blender 2.79b install out of the Ubuntu repositories (and not for the first time), I removed Blender and downloaded it from blender.org. Now my question: Where is the proper location to install Blender, and how do I get the Blender icon into the dock? So far, I have installed it in $HOME/Software. I am using Ubuntu 18.04 LTS/32 bit.

TIA,

Claus

P.S.: I found the solution myself. I moved the Blender files to $Home/bin, which is included in my $PATH. Now I can invoke Blender simply by typing 'blender' into a shell.

---

### Post by #&amp;thj^% on 2018-06-03
Just another method recommended.
this should work for even a 32bit install providing you downloaded the appropriate version for your computer, 32-bit or 64-bit.

I usally make a folder in my Home named "blender" and extract it there, for ease of moving it later. 
Very important to remove the previous installed blender with:
```
sudo apt-get remove blender
```

Then I copy the blender files where they need to go via:
```
sudo cp ~/blender /usr/lib/blender -r
```
From the proper path. ;)
You can check if everything is correct by browsing with your file manager in
folder **usr, then lib blender.** make sure blender shows there in both directories if not try the command above again.
just open blender now.
You can redo these steps as many times as needed when a new version of Blender comes out. To remove everything in the blender folder so you can do these steps again, open a terminal and run these commands: 
```
sudo rm /usr/lib/blender -r
```
Good Luck

---

