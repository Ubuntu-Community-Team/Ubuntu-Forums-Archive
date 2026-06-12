---
title: "Cannot install ATI Graphics driver on HP TX2500 Laptop"
date: 2013-01-25
forum: Multimedia Software
---

### Post by feerof on 2013-01-25
Hello there,

I'm very new to the Linux scene. I currently am running 12.10 (I believe it's called Quantal?) and I am attempting to install the ATI driver 13.1 onto my laptop. I'm in the process of following this wiki how to page: 

[http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Removing_Catalyst.2Ffglrx)

Just for your reference, I have a [Mobility Raedeon HD 3200]("http://www.notebookreview.com/default.asp?newsID=4511")... I'm not sure if that card is supported because the warning text doesn't seem like it's very clear. 

"ATI Radeon 9500-9800, Xpress200-1250, 690G, 740G, X300-X2500, Mobility RadeonHD 2300"
"ATI RadeonHD 2x00 - 4xx0 cards"

However I cannot get past the step with:

```
sudo sh ./amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run --buildpkg Ubuntu/quantal
```

I always get this error (with the **bolded **text in question):

```
			-e "s|#DEB_HOST_MULTIARCH#|i386-linux-gnu|g" \
			-e "s|#OTHER_ARCH#|x86_64-linux-gnu|g" \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		xpic     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# set the permissions on the pxpress scripts
chmod 744 debian/pxpress/switch*
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
dh build
 debian/rules binary
# refresh copyright file
cat debian/copyright_stub_0 > debian/copyright
cat usr/share/doc/fglrx/LICENSE.TXT >> debian/copyright
cat debian/copyright_stub_1 >> debian/copyright
#Steps that we can't easily represent in debhelper files or .in files yet
# Remove any libraries that may be caught by shell expansion
find . -name libGLE* | xargs rm -f
find . -name libEGL* | xargs rm -f
dh_installdirs -pfglrx
[B]# Install the QT libraries
dh_install -pfglrx "arch/x86_64/usr/share/ati/lib" "usr/share/ati"
cp: cannot stat `debian/tmp/arch/x86_64/usr/share/ati/lib': No such file or directory
dh_install: cp -a debian/tmp/arch/x86_64/usr/share/ati/lib debian/fglrx/usr/share/ati/ returned exit code 1
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.nImqVt
[/B]
```

Being new to this whole thing, installing this driver is quite overwhelming, please pardon my ignorance in some of the terms you guys might through my way. Spent probably a good 2 days on this issue with the help of google, and another couple days just trying to learn what some of the important commands mean on the terminal.

Any helpful pointers would be great.

I have tried "additional hardware" application, but it doesn't seem to work and according to a few of the reviews, the application does not work for 12.10.

Also, I have tried to follow bosyber's suggestions but I realized that they are installing 12.11 which may not apply to 13.1:

[http://ubuntuforums.org/showthread.php?t=2099793](http://ubuntuforums.org/showthread.php?t=2099793)


](*,)](*,)](*,)](*,)

---

### Post by furything on 2013-01-25
Have you ensured you have all the build files?
e.g.
```
apt-get install linux-headers-$(uname -r) build-essential fakeroot dh-make module-assistant
```The guide you followed looks more comlicated that some (try [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) this worked for me in the past). I would suggest as well you try 12.6 driver as this is reported by AMD as your driver although it does recommend downloading 13.1:confused:

Nowadays I use the additional driver gui found in system menu in xfce not sure on unity desktop. With that it lets you choose from a list of compatible tested linux drivers, downloads everything you need, complies, uninstalls old and installs new. You then reboot and the new driver is in operation.

---

### Post by furything on 2013-01-25
Have a look here for a post that goes through the complete uninstall and install 13.1 for ubunutu 12.10

[http://ubuntuforums.org/showthread.php?t=2098752&page=3](http://ubuntuforums.org/showthread.php?t=2098752&page=3)

---

### Post by rrich1974 on 2013-01-25
your hd3200 is not supported anymore by amd in 12.10. use 12.04 instead or stay on opensource driver.

---

### Post by Yellow Pasque on 2013-01-25
There's also the option of downgrading Xserver and using the Catalyst legacy driver, as described in this bug: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1058040](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1058040)
```
sudo add-apt-repository ppa:makson96/fglrx && sudo apt-get update && sudo apt-get -y upgrade && sudo apt-get -y install fglrx-legacy
```

> I'm not sure if that card is supported because the warning text doesn't seem like it's very clear..
Your card falls into the "ATI RadeonHD 2x00 - 4xx0 cards" group. Since I wrote that part of the wiki, I'm interested to hear why you thought it was vague and what you suggest to make it clearer.

---

### Post by feerof on 2013-01-28
> **Temüjin said:**
> There's also the option of downgrading Xserver and using the Catalyst legacy driver, as described in this bug: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1058040](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1058040)
```
sudo add-apt-repository ppa:makson96/fglrx && sudo apt-get update && sudo apt-get -y upgrade && sudo apt-get -y install fglrx-legacy
```


Your card falls into the "ATI RadeonHD 2x00 - 4xx0 cards" group. Since I wrote that part of the wiki, I'm interested to hear why you thought it was vague and what you suggest to make it clearer.

Maybe it was user error, but unfortunately I'm not that fluent with graphic cards since I don't keep up with the naming conventions. You included "Mobility RadeonHD 2300" to the list, but the card that I have on my laptop is a "Mobility RadeonHD 3200". Since my card is tagged with the Mobility badge to it, I thought that the "ATI RadeonHD 2x00 - 4xx0" category did not apply to me, since you made the effort to specify the mobility card. 

But again, it could've just been me missing the point =P 

As for the suggestion you made, I'll take a look into that, still learning all the terminology used ... (eg. xserver).

ps. good on you for owning up to it though, don't see that often from people.

> **rrich1974 said:**
> your hd3200 is not supported anymore by amd in 12.10. use 12.04 instead or stay on opensource driver.

Oh, okay I'll take a look at that also!


Thanks for the replies all, sorry I wasn't able to reply right away!

---

