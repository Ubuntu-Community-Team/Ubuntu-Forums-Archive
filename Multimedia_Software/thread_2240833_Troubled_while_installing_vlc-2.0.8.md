---
title: "Troubled while installing vlc-2.0.8"
date: 2014-08-22
forum: Multimedia Software
---

### Post by Rahul04789 on 2014-08-22
Hi friends,

I downloded vlc-2.0.8 source code and started installing it.
I did the following steps.
step 1: ./configure
Step 2: make
Step 3: make install

Step 1 and 2 were successful.
but will running step 3 I got following error.

rahul@rahul-VPCEG28FN:~/Gstreamer/vlc-2.0.8$ make install
make  install-recursive
make[1]: Entering directory `/home/rahul/Gstreamer/vlc-2.0.8'
Making install in compat
make[2]: Entering directory `/home/rahul/Gstreamer/vlc-2.0.8/compat'
make  install-am
make[3]: Entering directory `/home/rahul/Gstreamer/vlc-2.0.8/compat'
make[4]: Entering directory `/home/rahul/Gstreamer/vlc-2.0.8/compat'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/rahul/Gstreamer/vlc-2.0.8/compat'
make[3]: Leaving directory `/home/rahul/Gstreamer/vlc-2.0.8/compat'
make[2]: Leaving directory `/home/rahul/Gstreamer/vlc-2.0.8/compat'
Making install in doc
make[2]: Entering directory `/home/rahul/Gstreamer/vlc-2.0.8/doc'
make[3]: Entering directory `/home/rahul/Gstreamer/vlc-2.0.8/doc'
make[3]: Nothing to be done for `install-exec-am'.
 /bin/mkdir -p '/usr/local/share/doc/vlc'
 /usr/bin/install -c -m 644 bugreport-howto.txt fortunes.txt intf-vcd.txt '/usr/local/share/doc/vlc'
/usr/bin/install: cannot remove `/usr/local/share/doc/vlc/bugreport-howto.txt': Permission denied
/usr/bin/install: cannot remove `/usr/local/share/doc/vlc/fortunes.txt': Permission denied
/usr/bin/install: cannot remove `/usr/local/share/doc/vlc/intf-vcd.txt': Permission denied
make[3]: *** [install-docDATA] Error 1
make[3]: Leaving directory `/home/rahul/Gstreamer/vlc-2.0.8/doc'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/rahul/Gstreamer/vlc-2.0.8/doc'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/rahul/Gstreamer/vlc-2.0.8'
make: *** [install] Error 2


Please tell me what is wrong. I am not able to figure out.

Thanks

---

### Post by Dreamer Fithp Apprentice on 2014-08-22
Try going through the installation procedure again (I presume you have some sort of crib sheet listing the steps) but this time prefix all commands with "sudo ". It should ask for your password, at least once. When it does, type it in and press <enter>.

That may not be the problem, but usually when you see error messages like "Permission denied" or "Are you root?", that's a strong probability. The reason the VLC instructions didn't include the "sudo" is essentially that Ubuntu and its derivatives use sudo and related commands and permissions in a very eccentric manner. VLC's instructions probably assumed you were working with a root terminal obtained with "su". The Ubuntu devs deliberately cripple "su" cause they don't trust users to not do dumb things. There are many ways around that but speaking of them here is discouraged and instructions to enable "su" are totally verbotten. The canonical "'buntu way" is to preface every command needing root permissions to work with "sudo".

If that doesn't do it, there may be some prerequisite packages you need to install before you can compile VLC.

---

### Post by mc4man on 2014-08-22
> **Rahul04789 said:**
> Hi friends,


Step 3: make install

Step 1 and 2 were successful.
but will running step 3 I got following error.

rahul@rahul-VPCEG28FN:~/Gstreamer/vlc-2.0.8$ make install

use sudo
```
sudo make install
```

---

