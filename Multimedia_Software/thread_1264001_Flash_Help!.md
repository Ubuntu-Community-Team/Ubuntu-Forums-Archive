---
title: "Flash Help!"
date: 2009-09-11
forum: Multimedia Software
---

### Post by nofear3829 on 2009-09-11
[LEFT]I recently upgraded to ubuntu 9.04 and i am going through the process of installing missing plugins and various programs to get my system back in running order. When i tried to install flash via the .deb file on adobe.com, videos still wont work. I tried downloading the flash installer thingy from the synaptic, didnt work. I tried installing gnash, still nothing. To my knowledge the rest of the system including firefox, which is my primary browser btw, are up to date. I also have all of the gstreamer things to my knowledge. One other thing that i found odd . . . youtube works, but no other flash oriented anything, espn, msnbc, nothing like that and flash games wont work either. I'm not the most ubuntu savy person but i'm not quite a beginner either. Problem is driving me crazy any help would be great.:confused:
[/LEFT]

---

### Post by mjitkop on 2009-09-11
You may want to try this:

[http://ubuntuforums.org/showpost.php?p=7929700&postcount=5](http://ubuntuforums.org/showpost.php?p=7929700&postcount=5)

At the same time, you will be able to configure your Ubuntu to do other fun things. :D

---

### Post by nofear3829 on 2009-09-11
when i click on the download button it just gives me a long page with tons of command lines

---

### Post by HappyFeet on 2009-09-11
You could try what I do. First uninstall gnash and flash. Go [here]("http://get.adobe.com/flashplayer/") and download the .tar.gz flash file. Then right click it and **extract here**. Then copy the **libflashplayer.so** file and then open your home folder and do Ctrl-H. That will show you your hidden directories. Find the **.mozilla** folder and open it. Create a folder inside of there called **plugins**. Paste the **libflashplayer.so** file there. Restart firefox.

---

### Post by blur xc on 2009-09-11
> **mjitkop said:**
> You may want to try this:

[http://ubuntuforums.org/showpost.php?p=7929700&postcount=5](http://ubuntuforums.org/showpost.php?p=7929700&postcount=5)

At the same time, you will be able to configure your Ubuntu to do other fun things. :D


Is that for real?  No hidden rm -rf's hidden in there anywhere?

I've been looking for something like that forever.  IMO, that should be included in the Ubuntu install, nice big shiny icon on the dekstop.  Along side of that, an informative "readme" file, mabye in a nice pdf newsletter form.

BM

---

### Post by blur xc on 2009-09-11
> **nofear3829 said:**
> when i click on the download button it just gives me a long page with tons of command lines


Try to right-click he download button, save target as...  Then do like it says in the first lines of the script file, to give it executable permissions.

That's actually a pretty impressive looking script.  It'd make life easy for a lot of new users to get everything working in one shot.

BM

---

### Post by mjitkop on 2009-09-13
Sorry for the lack of information but I posted the link when I was at work and didn't have much time.

As blur xc said, right click on the link to download the script file (all text) and save it on your desktop (for example). Once the file is downloaded, do a right click on it and choose the option "Properties." Then click on the "Permissions" tab and check the little box in front of "Allow executing file as program." 

Finally, open a terminal window and type the command:

```
~/Desktop/perfectbuntu
```(assuming you saved the file on your desktop)

Enjoy! :D

P.S. There are no hidden \rm -rf commands anywhere. I checked line by line to make sure too. ;)

---

### Post by blur xc on 2009-09-13
> **mjitkop said:**
> Sorry for the lack of information but I posted the link when I was at work and didn't have much time.

As blur xc said, right click on the link to download the script file (all text) and save it on your desktop (for example). Once the file is downloaded, do a right click on it and choose the option "Properties." Then click on the "Permissions" tab and check the little box in front of "Allow executing file as program." 

Finally, open a terminal window and type the command:

```
~/Desktop/perfectbuntu
```(assuming you saved the file on your desktop)

Enjoy! :D

P.S. There are no hidden \rm -rf commands anywhere. I checked line by line to make sure too. ;)

I've done a lot of those setup steps manually over the months of running Ubuntu.  Would there be any harm from running it, and maybe having it install something I might have missed, w/o undoing anything I've already configured?

BM

---

### Post by mjitkop on 2009-09-14
That's a very good question, blur xc. 

I do not know how Synaptic handles repeat installation requests. Maybe it will just give an error message that a package is already installed and will not install it again. Unless maybe there is an update to a package. 

I do not have a definite answer. :(

Is there anybody else who can answer this question for sure? :confused:

---

