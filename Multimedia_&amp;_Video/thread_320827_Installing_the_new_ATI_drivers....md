---
title: "Installing the new ATI drivers..."
date: 2006-12-18
forum: Multimedia &amp; Video
---

### Post by casperiv on 2006-12-18
Well, I have been fighting to get my opengl to work with my Xpress 200M along with everyone else.  I figured I would give the new drivers, ati-driver-installer-8.32.5-x86.x86_64.run, a shot since they were a new release as of the 13th.  Anyway, I did the normal process:

chmod +x ati-driver-installer-8.32.5-x86.x86_64.run
sudo ln -sf bash /bin/sh
sudo ./ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/edgy

This is where it all went wrong.  With older versions this works just fine, with this version this is what happens:
```
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.32.5........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/edgy
cp: cannot stat `/home/casperiv/Drivers/ATI': No such file or directory
cp: cannot stat `8.32.5/fglrx-install/x710/*': No such file or directory
cp: cannot stat `/home/casperiv/Drivers/ATI': No such file or directory
cp: cannot stat `8.32.5/fglrx-install/arch/x86/*': No such file or directory
cp: cannot stat `/home/casperiv/Drivers/ATI': No such file or directory
cp: cannot stat `8.32.5/fglrx-install/common/*': No such file or directory
cp: target `/tmp/fglrx.LA8461/usr/X11R6/' is not a directory: No such file or directory
chmod: cannot access `/home/casperiv/Drivers/ATI': No such file or directory
chmod: cannot access `8.32.5/fglrx-install/packages/Ubuntu': No such file or directory
cp: target `/tmp/fglrx.LA8461/debian' is not a directory
cp: cannot stat `/home/casperiv/Drivers/ATI': No such file or directory
cp: cannot stat `8.32.5/fglrx-install/packages/Ubuntu/module': No such file or directory
./packages/Ubuntu/ati-packager.sh: line 34: /tmp/fglrx.LA8461/debian/changelog: No such file or directory
./packages/Ubuntu/ati-packager.sh: line 36: /tmp/fglrx.LA8461/debian/changelog: No such file or directory
./packages/Ubuntu/ati-packager.sh: line 38: /tmp/fglrx.LA8461/debian/changelog: No such file or directory
Package build failed!
Package build utility output:
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package is
Removing temporary directory: fglrx-install

```

So what am I doing wrong?

---

### Post by pay on 2006-12-18
It doesn't seem to be the right path of the installer. If it's on the Desktop change the path to
```
chmod +x Desktop/ati-driver-installer-8.32.5-x86.x86_64.run
sudo ln -sf bash /bin/sh
sudo ./Desktop/ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/edgy
```

---

### Post by RudolfMDLT on 2006-12-18
try using my How To for installing these drivers. It's quite detailed. [http://ubuntuforums.org/showthread.php?t=195845](http://ubuntuforums.org/showthread.php?t=195845)

Goodluck,

Rudolf

---

### Post by casperiv on 2006-12-18
Thanks for the info, I will try that when I get home.  It just stumped me since I couldn't even make the debs from that thing without that error.  I sure hope 200M's actually work with this driver, I want to be able to get opengl working.

---

### Post by casperiv on 2006-12-18
Nope, didn't help.  I ran through and got the exact same messages.  I tried doing:
> sudo sh ./ati-driver-installer-8.32.5-x86.x86_64.run
That opened the install GUI, but no good since it comes up as unknown.  Any other ideas?

---

### Post by casperiv on 2006-12-18
Ok, I tried it one more time and got all this again:
> casperiv@casperiv-laptop:~/Drivers/ATI 8.32.5$ sudo ./ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/dapper or edgy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.32.5........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/dapper
cp: cannot stat `/home/casperiv/Drivers/ATI': No such file or directory
cp: cannot stat `8.32.5/fglrx-install/x690/*': No such file or directory
cp: cannot stat `/home/casperiv/Drivers/ATI': No such file or directory
cp: cannot stat `8.32.5/fglrx-install/arch/x86/*': No such file or directory
cp: cannot stat `/home/casperiv/Drivers/ATI': No such file or directory
cp: cannot stat `8.32.5/fglrx-install/common/*': No such file or directory
chmod: cannot access `/home/casperiv/Drivers/ATI': No such file or directory
chmod: cannot access `8.32.5/fglrx-install/packages/Ubuntu': No such file or directory
cp: target `/tmp/fglrx.p13726/debian' is not a directory
cp: cannot stat `/home/casperiv/Drivers/ATI': No such file or directory
cp: cannot stat `8.32.5/fglrx-install/packages/Ubuntu/module': No such file or directory
./packages/Ubuntu/ati-packager.sh: line 34: /tmp/fglrx.p13726/debian/changelog: No such file or directory
./packages/Ubuntu/ati-packager.sh: line 36: /tmp/fglrx.p13726/debian/changelog: No such file or directory
./packages/Ubuntu/ati-packager.sh: line 38: /tmp/fglrx.p13726/debian/changelog: No such file or directory
Package build failed!
Package build utility output:
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package is
Removing temporary directory: fglrx-install
casperiv@casperiv-laptop:~/Drivers/ATI 8.32.5$ 

Please someone help me figure this one out.

---

### Post by RudolfMDLT on 2006-12-19
fglrx installer package doesn't understand edgy's changes yet.

With this help you can get it working:
Do sudo mv /bin/sh /bin/sh.backup
sudo ln -s /bin/bash /bin/sh

And now install fglrx package

after installing package do:
sudo rm /bin/sh && sudo mv /bin/sh.backup /bin/sh

Should work :)


Please give it a try and see what happens.

---

### Post by TusharG on 2006-12-19
Simply follow the steps mentioned on my blog. [http://tusharg.blogspot.com](http://tusharg.blogspot.com)

---

