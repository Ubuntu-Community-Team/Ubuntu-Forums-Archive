---
title: "How to Install MPlayer?"
date: 2009-10-31
forum: Multimedia Software
---

### Post by nonicutie on 2009-10-31
I have installed Mplayer but it doesnt seem work out. Im a newbie and i dont know how to run the program, its not an .exe, so what file i should run under? it says 'archive file' then  click open file with :( 

i have no choice what to open with :(

---

### Post by ugm6hr on 2009-10-31
Installing mplayer is much easier than that.

You can use point and click, but it is easier to just use Terminal:

```
sudo apt-get install mplayer
```

But before you do, what do you want mplayer for?  Most new users are perfectly happy with the default Totem / Rhythmbox combination for video / audio playback.

There are many links in the Start here page below that might be useful, particularly the section on installing programs.

---

### Post by SuperSonic4 on 2009-10-31
The repo version is good for most purposes but you can compile it still (for example if you want the latest [possibly unstable] version)

---

### Post by nonicutie on 2009-10-31
oh thanks. but i really cant see any movie or video using movie player or rythmbox. The file is .avi. it says there's no plugin installed. The request plugins are:

MPEG-1 Layer 3 (MP3) decoder
XVID MPEG-4 decoder. 

So i installed mplayer to resolve, but i cant install mplayer either :(

---

### Post by axel206 on 2009-10-31
Take a look at this:

[Ubuntu Karmic Koala 9.10 Post Installation Guide](http://www.my-guides.net/en/content/view/172/26/)

---

### Post by SuperSonic4 on 2009-10-31
Sounds like you need some codecs

Best option IMO would be to open Synaptic and search for either those two or the word "codec". ubuntu-restricted-extras is bound to have them but that comes with a load of potentially unwanted stuff like Java and Flash

---

### Post by nonicutie on 2009-10-31
I have run command using Post Installation Guide in command but the result is 
noni@nonicutie:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for noni: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras



Do i need to reinstall my Ubuntu? At one program i run into, it says, my ubuntu is not genuine.

Im not sure what to do by synaptic or codec. But it is true, that i have no java either flash player.

---

### Post by coffeecat on 2009-10-31
> **nonicutie said:**
>  E: Couldn't find package ubuntu-restricted-extras

It sounds as though the package metadata hasn't been refreshed since installing. Do you have a working internet connection? Try:

```
sudo apt-get update
```After that's finished, try to redo:

```
sudo apt-get install ubuntu-restricted-extras
```> **nonicutie said:**
> At one program i run into, it says, my ubuntu is not genuine.

:shock:

Which program? What was the exact error message?

> **nonicutie said:**
> i have no java either flash player.

ubuntu-restricted-extras will give you Java, flash and most of the codecs you need. Let's see if we can solve the problem with installing ubuntu-restricted-extras.

---

### Post by nonicutie on 2009-10-31
well DONE. i can watch movie and run flash player and java altogether. Thanks alot.

I dont really remember what isnt genuine, i guess mplayer. But forget it, its all run well now. I dont need mplayer:)

I still have an applications error, installing skype. ill look upto another thread for this.

Thanks again.

---

### Post by ugm6hr on 2009-10-31
For solutions to all multimedia problems with Ubuntu, follow the guide in the Multimedia link below.

---

### Post by nonicutie on 2009-10-31
okay. I will. Thanks for your assistance. Cheers. :)

---

