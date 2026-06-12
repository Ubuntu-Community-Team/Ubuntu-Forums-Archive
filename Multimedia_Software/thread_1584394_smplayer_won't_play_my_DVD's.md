---
title: "smplayer won't play my DVD's"
date: 2010-09-29
forum: Multimedia Software
---

### Post by bill23 on 2010-09-29
I have been trying to play a DVD but so far have been unsuccessful. I tried Movie Player and all I got was 'can not read from resource'. I heard that VLC was a good choice, but I could not get it to install. Then I saw in a thread that the smplayer was another good choice. I was able to install it and I had high hopes this time I would be able to watch a DVD. I inserted the disc in the drive selected smplayer and waited. Nothing happened. I could not even hear if it was spinning around and certainly no video or audio at all. Needless to say I am very disappointed.   :(

I am using Ubuntu 10.04. I am pleading for any and all help that is out there to help me find a way so I can watch a DVD. If there is anyone who can help me or point me in the right direction I would be very grateful.

bill23

---

### Post by drpjkurian on 2010-09-29
Hi
First check out whether you drive is ok.You can install VLC from Ubuntu software centre,

If that fails you can try installing Mediubuntu. This version of ubuntu is specifically for Media oriented techies. See this [link]("http://ubuntuguide.net/add-medibuntu-sources-to-install-more-useful-softwares-in-ubuntu")

---

### Post by cchhrriiss121212 on 2010-09-29
Hi Bill,
[This guide]("https://help.ubuntu.com/community/Medibuntu") shows you why and how of DVD playback, these steps are all you need do:

[LIST=1]
[*] install ubuntu-restricted-extras from synaptic
[*]Open a terminal and paste this:
[/LIST]
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Then install libdvdcss2:
```
sudo apt-get install libdvdcss2
```Remember if you want to install any software, use the software center or synaptic.

---

### Post by bill23 on 2010-09-29
> **cchhrriiss121212 said:**
> Hi Bill,
[This guide]("https://help.ubuntu.com/community/Medibuntu") shows you why and how of DVD playback, these steps are all you need do:

[LIST=1]
[*] install ubuntu-restricted-extras from synaptic
[*]Open a terminal and paste this:
[/LIST]
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```Then install libdvdcss2:
```
sudo apt-get install libdvdcss2
```Remember if you want to install any software, use the software center or synaptic.

Hi Chris,
This is part of what i got : 
bill@bill-desktop:~$ sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
[sudo] password for bill: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
This is another dealing with libdvdcss2;
bill@bill-desktop:~$ sudo apt-get install libdvdcss2
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
It nay be part of another package such as; 'libdvdread4' I have it installed but am not sure if 'libdvdcss2' is included. I think it is. How can I verify if it  is or is not?
I checked in Synaptic Package Manager for 'medibuntu' and it was not listed there. The same with the software center. Thought I had followed the directions correctly but maybe I missed something? Will read through them again and see what I come up with this time.
bill23

---

### Post by bill23 on 2010-09-29
Chris,

I got this long list after entering a command for the medibuntu list. I am not clear on what it all means, perhaps you could enlighten  me?;

bill@bill-desktop:~$ deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found
bill@bill-desktop:~$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
--2010-09-29 09:41:17--  [http://www.medibuntu.org/sources.list.d/lucid.list](http://www.medibuntu.org/sources.list.d/lucid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 268 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 268         --.-K/s   in 0s      

2010-09-29 09:41:18 (9.95 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [268/268]

Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en_US
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release
Hit [http://deb.opera.com](http://deb.opera.com) stable Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [44.7kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Get:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages [3,253B]
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages [8,867B]
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [3,240B]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [319kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [1,443B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [121kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [48.1kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [3,773B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [1,739B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [38.5kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [88.3kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [14B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [40.2kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [9,294B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [1,994B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [656B]
Fetched 742kB in 7s (94.8kB/s)
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by cchhrriiss121212 on 2010-09-29
Hi Bill,
You don't need to follow everything in that link, I posted it just to show where I got the instructions from.
All you need to do is the steps shown in my earlier post, sorry for not making that clear.

For future reference, you only need 3 things for watching DVDs on a fresh install:
A video player like VLC
ubuntu-restricted-extras - this will install all the codecs for audio and video you will ever need
libdvdcss2 - not included in the above package, so you get it from adding the medibuntu repository

Hopefully that simplifies things for you.

The error you are getting is because you have another installation program running, either software center or synaptic. Close everything down, and then try the terminal command again.

---

### Post by bill23 on 2010-09-30
> **drpjkurian said:**
> Hi
First check out whether you drive is ok.You can install VLC from Ubuntu software centre,

If that fails you can try installing Mediubuntu. This version of ubuntu is specifically for Media oriented techies. See this [link]("http://ubuntuguide.net/add-medibuntu-sources-to-install-more-useful-softwares-in-ubuntu")

I tried to use the command that began with deb http:// but the terminal would not accept it. This is what it read out:

No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)

Is there a simpler way of installing Medibuntu? What is offered is a bit confusing to a simple mind like mine. Are any of the four Commands above what I am looking for?

bill23

---

### Post by bill23 on 2010-09-30
> **cchhrriiss121212 said:**
> Hi Bill,
You don't need to follow everything in that link, I posted it just to show where I got the instructions from.
All you need to do is the steps shown in my earlier post, sorry for not making that clear.

For future reference, you only need 3 things for watching DVDs on a fresh install:
A video player like VLC
ubuntu-restricted-extras - this will install all the codecs for audio and video you will ever need
libdvdcss2 - not included in the above package, so you get it from adding the medibuntu repository

Hopefully that simplifies things for you.

The error you are getting is because you have another installation program running, either software center or synaptic. Close everything down, and then try the terminal 
command again.

I am obviously doing something wrong. I could not install Medibuntu but did install the medibuntu-keyring and the apport-hooks-medibuntu. In the synaptic package manager thjere were four other apps but they all had a warning about them not being authenticated and how you would be putting your system at risk if you installed them. Is it safe or is there a chance no matter how slim that installing any of them could cause harm to my system? 

Sorry if I am making this more complicated then it actually should be.

bill23

---

### Post by cchhrriiss121212 on 2010-09-30
Medibuntu is not something you install per se, it is just a repository. Think of it like a catalogue that lets you look at things you might like to get for your system, when you add a new repository you can install all the new things listed. The only thing you need from the medibuntu repository is libdvdcss2.

I don't know what four apps you are talking about, but if you are following what I posted above then there is no risk at all.

---

