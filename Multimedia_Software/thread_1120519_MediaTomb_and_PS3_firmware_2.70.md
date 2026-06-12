---
title: "MediaTomb and PS3 firmware 2.70"
date: 2009-04-09
forum: Multimedia Software
---

### Post by WENergy on 2009-04-09
I used to be able to stream media to my PS3 using MediaTomb as my media server.  It worked flawlessly.  However, ever since I updated the firmware for my PS3 to 2.70,  all my media now shows up as "Unsupported Data".  I was wondering if anyone has encountered this same problem and if there is a solution.

I tried using PS3 Media Server ( [http://ps3mediaserver.blogspot.com/](http://ps3mediaserver.blogspot.com/) ) but was not able to successfully stream anything.  It doesn't matter to me if I use MediaTomb or another program, I just want to be able to stream my media again !!

---

### Post by WENergy on 2009-04-09
any ideas to help me stream media to my ps3 again ?  ive been searching the net and havent been able to find any solution to this ><;  help would be very much appreciated !

---

### Post by Emanuele_Z on 2009-04-13
You're not the only one...
Actually I wrote the files into a DVD and PS3 is able to properly read those.

Now mediatomb works only with wmv and mpeg formats.
Is like avi container support is broken.
Whose fault? Sony's or Mediatomb?

Anyway, I'd like to stream my movies...

Cheers,

---

### Post by Emanuele_Z on 2009-04-13
Fixed:

It was just a merely configuration settings issue:

1) open the file */etc/mediatomb/config.xml* (you'll need *sudo* to write it)
2) Search the line ```
<protocolInfo extend="no"/><!-- For PS3 support change to "yes" -->
``` and replace *no* with *yes*
3) Search the line ```
<!-- <map from="avi" to="video/divx"/> -->
``` and uncomment it (in xml language it means remove the *<!--* and *-->* on the same line).
4) Restart the service (*sudo service mediatomb restart*) et voila', it's done!
5) Profit!

Hope this helps,

Cheers,

---

### Post by WENergy on 2009-04-16
thx for the tip emanuele !  i actually tried that before i posted here cuz i read it somewhere else, but for some reason, i still couldnt get it working.

anyway, i was just able to get my ps3 to stream media again using fuppes.  to me, it works exactly like mediatomb did, so i have no issue in keeping it.  thanks for the help !

---

### Post by guv999 on 2009-04-19
Thanks for posting Emanuale.   This worked well for me

---

### Post by nickwalnut on 2009-05-01
I'd like to bump, 'cause I'm experiencing the same problem and I would rather not have to change my media streaming software.

I know that it's a server-side issue, because I have a NAS and we had the same problem with it after the 2.70 update (.avi files no longer supported). We later found out that Sony had updated some sort of security feature or something to do with .avi and divx playback, and the company that makes my NAS quickly released an update which allowed the files to be played on the PS3 again.

It's this sort of update that I need with MediaTomb. The files on my NAS can't be played if they're stored on my Ubuntu PC. Does anyone know of the solution?

---

