---
title: "I'm finding it impossible to install VLC Media Player in 7.10 - PLEASE help!!"
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by BA005 on 2007-11-03
I am a very new user of Ubuntu. I downloaded and installed version 7.10 on October 25th.

One of the most important applications to me is VLC Media Player.

I had heard that it was no problem on Ubuntu, so I finally ditched Microsoft and went with Ubuntu.

So the first thing I did after I installed version 7.10 and got everything connected online, was to try and incorporate VLC. But it doesnt work :(

I have tried everything that all guides say, but still I can get it installed.

Can somebody PLEASE PLEASE PLEASE let me know a simple step-by-step way to get VLC up and running.

The things I have tried so far are...

> making "universe" repository activated.
> making "multiverse" repository activated
> Opening a terminal window and typing in sudo apt-get install vlc
> Opening a terminal window and typing in sudo apt-get update, followed by, sudo apt-get install vlc vlc-plugin-esd. After this command I get..

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 0.8.6.release.c-0ubuntu5) but it is not going to be installed
       Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
       Depends: ttf-dejavu but it is not installable
  vlc-plugin-esd: Depends: vlc-nox but it is not going to be installed
E: Broken packages

NOTHING IS WORKING!

If someone could help me, I would be so grateful!

Should I reinstall an earlier version of Ubuntu? My PC usage requires me to use VLC a lot, therefore it is very important.

OR, does anyone know of any other good media players that can handle files/codecs of all types?!

Thanks in advance!

---

### Post by mrvertigo on 2007-11-03
ok have you tried installing VIA synaptic or aptitude? its a nice front end for apt that makes things much easier command line is great but never underestimate the power of a well designed GUI

---

### Post by Craigus on 2007-11-03
Another issue that you might want to consider before you go too much further is that, under linux, vlc cannot easily play files held on network shares (ie other computers on the network). Is that what you need it to be able to do ?

---

### Post by BA005 on 2007-11-03
> **Craigus said:**
> Another issue that you might want to consider before you go too much further is that, under linux, vlc cannot easily play files held on network shares (ie other computers on the network). Is that what you need it to be able to do ?

No I dont need to do that. I just need to be able to play files stored on my PC.

---

### Post by jack4354353 on 2007-11-28
I have the exact same problem BA005 has and have done everything he has to fix it and get the same errors, is there anything i can do?:(

---

### Post by jack4354353 on 2007-11-28
> **jack4354353 said:**
> I have the exact same problem BA005 has and have done everything he has to fix it and get the same errors, is there anything i can do?:(

well i give up, im going back to windows. i tried but it got to complicating. learning to install a program was hard enough terminals? system pack managers? who the hell wants to deal with that. not me. a good old exe open in 2 seconds is what im about.

---

### Post by Yellowdog428 on 2007-11-28
Wow!  Giving up so quickly?!

You obviously did not read this before the install
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

The package manager is under 
**SYSTEM -> ADMINISTRATION -> SYNAPTIC PACKAGE MANAGER**

Good luck!
Cheers

---

### Post by JBAlaska on 2007-11-28
Well if your going back to windoze this may not help...but;

Graphical way:
Open Synaptic (System -> Administration -> Synaptic Package Manager). In Settings -> Repositories, make sure you have a "universe" repository activated.

Search for vlc and install it. You should also install vlc-plugin-esd, mozilla-plugin-vlc (and libdvdcss2).

Command line way:
You need to check that you have a "universe" mirror in your /etc/apt/sources.list.

   ```
% sudo apt-get update
```
   ```
% sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
```

---

### Post by jfinkels on 2007-11-28
> **jack4354353 said:**
> I have the exact same problem BA005 has and have done everything he has to fix it and get the same errors, is there anything i can do?:(

Can you (and BA005) post the output of entering the following command in the terminal?```
cat /etc/apt/sources.list
```

As for general info on installing programs, take a look at the first link in my signature.

---

### Post by mdpalow on 2007-11-28
I briefly read your posting and the problem seems to be your codecs if I understand correctly.

If that's the only problem, then I think you just didn't install the proper files to make this work. Even though it's pretty simple, a lot of people don't get it at first until after they have successfully done it AND then it seems simple.

Here's the deal for all you trying to play movies/DVDs etc..

Click on the link below in my signature and download my script called QuickStart .

Once you run QuickStart, go to option 13, which is the option to install all the proper DVD/codecs files for your system.

When finished, run totem to watch a movie and it'll work; as long as you don't have any other issues. If so, post back, but I'm pretty sure this will work for you as it has for me and many others.

Good luck and hope you didn't switch back to Windows that quickly...

One last thing.... most people don't realize that even Windows doesn't come with the codecs necessary to play DVDs; it's against the law to package these files with the OS. The reason you probably don't realize it with Windows is because when you install your disks (not windows disks), usually one of them will have a codecs program on it or maybe you installed NERO, which has a codecs in it. With Ubuntu, there's actually a posting that explains in detail the few steps you have to do in order to make this work. Most people probably don't see that posting if they aren't looking in the right place and I can't remember the link right now. However, my script actually does everything for you and saves you some reading, typing, and maybe even a lot of frustration. :)

---

### Post by jfank on 2007-11-29
> **jack4354353 said:**
> well i give up, im going back to windows. i tried but it got to complicating. learning to install a program was hard enough terminals? system pack managers? who the hell wants to deal with that. not me. a good old exe open in 2 seconds is what im about.

You know I thought the same way when I first started using Linux, that is why I kept Windows on one machine, and Linux on another machine.  That way if I screwed up the Linux Machine, I had something to fall back on.  All I use now is Linux, and I'm also having a problem getting this program to work, but the only way you can get it to work is to post on here and ask A LOT of QUESTIONS.  We are always here to help you out, and we all hope you can get this program to work for you, and that you will stay with Linux.  And since you said your going back to Windows.  Did you know that Windows Vista is part Linux?

On another note, I'm having a problem getting the "libdvdcss" installed so I can view a encrypted DVD on my laptop.  Can someone give me some ideas on how to get this installed?  I did some reading around, but since I'm using Kubuntu all the command lines I found were for Ubuntu.  Thank you for the help.

---

### Post by jfinkels on 2007-11-29
> **jfank said:**
> 
On another note, I'm having a problem getting the "libdvdcss" installed so I can view a encrypted DVD on my laptop.  Can someone give me some ideas on how to get this installed?  I did some reading around, but since I'm using Kubuntu all the command lines I found were for Ubuntu.

Ubuntu and Kubuntu have the same base. The only difference is the desktop environment. The command-line programs will be the same. However if you want to run a graphical text editor, or something like that, just replace "gedit" with "kate".

To install libdvdcss, make sure you have access to the Medibuntu repository ( [http://medibuntu.org/](http://medibuntu.org/) ). To do this, type (or copy and paste) the following in the terminal:```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
to add the repository to your list of repositories. Then add it's GPG key:```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
Then install libdvdcss like this:```
sudo aptitude install libdvdcss2
```

As for the original poster, and the poster who said "I'm going back to Windows", if you post the contents of your /etc/apt/sources.list, I can help diagnose your problem.

---

