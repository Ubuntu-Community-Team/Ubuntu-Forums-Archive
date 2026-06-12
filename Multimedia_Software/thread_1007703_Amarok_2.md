---
title: "Amarok 2"
date: 2008-12-10
forum: Multimedia Software
---

### Post by Squegee on 2008-12-10
Amarok 2 has just been released and and I am unable to get the package on my Kubuntu computer. I am currently using Amarok Nightly which is another version but has a lot of bugs. I followed the download link given on the Amarok web page to the Kubuntu website where it describes how to add the line of text given to the repositories and then the package should be available, but it isn't. I have no idea what to do and any help would be greatly appreciated. Thanks

---

### Post by benerivo on 2008-12-10
If you have checked that the repository line given on the kubuntu page is actually in your sources by looking in ```
/etc/apt/sources.list
``` then do ```
sudo apt-get update
```then try ```
apt-cache search amarok
```which should return all packages with amarok in the name or description. I think the package has been named amarok-kde4.

---

### Post by binbash on 2008-12-10
add this to your sources.list : 

deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main

remove amarok if you have, then 

sudo apt-get update && sudo apt-get install amarok-kde4

---

### Post by Squegee on 2008-12-10
Thanks for your help, the main thing was that i didn't know i had to uninstall Amarok to be able to install Amarok 2

---

### Post by kiisu on 2008-12-11
I just added the sources, then did sudo apt-get install amarok-kde4 .

It removed the old Amarok as it installed. No problems. Looks great, need some time to play with it.

---

### Post by Balinsky on 2008-12-27
i had more trouble installing in kubuntu today than xubuntu yesterday. im not really sold on adept

---

