---
title: "Can't connect to network on my desktop"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by Woody_Paranoia on 2010-03-13
Hello,

I am brand new to the whole ubuntu so I really don't know much about the system as whole other than the few weeks i had an older version on my laptop.

I have googled the problem and searched through some of the threads on here and seen other people with this problem and although i have followed some of the steps by other users i can't seem to find my network. 

The only advancement i have got is going from the network dialogue saying "no wireless networks" to "device not ready"... this may be a step back but as i said i am basically new to the system so i really don't know what I am doing.

Any help appreciated please, if you want anything from me i.e. pasting from terminal then just tell me what to type and what to paste and i will be happy to post them

Thanks in advance.

---

### Post by bkratz on 2010-03-13
Not much info here. It looks like you are trying to get wireless working? See this thread to get an idea of what information is needed to get help.

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by Woody_Paranoia on 2010-03-13
This is a copy of all the information that is mentioned in the link posted above:

[http://www.mediafire.com/?sharekey=1cd3fd4c7266330cc79b87b207592a1c5b9d182fe1584b024d71ee60c1ce7296]("http://www.mediafire.com/?sharekey=1cd3fd4c7266330cc79b87b207592a1c5b9d182fe1584b024d71ee60c1ce7296")

I hope that works as the files were too big to just upload as an attachment... one file is a version on notepad on windows and one is a version for the notepad on Ubuntu...


Also i think the problem is enabling my Wireless Adapter... As i can't even seem to pick up wireless networks.... But like i said i am basically brand new to Ubuntu and even after reading lots of posts and google'ing fro results i still cannot connect or even find a network... and now it seems the device can't be found....

---

### Post by Woody_Paranoia on 2010-03-13
Bump ](*,)

---

### Post by soropi on 2010-03-13
As I can understand from this error 
> [ 8378.011152] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.try to load driver giving
```
sudo apt-get install b43-fwcutter


```See information on site

---

### Post by Woody_Paranoia on 2010-03-13
That solution has not worked... the firmwire wont install and i can't go online for help from the website...

---

### Post by Woody_Paranoia on 2010-03-13
Bump :(

---

### Post by bkratz on 2010-03-13
the solution provided earlier would require you to have a wired connection available, are you saying you don't? If not, there are directions on how to download this from the live cd here

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by Woody_Paranoia on 2010-03-14
I have tried everything on that thread including the processes for both drivers. I have also tried downloading the drivers from the links provided at the bottom of the thread and installing them, but still no luck. 

I seem to have gone backwards as it now says nothing about a wireless connection.

I am thinking that maybe a re-installation may be necessary and try from there?

---

