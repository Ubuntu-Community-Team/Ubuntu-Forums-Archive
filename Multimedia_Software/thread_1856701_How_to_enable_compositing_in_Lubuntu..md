---
title: "How to enable compositing in Lubuntu."
date: 2011-10-08
forum: Multimedia Software
---

### Post by mystika1 on 2011-10-08
Hi,
I have just installed Lubuntu and I am really suprised at the speed difference with my machine. I have installed Docky and I am now getting a message that I need to enable compositing. I have searched and can't find any instructions on how to do that in lubuntu...everything I have found is for either KDE or Gnome. Please advise.

Thanks,

Penny

---

### Post by kerry_s on 2011-10-08
Install xcompmgr using synaptic
Then
Add xcompmgr -n
To the startup

Press alt+f2
Type gksudo leafpad /etc/xdg/lxsession/Lubuntu/autostart

---

### Post by mystika1 on 2011-10-08
Hi,
Thanks for the reply. I followed your directions but I am still getting a message from docky that I need to enable compositing for docky to work correctly. Is there something else I should try?

Thanks

Penny

---

### Post by kerry_s on 2011-10-09
Did you put the "@" at the front of the command & did you log out & back in?

---

### Post by WasMeHere on 2011-10-09
> **kerry_s said:**
> Did you put the "@" at the front of the command & did you log out & back in?
Sorry, I have to ask a stupid question: Why put "@" at the front of the command?
Olle

---

### Post by mystika1 on 2011-10-09
Hi,
I did put the @ and I restarted my computer. 

This is what I put...
@xcompmgr -n

Thanks,

Penny

---

### Post by mystika1 on 2011-10-09
bump

---

### Post by beew on 2011-10-09
I got composting by installing Compiz. There may be other ways to do it, didn't know about xcompmgr.

Lubuntu is fast but many things don't work apparently. Since there aren't many threads about Lubuntu, if you don't mind me asking, have you tried playing a cd or dvd? In my Lubuntu install that only works with command line.

---

### Post by 4Orbs on 2011-10-09
suggestion: Try putting the command xcompmgr -n in your .config/openbox folder by adding it to the autostart.sh file as below and save, reboot.
```
xcompmgr -n &
```

---

### Post by mystika1 on 2011-10-09
> **beew said:**
>  Since there aren't many threads about Lubuntu, if you don't mind me asking, have you tried playing a cd or dvd? In my Lubuntu install that only works with command line.


I watched a movie last night in Lubuntu with no problems. It played really well.

Penny

---

### Post by mystika1 on 2011-10-10
> **beew said:**
> 

Lubuntu is fast but many things don't work apparently. Since there aren't many threads about Lubuntu, if you don't mind me asking, have you tried playing a cd or dvd? In my Lubuntu install that only works with command line.

I installed Lubuntu using the daily build images for 11.10 and it works great. Maybe something happened during the install that caused your problem. 

I still have not been able to get xcompmgr working but I was only trying to use it for docky. I have discovered Cairo-dock works without compositing and tried that instead. It is great. My machine ran Kubuntu and Ubuntu Unity well but I am glad that I tried Lubuntu because I love the speed with which my programs load.

Penny

---

### Post by amjjawad on 2011-10-11
Hi there and thanks for using Lubuntu. 
I don't really have to write much except it ROCKS, period.

People/Users usually forget one simple fact which is: Lubuntu is designed to work on Old Machines and breath new life into them. Also, it's designed to work on Mini notebook, mobile devices, etc. It's not like Ubuntu and will never be. LXDE, the native Desktop Environment is not as fancy as Unity, GNOME or KDE but as of today, I have no problem with it at all. All what I need, work perfectly.

What could be better than super fast machine with 2 seconds to shutdown and less than 1 min to start up? 

For me, I don't care at all with anything like Docky, Compiz (which works on Lubuntu/LXDE by the way) or stuff like that. However, I installed Cairo-Dock the other day while I was helping my Lubuntu Team to test 11.10 and it worked perfectly.

I installed 11.10 (for testing purposes) on 242MB RAM and the Live Session worked and after the installation it worked without any issue. Yes, definitely it will be slow but neither Xubuntu, Ubuntu nor Kubuntu is capable of running on such low RAM.

Above all, I have installed 11 months ago, Linux Mint 9 LXDE on 12 years old laptop with 64MB RAM and 366MHz P2 CPU and ... it worked MUCH faster than XP or even Win98. IMHO, nothing can beat LXDE.

Lubuntu is amazing. I'm not writing that because I'm one of its team, but I'm writing that as one of its USERS :)

P.S.
I suggest to use Cairo-Dock instead of Docky but that's just a suggestion NOT a solution :)

---

### Post by mystika1 on 2011-10-11
> **amjjawad said:**
> 

P.S.
I suggest to use Cairo-Dock instead of Docky but that's just a suggestion NOT a solution :)

When I couldn't get xcompmgr to work I did a yahoo search for a dock that doesn't require compositing and Cairo-dock came up. I would have used that first if I would have known....:)

It works great. 

Penny

---

### Post by amjjawad on 2011-10-11
> **mystika1 said:**
> When I couldn't get xcompmgr to work I did a yahoo search for a dock that doesn't require compositing and Cairo-dock came up. I would have used that first if I would have known....:)

It works great. 

Penny

That's why it called "Search Engine" ;)

All the best and enjoy the crazy speed :D

---

### Post by mystika1 on 2011-10-12
I am ok without compositing but... I get the following message in the terminal when I type in xcompmgr:

> Another composite manager is already running

The only thing I have done is place xcompmgr in my autostart file. What other composite mgr could be running? Any clues as to why this message comes up? I thought that LXDE had no composite manager.

Thanks,

Penny

---

### Post by amjjawad on 2011-10-12
> **mystika1 said:**
> I am ok without compositing but... I get the following message in the terminal when I type in xcompmgr:



The only thing I have done is place xcompmgr in my autostart file. What other composite mgr could be running? Any clues as to why this message comes up? I thought that LXDE had no composite manager.

Thanks,

Penny

Very interesting. I must do some search :)

Please remind me after two days in case I didn't get back to you :)

Edit:
Wait, you said it's on your auto-start app, right? perhaps that's why?

---

### Post by mystika1 on 2011-10-12
> **amjjawad said:**
> 

Edit:
Wait, you said it's on your auto-start app, right? perhaps that's why?

Hi,
I followed the directions given to me in this same thread and put @xcompmgr -n & here: 
gksudo leafpad /etc/xdg/lxsession/Lubuntu/autostart

Should I have put it somewhere else?

I am not a noob but...:)I am not an expert either so please correct me if I placed that incorrectly.

thanks,

Penny

---

### Post by amjjawad on 2011-10-12
> **mystika1 said:**
> Hi,
I followed the directions given to me in this same thread and put @xcompmgr -n & here: 
gksudo leafpad /etc/xdg/lxsession/Lubuntu/autostart

Should I have put it somewhere else?

I am not a noob but...:)I am not an expert either so please correct me if I placed that incorrectly.

thanks,

Penny

```
 gksudo leafpad /etc/xdg/lxsession/Lubuntu/autostart
```
That's the auto start location, yes. But I'm not sure what to put there. I mean I'm not sure whether you need to enter this: ```
@xcompmgr -n
``` or something else?!

---

### Post by mystika1 on 2011-10-12
Hi,
I want to thank everyone for the help provided. I have discovered an old thread that has a small GUI for xcompmgr that solved the issue. 
The following dependency must be installed first...
> sudo apt-get install libgtkmm-2.4-1c2

I installed the GUI program
[http://ubuntuforums.org/showpost.php?p=555510&postcount=170](http://ubuntuforums.org/showpost.php?p=555510&postcount=170)

 and went in lxterminal and typed > gcompmgr and I was able to configure compositing. It is a great tool. Even though I could have quickly installed Compiz to take care of compositing.... I really wanted to keep my machine running bloat free. 

The original thread that lead me to the solution is here...
[http://ubuntuforums.org/showthread.php?t=75527](http://ubuntuforums.org/showthread.php?t=75527) to give credit where credit is due. I just condensed it to make a long story short for anyone else who uses Lubuntu that would like a little bit of bling without having to make big changes or having to install more than they may need.(compiz)

I like speed....Lubuntu rocks!

Penny

---

### Post by amjjawad on 2011-10-13
Hi Penny,

Looks like we (me and you) are going to write a new guide/howto for that ;)

I'm very glad you managed to fix it and it's really good to know that Lubuntu is very much capable of anything, not like some may think for a moment :)
It's lightweight but ROCK.

If you don't have another question, please mark this as SOLVED.
Also, I'd suggest to write on LXDE Forum a guide or howto which explains all the steps one needs to follow to enable that in Lubuntu.
I'm planning to have a sub-forum for Lubuntu on LXDE Forum but must talk to my team first. I'm a moderator yes but don't have Full-Access yet.

---

### Post by MobileTechie on 2011-10-18
Thanks for this Penny. I've searched all over for a compositing solution for Lubuntu and been down many blind alleys. At last something that works.

---

### Post by mystika1 on 2011-12-21
I found the 64bit version here
[http://ubuntuforums.org/attachment.php?attachmentid=4464&d=1134479263](http://ubuntuforums.org/attachment.php?attachmentid=4464&d=1134479263)

---

### Post by MorrisseyJ on 2012-01-17
I have just installed Lubuntu on my old machine and its a really wonderful distribution. 

Thanks for all the info here, but i am still stuck.

I have got gcompmgr running, but the preferences are beyond me. What settings do i put in place to get composting to work on my AWN Dock?

Thanks.

---

### Post by fkurniaaziz on 2012-05-01
type like this
@usr/bin/xcompmgr
this work for me

---

### Post by killmess on 2012-06-20
Thanks for 64 bits version! ;)

---

