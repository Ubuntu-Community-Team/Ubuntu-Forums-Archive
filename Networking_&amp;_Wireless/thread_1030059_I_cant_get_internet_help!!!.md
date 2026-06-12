---
title: "I cant get internet help!!!"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by jarett on 2009-01-04
I just got ubuntu studio and Im dual booting it with vista...but I dont have network manager and i tried to get it from add/remove hardware and it says it cant download it from the internet.So I dont know how to make to where i can set up my wireless internet.

help would be greatly appreciated:D

       thanks,

---

### Post by gettinoriginal on 2009-01-04
Have you tried in Synaptic ?? :P

---

### Post by jarett on 2009-01-04
> **gettinoriginal said:**
> Have you tried in Synaptic ?? :P

i have no clue what that is...

---

### Post by gettinoriginal on 2009-01-04
System > Administration > Synaptic Package Manager.  This is where your applications and dependencies are kept.  When selecting synaptic, it will ask you for your password, enter it, the in quick search type "network-manager" without the quote marks.  Right click network-manager-gnome and select mark for installation. if it gives you other things that will be installed, click ok, as those are the dependencies needed for it to work.  At the top you will see "Apply", click it and let it install.    And you may want to read these, they are a great help to a beginner in Ubuntu:
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

:P

---

### Post by jarett on 2009-01-04
> **gettinoriginal said:**
> System > Administration > Synaptic Package Manager.  This is where your applications and dependencies are kept.  When selecting synaptic, it will ask you for your password, enter it, the in quick search type "network-manager" without the quote marks.  Right click network-manager-gnome and select mark for installation. if it gives you other things that will be installed, click ok, as those are the dependencies needed for it to work.  At the top you will see "Apply", click it and let it install.    And you may want to read these, they are a great help to a beginner in Ubuntu:
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

:P

i dont have network manager at all...no where to be found... and even when i try to mark anything else to install it doesnt give me that option.

---

### Post by 2hot6ft2 on 2009-01-04
Open a terminal
Applications>Accessories>Terminal
put this in and hit Enter
```
nm-applet
```
Post the output. If any.
Look and see if you have it in the top right toolbar. While the terminal is open.

---

### Post by 2hot6ft2 on 2009-01-04
If the network applet shows up while the terminal is open then here's how to restore it.
Close the terminal and Go to:

System->Preferences->Sessions

Go to "+ Add"

Then fill in the fields as follows:

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

And click "Save"

Then logout and log back in to and see if you have the applet on your tool bar.

---

### Post by jarett on 2009-01-04
> **2hot6ft2 said:**
> Open a terminal
Applications>Accessories>Terminal
put this in and hit Enter
```
nm-applet
```
Post the output. If any.
Look and see if you have it in the top right toolbar. While the terminal is open.

this is what i got
```
jarett@ubuntu:~$ nm-applet
The program 'nm-applet' can be found in the following packages:
 * network-manager-gnome
 * mythbuntu-diskless-client
Try: sudo apt-get install <selected package>
bash: nm-applet: command not found
jarett@ubuntu:~$ sudo apt-get isntall network-manager-gnome
[sudo] password for jarett: 
E: Invalid operation isntall
jarett@ubuntu:~$ sudo apt-get install mythbuntu-diskless-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mythbuntu-diskless-client
```
and i forgot to look at the bar...

---

### Post by gettinoriginal on 2009-01-04
> **jarett said:**
> this is what i got
```
jarett@ubuntu:~$ nm-applet
The program 'nm-applet' can be found in the following packages:
 * network-manager-gnome
 * mythbuntu-diskless-client
Try: sudo apt-get install <selected package>
bash: nm-applet: command not found
jarett@ubuntu:~$ sudo apt-get isntall network-manager-gnome
[sudo] password for jarett: 
E: Invalid operation isntall
jarett@ubuntu:~$ sudo apt-get install mythbuntu-diskless-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mythbuntu-diskless-client
```
and i forgot to look at the bar...

You misspelled install for network-manager, copy and paste this in terminal:
```
sudo apt-get install network-manager-gnome
```

---

### Post by jarett on 2009-01-04
i just checked and there is no little icon on the bar when the terminal is up....

---

### Post by 2hot6ft2 on 2009-01-04
> **gettinoriginal said:**
> You misspelled install for network-manager, copy and paste this in terminal:
```
sudo apt-get install network-manager-gnome
```
Then you need to do as gettinoriginal says but that's not going to work if you have no network to begin with.

Which ubuntu are you running? 8.10 intrepid 32 bit, 64 bit, Hardy 8.04 or what?

---

### Post by jarett on 2009-01-04
> **gettinoriginal said:**
> You misspelled install for network-manager, copy and paste this in terminal:
```
sudo apt-get install network-manager-gnome
```
 i tried the code and i still get this
```
jarett@ubuntu:~$ sudo apt-get install network-manager-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package network-manager-gnome
```

so is there no other way i can get this...

---

### Post by jarett on 2009-01-04
> **2hot6ft2 said:**
> Then you need to do as gettinoriginal says but that's not going to work if you have no network to begin with.

Which ubuntu are you running? 8.10 intrepid 32 bit, 64 bit, Hardy 8.04 or what?

all i know is that its ubuntu studio 8.10 32 bit

---

### Post by gettinoriginal on 2009-01-04
First, go to System > Administration > Software Sources, the first four boxes should be checked, then:

Run these two in terminal, one at a time:

```
 sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list 
```

```
 wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update 
```

Then check synaptic for network-manager

---

### Post by 2hot6ft2 on 2009-01-04
Ok, go to:

System>Administration>Synaptic Package Manager
and search for
network-manager-gnome
When it finds it highlight it and select "Mark for Installation"
It may popup a box saying other things are required.

Take notes of everything it says it needs.
Mark them
Click on File then generate download script and save it somewhere.
Take it on a flash drive or in a shared folder to a pc that is online and double click the script choose "Run in Terminal" and it will download everything into the location where the script is.

I don't know if it will run on windows or not so if you don't have access to another linux pc and it wont run on windows then.

Go here to get [network-manager-gnome]("http://packages.ubuntu.com/intrepid-updates/i386/network-manager-gnome/download")

And this page has the other things that it may need here.
[http://packages.ubuntu.com/intrepid-updates/network-manager-gnome](http://packages.ubuntu.com/intrepid-updates/network-manager-gnome)
they are the dependencies.

Hope this helps some. May have more to add in a minute.

---

### Post by 2hot6ft2 on 2009-01-04
Once you download the packages you can go back to
System>Administration>Synaptic Package Manager
Click on File then "Add downloaded Packages"
point it to where the packages are
and it will install them for you.

---

### Post by jarett on 2009-01-04
> **gettinoriginal said:**
> First, go to System > Administration > Software Sources, the first four boxes should be checked, then:

Run these two in terminal, one at a time:

```
 sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list 
```

```
 wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update 
```

Then check synaptic for network-manager

the four boxes where checked
tried it twice and got this
```

jarett@ubuntu:~$ sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O             /etc/apt/sources.list.d/medibuntu.list

--2009-01-04 05:16:29--  http://www.medibuntu.org/sources.list.d/intrepid.list
Resolving www.medibuntu.org... failed: Name or service not known.
wget: unable to resolve host address `www.medibuntu.org'
jarett@ubuntu:~$ wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-     key add - && sudo apt-get update
gpg: no valid OpenPGP data found.
jarett@ubuntu:~$ 
jarett@ubuntu:~$ wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
gpg: no valid OpenPGP data found.
jarett@ubuntu:~$ sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list
--2009-01-04 05:17:29--  http://www.medibuntu.org/sources.list.d/intrepid.list
Resolving www.medibuntu.org... failed: Name or service not known.
wget: unable to resolve host address `www.medibuntu.org'
jarett@ubuntu:~$ 
```
and still didnt find it in the synaptic

---

### Post by 2hot6ft2 on 2009-01-04
You could run the download script from the livecd. It would save you some hassle. After creating the script save it somewhere like a shared partition or flash drive. Boot up with the livecd, browse to the script and run it.

Then reboot into ubuntu without the livecd and your files would be where the script is you saved.

---

### Post by jarett on 2009-01-04
> **2hot6ft2 said:**
> Ok, go to:

System>Administration>Synaptic Package Manager
and search for
network-manager-gnome
When it finds it highlight it and select "Mark for Installation"
It may popup a box saying other things are required.

Take notes of everything it says it needs.
Mark them
Click on File then generate download script and save it somewhere.
Take it on a flash drive or in a shared folder to a pc that is online and double click the script choose "Run in Terminal" and it will download everything into the location where the script is.



i/the computer cant even find it in synaptic... but ill try all the downloading

---

### Post by 2hot6ft2 on 2009-01-04
Think I found a deb for it [http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.6.6-0ubuntu5.8.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.6.6-0ubuntu5.8.04.1_i386.deb)

Download that and double click on it in ubuntu.

Found it here. [http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/)

---

