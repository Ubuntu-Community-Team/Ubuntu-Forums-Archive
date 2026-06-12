---
title: "Newbie needs help"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by TopTrainer on 2010-02-27
[SIZE=3][FONT=Arial]Hi 
This is my first post and of  course I am asking for help which I desperately need :-|

Circumstances:

I  have a windows XP Pro machine and also a Server running ubuntu, the  server was built for me and the builder is no longer availble for  consultation.
The server drives which were on my desktop beside my C  drive were working floorlessly allowing me access until windows started  running quite badly which meant i had to reinstall it.

After the  reinstall I could not see the drives displayed and I am unable to acess  them from windows. And also not able to mount them.

The server  has not been switched off at any time and does not even have a monitor  or keyboard or mouse. I have not done anything to change any settings to  it. I have zero knowledge of the system.

My windows  administrator password is exaclty the same I have looked on the server  and my files are intact I just cant access them from windows which I  need to do.

I got the following details off the server :
KERNAL  LINUX 2.6.27.5 - 117. fc10.i686
GNOME 2.24.1
MEMORY 881.4 MiB
Processor  AMD LE 1620
Samba Server Version 3.2.4-0 fc10

If someone  could help me with regard to monting the  drives it would be great but I  have no linux knowledge whatsoever so it would have to be easy to  follow please.
I was told the drives should appear on their own but  thats not happening I am not able to sight them at all file sharing and  printer sharing is enabled.

Thanks

Peter[/FONT][/SIZE]

---

### Post by quixote on 2010-02-28
It's been a long time since I used Windows, but here are a couple of ideas that might help, if I remember it right, which I may not.

1) Can you see the server if you tell network neighborhood to search the neighborhood? If yes, then when you right-click, somewhere there's the option to "Map Network Drive".  After it's mapped, you can put the shortcut on the desktop.  Possibly, all that happened was that Windows lost that mapping after the new install.

2) Make sure that in the new install you and the server are members of the same Workgroup.

Hope that helps.

---

### Post by TopTrainer on 2010-03-01
Hi

Yes I am aware of the network map facility. I have tried that already, I think the problem is that the server is not being seen by windows and I am not sure how to achieve that.


Peter

---

### Post by Iowan on 2010-03-01
I should fire up my (wife's) XP machine and check some things...
Have you re-created the same user and password? (shouldn't affect visiblity)
As mentioned - workgroup is the same?
Server doesn't show up (at all) under the "browse" option of "Map Network Drive"?

---

