---
title: "Boxee on 12.04"
date: 2012-07-07
forum: Multimedia Software
---

### Post by amir786_z on 2012-07-07
Hi there guys 
can someone tell me how can i install Boxee Media centre on 12.04?

---

### Post by vg2373 on 2012-07-07
[http://jack-server.com/blog/?p=3073]("http://www.unixmen.com/boxee-media-center-in-ubuntu-910/")

---

### Post by amir786_z on 2012-07-07
I have tried these steps but it fails

**Installation**

 Go to the Boxee homepage at [http://www.boxee.tv/](http://www.boxee.tv/) and select 'Join up'. Add  the repository by going to System - Administration - Software Sources,  click on the 'Third Party Software' ('Other Software' in Lucid) tab. Now  click on 'Add' and enter 

deb [http://apt.boxee.tv](http://apt.boxee.tv) lucid main


Click on 'Close' and press 'Reload' when prompted.  Now in Applications - Accessories - Terminal update the apt cache with 
```
sudo apt-get updateInstall
```the program with 
```
sudo apt-get install boxee
```ERROR

---

### Post by chriswhat21 on 2012-07-30
Boxee.tv has stopped developing for Linux, Windows, and Mac.  They are moving towards iPhone/iPad and just Boxee Boxes.  I've been searching around for the same thing. [http://jack-server.com/blog/?p=3073](http://jack-server.com/blog/?p=3073) is all I've found so far, but I haven't had time to try it out.  If I get around to it, I'll let you know.

---

### Post by amir786_z on 2012-08-14
> **chriswhat21 said:**
> Boxee.tv has stopped developing for Linux, Windows, and Mac.  They are moving towards iPhone/iPad and just Boxee Boxes.  I've been searching around for the same thing. [http://jack-server.com/blog/?p=3073](http://jack-server.com/blog/?p=3073) is all I've found so far, but I haven't had time to try it out.  If I get around to it, I'll let you know.

Thats sad :(.. XBMC is awesome :D

---

### Post by europa on 2012-08-15
if my blog post does not work, please let me know why. i'll update the page with updated information. the process i posted on jack-server.com works for me on my 12.04 installation.

---

### Post by crymsonfyre on 2012-08-25
Hi There, I havent been able to install this properly I suppose? I hvae no idea why? I went through your installation process to a T, but when I try to run it, nothing happens. Please if there is anything I can do differently I would appreciate it. I enjoy having Boxee, XBMC and Plex on my ubuntu. I find that 12.04 has become tough to figure out more than 10.10

---

### Post by amir786_z on 2012-08-25
> **crymsonfyre said:**
> Hi There, I havent been able to install this properly I suppose? I hvae no idea why? I went through your installation process to a T, but when I try to run it, nothing happens. Please if there is anything I can do differently I would appreciate it. I enjoy having Boxee, XBMC and Plex on my ubuntu. I find that 12.04 has become tough to figure out more than 10.10

XBMC is easy to install.u can find it in software centre. install and run.simple.

---

### Post by crymsonfyre on 2012-08-25
> **amir786_z said:**
> XBMC is easy to install.u can find it in software centre. install and run.simple.
i have been using xbmc for years now and already have that downloaded. however i liked having boxee on just as well.

---

### Post by europa on 2012-08-25
> **crymsonfyre said:**
> Hi There, I havent been able to install this properly I suppose? I hvae no idea why? I went through your installation process to a T, but when I try to run it, nothing happens. Please if there is anything I can do differently I would appreciate it. I enjoy having Boxee, XBMC and Plex on my ubuntu. I find that 12.04 has become tough to figure out more than 10.10

Did it install correctly? Did you have any errors during install?

As you said it doesn't do anything when you run it, I assume that you got it installed. Have you tried running it from the command line?

```
# /opt/boxee/run-boxee-desktop
```

Does this work? Do you get any errors?

---

### Post by rohmalik on 2012-09-13
Hi Europa;

I followed the steps on your blog

[http://jack-server.com/blog/?cat=9](http://jack-server.com/blog/?cat=9)


[LIST=1]
[*]Install Ubuntu 12.04. At the time of this writing, 12.04 is  currently in the Beta2 phase and will be released on april 26th. The GA  release will probably work just as well.
[*]Install the libmysqlclient16 package # wget [http://jack-server.com/files/libmysqlclient16_5.1.61-0ubuntu0.11.10.1_i386.deb](http://jack-server.com/files/libmysqlclient16_5.1.61-0ubuntu0.11.10.1_i386.deb)
[*]Install the boxee package# wget [http://jack-server.com/files/boxee-1.5.0.23596-2bcda77.i486.deb](http://jack-server.com/files/boxee-1.5.0.23596-2bcda77.i486.deb)
[*]start Boxee through the command line, or via its location at the terminal
$ /opt/boxee/run-boxee-desktop
[/LIST]
Can you please help me to install and run boxee.


thanks,

---

### Post by europa on 2012-09-14
I can assist. What problems are you having with the directions? Are you getting any errors messages? Please post them here.

---

### Post by europa on 2012-09-14
I also urge anybody who is using boxee to take a look at the upstream project: xbmc

xbmc is included in the ubuntu 12.04 repo and can be installed with a single command. It also has more features than boxee and you can install plugins to add further functionality.

Here is a post where I go over my current setup: [http://jack-server.com/blog/?p=3191](http://jack-server.com/blog/?p=3191)

---

### Post by yaniraD on 2012-10-20
Perhaps, you could try this one to install your boxee media center. First, download and install the following deb packages which includes libdirectfb-1.0-0 ,liblzo1 1.08-3 ,libkrb53 1.6. Second, add Jaunty Repo for Boxee. Third, open the  source, namely list sudo gedit /etc/apt/sources.list, then add this  line deb [http://apt.boxee.tv](http://apt.boxee.tv) jaunty main. Save and close the text editor, Installing Boxee, Last step is to update  and  install, sudo apt-get updatesudo apt-get install boxee.

---

### Post by iamthenewguy on 2012-11-02
I have tried installing Boxee by the above listed method and have ran into multiple problems.  I am running Zorin 6...same as 12.04.  When i tried to install the lib files, the first one shut me out of my network and I had to reboot into safe mode to repair packages in order to get back online. The 2nd 2 files would not install or installed but not correctly. I tried to continue with installation and got the following:

[B]rf@rf-NY540AA-ABA-CQ5210F:~$ sudo apt-get install boxee
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 boxee : Depends: libxmlrpc-c3 but it is not installable
         Depends: libdirectfb-1.0-0 but it is not installable or
                  libdirectfb-1.2-0 but it is not installable or
                  libdirectfb-1.2-9 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.[/B]


Admittedly I am still very new to the world of Linux and my knowledge is minimal, yet I am excitedly close to a Windows-free world of perfect bliss complete with singing angels and dessert for breakfast. Please help.

---

