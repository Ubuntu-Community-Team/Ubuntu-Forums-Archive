---
title: "HTS Tvheadend, 2.9 quick guide"
date: 2010-01-28
forum: Multimedia Software
---

### Post by Gorlist on 2010-01-28
Hi, just a quick post in regards to Tvheadend. Brilliant TV/EPG backend, nice alternative to Myth etc.

[http://lonelycoder.com/hts/](http://lonelycoder.com/hts/)

Hopefully you won't have todo the following...

If anyone is trying to install it through package manager with the current build (2.9), you may have to remove and re-add the user "hts" through the terminal. 

```
sudo userdel -r hts
sudo adduser hts
```

Then re-run the configuration:

```
sudo dpkg-reconfigure hts-tvheadend
```

The reason is without doing this you may not be able to "su" over to configure xmltv (which has to be done for the hts user).

Example:

```
sudo su hts
usr/bin/tv_grab_uk_rt --configure
```

I did think you might be able to run it as your own user then copy over the hidden .xmltv folder into hts, but im not sure if tvheadend is storing the configuration correctly until you delete and re-add the account.

Afterwards, reboot and run the admin webpage. Recommend adding an access control first ( use the default and just enable the services you want. in my case all).

Setup your xmltv, for the UK im having to use the Radio Times source (you maybe able todo this last). 

Then go to "TV Adapters" and select your DVB card, and save settings. Hopefully it will automatically detect your mulitplex's, however for me I had to add them manually using the correct data from "/usr/share/dvb/dvb-t" (and of course most of that is now out of date with the digital switchover).

Make sure everything is saved, and at this point I had to reboot before it found any services. After it does (hopefully) go back to "TV Adapters" and selecting your DVB card and press "Map DVB services to channels".

Again reboot. 

Finally when you next load it should setup the EPG data, and with anyluck everything will be working :)

Worth noting in version 2.9 live stream is broken, best just to record the program and simply open the file (as its recording) in your favorite media player.

---

### Post by l.capriotti on 2010-01-28
you can also consider to run tvheadend under your user account to avoid the need to sudo into hts, and/or have an hts user.

content of: /etc/default/tvheadend:
```

DAEMON_ARGS="-f -u YOURUSERNAME -g video"

```

---

