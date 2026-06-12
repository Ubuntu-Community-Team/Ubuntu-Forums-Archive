---
title: "Video Problem with Jaunty"
date: 2009-07-05
forum: Multimedia Software
---

### Post by wildeagle on 2009-07-05
Hi,

  I upgraded my system to 9.04 with ATI Radeon card and had nothing but issues, I found a couple posts that helped me get it to the point where I can boot up and get video using the builtin Intel video card but when I log in to the system I get an error that the session only lasted 10 seconds and it can't open /etc/ati/ati-fglrx.sh

I have completely purged all FGLRX and rebuilt to the default xorg.conf file but somewhere it is still looking for the fglrx driver which is not on the machine anywhere.

Any help as to where I can find this file and remove it would be greatly appreciated.

  Andrew

---

### Post by pme 72 on 2009-07-05
Not sure if this will help:

 [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

There are instructions for completely removing the fglrx driver and installing the open source ati radeon driver.

---

### Post by wildeagle on 2009-07-06
> **pme 72 said:**
> Not sure if this will help:

 [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

There are instructions for completely removing the fglrx driver and installing the open source ati radeon driver.

I did find that and tried it but to no avail.  As I said there is no remenence of the FGLRX driver on the machine but for some reason when you try and login to the xserver it tries to launch it.  Basically I need to find out what config file would refrence this program on login to xserver and remove that one refrence and then I should be good to go.

---

### Post by shabazzk on 2009-07-06
DUDE! You REALLY need to give other more info on your system. Like the version of ATI driver you are trying to remove, what version of Ubuntu, kernel, method used to install drivers. etc. As much as possible without overkill.

If dpkg really-really refuses to remove an older fglrx-package, it might be needed to sudo gedit /var/lib/dpkg/diversions and remove a few lines. This is a hack and should be avoided. 

You find other great tips, and even the proper whay to install the ATi driver here: [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Can.27t_remove_fglrx_with_dpkg](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Can.27t_remove_fglrx_with_dpkg)

---

### Post by wildeagle on 2009-07-07
> **shabazzk said:**
> DUDE! You REALLY need to give other more info on your system. Like the version of ATI driver you are trying to remove, what version of Ubuntu, kernel, method used to install drivers. etc. As much as possible without overkill.

If dpkg really-really refuses to remove an older fglrx-package, it might be needed to sudo gedit /var/lib/dpkg/diversions and remove a few lines. This is a hack and should be avoided. 

You find other great tips, and even the proper whay to install the ATi driver here: [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Can.27t_remove_fglrx_with_dpkg](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Can.27t_remove_fglrx_with_dpkg)

I was running the ATI 9.3 driver on my machine before I upgraded to Jaunty.  As I said it removed all the ati drivers and fglrx drivers on my machine, machine boots up fine now that I removed the ati and fglrx but as soon as you login to the xserver it comes up saying session only lasted 10 seconds and can't find the etc/ati/fglrx.sh so I need to figure out which file to edit and remove that line as it for some reason was not removed.

---

### Post by shabazzk on 2009-07-07
You probably need to remove the fglrx from the dkms tree, but you have to know which version it is.

```
sudo dkms remove -m fglrx -v 8.522 --all
```

But you have to replace the 8.522, with the correct version number for 9.3 drivers. Which I am not sure of.

---

### Post by wildeagle on 2009-07-16
> **shabazzk said:**
> You probably need to remove the fglrx from the dkms tree, but you have to know which version it is.

```
sudo dkms remove -m fglrx -v 8.522 --all
```

But you have to replace the 8.522, with the correct version number for 9.3 drivers. Which I am not sure of.
Unfortunately DKMS isn't even installed, when I tried to run that command it said it could not be found.

  Any other ideas?

---

### Post by shabazzk on 2009-07-16
DUDE! Of course it didn't find it. You can't just run that command. 

You have to put did not replace the "8.522" with the correct version you previously installed.

---

### Post by blazerte on 2009-10-24
Same problem here with a Debian installation.

Apparently an old version of fglrx that I installed added a line in /etc/profile that tries to run /etc/ati/ati-fglrx.sh

And so /etc/gdm/Xsession (which runs /etc/profile) fails after ati-fglrx.sh is deleted.

Just remove that line as root.

Gawd I hate non-standard/proprietary/closed software.

---

