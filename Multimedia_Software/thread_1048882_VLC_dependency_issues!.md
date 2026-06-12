---
title: "VLC dependency issues!"
date: 2009-01-23
forum: Multimedia Software
---

### Post by dzinae on 2009-01-23
Perhaps I should be posting this in Absolute Beginner Talk, but I hoped to be topic conscious and post it here first instead.  I just finished installing Xubuntu 8.04 on my little sister's computer.  Figured that Xfce was the best way to go, since she's got a little junk box for a computer, and it barely runs anything as it is.  It works beautifully so far!  

I've been trying to download and install vlc, and all the codecs required for her to play mp3s, and whatnot on her computer, but have come up with a few issues.  There is absolutely no way I can hook her up to the internet.  So, instead I attempted to download a .deb for VLC and install it on her computer.  

I've discovered I'm screwed for the dependencies.  I'm a complete Ubuntu newbie, so I'm unsure how to procede.  I can certainly hunt down each little dependency and download them... but I've no idea which ones I need, and where to find them.  Nor do I know how to put them together.  

Just hoping someone can give me some helpful advice, or point me towards an 'installer' that's got all the goodies required already included.  If I'm in the wrong subforum, feel free to chew me out as I'm still a first-posting newbie.  

Thank ya kindly.

---

### Post by jrusso2 on 2009-01-23
VLC is in the repository.  Use synpatic and it will add the dependency for you.

You probably need to add like the mediabuntu repository 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by dzinae on 2009-01-23
> **jrusso2 said:**
> VLC is in the repository.  Use synpatic and it will add the dependency for you.

You probably need to add like the mediabuntu repository 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I cannot hook her computer up to the internet at all, ever... ever!  I can only get online on my own computer, and download the .deb files and transfer them via my flash drive.  That's the trouble.  If I could just go to Synaptic and download it, I would.

Thank you, though.  If you could even show me where to get a list of all the dependencies, I might be able to just plug away at downloading them individually.

---

### Post by jrusso2 on 2009-01-23
check the website and see if the dependency are listed.   It has a fair amount of them.

---

### Post by mc4man on 2009-01-24
There are several ways, here's one. Does require either a flash or usb ext. drive or a 2nd cdrom that can write to a cd . (I think usb/flash is quicker and easier.
 Take the livecd you installed Xubuntu 8.04 with and boot up to the livecd on a box with internet. (you pick the try without changing..., option.

Go to System, Admin..., software sources, ubuntu software and uncheck the cdrom box (1st. 4 boxes should be checked.

Because your on 8.04 there are medibuntu versions of some of needed packages. **Before** installing vlc add medibuntu as a repo. See below for how. 

Then install vlc and anything else you want. When done go to places -> computer -> filesystem ->  /var/cache/apt/archives. Copy all the .debs or just copy the archives folder itself. There'll be a pop up copy error box, click 'skip all' and then don't worry about it. ( if you copy the whole folder.

Transfer the folder to the other box and put in home folder.
From the terminal (use name of folder, showing 'archives'

```
cd ./archives && sudo dpkg -i *.deb
```


When your done you can delete the archives folder in home.

Edit;

to add medibuntu, libdvdcss2,  in a terminal
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

```
sudo apt-get install libdvdcss2
```

---

### Post by dzinae on 2009-01-24
You're wonderful!  I'm going to try this today.  Thank you very much.

---

### Post by mc4man on 2009-01-24
> I'm going to try this toda
Let me know if you have an difficulties, does work, I tested it fully a while back for someone else.

There's also something like this (I like above for your situation, I believe below requires a linux install the same as target install

[http://keryx.betaserver.org/](http://keryx.betaserver.org/)

---

