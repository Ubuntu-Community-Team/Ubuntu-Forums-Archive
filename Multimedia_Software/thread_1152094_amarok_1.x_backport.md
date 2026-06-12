---
title: "amarok 1.x backport?"
date: 2009-05-07
forum: Multimedia Software
---

### Post by willistg on 2009-05-07
I hope I don't offend anyone with this....

Anyone know if it exists or whether it's possible to get the 1.x series of amarok on jaunty? 

Though I like where amarok 2 is going, some of the lack of features  will make it somewhat difficult to run a radio show from my laptop.

---

### Post by mr_finn on 2009-05-07
Open up Software Sources under System>Administration and on the Third Party Software tab>  Add...

Type or Copy/Paste the following two lines(one at a time)into the 'APT line:' input box and 'Add Source' for both.

```
deb http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
```
```
deb-src http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
```

Close the Software Sources window and 'Reload'.

Add the key for the PPA by pasting the following into the terminal:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \
0x1d7e9dd033e89ba781e32a24b9f1c432ae74ae63

```
Now update your sources, remove Amarok2 and install Amarok1.4(Paste one line at a time into the terminal):

```
sudo apt-get update
```
```
sudo apt-get remove amarok
```
```
sudo apt-get install amarok14
```

Xine error fix: Settings>Configure Amarok>Output Plugin(drop down menu)>Alsa

You are done.

Enjoy Amarok as it should have(in my opinion)remained!!

This is working for me as I type on Jaunty x64. and also Jaunty x32 on a secondary machine.


: ]

Respect to the original poster/hoster of the sources, I have no idea where on the net I got them from now but they still work (I just used them now) so gratz.

---

### Post by willistg on 2009-05-31
Doh, I thought I had subscribed to this thread, and I guess I haven't. Thanks so much for the info, I'm setting things right, right now. I thought I could manage with 2.1 but it started pissing me off again yesterday, and this morning I saw it was using 625M of ram, that's just not right.

---

### Post by Naatan on 2009-06-09
Doesn't work on Kubuntu 9.04 AMD64 with KDE 4.3 Beta 2.

The following packages have unmet dependencies:
  amarok14: Depends: amarok14-common (>= 2:1.4.10-0ubuntu3~ppa3) but it is not going to be installed
E: Broken packages

---

### Post by swinky on 2009-06-10
> Doesn't work on Kubuntu 9.04 AMD64 with KDE 4.3 Beta 2.

The following packages have unmet dependencies:
amarok14: Depends: amarok14-common (>= 2:1.4.10-0ubuntu3~ppa3) but it is not going to be installed
E: Broken packages 

I was using the packages in this ppa just fine up until tonight. I upgraded the packages on my computer and suddenly it uninstalled amarok14. Trying to reinstall it gives me the same error about depending on amarok14-common, even though I have the *exact same* version of amarok14-common that it wants already installed. I'm wondering if they tried to update the packages and broke something? Can anybody confirm this?

For now I have to use Amarok 2 or Exaile to play music...

---

### Post by H4rold on 2009-06-10
> **swinky said:**
> I was using the packages in this ppa just fine up until tonight. I upgraded the packages on my computer and suddenly it uninstalled amarok14. Trying to reinstall it gives me the same error about depending on amarok14-common, even though I have the *exact same* version of amarok14-common that it wants already installed. I'm wondering if they tried to update the packages and broke something? Can anybody confirm this?

For now I have to use Amarok 2 or Exaile to play music...

Exactly the same here :(

---

### Post by swinky on 2009-06-10
Did something I should have done from the get go: I looked at the maintainer's page ([https://launchpad.net/~bogdanb/+archive/ppa](https://launchpad.net/~bogdanb/+archive/ppa)) and sure enough, the amarok14 package was changed changed 9 hours ago. So for now it seems like the amarok14 package is broken. So unless somebody knows how to obtain the old version (if that is even possible) or fix the install issue themselves, we're stuck without Amarok 1.4 for now. :( Hopefully, it is fixed soon.

---

### Post by dzark on 2009-06-10
anyone got a source floating around?

---

### Post by kili9r on 2009-06-10
I had the same problems after updating today

> **dzark said:**
> anyone got a source floating around?

Luckily I still had the old amarok14 *.deb files in 

```
/var/cache/apt/archives
```

I could install them manually with ```
dpkg -i
```

You will have to look for the following filenames or similar ones:

amarok14_2%3a1.4.10-0ubuntu3~ppa2_i386.deb
amarok14-common_2%3a1.4.10-0ubuntu3~ppa2_all.deb
amarok14-engine-xine_2%3a1.4.10-0ubuntu3~ppa2_i386.deb

I have uploaded my files here in case you can not find them:

[http://www.2shared.com/file/6223745/7ccc7096/amarok14.html](http://www.2shared.com/file/6223745/7ccc7096/amarok14.html)

I have put them in a tar ball for convenience so you will have to untar it before you can install them:

```
tar xvf amarok14.tar
```

Please keep in mind that installing those packages manually is a quick and dirty workaround, so no guarantees!!!

It brought back my beloved amarok14 but that does not mean it will work for you.

---

### Post by andrewyoungisgreat on 2009-06-10
:KS kili9r, thank you.

I extracted the tar and then ran "sudo dpkg -i amarok*". I now have a working Amarok 1.4.

---

### Post by swinky on 2009-06-10
Unfortunately, I'm running 64-bit and even after tinkering with the provided files (thanks kili9er!) with some 386 compatibility it just doesn't work. Does anybody happen to have the 64 bit version in their cache? I of course happened to clear my cache recently so I don't have it.

Also, I checked the ppa about 15 minutes ago, the whole amarok14 package was taken down. I would imagine that means they are aware of the problem. Unfortunately, still no fix for it.

---

### Post by surfed on 2009-06-10
> **swinky said:**
> Unfortunately, I'm running 64-bit and even after tinkering with the provided files (thanks kili9er!) with some 386 compatibility it just doesn't work. Does anybody happen to have the 64 bit version in their cache? I of course happened to clear my cache recently so I don't have it.

Also, I checked the ppa about 15 minutes ago, the whole amarok14 package was taken down. I would imagine that means they are aware of the problem. Unfortunately, still no fix for it.


try this ppa:
deb [http://ppa.launchpad.net/surfed/ppa/ubuntu](http://ppa.launchpad.net/surfed/ppa/ubuntu) jaunty main
it has the old amarok deb 32 + 64 bit for jaunty
you can also download the debs instead of using the ppa

---

### Post by swinky on 2009-06-10
> try this ppa:
deb [http://ppa.launchpad.net/surfed/ppa/ubuntu](http://ppa.launchpad.net/surfed/ppa/ubuntu) jaunty main

Beautiful! That did the trick quite nicely. Thank you! :D

---

### Post by DougieFresh4U on 2009-06-10
I can only get the 'amarok-commom' installed and then the other 2 (amarok and amarok xine) play games telling can't install because of the other not installed. Please, I know there's a way to install all of them together but I do not know the codes or how (not a 'guru')

---

### Post by PureLoneWolf on 2009-06-10
I just found this [http://nforce-it.nl/blog/?p=321](http://nforce-it.nl/blog/?p=321) which suggests there is a different package now "amarok-kde3"

Not sure if this helps

---

### Post by DougieFresh4U on 2009-06-10
> **PureLoneWolf said:**
> I just found this [http://nforce-it.nl/blog/?p=321](http://nforce-it.nl/blog/?p=321) which suggests there is a different package now "amarok-kde3"

Not sure if this helps

No luck on that.
Thanks for suggestion :)

---

### Post by Naatan on 2009-06-10
> **surfed said:**
> try this ppa:
deb [http://ppa.launchpad.net/surfed/ppa/ubuntu](http://ppa.launchpad.net/surfed/ppa/ubuntu) jaunty main
it has the old amarok deb 32 + 64 bit for jaunty
you can also download the debs instead of using the ppa

You rock! Thanks mate! :D

Anyone know if it's possible to have KDE 3 apps integrate with KDE 4? Would be nice :) Either way I'm sticking with Amarok 1 for now :D

---

### Post by mc4man on 2009-06-10
You can install multiple .deb's by putting them all in a folder and using dpkg **as long as all the dependent packages are in the folder**. (hopefully that's the case here

If there are any additional packages needed then dpkg won't fetch them and you'll end up with a broken package(s)

Having a broken package is usually not a big deal, if the additional required packages are available from your repo sources than just open synaptic -> edit -> fix broken packages, **then click apply**. Synaptic will fetch and install the missing packages.

If they're not available then you'll need to remove the broken package(s) and get the additional dependant ones. For that open synaptic -> click on 'custom filters' and choose 'broken' and remove them.

If you want to try then create a folder, put the .debs inside, cd to the folder in a terminal and go 
```
sudo dpkg -i *.deb
```

Or just add the repo in question and install amarok (switch source list dropdown to jaunty

[https://edge.launchpad.net/~surfed/+archive/ppa](https://edge.launchpad.net/~surfed/+archive/ppa)

---

### Post by Sportingfan on 2009-06-11
> **kili9r said:**
> I had the same problems after updating today



Luckily I still had the old amarok14 *.deb files in 

```
/var/cache/apt/archives
```

I could install them manually with ```
dpkg -i
```

You will have to look for the following filenames or similar ones:

amarok14_2%3a1.4.10-0ubuntu3~ppa2_i386.deb
amarok14-common_2%3a1.4.10-0ubuntu3~ppa2_all.deb
amarok14-engine-xine_2%3a1.4.10-0ubuntu3~ppa2_i386.deb

Please keep in mind that installing those packages manually is a quick and dirty workaround, so no guarantees!!!

It brought back my beloved amarok14 but that does not mean it will work for you.

This did the trick! 

To make it clear for everybody, I did:

```

cd /var/cache/apt/archives

```

then

```

sudo dpkg -i amarok14_2%3a1.4.10-0ubuntu3~ppa2_i386.deb amarok14-engine-xine_2%3a1.4.10-0ubuntu3~ppa2_i386.deb amarok14-common_2%3a1.4.10-0ubuntu3~ppa2_all.deb 

```

Start Amarok and rediscover your music.;)

THY

---

### Post by DougieFresh4U on 2009-06-11
> **mc4man said:**
> You can install multiple .deb's by putting them all in a folder and using dpkg **as long as all the dependent packages are in the folder**. (hopefully that's the case here

If there are any additional packages needed then dpkg won't fetch them and you'll end up with a broken package(s)

Having a broken package is usually not a big deal, if the additional required packages are available from your repo sources than just open synaptic -> edit -> fix broken packages, **then click apply**. Synaptic will fetch and install the missing packages.

If they're not available then you'll need to remove the broken package(s) and get the additional dependant ones. For that open synaptic -> click on 'custom filters' and choose 'broken' and remove them.

If you want to try then create a folder, put the .debs inside, cd to the folder in a terminal and go 
```
sudo dpkg -i *.deb
```

Or just add the repo in question and install amarok (switch source list dropdown to jaunty

[https://edge.launchpad.net/~surfed/+archive/ppa](https://edge.launchpad.net/~surfed/+archive/ppa)

Thanks, don't know why other ppa didn't work but your link was great. 
amarokin now!!  :p

---

### Post by swinky on 2009-06-11
Just fyi, the other ppa ([https://edge.launchpad.net/~bogdanb/+archive/ppa](https://edge.launchpad.net/~bogdanb/+archive/ppa)) is working again. I've switched back to that ppa (simply because I still can't figure out apt pinning and don't really need the other stuff in some of these alternate ppas.)

Of course, I've backed up working versions of amarok14 .deb files, just in case. I spent a good chunk of yesterday A) Trying to get Amarok 1.4 to work or B) trying out other music players and hating them. I'd rather not have to do that again.

---

### Post by Job-scp on 2009-08-12
Thanks mr_finn.
It works great for me on a AMD 64x with kde4.

---

