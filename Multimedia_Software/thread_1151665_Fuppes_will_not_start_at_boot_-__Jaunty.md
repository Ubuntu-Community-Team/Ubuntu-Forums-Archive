---
title: "Fuppes will not start at boot -  Jaunty"
date: 2009-05-07
forum: Multimedia Software
---

### Post by nickwalnut on 2009-05-07
Hi,

I've had fuppes installed on 9.04 for about a week now, and all seems to be working fine with it (all my devices can see it except the xbox 360, which is another matter). I want to get fuppes to start up at boot now without me having to log in every time, and so I followed the instructions at [http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d)

Unfortunately, the service is not apparently running when I boot up, even though I followed the instructions on the wiki to the letter. I've looked everywhere on the net for a similar problem, but have not found one, so I thought it may be an issue with how Jaunty handles startup scripts or something. I've done the same with my other ubuntu machine (also running Jaunty), and I get the same result.

Any ideas?

Thanks in advance,
nick

---

### Post by mgienke on 2009-05-17
I have the same problem. It does start, once the system is up an running, though.
I simply added a cron job that does start the daemon later on. Not nice, but works.

Michael

---

### Post by nickwalnut on 2009-10-29
Hi sorry for the post in old thread but was wondering if this has been solved yet?
 
If not, could someone please explain to me what a "cronjob" is and how to set one up to start fuppes at boot?
 
Thanks

---

### Post by Shhnap on 2009-11-04
A cronjob is a program that is set to run via a program called cron. To find out more open up your terminal and type in:

```
sudo apt-get install cron
man cron
```

Though i'm pretty sure that cron is automatically installed.

For more information on how to setup fuppes on the latest ubuntu go here: [http://ubuntuforums.org/showthread.php?t=1310511](http://ubuntuforums.org/showthread.php?t=1310511)

For information on how to make fuppes run on startup go here: [http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d)

I hope that helps.

---

### Post by repsak on 2010-02-09
I found out that (for me) the network took too long to assign an IP-adress to the eth0, because I use DHCP. And fuppes won't start if eth0 doesn't have an IP adress (can't resolve).

For me the following did the trick:

added the line that starts fuppes in /etc/rc.local:
```
su -c '/usr/bin/fuppes' - fuppes
```

but then added the sleep command to it:
```
sleep 10; su -c '/usr/bin/fuppes' - fuppes
```

This way, the /usr/bin/fuppes starts after 10 seconds (as user fuppes). It is not nice, but this is for me the only way it would work.

I tried it in System->Preferences->start at boot, didn't work.
I tried it in the init.d system, didn't work.

But with this sleep command, it works. Hopefully helping a lot of people with this.

---

### Post by nickwalnut on 2010-02-13
Thankyou so much!

LOL by chance I came back here months later to find a post that fixes everything made four days prior.

+rep

---

### Post by Shhnap on 2010-02-14
Um, can I ask what went wrong with the setup of the Init.d script? It's kinda the way that running programs on startup is supposed to be run so if it's not working then I would really like to know about it so that I can fix it. Thanks.

---

