---
title: "Flash Videos Won't Play"
date: 2009-01-21
forum: Multimedia Software
---

### Post by Cheemag on 2009-01-21
Flash videos on YouTube won't play as I don't have the flash
player installed.

Four versions are offered: tar.gz, rpm,  YUM and deb.

Which should I choose? I'd prefer not to mess with tar.gz at the
moment, as I haven't a clue about handling them.

When I get the player, does it install automatically?

From what I read in other threads, installing the player very
probably won't solve the problem ... but you never know ...

---

### Post by gandaran on 2009-01-21
it's better you install flash from the repos, open synaptic package manager, look for flashplugin-nonfree mark for install and click the apply button, reload/update synaptic (sudo apt-get update) before installing anything or flash mite not work
or install using the command line **sudo apt-get install flashplugin-nonfree**
the flashplugin-nonfree in 8.04 installs adobe flash 9 in ubuntu 8.10 flash 10
if you still prefer installing flash from adobe.com get the .deb package and just double click to install

---

### Post by Cheemag on 2009-01-21
> **gandaran said:**
> it's better you install flash from the repos, open synaptic package manager, look for flashplugin-nonfree mark for install and click the apply button, reload/update synaptic (sudo apt-get update) before installing anything or flash mite not work
or install using the command line **sudo apt-get install flashplugin-nonfree**
the flashplugin-nonfree in 8.04 installs adobe flash 9 in ubuntu 8.10 flash 10
if you still prefer installing flash from adobe.com get the .deb package and just double click to install

Thanks, Gandaran.

I went the apt-get install route. Worked.

---

### Post by WatchingThePain on 2009-01-21
I just installed ubuntu restricted-extras and everything worked on youtube.

---

### Post by Cheemag on 2009-01-21
> **WatchingThePain said:**
> I just installed ubuntu restricted-extras and everything worked on youtube.

Yes, mine's working fine now. Thanks.

---

### Post by Juggercat on 2009-02-03
I found out that on certain laptops, uninstalling gnash and installing the flash plugiin mentioned above fixed everything.

---

### Post by Cheemag on 2009-02-03
> **Juggercat said:**
> I found out that on certain laptops, uninstalling gnash and installing the flash plugiin mentioned above fixed everything.

It's working, but the quality isn't as good as I expected or as good as I get on the Windows machine.

I thought it might be the monitor, but as the monitor is shared with a Windows machine via a KVM, it can hardly be that as the Windows rendering of the same video is much better, sharper.

:(

---

### Post by Niko Johnson on 2009-10-14
no need to go through all the hassle, just install the flash plugin from the command line ```
 sudo apt-get install flashplugin-nonfree 
```

---

### Post by Niko Johnson on 2009-10-14
Just keep in mind that some browsers suck and dont work as well.... as much as i love firefox, there newiest version is lacking in a lot of areas and doesnt have full flash video support. I had everything working just fine but firefox decided witch videos it wanted to play and witch videos it didnt want to play, it was real annoying that my browser would only play about 30% of the videos i wanted it to. so i tryed out a different browsers to see witch one i liked best and i have to go with opera! it has a cool sleek look and played ever one of the videos i requested.... including southparkstudios.com!! but i did have some problems installing it the first time. what i found out that worked the best is to download the tar.gz file first.... then run ```
tar -xzvf filename
``` sorry i dont really remember what the name was beacuse it was a long name but anyway, after extracting the file just change directory into the new file and run the install file ```
 cd newfile
./install.sh 
``` after that it should work but for me it didnt... if you have the same problem like me then go back to the opera download website and grab the .deb file and open it with the package installer and then your good to go.... i know what your thinking, why dont you just get the .deb file first?! well i tryed that and it didnt work and it really messed up my system. it told me i had to reistall it but couldnt find the archives for it... that little error didnt allow me to run synaptic package manager or even run apt-get anymore... it really messed me up to the point that i had to reinstall ubuntu, so dont make the same easy to make mistake i did. unless you like reinstalling ubuntu. witch i kinda do :)

---

