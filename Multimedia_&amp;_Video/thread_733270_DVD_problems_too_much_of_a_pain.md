---
title: "DVD problems too much of a pain"
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by Sturch001 on 2008-03-23
It has been a week since I installed Ubuntu 7.10. And in that week I have gotten webpages to load, cds to play music and everything else I needed to get done working. Only thing I haven't gotten to work is DVD playing.

Tried installing gxine and it didn't work. 

sudo apt-get install gxine 
won't work for me

Tried Kaffeine

Same problem as with gxine

Keeps saying I need to install Libxine1 before I can install libxine1 

I installed the restricted stuff in synaptic program manager

Still nothing. 

Rebooted PC 
still nothing

Ran 

sudo atitude updates

Hangs up at [www.getautomatix.com](www.getautomatix.com) 

I think I'm going to go running Happily back to windows while I still have hair. 

Thank you for all your help, but Ubuntu is just too much of a pain playing DVDs for me to justify spending a week trying to get it to work.

---

### Post by wolfen69 on 2008-03-23
relax. here you go. copy and paste into terminal the following.
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
then
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
then
```
sudo apt-get install libdvdcss2
```
enjoy your movie

---

### Post by steveneddy on 2008-03-23
he was given the answer in [this thread]("http://ubuntuforums.org/showthread.php?t=730467").

---

### Post by Sturch001 on 2008-03-23
When I try to install W32Codecs it gives an error message and wont install

When I try to install the program the error gives me it gives me a new error.

so on and so on...

When I cut and paste the code in the above post. I still can't install a movie player after everything. 

And I keep getting libxine1 errors

---

### Post by steveneddy on 2008-03-23
> **Sturch001 said:**
> When I try to install W32Codecs it gives an error message and wont install

When I try to install the program the error gives me it gives me a new error.

so on and so on...

When I cut and paste the code in the above post. I still can't install a movie player after everything. 

And I keep getting libxine1 errors

Did you enable the repo?

Are you doing these in order?

Or are you trying to jump to the part that you think you need and it isn't working?

You must enable the correct repo for the correct libs and codecs to be installed properly.

Follow wolfrn69's advice, in order, from top to bottom, and see if you get favorable results.

look [here]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories")

and [here]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability")

These are in the[ ubuntu guide]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy"), please read the guide.

---

### Post by fela on 2008-03-23
libxine not installing seems to be a different problem altogether, but there is a movie player included in Ubuntu by default that plays DVDs (called 'Movie Player'). Put a DVD in and it should autoplay once the disc has loaded (if not, look in System > preferences > prefered apps and in the dvd playing select 'totem')

---

### Post by wolfen69 on 2008-03-23
to enable repos, go to system>admin>software sources. then make sure all boxes are checked. close and reload.

---

### Post by fela on 2008-03-23
I just hate it when people can't be bothered to get off their *** to sort a problem out in Linux, and go running back to windows. It really winds me up that people can be so lazy - quick - we need a rant section! :lolflag:

---

### Post by Sturch001 on 2008-03-23
Ok

Reloaded Ubuntu

Applied Updates

restarted

Used above commands
and checked boxes in synapic

Kaffeine installed no problem

Still cant watch DVDs Its saying

Source cant be read maybe you don't have enough rights

any ideas?

---

### Post by Sturch001 on 2008-03-23
YAHOO!!!

IT WORKS!

Thank you all! 

(Still prefer Windows)

All I had to do to fix the new problem was point Kaffeine to /dev/cdrom0

Thank you every one=D>:popcorn:

---

