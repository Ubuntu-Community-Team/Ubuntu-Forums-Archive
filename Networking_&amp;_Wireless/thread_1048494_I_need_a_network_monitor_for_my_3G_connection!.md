---
title: "I need a network monitor for my 3G connection!"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by josamoto on 2009-01-23
Can anyone recommend a good application that monitors traffic on an internet connection.

I've used Netmeter on Windows before amd was hoping for an app for Ubuntu that would allow me to monitor and keep statistics for a period of time.

I would like to be able to see traffic reports for up to a month on a day to day basis.

Thanks for the help in advance!

---

### Post by Vesperatus on 2009-01-23
I haven't tried it myself, but you could try this :

[http://gnome-look.org/content/show.php/Net+Monitor?content=72013](http://gnome-look.org/content/show.php/Net+Monitor?content=72013)


just do : sudo apt-get install screenlets

and start it at the command line :

screenlets-manager


From there, you can add it to your desktop.

---

### Post by josamoto on 2009-01-23
Thanks for the link, that looks perfect!!!

:)

---

### Post by josamoto on 2009-01-24
Tried getting the above app to work, but to no avail!

Can anyone help! There's not a lot of documentation.

---

### Post by Vesperatus on 2009-01-24
> **josamoto said:**
> Tried getting the above app to work, but to no avail!

Can anyone help! There's not a lot of documentation.

I'm not in front of my ubuntu box right now but i'll try to help. I cant remember if the app is in the default package but, anyway, just download it.

First, did you manage to install screenlets ?

If you did, did you manage to start the screenlets-manager ?

If you did, make sure you untar ( tar xfz theappname.tar.gz ) in your ~/.screenlets directory. If you did, it should appear in the screenlet manager and you should be able to start it.

I hope it helps.

---

### Post by josamoto on 2009-01-24
Hi, got the thing working but it's but ugly, themes don't work etc. So I've abandoned the whole screenlet thing.

Instead, I installed vnstat, and rigged it up with conky, and some other tutorial on beautifying it!

Works perfectly now! I can now see my daily, weekly and monthly usage statistics on my deskop.

Here are some links that helped me:

[http://www.gnome-look.org/content/show.php/CONKY-colors?content=92328]("http://www.gnome-look.org/content/show.php/CONKY-colors?content=92328")

[http://ubuntuforums.org/showthread.php?t=205865]("http://ubuntuforums.org/showthread.php?t=205865")

---

### Post by UberKnight on 2009-05-05
Would you mind posting a screenshot?

---

### Post by ingeon on 2009-11-01
sudo apt-get install systemsettings
sudo apt-get install knemo

In terminal run 'systemsettings'
Select 'network settings'
Select 'network monitor'
Tick 'Use Knemo to monitor your interfaces'
Tick 'Hide icon when not connected'
Tick 'Active statistics'

I use ultimate edition so I don`t know if it comes with Ubuntu vanilla.

Just one problem i am having with knemo is it looses my history when i shutdown my pc...

Okay. I deleted my .kde folder, removed knemo from my Ubuntu Startup Application and now manually
launch it after dialup established then it doesn`t loose my history.

---

### Post by ingeon on 2010-02-10
I have not tested it yet, but bitmeter II is now available on linux [http://codebox.org.uk/controller?page=bitmeterOsDl](http://codebox.org.uk/controller?page=bitmeterOsDl)

The only problem is it does not give the option to split between interfaces like netmeter "http://www.metal-machine.de/readerror/" and netmeter only has a windows version so far.

---

### Post by alexfish on 2010-02-10
hi

there should be a one in the repos called pppstatus, it is run from the terminal

also has a config file called pppstatus.cfg

---

### Post by r0bd on 2010-04-17
> **ingeon said:**
> I have not tested it yet, but bitmeter II is now available on linux [http://codebox.org.uk/controller?page=bitmeterOsDl](http://codebox.org.uk/controller?page=bitmeterOsDl)

The only problem is it does not give the option to split between interfaces like netmeter "http://www.metal-machine.de/readerror/" and netmeter only has a windows version so far.

Hi, 

I'm the author of BitMeter OS - just letting you know that the latest version (v0.4.0) now includes the ability to filter data according to network interface (and also by host, if you have imported data from other hosts). Feedback always welcome!

thanks

Rob D

---

### Post by ingeon on 2010-05-12
> **r0bd said:**
> Hi, 

I'm the author of BitMeter OS - just letting you know that the latest version (v0.4.0) now includes the ability to filter data according to network interface (and also by host, if you have imported data from other hosts). Feedback always welcome!

thanks

Rob D

Excellent.
My latest problem is I moved to 64bit.

---

### Post by r0bd on 2010-06-20
> **ingeon said:**
> Excellent.
My latest problem is I moved to 64bit.
[A 64-bit version of BitMeter OS is now available!]("http://codebox.org.uk/pages/bitmeteros/downloads")

---

