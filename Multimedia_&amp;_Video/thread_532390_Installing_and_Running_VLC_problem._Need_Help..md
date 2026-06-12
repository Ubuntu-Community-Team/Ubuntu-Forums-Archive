---
title: "Installing and Running VLC problem. Need Help."
date: 2007-08-22
forum: Multimedia &amp; Video
---

### Post by swy000 on 2007-08-22
So I was trying to install VLC to try and get simple mp3s running and all. I followed the directions on the VLC website here: [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html).

I first typed: 
```
sudo apt-get update
```
and then:
```
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
```

After that, it seemed done but was never added to Applications -> Sound&Video and I cant seem to run it from anywhere.

If i type ```
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
```
i get this as an error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mozilla-plugin-vlc: Depends: vlc-nox (= 0.8.6.release-0ubuntu4) but it is not going to be installed
  vlc: Depends: vlc-nox (= 0.8.6.release-0ubuntu4) but it is not going to be installed
       Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
  vlc-plugin-esd: Depends: vlc-nox but it is not going to be installed
E: Broken packages

```

Any ideas how I can get VLC working? I found a similar post without much of a solution.
Thanks,

swy

EDIT: this is literally my first day using Ubuntu. No prior experience. Ive used red hat about 4 years ago. but ive been on XP since then.

---

### Post by linuxwizard on 2007-08-22
Sometimes when you install a new applications they don't get added  to the menu.You will have to add them to the menu. Use the link below and look for section:  Changing Your Menu Layout. ( right click application on panel) When you get to the first window > on the left side find Sound & Video click on > look on right side of window shows all applications installed on your system > look through and see if VLC is there > if there make sure put check in box next to it and close > now will show up in your menu. If it is not listed you will have to add it > continue to follow link >





[https://help.ubuntu.com/6.10/book/book/ubuntubook-ch3-html/UsingUbuntuontheDesktop.html](https://help.ubuntu.com/6.10/book/book/ubuntubook-ch3-html/UsingUbuntuontheDesktop.html).

---

### Post by Scunizi on 2007-08-22
You can also "sudo /etc/init.d/gdm restart which is basically the same as CTRL+ALT+Backspace.  that will reset the gui to recognize any new additions to the menu.

---

### Post by swy000 on 2007-08-22
ok, so i didnt find it in the search. So im assuming I have to add it. 
Im new to this, so im not sure where VLC installed itself. I did a search and I couldnt find that many files....
Where should I be able to find it installed? what is the extension of the filename that I need to browse to? (in windows i would search for a .exe, im not sure what i would search for here)...

thnx

---

### Post by linuxwizard on 2007-08-22
in the command box put > /usr/bin/vlc

---

### Post by swy000 on 2007-08-23
> **linuxwizard said:**
> in the command box put > /usr/bin/vlc

this is what i get: 

```
Failed to execute child process "/usr/bin/vlc" (No such file or directory)
```

so im assuming it really isnt installed... right :S ?

---

### Post by swy000 on 2007-08-23
> **Scunizi said:**
> You can also "sudo /etc/init.d/gdm restart which is basically the same as CTRL+ALT+Backspace.  that will reset the gui to recognize any new additions to the menu.

thought i would reply to this as well. i dont think the app is installed. i resarted however like u said. i thought it froze and i powered of the computer. but apparently it was busy working and i never gave it more than 3 minutes.. i think it needs time to restart... but i dont think its installed anyway!

---

### Post by linuxwizard on 2007-08-23
Go to Synaptic search for vlc and see if installed box will be colored if installed. If it is not installed I would recommend installing VLC through Synaptic.

---

### Post by swy000 on 2007-08-23
> **linuxwizard said:**
> Go to Synaptic search for vlc and see if installed box will be colored if installed. If it is not installed I would recommend installing VLC through Synaptic.

no, its not installed. under the installed column, there is nothing there so its not installed. i googled around and everytime i try to install vlc, or plugin-vlc, etc... i get a different error... for example: when i mark vlc for installation, window pops up telling me other packages will be affected, i hit ok and i get this error msg:

```
vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: libsdl-image1.2 (>=1.2.5) but it is not installable
```

---

### Post by swy000 on 2007-08-24
So the solution was found in another thread I put up I needed help in.

It can be found here just in case someone might have faced the same problem:
[http://ubuntuforums.org/showthread.php?t=532613&page=2](http://ubuntuforums.org/showthread.php?t=532613&page=2)

---

