---
title: "Toshiba nb255-450 headphone jack doesn't work"
date: 2010-10-03
forum: Multimedia Software
---

### Post by chesterlinux on 2010-10-03
I have tried every forum that exists, but I have been sadly frustrated in setting up this netbook's headphone jack and internal microphone to work.  Basically the speakers work fine, but as soon as I plug in headphones nothing happens, then I unplug the headphones and the speakers work fine.  I tried adding the following two lines to the /etc/modprob.d/alsa-base.conf
options snd-hda-intel position_fix=1 model=3stack
options snd-hda-intel model=dell-vostro enable=1 index=0
one of the other forums told me to do this, but no luck.
Also I tried this too:  [http://playingwithsid.blogspot.com/2010/06/headphone-jack-sense-problem-in-ubuntu.html](http://playingwithsid.blogspot.com/2010/06/headphone-jack-sense-problem-in-ubuntu.html)
Also no luck...
Please help!
Thanks

---

### Post by Saracho on 2010-10-05
I have the exact problem but with a Sony VAIO netbook :(
help!!

---

### Post by gregork on 2010-10-20
The problem with the headphones on the Toshiba NB255 is that the snd_hda_intel module is not properly configured.  Unfortunately, the options that I could find for configuration using the alsa-base.conf file (found at /etc/modprobe.d/) did not work.  In the future, using the 'options snd-hda-intel model=<option>' should work, but none of the possible options currently is the right one for the Toshiba.

There are two ways to solve the problem that I have found.

Use the HDA_Analyzer to set the variable in real time.
 [http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)
 
Follow the directions on the website, but you need to use 'sudo'
sudo python run.py

 Go to node 0x21 and make sure in the connection list that the audio mixer [0x0c] is selected.
 
A second way to do it is to get the hda-verb utility.

Download hda-verb 

 [ftp://ftp.skynet.be/mirror2/suse.com/people/tiwai/misc/hda-verb-0.3.tar.gz](ftp://ftp.skynet.be/mirror2/suse.com/people/tiwai/misc/hda-verb-0.3.tar.gz)
 
 After using tar and running make, put hda-verb in /usr/sbin
 
 I then added the following to the /etc/rc.local  
 
 /usr/sbin/hda-verb /dev/snd/hwC0D0 0x21 SET_CONNECT_SEL 0
 
so the 0x21 node would be correctly set at startup.

---

### Post by M0JAVE85 on 2010-11-20
[I]"Use the HDA_Analyzer to set the variable in real time.
[http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)

Follow the directions on the website, but you need to use 'sudo'[/I]    [I]
sudo python run.py

 Go to node 0x21 and make sure in the connection list that the audio mixer [0x0c] is selected."[/I] 

[SIZE=4][COLOR=Red]This was WAY easier than a different post I saw for the same issue. Thanks gregork!

[COLOR=Black](I didn't have a node 0x21 -it stopped at 0x19. I changed any node to [/COLOR][/COLOR][/SIZE][SIZE=4][COLOR=Red][COLOR=Black]0x0c [/COLOR][/COLOR][/SIZE][SIZE=4][COLOR=Red][COLOR=Black]that had 0x0c as an option. Headphones worked just the same)[/COLOR]
[/COLOR][/SIZE]

---

