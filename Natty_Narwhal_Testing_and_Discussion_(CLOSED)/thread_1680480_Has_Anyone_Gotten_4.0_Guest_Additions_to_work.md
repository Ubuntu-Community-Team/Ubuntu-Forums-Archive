---
title: "Has Anyone Gotten 4.0 Guest Additions to work?"
date: 2011-02-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by grubdude on 2011-02-02
Since the latest builds I have not been able to get 32bit virtualbox guest additions to install. It keeps failing because it says it cannot find the kernel headers.
 
Anyone else have this issue and were you able to get around it? Thanks
 
This began after the latest kernel upgrade...37 was okay...

---

### Post by Mr. Picklesworth on 2011-02-02
I'm unsure from you're post if this is what you're doing, but you can actually grab guest additions for Virtualbox 4 from the repository now :)
The package is virtualbox-ose-guest-x11

---

### Post by grubdude on 2011-02-02
Well actually, I am installing them from inside the virtualbox program. It has always worked before. Now, during the install it fails saying it cannot find the kernel headers. So, it would do the same if selected from the repository, I suspect. Thanks.

---

### Post by jaezcurra on 2011-02-02
I have this same issue too.  It used to work last week.  The breakage was caused by the January 31st update.

---

### Post by grubdude on 2011-02-02
Yes, same for me.....Seems like Gnome is also messed up to now.....

---

### Post by ubuntu27 on 2011-02-02
I can confirm the same thing. The Guest Addition script "VBoxLinuxAdditions.run" does not work anymore.

After showing a couple of errors, it closes automatically. Now we are stuck with Ubuntu Natty without Unity.

---

### Post by grubdude on 2011-02-02
Well, I was stuck without unity anyway on this box because does not support 3D, but now even classic desktop is no longer showing the proper colors for the panels and the icons are all from like 9.10 ubuntu. It tries to boot into the proper mode but then revets back. Also, menus on the topupper left panel keep showing up and disappearing now....really messed up noe I guess........

---

### Post by Mr. Picklesworth on 2011-02-02
> **ubuntu27 said:**
> I can confirm the same thing. The Guest Addition script "VBoxLinuxAdditions.run" does not work anymore.

After showing a couple of errors, it closes automatically. Now we are stuck with Ubuntu Natty without Unity.

Which is why someone should try the solution I mentioned ;)
Honest, install [that package]("apt:virtualbox-ose-guest-x11") in the guest and it will pull in all the dependencies to work well from here on out. It'll be fun!

(It may ask you about replacing a configuration file; just let it do that).

---

### Post by grubdude on 2011-02-02
okay, I am game. I will give it a try........  :-)

---

### Post by grubdude on 2011-02-02
And the answer is:
 
virtualbox-ose-guest-x11
 
Depends: xorg-video-abi-8.0 but it is not installable
Depends: xserver-xorg-core  but it is not going to be installed
Depends: xorg-input-abi-11.0 but it is not installable
 
 
oh well......

---

### Post by ubuntu27 on 2011-02-02
> **Mr. Picklesworth said:**
> Which is why someone should try the solution I mentioned ;)
Honest, install [that package]("apt:virtualbox-ose-guest-x11") in the guest and it will pull in all the dependencies to work well from here on out. It'll be fun!

(It may ask you about replacing a configuration file; just let it do that).

It wants to uninstall many X.org related packages. ><;

---

### Post by Mr. Picklesworth on 2011-02-02
> **ubuntu27 said:**
> It wants to uninstall many X.org related packages. ><;

Yeah, I forgot about that. There was an update to xorg recently and it's all being held back on something (which probably hasn't landed yet). When those updates finally install, this package will work.

So, never mind my claim that this is a quick solution. At the moment, it isn't :)

---

### Post by WorLord on 2011-02-03
> **Mr. Picklesworth said:**
> Yeah, I forgot about that. There was an update to xorg recently and it's all being held back on something (which probably hasn't landed yet). When those updates finally install, this package will work.

So, never mind my claim that this is a quick solution. At the moment, it isn't :)

It's not a dep issue.

The new .38 kernel has changed the location of autoconf.h (along with a few other files).  You can fix this problem easily by symlinking in the /lib/modules folder. 

You still get the "I can't find kernel headers" message, which is puzzling, but the entire message actually reads "...so IF the compile fails, that's why."  It proceeds and builds.

This new X-stuff, on the other hand, is what's broken for me.  It won't build the X drivers, stating that I'm using an unsupported pre-release.  I don't think I can fix that with some symlinks.  :-(

As for the panel not showing up with the proper colors: this is a known bug with gnome-settings-daemon.  Kill it, re-launch it.  Should be good.

---

### Post by grubdude on 2011-02-03
Thanks but it won't let me kill or restart gnome.....

---

### Post by loukingjr on 2011-02-03
I just installed Xubuntu 11.04 alpha 2 into VirtualBox. Much to my dismay, :p, the headers and source are much newer than the kernel and looking through synaptic, there doesn't seem to be a kernel and header package that matches. This means of course VB won't compile the guest additions. There are guest additions for the 4.0.2 OSE version of VB but I am running the PUEL version. Plus I don't know if they would even work seeing you need a matching kernel and header package for the OSE version as far as I know.

any thoughts on what I might be able to do?
thanks

---

### Post by cariboo on 2011-02-03
Merged two threads on essentially the same subject.

---

### Post by nilarimogard on 2011-02-03
There is a way around this: install an older Kernel from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) (2.6.37 should do it) and use Startup-Manager to boot that Kernel. The Guest Additions will then work.

---

### Post by loukingjr on 2011-02-03
> **nilarimogard said:**
> There is a way around this: install an older Kernel from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") (2.6.37 should do it) and use Startup-Manager to boot that Kernel. The Guest Additions will then work.
well, I downloaded the 2.6.37 header and image .deb packages from there and it won't let me install them. It opens ubuntu software center and won't let me install them.

---

### Post by nilarimogard on 2011-02-04
Assuming you've downloaded them in ~/Downloads (make sure you download the packages for your Ubuntu version - 32bit or 64bit), run these commands:

cd ~/Downloads
sudo dpkg -i *.deb

---

### Post by loukingjr on 2011-02-04
> **nilarimogard said:**
> Assuming you've downloaded them in ~/Downloads (make sure you download the packages for your Ubuntu version - 32bit or 64bit), run these commands:

cd ~/Downloads
sudo dpkg -i *.deb
well, for whatever reason it wouldn't install the headers. there are unmet dependencies.

---

### Post by nilarimogard on 2011-02-04
You need to download 3 files - make sure you got them all. I used this method so it works :)

---

### Post by user333 on 2011-02-04
I'm using virtualbox 4.0.2 on ubuntu 10.04. I'm testing 11.04 alpha 2 and I wanted to get unity working, so I tried to install guest additions to get 3d support.

When I run the autorun file, I get this error:

```


The headers for the current running kernel were not found. If the following module compilation fails then this could be the reason.

Building the main Guest Additions module ...fail!


```I have already installed these packages:

```

 sudo apt-get install build-essential linux-headers-$(uname -r) dkms
```Any ideas?

---

### Post by user333 on 2011-02-04
Perhaps I should mention I'm using a 64 bit computer, and running a 32 bit guest

---

### Post by CharlesA on 2011-02-04
Threads merged.

---

### Post by loukingjr on 2011-02-04
> **nilarimogard said:**
> You need to download 3 files - make sure you got them all. I used this method so it works :)
well, I believe you! lol but I'm not sure what the third file would be. I just downloaded the image and headers.  want to let me know what the third one would be?:D

---

### Post by grubdude on 2011-02-04
And the three files are?.................. :-)

---

### Post by grubdude on 2011-02-04
> **nilarimogard said:**
> You need to download 3 files - make sure you got them all. I used this method so it works :)
 
 
Can you please expand on this?

---

### Post by loukingjr on 2011-02-04
> **loukingjr said:**
> well, I believe you! lol but I'm not sure what the third file would be. I just downloaded the image and headers.  want to let me know what the third one would be?:D
geez my bad, I missed the generic-all.deb file.

---

### Post by grubdude on 2011-02-04
So, essentially the only way to run guest additions at this point is to downgrade the kernel to 37, yes? I think that I may just wait for now...

---

### Post by loukingjr on 2011-02-04
okay, I got the earlier kernel installed with the headers, but now I am getting a message that it's not going to install the xorg files because of using a pre-release version, :lolflag:

---

### Post by loukingjr on 2011-02-04
okay, I got the earlier kernel installed with the headers, but now I am getting a message that it's not going to install the xorg files because of using a pre-release version, :lolflag:
"Warning: unsupported pre-release version of X.Org Server installed.  Not
installing the X.Org drivers."

---

### Post by grubdude on 2011-02-04
Lovely........ :-)

---

### Post by Mr. Picklesworth on 2011-02-04
Yeah, just to make it a little more prominent, this was the bug report:
[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/712385](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/712385)
I found that yesterday and forgot to properly point it out.

Looks like VirtualBox needed a patch to support the new stuff, and that was just released a couple hours ago with the virtualbox-ose-guest-x11 package in Ubuntu's repository. (I just confirmed it with my VM; it finally upgraded xorg and virtualbox-ose-* stuff happily after being stuck for a few days). It could take a while to trickle through to the other mirrors if you're using one other than the main server. The package version you want is this one: [https://launchpad.net/ubuntu/+source/virtualbox-ose/4.0.2-dfsg-1ubuntu2](https://launchpad.net/ubuntu/+source/virtualbox-ose/4.0.2-dfsg-1ubuntu2)

The image you download through VirtualBox directly probably doesn't have that change yet.

---

### Post by loukingjr on 2011-02-04
> **Mr. Picklesworth said:**
> Yeah, just to make it a little more prominent, this was the bug report:
[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/712385](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/712385)
I found that yesterday and forgot to properly point it out.

Looks like VirtualBox needed a patch to support the new stuff, and that was just released a couple hours ago with the virtualbox-ose-guest-x11 package in Ubuntu's repository. (I just confirmed it with my VM; it upgraded xorg and virtualbox-ose-* stuff happily after being stuck for a few days).

The image you download through VirtualBox directly probably doesn't have that change yet.
actually I just tried to install the virtualbox-ose-guest-x11 package and I got this message...
 Depends: xorg-video-abi-8.0  but it is not installable
 Depends: xserver-xorg-core but it is not going to be installed
 Depends: xorg-input-abi-11.0  but it is not installable
:mad:

---

### Post by bvidinli on 2011-02-05
I installed with:
apt-get install virtualbox-ose-guest-x11 virtualbox-ose-guest-utils virtualbox-ose-guest-dkms

(actually with aptitude)

now, virtualbox guest additions seems working.
virtualbox resize, fullscreen working.

however, I cannot see the left panel that exists in natty alpha 1, now I use natty alpha2.  It seems I cannot use wayland. is it normal ?

---

### Post by loukingjr on 2011-02-05
> **bvidinli said:**
> I installed with:
install virtualbox-ose-guest-x11 virtualbox-ose-guest-utils virtualbox-ose-guest-dkms

(actually with aptitude)

now, virtualbox guest additions seems working.
virtualbox resize, fullscreen working.

however, I cannot see the left panel that exists in natty alpha 1, now I use natty alpha2.  It seems I cannot use wayland. is it normal ?

well, I also managed to get the OSE versions working somehow :lolflag:
I don't know about Unity because I am playing with Xubuntu. So no left panel.

---

### Post by bvidinli on 2011-02-05
I also managed to see unity (wayland) and left panel too.
did this way: shut down virtual Machine, go to settings of VM
enable 3D acceleration.
start machine.

however, this time, the desktop of natty becomes unresponsive sometime,
I dont know why. mous disappears, and it seems frozen.

---

### Post by cariboo on 2011-02-05
> **bvidinli said:**
> I also managed to see unity (wayland) and left panel too.
did this way: shut down virtual Machine, go to settings of VM
enable 3D acceleration.
start machine.

however, this time, the desktop of natty becomes unresponsive sometime,
I dont know why. mous disappears, and it seems frozen.

Just to let you know there is no wayland in Natty, it is an X-server that we may see in the future, as it is nowhere near usable yet.

---

### Post by dangmc on 2011-02-07
> **bvidinli said:**
> I installed with:
install virtualbox-ose-guest-x11 virtualbox-ose-guest-utils virtualbox-ose-guest-dkms

(actually with aptitude)

now, virtualbox guest additions seems working.
virtualbox resize, fullscreen working.

however, I cannot see the left panel that exists in natty alpha 1, now I use natty alpha2.  It seems I cannot use wayland. is it normal ?

Well it worked for me! Unity and all-but it crashed right away. Now I need to play around with it. I'm using alpha2 amd64. Thank you for the tip bvidini

---

### Post by bvidinli on 2011-02-07
At last, I give up trying with Virtualbox, and installed natty on my computer ! (upgraded existing ubuntu)
as stated on [http://ubuntuforums.org/showthread.php?t=1683104](http://ubuntuforums.org/showthread.php?t=1683104)
sometime, screen clutters/freezes.

luckily, I can Ctrl+alt+F1, then
/etc/init.d/gdm restart
then, login using "classic ubuntu desktop" 
that way, old normal (maverick way) desktop appears with no problem.
now, i will test natty from time to time, on my real machine

Btw: does anybody knows when wayland will be used, and will it be useful/advantagous ? as cariboo907 said, natty is not wayland... 

Another subject: As stated on [http://ehcp.net/?q=node/1070](http://ehcp.net/?q=node/1070)  I prepared a deb package. Can anybody submit it to Ubuntu repositories ? As I read some ubuntu sites,it is quite complex.. An experienced person for doing this is welcome.

---

### Post by cariboo on 2011-02-07
> Btw: does anybody knows when wayland will be used, and will it be useful/advantagous ? as cariboo907 said, natty is not wayland... 

Another subject: As stated on [http://ehcp.net/?q=node/1070](http://ehcp.net/?q=node/1070) I prepared a deb package. Can anybody submit it to Ubuntu repositories ? As I read some ubuntu sites,it is quite complex.. An experienced person for doing this is welcome.

I doubt if we'll see anything about wayland until after the next LTS version is released (12.04).

You can create a ppa, if you have a launchpad account and have signed the Ubuntu Code of Conduct, which is different from the forum code of conduct.

Have a look here:

[https://help.launchpad.net/Packaging/PPA/Uploading](https://help.launchpad.net/Packaging/PPA/Uploading)

---

### Post by nick_goodfate on 2011-02-11
Hello forum !

I installed Ubuntu 11.04 in VirtualBox 4.0.2 r69518. When i try to install VBoxadditions i get an error(first screenshot). 
Looking at vboxadd-install.log(second screenshot) i see some errors but i can't understand what went wrong. Any idea?
Google didn't found anything helpful, at least for my level of knowledge...:roll:
Thank you for any help![-o<
[ATTACH]183232[/ATTACH][ATTACH]183233[/ATTACH]

---

### Post by CharlesA on 2011-02-11
Merged into Natty thread.

---

