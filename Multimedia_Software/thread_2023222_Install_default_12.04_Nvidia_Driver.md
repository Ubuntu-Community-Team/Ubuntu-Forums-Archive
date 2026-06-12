---
title: "Install default 12.04 Nvidia Driver"
date: 2012-07-12
forum: Multimedia Software
---

### Post by Kmels on 2012-07-12
Hello. 

**TLDR: I would like to know which version of the nvidia driver comes with Ubuntu 12.04. Where can I see that? **

When I installed Ubuntu 12.04 everything worked fine.

Event A: I did an update and I wasn't able to log anymore (it broke the nvidia driver). I fixed it with a driver from the nvidia website. Then, event A happened again.

The problem is, after installing the new driver, Flash doesn't work well. It gets more blue colors on videos and continuously interrupted audio. 

I'm pretty sure it is because of the updates, this also happened in my previous version of Ubuntu 11.04.

My graphic card is a Nvidia GeForce GT 430.

Thank you

---

### Post by kc1di on 2012-07-12
one of the problems you may be having is that when you install a driver directly form nvidia you must rebuild the kernel modules for each new kernel installed during an update. a better approach would be to go to unity dash and type drivers and open the additional driver tool. install the most current nvidia driver from there in your case i believe it would nvidia current, drivers in the additional driver tool have been checked out by the ubuntu team and should work.  Also if installed this way they automatically update with a new kernel. 
Good Luck.

---

### Post by tophchris on 2012-07-12
I have the same problem after upgrading to 12.04: Black screen with orange dots when booting. I can get to a terminal where I did make some attempts to update the nvidia driver (GT 210), but it says 'already latest driver installed'. (my kernel is 3.2.0-24-generic-pae, the driver 295.40-Oubuntu1)I am pretty deperate now...:(

---

### Post by kc1di on 2012-07-12
> **tophchris said:**
> I have the same problem after upgrading to 12.04: Black screen with orange dots when booting. I can get to a terminal where I did make some attempts to update the nvidia driver (GT 210), but it says 'already latest driver installed'. (my kernel is 3.2.0-24-generic-pae, the driver 295.40-Oubuntu1)I am pretty deperate now...:(

Nvidia was having some problems with linux drivers and 3d in unity.

you should boot into unity 2d for now. 
you could add the ppa repository from xswat and install the latest driver from there believe it is 302.17-0.
here's the page
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

Believe the problem has been fix in the 302 driver series. 
good luck

---

### Post by Kmels on 2012-07-12
> **kc1di said:**
> Nvidia was having some problems with linux drivers and 3d in unity.

you should boot into unity 2d for now. 
you could add the ppa repository from xswat and install the latest driver from there believe it is 302.17-0.
here's the page
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

Believe the problem has been fix in the 302 driver series. 
good luck

Hello, thanks for your answer. I don't unity, I use gnome-panel because I use xmonad. 

I installed nvidia-current from the xswat ppa, but it didn't work. I got a gray screen inside of a black screen. Earlier I think I had a prompt to login.

I'm still interested in the driver that comes as default :) How can I get it?

---

### Post by cuyo01 on 2012-07-12
> **kc1di said:**
> one of the problems you may be having is that when you install a driver directly form nvidia you must rebuild the kernel modules for each new kernel installed during an update. a better approach would be to go to unity dash and type drivers and open the additional driver tool. install the most current nvidia driver from there in your case i believe it would nvidia current, drivers in the additional driver tool have been checked out by the ubuntu team and should work.  Also if installed this way they automatically update with a new kernel. 
Good Luck.

second, but not only with kernel updates but xorg updates too and update the driver or reinstall dont fix the problem, needed to uninstall first the driver and install it again.

---

### Post by tophchris on 2012-07-12
> **kc1di said:**
> Nvidia was having some problems with linux drivers and 3d in unity.

you should boot into unity 2d for now. 
you could add the ppa repository from xswat and install the latest driver from there believe it is 302.17-0.
here's the page
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

Believe the problem has been fix in the 302 driver series. 
good luck
I get: "Couldn't resolve host 'launchpad.net'" when I run #sudo add-apt-repository ppa:launchpad.net#

---

### Post by robtygart on 2012-07-12
Add me to the list 

When I install Nvidia-Current I can only get into unity 2d, 

However if i Install Nvida post-release updates I can, but when I do I can't access my second monitor.

---

### Post by firekage on 2012-07-12
> **cuyo01 said:**
> second, but not only with kernel updates but xorg updates too and update the driver or reinstall dont fix the problem, needed to uninstall first the driver and install it again.

could you write how to perform all of this?


I have similar problem. In my case, however, everything works with new drivers for nVidia GTX260 but as soon as i use something to play movies than Ubuntu goes back to login screen, i have auto log out.

---

### Post by robtygart on 2012-07-12
> **robtygart said:**
> Add me to the list 

When I install Nvidia-Current I can only get into unity 2d, 

However if i Install Nvida post-release updates I can, but when I do I can't access my second monitor.


Edit: 

I don't even get sent back to the login, Ijust get a black screen, I can Ctrl+Alt+Delete then it enter to log out, the log out box does not even show so I am just guessing were the logout button is. 

This happens in both Kubuntu and Ubuntu.

---

### Post by kc1di on 2012-07-12
> **Kmels said:**
> Hello, thanks for your answer. I don't unity, I use gnome-panel because I use xmonad. 

I installed nvidia-current from the xswat ppa, but it didn't work. I got a gray screen inside of a black screen. Earlier I think I had a prompt to login.

I'm still interested in the driver that comes as default :) How can I get it?

go to a terminal and do the following if you want the default drivers.
```
sudo apt-get purge nvidia
sudo apt-get install nouveau
```

Reboot a give it a try.

---

### Post by oldfred on 2012-07-12
I am running post release updates version which is -49,  Synaptic tells me I am using -49.

The -40 is the one with issues for certain models of nVidia. Synaptic shows me both -40 & -49 as available but when in the system settings drivers it just gives me current or post release updates as choices.
fred@fred-Precise:~$ jockey-text -l
xorg:nvidia_current - NVIDIA accelerated graphics driver (Proprietary, Disabled, Not in use)
xorg:nvidia_current_updates - NVIDIA accelerated graphics driver (post-release updates) (Proprietary, Enabled, In use)

NVIDIA 295.49 Fixes Linux Performance Regression
[http://www.phoronix.com/scan.php?page=news_item&px=MTA5NjQ](http://www.phoronix.com/scan.php?page=news_item&px=MTA5NjQ)
Fixing the performance regression of the 295.40 driver that affected GeForce 6 and GeForce 7 series hardware. 

Now older as -49 is available in the repositories.
Warning for nVidia GeForce 6, 7, and 8800 cards with 12.04 Precise
[http://ubuntuforums.org/showthread.php?t=1969754](http://ubuntuforums.org/showthread.php?t=1969754)
serious issue with the GeForce 6, 7, and 8800 GTS/GTX cards, K/Ubuntu 12.04, and their latest 295.40 driver.

---

### Post by robtygart on 2012-07-12
> **kc1di said:**
> go to a terminal and do the following if you want the default drivers.
```
sudo apt-get purge nvidia
sudo apt-get install nouveau
```

Reboot a give it a try.

Mine keeps saying "Unable to locate package nouveau"

I installed the PPA

```
rob@rob-mobile:~$ sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
[sudo] password for rob:
You are about to add the following PPA to your system:
 Updated versions of X.org drivers, libraries, etc. for Ubuntu.

This PPA is for stable upstream releases of X.org components.  If you're looking for something even more bleeding-edge, please see the xorg-edgers PPA.  Or, if you're actually wanting backports of the current stable X stack to an older Ubuntu release, see the x-backports PPA.

While Ubuntu-X does not officially support these packages, if you discover problems when installing these debs please feel free to report bugs to launchpad.  However, please make sure to clearly state that you are running packages from this PPA so we know the fixes need to come here.

If you are uprading from one release to another with this PPA activated, please install the ppa-purge package and use it to downgrade everything in here beforehand. sudo ppa-purge ppa:ubuntu-x-swat/x-updates will do it.
 More info: https://launchpad.net/~ubuntu-x-swat/+archive/x-updates
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.eYIPLu1SeZ --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: key AF1CDFA9: public key "Launchpad PPA for Ubuntu-X" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

```

---

### Post by kc1di on 2012-07-13
> Mine keeps saying "Unable to locate package nouveau
Try this then
```
sudo apt-get install nouveau-firmware
```

---

