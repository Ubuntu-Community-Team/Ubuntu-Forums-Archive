---
title: "dvd burning impossible????"
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by curtk69 on 2007-04-26
hey dudes, i am totally fed up with microsoft and therefor am trying to migrate to ubuntu and will not be able to do so unless i can do almost everything in linux/ubuntu as i can under windows xp

today i am having trouble burning copies of my own dvds
i am sure they are copyrighted as are all dvds but whatever, i should be able to make a single copy of my own dvd. i try to be careful and not scratch them or lose them but over the years several have either gotten too scratched or completely lost and that problem is 100 times worse with music cds bouncing around my car..

i have autmatix and all download necessary i think anyways? at least i can play wmv  files i get in email now.

i have tried BRASERO and GNOMEBAKER  and DVD RIP.

in gnomebaker i cant seem to copy and burn the disc . the copy part seems to work but burning fails immediately upon inserting blank discs.
i did manage to make data copies but that way only fit about 4/5 ths of the movie on one disc. [4.3gb]
besides buying bigger discs isnt there a better way to copy my dvds?

in brasero i try making a copy with copy dvd and make image but i immediately get the error that says my home folder hasnt got enuff space?
when i installed ubuntu on my 200 gig hdd i left windows xp with only 50 gigs so 150 should be available to ubuntu and i can confirm there is about 138 or so left. 
so whats the problem?
i have also tried brasero making a direct copy but i only have one dvd drive and it gives me some error saying the disc isnt writable thinking i am gonna copy and burn on the same disc? doesnt it have the capqability to copy in a temp folder then after a blank disc is inserted record?

dvd rip seems to rip ok but then what do i do with that file? how do i get it to a dvd?

K9COPY says dvd isnt open. what does that mean?
DVD SHRINK opens a shell/console and says press any key to start but nothing happens.?

---

### Post by Sheik Yerbouti on 2007-04-26
Your best bet is k9copy and k3b combo it is in the repositories (apt-get install k9copy k3b)

After you install k9copy launch it and go to the settings menu >> configure k9copy >> dvd and select burn with k3b and autoburn.

 select the DVD drive with the source DVD in it under input device and select the destination DVD burner under output device and then click the folder icon  on the toolbar and blamo it will read the source DVD. And then show you a tree structure with the titleset selection and audio selection, etc. Select the video titles, audio track, and subtitles you want to rip etc.. Then click the DVD icon to start the rip and burn. Easy as pie it will auto shrink to fit on whatever DVD size you configure under settings >> configure k9copy >> DVD >> DVD size

---

### Post by curtk69 on 2007-04-27
ok thanks dude, it looks like thats one less problem for me solved but i will let you know if it still isnt working
pretty soon i will be able to say linux/ubuntu kicks ***

one last thing, how do i know which files or folders or titles sets etc to inc if i just want the movie to play instantly with no menus or previews or audio selections maybe i might wanna inc scene selctions but thats it?
on my first try i just inc all of them but its taking 45 minutes just to copy let alone burn?

---

### Post by Sheik Yerbouti on 2007-04-27
So the easiest way to pick just the main feature on the DVD is just by size. The main feature will be by far the biggest titleset like several gigabytes just pick that and you should be good. Also there is a little check box on the lower right hand side to include menus this would only matter if you were ripping the whole disk including menus but wanted to turn the menus off to launch straight in to the main feature.

---

### Post by curtk69 on 2007-04-27
ok it worked on my first try but the second movie i tried got some error and quit before copying?
i get an error saying    An error occured while running DVDAuthor:  CANNOT PARSE SUBPICTURE OPTION  'Ã¿Ã¿' on track 0 

I have a screen shot,  if need be give me an email to send it to?

---

### Post by Sheik Yerbouti on 2007-04-28
Yeah not sure about that error might google it. But I have noticed that it is a good idea to quit k9copy and restart in between burning multiple disks. I am not sure but I think it has something to do with k3b having the DVD burner device open at the end of the burn. I just close k3b and restart k9copy between burns and I have not gotten any errors or burned any coasters good luck.

---

### Post by GMachine_24 on 2007-04-28
hi:

this program will rip and copy the main title from your dvd. it is easy to use, fast and simple to set up. you might need to install a couple other packages but you get a notice about them if they're missing and you can just do a 'sudo apt-get install <packagename>' and everything will be cool.

follow the link....

[http://dvdshrink.sourceforge.net/](http://dvdshrink.sourceforge.net/)

Please note: this is NOT the Windows DVDShrink running under Wine. This is a pure Linux program.

---

### Post by curtk69 on 2007-04-28
heyGMachine_24 , i already stated at the end of my original post how dvd shrink DOESNT  work either. when i hit start copying it opens a shell /konsole window that says hit any key, and when i hit any key nothing happens?????wtf?
is this normal or what am i doing wrong?
btw dvd shrink also pops up  a window saying rip is in progress but there seems to be no activity or working sounds coming from the burner nor is there a progress bar showing it actually started and is progressing? any ideas?

---

### Post by curtk69 on 2007-04-28
sheik, i dont think it has to do with two consecutive burns since they were a day  apart?
i am trying a 3rd movie just for practice to see what happens

---

### Post by GMachine_24 on 2007-04-28
Hi:

As I wrote in my private message to you, hitting "any key" after starting dvdshrink will not work for some reason - you need to hit 'enter.' At least that works for me.

Also, re: dvd::rip, there are dependency problems which have not been resolved. I used dvd::rip for awhile to create ..mp4 copies of DVDs but could never get it to copy DVD-to-DVD - and I'm not even sure if this is possible so I can't say anything about this.

--GM

---

### Post by curtk69 on 2007-04-28
ok i guess k9 copy and k3 will still work on other dvds and i managed to get dvd shrink to work by opening a shell like you and theeeen hitting any key AND  pressing enter. so it recorded the stubborn movie that kept getting errors with k9 copy.
is it possible one little scratch would make a burn fail completely?
thanks guys

---

### Post by stchman on 2007-05-08
> **curtk69 said:**
> hey dudes, i am totally fed up with microsoft and therefor am trying to migrate to ubuntu and will not be able to do so unless i can do almost everything in linux/ubuntu as i can under windows xp

today i am having trouble burning copies of my own dvds
i am sure they are copyrighted as are all dvds but whatever, i should be able to make a single copy of my own dvd. i try to be careful and not scratch them or lose them but over the years several have either gotten too scratched or completely lost and that problem is 100 times worse with music cds bouncing around my car..

i have autmatix and all download necessary i think anyways? at least i can play wmv  files i get in email now.

i have tried BRASERO and GNOMEBAKER  and DVD RIP.

in gnomebaker i cant seem to copy and burn the disc . the copy part seems to work but burning fails immediately upon inserting blank discs.
i did manage to make data copies but that way only fit about 4/5 ths of the movie on one disc. [4.3gb]
besides buying bigger discs isnt there a better way to copy my dvds?

in brasero i try making a copy with copy dvd and make image but i immediately get the error that says my home folder hasnt got enuff space?
when i installed ubuntu on my 200 gig hdd i left windows xp with only 50 gigs so 150 should be available to ubuntu and i can confirm there is about 138 or so left. 
so whats the problem?
i have also tried brasero making a direct copy but i only have one dvd drive and it gives me some error saying the disc isnt writable thinking i am gonna copy and burn on the same disc? doesnt it have the capqability to copy in a temp folder then after a blank disc is inserted record?

dvd rip seems to rip ok but then what do i do with that file? how do i get it to a dvd?

K9COPY says dvd isnt open. what does that mean?
DVD SHRINK opens a shell/console and says press any key to start but nothing happens.?

I have a procedure to download the codecs and configure k9copy to rip your DVDs to a .iso file.  You will need to install the medibuntu codecs and the CSS decoder to play encrypted DVDs.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

It works for many DVDs, but some newer DVDs it won't work.

---

### Post by yogo on 2007-07-29
> **Sheik Yerbouti said:**
> Your best bet is k9copy and k3b combo it is in the repositories (apt-get install k9copy k3b)

After you install k9copy launch it and go to the settings menu >> configure k9copy >> dvd and select burn with k3b and autoburn.

 select the DVD drive with the source DVD in it under input device and select the destination DVD burner under output device and then click the folder icon  on the toolbar and blamo it will read the source DVD. And then show you a tree structure with the titleset selection and audio selection, etc. Select the video titles, audio track, and subtitles you want to rip etc.. Then click the DVD icon to start the rip and burn. Easy as pie it will auto shrink to fit on whatever DVD size you configure under settings >> configure k9copy >> DVD >> DVD size



Great post, I am almost there for getting K9copy to work.

Not sure what it wants in the last step (Then click the DVD icon ) It asks me for a location, I assume this is my problem, because I was trying to give the .iso a file name but it errors out immediately. What should I enter in the Location window?

TIA

---

### Post by Gotblade on 2008-02-20
K3b says my dvd+r discs are empty but not writable even after downgrading dvd+rw-tools.
The weirdness is that they record just fine after the downgrade.:-k

---

