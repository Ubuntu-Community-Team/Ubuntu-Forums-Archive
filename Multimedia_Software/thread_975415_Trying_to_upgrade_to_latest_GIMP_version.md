---
title: "Trying to upgrade to latest GIMP version"
date: 2008-11-08
forum: Multimedia Software
---

### Post by MaxMax on 2008-11-08
Hello,

I have GIMP 2.6.0 running in Ubuntu 8.04.

The GIMP website [http://gimp.org/](http://gimp.org/) states that the latest version is 2.6.2 (and there was also a version 2.6.1). They also say: [I]"Ubuntu or Debian users can simply run **apt-get install gimp** to get the latest stable release of GIMP."
[/I]
I tried it and the reply I get on the terminal is that I already have the latest version (which obviously is incorrect). 

Any hints on how to get the latest version?

Is it also possible to have GIMP and various other software packages automatically notify me when there are new updates available, in the same way Ubuntu does it?

Thanks for any help -- MaxMax

---

### Post by wolfen69 on 2008-11-08
i believe that editing your /etc/apt/sources.list should do the trick.
do ```
gksudo gedit /etc/apt/sources.list
```
then find the line that has "backports" in it. uncomment that by removing the "#" from the beginning of the line. save the file. then do ```
sudo apt-get update
``` try reinstalling gimp.

after installing gimp, you may want to go back and change your sources list back to original state.

---

### Post by MaxMax on 2008-11-08
Hello Wolfen69, I uncommented the line
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

and now I am offered 24 updates, but none of them mention GIMP... Could it be another repository?

---

### Post by DJ_Peng on 2008-11-08
You can get the latest Gimp from [GetDeb]("http://www.getdeb.net/app/Gimp"), but you can also look through the [Personal Package Archives]("https://launchpad.net/ubuntu/+ppas") (PPA's) on Launchpad. Between those two sources you can find pretty much anything you want.

---

### Post by greg73654 on 2008-11-08
I think the easiest way is to use Synaptic, since 8.10 is out now, it should be updated.

---

### Post by DJ_Peng on 2008-11-08
Except the latest GIMP isn't in Intrepid. There's currently a bug filed in hopes of getting it into Jaunty.

---

### Post by greg73654 on 2008-11-08
Holy F'n Crap, you're right. Sorry about the misinformation. hehehe ^_^

---

### Post by DJ_Peng on 2008-11-09
No prob. I get confused about which version is where myself. 8-)

---

