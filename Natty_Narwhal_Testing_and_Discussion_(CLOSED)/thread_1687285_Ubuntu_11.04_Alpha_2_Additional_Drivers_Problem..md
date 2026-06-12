---
title: "Ubuntu 11.04 Alpha 2 Additional Drivers Problem."
date: 2011-02-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by 8jwong14 on 2011-02-13
Hi everyone.  Recently, i installed Ubuntu 11.04 Alpha 2 on my computer, as always, I first installed the graphics drivers from the "Additional Drivers" window that pops up.  There are choices for "experimental 3d support for Nvidia cards" and 2 binary drivers which are nvidia-current and nvidia-173.  After installing the nvidia-current, I rebooted my computer but it seems to freeze or not do anything once it reaches the place where there is a Ubuntu logo in the center and 5 small circles under it.  

I was forced to reinstall Ubuntu 11.04 as I didn't know what else to do since I don't have the knowledge of a super Ubuntu user.  Now I didn't install any of the additional drivers.

Firstly, what is the problem and how do I solve it?
Secondly, if I have that problem again, can I remove the nvidia-current and replace it with nvidia-173 to test if it works without reinstalling.

---

### Post by Quackers on 2011-02-13
Have a look in the Natty testing forum (where this thread should really be :-)  )

[http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=394](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=394)

---

### Post by Perfect Storm on 2011-02-13
Moved to Natty Testing forum.

---

### Post by Quackers on 2011-02-13
If you have run all the updates, then you have probably upgraded xserver to 1.10.
This is a problem for nvidia cards. See the stickies and several other threads in this section.

---

### Post by 8jwong14 on 2011-02-13
> **8jwong14 said:**
> Hi everyone.  Recently, i installed Ubuntu 11.04 Alpha 2 on my computer, as always, I first installed the graphics drivers from the "Additional Drivers" window that pops up.  There are choices for "experimental 3d support for Nvidia cards" and 2 binary drivers which are nvidia-current and nvidia-173.  After installing the nvidia-current, I rebooted my computer but it seems to freeze or not do anything once it reaches the place where there is a Ubuntu logo in the center and 5 small circles under it.  

I was forced to reinstall Ubuntu 11.04 as I didn't know what else to do since I don't have the knowledge of a super Ubuntu user.  Now I didn't install any of the additional drivers.

Firstly, what is the problem and how do I solve it?
Secondly, if I have that problem again, can I remove the nvidia-current and replace it with nvidia-173 to test if it works without reinstalling.
Oops.  I didn't know there was a testing forum for ubuntu.

---

### Post by 8jwong14 on 2011-02-13
> **Quackers said:**
> If you have run all the updates, then you have probably upgraded xserver to 1.10.
This is a problem for nvidia cards. See the stickies and several other threads in this section.
Would you mind telling me what stickies and threads I should look at please?

---

### Post by Quackers on 2011-02-13
No problem. Neither did I until I had a thread moved here :wink:

---

### Post by Quackers on 2011-02-13
The top sticky and some of the more recent posts in it would be a good place to start. It basically relates how the upgrade to xserver breaks all existing nvidia drivers. No fix is currently available (as nvidia haven't yet released a new driver), however, it is possible to downgrade xserver back to 1.9, which should leave your nvidia driver working - as I understand it!

---

### Post by farooq23 on 2011-02-14
Yes, downgrading xserver to 1.9 fixes nvidia driver issue.

---

### Post by 8jwong14 on 2011-02-15
> **farooq23 said:**
> Yes, downgrading xserver to 1.9 fixes nvidia driver issue.
And how do I downgrade?  When Nivida does release the fix, I can easily upgrade back using the system update right?

---

### Post by 8jwong14 on 2011-02-15
> **Quackers said:**
> The top sticky and some of the more recent posts in it would be a good place to start. It basically relates how the upgrade to xserver breaks all existing nvidia drivers. No fix is currently available (as nvidia haven't yet released a new driver), however, it is possible to downgrade xserver back to 1.9, which should leave your nvidia driver working - as I understand it!
Also, would you mind posting in this thread if Nivida does release a new?

---

### Post by cariboo on 2011-02-15
> **8jwong14 said:**
> Also, would you mind posting in this thread if Nivida does release a new?

You'll see an updated nvidia-current in the repositories when a new driver becomes available.

I'm sure there will be plenty of notice in this sub-forum when the driver is released.

---

### Post by 8jwong14 on 2011-02-16
> **cariboo907 said:**
> You'll see an updated nvidia-current in the repositories when a new driver becomes available.

I'm sure there will be plenty of notice in this sub-forum when the driver is released.
Thanks.  To scheck for new drivers I can sue the "additional Drivers" to check right?

---

### Post by cariboo on 2011-02-16
I suggest you use Synaptic Package Manager to do your updates, click on the status button on the lower left, then click reload, you'll see installed (upgradeable), in the left pane, click that to show all the upgradeable packages on the right.

---

### Post by 8jwong14 on 2011-02-25
> **cariboo907 said:**
> I suggest you use Synaptic Package Manager to do your updates, click on the status button on the lower left, then click reload, you'll see installed (upgradeable), in the left pane, click that to show all the upgradeable packages on the right.
So I just look at for the part that involves Nividia drivers I assume?

---

### Post by Harry33 on 2011-02-25
> **8jwong14 said:**
> So I just look at for the part that involves Nividia drivers I assume?

The new NVidia drivers (nvidia-current_270.29) supporting xserver 1.10 are now in Natty official repos.
This means you can now fully upgrade your system.
If you cannot start X, then run recovery mode from grub menu.
and then run these commands:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by 8jwong14 on 2011-02-25
> **Harry33 said:**
> The new NVidia drivers (nvidia-current_270.29) supporting xserver 1.10 are now in Natty official repos.
This means you can now fully upgrade your system.
If you cannot start X, then run recovery mode from grub menu.
and then run these commands:
```
sudo apt-get update
sudo apt-get upgrade
```
Yes!  I will try that.  Hope it works!

Wait...How do I install it?

OI jsut ran a systme update and now, in "additional Drivers", I don't see the option to install that.  Did the update install it?

I see Synaptic only has nvidia-current_270.19.29-0ubuntu1

---

### Post by Harry33 on 2011-02-25
> **8jwong14 said:**
> Yes!  I will try that.  Hope it works!

Wait...How do I install it?

OI jsut ran a systme update and now, in "additional Drivers", I don't see the option to install that.  Did the update install it?

I see Synaptic only has nvidia-current_270.19.29-0ubuntu1

New nvidia-current is in official repos.
Here:
[https://launchpad.net/ubuntu/natty/+source/nvidia-graphics-drivers/270.29-0ubuntu2](https://launchpad.net/ubuntu/natty/+source/nvidia-graphics-drivers/270.29-0ubuntu2)

---

### Post by 8jwong14 on 2011-02-25
> **Harry33 said:**
> New nvidia-current is in official repos.
Here:
[https://launchpad.net/ubuntu/natty/+source/nvidia-graphics-drivers/270.29-0ubuntu2](https://launchpad.net/ubuntu/natty/+source/nvidia-graphics-drivers/270.29-0ubuntu2)
Sorry for asking so much but how do I download it and then install it?

---

### Post by cariboo on 2011-02-25
The nvidia 270.29 is in the repositories, use the usual methods to install it, The Software Center, Synaptic or the command line.

---

### Post by 8jwong14 on 2011-02-26
> **cariboo907 said:**
> The nvidia 270.29 is in the repositories, use the usual methods to install it, The Software Center, Synaptic or the command line.
I tried Synaptic but I only see version 260.19.29 at most recent.  

Sadly, I don't know the otehr methods to install 270.29.  270.29 isn't in "additional drivers" either.

---

### Post by Harry33 on 2011-02-26
> **8jwong14 said:**
> I tried Synaptic but I only see version 260.19.29 at most recent.  
Sadly, I don't know the otehr methods to install 270.29.  270.29 isn't in "additional drivers" either.

Check from software-properties-gtk, that your system uses "Main server" to download the updates.

---

### Post by 8jwong14 on 2011-02-26
> **Harry33 said:**
> Check from spoftware-properties-gtk, that your system uses "Main server" to download the updates.
In the Ubuntu software tab, I ahve everything checked checked/bolded in.

---

### Post by Harry33 on 2011-02-26
> **8jwong14 said:**
> In the Ubuntu software tab, I ahve everything checked checked/bolded in.

Yes OK, I wonder do you need the box "source" checked.
But, what server is listed in the box "download from"?

---

### Post by 8jwong14 on 2011-02-26
> **Harry33 said:**
> Yes OK, I wonder do you need the box "source" checked.
But, what server is listed in the box "download from"?
Oh.  I changed it from downlaod from server from US to Main Server.  Now I see 270.29.  Thanks a lot.    In general, is it best to use the main server?

---

### Post by mc4man on 2011-02-26
> In general, is it best to use the main server? 
you can get updates a bit earlier, though in this case the us servers have had the package for awhile
You should always update your sources if something isn't showing up that should
```
sudo apt-get update
```
(when you switched servers you likely updated your sources

---

### Post by ktp on 2011-02-26
For alpha version, I try to stay with the main so don't have to worry about delay in syncing the repositories.  This can be good or bad but only reason I am running alpha is to test to I want the latest as soon as possible.

---

### Post by cariboo on 2011-02-26
+1 for the Main Server during testing. I normally use the Main Canadian server, but have found it to be a couple of hours behind the Main Server.

---

### Post by 8jwong14 on 2011-02-28
Thanks for all your help everyone!  NAtty is working fine now.

---

### Post by 8jwong14 on 2011-02-28
> **cariboo907 said:**
> +1 for the Main Server during testing. I normally use the Main Canadian server, but have found it to be a couple of hours behind the Main Server.
When I am using a normal release and not testing, it would be best to stick with the American Server right?

---

### Post by Harry33 on 2011-02-28
> **8jwong14 said:**
> When I am using a normal release and not testing, it would be best to stick with the American Server right?

There is only one thing to take into consideration, others are merely opinions or habits.
The main server is the first to be uploaded. That means you get upgrades and updates sooner.
That brings us to another consideration.
Would it be safer to get updates a bit (generally one day) later, so that occasional bugs could have been solved by then.
And this is true. In case of a buggy update is uploaded, it finds its way into the main server first. If this particular update is then cancelled or superseded, it may very well be that slower servers do not even get uploaded by the buggy version, saving you from trouble.

:lolflag: But then again, you do not get a change to test that bugger either.

---

