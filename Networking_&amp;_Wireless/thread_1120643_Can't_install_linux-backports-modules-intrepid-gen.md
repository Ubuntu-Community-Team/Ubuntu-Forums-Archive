---
title: "Can't install linux-backports-modules-intrepid-generic"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by tadzio on 2009-04-09
Hello

I am trying to install "linux-backports-modules-intrepid-generic" to get my Atheros WIFI working.
However when i run the following commnd:

```

sudo aptitude install linux-backports-modules-intrepid-generic

```

...it tells me "Couldn`t find any package ..... matched linux-backports-modules-intrepid-generic"

I have also downloaded and tried to install linux-backports-modules-intrepid-server_2.6.27.11.14_i386.deb and this too gives me the same error above i.e. cannot find package.

Also if i run double click the latter package, the Package Installer dialog popups up saying:

**Error: Dependency is not satisfiable: linux-backports-modules-2.6.27-11-server.**

Any ideas would be appreciated.

Troy

---

### Post by coffeecat on 2009-04-09
Have you enabled the backports repository? Have a look in Synaptic: Settings > Repositories > Updates tab.

---

### Post by tadzio on 2009-04-09
Hi 

Thanks for the prompt response!

I went to Settings > Repositories > Updates tab and clicked [B]Unsupported updates (intrepid-backports).
[/B]
However I get an error when I do this (as my Wifi isn't working this makes sense - i cannot access the internet)

Example of error text:

W: Failed to fetch [http://es.archive.ubuntu](http://es.archive.ubuntu) ... could not resolve 'es.archive.ubuntu.com'
 ...
many similar lines follow.

Is there another way ... ?

Regards 
T

---

### Post by coffeecat on 2009-04-09
OK. Yes, you're right. It's because you have no internet connection that you get that error. The simplest way would be to connect your machine with an ethernet cable to do the downloads you need. And you need an internet connection to do a 'Reload' in Synaptic to update the repository metadata first. Can you connect with an ethernet cable? Do you have access to your own router?

The only other way would be to download all the packages you need and install them manually.

> Also if i run double click the latter package, the Package Installer dialog popups up saying:

**Error: Dependency is not satisfiable: linux-backports-modules-2.6.27-11-server.**I guess what you'd have to do is to download that second package and then double-click on that, and if you get another dependency error, download a third package, and so. And then install them in reverse order. That's why plugging in an ethernet cable would be simpler. Synaptic will deal with the dependencies for you.

---

### Post by tadzio on 2009-04-09
Hi

OK I have connected an ethernet cable to my router now.

Not sure what to do now ... how do I get the connection configured?

Thanks for your help btw ...

Tadzio

---

### Post by tadzio on 2009-04-09
Ignore my last post.  I am now connected with the ethernet.
Will now update the repository..

---

### Post by tadzio on 2009-04-09
Hi Coffeecat

Wifi Works!

I have updated my repositiries and then I re-ran the command :

sudo aptitude install linux-backports-modules-intrepid-generic

This gave me a new Hardware Driver:

Support for 5xxx series of Atheros 802.11 wireless LAN cards

After rebooting it detected wireless.

Excellent.  Thanks for your help.  Now I might be able to start my defection from Windows....;)

Cheers,
Tadzio

---

### Post by coffeecat on 2009-04-09
I'm pleased.

> **tadzio said:**
> Now I might be able to start my defection from Windows.... :wink:

Now that's something I can wish you good luck with from the bottom of my heart. :p

**Edit:** by the way, if you want to play multimedia files and are baffled/frustrated by the lack of proprietary codecs, flash, and so on, now that you have an internet connection, install the ubuntu-restricted-extras package. You won't regret it. And if you want to play commercial DVDs, enable the [medibuntu repository](https://help.ubuntu.com/community/Medibuntu) and install libdvdcss2.

---

### Post by tadzio on 2009-04-09
Thanks for the info.  I cannot find the ubuntu-restricted-extras in Synaptics Package Manager - do i just download it from a site and install it?  On the following link they mention installing other packages which are necesarry for it ...

[http://packages.ubuntu.com/gutsy/ubuntu-restricted-extras](http://packages.ubuntu.com/gutsy/ubuntu-restricted-extras)

---

### Post by coffeecat on 2009-04-09
> **tadzio said:**
> I cannot find the ubuntu-restricted-extras in Synaptics Package Manager

Have you got the multiverse repository enabled? That's where you'll find it. You seem to be having a bit of repository trouble today. :wink: I thought multiverse was enabled by default. Whatever - while you're about it, check that universe is also enabled. Ubuntu with only the main and restricted repositories is a bit bland.

---

### Post by tadzio on 2009-04-09
> Have you got the multiverse repository enabled? That's where you'll find it. You seem to be having a bit of repository trouble today. I thought multiverse was enabled by default. Whatever - while you're about it, check that universe is also enabled. Ubuntu with only the main and restricted repositories is a bit bland.

Both multiverse & universe were enabled (sounds quite surreal)
But I noticed the download server was for Spain which is where I am so made sense.  I changed it to Main Server and after clicking Reload it seems to have pulled in the ubuntu-restricted-extras.

Now I can see flash etc.  Again many thanks for your time Coffeecat.

---

