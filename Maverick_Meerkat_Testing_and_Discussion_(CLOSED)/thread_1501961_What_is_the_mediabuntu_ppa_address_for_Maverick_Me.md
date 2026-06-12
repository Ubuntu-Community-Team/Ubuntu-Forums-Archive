---
title: "What is the mediabuntu ppa address for Maverick Meerkat?"
date: 2010-06-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-06-04
Thanks in advance.

This command doesn't work well anymore
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update && sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo aptitude install ubuntu-restricted-extras avidemux wireshark axel axel-kapt gnome-alsamixer amule p7zip-full p7zip-rar gparted startupmanager acpi gnome-device-manager apt-p2p mplayer smplayer gnome-mplayer wine human-theme x264 python python-gtk2 intltool gettext nfoview assogiate fusion-icon simple-ccsm emerald vlc cheese compiz subversion compiz-fusion-plugins-extra gmountiso rar apache2.2-bin libapache2-mod-dnssd git-core gimp w32codecs alsa-oss shutter faac gnome-themes-more faad flashplugin-nonfree gstreamer0.10-ffmpeg samba gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse git-core wine gstreamer0.10-plugins-ugly gshare gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs unrar && sudo aptitude install xfonts-terminus compiz-fusion-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool libgl1-mesa-dev and libglu1-mesa-dev 

```

And also fglrx doesn't work.

---

### Post by ronacc on 2010-06-04
there isn't a medibuntu repo for maverick yet , hand add it to your sources.list and use the lucid repo .

---

### Post by aviramof on 2010-06-04
lucid repo does't work do you have a working address?

---

### Post by wojox on 2010-06-04
Look in my signature.

---

### Post by ronacc on 2010-06-04
try manualy downloading the files you need and install with dpkg . I juat checked and was able to d/l a file ok , I'm not on my test box right now so I cant post the sources list entry but here is a link direct to the medibuntu lucid repo [http://packages.medibuntu.org/lucid/index.html](http://packages.medibuntu.org/lucid/index.html)

---

### Post by aviramof on 2010-06-04
> **wojox said:**
> Look in my signature.

Thanks i think it worked.

By the way does any body know when can we expect a working fglrx driver? and where is the keyring gui shortcut(seashore?)?

---

### Post by taavikko on 2010-06-05
What's in the medibuntu repos that requires having it?

/* codecs isn't a valid answer */

---

### Post by aviramof on 2010-06-05
Basically all the non-free softwares like movies codecs and etc.

[http://medibuntu.org/](http://medibuntu.org/)

---

### Post by ronacc on 2010-06-05
also google earth , that is a must have .

---

### Post by garvinrick4 on 2010-06-06
> **ronacc said:**
> also google earth , that is a must have .
Just in case of a new Maverick user is looking.

                                 Add first line to sources.list manually or add in Software Sources.

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free  
 

 Code in Terminal for keyring.

```
sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update 

```

---

### Post by ranch hand on 2010-06-06
> **garvinrick4 said:**
> Just in case of a new Maverick user is looking.

                                 Add first line to sources.list or add in Software Sources.
 

 deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free  
 

 Code in Terminal for keyring.

```
sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring &&sudo apt-get --quiet update 

```
OK, I do not understand this at all.   I changed my upgrade to 10.10 OS mediubuntu to maverick when the toolchain went up.

I have added it to my clean install.

I have no trouble with it at all.

Am I in some kind of alternative universe or are all of you?

---

### Post by ronacc on 2010-06-06
None of us or else all of us , If you go to medibuntu.org and look at their repoaitories there isn't one for maverick but if you use maverick in your software-sources it works , they must have something at medibuntu that translates apt calls to maverick to the lucid repo , if you load the lucid repo in a browser and then change to maverick you get a 404 not-found error .

---

### Post by ranch hand on 2010-06-06
Hmm, interesting.  I have never tried looking at a repo on a browser.  Probably should sometime.

---

### Post by wilee-nilee on 2010-06-06
> **ranch hand said:**
> Hmm, interesting.  I have never tried looking at a repo on a browser.  Probably should sometime.

I like alternative universe idea though.;) not that you are it just sounds funny. I used the wojox link and have no problem.

---

### Post by ranch hand on 2010-06-06
Well you never know when you may have wandered down the wrong leg in the trousers of time.

---

### Post by garvinrick4 on 2010-06-07
> **ronacc said:**
> None of us or else all of us , If you go to medibuntu.org and look at their repoaitories there isn't one for maverick but if you use maverick in your software-sources it works , they must have something at medibuntu that translates apt calls to maverick to the lucid repo , if you load the lucid repo in a browser and then change to maverick you get a 404 not-found error .
Thanks for having my back there ronacc,appreciate it.

---

### Post by DevHead on 2010-09-13
Any updates on this PPA?

---

### Post by coffeecat on 2010-09-13
> **DevHead said:**
> Any updates on this PPA?

It's not actually a PPA - it was the OP who called it that. Here's the Medibuntu home page:

[http://medibuntu.org/](http://medibuntu.org/)

If you click on Packages you'll see - at the time of posting - that there is no Maverick repo, but as others have said you can use the Lucid repo for now. Or simply download the deb packages for the apps you want - they're easily found in the website - and install them manually.

If I remember correctly, Medibuntu doesn't add a version repo until that version goes final.

**Edit:** hmm, I must be wrong about that last bit. On the Packages page it gives dates for adding Karmic and Lucid at the beginning of the development cycle. **Very** early for Lucid. Oh well. :?

---

### Post by DevHead on 2010-09-13
Thanks for the info.  I'll just d'load and install the .debs from there.

---

### Post by dutchhome on 2010-09-13
For now, just change the $(lsb_release -cs) to lucid and the install is fine:

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list [http://www.medibuntu.org/sources.list.d/lucid.list](http://www.medibuntu.org/sources.list.d/lucid.list) && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

---

