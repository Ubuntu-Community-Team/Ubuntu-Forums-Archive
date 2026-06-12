---
title: "Cannot play youtube videos"
date: 2010-05-27
forum: Multimedia Software
---

### Post by chejose on 2010-05-27
I carefully followed the instructions in the main page about setting everything up for multimedia.

But... there are often youtube videos in Google news and they will not play.

There is a warning that some plugins are missing, but when I go to install them as it suggests, there are three listed (one is Adobe flash (installer)) but when I try to install them the answer is that they are already installed.

I am afraid that multimedia is an area I am a bit lost in, so need help.

Many thanks,

José

---

### Post by dv3500ea on 2010-05-27
Try installing the software packages:
[ubuntu-restricted-extras]("apt:ubuntu-restricted-extras")
or
[adobe-flashplugin]("apt:adobe-flashplugin")

You may need to first go to System -> Administration -> Software Sources
and tick the restricted or multiverse repositories.

Then you can click on the above links to install.

---

### Post by chejose on 2010-05-27
Thanks, but I have the ubuntu-restricted-extras installed. And... I am afraid that when I want to install the adobe flash player I get a message that it is not available for an amd64 runnning computer.

So hopefully someone will have a way to work around that.

José

---

### Post by phr33k-dc on 2010-05-27
ah hold on. are you running 64bit?

---

### Post by Guitar John on 2010-05-27
If you upgraded, try System > Administration > Synaptic Package Manager and search for adobe-flashplugin.  

On the computer that I upgraded, I selected Mark for Re-Installation.  Click Apply, and everything was good after that.

---

### Post by ubun2warrior on 2010-05-27
The simplest thing to do is.. go to synaptics package manager. Click on the reload button there. Then search for Adobe flash plugin and perform the installation.

---

### Post by chejose on 2010-05-27
The problem seems to be that adobe flash plugin is not compatible with the 64 bit Ubuntu. For example it does not even show up in package manager.

I wish that the problem were as simple as you suggest. When I try to play a youtube Ubuntu says that additional plugins are necessary. If I tell it to look for them it finds "adobe flash player (installer)" but then it says it is already installed.

So again, I hope there is a workaround for this.

José

---

### Post by qwerty2009 on 2010-05-27
you could try using my script to download the latest flash.

[flash.sh]("http://ubuntuone.com/p/5Gs/")

once downloaded right-click > properties> permissions> allow exicuting file as program

then double click the script and run in terminal

---

### Post by dustinmarlowe56 on 2010-05-27
flash is available on 64 bit Ubuntu. I run a 64 bit Ubuntu 10.04 LTS and i have full flash support. 


if worst comes to worst you could resize your current Ubuntu Partition to free up about 10GB for another fresh Ubuntu install and try to get it working in there. the steps on the comprehensive multimedia guide worked fine for me.

---

### Post by chejose on 2010-05-27
Thanks for that last sugestion. I did as you said and the process started but hung up on "conecting to download.macromedia.com". I waited for over 5 minutes and then gave up.

José

---

### Post by qwerty2009 on 2010-05-27
sorry it seems adobe have updated there flash player 

you can download the new script here:[flash.sh]("http://ubuntuone.com/p/5Gs/")

instructions same as above...

> once downloaded right-click > properties> permissions> allow exicuting file as program

then double click the script and run in terminal

---

### Post by chejose on 2010-05-27
Again, thanks, but I am afraid that the same thing happened. An attempt to connect to download.macromedia failed. I waited for some 10 tries and closed.

José

---

### Post by qwerty2009 on 2010-05-27
ok i dont know why you cant connect perhaps your isp is blocking adobe

ive provided a .tar.gz here: [flash.tar.gz]("http://ubuntuone.com/p/5H3/")

just extract the folder and make the sh executable then run in terminal


p.s you might have to restart to allow firefox to read the updated mozilla plugin directory

---

### Post by lovinglinux on 2010-05-27
Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

I'm the developer, so feel free to ask any questions. I have created that extension because I have already replied to hundreds of threads like yours, talking about the exact same problem. So, it will fix your problem.

---

### Post by VastOne on 2010-05-27
> **lovinglinux said:**
> Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

I'm the developer, so feel free to ask any questions. I have created that extension because I have already replied to hundreds of threads like yours, talking about the exact same problem. So, it will fix your problem.

Simply Brilliant...

Well done LL

---

### Post by lovinglinux on 2010-05-27
> **VastOne said:**
> Simply Brilliant...

Well done LL

Thank you.

---

### Post by oleink on 2010-05-27
> **chejose said:**
> Thanks, but I have the ubuntu-restricted-extras installed. And... I am afraid that when I want to install the adobe flash player I get a message that it is not available for an amd64 runnning computer.

So hopefully someone will have a way to work around that.

José

It's not adobe flash player you want.  Just the plugin because the actual thing itself may not be available for your architecture.

---

### Post by rossmurray on 2010-05-27
I just used this install method on 64 bit install for my iMac. Worked fine!
[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

Be sure to add the PPA from here:
[https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash)

---

