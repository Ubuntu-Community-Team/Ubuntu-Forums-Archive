---
title: "How to remove Gnome 3 from Ubuntu 11.04"
date: 2011-04-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by duranl on 2011-04-11
I have Ubuntu 11.04 Beta installed.  I wanted to try out Gnome 3.0, so I followed this website's intructions: [http://news.softpedia.com/news/How-to-Install-GNOME-3-on-Ubuntu-11-04-194085.shtml](http://news.softpedia.com/news/How-to-Install-GNOME-3-on-Ubuntu-11-04-194085.shtml)

The Gnome 3 isn't working properly and I get tons of error messages.  I can't even report the errors because it says that I don't have a valid Ubuntu distro installed.  Plus, the machine is running slower.

How can I revert back to regular Ubuntu without the Gnome 3?

Also, I'm a newb with Ubuntu.

Thanks in advance!

---

### Post by KegHead on 2011-04-11
Hi!

Try:

System...admin...login screen.

Login and change to classic.

Should work!

KegHead

---

### Post by coffeecat on 2011-04-11
Most of us following the [Gnome 3 PPA thread]("http://ubuntuforums.org/showthread.php?t=1722627") in the Natty subforum are using a "spare" installation or partition to try this out, with no thought of reverting back if things go wrong.

It would take an experienced person a long time to uninstall all the gnome 3 stuff and revert the system to a standard Natty - and with no guarantee of success. If you are new to Ubuntu, I suggest you cut your losses and re-install.

If you need to rescue personal files you can do that with the live CD and if you need help with this, post back with what you need.

---

### Post by duranl on 2011-04-11
> **KegHead said:**
> Hi!

Try:

System...admin...login screen.

Login and change to classic.

Should work!

KegHead

Tried that.  I get a "Failed to load Ubuntu Classic'" error and get sent back to the login screen.  I can only login to Ubuntu Gnome Shell desktop and recovery console.

---

### Post by bapoumba on 2011-04-11
Moved to Natty.

---

### Post by duranl on 2011-04-11
> **coffeecat said:**
> Most of us following the [Gnome 3 PPA thread]("http://ubuntuforums.org/showthread.php?t=1722627") in the Natty subforum are using a "spare" installation or partition to try this out, with no thought of reverting back if things go wrong.

It would take an experienced person a long time to uninstall all the gnome 3 stuff and revert the system to a standard Natty - and with no guarantee of success. If you are new to Ubuntu, I suggest you cut your losses and re-install.

If you need to rescue personal files you can do that with the live CD and if you need help with this, post back with what you need.


Should I try to update ubuntu or format the hard drive and re-install from scratch?

---

### Post by Harry33 on 2011-04-11
> **coffeecat said:**
> Most of us following the [Gnome 3 PPA thread]("http://ubuntuforums.org/showthread.php?t=1722627") in the Natty subforum are using a "spare" installation or partition to try this out, with no thought of reverting back if things go wrong.

It would take an experienced person a long time to uninstall all the gnome 3 stuff and revert the system to a standard Natty - and with no guarantee of success. If you are new to Ubuntu, I suggest you cut your losses and re-install.

If you need to rescue personal files you can do that with the live CD and if you need help with this, post back with what you need.

+1
Probably the best thing to do.

---

### Post by KegHead on 2011-04-11
Hi!

One more try!

System setting...login screen.

Change via this method.

You might need to restart.

Let us know is this works!

Other option is a reinstall.

KegHead

---

### Post by coffeecat on 2011-04-11
> **duranl said:**
> Should I try to update ubuntu or format the hard drive and re-install from scratch?

You could try updating from the command line and hope the updates sort things out, but I don't hold out much hope of achieveing anything except wasting downloads. I'm posting from a working (sort-of) gnome 3 in Natty courtesy of the same PPA, and I'm downloading over 200MB of updates that have become available since yesterday.

I think you need to re-install.

---

### Post by sgage on 2011-04-11
> **duranl said:**
> I have Ubuntu 11.04 Beta installed.  I wanted to try out Gnome 3.0, so I followed this website's intructions: [http://news.softpedia.com/news/How-to-Install-GNOME-3-on-Ubuntu-11-04-194085.shtml](http://news.softpedia.com/news/How-to-Install-GNOME-3-on-Ubuntu-11-04-194085.shtml)

The Gnome 3 isn't working properly and I get tons of error messages.  I can't even report the errors because it says that I don't have a valid Ubuntu distro installed.  Plus, the machine is running slower.

How can I revert back to regular Ubuntu without the Gnome 3?

Also, I'm a newb with Ubuntu.

Thanks in advance!

And I quote:

"This is intended to be installed on a fresh install of the latest natty beta. DO NOT install this on a production machine, THERE IS NO DOWNGRADE PATH. THIS HAS NO WARRANTY, AND IT COULD SERIOUSLY MESS THINGS UP."

Just re-install.

---

### Post by 5149.5 on 2011-04-11
Last week I decided to try G3 and it really hosed up my system. I booted from a USB stick and did an upgrade. It was very similar to a reinstall but retained most of my configuration and settings.

---

### Post by pgawron on 2011-04-12
I just experienced the same thing. When I tried to submit crash reports it told me that it wasn't an official gnome version.  I could not log into classic or Unity.

I installed ppa-purge and removed the ppa package that I used to get gnome 3.  PPA-purge removed the repository and automatically did an apt-get update and told me it wanted to remove many packages and downgrade several others.  After clearly laying out what it wanted to do, it asked me if I wanted to accept this solution. 

I said "yes". 

After it did it's thing I rebooted back into Unity and everything works as before :)

I hope this works for others as well.

---

### Post by KegHead on 2011-04-12
Hi pgawron!

Congrats!

Are you using Ubuntu classic?

I am:

11.04b2/classic/2.6.39-999

KegHead

---

### Post by duranl on 2011-04-12
I booted from the Ubuntu 11.04b cd and did an upgrade.  The Gnome 3 is gone and everything seems normal.  Except, I am getting errors every once in a while, which never happened before.  Once the semester is over and the good edition of 11.04 comes out, I'm going to wipe my hard drive and do a fresh install.

Thanks for the help, everyone! ):P

---

### Post by KegHead on 2011-04-12
Hi!

Under tread tools mark your tread as solved!

KegHead

---

### Post by jcrow on 2011-04-12
I messed up my system back on alpha 3. To fix it I disabled the gnome 3 ppa then uninstalled each package from the ppa using synaptic and reinatalled the current package. It took a while, but i didn't have to reinstall.

---

### Post by rajeev1204 on 2011-04-12
Yes, i advise you to install the ppa-purge package in the future and then remove it.It doesnt display any messages while running but will download and later present a few options and restore your previous sources list and other files i believe.

usage is :  sudo ppa-purge ppa : name

---

### Post by reebomber on 2011-04-15
> **pgawron said:**
> I just experienced the same thing. When I tried to submit crash reports it told me that it wasn't an official gnome version.  I could not log into classic or Unity.

I installed ppa-purge and removed the ppa package that I used to get gnome 3.  PPA-purge removed the repository and automatically did an apt-get update and told me it wanted to remove many packages and downgrade several others.  After clearly laying out what it wanted to do, it asked me if I wanted to accept this solution. 

I said "yes". 

After it did it's thing I rebooted back into Unity and everything works as before :)

I hope this works for others as well.

It works!!! Congrats man. And how amazing it is that all the hard-core ubuntu people said it was impossible and you just nailed it!! Excellent job! Thanks (you saved me)

---

### Post by Visceral Monkey on 2011-04-16
Both the Gnome 3 install and Gnome 3 un-install instructions from here worked for me: [http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3](http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3)

---

### Post by nanouser on 2011-04-16
After doing the ppa-purge it might also be a good idea to re-enable the Gnome 3 PPA in Synaptic to look for any left over packages and remove them. When I did this I found about 18 Gnome 3 packages still installed. After removing them just disable or remove the PPA again. Running Computer Janitor may also clean them out.

---

### Post by Sunsetpfff on 2011-04-17
[http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3](http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3)

worked for me, no need for reinstaling whole system :D

---

### Post by zoonzox on 2011-04-17
I had the exact same problem, and i managed to fix it pretty easily. I loaded up an Ubuntu 11.04 live cd, and chose the upgrade option. (Even though i was already using 11.04) I let it go through the upgrade process, and when it was done, my computer booted up, i chose Ubuntu classic as my desktop environment (because i am not a fan of unity) and it started it normally with all of my programs and files still there with no sign of gnome 3 in sight. I hope this helps.

---

