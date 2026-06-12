---
title: "Video Resolution no longer works"
date: 2006-10-20
forum: Multimedia &amp; Video
---

### Post by timmahhny on 2006-10-20
Yesterday this was working great, no problems with the sceen resolution. Today turn it on and wham, can't get the resolution off of 640X480.
 I can't change the resolution due to no options. I click on the arrow and nothing. I read in another post about the sudo command: <b>sudo dpkg-reconfigure -phigh xserver-xorg<b>
But that didn't do anything.

 I am not sure what is in this box, since I did not build it, it was given to me. But it is an hp pavilion 513x. The only thing I did, was to throw spare ram in it, a few months ago.

 I just recently as of two weeks ago, reinstalled Ubuntu because of some reason, that I can't remember right now. 

 Any help would be greatly appreciated, since I don't want to go through the install and updates again. (MY internet provider has a small 2 gig a month limit on downloads for any reason). So called highspeed internet service. And I am sure I just used all of that and more this past two weeks. 

 Thanks

-timmahhny

---

### Post by DC@DR on 2006-10-20
How about boot up in recovery-mode, and then "sudo dpkg-reconfigure xserver-xorg", then follow the instructions from that screen?. Even better, please post your /etc/X11/xorg.conf here, and it seems weird to me that Ubuntu should never suddenly break things overnight like that, didn't you do smth seriously to the system yesterday? :)

---

### Post by tommcd on 2006-10-20
You have to be sure to stop X first, so go to a command promp (ctrl+alt+ F1, or F2, etc) then type 'sudo /etc/init.d gdm stop'. Then do 'sudo dpkg-reconfigure xserver-xorg' to add higher resolutions. When done, to restart X do 'sudo /etc/init.d/gdm start'.
You can also boot to recovery console as the system starts to boot and do 'sudo dpkg-reconfigure xserver-xorg' from there as well.
Hope this helps.
EDIT: it is 'sudo /etc/init.d/gdm stop' sorry for the typo.

---

### Post by timmahhny on 2006-10-20
I will try that as soon as I get down there to do it.

*"and it seems weird to me that Ubuntu should never suddenly break things overnight like that, didn't you do smth seriously to the system yesterday?* 

 I worked with abiword last night and that was it. I shut it down and started it about an hour or so ago.
I can't think of anything that I did other than word processing. I ran updated today but that was after the problem occurred. 

 I am new to Linux, and the previous install all of a sudden did not want to do any updates. I looked for possible solutions and just said to heck with it and reinstalled Ubuntu. 

 Otherwise Ubuntu has been great. 
I will try some of the following posts and see how that works.
Take care and thanks
I will give an update.
-Timmahhny

---

### Post by timmahhny on 2006-10-20
I just turned on the monitor and all works well. I think what ever it was that I tried before; maybe it just needed to reboot. At any rate it looks good at this moment.

 Thanks for all of the hlep.

-Timmahhny-

---

