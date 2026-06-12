---
title: "ATI Drivers"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by weirdlookinguy on 2007-07-19
Hey guys, I switched over from Windows to Ubuntu Feisty on my laptop and it has been GREAT so far!!  I liked it so much, I completely erased Windows from my drive.

Well anyway, my laptop (HP Pavilion ze2113us) uses integrated ATI graphics, XPRESS 200M.  I have tried to install the ATI drivers using this method:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way)

everything installs fine, but ALL of the screensavers lag so badly they are unusable.  If the drivers were correctly installed, they wouldn't lag, would they?

Also, I have Miro installed.  It was working GREAT last night, but whenever I try to download ANYTHING, it starts downloading at 0kbps and then after 2 or 3 seconds stops downloading and says Error.  It has been this way all day today, but my friend's PC (Kubuntu 7.04) is also running Miro on the same net connection is downloading everything fine.

Can you guys help me with either of the issues?  The ATI drivers are the most urgent.

Side note - even though the screen savers lag, I can play back HD content in Miro and it looks beautiful, crystal clear, and does not skip at all.  Does that mean the ATI driver IS correctly installed and the screensavers lag for some other reason?  DVD playback is also working fine

---

### Post by wolfen69 on 2007-07-19
if the screensaver is the only thing not working well, i wouldnt worry about it. these things happen.

---

### Post by weirdlookinguy on 2007-07-19
I have no idea what is wrong with Miro though, and I REALLY want it to work!!  It was working fine yesterday

---

### Post by Shakkaa on 2007-07-20
To me it sounds like your'e having problems with 3D generation by your video card.......Personally I have an ATI card and it definately took me a while before I could use 3D features.....Some of the things I've had to do are using the restricted drivers which will give you fgrlx, install XGL (that's a big one) and trying to get the most up to date drivers out there....I dont' have the links, but everything you need has already been done by others.  I have such few posts because the only thing I have to do is use the search feature in the forum to be able to find how to configure something.....Now, integrated cards do tend to be more ineficient than stand alone ones because they share your pc RAM.  Even with my stand alone X1650 I have issues from time to time, but that's a driver limitation....ATI will hopefully release their card info soon so that some open source drivers can be made.....good luck :)

---

### Post by weirdlookinguy on 2007-07-20
yup, no 3D acceleration...... dangit child, I really want to play neverball and sauerbraten but they both lag so badly they are completely unplayable.  I have installed fglrx, and followed several guides on getting OpenGL working... no dice

---

### Post by Motoxrdude on 2007-07-20
post the output of```
glxinfo | grep direct
```
did you try using the restricted drivers manager? System>>Administration>>Restricted Drivers Manager.

---

### Post by wildgene789 on 2007-07-21
ubuntu@ubuntu:~$ glxinfo | grep direct
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17
ubuntu@ubuntu:~$ 

thats wat im getting in the terminal and when i enable my "Ati Accelerated graphics driver" its screws ubuntu totaly up and i dont even see the desktop anymore all i see if text at the beginning please help me.

---

