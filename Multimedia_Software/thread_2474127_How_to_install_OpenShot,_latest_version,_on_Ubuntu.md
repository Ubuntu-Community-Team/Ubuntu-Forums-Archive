---
title: "How to install OpenShot, latest version, on Ubuntu 22.04"
date: 2022-04-22
forum: Multimedia Software
---

### Post by satimis on 2022-04-22
Hi all,

Ubuntu 22.04

Please advise how to install OpenShot, latest version, on Ubuntu 22.04

On Terminal;
$ sudo add-apt-repository ppa:openshot.developers/ppa```

......
......
Hit:1 https://dl.google.com/linux/chrome/deb stable InRelease
Ign:2 https://ppa.launchpadcontent.net/openshot.developers/ppa/ubuntu jammy InRelease       
Hit:3 http://security.ubuntu.com/ubuntu jammy-security InRelease                            
Get:4 http://hk.archive.ubuntu.com/ubuntu jammy InRelease [270 kB]              
Err:5 https://ppa.launchpadcontent.net/openshot.developers/ppa/ubuntu jammy Release      
  404  Not Found [IP: 91.189.95.85 443]
Hit:6 http://hk.archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:7 http://hk.archive.ubuntu.com/ubuntu jammy-backports InRelease
Reading package lists... Done
E: The repository 'https://ppa.launchpadcontent.net/openshot.developers/ppa/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

I don't prefer to run "OpenShot 2.2 (64-bit AppImage) for Linux

Thanks in advance

Regards

---

### Post by ajgreeny on 2022-04-22
I have no idea if this will help i your situation but I am one of those users who keeps away from snaps and tries to find alternative methods of installing a .deb version if possible.

I had the same problem as you when I started using 22.04 which at the time had no ppa for chromium.  However it was possible to change the ppa address and point it to the impish (21.10) version which for a long time worked without problems.
That ppa ***[http://ppa.launchpad.net/saiarcot895/chromium-dev/ubuntu](http://ppa.launchpad.net/saiarcot895/chromium-dev/ubuntu)*** has now been updated to jammy but was working only about a week ago.  maybe the openshot ppa will also be fine if you change to the impish version, assuming impish is enabled, of course.

---

### Post by Dennis N on 2022-04-22
Your best option: Install it using Flatpak:

```
[dmn@Tyana ~]$ flatpak info org.openshot.OpenShot

OpenShot Video Editor - An easy to use, quick to learn, and surprisingly
powerful video editor

          ID: org.openshot.OpenShot
         Ref: app/org.openshot.OpenShot/x86_64/stable
        Arch: x86_64
      Branch: stable
     Version: 2.6.1

```

---

### Post by satimis on 2022-04-22
> **ajgreeny said:**
> I have no idea if this will help i your situation but I am one of those users who keeps away from snaps and tries to find alternative methods of installing a .deb version if possible.

I had the same problem as you when I started using 22.04 which at the time had no ppa for chromium.  However it was possible to change the ppa address and point it to the impish (21.10) version which for a long time worked without problems.
That ppa ***[http://ppa.launchpad.net/saiarcot895/chromium-dev/ubuntu](http://ppa.launchpad.net/saiarcot895/chromium-dev/ubuntu)*** has now been updated to jammy but was working only about a week ago.  maybe the openshot ppa will also be fine if you change to the impish version, assuming impish is enabled, of course.
Hi,

Thanks for your advice.

Whether following document will be suitable for me to follow ?

Add software repositories
[https://help.ubuntu.com/stable/ubuntu-help/addremove-sources.html.en](https://help.ubuntu.com/stable/ubuntu-help/addremove-sources.html.en)
....
.....
3. Click Add and enter the APT line for the repository. This should be available from the website of the repository, and should look similar to:

Add following line; ?
[http://ppa.launchpad.net/saiarcot895/chromium-dev/ubuntu/dists/impish/](http://ppa.launchpad.net/saiarcot895/chromium-dev/ubuntu/dists/impish/)

Do I need adding deb before the line ?
Do I need reboot ?

Thanks

Regards

[B][COLOR="#FF0000"]Edit-1
===[/COLOR][/B]
I'm testing Ubuntu 22.04 on VM of Oracle VirtualBox.  I'll clone a new VM to perform this testing.

[B][COLOR="#FF0000"]Edit-2
===[/COLOR][/B]
It is also the same.

$ sudo add-apt-repository ppa:tomtomtom/woeusb```

.....
......
Hit:1 https://dl.google.com/linux/chrome/deb stable InRelease
Get:2 http://hk.archive.ubuntu.com/ubuntu jammy InRelease [270 kB]                                             
Hit:3 http://security.ubuntu.com/ubuntu jammy-security InRelease                                               
Ign:4 https://ppa.launchpadcontent.net/openshot.developers/ppa/ubuntu jammy InRelease                          
Hit:5 http://hk.archive.ubuntu.com/ubuntu jammy-updates InRelease                        
Hit:6 https://ppa.launchpadcontent.net/tomtomtom/woeusb/ubuntu jammy InRelease
Hit:7 http://hk.archive.ubuntu.com/ubuntu jammy-backports InRelease
Err:8 https://ppa.launchpadcontent.net/openshot.developers/ppa/ubuntu jammy Release
  404  Not Found [IP: 91.189.95.85 443]
Reading package lists... Done
E: The repository 'https://ppa.launchpadcontent.net/openshot.developers/ppa/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

---

### Post by satimis on 2022-04-22
> **Dennis N said:**
> Your best option: Install it using Flatpak:

```
[dmn@Tyana ~]$ flatpak info org.openshot.OpenShot

OpenShot Video Editor - An easy to use, quick to learn, and surprisingly
powerful video editor

          ID: org.openshot.OpenShot
         Ref: app/org.openshot.OpenShot/x86_64/stable
        Arch: x86_64
      Branch: stable
     Version: 2.6.1

```
Hi,

Thanks for your advice.

I'm now testing Ubuntu 22.04 and trying to learn something new to me.  If fail I'll follow your step.

I ran flatpak before.

Regards

---

### Post by satimis on 2022-04-22
Hi ajgreeny

Lot of problem on Ubuntu 22.04. It took me several hours without solving all problems encountered by me.

Now I have solved the update problem as follow;
On Terminal ran following commands```

mkdir ~/solution
cd ~/solution/
wget https://gist.githubusercontent.com/ishad0w/788555191c7037e249a439542c53e170/raw/3822ba49241e6fd851ca1c1cbcc4d7e87382f484/sources.list
sudo rm -r /etc/apt/sources.list
sudo cp -r ~/solution/sources.list /etc/apt/sources.list
sudo mv /etc/apt/sources.list.d/* ~/solution

```

$ sudo apt update ```

Hit:1 http://archive.canonical.com/ubuntu focal InRelease                                             
Hit:2 http://archive.ubuntu.com/ubuntu focal InRelease                                                
Hit:3 http://archive.ubuntu.com/ubuntu focal-updates InRelease
Hit:4 http://archive.ubuntu.com/ubuntu focal-security InRelease
Hit:5 http://archive.ubuntu.com/ubuntu focal-backports InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.

```

Reboot

But I couldn't run ```

sudo add-apt-repository ppapenshot.developers/ppa

```
Problem comes back.  I don't know why?

$ lsb_release -a```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04 LTS
Release:        22.04
Codename:       jammy
```

---

### Post by satimis on 2022-04-22
Hi Dennis,

$ sudo apt install flatpak -y```

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgdk-pixbuf-2.0-0 : Breaks: libgdk-pixbuf2.0-0 (< 2.40.0+dfsg-6~) but 2.40.0+dfsg-3ubuntu0.2 is to be installed
 libgdk-pixbuf2.0-0 : Depends: libgdk-pixbuf2.0-common (= 2.40.0+dfsg-3ubuntu0.2) but 2.42.8+dfsg-1 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

Regards

---

### Post by Dennis N on 2022-04-22
I installed 2204 to check out all the great new features. For flatpak support in 2204, I installed flatpak from Software (not Ubuntu Software) which is now installed by default. Open the application page for Software, and scroll down to the add-ons section (see screenshot). check the box to Install the flatpak support (almost). You still have to enable the flathub remote to find any flatpaks. I had to use the command from the flathub web site to add the remote:
```
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```
Then restart, and you can find Flatpaks in Software app and install them, or use the flatpak command in the terminal to find and install.

P.S. - I don't know why your terminal apt install has those problems. Using Software, I had none.

---

### Post by jensclear12 on 2022-04-22
I had the same problem as you when I started using 22.04 which at the time had no ppa for chromium. However it was possible to change the ppa address and point it to the impish (21.10) version which for a long time worked without problems. That ppa [http://ppa.launchpad.net/saiarcot895...ium-dev/ubuntu](http://ppa.launchpad.net/saiarcot895...ium-dev/ubuntu) has now been updated to jammy but was working only about a week ago. maybe the openshot ppa will also be fine if you change to the impish version, assuming impish is enabled, of course.

---

### Post by wildmanne39 on 2022-04-22
@jenclear12 the link to ppa is not found when I click on it.

---

### Post by satimis on 2022-04-23
> **Dennis N said:**
>  - snip -

P.S. - I don't know why your terminal apt install has those problems. Using Software, I had none.
I download and installed Ubuntu 22.04 2 days ago.  Its sha256sum is correct.

Another problem, which I found, is unable to start WoeUSB

I followed the steps on;
Steps to install WoeUSB on Ubuntu 22.04 LTS
How to install WoeUSB on Ubuntu 22.04 LTS Jammy JellyFish
[https://www.how2shout.com/linux/how-to-install-woeusb-on-ubuntu-22-04-lts-jammy-jellyfish/](https://www.how2shout.com/linux/how-to-install-woeusb-on-ubuntu-22-04-lts-jammy-jellyfish/)

Installation went through but unable to start WoeUSB

Adding Application Launcher
right-click on spare space of top-menu bar
no response

I'll download another Ubuntu 22.04 desktop and try again.

Regards

---

### Post by satimis on 2022-04-23
> **Dennis N said:**
> I installed 2204 to check out all the great new features. For flatpak support in 2204, I installed flatpak from Software (not Ubuntu Software) which is now installed by default. Open the application page for Software, and scroll down to the add-ons section (see screenshot). check the box to Install the flatpak support (almost). You still have to enable the flathub remote to find any flatpaks. I had to use the command from the flathub web site to add the remote:
```
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```
Then restart, and you can find Flatpaks in Software app and install them, or use the flatpak command in the terminal to find and install.

I couldn't  find "add-ons section "

Please refers to screenshots attached

Regards

[B][COLOR="#FF0000"]Edit
===[/COLOR][/B]
In the circumstance I'll wait for another week to download a new Ubuntu 22.04 desktop ISO and try again

Unfortunately the building of my new AMD Ryzen9 12-core PC will be delayed accordingly.

---

### Post by Dennis N on 2022-04-23
> I couldn't find "add-ons section "
Try again - It was a bit hard to discover - First, search for "gnome software" using search box of "Software" or even from "Ubuntu Software" (see Screenshot below). Just click anywhere on the description to open the details page (shown in previous post screebshot). Scroll down and you will see the "add-ons" section.

---

### Post by satimis on 2022-04-23
> **Dennis N said:**
> Try again - It was a bit hard to discover - First, search for "gnome software" using search box of "Software" or even from "Ubuntu Software" (see Screenshot below). Just click anywhere on the description to open the details page (shown in previous post screebshot). Scroll down and you will see the "add-ons" section.
I found it, but unable to install FlatPak Support

Pls refers to attached screenshot.

I suspect whether this Ubuntu 22.04 desktop ISO having problem?

Regards

---

### Post by Dennis N on 2022-04-23
> **satimis said:**
> I found it, but unable to install FlatPak Support. Pls refers to attached screenshot. I suspect whether this Ubuntu 22.04 desktop ISO having problem?
Regards
Maybe. I downloaded the ISO of the release version just this evening (Friday in the U.S.), not a beta or development version. When I did the install, I did the minimal install option, but I doubt that would matter - just fewer applications on mine. This is also a virtual machine (QEMU/KVM) but that should not matter either.  I would try a new downloaded ISO, and it you have the final release ISO, you should get the same result.

---

### Post by satimis on 2022-04-23
> **Dennis N said:**
> Maybe. I downloaded the ISO of the release version just this evening (Friday in the U.S.), not a beta or development version. When I did the install, I did the minimal install option, but I doubt that would matter - just fewer applications on mine. This is also a virtual machine (QEMU/KVM) but that should not matter either.  I would try a new downloaded ISO, and it you have the final release ISO, you should get the same result.
According to my recollection, I download Ubuntu 22.04 desktop ISO in the mid day on April 21, 2022 (USA west coast time), direct on;

Ubuntu website
[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)

Not via torrents.  So I'll wait for another week and download Ubuntu 22.04 desktop ISO again

---

