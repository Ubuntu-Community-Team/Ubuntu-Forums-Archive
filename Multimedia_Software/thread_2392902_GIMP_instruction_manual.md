---
title: "GIMP instruction manual"
date: 2018-05-26
forum: Multimedia Software
---

### Post by satimis on 2018-05-26
Hi all,

Please advise where can I find GIMP instruction manual describing the tool list and their function?  The setting manual of GIMP e.g. to increase the size of the tool icons.

Thanks in advance.

Regards
satimis

---

### Post by monkeybrain20122 on 2018-05-26
If you haven't installed synaptic, install it
```

sudo apt install synaptic
```

It is a very convenient gui package manager that many new users don't know because of the crappy app store installed by default (the listing is just a small fraction of what are available in the repo) It allows you to search for packages and install/uninstal them rather than cut and pasting random sudo apt install blah blah (how do you know the actual name of the package and what related ones are available?  There is apt-cache search but this is much better)

Now open synaptic and look for gimp and you will find gimp-help in different languages. Choose the one you want,

---

### Post by satimis on 2018-05-27
> **monkeybrain20122 said:**
> If you haven't installed synaptic, install it
```

sudo apt install synaptic
```

It is a very convenient gui package manager that many new users don't know because of the crappy app store installed by default (the listing is just a small fraction of what are available in the repo) It allows you to search for packages and install/uninstal them rather than cut and pasting random sudo apt install blah blah (how do you know the actual name of the package and what related ones are available?  There is apt-cache search but this is much better)

Now open synaptic and look for gimp and you will find gimp-help in different languages. Choose the one you want,

Thanks for your help.

Start synaptic

-> search for gimp
-> gimp -> gimp-help-en

Documentation for the GIMP (English)
[Get Screenshot][Get Changelog][Visit Homepage]

-> [Get Screenshot]
An empty screen

-> [Get Changelog]
Complete changelog of the latest version:

-> [Visit Homepage]
Bring me to;
[https://www.gimp.org/](https://www.gimp.org/) (GIMP website)

Actually what I need are basic information of GIMP

1) Tool list on the screen and their basic function rather than moving mouse cursor over them to read
2) How to increase the size of the tool icons ?
3) What are the tiny icons on the right menu under 2.Hardness 050 (51x51) ?

Before posting I have had searching on Internet without result. What I found on Internet were the application of GIMP including Youtube video.  I found many of them.

Regards
satimis

---

### Post by kazakore on 2018-05-27
[https://docs.gimp.org/2.8/en/](https://docs.gimp.org/2.8/en/)

Or if you've installed the latest version from the Gimp ppa then

[https://docs.gimp.org/2.10/en/](https://docs.gimp.org/2.10/en/)


You can definitely find all your answers in there!


Alternatively have you tried pressing F1 when GIMP is open?

---

### Post by satimis on 2018-05-27
> **kazakore said:**
> [https://docs.gimp.org/2.8/en/](https://docs.gimp.org/2.8/en/)

Or if you've installed the latest version from the Gimp ppa then

[https://docs.gimp.org/2.10/en/](https://docs.gimp.org/2.10/en/)


You can definitely find all your answers in there!


Alternatively have you tried pressing F1 when GIMP is open?
Hi,

Thanks for your advice

-> F1
GIMP user manual is missing```

The GIMP user manual is not installed on your computer.
You may either install the additional help package or change your preferences to use the online version.

```

Icons are controlled by Theme which is operated by gtkrc and icons in combination.  Is there any way changing the content of gtkrc to increase the icon size?  Copy of gtkrc is attached to this post.

Thanks

Edit:
===
Just found following article:-
GIMP Basics
[https://coma4317.files.wordpress.com/2012/08/gimpbasics.pdf](https://coma4317.files.wordpress.com/2012/08/gimpbasics.pdf)

It is useful to me.

Regards
satimis

---

### Post by #&amp;thj^% on 2018-05-27
> **satimis said:**
> Hi all,

Please advise where can I find GIMP instruction manual describing the tool list and their function?  The setting manual of GIMP e.g. to increase the size of the tool icons.

Thanks in advance.

Regards
satimis

You can use Kevin Payne's themes with big icons: these are available and found here: [https://www.gimp-forum.net/Thread-GIMP-2-8-Large-size-Icons-Themes](https://www.gimp-forum.net/Thread-GIMP-2-8-Large-size-Icons-Themes)
I have about 4 .gz man pages if you need them.

---

### Post by satimis on 2018-05-27
> **1fallen said:**
> You can use Kevin Payne's themes with big icons: these are available and found here: [https://www.gimp-forum.net/Thread-GIMP-2-8-Large-size-Icons-Themes](https://www.gimp-forum.net/Thread-GIMP-2-8-Large-size-Icons-Themes)
I have about 4 .gz man pages if you need them.
Thanks for your advice.

OK, I have Ubuntu 16.04 VM (VirtualBox) running.  I'll try "GIMP 2.8 Large size Icons Themes" on it.

There are 4 Theme folders:
1)
Preference -> Theme
Theme Folder```

Default /usr/share/gimp/2.0/themes/Default
Small  /usr/share/gimp/2.0/themes/Small

```
2)
Preference -> Folders -> Themes
Folder```

/home/satimis/.gimp-2.8/themes
/usr/share/gimp/2.0/themes

```

Which of them shall I use to store the unpackes theme?  I'm running GIMP 2.8 here

Besides I have Ubuntu 18.04 VM.  Also I can try GIMP2.10 on it.  But the drawback is I can't check;
Settings -> Display
[check] Enable 3D Acceleration

Otherwise Ubuntu 18.04 VM can't start.  I can't find out its cause.  Will GIMP works without problem?

Regards
satimis

---

### Post by #&amp;thj^% on 2018-05-27
If it is just the bigger Icon size you want you can alter them with going to Edit>>Preferences>>Box will open select **"Icon Theme"** click or highlilte that and at the bottom you should see a dropdown box probably reading <guess icon size> change that to <Custom icon size> move the slider below to your preference

---

### Post by satimis on 2018-05-27
> **1fallen said:**
> If it is just the bigger Icon size you want you can alter them with going to Edit>>Preferences>>Box will open select **"Icon Theme"** click or highlilte that and at the bottom you should see a dropdown box probably reading <guess icon size> change that to <Custom icon size> move the slider below to your preference
Hi,

My Preferences looks completely different from yours.  I'm running GIMP 2.8 version.  Unfortunately I couldn't upload the screenshot here which is a .png file of 194.7kB.

-> Manage Attachment -> Add Files -> Choose File -> Upload
But the .png file can't be uploaded.  I don't know why.  I have tried multiple times.

Besides there are previous upload old files there which I have been used in the past.  How to delete them?

Regards
satimis

---

### Post by #&amp;thj^% on 2018-05-28
Sorry I was on Arch yesterday so I also was surprised to see the difference's in the "UI"
Ok then, I just extracted them to "/usr/share/gimp/2.0/themes" 
And my version is: 
```
apt policy gimp
gimp:
  Installed: 2.8.22-1
  Candidate: 2.8.22-1
  Version table:
 *** 2.8.22-1 500
        500 http://archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        100 /var/lib/dpkg/status

```
To change the theme it is still in the "preferences" option click on "theme" you should now see the different themes to use.

---

### Post by satimis on 2018-05-28
> **1fallen said:**
> Sorry I was on Arch yesterday so I also was surprised to see the difference's in the "UI"
Ok then, I just extracted them to "/usr/share/gimp/2.0/themes" 
And my version is: 
```
apt policy gimp
gimp:
  Installed: 2.8.22-1
  Candidate: 2.8.22-1
  Version table:
 *** 2.8.22-1 500
        500 http://archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        100 /var/lib/dpkg/status

```
To change the theme it is still in the "preferences" option click on "theme" you should now see the different themes to use.

I'm running
&#10219; apt policy gimp```

gimp:
  Installed: 2.8.16-1ubuntu1.1
  Candidate: 2.8.16-1ubuntu1.1
  Version table:
 *** 2.8.16-1ubuntu1.1 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
        100 /var/lib/dpkg/status
     2.8.16-1ubuntu1 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
```

Actually what I need is to change the size of tool icons.  I need bigger icons but I couldn't make it on GIMP 2.8.

Yesterday I installed GIMP 2.10 on a Ubuntu 16.04 VM of Oracle VirtualBox.  I could change the size of tool icons from "Medium" to "Extralarge" but they look no difference on screen to me.

Regards
satimis

---

