---
title: "mythtv problem of colors in live tv"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by fededs83 on 2007-05-01
Hi guys,
I'm running mythtv with an hauppauge pvr usb 2 and an ati radeon x1300. All works fine: lirc is ok, live tv is ok music is ok i have only one big problem.
The problem is this: when I watch live tv I have some color problem. I have blue instead of red. All people's skin is blue!!!
Do you know how can I fix the problem?
I tried to modify color and hue settings in mythtv setup but it doesn't work!
The strange thing is that if I watch the preview of channels that I have registered the colors are ok but If i watch  it on fullscreen the colors are wrong!
I read that's a fglrx bug in fact if I use the vesa dirver all is ok but the quality is worste. Is there a solution?
Excuse me for my bad english!
Thank you
Fede

---

### Post by superm1 on 2007-05-01
There is a deb on launchpad that can be used as a workaround for this fglrx bug.  It compiles mythtv with a specific hack to change video overlays.  

[http://librarian.launchpad.net/7388614/libmyth-0.20_0.20-svn20070122-0.0ubuntu6_i386.deb](http://librarian.launchpad.net/7388614/libmyth-0.20_0.20-svn20070122-0.0ubuntu6_i386.deb)

---

### Post by fededs83 on 2007-05-01
What have I to do? After the installation of your .deb package have I to reinstall mythtv? I didn't compile mythtv I installed through the repo and I think I'm not good enough to compile mythtv.
Can you explaine a little more?
Thanks a lot!
Fede

---

### Post by superm1 on 2007-05-01
> **fededs83 said:**
> What have I to do? After the installation of your .deb package have I to reinstall mythtv? I didn't compile mythtv I installed through the repo and I think I'm not good enough to compile mythtv.
Can you explaine a little more?
Thanks a lot!
Fede
Sorry should have explained better.  That deb wasn't compiled by me (but I might start providing a special deb with mythtv if this fglrx bug isn't resolved soon).
If you are on a GUI install (and have gnome or kde), download it and double click.

If not, then download it, and install with
sudo dpkg -i DEB
where DEB is the name of the file.

Note, that you will need to lock this version of the package in synaptic if you are on a GUI or with an apt pin elsewise, since it will conflict with the one that is in the repos.  (You dont need to do this immediately, make sure it works for you before looking into it)

---

### Post by fededs83 on 2007-05-02
thanks all works great!!
fede

---

### Post by sdyson on 2007-05-07
Cheers, worked for me too!

---

### Post by djhworld on 2007-07-05
Excellent, a big thanks to "superm1" for solving this!

You wouldn't believe how many hours I've spent trawling google with variations of "mythTV blue skin", "mythTV blue faces" 

etc!

Solved now though :-).

---

### Post by _Jacky_ on 2007-08-30
I have a similar problem, yet not with myth tv but mplayer. could it be the same issue? i also have the fglrx driver installed..

---

### Post by superm1 on 2007-08-30
> **_Jacky_ said:**
> I have a similar problem, yet not with myth tv but mplayer. could it be the same issue? i also have the fglrx driver installed..
Most likely.  It affects any xv apps.

---

### Post by saand1 on 2007-09-04
Thanks superm1 for solving this!
Like many other I spent a long time searching google to fix this issue until your solution fixed the problem.

I have upgraded to mythtv 0.20.2 and the problem has come back . 
Is there a setting in the new mythtv version to get around this or is there an new deb package to get around the fglrx bug mentioned in the post by superm1

---

### Post by jb5 on 2007-10-04
I'm getting the blue skin problem also.
Live TV; recordings; or DVDs played through MythTV - blue skin.
Thumbnail previews are unaffected and play with correct colour response.

Feisty 7.04 (64bit) 
MythTV 0.20.20070821-1
Hauppauge - Nova-T-500
ATI X1600pro


If I disable the ATI restricted driver the colours are ok in live TV but the picture is "jerky".

With the ATI restricted driver running the picture motion is smooth but the colours are inverted.

Anybody know a solution to this problem for 64bit installs of feisty?

NB Totem movie player plays DVDs ok (without colour problems), after installing the restricted codecs package.

---

### Post by jb5 on 2007-10-05
This web page may help someone in a similar position [[COLOR="Red"]Ati Feisty[/COLOR] ](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)
Unfortunately with my system / specs I'm up to date

```
  
Reading state information... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6334 (8.34.8)
 

```

There are later versions of fglrx which may sort out the problems for people with other cards.

---

### Post by jb5 on 2007-10-09
I gave the above guide another go, this time following the *manual method*.

This time the trick worked and the TV pictures have the correct colours!

One point to note is that I **had** to issue the ```
sudo aticonfig --initial
``` command when configuring the driver, as the alternative didn't work for me.

```
jb@eric:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6849 Release

```

HTH

---

### Post by fededs83 on 2007-10-22
now I'm under "mythubuntu" and I have the same trouble of blue skin. I tried to install that library but it's older than mythubuntu's one.
How can I do? where can I find the new version of that library?
thanks!
fede

---

### Post by fusionisthefuture on 2007-10-28
im having the same problems as the other newer posts in this forum, theres no way to install that deb package that superm1 posted, now that the version of mythtv is too new.  it says that theres already a newer version installed in the gui mode, and when you do dpkg, it says

```
sudo dpkg -i /home/user/Desktop/libmyth-0.20_0.20-svn20070122-0.0ubuntu6_i386.deb 
Selecting previously deselected package libmyth-0.20.
(Reading database ... 91604 files and directories currently installed.)
Unpacking libmyth-0.20 (from .../libmyth-0.20_0.20-svn20070122-0.0ubuntu6_i386.deb) ...
dpkg: dependency problems prevent configuration of libmyth-0.20:
 libmyth-0.20 depends on libartsc0 (>= 1.5.0-1); however:
  Package libartsc0 is not installed.
 libmyth-0.20 depends on libjack0.100.0-0 (>= 0.102.20); however:
  Package libjack0.100.0-0 is not installed.
 libmyth-0.20 depends on liblame0 (>= 3.96.1); however:
  Package liblame0 is not installed.
 libmyth-0.20 depends on libqt3-mt (>= 3:3.3.8really3.3.7); however:
  Package libqt3-mt is not installed.
 libmyth-0.20 depends on libxvmc1; however:
  Package libxvmc1 is not installed.
 libmyth-0.20 depends on libqt3-mt-mysql | libqt3c102-mt-mysql; however:
  Package libqt3-mt-mysql is not installed.
  Package libqt3c102-mt-mysql is not installed.
dpkg: error processing libmyth-0.20 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libmyth-0.20

```
any ideas superm1?

thanks alot
-arne

---

### Post by ryth on 2007-11-18
I have this same problem, running 0.20.2 and Gutsy-adm64 with an ATI X1950.  Anyone find any sort of work around yet?

Any suggestions would be greatly appreciated.

R.

---

### Post by fusionisthefuture on 2007-11-18
its that damn x1950 pro... whyd i have to get the ONLY old videocard with problems... :*(

---

### Post by usererror on 2008-05-28
I know this is a really old post, but the blue screen stuff is from an incorrect driver.

I ditched my ATI X1300 for an old NVidia card with 64MB video ram and it works great!

---

### Post by fusionisthefuture on 2008-05-28
i think we all realize that nvidia is the superior linux video cards, we just dont want to have to buy new ones.

---

