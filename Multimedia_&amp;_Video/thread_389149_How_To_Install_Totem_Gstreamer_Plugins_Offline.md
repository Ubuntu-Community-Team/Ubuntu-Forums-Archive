---
title: "How To: Install Totem Gstreamer Plugins Offline"
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by Masterj15 on 2007-03-20
I dicided to make this installation guide beacuse I was board of waiting for someone at my beryl thread. 

Totem is a media application that can play almost anything you throw at it. It can play mp3, mpeg, avi, ogg, mp4 and much, much more. The only problem is that you do not have the plugins for all those cool things when you first install ubuntu. I will tell you how to install totem offline. I don't have internet on my ubuntu computer but my mom's computer does have internet. (seh has windows XP) Now lets go though this installation step by step.


WARNING: THIS IS JUST A SUGESTION OF WHAT TO DO> THIS MEANS THAT IT WORKED FOR ME. IF IT DOES NOT WORK FOR THEN I'M SURE THEY HAVE SOME HOW TO AND TIPS.



Step 1. Get a flash drive or blank disk so that you can download the packages of the internet.

Step 2. You will have to install the lastest Gstreamer plugin avalable to world. That should be gstreamer 0.10 (or something like that.) Theirs more. You will have to install the dependences with it. The reason I say that is beacuse when you try to install a deb file file the manager would want all dependeces satified. So when you see the plugins and the tools and they say that the dependeces are that then make sure you download those. Then make sure you download the dependences' depdences. (LOL) I know it is kind of hard at first but you will get it. I have download over about 300 packages for everything that I have. Most of them I don't need but I like to be on the safe side.

You will have to doad these packages:
libgstreamer-plugins-base0.10-0
libgstreamer-plugins-base0.10-dev
libgstreamer-plugins-pulse0.10-0
libgstreamer0.10-0
libgstreamer0.10-0-dbg
libgstreamer0.10-dev
libgstreamer0.10-ruby1.8
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-base-doc
gstreamer0.10-plugins-good
gstreamer0.10-plugins-good-dbg
gstreamer0.10-plugins-good-doc
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-fluendo-mp3
gstreamer0.10-ffmpeg
gstreamer0.10-pitfdll 
gstreamer0.10-doc
gstreamer0.10-alsa
gstreamer0.10-esd
gstreamer-tools
gxine 
libxine-main1 
libxine-extracodecs 
ogle 
ogle-gui

And there dependences




The place to download all the plugins for gstreamer0.10 is here

[http://packages.debian.org/cgi-bin/search_packages.pl?keywords=Gstreamer&searchon=names&subword=1&version=all&release=all](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=Gstreamer&searchon=names&subword=1&version=all&release=all)

( I don't know why but the tred that i am posting is messed up. I cannot show click on anything) 

anyway search in their on page one and two for the things I said.

Step 3: Put them on your flash drive or cd or whatever mean of data storage and put the .deb packages on your computer. 

Step 4: Put each and every one of the packages through the Gdebi package manager and click on Install.

Step 5: Restart your computer and try to run one of your mpegs and mp3.

Step 6: Celebate the victory over the totem Gstreamer. (LOL)

Questions, statements, and answeres



Q1: Dude, why is my downloads going so awfully quick? 

A:That is normal. Mosts packages that you download for ubuntu are small. Problably in the kbs.



S1: Dude, they won't allow me to install because of some dependecy crap. Your Guide SUCKS.

A: You can think whatever you want about my guide and if you were halve smart enough you would have known about the dependecies and how to get rid of them if you were paying attention.



Q2: Their totally bugging out on me dude. Their saying that I need this dependecy and that dependency is saying I need this dependency. What do I do if they need each other to install itself?

A: Smart question. They way you go about doing this is that you have to install them through the terminal. Type in sudo dpkg  -i /whatever/whatever to install manualy. then do the same for the other package. then go into the synaptic package manager and uninstall something. (Make sure that you don't uninstall anything inportant or something that will uninstall more things.) this will configure your two packages Then reinstall the package you uninstalled. Then your done.


Q3: I don't want the plugins anymore so I deleted them. / I don't know what happened I was installing them and the wanted me to install libpango-common. The next thing i knew I could not read some fonts on my ubuntu. Their all is squares now.
What do I do if I want to remove something that I put on the computer but they want me to remove some things that the computer needs as well?

A:This was annoying for me as well. Go to the terminal and type in sudo aptitude.
Then type in / for a search bar. Type in your packages that you want to delete. Then type "-"
to remove package and that will downgrade to the origanal package for the live or non live disk. make sure you have you cd with on hand. then it should be back to the way it was.



S2: I typed in sudo dpkg -i /whatever/whatever and nothing worked. Like I said before, your GUIDE SUCKS. 

A: Stinks and stone will break my bones badly but words will never hurt me. Unless words were missles then we would all die.(LOL) To tell you the truth I am going on memory and I am wrong I will tell you which sudo command it is. I know that it does have an -i after it and I know that it does have those four letters in it. As far as the /whatever/whatever that is stupid if you typed that in, but hey I was as stupid 5 months ago when I heard about ubuntu. I would have typed that in. For eople who do not know this what you need to do is copy the package then pasts the package after the -i inthe terminal to make it work. Make sure their is a space after the -i.



I will edit this in the near future.

---

### Post by Masterj15 on 2007-03-21
You can posts your thoughts, comments, and what I said wrong so I can fix it.:)

---

### Post by LordMu on 2008-04-22
i appreciate you taking time to write this. i'm new to linux and had the same problem with internet. i haven't tried this yet; even if it doesn't work for me, you've given enough information to get a serious student thinking in the best direction. thank you :)

---

