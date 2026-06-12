---
title: "gimp 2.10.??"
date: 2019-11-23
forum: Multimedia Software
---

### Post by jgw on 2019-11-23
I am trying to get gimp up and running.  I have had it on my machine for a long time and now its upgraded to the latest and greatest.  However, I am not convinced its right.  If I goto ubuntu software they have two gimps.  One is snap and one is not.  Ubuntu software tells me that the non-snap version is installed (v. 2.10.14) and the snap version is not.  When I do a search of my home directory I find that there is a pile of gimp stuff in my snap directories as well as elsewhere.   

So, my first question does this seem to be right?  (gimp in both snap and non-snap whilst non snap is the one installed).  My thought is that, perhaps, I should just delete ALL gimp stuff, regardless of location and then re-install the complete package.  I suspect that the easiest may be to install the non-snap version but, then again, maybe not.  

this all started with trying to install a couple of addons.  There were indications that installing these, with a snap installation, may not be the easiest way to go.  The problem is that a lot of the instructions were before 2.10 was out so those may not actually apply.

Anyway, I would appreciate any thoughts on this one - thank you...........

---

### Post by SeijiSensei on 2019-11-23
I have avoided all snap packages and will continue to do so. 

Using the latest repository version, I have a .config/GIMP/2.10 directory in my home directory.  I have no other GIMP-related files in my $HOME.

---

### Post by deadflowr on 2019-11-24
If you had the snap version, but don't any longer, then just delete the ~/snap/gimp folder.
You can double check to see if it is indeed not installed with
```
snap list
```
anything listed is installed.
As far as I know snaps work like other packaging/software where if something goes into the home folder for it it does not remove it when the package is uninstalled.

---

### Post by jgw on 2019-12-15
Thank you for the response.  

I did the snap list and got:
```
greg@gregdown:~$ snap list
Name                  Version                     Rev   Tracking  Publisher          Notes
canonical-livepatch   9.4.8                       90    stable    canonical&#10003;         -
core                  16-2.42.4                   8213  stable    canonical&#10003;         core
core18                20191126                    1279  stable    canonical&#10003;         base
gedit                 3.34.0+git15.9a0dbede2      371   stable    canonical&#10003;         -
gnome-3-26-1604       3.26.0.20191114             98    stable/…  canonical&#10003;         -
gnome-3-28-1804       3.28.0-16-g27c9498.27c9498  110   stable    canonical&#10003;         -
gnome-calculator      3.34.1+git1.d34dc842        544   stable/…  canonical&#10003;         -
gnome-characters      v3.32.1+git2.3367201        367   stable/…  canonical&#10003;         -
gnome-logs            3.34.0                      81    stable/…  canonical&#10003;         -
gnome-system-monitor  3.32.1-3-g0ea89b4922        111   stable/…  canonical&#10003;         -
googletools-desktop   1.0.0                       1     stable    sebastianbrunnert  -
gtk-common-themes     0.1-25-gcc83164             1353  stable/…  canonical&#10003;         -
guvcview              2.0.6+pkg-f796              81    stable    brlin              -
hello-world           6.4                         29    stable    canonical&#10003;         -
yakyak                1.5.3                       45    stable    snapcrafters       -
greg@gregdown:~$ 

```

I, obviously, have a lot of snap stuff.  If I delete it I fear a mess.  I can look up, and reinstall stuff like guvcview, etc but the gnome stuff confuses.

Thoughts?

---

### Post by deadflowr on 2019-12-15
The logs,calculator,characters, and system-monitor snaps are the snap versions of those packages.
(These are now the defaults included in Ubuntu.)

The gnome-3-26/3-28 snaps contain the gnome stacks any gnome snap, such as those listed, might require to run properly.

And along with those gnome stack snaps you can include the gtk-common-themes as snaps do not have proper access to the system themes.
The themes snap mitigates this issue and allow snaps to use the most common themes Ubuntu ships with.
That basically means snaps can have a consistent look with the rest of the system.

Sorry that probably did nothing but add to the confusion.

But getting back to gimp, you have no gimp snap installed so you can just trash the ~/snap/gimp folder without remorse.

---

### Post by jgw on 2019-12-20
Thank you for the response.

I will get rid of the /snap/gimp thing.  Is there a way to make sure I am not adding a snap thing?  (I have had other problems with snap - not exactly sure just what it is)

I will mark this as solved......

---

### Post by deadflowr on 2019-12-20
>  Is there a way to make sure I am not adding a snap thing?
Easy as removing the package gnome-software-plugin-snap.
That's the package that allows snaps to be available in the software store.
In this way any snaps you want would have to be installed using snap cli.
(So you'd have to know if you installed any)

More tedious if you want to not have any snaps is to remove the snaps you have in the snap list one by one and then remove the snapd apt package.

---

