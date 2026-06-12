---
title: "ISA sound card problem"
date: 2006-04-06
forum: Multimedia &amp; Video
---

### Post by tamray on 2006-04-06
I have a dozen installs to do on Dell Optiplexes. They all have a built in ISA sound card which Ubuntu does not find on its own. Originally, I was installing Knoppix on these machines and ran alsaconf to install the Cirrus Logic cs4236 driver. I had a few people advise me to move to Ubuntu, but I am having the same problem, only alsaconf is not available to set up the sound card. I see I have alsa-base, and alsa-utils installed, but cannot find a command that will let me probe and configure the card.

Any advise would be appreciated.

Raymond

---

### Post by Wyrm_1972 on 2006-04-06
Have you looked here...

[https://wiki.ubuntu.com/HowToSetupSoundCards?highlight=%28sound%29](https://wiki.ubuntu.com/HowToSetupSoundCards?highlight=%28sound%29)

---

### Post by camorri on 2006-04-09
alsaconf is available, see thread 156975, or just browser the audio/video forum, you should find it. There are instructions on how to install it.

---

### Post by razu on 2006-04-10
Cze&#347;&#263;,

If your card is compatibile with cs4236 driver try to add line 'snd-cs4236' in '/etc/modules' file. This will load cs4236 driver on system start.

Pozdrawiam
Radek

---

### Post by danrael on 2006-05-21
I also have an Optiplex GX1 with an onboard ISA sound card, Crystal Semiconductor CS4236.  I found the 'modules' file in the 'etc' folder, but was unable to add the command:  [COLOR="Blue"]snd-cs4236[/COLOR] as you suggested.  I tried opening up "new" and doing it there, but it was not accepted.    
How about a bit more information on how to do this?  Your input is appreciated by us newbies.

---

### Post by camorri on 2006-05-22
[QUOTE=danrael]I also have an Optiplex GX1 with an onboard ISA sound card, Crystal Semiconductor CS4236.  I found the 'modules' file in the 'etc' folder, but was unable to add the command:  [COLOR="Blue"]snd-cs4236[/COLOR] as you suggested.  I tried opening up "new" and doing it there, but it was not accepted.    
How about a bit more information on how to do this?  Your input is appreciated by us newbies.[/QUOTE]

You need root privliges to edit the file /etc/modules. In Ubuntu you can start up your farorite editer with the sudo command. Example 'sudo gedit' ( without the qouotes ) would start the editror gedit. You will be prompted for  a password, enter your user password and gedit will start ( with root privleges ). Now open up the file and add a line to it, save it, and you are done.

---

### Post by DarkW0lf on 2006-10-20
I am having problems witht he same soundcard and hardware, Dell Optiplex. Before I edit /etc/modules, I wanted to make sure that the module will work.

I use 'sudo modprobe snd-cs4236' and I am told the device cannot be found. In fact I have tried all three of the CS423x modules, not have worked with modprobe yet. And the onboard card is enabled.

---

### Post by Plautus on 2006-10-23
> **razu said:**
> Cze&#347;&#263;,

If your card is compatibile with cs4236 driver try to add line 'snd-cs4236' in '/etc/modules' file. This will load cs4236 driver on system start.

Pozdrawiam
Radek

Thanks for this tip, it works flawlessly on my Dell Optiplex GXa running Kubuntu.

Plautus

---

### Post by dearteaga on 2006-12-20
Thanks to all on this thread. 
I am reviving several OptiPlexes to run Edubuntu for some children  that cannot afford their own machines - for Christmas.
This sound issue was really giving me trouble.  
Adding the snd-cs4236 to the etc/module file worked the first time!
You've all helped some kids get sound!

---

