---
title: "How to install Lxsplit?"
date: 2007-01-06
forum: Multimedia &amp; Video
---

### Post by Laotse on 2007-01-06
Hi, I don't know how to install Lxsplit. I have read "readme.txt" and i can't install Lxsplit. Please, help me. Thanks.

---

### Post by Spano on 2007-01-06
I built these .deb packages with checkinstall. 
Download to your home directory and from the terminal install lxsplit with
```
sudo dpkg -i  /home/your_user_name/lxsplit_0.1.1-1_i386.deb
```
if you want the graphical interface too, do
```
sudo dpkg -i  /home/your_user_name/gtksplit_20060827-1_i386.deb
```

Run it with the command
```
gtklxsplit
```
hjsplit in linux

---

### Post by Laotse on 2007-01-07
Thank you very much, it's working now :D

---

### Post by Spano on 2007-01-07
Your welcome - happy to help.

---

### Post by H.E. Pennypacker on 2007-01-27
> **Spano said:**
> Your welcome - happy to help.

Spano, thanks!

---

### Post by ricardisimo on 2007-02-28
Many thanks Spano. I'd added a menu item, just using the command line, but I was wondering if there is an "official" icon for it as well. Also, I tried <locate gtklxsplit> to find where it installed, but no dice. Do you know where it is in file system or elsewhere? thanks.

---

### Post by Spano on 2007-03-19
The .deb installs gtklxsplit and lxsplit to /usr/local/bin 
No icon I'm aware of.  In Windows you run the program from the file you installed it in - no menu entry, the icon in the file is a simple black check mark.

---

### Post by bluehue on 2007-04-25
I downloaded the .deb packages to my ~/Desktop directory and double-clicked them to install (nothing done via terminal). I checked and can confirm that lxsplit and gtklxsplit are in my /usr/local/bin directory. However, I get the following error when I try to run gtklxsplit:
```
spiral@spiral-desktop:/usr/local/bin$ gtklxsplit
gtklxsplit: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```
Any ideas what the problem may be? :confused:

I'd also be interested if someone could show me how to add a menu item for gtklxsplit through the command line as someone had done so in this thread.

---

### Post by bluehue on 2007-04-25
Well, that was simple enough. To solve the above problem install the following from Synaptic Package Manager:

libgtk1.2
libgtk1.2-common

I then created a link icon on my desktop for easy access to gtklxsplit.

---

### Post by indrajeetak on 2007-05-03
> **Spano said:**
> I built these .deb packages with checkinstall......

Thanks a lot Spano......Your deb packages were a a lot helpful. I was going crazy getting errors trying to install lxsplit and HJSplit at the command line.

---

### Post by jabba1 on 2007-06-11
Thanks dude :) I have problems with your commend to grafic interface but command line works :)

---

### Post by Spano on 2007-06-11
> Thanks dude  I have problems with your commend to grafic interface but command line works 
Your welcome.
Are you having a problem with the gui install command or the gui run command?

---

### Post by AHumanUser on 2007-07-26
> **Spano said:**
> I built these .deb packages ...
Awesome, Spano, and thank you.

I'm running out of reasons to keep faulty Windows XP on my dual-boot-system.

GNU/Linux - and especially Ubuntu - really means power to the people!

Best wishes,
A Human User

---

### Post by flakolol on 2007-08-19
gracias

---

### Post by richharding1 on 2007-09-28
Thanks for the advice.  I have been trying to migrate from Win  XP to Linux and I have fallen in love with Ubuntu (tried Fedora first and liked it but Ubuntu had the drivers in place for my wireless network card, so much easier!).  I am trying out various archiving and splitting programs and HJSplit and Lxsplit seem so easy, but until now had trouble installing them.  Thanks a lot.  I would also like to try using Rar for Linux, downloaded it but had trouble installing that one, too.  Any advice would be appreciated.  In any case, Linux is so much more fun than windoze, it is a real community!  So much fun to see what's out there in open source software, I'm even learning a bit about editing scripts and picking up a little programming knowledge as well.  Linux lets you look under the hood of the OS and really get acquainted with what's going on inside the computer.  Thanks again from a newbie!

---

### Post by windstarmb on 2007-10-26
> **Spano said:**
> I built these .deb packages with checkinstall. 
Download to your home directory and from the terminal install lxsplit with
```
sudo dpkg -i  /home/your_user_name/lxsplit_0.1.1-1_i386.deb
```
if you want the graphical interface too, do
```
sudo dpkg -i  /home/your_user_name/gtksplit_20060827-1_i386.deb
```

Run it with the command
```
gtklxsplit
```
hjsplit in linux

Spano, Thank you for your time and effort and for sharing it. I'm still a newbie to Linux and it's guys like you that figure this stuff out and then take the time to share it with those of us trying to learn, that makes all the difference.
Read you later,

8)windstarmb
            "If you build it, they will come"

---

### Post by rahagi on 2008-02-20
> **Spano said:**
> I built these .deb packages with checkinstall. 
Download to your home directory and from the terminal install lxsplit with
```
sudo dpkg -i  /home/your_user_name/lxsplit_0.1.1-1_i386.deb
```
if you want the graphical interface too, do
```
sudo dpkg -i  /home/your_user_name/gtksplit_20060827-1_i386.deb
```

Run it with the command
```
gtklxsplit
```
hjsplit in linux

I had try to install HJSplit at my Ubuntu. but when I try to run it. there are no progress.

I will try your deb package when i arrive at my home.

Thanks for your effort
Regards
[http://bukhory.web.id](http://bukhory.web.id)
:lolflag:

---

### Post by jvaudrey on 2008-04-05
Thank you for the deb files i found wine and HJSplit were locking up UBUNTU where only a reisub or hard reboot would get it working again

Using these everything is fine again!

---

### Post by dln1969 on 2008-05-09
HELP,
I am NEW to Ubuntu from windows vista. I would like to install hjsplit or Lxsplit so I can join video clips..
How do I do it and simple.
I am useing 8.04 ubuntu .. 

I have read the other things on this but just dont understand it .
please help if you can ..
[email]dln1969@cox.net[/email]

I really like this OS and when I go back to vista I hate it ..
would like to just use on system and not have to move files ..
thanks
David
:confused:

---

