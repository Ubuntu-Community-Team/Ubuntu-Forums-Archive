---
title: "[SOLVED] Unable to view youtube videos"
date: 2008-08-15
forum: Multimedia Software
---

### Post by Holleywood on 2008-08-15
I installed Gutsy, and I am unable to view videos on Youtube. Help please.

---

### Post by Shunsuke_01 on 2008-08-15
> **Holleywood said:**
> I installed Gutsy, and I am unable to view videos on Youtube. Help please.
You will need to install flash player.

Try this (in terminal):

```
sudo apt-get install flashplugin-nonfree
```


Edit: I think you can update the flash plugin by running:

```
sudo update-flashplugin
```

---

### Post by tech0007 on 2008-08-15
Streaming videos from the web requires flash. Open a terminal and type:

```

sudo apt-get update
sudo apt-get install flashplugin-nonfree

```

---

### Post by Holleywood on 2008-08-15
Thank you very much.

---

### Post by Aumonae on 2009-05-31
> **Shunsuke_01 said:**
> You will need to install flash player.

Try this (in terminal):

```
sudo apt-get install flashplugin-nonfree
```
Edit: I think you can update the flash plugin by running:

```
sudo update-flashplugin
```


I did this and still can only hear the video.... the video screen just stays blank while the audio plays. How do I fix this (and I am only using Ubuntu (9.xx) because I hate Windows... not because I can code or anything.

---

### Post by kc4mts on 2009-07-23
Hello There!
Try this to solve your issue...
One other thing you can try is as follows:  (follow these directions ONLY IF you are using Ubuntu AND Synaptic Package Manager) in Synaptic search for Adobe flash and right click and chose "mark for complete removal" Adobe-flashplugin and select apply. Only after this is completed, do NOT install from Synaptic, instead, go to [http://www.adobe.com/go/getflash](http://www.adobe.com/go/getflash) and select the correct package for you system ( they have YUM, tar.gz, rpm, and deb packages) at the time of this writing it is version 10.0.22.87-1 and I would recommend installing instead of saving and then installing( it saves a lot of work). This should get your flash pages working. Almost as soon as you finish doing this, synaptic will alert you to an update (ver 10.0.22.87-2). This update from Ubuntu repositories seems to work fine.
 Back ground: I have not had flash working for a long, long time and and completely removing it and re-installing from Adobes site (not the Ubuntu repository)
seems to have cured my problems. I can only assume that something was incorrect on the 8.04 Ubuntu Live CD or one of the updates shortly after I reinstalled Ubuntu on this machine. The original Flash version was 9.0.....something. 

Disclaimer......this fix may work for other flavors of Linux but has not been tested on them... use at your own risk. Back up files if possible before trying this method as I REALLY do not like screwing up other peoples machines....remember re-image takes 20 minutes and one or two explitives....reinstall can last a lifetime.

---

