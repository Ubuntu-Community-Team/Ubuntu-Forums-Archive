---
title: "Video Tearing help"
date: 2010-12-03
forum: Multimedia Software
---

### Post by ricky222 on 2010-12-03
Hi, I've had a constant problem with video tearing using Ubuntu, I installed VLC media player yesterday and it seemed to help but it's happening again, any help configuring VLC world be appreciated.

 I followed the sticky guide for media but got this error:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0

Does this mean I will have to install it manually or has it partly installed, can I re-install it manually again or do I have to remove the first attempt done through the terminal, many thanks.

---

### Post by a-user on 2010-12-03
is it so difficult to provide at least infos like your ubuntu version, graphic card, driver version, desktop enviroment used and if you run compiz or not? effects enabled or not?

and if you already are posting this, post also your /etc/X11/xorg.conf file.

---

### Post by sikander3786 on 2010-12-03
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0

Import the missing GPG key.

[http://www.webupd8.org/2010/05/automatically-import-all-missing.html](http://www.webupd8.org/2010/05/automatically-import-all-missing.html)

Regarding your original issue with video, we need some more info like RAM, graphics card and proprietary drivers?

---

### Post by ricky222 on 2010-12-03
Sorry, I'm a complete newbie and thought it was a common poblem with all versions, was going to post these details.

Ubuntu 9.10-Karmic Koala
Gnome Desktop
ATI 3200 intergrated graphics with ATI binary X.org driver installed.
Athlon II x2 250 processors
2GB Corsair Ram
Don't know if I running compiz or if effects are enabled or not, how do I find the /etc/X11/xorg.conf file.

Things were made worse after I followed the sticky media guide and ran this command, can I remove this: 

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

---

### Post by sikander3786 on 2010-12-03
I don't see any harm in the above command :-)

Backup your existing xorg.conf,

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Reconfigure your graphics,

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot and see if any improvement....

---

### Post by ricky222 on 2010-12-03
It won't work:
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

I get this:
mv: cannot stat `/etc/X11/xorg.conf': No such file or directory
ricky@ricky:~$

---

### Post by sikander3786 on 2010-12-03
No problem, proceed to the next command and reconfigure your graphics.

Modern X deals with all the graphics stuff itself and doesn't need an xorg.conf unless it is created manually.

---

### Post by ricky222 on 2010-12-03
No problem, proceed to the next command and reconfigure your graphics.

I've lost all sound now?

---

### Post by ricky222 on 2010-12-03
sudo dpkg-reconfigure -phigh xserver-xorg

I get nothing?

Need to be super user I think?

---

### Post by sikander3786 on 2010-12-03
Sound is not associated to that command anyway :-k

What you mean be "I get nothing?"

If no errors reported, just reboot!

---

### Post by ricky222 on 2010-12-03
I did reboot after that command, no errors, I've now lost all sound.

---

### Post by ricky222 on 2010-12-03
double post, please ignore.

---

