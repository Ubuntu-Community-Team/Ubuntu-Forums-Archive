---
title: "Firefox does not load plugins"
date: 2010-08-03
forum: Multimedia Software
---

### Post by travkilde on 2010-08-03
Hi all,

I have a peculiar problem, that I haven't been able to find any other posts mentioning. Firefox is getting confused over my plugins. about:plugins show an empty list but the plugins tab of the Add-On Manager show them all and says they are enabled.

It was working a week ago without any issues whatsoever. Probably an update broke something. Any ideas, anyone? Or people with the same problem?

Plugins are Shockwave Flash, Sun Java, VLC media player and others.
Firefox 3.6.8
Ubuntu 10.04 LTS Lucid Lynx

---

### Post by lovinglinux on 2010-08-03
It could be an issue with the *pluginreg.dat* file in your profile, in which case deleting it could solve the problem, or could be that you are using a 32 bit browser on a 64bit Ubuntu.

Please provide the output of the following commands and instructions, so I can troubleshoot it properly. This will make sure I will have a good understanding of your Firefox and Plugin installations, so I don't need to guess what might be happening to your system:

**1 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog:

[IMG]http://tinyurl.com/26b85o2[/IMG]


**2 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by travkilde on 2010-08-03
Thank you for your efforts! Greatly appreciated!

Removed ~/.mozilla/firefox/pluginreg.dat. Still nothing in about:plugins. pluginreg.dat is not created anew.

1.
About Firefox yields: Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.2.3) Gecko/20100401 Firefox/3.6.3
which does not look healthy to me! I never did a manual installation of Firefox. Only upgrades through repos. My sources.list contains this:
```

deb http://dk.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ lucid main restricted

deb http://dk.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

deb http://dk.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://dk.archive.ubuntu.com/ubuntu/ lucid universe
deb http://dk.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://dk.archive.ubuntu.com/ubuntu/ lucid-updates universe

deb http://dk.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://dk.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://archive.canonical.com/ lucid partner

```
Right now I tried a removal+installation through Synaptic to force a new download of the package, but to no avail. "Windows" still shows up.

Your code block yields:
```
Ubuntu Architecture

Linux tlr-laptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox						install
firefox-3.5					deinstall
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.8/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

google.list
google.list.distUpgrade
google.list.save
medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save

Flash packages

flashplugin-installer				install

Plugin locations

/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped

```

---

### Post by lovinglinux on 2010-08-03
> **travkilde said:**
> About Firefox yields: Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.2.3) Gecko/20100401 Firefox/3.6.3
which does not look healthy to me! I never did a manual installation of Firefox. Only upgrades through repos. 


Definitively not right. Looks like you have a Windows 32bit 3.6.3 version of Firefox being loaded through Wine. 

How are you starting it? If you are staring from an icon launcher in your Desktop, then delete that launcher.

Also go to Wine and remove Firefox 3.6.3 version.

Start Firefox with the command below and check the version and the plugins:

```
firefox 
```

Then test the launcher from the menu. If it doesn't work, update the launcher command to **firefox %u**. Also check in Preferred Applications if the default browser is pointing correctly to /usr/bin/firefox or simply **firefox**.

---

### Post by elianto on 2010-08-03
Hi there looks like I have the same problem! I've a 64bit system and having problem running nspluginwrapper for flash. i've read all the info and tried everything suggested on the forums and I'm running out of ideas. the main problem now is that pluginreg.dat doesn't get updated and about:plugins shows no flash installation even if all the package are installed.
The flash plugin just worked once then I've added the partner repository installed sun-java after that nspluginwrapper started having problems hanging firefox, after several purge and reinstall I found [http://ubuntuforums.org/showthread.php?t=1511278](http://ubuntuforums.org/showthread.php?t=1511278) even if the problem was unrelated I tried what suggested and disabled partner updated reinstalled all the nsplugingwrapper dependencies 
```

#remove partner rep 
aptitude update

aptitude reinstall ia32-libs lib32gcc1 libatk1.0-0 libc6 libc6-i386 libcairo2 libcurl3-gnutls libfontconfig1 libfreetype6 libglib2.0-0 libgtk2.0-0 libpango1.0-0 libx11-6 libxt6
apt-get install flashplugin-installer

```
but still firefox doesn't want to acknoledge the flash plugin and doesn't update plugin list.

please HELP

---

### Post by lovinglinux on 2010-08-03
> **elianto said:**
> Hi there looks like I have the same problem! I've a 64bit system and having problem running nspluginwrapper for flash. i've read all the info and tried everything suggested on the forums and I'm running out of ideas. the main problem now is that pluginreg.dat doesn't get updated and about:plugins shows no flash installation even if all the package are installed.
The flash plugin just worked once then I've added the partner repository installed sun-java after that nspluginwrapper started having problems hanging firefox, after several purge and reinstall I found [http://ubuntuforums.org/showthread.php?t=1511278](http://ubuntuforums.org/showthread.php?t=1511278) even if the problem was unrelated I tried what suggested and disabled partner updated reinstalled all the nsplugingwrapper dependencies 
```

#remove partner rep 
aptitude update

aptitude reinstall ia32-libs lib32gcc1 libatk1.0-0 libc6 libc6-i386 libcairo2 libcurl3-gnutls libfontconfig1 libfreetype6 libglib2.0-0 libgtk2.0-0 libpango1.0-0 libx11-6 libxt6
apt-get install flashplugin-installer

```
but still firefox doesn't want to acknoledge the flash plugin and doesn't update plugin list.

please HELP

Try [FLASH-AID]("https://addons.mozilla.org/en-US/firefox/addon/161939/"). If that doesn't help, post the result of the report script I have created ([see post #2]("http://ubuntuforums.org/showpost.php?p=9673072&postcount=2"))

---

### Post by elianto on 2010-08-03
I've already did both (tried that 'stupid' extension making no difference the file is in place there) and attached the output see Attached Files
firefox-report.txt

---

### Post by lovinglinux on 2010-08-03
> **elianto said:**
> I've already did both (tried that 'stupid' extension making no difference the file is in place there) and attached the output see Attached Files
firefox-report.txt

You haven't attached any file. Please use the **Manage Attachment ** button on the bottom of the post or copy the contents of the file and paste here.

Just a friendly advice. Before calling someone else application 'stupid', make sure is not your fault and be careful to not offend someone that is making a lot of effort to help you, even considering you are not the thread starter. I think you are not aware that I'm the developer of that extension and that it helps a lot of people. It currently has more than 2900 active users and a five star review on Mozilla site.

---

### Post by travkilde on 2010-08-04
> **lovinglinux said:**
> Definitively not right. Looks like you have a Windows 32bit 3.6.3 version of Firefox being loaded through Wine.

Definitively not right. No Wine installed, see below:
```

tlr@tlr-laptop:~$ firefox -version
Mozilla Firefox 3.6.8, Copyright (c) 1998 - 2010 mozilla.org
tlr@tlr-laptop:~$ 
tlr@tlr-laptop:~$ dpkg -l | grep wine
tlr@tlr-laptop:~$ dpkg -l | grep firefox
ii  firefox                                    3.6.8+build1+nobinonly-0ubuntu0.10.04.1         safe and easy web browser from Mozilla
rc  firefox-3.5                                3.6.8+build1+nobinonly-0ubuntu0.10.04.1         dummy upgrade package for firefox-3.5 -> firefox
ii  firefox-branding                           3.6.8+build1+nobinonly-0ubuntu0.10.04.1         Package that ships the firefox branding
ii  firefox-gnome-support                      3.6.8+build1+nobinonly-0ubuntu0.10.04.1         Support for GNOME in Mozilla Firefox
tlr@tlr-laptop:~$ 
tlr@tlr-laptop:~$ which firefox
/usr/bin/firefox
tlr@tlr-laptop:~$ 

```

I am starting Firefox from an icon launcher which executes `firefox %u' as it should do. 

I started Firefox from terminal as you asked me to, but it is the same. Note also the discrepancy in version numbering:
[IMG]http://phys.au.dk/~ravkilde/download/Screenshot-About_Mozilla_Firefox.png[/IMG]

---

### Post by travkilde on 2010-08-04
> **lovinglinux said:**
> You haven't attached any file. Please use the **Manage Attachment ** button on the bottom of the post or copy the contents of the file and paste here.
The file *is* indeed attached...

> **lovinglinux said:**
> 
Just a friendly advice. Before calling someone else application 'stupid', make sure is not your fault and be careful to not offend someone that is making a lot of effort to help you, even considering you are not the thread starter.
elianto, I back this up. This problem is certainly frustrating. I too have spent a lot of time in vain trying to find the reason and a solution for this. But please refrain from stepping on people's toes... ;)

---

### Post by lovinglinux on 2010-08-04
> **travkilde said:**
> The file *is* indeed attached...

Indeed. I missed the fact that it was attached on his previous post, not the one I was replying to. My bad.

> **travkilde said:**
> Definitively not right. No Wine installed, see below:
```

tlr@tlr-laptop:~$ firefox -version
Mozilla Firefox 3.6.8, Copyright (c) 1998 - 2010 mozilla.org
tlr@tlr-laptop:~$ 
tlr@tlr-laptop:~$ dpkg -l | grep wine
tlr@tlr-laptop:~$ dpkg -l | grep firefox
ii  firefox                                    3.6.8+build1+nobinonly-0ubuntu0.10.04.1         safe and easy web browser from Mozilla
rc  firefox-3.5                                3.6.8+build1+nobinonly-0ubuntu0.10.04.1         dummy upgrade package for firefox-3.5 -> firefox
ii  firefox-branding                           3.6.8+build1+nobinonly-0ubuntu0.10.04.1         Package that ships the firefox branding
ii  firefox-gnome-support                      3.6.8+build1+nobinonly-0ubuntu0.10.04.1         Support for GNOME in Mozilla Firefox
tlr@tlr-laptop:~$ 
tlr@tlr-laptop:~$ which firefox
/usr/bin/firefox
tlr@tlr-laptop:~$ 

```

I am starting Firefox from an icon launcher which executes `firefox %u' as it should do. 

I started Firefox from terminal as you asked me to, but it is the same. Note also the discrepancy in version numbering:
[IMG]http://phys.au.dk/~ravkilde/download/Screenshot-About_Mozilla_Firefox.png[/IMG]

We have a mystery to solve.

Let's try to purge it from your system.

```
sudo apt-get purge firefox
sudo apt-get purge firefox-3.5
rm -f /var/cache/apt/firefox*
sudo apt-get update
sudo apt-get install firefox
```

Check the version again and if flash is detected.

If that doesn't work, create a new profile. Close Firefox and start the profile manager with:

```
firefox -P
```

Create the new profile and test it.

---

### Post by travkilde on 2010-08-04
> **lovinglinux said:**
> If that doesn't work, create a new profile. Close Firefox and start the profile manager with:

```
firefox -P
```

Create the new profile and test it.

This did it! Firefox version is correct and all plugins are loaded. Easy fix, I just didn't imagine it being a profile issue...
I have no idea what in my profile caused the problem, but I will post the answer if I find it.

Thanks a whole heap! :D

---

### Post by lovinglinux on 2010-08-04
> **travkilde said:**
> This did it! Firefox version is correct and all plugins are loaded. Easy fix, I just didn't imagine it being a profile issue...
I have no idea what in my profile caused the problem, but I will post the answer if I find it.

Thanks a whole heap! :D

You are welcome. To restore some files from your old profile, see [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html).

---

### Post by travkilde on 2010-08-04
> **lovinglinux said:**
> You are welcome. To restore some files from your old profile, see [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html).

Thx.

---

### Post by elianto on 2010-08-04
...nice to see travkilde has solved his issue :)
apologies to lovinglinux I wrote 'stupid' (with'') but I just meant 'simple' since it just run a bunch of command in a terminal and I certanly don't need a firefox extension for that!
Saying so, doesn't meant I disregard the incredible support by all people like you, we try to help each other and I'm actually surprised there are people reading this instead of taking a trip to the sea!

btw back to my problem I tried also to purge, make a new profile etc. but it makes no difference... any suggestion?
I went on and made a 32bit chroot now flash works but with no sound. I need to solve this in some way:/

---

### Post by lovinglinux on 2010-08-04
> **elianto said:**
> apologies to lovinglinux I wrote 'stupid' (with'') but I just meant 'simple' since it just run a bunch of command in a terminal and I certanly don't need a firefox extension for that!

I don't want to start an argument, since this is a support thread. But there is a reason for using an extension to run such simple commands. The extension allows to easily provide updates to all users. This is specially useful whenever Adobe decides to screw flash. For instance, a couple of months ago Adobe stopped providing support for 64bit plugin and a critical security vulnerability was discovered in the plugin. By that time, FLASH-AID allowed to install the 64bit version directly from Adobe, since it is not available in the repositories. So I immediately released a new version of the extension, that prompted FLASH-AID users to run the script again, in order to remove the 64bit version and install the 32bit. Everyone was able to re-install the safe version of flash without hassle.

Users that don't run FLASH-AID would have to do this manually and there are tons of users that don't even know all versions 64bit flash has a critical vulnerability, because they installed by copying and pasting commands, which are not updated and do not interact with the package manager.

> **elianto said:**
> btw back to my problem I tried also to purge, make a new profile etc. but it makes no difference... any suggestion?
I went on and made a 32bit chroot now flash works but with no sound. I need to solve this in some way:/

I'm thinking...

---

### Post by lovinglinux on 2010-08-04
> **elianto said:**
> btw back to my problem I tried also to purge, make a new profile etc. but it makes no difference... any suggestion?
I went on and made a 32bit chroot now flash works but with no sound. I need to solve this in some way:/

I need some information you didn't provide in the report file:

**1 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog:

[IMG]http://tinyurl.com/26b85o2[/IMG]

I also need the output of:

```
uname -a
```

---

### Post by elianto on 2010-08-04
I've tried making a whole new user and it worked!
wiping out .mozilla doesn't suffice... it must be something else...

---

### Post by elianto on 2010-08-04
Mozilla/5.0 (X11; U; Linux x86_64; it; rv:1.9.2.8) Gecko/20100723 Ubuntu/10.04 (lucid) Firefox/3.6.8
Linux studio 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux

---

### Post by lovinglinux on 2010-08-04
> **elianto said:**
> I've tried making a whole new user and it worked!
wiping out .mozilla doesn't suffice... it must be something else...

Probably a Gnome setting messing with flash.

---

### Post by lovinglinux on 2010-08-04
Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog:

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by elianto on 2010-08-04
it turned out to be a completly different problem and a 'mistake' from my side. I had echo 'linux' in my ~/bin/uname for an old compatibility reason and I forgot to delete it and this made everything not working!!!

thanks for taking the time to investigate it with me, and about the extension: I'm just wondering if the web will, in the near future, be full of little add-on made by user2user trying to accomodate what a comunity mantained distro is not able to catch and fix. Is this THE way?

Congrats for FlashVideoReplacer (but you loose stream feature isn't it?)
regards

---

### Post by lovinglinux on 2010-08-04
> **elianto said:**
> it turned out to be a completly different problem and a 'mistake' from my side. I had echo 'linux' in my ~/bin/uname for an old compatibility reason and I forgot to delete it and this made everything not working!!!

That's why I asked you to provide the report again. But I thought you edited that info manually on the report and didn't realize you had modified it on the system level and that it could cause such issues. I guess that report script is becoming more useful than I expected :)

Did you change the info with User Agent Switcher?

> **elianto said:**
> thanks for taking the time to investigate it with me...

No problem. I'm glad you fixed it.

> **elianto said:**
> ...and about the extension: I'm just wondering if the web will, in the near future, be full of little add-on made by user2user trying to accomodate what a comunity mantained distro is not able to catch and fix. Is this THE way?

You are right, this is not THE way. But what else can we do? Hopefully we will be less dependent on flash some day. 

> **elianto said:**
> Congrats for FlashVideoReplacer (but you loose stream feature isn't it?)

Thanks. No, it just needs to buffer a little. The buffer size depends on the plugin type and settings. Some players need to buffer all the way to the end, while others need just a little, that's why I recommend gecko-mediaplayer.

---

### Post by travkilde on 2010-08-09
> **travkilde said:**
> This did it! Firefox version is correct and all plugins are loaded. Easy fix, I just didn't imagine it being a profile issue...
I have no idea what in my profile caused the problem, but I will post the answer if I find it.


For the record, it turned out to be the Tab Mix Plus extension that was the culprit. It wasn't enough to just remove the extension, as it had corrupted a few other files. I just copied passwords and the like to a new profile and installed extensions anew.

---

