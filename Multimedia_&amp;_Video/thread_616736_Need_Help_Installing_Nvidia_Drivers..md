---
title: "Need Help Installing Nvidia Drivers."
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by Pepse3 on 2007-11-18
Hopefully I can get the help I need for this.  I have been a Linux user for almost 7years.  Updating Nvidia drivers has never been my forte'.  It is something I have done maybe 6 times.  It has only worked flawlessly once.  Until about 6 months ago I was a Mandrake/Mandriva user.  Now that I am with Kubuntu I am willing to give it another try.  I have read tseliot's "how to" and it appears to be confusing.  I have kernel 2.6.20-16 generic; which I think is good.  However in "Method 1.2" he states "Now that you know the architecture type:  sudo apt-get install linux-generic ".  If it is for a "safe mode" I do have that anyway.  Of course if I don't need this then apparently I would do Method 1.3, Install linux driver.  I have an Nvidia GE Force FX 5200 AGP card on a Gigabyte 8I865GME-775-RH mobo with onboard Intel video disabled.  To this point I have not had any issues with my Nvidia card.  Also, if it helps to know what is what in my "System Settings-Monitor & Display-Hardware" it shows Graphics card nv  Driver nvidia .  If all this to this point is good the I assume I go to Method 1.4 Backup your Xorg.conf?  Then go to Method 1.5? Or Method 1.6, because I use KDE?  Then that second part of M1.6?  And if this is all OK tell me what else I might be forgetting before I attempt this.

Later. Pepse.

---

### Post by Qwerty_ on 2007-11-18
Well I would just install the restricted drivers.

System>Administration>Restricted Drivers Manager.

Make sure you have enabled all of the repos bar source.

System>Administration>Software Sources.

---

### Post by Pepse3 on 2007-11-18
qwerty,

  I think because you run Ubuntu and I run Kubuntu there is a difference as to where I should go.  But, I am thinking I go to System Settings-General-Computer Administration-Monitor & Display??  Or??

  And if we are talking the Kubuntu GUI I don't see System-Admin-Software Resources I don't have that either.

Pepse.

---

### Post by Qwerty_ on 2007-11-18
Ahh ok your on Kubuntu, I assume that they would have a restricted drivers manager somewhere. Have a look around in your administration settings.

I just did a quick google and found these few things that might help you.

[http://ubuntuforums.org/showthread.php?t=491468](http://ubuntuforums.org/showthread.php?t=491468)

I did notice that the restricted drivers manager has been included with Kubuntu 7.10

[http://www.kubuntu.org/announcements/7.10-release.php](http://www.kubuntu.org/announcements/7.10-release.php)

---

### Post by Pepse3 on 2007-11-19
Qwerty_

  First to say, I am a little nervous about upgrading to 7.10; true I never had problems with Mandrake/Madriva but this is different.  And I did do the "sudo apt-get install restricted-manager" and I will paste the answer here.  Before I do I will say that I have no clue where in the heck this restricted driver manager is.

jim@jims-computer:~$ apt-get install restricted-manager
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
jim@jims-computer:~$ sudo apt-get install restricted-manager
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
restricted-manager is already the newest version.
The following packages were automatically installed and are no longer required:
  libwxgtk2.8-0 libxml++2.6c2a librainbow0c2 libwxbase2.8-0 libroboradio0c2 libcrypto++5.2c2a
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
jim@jims-computer:~$


Later. Pepse.

---

### Post by Qwerty_ on 2007-11-19
Ok try running 

```
 sudo restricted-manager
```

---

### Post by GoJa on 2007-11-19
I have a problem trying to access the restricted drivers.  I have a brand new machine running Ubuntu fiesty fawn 7.04, with nVidia 8300 GS video card, Intel Core 2 duo processors.  If I do System -> Administration -> Restricted Drivers Manager all I get is a dialog box telling me that "Your hardware does not need any restricted drivers".  I just followed your suggestion and did sudo restricted-manager.  I get the same result.

All the threads/posts I've seen tell me I need to enable the restricted driver to be able to use my video card to its potential.  Any ideas as to how I can enable the driver if the restricted manager doesn't let me?  I even updated the restricted manager package using Synaptic.  I still get the same result.  Any ideas or thoughts would be appreciated.

---

### Post by ralyon on 2007-11-19
I think I remember seeing issues with the newer nvidia cards. You might try and do a search for others with the same card.

Also for the latest drivers I have found [Envy]("http://albertomilone.com/nvidia_scripts1.html") to be very good at getting drivers to work. GL

---

### Post by Pepse3 on 2007-11-19
Qwerty_

  Okay, I did that and I get a small box that states "NVIDIA accelerated graphics driver"   The Enabled box is checked and it states it is in use.

  Ralyon,  
  I have an older Nvidia card.  It takes the newer software but it is about 3 years old.  I am thinking that if I can get to the restricted drivers page I Might be able to get things to work.

Pepse.

---

