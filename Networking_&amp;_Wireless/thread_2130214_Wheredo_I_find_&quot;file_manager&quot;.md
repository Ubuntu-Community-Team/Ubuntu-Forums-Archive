---
title: "Wheredo I find &quot;file manager&quot;"
date: 2013-03-28
forum: Networking &amp; Wireless
---

### Post by ejdiii on 2013-03-28
I was given a DELL notebook computer from my son with UBUNTU some time back and things where fine,  but now I cannot get on line. either wireless or wired.   I use to just turn it on, and it would make the wireless connection from my linksys.  I have 5 other computers in the household, but this one is the the only one with  UBUNTU. (thankfully, it keeps everyone off of it since it's not there  normal OS). nothing has changed in my internet provider, service, computers, wired or wireless etc.  I have tried resetting the linksys, etc. but all my screen says is "wireless service is ready, select internet service" or something like that.  But I can't find where to do that? I went to the HELP option and it says to go to "file manager" and select the internet provider.  I have looked in every file from the main menu drop down, an no file is called  "File Manager" , I have also tried all the NEtwork,internet service options on that main menu, but they just say I need name, and all kinds of  server specific info to set up a network.  I just want to get back on line, just as I did a few days ago, an have been for the past year. what happened?  could something have gotten hidden or deleted?  possibly from updates ubuntu suggest I load  or have loaded? (nothing in trash can).   I'm not a very tech savvy user, but been a  user since 1980  (Sperry Univac 1050-II) so I,m not totally dim on them.  I have tried searching everywhere, and trying anything that even sounds possible, my son moved away and said to ask on this forum since he would have to "SEE"  my computer to figure it out.

---

### Post by wojox on 2013-03-28
My Dell has a switch to toggle the wireless on and off. Is yours on? Can you connect wired with a cable?

---

### Post by Bashing-om on 2013-03-28
ejdiii; Hi ! Welcome to the forum.

In oder to assist you concisely, what version of ubuntu are you using, and do you use other than the default desk top ?

Things change version to version.[INDENT=2]
ubuntu, All for 1 and one for all
[/INDENT]

---

### Post by pfeiffep on 2013-03-28
From a terminal window (Ctrl-Alt-T) type > nautilus  which is the graphical file manager in current Ubuntu
Since I'm new to Ubuntu and Linux I'm not entirely certain how long nautilus has bee the file manager.

in the same window type > uname -a  this will provide some basic information about your system

Post back with results for more aid if needed

---

### Post by Hadaka on 2013-03-28
hi, since you are a sperry dude you should have
no trouble with this command. Open a terminal
ctrl/alt/t   then enter the following command.
```
lspci -n | egrep '0200|0280' | awk '{print$2,$3}' 
```
what this does is show the pcid..driver info for the wired and wireless
0200-wired  0280-wireless
you will see 2 lines of code.. both will likely have a [14e4:XXXX]
please post back the results in this format.
0200 14e4:the number
0280 14e4:the number
*Note..the 0200 wired may not have a 14e4:number
but...i have a feeling it will.
also..if it's saying wireless connections found...
click the icon next to the envelope..upper right corner..
that should show wireless connections...choose yours
and see if it connects.
thanks.

---

### Post by ejdiii on 2013-03-30
Thanx for the replies, but I have found out that the "Fn" key, along with 6 others , does not work, this being the reason I have a plug in key board I was told by my son, who pawned it off on me, I thought the reason for the standard key board was because I have a hard time with the tiny and flat netbook keys. .  So, I guess I either have to locate a keyboard with an Fn , or scrap the old netbook.

---

