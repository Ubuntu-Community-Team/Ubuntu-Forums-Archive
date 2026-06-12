---
title: "Wireless with shell script?"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by DejitaruJin on 2009-10-05
I'm in an emergency situation where I need to very quickly create a shell script that will activate wireless, download a couple packages, and run SSH so I can remotely control this system. Thing is, this is a LiveCD I'm working with, which seems to be causing problems. Anything involving iwconfig just isn't working; it says it's connected to the access point, but it actually isn't and dhclient fails. Using the NetworkManager GUI applet works perfectly fine for connecting, but I don't know how I would script that. Please help!

---

### Post by DejitaruJin on 2009-10-05
Bump? I've got maybe two hours before I need to drive 350 miles back home - from where I will either be able to do my job, or not, depending on whether I can make this work.

---

### Post by kevdog on 2009-10-05
How does iwconfig not work?  I don't understand.

---

### Post by t0mppa on 2009-10-05
How about just resorting to the good old [command line practices]("http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html")?

---

### Post by DejitaruJin on 2009-10-06
Well, iwconfig just wouldn't do anything. I could use ifconfig to bring the device "up" and even give it a static IP address, but iwconfig would not work at all to actually connect to an access point - it would remain "Not-Associated". That is, until someone had already tried connecting with the NetworkManager applet, thus creating the "keyring" (the purpose of which I've never been able to understand). I have reason to believe this is the source of the problem; once the keyring had been created, regardless of what was involved in doing it, iwconfig as a whole would work perfectly fine.

Unfortunately, I have no idea how to get that keyring created through the command line, which is pretty important when making a bash script. And it's a shame, too, because as long as the keyring was created first, the rest of my script worked perfectly. But, on the bright side, that's not what ended up bringing this effort to an end - it turns out my mother's 2wire modem/router has a widely-reported and irreparable bug that causes all port-forwarding to fail entirely, so it will never allow SSH anyways.

---

### Post by slakkie on 2009-10-06
Maybe give this a try.

[https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic)

There is also a way to use wpa- directives directly into /etc/network/interfaces, but I never tried it.

---

### Post by DejitaruJin on 2009-10-07
Interesting, perhaps it is not the creation of a keyring, but the initialization of encryption that allows the script to connect after it's been done once manually. However, that's easily venturing into "I'd rather not have to script all this" territory, with a big load of "there's no reason for it to be this complicated" along for the ride. It's also a bit odd that it needs a whole new package downloaded when doing it that way, if NetworkManager doesn't need anything of the sort.

---

