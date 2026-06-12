---
title: "Wusb11 - Success!!"
date: 2005-02-04
forum: Networking &amp; Wireless
---

### Post by KenLin on 2005-02-04
I've complained on here a couple times about how I liked ubuntu, but can't use it because it won't work with my wireless usb adapter. I could get it working in Fedora and suse recognized it out of the box, but ubuntu wouldn't cooperate. 

Well, it turns out to be pretty easy. I just followed this item from the support pages:

[http://www.ubuntulinux.org/support/documentation/faq/compile-kernel-module/view?searchterm=kernel](http://www.ubuntulinux.org/support/documentation/faq/compile-kernel-module/view?searchterm=kernel)

then I was able to download the source from here:

[http://at76c503a.berlios.de/](http://at76c503a.berlios.de/)

make, make install, and shazam! it works!

now I'm happily ubuntuing  =D>

---

### Post by shriek on 2005-02-14
Hi, 
I'm another (unfortunate?) owner of a wusb11 receptor. I've been trying to use ubuntu as my main OS for a long time for I just can't live without my wireless lan connection and it was good to hear from you!

I tried what you wrote here but couldn't install it because I'm using a 2.6 kernel version and I just don't know how to handle CVSs (I don't quite understand this concept, I'm not a developer)

I suppose you're using the same ubuntu version as I am so could you provide some more tips?

---

### Post by otterit on 2005-03-08
[QUOTE=shriek]Hi, 
I'm another (unfortunate?) owner of a wusb11 receptor. I've been trying to use ubuntu as my main OS for a long time for I just can't live without my wireless lan connection and it was good to hear from you!

I tried what you wrote here but couldn't install it because I'm using a 2.6 kernel version and I just don't know how to handle CVSs (I don't quite understand this concept, I'm not a developer)

I suppose you're using the same ubuntu version as I am so could you provide some more tips?[/QUOTE]

In WinXP, I just download the CVS files from the site using a program called WinCVS.  I installed the command line version of the tool also and followed the instructions on how to download the files using a command line.

---

### Post by KenLin on 2005-03-09
so you were able to get it working?

I'm thinking I should write up a how-to for installing these drivers.

---

### Post by norma jean on 2005-03-25
A how-to would be appreciated.  Does Ubuntu recognize Linksys BEFW11S4 Wireless-B broadband routers out of box?

---

### Post by zsr on 2005-04-05
I ran the sudo command from the first link with success but as soon as I try to run make on the drivers, it spits all sorts of errors.  ](*,)

The error list is so large, I doubt I'd be able to paste everything, but if anyone has a work-around for this, that would be nice.

I do remember one error says something about owner not being a user and something about a "cursor".

---

### Post by asimon623 on 2005-04-25
Any chance you'd make that HOW TO?

---

### Post by peejay on 2005-04-28
I just installed the latest ubuntu and this card last night:

Go to [http://at76c503a.berlios.de/cvs.html](http://at76c503a.berlios.de/cvs.html)
Click the 'snapshot of the cvs repository link' and save to a disk, another partition, or by using a different method of internet access.

# sudo apt-get install build-essential linux-headers-`uname -r`

tar xzvf at76c503a-cvsroot.tar.gz
mv at76c503a CVS   
cvs -d `pwd`/CVS co at76c503a

cd at76c503a
make
make install

Go to menu item System/Administration/Networking and enable and setup the device.

I think I restarted once just to be sure all of the settings "took".

---

### Post by DJ_Max on 2005-04-28
[QUOTE=shriek]Hi, 
I'm another (unfortunate?) owner of a wusb11 receptor. I've been trying to use ubuntu as my main OS for a long time for I just can't live without my wireless lan connection and it was good to hear from you!

I tried what you wrote here but couldn't install it because I'm using a 2.6 kernel version and I just don't know how to handle CVSs (I don't quite understand this concept, I'm not a developer)

I suppose you're using the same ubuntu version as I am so could you provide some more tips?[/QUOTE]
 CVS is a revision control system. Basicly, you as an end users would "checkout" the latest source, it'll then download it to your local cvs directory, it doesn't download any special packages or formats, just the files for whatever project your getting. There are a lot of guides for the CVS.

---

### Post by xcapulet on 2005-05-20
I was able to succesfully go through those steps (download, unzip, make, make install, etc.).  I do not have a wireless connection option when i go to the system >> networking area, however.  Is there something i need to do to make this show up/force it to show up?

Any suggestions/other ideas?

---

### Post by David C on 2005-06-01
[QUOTE=peejay]I just installed the latest ubuntu and this card last night:

Go to [http://at76c503a.berlios.de/cvs.html](http://at76c503a.berlios.de/cvs.html)
Click the 'snapshot of the cvs repository link' and save to a disk, another partition, or by using a different method of internet access.

# sudo apt-get install build-essential linux-headers-`uname -r`

tar xzvf at76c503a-cvsroot.tar.gz
mv at76c503a CVS   
cvs -d `pwd`/CVS co at76c503a

cd at76c503a
make
make install

Go to menu item System/Administration/Networking and enable and setup the device.

I think I restarted once just to be sure all of the settings "took".[/QUOTE]

I managed to do a make/make install without any errors. Everything seems normal, but when I go to System > Admin > Networking, my WUSB11 wasn't on the list.

On my dmesg, I can't find anything about any USB thing. Could it be that my USB cannot be detected? My Wireless Adapter is connected to my PC and has its power LED lighted up. 

I'm really lost now.

---

### Post by Y4CcduyctJL3 on 2006-10-23
k, so i clicked on the first link in the originating post, but it's broken. so i'm a little foggy on the details of what i'm supposed to do to get my wusb11 going.  my ubuntu (6.06) didn't come with a compiler (that i can find) and with out the internet on it, i'm not sure how to get one on there, so i can't do the 'make, make install' steps.  i'm going to look around for details on that little barrier, but what i'm unsure of is how i'm supposed to implement whatever it is i'll be compiling.:confused:

---

