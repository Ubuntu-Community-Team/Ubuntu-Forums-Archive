---
title: "Can't install RealPlayer 11 in 8.10"
date: 2008-11-24
forum: Multimedia Software
---

### Post by newtoubuntu on 2008-11-24
I have installed Ubuntu 8.10 on my thinkpad laptop.  I wanted to install RealPlayer.  I followed the directions, and downloaded the linux installation file from the RealPlayer web site.  The files name is: RealPlayer11GOLD.bin.  I changed the permissions to make the file executable: sudo chmod 755 RealPlayer11GOLD.bin.

this gives it rwxr-xr-x permission.

I then tried to execute it: sudo ./Realplayer11GOLD.bin  I am consistantly
getting this response when I execute the above command:
sudo: unable to execute ./RealPlayer11GOLD.bin: No such file or directory

I can see the file.  I have tried this as myself, using sudo, using sudo to become root (sudo su -) and no matter what I do, it comes back with this strange response.  Any help would be appreciated.

---

### Post by kpkeerthi on 2008-11-25
1. Open terminal and cd to the folder where the bin is saved
2. Type sudo ./Real[TAB][TAB] and press [enter]

[TAB] -> Press the TAB key to autocomplete file name

---

### Post by gandaran on 2008-11-25
> sudo: unable to execute ./RealPlayer11GOLD.bin: No such file or directory

I can see the file. I have tried this as myself, using sudo, using sudo to become root (sudo su -) and no matter what I do, it comes back with this strange response. Any help would be appreciated.
where is the realplayer file? desktop? then this is the reason you get the error message
if you don't know how to cd the terminal to desktop, then drop the realplayer file in your home 'user' folder, open the terminal and run the install command, it'll run okay.

---

### Post by newtoubuntu on 2008-11-25
Hey, the file was downloaded to the desktop.  I know how to change directories.  And of course when useing the shell, I listed to see the file.
used chmod 755 to set it to executable.  That is what is so weird.  I was able to do this for both Mandriva, and RedHat (5.2)
It seems like such a strange response that it can't see the file that is right there.

---

### Post by newtoubuntu on 2008-11-25
Note, I'm familiar with using Tab to autocomplete names too.  I did that.  Out of curiosity, why 2 tabs?  Is there some arcane thing that a 2nd Tab would accomplish?

---

### Post by Anbin89 on 2008-12-02
Hey guys. Same problem here and tried everything that was suggested here. I still cannot manage to install realplayer. It would be great if someone can let find out how to ... Thanks in advance

---

### Post by thadacto on 2008-12-05
If your still trying to install RealPlayer - it's not marked SOLVED.

I installed it on 8.04, +64. Initially I made a mistake in the name of the file on the desktop and got your response "No such file or directory". but that was my error (copying and pasting from instructions I found somewhere.
NOTE: This version of Real is nowhere near as good as the Windows version.

---

### Post by newtoubuntu on 2008-12-09
Hey, what I found out is that I had installed the 64 bit version of Ubuntu, and the RealPlayer installation program does not work for that version.  I reinstalled the 386 version of Ubuntu, and now RealPlayer installs fine.  I am betting that if you are having problems you might be in the same boat. 

By the way it is annoying that RealPlayer, and this forum, and the Ubuntu selection criteria do not point out that programs like RealPlayer will not install on the 64bit versions.  It would save a lot of time and grief if it was pointed out, when you are making the choice.

---

### Post by pierre.s.rosen on 2008-12-31
I got RealPlayer to work by going to [http://www.real.com/linux](http://www.real.com/linux) and selecting the .deb file from the bottom of the page, listed under "Advanced Installation Options".  When you download the .deb file, Firefox will prompt you to open the file with the GDebi Package Installer.  Click ok and install the file.  If the Installer seems to freeze, click the little triangle arrow thingy to see more details, and type the appropriate answer at the command prompt (I chose 1, no configuration for no mail).

For some reason, when I click on a RealPlayer link in Firefox, Totem launches and an error displays.  So, I just launch the player from the Applications menu---> Sound and Video ---> RealPlayer 11, then cut and paste the link directly into the player.  This worked for VOA radio broadcasts at voa.gov  -- YMMV at other websites.

---

### Post by gidyeo on 2009-04-07
had the same problem, i'm using Ubuntu 8.04 so i'm not too sure if the following works for 8.10... 

The problem (i think) is because the 64bit Ubuntu is trying to run a 32bit program, and to do that you'll need to install the 32bit library.

Use Synaptic Package Manager, search and install the following:
libc6 
libc6-dev 
libc6-i386
lib32gcc1 
lib32z1
lib32stdc++6 
lib32asound2 
lib32ncurses5 
ia32-libs

So far my realplayer has been working fine :)

credit:
[http://narnia.cs.ttu.edu/drupal/node/113](http://narnia.cs.ttu.edu/drupal/node/113)

---

### Post by noteviljoe on 2009-05-09
Trying to watch dizzle rascal video on bbc iplayer, I got the iplay radio wrking by installing kmplayer plugin through synaptic package manager but the Dizzle video still didn't seem to want to play. I then tried installing realplayer using the DEB package, and following the instruction above when it seemed to crash --> Video still not working though :-(

Tried the video in Windows vista and it worked fine on both explorer and firefox.

---

### Post by GROMS on 2009-06-06
> **gidyeo said:**
> had the same problem, i'm using Ubuntu 8.04 so i'm not too sure if the following works for 8.10... 

The problem (i think) is because the 64bit Ubuntu is trying to run a 32bit program, and to do that you'll need to install the 32bit library.

Use Synaptic Package Manager, search and install the following:
libc6 
libc6-dev 
libc6-i386
lib32gcc1 
lib32z1
lib32stdc++6 
lib32asound2 
lib32ncurses5 
ia32-libs

So far my realplayer has been working fine :)

credit:
[http://narnia.cs.ttu.edu/drupal/node/113](http://narnia.cs.ttu.edu/drupal/node/113)

@@@@@@@

I tried the install after checking that all the packages you (and the web site) suggested were in place. I tried the deb package from [www.real.com/linux](www.real.com/linux) having it execute the Package Installer. It ran but ended with the error -

Status; Error: Wrong architecture 'I386'

 I'm using the 8.04 64 bit Ubuntu with a Core 2 Quad Intel processor. I have another 32 bit app that works fine.

Any ideas??

Stephen

---

