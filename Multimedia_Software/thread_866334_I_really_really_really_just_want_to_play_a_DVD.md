---
title: "I really really really just want to play a DVD"
date: 2008-07-21
forum: Multimedia Software
---

### Post by EVPS on 2008-07-21
I have searched tirelessly for days now looking for instructions on making Totem play dvds I have installed every package going to try and help me play a dvd.

I have finally got down to the point where I get a message asking if I am trying to play encrypted dvds without libdvdcss.....I can't find where to get this although I have installed the xine version of totem which i thought came with all the codecs I need.  I can play some none commercial dvds, so something must be working.  I am on Ubuntu Gutsy Gibbon and I am losing the will, please if anyone can help me I would be most grateful.

I have used the terminal to try and find libdvdcss2 and it says that its not there but another file links to it but doesnt tell me the name of the other file. I am so confused, I have been at the computer for hours now trying to do this, I'm sure my linux book made this sound easy.

Thank you for any help,

James

---

### Post by issih on 2008-07-21
go to add/remove, install ubuntu restricted extras (note the legality of that depends on where you live)

After that all should be fine.

In general though if you need to install a package, you can just open up the synaptic package manager and search for its name (or something that seems plausible). Then just select it and hit apply.

In this case however doing as I suggested is probably best as it will solve a few other media related hiccups for you.

Thinking about it, that assumes you are using hardy heron, if not, this page may be of more help:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Prefix100 on 2008-07-21
don't use totem. Use vlc and install the needed packages from the medibuntu repo.

---

### Post by ktrnka on 2008-07-21
Here's the link to download libdvdcss2.

[http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb]("http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb")

---

### Post by mc4100 on 2008-07-21
To get libdvdcss2, first, open a terminal ( Applications -> Accessories -> Terminal)

And copy and paste this in (Select everything in the box, press CTRL+C, go to the terminal, right click and press "Paste")
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
 (It will ask for you're password, type that in also  -- remember, it will stay blank and won't show any *** like when you log-in.)

And then...
```
sudo apt-get update && sudo apt-get install libdvdcss2
```
This allows you to read encrypted DVD's.

Now, I don't know if these are needed, since you said you can already play *some* DVD's, but try it anyway: 
let's get "libdvdnav4" and "libdvdread3", these are found in Ubuntu's 'universe' repo...

Open up "Software Sources" ...
(System -> Administration -> Software Sources)
And tick the box beside "Community Maintained Open Source Software (universe)"
Then close, a box will pop-up, and you'll press "reload".

Open another "terminal", and type...
```
sudo apt-get install libdvdnav4 && sudo apt-get install libdvdread3
```

Now, try your DVD again. It should work.

---

### Post by ericartman on 2008-07-21
I've used [http://quickstart.phpbb.net/](http://quickstart.phpbb.net/) since feisty and haven't had any problem yet

Cart

---

