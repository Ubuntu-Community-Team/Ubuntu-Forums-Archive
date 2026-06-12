---
title: "nVIDIA latest drivers Installation Script"
date: 2012-08-28
forum: Multimedia Software
---

### Post by Dr.Paneas on 2012-08-28
Hello guys,

I've made up a script that does the following:

[LIST=1]
[*]Installs the latest nVIDIA Proprietary Driver
[*]Removes the Proprietary and Installs Nouveau (Open Source)
[*]Fixes any broken drivers issues
[*]Fixes the purge bug when removing and re-installing Xorg-Edgers PPA
[/LIST]
I've contacted with Unigine Heaven Benchmarks QA Team and their feedback is positive, meaning that this script works good on their computers. However, I need to improve it in order to become better :)


I would appreciated it if you could give me a feedback and how things worked on your machine:popcorn:


Download link: [https://github.com/ubuntuxtreme/Nvidia-installer/tarball/master](https://github.com/ubuntuxtreme/Nvidia-installer/tarball/master)


How to run instructions:
  
[LIST=1]
[*]Just open a terminal (Ctrl + T)
[*]type **sudo -i**
[*]hit enter and provide your password to become admin
[*]“drag n’ drop” the **nvidia_installer.sh** executable to the terminal
[*]hit enter to run the script
[/LIST]
Proof of Concept:
[http://www.youtube.com/watch?feature=player_embedded&v=GFhGHbBwsZU](http://www.youtube.com/watch?feature=player_embedded&v=GFhGHbBwsZU)
[http://www.youtube.com/watch?feature=player_embedded&v=1auRQIdJ2aM](http://www.youtube.com/watch?feature=player_embedded&v=1auRQIdJ2aM)

More information:
[http://ubuntuxtreme.com/howto/how-to-install-nvidia-304-43-with-one-click/](http://ubuntuxtreme.com/howto/how-to-install-nvidia-304-43-with-one-click/)

---

### Post by Dr.Paneas on 2012-08-30
Updated to version 1.1

- You can select between X-Swat (stable) or Xorg-Edgers (beta)
- Works for any ubuntu version including dev-branch and quantal 12.10

[http://ubuntuxtreme.com/news/nvidia-installer-script-ver-1-1-released/](http://ubuntuxtreme.com/news/nvidia-installer-script-ver-1-1-released/)

---

### Post by wllk on 2012-09-19
Hello Dr.Paneas, 
your script rocks. it works like charm ;). But I have to ask you for help I have problem to run Unigine Heaven Benchmark. I did install 3.0 and when I want to run launcher_x64  (have 64bit platform and xubuntu 12.04) it says Can't open "launcher_x64.xml" config could you help me with this issue ? 

thanx 
Peter

---

### Post by wllk on 2012-09-28
> **wllk said:**
> Hello Dr.Paneas, 
your script rocks. it works like charm ;). But I have to ask you for help I have problem to run Unigine Heaven Benchmark. I did install 3.0 and when I want to run launcher_x64  (have 64bit platform and xubuntu 12.04) it says Can't open "launcher_x64.xml" config could you help me with this issue ? 

thanx 
Peter
SOLVED :) For those who has this launcher_x64.xml problem: edit file heaven in Unigine-Heaven-3.0 directory and change launcher_x86 to launcher_x64 Thats'it.
Thanks to my friend Mokrejs

---

### Post by smuggly on 2012-11-01
I tried it with a gt240 on xubuntu 12.10 and i get a black screen only After reboot. Im not sure what to do. I reinstalled Xubuntu And now Am running Xubuntu 12.10 64 bit. Thanks Smuggly

My hardware is a biostar AM3+ Mobo W/A 1035 6 core And the Nvidia GT240!

---

