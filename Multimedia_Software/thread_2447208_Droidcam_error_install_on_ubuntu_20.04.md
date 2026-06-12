---
title: "Droidcam error install on ubuntu 20.04"
date: 2020-07-14
forum: Multimedia Software
---

### Post by andreberg on 2020-07-14
Hello,

have been trying to install Droidcam on Ubuntu 20.04 unsuccesfully.

I followed the instructions at dev47apps website:

```
cd /tmp/
wget https://files.dev47apps.net/linux/droidcam_latest.zip
echo "73db3a4c0f52a285b6ac1f8c43d5b4c7  droidcam_latest.zip" | md5sum -c --
#OK?
unzip droidcam_latest.zip -d droidcam && cd droidcam
sudo ./install
```

but after the last line I get the following error in terminal

```
Webcam parameters: '640' and '480'
Building v4l2loopback-dc.ko
make: Entering directory '/tmp/droidcam/v4l2loopback'
make -C /lib/modules/5.4.0-40-generic/build M=/tmp/droidcam/v4l2loopback modules
make[1]: Entering directory '/lib/modules/5.4.0-40-generic/build'
make[1]: *** No rule to make target 'modules'. Stop.
make[1]: Leaving directory '/lib/modules/5.4.0-40-generic/build'
make: *** [Makefile:8: all] Error 2
make: Leaving directory '/tmp/droidcam/v4l2loopback' 
```

I have verified that gcc make and linux-headers are installed.

Current kernel version is 5.4.0-40-generic so I re-installed linux-headers for that kernel and manually created the /lib/modules/5.4.0-40-generic/build directory as it didn't exist and the installer was throwing the error "no such file or directory".

I have searched for help in AskUbuntu and ArchLinux but have found no solution to this issue.

Any help appreciated.

---

### Post by andreberg on 2020-07-14
Solved.

Found this thread

[https://stackoverflow.com/questions/33425273/no-rule-to-make-target-for-simple-hello-module](https://stackoverflow.com/questions/33425273/no-rule-to-make-target-for-simple-hello-module)

It appears there was a missing lynk between /usr/source/linux-headers and /lib/modules/

The solution was to create a symbolik link with the following code

```
ln -s /usr/src/linux-headers-5.4.0-40-generic/ /lib/modules/5.4.0-40-generic/build
```

Had to delete the previously created folder /lib/modules/5.4.0-40-generic/build for the symlink to work.

After that the installation went through swiftly.

Hope this helps others.

---

