---
title: "Help installing codecs"
date: 2009-02-12
forum: Multimedia Software
---

### Post by servlet on 2009-02-12
I am a windows XP user, and installed ubuntu last night, but I am not able to play many audio/video formats.

Can any one help me in installing restricted multimedia codecs offline.

Note: The PC dont have internet access, so I will have to download codecs and then install it offline.

**Beryl**
I want to install Beryl, again without internet connection.

I am using ubuntu 8.10

Thanks

---

### Post by logos34 on 2009-02-12
[https://help.ubuntu.com/community/RestrictedFormats#Playing%20Restricted%20Formats](https://help.ubuntu.com/community/RestrictedFormats#Playing%20Restricted%20Formats)

[http://wubdepends.sourceforge.net/](http://wubdepends.sourceforge.net/)

hope that helps

---

### Post by servlet on 2009-02-12
Being a widows user, its really strange for me that, all the softwares must be installed from repositories and there are no installables.

---

### Post by servlet on 2009-02-12
IS this the only way? Cant I get installers like windows?
Some one guide me, before I get frustrated with ubuntu and go back to windows.

---

### Post by cb951303 on 2009-02-12
Go to synaptics package manager, and search for "ubuntu-restricted-extras". Install it, Problem solved :popcorn:

repos are the linux way of installing software. you can download *.deb files from net and double click on them to install but, using repos has *much more* advantages.

---

### Post by servlet on 2009-02-12
> **cb951303 said:**
> Go to synaptics package manager, and search for "ubuntu-restricted-extras". Install it, Problem solved :popcorn:


Will that work without internet connection?

---

### Post by cb951303 on 2009-02-12
> **servlet said:**
> Will that work without internet connection?

ah sorry! I didn't see that you have no internet connection.
you can download single packages from packages.ubuntu.com but note that there will be a lot of dependencies :/

---

### Post by SuperSonic4 on 2009-02-12
No it won't.

You need an internet connection and you can do ```
sudo apt-get install -d ubuntu-restricted-extras 
``` which is download only which can then be transferred (although flash may be a problem).

---

### Post by servlet on 2009-02-12
What's the solution then? Does that mean, computers which are not on network and don't have direct internet access should not install linux? Or it can be a pain.

---

### Post by webyvolve on 2009-02-12
Hello servlet, I'm just a brand new user myself, but I do know enough to tell you that there are essentially no installers in linux. To do so means doing the "installing" yourself; downloading the packages off the internet, and then getting a compiler to compile the program on your computer. If there is any possible way to get internet access to the computers in question, it would probably save you a lot of headaches.

---

### Post by cb951303 on 2009-02-12
> **webyvolve said:**
> and then getting a compiler to compile the program on your computer.

average user doesn't need to compile its own packages

---

### Post by servlet on 2009-02-12
This indicates why lots of non techies prefers Windows. Sorry, but thats what I feel at this time. Actually I am not a dumb computer operator, I am a programmer, but this is my very first experience with linux, if given proper instructions, I can do it, but I even don't find proper docs that explains this type of scenarios.

---

### Post by webyvolve on 2009-02-12
True, but in the absence of an internet connection? Or does the terminal just do a compile for you?

---

### Post by cb951303 on 2009-02-12
> **servlet said:**
> This indicates why lots of non techies prefers Windows. Sorry, but thats what I feel at this time. Actually I am not a dumb computer operator, I am a programmer, but this is my very first experience with linux, if given proper instructions, I can do it, but I even don't find proper docs that explains this type of scenarios.

you're right at some point. there isn't an easy way to install codecs with a machine not connected to net. 

but you do realise that you need to download codecs in windows too, right? the fact that there is some illegal codec packs on internet with 1 click installers doesn't mean windows users has an advantage.

that being said, if you are willing to pay, there is a comerical codec pack which can play a lot of formats here: [http://www.fluendo.com/](http://www.fluendo.com/)

---

### Post by cb951303 on 2009-02-12
> **webyvolve said:**
> True, but in the absence of an internet connection? Or does the terminal just do a compile for you?

compilation is only necesseary if there is no binary (*.deb for ubuntu/debian) package for that application.

---

### Post by webyvolve on 2009-02-12
> **servlet said:**
> This indicates why lots of non techies prefers Windows. Sorry, but thats what I feel at this time. Actually I am not a dumb computer operator, I am a programmer, but this is my very first experience with linux, if given proper instructions, I can do it, but I even don't find proper docs that explains this type of scenarios.

I can understand you completely. I didn't mean to imply that you were computer illiterate; I'm sorry if it sounded that way. I am currently banging my head against a wall as well, over almost the same issue- codecs. Linux, even now with all of its advances and good points, is still not perfect, and (except for the enthusiastic) it should probably be viewed as a project. That is my current position.

---

### Post by servlet on 2009-02-12
Hey webyvolve, don't be sorry. It wasn't for you or any one else.

---

### Post by johnjohn2 on 2009-02-12
> **servlet said:**
> This indicates why lots of non techies prefers Windows. Sorry, but thats what I feel at this time. Actually I am not a dumb computer operator, I am a programmer, but this is my very first experience with linux, if given proper instructions, I can do it, but I even don't find proper docs that explains this type of scenarios.

There are packages you may install and they are .deb (As in Debian)

The same case is with windows usually no Internet means no new software.

Synaptic as mentioned before is your best friend and i would highly recommend you connect your rig to the outside world.
Synaptic takes all the hard work out of installing software as it makes sure all your dependencies are present and correct,if not it will usually mark the correct packages to install allowing your chosen application to work.

The reason why you cannot play DVD movies out of the box is due to copyright restrictions.
But they may be added later.

Regards John

---

### Post by servlet on 2009-02-12
> **johnjohn2 said:**
> 

The same case is with windows usually no Internet means no new software.



But I can use my little pendrive to get it from somewhere on the net.

Anyway, that's no the point here. 
What all packages do I need to get. can some one please point out.

ubuntu 8.10 = intrepid right?

---

### Post by servlet on 2009-02-12
codecs are not only thing, I need to download Beryl too.

---

### Post by wildman4god on 2009-02-12
I also don't have an internet connection so I use a program called keryx: keryx.betaserver.org

It is a pakage manager that sits on your flash drive and runns on windows/mac/linux, so far it only has a gui for the windows machine, but to create a project plug it into linux computer and run a command, which the toutorial on the website tells you, and then plug it into a windows machine that has internet and open up the keryx gui and select the packages you want, more detail instructions are on the website tutorial. also a quick tip to find all codecs, goto appnr.com, an online package manager, click on codecs in side bar and it will list all codecs, you obviously can't use it to install anything but it will tell you the name of the packages you need, so you can find them in keryx. if you have any other problems pm me. good luck.

---

### Post by wildman4god on 2009-02-12
> **servlet said:**
> codecs are not only thing, I need to download Beryl too.

ubuntu has compiz, whats wrong with that?

---

### Post by servlet on 2009-02-12
> **wildman4god said:**
> ubuntu has compiz, whats wrong with that?

I don't know, I heard that Beryl gives cool effects.

---

### Post by EXCiD3 on 2009-02-12
Beryl is outdated, Its now called Compiz Fusion which is included in Ubuntu. You may want to install the extra plugins pack and the compizconfig-settings-manager to configure it.

Btw, I'm the developer of Keryx, hope you like it! ;) I am working on getting Keryx to install the packages for you once you get back to your linux box at home and also an executable for linux so that you can use the GUI. :D

---

### Post by cb951303 on 2009-02-12
I forgot to tell you that, there is a ubuntu based linux distro called Mint, which I believe has all you want out of the box :popcorn:

---

### Post by servlet on 2009-02-13
> **EXCiD3 said:**
> Beryl is outdated, Its now called Compiz Fusion which is included in Ubuntu. You may want to install the extra plugins pack and the compizconfig-settings-manager to configure it.

Btw, I'm the developer of Keryx, hope you like it! ;) I am working on getting Keryx to install the packages for you once you get back to your linux box at home and also an executable for linux so that you can use the GUI. :D

Thanks a lot buddy, You have created a very useful tool, I have downloaded it and had a look at, I think it will solve my problem.

Thanks again, Nice utility

---

### Post by servlet on 2009-02-13
I have created a Keryx project on my linux box, and downloaded ubuntu-restricted-extras from XP machine. Now I would be able to install it on linux box ryt? and that will solve codecs problem.

---

### Post by UNME on 2009-02-13
[Servlet] I think you should look in this location: [http://packages.medibuntu.org/intrepid/index.html](http://packages.medibuntu.org/intrepid/index.html)

They are packages that could not be given on Ubuntu because of legal issues.

One more thing:

think of situation: you don't have internet and you want to listen to ogg format songs on windows. what will you do?

If linux distribute all these in a package, we will be facing legal problem (say thanks to windows).

Also one last thing you can convert your mp3 files to linux compatible format (just like itunes for apple ! - apple also cannot make mp3 compatible to there device so they came with Itune)

I hope above link helps you.

---

### Post by wildman4god on 2009-02-13
> **servlet said:**
> I have created a Keryx project on my linux box, and downloaded ubuntu-restricted-extras from XP machine. Now I would be able to install it on linux box ryt? and that will solve codecs problem.

Not all your codec problems, like I said, go to appnr.com and click on codecs in the side bar and all those packages that show up, click on each one for more info including the actual package name, those are what you want to download if you want full codec support.

---

### Post by venupatterkandy on 2009-10-11
> **servlet said:**
> I am a windows XP user, and installed ubuntu last night, but I am not able to play many audio/video formats.

Can any one help me in installing restricted multimedia codecs offline.

Note: The PC dont have internet access, so I will have to download codecs and then install it offline.

**Beryl**
I want to install Beryl, again without internet connection.

I am using ubuntu 8.10

Thanks
i have installed realplayer in ubuntu 8.10 , it wanted executable decoder , how can i down load it, thanks

---

### Post by sloth_ibanez on 2009-11-03
hey friends i am new to linux, downloaded keryx on my windows but cant use it. i have renamed my pendrive as mugdha. can u help me with the command line to use keryx. i have no idea  evn after i read the keryx tutorial. when i try to navigate to linux folder in my pendrive it says no such file or directory. i am using ubuntu 9.10. also i will be glad if you give me instructions about using the gui to use keryx. i have wxversion installed on ubuntu. but have slow internet so want to use keryx.
thnks in advance

---

### Post by mac9416 on 2009-11-04
Hi there!

First, [download Keryx]("http://keryxproject.org/download"). Then extract it onto your flash drive.

Before downloading packages, you must create a snapshot, or "project," on your offline computer. To do this, plug in your flash drive, go to Places > Computer, and double-click your flash drive. This will mount it. Now open Applications > Accessories > Terminal and run the following commands:

```
$ cd /media/mugdha/keryx_0.92.3/linux  # Replace "mugdha" with your flash drive name
$ python ./keryx.py --create sloth_ibanez debian  # Replace "sloth_ibanez" with the desired project name
```

Since you have wxversion installed, you can replace the second command with the following one and create your project using the GUI...

```
$ python ./keryx.py
```

That's it! Your project has been created. Now, take it back to the online computer (which you say is XP for you) and run keryx.exe. Open the project named "sloth_ibanez," then start downloading!

---

### Post by izh34 on 2009-11-17
Maybe you could follow this,

[SIZE=2]1. unpack/extract
   2. double-click the file "install.sh" on folder "offline-installer"
   3. Select "run in terminal"
   4. Enter your password if/when the installer asks you
   5. Acept Java license when that appears, by pressing: <TAB> <ENTER> <TAB> <ENTER>
   6. When program finishes, close the window and remove the folder "offline-installer" 

download file :

[http://www.zshare.net/download/59368408526cd812/](http://www.zshare.net/download/59368408526cd812/)[/SIZE][SIZE=2]

source:
[http://hacktolive.org/wiki/Ubuntu-restricted-extras_offline_installer](http://hacktolive.org/wiki/Ubuntu-restricted-extras_offline_installer)[/SIZE]

---

### Post by eryulant on 2009-11-17
I believe I once just plonked, ie without installing, a lot of codec files into two locations:
/usr/local/lib/codecs/ and /usr/libs/codecs on my xandros eeepc, and mplayer 
just saw and used them. More at [http://www.mplayerhq.hu/DOCS/README](http://www.mplayerhq.hu/DOCS/README)
also you could search [http://forum.eeeuser.com/](http://forum.eeeuser.com/)
becuase that's where I got the idea from.

---

