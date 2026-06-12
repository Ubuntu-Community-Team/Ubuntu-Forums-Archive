---
title: "has anyone managed to get Handbrake going on natty?"
date: 2011-04-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by shantiq on 2011-04-09
[FONT="Comic Sans MS"]myself not as yet    although fine as ```
HandBrakeCLI
```from command line

synaptic giving me this message when i try for the gui

```
handbrake-gtk:
 Depends: libwebkit-1.0-2  but it is not installable
```



i took this route

```
sudo add-apt-repository ppa:stebbins/handbrake-releases 

sudo apt-get update
sudo apt-get install handbrake-gtk
```


any help welcome[/FONT]

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-04-09
There's something wrong with your post. Your text appears in comic sans.

---

### Post by shantiq on 2011-04-09
sorry?   how is that answering my question   found your intervention a bit rude and a waste of my time so please actually help me if you know about this  


comic sans is one of the fonts provided here i happen to like it  :KS

---

### Post by MadCow108 on 2011-04-09
libwebkit-1.0-2 does not exist in natty.
you'll have to replace libwebkit-1.0-2 dependency with libwebkitgtk-3.0-0 in debian/control and hope it still works.
or wait until the ppa sorts it out and publishes a natty version.

---

### Post by shantiq on 2011-04-09
thanx madcow  any chance you could tell me a bit more about steps to take; i am not sure how to do this






by default natty has libwebkitgk-1.0-0 installed and libwebkitgtk-3.0-0 present but not installed   

  thanx   shan

---

### Post by Wobblybob on 2011-04-09
Yes but it's a bit of a odd workaround but it works on my install which is up to date as of Wed 6th Apr, I downloaded the Maverick .deb called handbrake-gtk_0.9.5ppa1~maverick1_amd64 from here I am using natty64bit

[[COLOR="Navy"]https://edge.launchpad.net/~stebbins/+archive/handbrake-releases/+packages[/COLOR]]("https://edge.launchpad.net/~stebbins/+archive/handbrake-releases/+packages")

when you try and install this .deb you get a dependency error for libwebkit-1.0-2 which is not going to be installed and as far as I can see is now renamed as libwebkitgtk and on my system ia at version 3

I opened the above package with the archive manager and extracted it to a directory called handbrake-gtk_0.9.5_natty_amd64. There are now 2 directories within this called DEBIAN and usr, in DEBIAN is a file called control. Open that with a text editor and look for this section 

Depends: libatk1.0-0 (>= 1.29.3), libbz2-1.0, libc6 (>= 2.7), libcairo2 (>= 1.2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libgcc1 (>= 1:4.1.1), libgdk-pixbuf2.0-0 (>= 2.21.6), libglib2.0-0 (>= 2.16.0), libgstreamer-plugins-base0.10-0 (>= 0.10.12), libgstreamer0.10-0 (>= 0.10.0), libgtk2.0-0 (>= 2.18.0), libgudev-1.0-0 (>= 147), libnotify1 (>= 0.5.0), libnotify1-gtk2.10, libpango1.0-0 (>= 1.18.0), libpng12-0 (>= 1.2.13-4), libstdc++6 (>= 4.4.0), zlib1g (>= 1:1.2.3.3.dfsg), libwebkit-1.0-2

and change the last option from libwebkit-1.0-2 to libwebkitgtk-3.0-0 and resave. Now open a Terminal and type;

**$ dpkg-deb --build /path_to_handbrake_directory/handbrake-gtk_0.9.5_natty_amd64**

This will produce a .deb called handbrake-gtk_0.9.5_natty_amd64.deb which you can double click on to install.

---

### Post by MadCow108 on 2011-04-09
if you have the time better rebuild the package, just in case webkit 1.3 is not binary compatible with webkit 1.2

```
sudo apt-get install devscripts equivs

#get source
dget -ux https://launchpad.net/~stebbins/+archive/handbrake-releases/+files/handbrake_0.9.5ppa1~maverick1.dsc
cd handbrake-0.9.5ppa1~maverick1

#replace webkit dependency in debian/control line 22

#install build dependencies
sudo mk-build-deps -i -r

#build package
debuild -us -uc

#here are the packages, install with e.g. gdebi or dpkg -i
ls -ltr ../*deb
```

---

### Post by shantiq on 2011-04-09
thank you to both of you guys will try all this


in the meantime spent the morning learning 
HandBrakeCLI  and some fun it is good guide [here]("https://trac.handbrake.fr/wiki/CLIGuide")

                             ========================================

ok Wobblybob but the file called control is in DEBIAN on my system



ok need this ```
sudo apt-get install build-essential autoconf automake autotools-dev dh-make debhelper devscripts fakeroot xutils lintian pbuilder

```to run  ```
dpkg-deb --build /path_to_handbrake_directory/handbrake-gtk_0.9.5_natty_amd64
```



but now i get  ```
Error: Dependency is not satisfiable: libwebkit-3.0-0

```  although i have all the ones you see on image



========================================

madcow looks brill will try that too

---

### Post by MadCow108 on 2011-04-09
> **shantiq said:**
> 

but now i get  ```
Error: Dependency is not satisfiable: libwebkit-3.0-0

```  although i have all the ones you see on image


its libwebkit**gtk**-3.0-0


> ========================================

madcow looks brill got stuck

where exactly?
editing the control is replacing:
Depends: ${shlibs:Depends}, ${misc:Depends}, libwebkit-1.0-2, libnotify1
with
Depends: ${shlibs:Depends}, ${misc:Depends}, libwebkitgtk-3.0-0, libnotify1

---

### Post by shantiq on 2011-04-09
> its libwebkit**gtk**-3.0-0
:KS:KS    and there you go i misread it   thanx for pointing it out  sorted


========================

[B][U]Working deb packages:
[/U][/B]

Again thanx to both of you    if anyone wants 	**handbrake-cli and -gtk for Natty Narwhal.zip  [COLOR="Red"]64-bit[/COLOR]** ready-made as 2 debs (built with madcow's [instructions]("http://ubuntuforums.org/showpost.php?p=10656152&postcount=7")) collect it through 

[URL="http://ubuntuone.com/p/nrW/"][COLOR="Blue"]**Ubuntu One**[/COLOR]
[/URL] 

**make sure** **[COLOR="Red"]you have allowed libwebkitgtk-3.0-0 in your synaptic first[/COLOR]**

==============================================    

PS:Great thinking Ondope; never thought of using this

---

### Post by shantiq on 2011-04-10
==========

---

### Post by ondope on 2011-04-20
Hi, I have uploaded the debs for x86_64+natty on my ubuntu one account:

[Handbrake-gtk]("http://ubuntuone.com/p/nlA/")
[Handbrake-cli]("http://ubuntuone.com/p/nlD/")

these are without libwebkit3 as a dependency, you should install libwebkitgtk3.0-0 first, then these.

---

### Post by JohnAStebbins on 2011-04-20
I haven't added natty to the HandBrake 0.9.5 PPA yet.  If you want to play with pre-release code (and apparently you do since you are using Natty), I suggest using the HandBrake nightly builds PPA which has natty packages.

[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by donniezazen on 2011-04-26
> **JohnAStebbins said:**
> I haven't added natty to the HandBrake 0.9.5 PPA yet.  If you want to play with pre-release code (and apparently you do since you are using Natty), I suggest using the HandBrake nightly builds PPA which has natty packages.

[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)


Thanks for PPA. Saved me a lot of hack.

---

