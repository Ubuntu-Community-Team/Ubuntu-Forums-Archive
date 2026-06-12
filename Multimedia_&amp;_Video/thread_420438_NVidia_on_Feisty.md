---
title: "NVidia on Feisty"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by deadfolk on 2007-04-23
Hi all,

I'm in a spot of bother, and I'm hoping that one of you fine people can help.

I have installed Feisty on my Alienware laptop, but I cannot get the NVidia GeForce 7800GTX GO to work properly.

The default installation was in some horrible resolution, so I used Automatix2 to install the NVidia drivers.  After doing this, X won't start - I just get a black screen.

I then tried to install the latest NVidia drivers manually.  No change.  So I copied back the xorg.conf backup file made by the installer, but I still can't get X to start.

I know you probably need more info to go on - log files and such - but I don't know what/where.  If so, I'll post whatever you need.

Thanks for any help you can offer,

DF

---

### Post by deadfolk on 2007-04-23
For some reason, I'm in (unrelated) apt-get hell.  It's a new install, so I'm just going to reinstall tomorrow.

Can anyone please point me at an up-to-date guide for installing NVidia drivers on Feisty?  I might have more luck doing it the right way from scratch.

---

### Post by Jroller90 on 2007-04-23
I'm fairly new to this. I'm having my own problems with Nvidia drivers and such, but one app that was sort of helpful was Envy, maybe you could give it a try. 

apt-get install envy

hope it helps! :)

---

### Post by deadfolk on 2007-04-24
Thanks for the suggestion - I'll give it a try. :)

---

### Post by necrolin on 2007-04-24
Hopefully the above works for you. If not you've got another solution at:
[http://ubuntuforums.org/showthread.php?t=419738&highlight=nvidia+feisty+black](http://ubuntuforums.org/showthread.php?t=419738&highlight=nvidia+feisty+black)

That's how I fixed my Nvidia problem. My screen was shutting right off with the Nvidia driver.

---

### Post by electronikjunkie on 2007-04-24
Envy should take of it:
```

wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.2-0ubuntu4_all.deb
sudo dpkg -i envy_0.9.2-0ubuntu4_all.deb (you'll get some dependencies errors)
sudo apt-get -f install
sudo envy -t
```

---

