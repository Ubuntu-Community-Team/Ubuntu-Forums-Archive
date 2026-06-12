---
title: "Using get-iplayer to download BBC radio shows"
date: 2013-02-05
forum: Multimedia Software
---

### Post by dreamkatcha on 2013-02-05
Hi,

To download shows I currently go to the home page to retrieve the latest pid, type my command into terminal and then add this unique reference to the end like this:-

get-iplayer --type=radio --get --aactomp3 --pid=b01qdrmp

What I'd like to know is, can I save a script that would when executed automatically check the web site ([this is the one]("http://www.bbc.co.uk/programmes/b006wr3p/broadcasts") I'm most interested in), determine the pid of the latest show and start downloading it? I've had a look at the list of modifiers but it's endless and I'm lost.

---

### Post by coldraven on 2013-02-05
get_iplayer seems to have a PVR (**personal video recorder** )function but I have only just tried it. I followed the instructions here:
[http://linuxcentre.net/getiplayer/documentation#PVR%20Usage]("http://linuxcentre.net/getiplayer/documentation#PVR%20Usage")

and made a PVR file like this
```
get_iplayer --pvr-add=Jeremy_Vine --type=radio "Jeremy Vine"
```Then you need to run the PVR, I just did it manually but it says to make a cron job to do it automatically.

```
get_iplayer --pvr
```Don't ask me how to use cron because I have never tried it. I'm sure it is fairly simple. :confused:
In theory it should record any new shows in the series if that is what you're after

See ```
man cron
```good luck ;)

Edit: I read that wrong, it should be crond not cron.
I did a search and the best result so far is here:
[http://www.pantz.org/software/cron/croninfo.html](http://www.pantz.org/software/cron/croninfo.html)

It seems that if you run the command "crontab -e" you can edit your crontab file and add the "get_player --pvr" comand to run at whatever time you like.

---

### Post by dreamkatcha on 2013-02-06
Ah, brilliant. I reckon I can cope with that. Not having to go to the web site, finding the right page and copying and pasting the pid every day is a nice time saver alone. I'll create a PVR for now and then look into automating the process entirely later.

Thanks very much for your help. :)

---

### Post by shantiq on 2013-02-06
not entirely sure but i shall run this to see if it works;not used crontab for a while ...



create   a file     yourname.cron   

enter  ```
0 20 * * 1-5  get_iplayer --pvr 
```  and save in home folder  [**Make sure! **you place your cursor at end of line and press enter before you save]

  see info here  [http://www.scrounge.org/linux/cron.html](http://www.scrounge.org/linux/cron.html)      

**in terminal**

```
crontab yourname.cron
```    will install new command

crontab -l will show it
crontab -r will cancel it

to modify  command or settings open with gedit yourname.cron
then run ```
crontab yourname.cron
```  to change that


[at 8 oclock every day  monday to friday  give the Beeb time to get program out --pvr will be run  and therefore new programs downloaded; i take it get-iplayer will see the ones already downloaded and only take the missing one[s]]   i hope  ::]]  as i say not a 100% sure but trying it as interested to do same for another radio program

---

### Post by coldraven on 2013-02-08
Thanks shantiq!
I had looked at several sites that all told me the time format but none had mentioned actually creating the text file yourname.cron.
That is so easy I shall start doing some cron stuff just for the hell of it :)

P.S. The Africa series is amazing

---

### Post by shantiq on 2013-02-08
well coldraven thanx for pvr i had never even seen it there...

i too shall be trying things out see how it all works...

PS [edit] :   ok first night at 8:00  it took the 4 which were there;  next night at 8:00 it "knew"  to take just the new one   ... so gravity works  ::]]

---

### Post by dreamkatcha on 2013-02-08
The level of support on this forum is second to none! Thanks guys. :) 

Once this is setup it's a much nicer solution than any GUI-based software on any system... and of course you feel really smug because you're learning new skills at the same time.

---

