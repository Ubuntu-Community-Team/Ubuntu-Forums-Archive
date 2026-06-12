---
title: "Avoid reinstalling nvidea drivers each time kernel updates?"
date: 2010-05-29
forum: Mythbuntu
---

### Post by geekyhawkes on 2010-05-29
I have just about taken all the rough edges off my mythbuntu setup but one of my outstanding minor issues is the fact i have to reinstall the nvidia drivers each time i update the kernel.

Is there some way i can get my machine to do this for me during the kernel update process?

---

### Post by kja999 on 2010-05-31
If you have selected the nvidia kernel module in synaptic it should be doing this for you already.
The restricted driver dialogue should help in this.

I have installed the nvidia drver before on ubuntu and it fails to update correctly ... that was 9.10 though.

---

### Post by laffinet on 2010-05-31
If you are using drivers newer than the ones in the repos (ie you have installed them manually) then I don't think there is an easy solution.

I have read about a ppa that gets updated a few days (latest) after the newest drivers are released. Adding that to your system might help, but I haven't tried it myself.

Couple of links:
[http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html]("http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html")[https://launchpad.net/~nvidia-vdpau/+archive/ppa]("https://launchpad.net/~nvidia-vdpau/+archive/ppa")

---

### Post by JugeHuge on 2010-06-01
I have a problem with ATI that when i just run updates i need to install ATI driver again.. No need to be kernel update..

---

### Post by geekyhawkes on 2010-06-01
I am using the latest nvidia driver so not in the repos.  I will stick with reinstalling the driver each time i do a kernel update for now.  Its not a huge price to pay for decent video drivers i guess.

---

### Post by nickrout on 2010-06-01
lucid provides me with the 195.36 drivers and i am pretty sure that is from the standard repos.

What are you running?

Also have to ask, if you don't want this problem, why are you updating your kernel? Rule one for successful mythtv: if it ain't broke, don't fix it!

Nick.

---

