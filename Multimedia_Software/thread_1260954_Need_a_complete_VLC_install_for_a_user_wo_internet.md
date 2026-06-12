---
title: "Need a complete VLC install for a user w/o internet"
date: 2009-09-08
forum: Multimedia Software
---

### Post by bbbaldie on 2009-09-08
I've been asked to put together a DVD player for a user in a faraway location who doesn't have internet. Is there a way to install VLC through Synaptics and grab all installed files and create a self-contained install?

I rate myself a 7 on a scale of 10, knowledge-wise. I've been running Ubuntu desktops and CentOS servers for three years. So I can handle command-line stuff, if someone can get me steered right.

Thanks.

---

### Post by rob-ward on 2009-09-08
I havn't tried it and unfortunetly because of custom VLC installs from uni work I can't try this but if you visit this address: [https://launchpad.net/~c-korn/+archive/vlc/+build/1150260](https://launchpad.net/~c-korn/+archive/vlc/+build/1150260) at the bottom of the page there are several deb files, I think these are all you need for a VLC install... maybe

Hope that helps, 

oh note that this is the newer version of vlc than in the repos.

---

### Post by bbbaldie on 2009-09-08
Sweet! I'll download them and see if it works on my machine.

Well, it was a good try, but some of those debs had other dependency issues.

---

### Post by andrew.46 on 2009-09-08
Hi bbbaldie,

It is no use to you I am afraid but you may be interested to know that such a package exists under Slackware. The packages are here:

[http://connie.slackware.com/~alien/slackbuilds/vlc/pkg/13.0/](http://connie.slackware.com/~alien/slackbuilds/vlc/pkg/13.0/)

while the incredibly elaborate build script can be seen here:

[http://connie.slackware.com/~alien/slackbuilds/vlc/build/vlc.SlackBuild](http://connie.slackware.com/~alien/slackbuilds/vlc/build/vlc.SlackBuild)

but I would be a little surprised if such a package could be produced under Ubuntu. It would be a big project to modify this build script to suit Ubuntu conditions... Perhaps mc4man might have an idea??

Andrew

---

### Post by Megaptera on 2009-09-09
Sorry if this is not allowed!! But there's a portable version of VLC for Windows that can be run from a flashdrive/USB device
[http://portableapps.com/apps/music_video/vlc_portable](http://portableapps.com/apps/music_video/vlc_portable)

If Windows is an option for your needs I hope this is of help?

---

### Post by mc4man on 2009-09-09
Will find it interesting to look thru that script. 
As far as an offline install of vlc figure about 30 -40 packages plus maybe some extra libs for usability. 

There is aptoncd though I've never used it, you could research that. Some one also made an app that does something similar though the name escapes me ( begins with a k i think.

What would also work is to use a live cd, It's pretty straightforward though obviously you need to use the same release as your friend.

There may or may not be any issues if there is an update version difference, like for example you use a 8.04.3 live cd and your friend is using the orig 8.04 release that hasn't been updated.

Anyway if you boot to a live cd and install vlc (and or anything else), the .debs installed will be found in /var/apt/cache/archives

I'd use the terminal to install, before confirming the install copy all of the package names from the terminal to a text file so you can compare later to see if your missing any.

To use a live cd in this manner right after getting the internet connected go into system -> admin.. -> software sources and disable the cdrom as a source and enable the four main ubuntu software sources.

Also if desired add medibuntu and or a ppa.


On the install side just provide all the .debs in a folder. If your friend then copys the folder to home or desktop then this command could work.
in a terminal cd to the folder and then

```
sudo dpkg -i *.deb
```

The only danger there is that if even one dep is missing they'll end up with broken packages

A far better way is to learn how to create and use a local repo, then provide instructions along with the package set. This way vlc or whatever will be available like any other package in synaptic, if any thing is missing the install won't proceed.

Thread on how to
[http://ubuntuforums.org/showthread.php?t=42862](http://ubuntuforums.org/showthread.php?t=42862)

and my post in 
[http://ubuntuforums.org/showthread.php?p=7606998#post7606998](http://ubuntuforums.org/showthread.php?p=7606998#post7606998)

(( I actively use a local repo for our hardy installs, works great and has pulled hardy from the dark ages multimedia wise - about 150 packages now

It would be good if you knew the state of their install ( from grub screen

Before sending off you could test from a fresh reboot to live cd with no internet ( either the local repo or dpkg method

---

### Post by bbbaldie on 2009-09-10
Thanks, all, but I'm just going to advise the user finding an internet cafe somewhere and installing through Synaptic. For once, I envy the Windows users' single executable for install. But ONLY for once ;)

---

### Post by rob-ward on 2009-09-10
You may consider puting together a custom version of ubuntu with vlc included in the live cd, that shouldn't take too long and will do what you want.

---

### Post by bbbaldie on 2009-09-10
Good idea, but I don't even know what type of laptop it's going on. Will it install on any system, or would it have to be reasonably close to mine?

---

### Post by rob-ward on 2009-09-10
You can make a custom distro that is basically identical to ubuntu but includes VLC. That means that it will install/run on anything that ubuntu does.

Check out an application called reconstructor, that should do everything you want.

If you like I could make you a custom distro my problem however is getting it to you, my internet connection is rather slow, it would probably be faster to do it yourself.

---

### Post by bbbaldie on 2009-09-10
It worked! I tested remastersys on my desktop machine, then installed from the custom distro DVD to another hard drive. Thanks for the idea, rob-ward! :guitar::popcorn:

---

### Post by rob-ward on 2009-09-10
No Problem

---

