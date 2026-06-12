---
title: "Teamviewer in Natty:"
date: 2011-03-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kuvanito on 2011-03-06
Boy,I am learning,this is for 32 bit and it worked for me,you can either go directly to the teamviewer page and download your flavour and then just run the two last commands in a terminal,remember to replace the teamviewer name acordingly with your download or simply run all three commands. :D 

wget [http://www.teamviewer.com/download/teamviewer_linux.deb](http://www.teamviewer.com/download/teamviewer_linux.deb)
sudo dpkg -i teamviewer_linux.deb
sudo apt-get -f install

---

### Post by Briga on 2011-03-14
Well it's pretty easy also for amd64. 
Go to the website and download the latest 64 .deb
Right now you should be able to fetch it with:
```
wget http://www.teamviewer.com/download/teamviewer_linux_x64.deb 
```
then you can install it with:
```

sudo dpkg -i teamviewer_linux_x64.deb
```
Funny enough this works, if you double click the .deb the Ubuntu Software Centre (that now looks after installing .deb) fails claiming it is a bad package.

---

### Post by MadCow108 on 2011-03-14
> **Briga said:**
> 
Funny enough this works, if you double click the .deb the Ubuntu Software Centre (that now looks after installing .deb) fails claiming it is a bad package.
possibly this "bug":
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/712377](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/712377)

you can also use gdebi to install local packages correctly

---

