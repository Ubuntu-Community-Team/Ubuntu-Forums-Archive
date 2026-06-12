---
title: "[SOLVED] Banshee 1.2.1 crashes with Creative Zen"
date: 2008-11-04
forum: Multimedia Software
---

### Post by Jompa on 2008-11-04
After I updated my Ubuntu from 8.04 to 8.10 Banshee has started crashing when I plug in my Creative Zen player. It worked fine before the update, but now I can't even use Banshee while the Zen is plugged in. I have the latest version of Banshee (1.2.1) and enjoy the player, so it would be nice to continue using it.

Here is the error I get:
```
=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================
```

---

### Post by Jompa on 2008-11-06
Noone that can help me with this problem?

---

### Post by Neo40 on 2008-11-07
I have the same problem. :( 
Worked great with Hardy and Banshee 1.0
Anyone can help??

---

### Post by Twexcom on 2008-11-14
This is what I use to automatically mount my Creative Zen as a USB drive: [http://www.kompulsa.com/it/itdownloads.php](http://www.kompulsa.com/it/itdownloads.php)

---

### Post by Jompa on 2008-11-15
I tried it, but it can't open the script
```
sh: Can't open mtpmount
```

---

### Post by czescik on 2008-11-15
banshee in 8.10 uses libmtp8 where banshee in 8.04 uses libmtp7. 
So here is what you need to do:

uninstall "interpid" banshee

> sudo apt-get remove banshee

download "hardy" banshee from website (important!!) because banshee in repository of 8.10 is meant to be working with libmtp8.

> wget http://ubuntu.uni-klu.ac.at/ubuntu/pool/universe/b/banshee/banshee_0.13.2+dfsg-9_i386.deb 

then install downloaded package

> sudo dpkg -i banshee_0.13.2+dfsg-9_i386.deb

this banshee downloaded from website will install libmtp7 so thats it.. you got working banshee. 

There are one problem: you'll get notification to update to newest banshee which is annoying... You can find stop version in Synaptic wich will stop updating banshee...

Cheers:guitar:

---

### Post by ukblacknight on 2008-11-15
Banshee 1.4.1 is out, you may wish to give that a try first!

You'll need to add the following repo's (System > Administration > Software Sources > Third Party Software > Add):

```

deb http://ppa.launchpad.net/banshee-team/ubuntu intrepid main
deb-src http://ppa.launchpad.net/banshee-team/ubuntu intrepid main

```

After it's reloaded, you should be notified of an update available.

---

### Post by Jompa on 2008-11-16
It works fine with the newest Banshee :) They have also fixed it so that you can see which videos you have on your player now.

Thanks for all the help :)

---

### Post by sama_j on 2008-11-17
I have "Samsung YP-K3" x2. The first one I plugged in works a treat with the new Banshee. The second one causes > 

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

After this error the first one will still work. The second one gives the error every time. 

Any Ideas??

---

### Post by almalaci on 2008-11-20
I have the Samsung YP-U3 and it works fine with these repos and the new version, thanks ukblacknight.
sama_j: If you have two of the same players, you should check if they have the same firmware. Or try formatting the one that doesn't work.


> **sama_j said:**
> I have "Samsung YP-K3" x2. The first one I plugged in works a treat with the new Banshee. The second one causes > 

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

After this error the first one will still work. The second one gives the error every time. 

Any Ideas??

---

