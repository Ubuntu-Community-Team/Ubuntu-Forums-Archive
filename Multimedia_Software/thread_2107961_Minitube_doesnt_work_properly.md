---
title: "Minitube doesnt work properly"
date: 2013-01-23
forum: Multimedia Software
---

### Post by Crisshome on 2013-01-23
I am using Lubuntu 12.10 and I installed minitube the lastest version and it still won't work right.
The appication does open but when I type to search something it just keeps on searching without anything to display.
After a while of searching finally it found something but I have to wait forever for the video to load.

I didn't had this problem with other versions of the Os.
So what gives?

---

### Post by abduljones on 2013-12-30
I have just received an update on my computer for the unpaid minitube due to an entry in my "other sources" in "software sources for  http;//ppa.launchpad.net/nilarimogard/webupd8/ubuntu precise main . I've now put this address into the "other sources" on my other 2 computers that have non working you tube, checked for updates and now they're all playing videos one after the other and downloading. I tried to put this info in a review but the auto editor insisted I couldn't so I leave it here for anyone who wants to try it. Please note you need to prefix this address with deb, as per the example, if you want to add it to your sources (the version of minitube is 2.0.1~webupd8~precise0)

 addendum Methinks you may have to use the ppa to install minitube in the first place. i say this because i tried it on my newest install and it doesn't work with the software centre version. Presumably I used nilarimogard's version on the other two, hence the update.


There's more- just did this and got a fully working minitube   [http://www.webupd8.org/2013/02/minitube-20-and-musique-121-released.html](http://www.webupd8.org/2013/02/minitube-20-and-musique-121-released.html)


to do 
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install minitube

---

### Post by monkeybrain20122 on 2013-12-30
That version of minitube is old and broken. The developer now sells an up to date version in the USC for $4 (called minitube-ubuntu instead of just minitube). Alternatively you can grab the source and compile it yourself, takes less than 5 minutes (don't know why the USC says the license is proprietary, developer insists that it is still gplv3 and source codes are available for download)

---

