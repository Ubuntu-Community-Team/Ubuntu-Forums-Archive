---
title: "nVidia driver in Jaunty"
date: 2009-04-25
forum: Multimedia Software
---

### Post by Onay on 2009-04-25
I've been searching through the forums looking for ways to get this to work... I have a GeForce 6200 and it has worked with glx-new drivers every past iteration of ubuntu. I've tried twice to install nvidia drivers from restricted hardware drivers and both times tanked my xorg... I had no graphical environment to run on.

Apparently in synaptic when I choose to install nvidia-glx-180, it removes all xorg-* packages... is this supposed to happen? How can I get my nvidia drivers to work in jaunty?

---

### Post by Onay on 2009-04-25
And how do I fix my system if x won't start after installing nvidia drivers from the restricted hardware manager?

---

### Post by H0PE on 2009-04-25
Hi guys,
 
I'm totally n00b with linux, IF you give me some explanation, bear in mind I no nothing about the commands nor how to do "usual" things, that even the stupidest linux user can handle... I cant...
 
My problem is the same as above. I thought maybe because I got SLI mobo, with 2x8800GTS 512MB.
 
No error message, the system just stop running and I see some check-up or system "load" screen, but no errors. Weirdly, you can type characters, hit enter and stuff, but its not a command line that you typing into, its just a half-loaded/freezed boot sequence I guess.
 
I would appreciate some help too, though probably I have to be patient and wait a couple of days since it seems a regular issue with the brand new ubuntu build.
 
So all in all I'm a linux wannabe, and I would like to try this baby out on my system.
 
Let us know if you aware how to install any good and new nvidia driver to the latest ubuntu.
 
Many thanks!

---

### Post by Onay on 2009-04-25
I finally got mine to work! I did it using the avenard repository. I found this while browsing the forums but I need to make a small tweak to it. The one I found on[ this post](http://ubuntuforums.org/showthread.php?t=1134915) indicates the need to add a repository that is for intrepid. I checked avenard's website and he now has an updated jaunty repository.

```
wget http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key && sudo apt-key add ubuntu-repos.key && rm ubuntu-repos.key

echo "deb http://www.avenard.org/files/ubuntu-repos jaunty release" | sudo tee /etc/apt/sources.list.d/avenard.list

sudo apt-get update
```

Add the avenard jaunty repository. Then go into synaptic and sort it by "Origin" along the bottom left. Then click on avenard's restricted repository and install the nvidia-glx-180.



The problem with the one on the page posted above is that the intrepid nvidia driver's detect that you're using a different (read: NEWER) xorg than the one in intrepid, so it removes xorg completely. By using the repository listed in this post, you should have no problems setting up.

NOTE you may have to run
```
sudo nvidia-xconfig
```
in order to get your xorg configured to use the "nvidia" driver correctly.

Restart gdm and you should be set!

---

