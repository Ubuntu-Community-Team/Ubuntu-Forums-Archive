---
title: "DVD playback"
date: 2008-06-13
forum: Multimedia Software
---

### Post by Brendantb on 2008-06-13
I am having trouble following the instructions on the Movies, DVDs and Videos section of the Documentation, where it directs you to use this command to install the codes for playing encrypted DVDs: 

sudo /usr/share/doc/libdvdread3/install-css.sh


This is the error returned: 

... sudo /usr/share/doc/libdvdread3/install-css.sh
--22:17:22--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb)
           => `/tmp/dvdcss-JF5867/libdvdcss.deb'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.29.100
Connecting to [www.dtek.chalmers.se|129.16.29.100|:80](www.dtek.chalmers.se|129.16.29.100|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
22:17:22 ERROR 404: Not Found.


Can anyone point me in the right direction to resolve this problem? 

Thanks in advance,

---

### Post by mc4man on 2008-06-14
I just set up a fresh box, here's what worked well to take care of dvd/cd playback for any ver. of ubuntu. (_none of the default stuff at bottom is for kubuntu_)
 Run in order
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```


Edit: if the code to add medibuntu doesn't work (shows errors in terminal) then use an alt. method (at times you can't add it with wget)
go to system -> administration -> software sources -> third party
click add and add these two lines one at a time
```
deb http://packages.medibuntu.org/ hardy free non-free
```
```
deb-src http://packages.medibuntu.org/ hardy free non-free
```
Then exit out, clicking the reload tab when prompted
You can then try the get key line from above or don't worry about it and
 when you install the packages if an unauthenticated line comes up just choose yes

do run sudo apt-get update in any event
End Edit

Then run

```
sudo apt-get install vlc libdvdcss2 ubuntu-restricted-extras w32codecs
```
Thats it.

To add the better totem-xine player 
```
sudo apt-get install totem-xine 
``` 

(to set as a default choice see here, read thru mplayer part and see edit
[http://ubuntuforums.org/showthread.php?p=5633803#post5633803](http://ubuntuforums.org/showthread.php?p=5633803#post5633803)

edit : the libdvdread3/install-css.sh thing is somewhat outdated, much better to get your libs, codecs and players from medibuntu. In the _rare case_ the current libdvdcss2 doesn't work for your system then that's an option

Strongly suggested to add vlc as a default choice or at least set the launcher command for vlc to vlc %m or vlc %f as here (just for ubuntu as far as default - **for xubuntu go to removable drives and media and replace totem %m with vlc %m )** (note that's a space between vlc and %m
[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

---

### Post by Brendantb on 2008-06-14
Hi, 

Thanks for the reply. I'll not have access to my ubuntu box for a while, but I'll try that when I get back.

---

### Post by Pjotr123 on 2008-06-14
Here's a comprehensive multimedia how-to:
First this step:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Then this one:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

---

### Post by HullDown on 2008-06-23
Pjotr123,

Thanks for the helpful info on your web page.  It solved several issues for me, such as DVD playback, and made my recent wholesale switch from Win XP to Ubuntu much nicer.

---

### Post by rockcrawler on 2008-07-24
I am completely new to Linux and Ubuntu so please excuse any ignorance or anything I may have looked over.  I followed you guide to get my dvd player working on my HP laptop.  Everything seemed like it was going fine.  The previews plays and then I hit play on the main menu and got this error:

[IMG]http://www.nickadamsonline.net/Christophe/Screenshot-totem-1.png[/IMG]

Any help to get the dvds to play would be greatly appreciated.

---

### Post by eurohim on 2008-10-01
First, I'll point you to: [http://ubuntuforums.org/showthread.php?t=856190](http://ubuntuforums.org/showthread.php?t=856190)

And I believe this part of that link will fix your problem, because it did for me:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by keenboy on 2009-01-20
Great post, thanks.

Now why don't Canonical include these packages into a script which can be installed as an option easily by a non technical Ubuntu user?

---

### Post by sgtrock on 2009-01-20
> **keenboy said:**
> Great post, thanks.

Now why don't Canonical include these packages into a script which can be installed as an option easily by a non technical Ubuntu user?

Probably because of some truly silly legal minefields that they have to tiptoe through...

---

### Post by Bablefish on 2009-01-20
In one word... Automatrix

---

### Post by srlake314 on 2011-04-06
Ok, so now the dvd plays after ALL those sudo commands that you all had posted, however, the dvd is jumpy and in the beginning was pixelated.  Any clues?

Is there someway that I can show you a print out of my system set up?

I have Ubuntu Studio 10.10.

VLC wont run, but Movie Player will, now isnt that a hoot.  Just the opposite of what everyone says.

Sean

---

