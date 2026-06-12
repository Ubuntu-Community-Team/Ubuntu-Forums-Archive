---
title: "Cant get ati mobile x700 to work. ( struggling second day in a row)"
date: 2007-06-02
forum: Multimedia &amp; Video
---

### Post by haplo_09 on 2007-06-02
Hello everybody. for 2 days I have been trying to get my ati x700 mobile to work with ubuntu. I tried ubuntu 7.04, kubuntu 7.04 6.10. Right now I made a clean install of kubuntu, performed all upgrades, Enabled restricted modules and was performing manual ati driver install following this guide. 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=%28binary%29#head-796aa4d6d0477c8ed722acef1878cc5626855ae3-2](https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=%28binary%29#head-796aa4d6d0477c8ed722acef1878cc5626855ae3-2) 

Everthing was going smoth till point when I had to enter 
sudo aticonfig --initial. 

and I was getting following message. Which confused me.   
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11 

Is there any way to solve this problem. 
thanks

---

### Post by sloggerkhan on 2007-06-02
HI. I have ATI 700 mobility.

With feisty it is easy.
Off of a fresh install, click the check mark next to ATI driver in the restricted drivers manager. Hit OK. When you are done, reboot.

Otherwise you are using the open source ATI driver.


PS: more complicated instructions are for installing the NEWEST fglrx driver, which has known issues, are what you get from the link you gave.

---

### Post by haplo_09 on 2007-06-02
thanks but I tried all possibl fiesty insallations and it failed to work.  
Normal cd failed to laod. 
whil alternate cd install was giving blank screen all time. 
Even after I reconfigured xorg server. 

Any suggestions how to completly remove cuurent ati driver files, so I can try to make clean driver reinstall.? I am just so tired of installing and reinstalling linux.

---

### Post by ninesun on 2007-06-03
You can find something useful here:[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

---

### Post by djorzgul on 2007-06-03
I successfully installed x600 mob. few moments ago. I used Envy, and later I did all things here:
[http://ubuntuforums.org/showthread.php?t=463089](http://ubuntuforums.org/showthread.php?t=463089) it is a bit tricky if you're new to linux like me... but it is working.
For cd, phuh, I had to burn a new copy and it worked, so maybe you should try that. Also there is a *check disc integrity* option you should run too...

---

