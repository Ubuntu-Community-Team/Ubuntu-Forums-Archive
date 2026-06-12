---
title: "Issues while upgrading JACK"
date: 2009-01-14
forum: Multimedia Software
---

### Post by originalsynthesis on 2009-01-14
Hey all,

I make the mistake of trying to upgrade jack to the more recent 0.116.2 version, without realizing at first that ubuntu isn't going to work with it:mad:  My question may be beg. talk material, but ive put it here since it relates to JACK. 
  
 Indeed, the new version doesn't work, as I immediately was no longer able to connect to the JACK server, even by qjackctl. So im gonna switch back. 

 What seems to me to be the best/simplest idea is to go into synaptic and remove jackd and redownload the .109 version. Buuuuut, syn says that i have to delete Ardour and every audio program that uses JACK. So my question is: Do I really have to do this?  Is there an alt.? 

 BTW, the upgrade I did was from a source code tarball, and the compile seemed to go just fine. This is another reason why i'm asking this, as the install flew underneath synaptic's radar, and i dont even know if synaptic will clean this up.   

suggestions? insults?

---

### Post by originalsynthesis on 2009-01-14
well, i went ahead and tried a complete removal of jack from synaptic. It took qjackctl and ubuntustudio audio with it. Reboot+Reinstalling+reboot did not work.  i get the "could not connect to jack server as client mess." it also says:

```
could not open driver .so '/usr/lib/jack/jack_dummy.so': /usr/lib/jack/jack_dummy.so: undefined symbol: jack_driver_nt_init
could not open driver .so '/usr/lib/jack/jack_oss.so': /usr/lib/jack/jack_oss.so: undefined symbol: jack_driver_init
could not open driver .so '/usr/lib/jack/jack_freebob.so': /usr/lib/jack/jack_freebob.so: undefined symbol: jack_driver_nt_init
could not open driver .so '/usr/lib/jack/jack_alsa.so': /usr/lib/jack/jack_alsa.so: undefined symbol: jack_driver_nt_init
could not find any drivers in /usr/lib/jack!
jackd: no drivers found; exiting
```
 
going to the usr/lib/jack folder and opening any of the driver files w/ mousepad gets me this:
                 
 > ELF  (text editor couldn't even open it)

seems like a mean joke, doesn't it?

This leads me to believe that upgrade i installed is causing this, or i dont know how to open up a .so file.  Anyone know what to do here?

---

### Post by originalsynthesis on 2009-01-14
i also notice i've got a file in usr/lib/ called libjack 0.100 which is identical to the one called simply 'jack' in the same directory.

---

### Post by originalsynthesis on 2009-01-15
](*,)

---

### Post by originalsynthesis on 2009-01-17
Well, I got jack going again, but not by reverting back to old .109. Through the jack dev mailing list, i found a PPA by one of the Dev guys who has ported the .116 version of JACK to work with Hardy. For all of you using 8.04 with jack woes, these can be found here: 

[https://launchpad.net/~danmbox/+archive](https://launchpad.net/~danmbox/+archive)

or just add : 
deb [http://ppa.launchpad.net/danmbox/ubuntu](http://ppa.launchpad.net/danmbox/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/danmbox/ubuntu](http://ppa.launchpad.net/danmbox/ubuntu) hardy main
 to sources.list

and a link to his blog on the packages:
[http://www.omnigia.com/news/2008/12/21/update-hardy-audio-music-tools/](http://www.omnigia.com/news/2008/12/21/update-hardy-audio-music-tools/)

Though, to be fair, I have to warn that although Jack and my audio apps work again, and several of them w/ improvement/ ardour has taken a hit on performance. I cant say if that is a fault of the upgrade, or residuals of my failed first attempt to upgrade. So, if anyone tries this, let me know how it goes for you. On the positive side though, Ive discovered i really like rosegarden and dont actually need to use Ardour all the freakin time since I primarily use my computer to help in songwriting. Also, Jack seems to be able to handle more apps, in general. Before, running hydrogen, a sequencer, and jackrack would really maul my system and inevitably crash the whole thing (this is an older toshiba laptop, btw) 
. Now, It handles all that fairly well as long as I dont go too nuts on production.

Praise be to JAH and Dan Muresan!

---

