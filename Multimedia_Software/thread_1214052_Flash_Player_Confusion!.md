---
title: "Flash Player Confusion!"
date: 2009-07-15
forum: Multimedia Software
---

### Post by bellabrokenxx on 2009-07-15
i just got my laptop screen fixed after quite some time and i log in to see that my flash player doesn't work on most websites. i click on the 'download flashplayer' and i download it and nothing happens.

 i'm absolutely begginer and have no knowledge at this.

please help??

---

### Post by igorzwx on 2009-07-15
make this:
**[Howto make Ubuntu 9.04 (Jaunty Jackalope) Multimedia Ready]("http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html")**

[http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html](http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html)

and relax

---

### Post by bellabrokenxx on 2009-07-15
> **igorzwx said:**
> make this:
**[Howto make Ubuntu 9.04 (Jaunty Jackalope) Multimedia Ready]("http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html")**

[http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html](http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html)

and relax

i have hardy heron.

---

### Post by Ra-Hoor-Khuit on 2009-07-15
See this tutorial:  [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by igorzwx on 2009-07-15
It is the same, you should only enable Medi-Repos for Hardy
or simply make this:
QUOTE:
**Any** Ubuntu Release and keyring: 
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q updatesee also
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by igorzwx on 2009-07-15
**Any** Ubuntu Release and keyring: 
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

---

### Post by bellabrokenxx on 2009-07-15
> **Ra-Hoor-Khuit said:**
> See this tutorial:  [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

well that didnt work At ALL.

and>  Any Ubuntu Release and keyring:
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
didn't work either.

---

### Post by Ra-Hoor-Khuit on 2009-07-15
Okay... Time to play hardball.

Open Synaptic.

Search on **swfdec**.
Do you get hits/installed packages on that search?  If so, mark them for removal.

Search on **gnash**.
Do you get hits/installed packages on that search?  If so, mark them for removal.

Install the Adobe Flash Player from the adobe website listed below.
It's a .deb so you download it, and double-click on the file to install it. 
 Restart Firefox after installing:

[http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)

You want the **Flash Player 10 for Linux (.deb)** package at the bottom once you've selected "Linux" from the drop-down menu.

---

### Post by lovinglinux on 2009-07-15
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by igorzwx on 2009-07-15
Actually, if you simply enable the Repositories, nothing should happen.
You should install something from them :p

---

### Post by bellabrokenxx on 2009-07-15
> **igorzwx said:**
> Actually, if you simply enable the Repositories, nothing should happen.
You should install something from them :p

How do i do that?


and to the others; ive tried all of yours but some stuff shows others don't.
(i.e. music players dont work, videos do.)

---

### Post by lovinglinux on 2009-07-15
> **bellabrokenxx said:**
> How do i do that?


and to the others; ive tried all of yours but some stuff shows others don't.
(i.e. music players dont work, videos do.)

Open "System >> Administration >> Software Sources", then make sure the option "Software restricted by copyright or legal issues (multiverse)" is selected. Then run the following command in a terminal:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash adobe-flashplugin flashplugin-nonfree && sudo apt-get install flashplugin-nonfree
```

> [color=#CC0000]**How to run commands in a Terminal: **[/color]Open "Applications >> Accessories >> Terminal", then type or paste the code (CTRL+SHIFT+V) and hit *Enter*. You might be prompted to enter your password. You cannot see it while you type, but it is there. Then just hit *Enter* again to run the command. Please do not run commands without knowing what they do. If you do not understand what a command does, ask for explanations.

From **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by igorzwx on 2009-07-15
Repositories are already enabled.
we make it once more now:

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

[COLOR=#990000]**Run**[/COLOR]
[COLOR=#3333FF]**$ sudo apt-get update**[/COLOR]


[COLOR=#990000]**Now you can Install non-free-codecs**[/COLOR]
[COLOR=#3333FF]**$ sudo apt-get install non-free-codecs**[/COLOR]
[COLOR=#3333FF][B]
[/B][/COLOR]
[COLOR=#006600]It will enables your system to support for MP3 and various other audio formats, unrar. Java runtime environment, Flash plugin, Microsoft fonts, w32codecs etc![/COLOR]
[COLOR=#990000]**You can install more codecs and DVD Support by using**[/COLOR]
[COLOR=#990000][B]
[/B][/COLOR]
[COLOR=#3333FF]$ sudo apt-get install libdvdcss2 libxine1-ffmpeg gxine   mencoder 
[/COLOR]
[COLOR=#3333FF][/COLOR]

[COLOR=#006600]It will help you to run DVDs, AVI files and other mpeg codecs.[/COLOR]
[COLOR=#990000]**Now Install Famous VLC player and Mplayer**[/COLOR]
[COLOR=#3333FF][B]$ sudo apt-get install vlc mplayer 
[/B][/COLOR]
[COLOR=#3333FF][B]
[/B][/COLOR]
[COLOR=#990000]**You can Install following interesting and useful utilities**[/COLOR]
[COLOR=#990000]**Audio Editing Software Audacity**[/COLOR]
[COLOR=#3333FF]**$ sudo apt-get install  audacity**[/COLOR]
[COLOR=#3333FF][B]
[/B][/COLOR]
[COLOR=#990000]**Adobe Acrobat Reader**[/COLOR]
[COLOR=#3333FF]**$sudo apt-get  install acroread acroread-plugins**[/COLOR]
[COLOR=#3333FF][B]
[/B][/COLOR]
[COLOR=#3333FF]**[http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html](http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html)**[/COLOR]
[COLOR=#3333FF][B]
[/B][/COLOR]
[COLOR=#3333FF]**try to make it carefully!**[/COLOR]
[COLOR=#3333FF][B]
[/B][/COLOR]
[COLOR=#3333FF][B]Good luck!
[/B][/COLOR]

---

### Post by bellabrokenxx on 2009-07-15
ok, and this is what i get.
```
bella@Rawr:~$ sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash adobe-flashplugin flashplugin-nonfree && sudo apt-get install flashplugin-nonfree
[sudo] password for bella: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package swfdec-mozilla
bella@Rawr:~$


```

---

### Post by lovinglinux on 2009-07-15
> **bellabrokenxx said:**
> ok, and this is what i get.
```
bella@Rawr:~$ sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash adobe-flashplugin flashplugin-nonfree && sudo apt-get install flashplugin-nonfree
[sudo] password for bella: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package swfdec-mozilla
bella@Rawr:~$


```

If it can't find them then it's good, but let's split the command to avoid the error

```
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin 
sudo apt-get remove flashplugin-nonfree 
sudo apt-get install flashplugin-nonfree

```

---

### Post by bellabrokenxx on 2009-07-15
OK, i did that, and it comes to
```
The following packages will be REMOVED:
  adobe-flashplugin
0 upgraded, 0 newly installed, 1 to remove and 306 not upgraded.
After this operation, 10.2MB disk space will be freed.
Do you want to continue [Y/n]? 

```
after putting yes it says 'Abort.'
is that good or bad?

---

### Post by lovinglinux on 2009-07-15
> **bellabrokenxx said:**
> OK, i did that, and it comes to
```
The following packages will be REMOVED:
  adobe-flashplugin
0 upgraded, 0 newly installed, 1 to remove and 306 not upgraded.
After this operation, 10.2MB disk space will be freed.
Do you want to continue [Y/n]? 

```
after putting yes it says 'Abort.'
is that good or bad?

I think is bad. It shouldn't do that. Have you tried to play flash videos after those commands?

BTW, you have 306 package updates waiting for you. You should update first.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by igorzwx on 2009-07-15
**[How can *Chaos Theory* be applied to Crisis *Management*?]("http://www.santafe.edu/%7Egmk/MFGB/node10.html")**

How can *Chaos Theory* be applied to Crisis *Management*? As we tried to explain above, *chaos theory* is intrinsically based on the treatment of problems as **...**
[www.santafe.edu/~gmk/MFGB/node10.html](www.santafe.edu/~gmk/MFGB/node10.html) - [Cached]("http://209.85.129.132/search?q=cache:mTFVxhSEuKkJ:www.santafe.edu/%7Egmk/MFGB/node10.html+chaos+management+theory&cd=6&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:www.santafe.edu/%7Egmk/MFGB/node10.html")

---

### Post by bellabrokenxx on 2009-07-15
thanks for updating, i didnt know what that meant at all.

as you can see im a total (i hate this word but) noob at this technical stuff.

and flash videos work fine. :]

but i have a music player that does NOT work

[IMG]http://i531.photobucket.com/albums/dd354/IzzyKiss/Screenshot.png[/IMG] 

and i get something like that.

---

### Post by lovinglinux on 2009-07-15
> **igorzwx said:**
> **[How can *Chaos Theory* be applied to Crisis *Management*?]("http://www.santafe.edu/%7Egmk/MFGB/node10.html")**

How can *Chaos Theory* be applied to Crisis *Management*? As we tried to explain above, *chaos theory* is intrinsically based on the treatment of problems as **...**
[www.santafe.edu/~gmk/MFGB/node10.html](www.santafe.edu/~gmk/MFGB/node10.html) - [Cached]("http://209.85.129.132/search?q=cache:mTFVxhSEuKkJ:www.santafe.edu/%7Egmk/MFGB/node10.html+chaos+management+theory&cd=6&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:www.santafe.edu/%7Egmk/MFGB/node10.html")

What is the point?

---

### Post by bellabrokenxx on 2009-07-15
> **igorzwx said:**
> **[How can *Chaos Theory* be applied to Crisis *Management*?]("http://www.santafe.edu/%7Egmk/MFGB/node10.html")**

How can *Chaos Theory* be applied to Crisis *Management*? As we tried to explain above, *chaos theory* is intrinsically based on the treatment of problems as **...**
[www.santafe.edu/~gmk/MFGB/node10.html](www.santafe.edu/~gmk/MFGB/node10.html) - [Cached]("http://209.85.129.132/search?q=cache:mTFVxhSEuKkJ:www.santafe.edu/%7Egmk/MFGB/node10.html+chaos+management+theory&cd=6&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:www.santafe.edu/%7Egmk/MFGB/node10.html")

.....? what is that for? because i know its not for me. >>

---

### Post by lovinglinux on 2009-07-15
> **bellabrokenxx said:**
> .....? what is that for? because i know its not for me. >>

I think is for me.

---

### Post by igorzwx on 2009-07-15
I just wnted to say that it is not a good thing to mix everything together.
It might be better to try one solution and see if it works.
And make it carefully.
Then you can try another solution.
I propose to start once more here:

 				 				**Re: Flash Player Confusion!** 			
 			 			 		   		 		 		Repositories are already enabled.
we make it once more now:

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

[COLOR=#990000]**Run**[/COLOR]
[COLOR=#3333ff]**$ sudo apt-get update**[/COLOR]


[COLOR=#990000]**Now you can Install non-free-codecs**[/COLOR]
[COLOR=#3333ff]**$ sudo apt-get install non-free-codecs**[/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#006600]It will enables your system to support for MP3 and various other audio formats, unrar. Java runtime environment, Flash plugin, Microsoft fonts, w32codecs etc![/COLOR]
[COLOR=#990000]**You can install more codecs and DVD Support by using**[/COLOR]
[COLOR=#990000][/COLOR]
[COLOR=#3333ff]$ sudo apt-get install libdvdcss2 libxine1-ffmpeg gxine   mencoder 
[/COLOR]


[COLOR=#006600]It will help you to run DVDs, AVI files and other mpeg codecs.[/COLOR]
[COLOR=#990000]**Now Install Famous VLC player and Mplayer**[/COLOR]
[COLOR=#3333ff][B]$ sudo apt-get install vlc mplayer 
[/B][/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#990000]**You can Install following interesting and useful utilities**[/COLOR]
[COLOR=#990000]**Audio Editing Software Audacity**[/COLOR]
[COLOR=#3333ff]**$ sudo apt-get install  audacity**[/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#990000]**Adobe Acrobat Reader**[/COLOR]
[COLOR=#3333ff]**$sudo apt-get  install acroread acroread-plugins**[/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#3333ff]**[http://shibuvarkala.blogspot.com/200...jackalope.html]("http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html")**[/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#3333ff]**try to make it carefully!**[/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#3333ff]**Good luck!**[/COLOR]

---

### Post by bellabrokenxx on 2009-07-15
ooooh, OK.

---

### Post by bellabrokenxx on 2009-07-15
> **igorzwx said:**
> I just wnted to say that it is not a good thing to mix everything together.
It might be better to try one solution and see if it works.
And make it carefully.
Then you can try another solution.
I propose to start once more here:

 				 				**Re: Flash Player Confusion!** 			
 			 			 		   		 		 		Repositories are already enabled.
we make it once more now:

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

[COLOR=#990000]**Run**[/COLOR]
[COLOR=#3333ff]**$ sudo apt-get update**[/COLOR]


[COLOR=#990000]**Now you can Install non-free-codecs**[/COLOR]
[COLOR=#3333ff]**$ sudo apt-get install non-free-codecs**[/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#006600]It will enables your system to support for MP3 and various other audio formats, unrar. Java runtime environment, Flash plugin, Microsoft fonts, w32codecs etc![/COLOR]
[COLOR=#990000]**You can install more codecs and DVD Support by using**[/COLOR]
[COLOR=#990000][/COLOR]
[COLOR=#3333ff]$ sudo apt-get install libdvdcss2 libxine1-ffmpeg gxine   mencoder 
[/COLOR]


[COLOR=#006600]It will help you to run DVDs, AVI files and other mpeg codecs.[/COLOR]
[COLOR=#990000]**Now Install Famous VLC player and Mplayer**[/COLOR]
[COLOR=#3333ff][B]$ sudo apt-get install vlc mplayer 
[/B][/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#990000]**You can Install following interesting and useful utilities**[/COLOR]
[COLOR=#990000]**Audio Editing Software Audacity**[/COLOR]
[COLOR=#3333ff]**$ sudo apt-get install  audacity**[/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#990000]**Adobe Acrobat Reader**[/COLOR]
[COLOR=#3333ff]**$sudo apt-get  install acroread acroread-plugins**[/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#3333ff]**[http://shibuvarkala.blogspot.com/200...jackalope.html]("http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html")**[/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#3333ff]**try to make it carefully!**[/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#3333ff]**Good luck!**[/COLOR]

OK, i started it and got this

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
bella@Rawr:~$

---

### Post by igorzwx on 2009-07-15
Close Synaptic 
and make this

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

[COLOR=#990000]**Run**[/COLOR]
[COLOR=#3333ff]**$ sudo apt-get update**[/COLOR]


[COLOR=#990000]**Now you can Install non-free-codecs**[/COLOR]
[COLOR=#3333ff]**$ sudo apt-get install non-free-codecs**[/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#006600]It will enables your system to support for MP3 and various other audio formats, unrar. Java runtime environment, Flash plugin, Microsoft fonts, w32codecs etc![/COLOR]
[COLOR=#990000]**You can install more codecs and DVD Support by using**[/COLOR]
[COLOR=#990000][/COLOR]
[COLOR=#3333ff]$ sudo apt-get install libdvdcss2 libxine1-ffmpeg gxine   mencoder 
[/COLOR]


[COLOR=#006600]It will help you to run DVDs, AVI files and other mpeg codecs.[/COLOR]
[COLOR=#990000]**Now Install Famous VLC player and Mplayer**[/COLOR]
[COLOR=#3333ff][B]$ sudo apt-get install vlc mplayer 
[/B][/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#990000]**You can Install following interesting and useful utilities**[/COLOR]
[COLOR=#990000]**Audio Editing Software Audacity**[/COLOR]
[COLOR=#3333ff]**$ sudo apt-get install  audacity**[/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#990000]**Adobe Acrobat Reader**[/COLOR]
[COLOR=#3333ff]**$sudo apt-get  install acroread acroread-plugins**[/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#3333ff]**[http://shibuvarkala.blogspot.com/200...jackalope.html]("http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html")**[/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#3333ff]**try to make it carefully!**[/COLOR]

---

### Post by lovinglinux on 2009-07-15
> **igorzwx said:**
> I just wnted to say that it is not a good thing to mix everything together.
It might be better to try one solution and see if it works.
And make it carefully.
Then you can try another solution.
I propose to start once more here:

 				 				**Re: Flash Player Confusion!** 			
 			 			 		   		 		 		Repositories are already enabled.
we make it once more now:

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

[COLOR=#990000]**Run**[/COLOR]
[COLOR=#3333ff]**$ sudo apt-get update**[/COLOR]


[COLOR=#990000]**Now you can Install non-free-codecs**[/COLOR]
[COLOR=#3333ff]**$ sudo apt-get install non-free-codecs**[/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#006600]It will enables your system to support for MP3 and various other audio formats, unrar. Java runtime environment, Flash plugin, Microsoft fonts, w32codecs etc![/COLOR]
[COLOR=#990000]**You can install more codecs and DVD Support by using**[/COLOR]
[COLOR=#990000][/COLOR]
[COLOR=#3333ff]$ sudo apt-get install libdvdcss2 libxine1-ffmpeg gxine   mencoder 
[/COLOR]


[COLOR=#006600]It will help you to run DVDs, AVI files and other mpeg codecs.[/COLOR]
[COLOR=#990000]**Now Install Famous VLC player and Mplayer**[/COLOR]
[COLOR=#3333ff][B]$ sudo apt-get install vlc mplayer 
[/B][/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#990000]**You can Install following interesting and useful utilities**[/COLOR]
[COLOR=#990000]**Audio Editing Software Audacity**[/COLOR]
[COLOR=#3333ff]**$ sudo apt-get install  audacity**[/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#990000]**Adobe Acrobat Reader**[/COLOR]
[COLOR=#3333ff]**$sudo apt-get  install acroread acroread-plugins**[/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#3333ff]**[http://shibuvarkala.blogspot.com/200...jackalope.html]("http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html")**[/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#3333ff]**try to make it carefully!**[/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#3333ff]**Good luck!**[/COLOR]

Well, so why are you recommending installing audacity, acrobat reader and other stuff?

The OP clearly has a problem of conflict between flash players. Nothing more.

---

### Post by igorzwx on 2009-07-15
audacity is not necesary

codecs are needed

[COLOR=#990000]**Now you can Install non-free-codecs**[/COLOR]
[COLOR=#3333ff]**$ sudo apt-get install non-free-codecs**[/COLOR]
[COLOR=#3333ff][/COLOR]
[COLOR=#006600]It will enables your system to support for MP3 and various other audio formats, unrar. Java runtime environment, Flash plugin, Microsoft fonts, w32codecs etc![/COLOR]
[COLOR=#990000]**You can install more codecs and DVD Support by using**[/COLOR]
[COLOR=#990000][/COLOR]
[COLOR=#3333ff]$ sudo apt-get install libdvdcss2 libxine1-ffmpeg gxine   mencoder [/COLOR]

---

### Post by lovinglinux on 2009-07-15
My suggestion:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove flashplugin-nonfree 
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by igorzwx on 2009-07-15
I think it is not necessary

---

### Post by igorzwx on 2009-07-15
why install restricted, the remove them, and once more?

---

### Post by lovinglinux on 2009-07-15
> **igorzwx said:**
> I think it is not necessary

Just to let you know, the problem was fixed via PM following the steps I suggested in my first post. The packages *swfdec-mozilla* and *mozilla-plugin-gnash* were removed previously, so all the OP had to do was:

```
sudo apt-get remove flashplugin-nonfree
```

```
sudo apt-get remove adobe-flashplugin
```

```
sudo apt-get install flashplugin-nonfree
```

For future reference:

See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by igorzwx on 2009-07-15
Hi lovinglinux!

I sent you a private message with explanation.
We may better discuss the problem,
not to mixing this with troubleshooting

Best,
Igor

---

### Post by lovinglinux on 2009-07-15
> **igorzwx said:**
> Hi lovinglinux!

I sent you a private message with explanation.
We may better discuss the problem,
not to mixing this with troubleshooting

Best,
Igor

There is no need to discuss this further unless you have any additional questions. Medibuntu is great, but not related to the OP problem.

For additional media support, just follow [Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683). It explains how to enable Medibuntu repositories to install players, plugins and codecs related to other audio and video issues.

---

### Post by igorzwx on 2009-07-15
Perhaps, I am absolutely stupid,
but I fail to understand what you are going to say.

---

### Post by lovinglinux on 2009-07-15
> **igorzwx said:**
> Perhaps, I am absolutely stupid,
but I fail to understand what you are going to say.

What do you want?

---

### Post by igorzwx on 2009-07-15
Could you please translate your message to 
a kind of "simplified English".
I really cannot understand whether you advice me to read Ubuntu
documentation, or, perhaps, you want to say something else.

---

### Post by lovinglinux on 2009-07-15
> **igorzwx said:**
> Could you please translate your message to 
a kind of "simplified English".
I really cannot understand whether you advice me to read Ubuntu
documentation, or, perhaps, you want to say something else.

I'm just giving you a link to a great tutorial that explains how to install codecs, plugins and media players from Medibuntu. I never had a problem after using it. 

I don't expect you to read it, I just think would be easier for you to provide the link to that tutorial when you are helping other users with multimedia issues, since you sent me the link to medibuntu.org by PM.

---

### Post by igorzwx on 2009-07-15
O.K. Now I feel absolutely confused.
I cannot understand anything.
But we can let it so.

Thanks,
Igor

---

### Post by lovinglinux on 2009-07-15
> **igorzwx said:**
> O.K. Now I feel absolutely confused.
I cannot understand anything.
But we can let it so.

Thanks,
Igor

OK. Let's talk plain English. Don't copy and paste commands from a tutorial provided by a blog somewhere on the Internet, if you don't know what they do. If you need to follow or recommend a tutorial, then it is better to use well recognized and praised tutorials from these forums, specially [from stickies](http://ubuntuforums.org/showthread.php?t=766683) or the [Tutorials & Tips](http://ubuntuforums.org/forumdisplay.php?f=100) (see approval process). Additionally, don't suggest other users to use them if you don't know the source of the OP problem, specially considering the OP said "i'm absolutely begginer". To end this discussion, which is not going anywhere, don't post cryptic messages about Chaos Theory when you are the one causing the chaos.

---

### Post by igorzwx on 2009-07-15
Thanks!
Now I understand what you want to say.

---

### Post by larsman1 on 2009-07-16
Until they have flash in the "add/remove applications" for Ubuntu 9.04, just download the Firefox.exe for Windows, and open then it up in WINE.  I do most of my browsing in 9.04 with the WINE Firefox.  Everything works great.

---

