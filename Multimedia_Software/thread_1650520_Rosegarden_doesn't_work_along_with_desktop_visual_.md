---
title: "Rosegarden doesn't work along with desktop visual effects"
date: 2010-12-21
forum: Multimedia Software
---

### Post by fernando.a.martin on 2010-12-21
I have just finished installing Ubuntu Studio in my machine and downloaded and installed the Nvidia drivers. I was so excited about using the desktop visual effects that I had seen in some advertising. But first, I just found 3 options in the Appearences config none, normal and extra. Where are desktop effects such as windows trasparence, the cube an others?
Second, and worst, I enabled the "extra" options and found its effects pleasant, but I could not use the for any longer because when I launch Rosegarden with desktop effects enabled, Rosegarden's title screen appears and after that its windows doesn't appear. I found out that the problem is enabling desktop effects because when they are disabled Rosegarden starts completely in few seconds. I even made a test and enabled effects, launched Rosegarden, wich of course dind't appear, after that disabled effects and Rosegarden's window imediately appeared. I use this software every day and it was the main reason why I migrated to Ubuntu. How can I use Rosegarden and visual effects as well?
PS: My PC has Pentium dual core with 2 x 1,88, 3GB RAM and Nvidia Geforce 8400 GS. My system is Ubuntu Studio 10.10 with Rosegarden 10.10 installed from <[http://ppa.launchpad.net/ferramroberto/rosegarden/ubuntu](http://ppa.launchpad.net/ferramroberto/rosegarden/ubuntu) maverick>.

---

### Post by fernando.a.martin on 2010-12-24
I have went back to Rosegarden 10.02 from Ubuntu repositories and the problem remains.
I have also had another problem: I use the connection Rosegarden + Qjackctl + Qsynth. I formerly played any preset in my soundfont, even the banks variations. Now it only plays sounds from the first bank. It happens even in files where it played all the banks before.

---

### Post by shantiq on 2010-12-24
ok a couple of tips


install compiz-fusion-icon   ```
sudo apt-get install compiz-fusion-icon
```  i think:KS

if you have compiz installed


then go applications/systemtools/compiz-fusion-icon

and take it to the top bar


click on it it opens next to the first icon


right clich and pick    reload windows manager



see if rosegarden appears again    i too use it every day and yes it does not always like the effects but gets used to them

trick number 2    open terminal    enter     ```
compiz --replace
```



trick 3     open rosegarden    then move it to another window from bottom bar


see if any of these help you. good luck

---

### Post by fernando.a.martin on 2010-12-27
Thank you very much! Your suggestions worked. This forum is very nice. Unfortunately, though, I am not an Ubuntu user anymore. I was getting mad at Ubuntu, although it is a very good distro, but i could not stand configuring everything in command line anymore. So I moved to OpenSUSE. Here in OpenSUSE I could customized all the compiz effects making it very pratical to switch between desktops and applications. Here your suggestion also worked because when I launch Rosegarden I round the cube and it appears in some of the desktops. I find it very unhappy that Ubuntu doesn't have a Control Center like YaST. This all that is missing to make it the best distro ever. Thank you again.

---

### Post by shantiq on 2010-12-28
cool please to know it worked


i have no experience of opensuse   but i am REALLY happy with the old buntu



found [this]("http://ubuntuforums.org/showpost.php?p=8763690&postcount=17") on my travels which you might enjoy reading

---

