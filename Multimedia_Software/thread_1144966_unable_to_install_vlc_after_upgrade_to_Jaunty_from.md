---
title: "unable to install vlc after upgrade to Jaunty from Intrepid Ibex"
date: 2009-05-01
forum: Multimedia Software
---

### Post by shankru85 on 2009-05-01
Hi All,

I had vlc, mplayer, gnome-do and many such apps installed when i was in Intrepid Ibex. I downloaded alternate cd of ubuntu 9.04 Jaunty Jackalope and upgraded. The upgrade was successful. But while upgrading it asked me whether it could remove some software. I thought it was some kinda cleanup and said yes. Only later i realized that it had removed some of my favourite softwares like vlc, mplayer gnome-do etc etc. So when i try to install vlc back, it says some unresolved dependancies. Can someone help me out to resolve this ? Thanks in advance.

Below is the output i get when i try to install vlc.

shankar@shankar-desktop:~$ sudo apt-get install vlc
[sudo] password for shankar: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 0.9.9a-2ubuntu1) but it is not going to be installed
E: Broken packages

---

### Post by zigga15 on 2009-05-01
Either open synaptic package manager > click edit > click repair broken packages

Or something through terminal

```

sudo dpkg --configure -a
sudo apt-get install -f

```

Check this out for more details: 

[https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages](https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages)

PS: never a good idea to do a straight upgrade like that (in my opinion) I usually do a reformat by save the contents of ~/ on an external (although that can lead to dramas also)

---

### Post by shankru85 on 2009-05-01
Thanks for the reply. Tried your suggestion. It says fixed all dependancies. but still doesnt allow installing vlc. Never mind though. I can manage with mplayer. 

Btw, I have another question, for which i didnt want to open another thread. For some reason, i dont see log off and shut down in the system menu. I have to go to the button which shows my login name at the top right which is quite annoying. I checked out editing the menus. Still no luck. Anybody have any idea about it ?

---

