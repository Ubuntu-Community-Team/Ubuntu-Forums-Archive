---
title: "ubuntu one music store now inoperative in rhythmbox"
date: 2010-10-22
forum: Multimedia Software
---

### Post by Tanker Bob on 2010-10-22
Everything worked fine until the recent update. I'm using Rhythmbox 0.13.1. After updating to the 1.9, I get a message saying that "Unable to activate plugin Ubuntu One Music Store". I tried reinstalling the plugin, but that didn't work. Today, one of my other repositories offered up version 1.8 disguised as 1.9.1. I installed that but it made no difference. So, I purged the plugin with Synaptic, then reinstalled it. Still won't load.

Anybody have any ideas?

---

### Post by Tanker Bob on 2010-10-23
With the help of the launchpad team, I was able to get back to even. I was using the webupd8team ppa for lucid, which apparently outran the support libraries with the latest ubuntu one plugin. I disabled the ppa, uninstalled rhythmbox and all its plugins, then reinstalled from the basic lucid repositories. Everything works now, but I'm sure that with rhythmbox 0.12.8 I lost some functionality, especially with the plugins, but I do have the ubuntu one music store back.

---

### Post by Tanker Bob on 2010-10-23
FWIW, I found Rhythmbox 0.12.8 too buggy to use, so went back to 0.13.1 and installed the PPAs listed [here](https://bugs.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/623655/comments/14). I no longer have the U1 music store, but at least Rhythmbox works better.

Since I'm still being charged the international surcharge on my credit card through Paypal using U1's UK-based store, I've decided to go directly to [http://us.7digital.com/](http://us.7digital.com/) for my music. It's all the same but without the Rhythmbox plugin hassles or international surcharges. I'll be happy to go back to using the U1 music store when Cannonical allows users to access their own country's 7Digital site and they work out the plugin bugs.

The U1 music store is a great idea for supporting Ubuntu, but the implementation on the desktop leaves much to be desired.

---

### Post by Keen101 on 2011-04-17
Thanks. I had the same problem on 8.04. Removing the lucid ppa and purging both the ubuntu one plugin and rhythmbox, and reinstalling them from the default repo seems to have worked.

---

