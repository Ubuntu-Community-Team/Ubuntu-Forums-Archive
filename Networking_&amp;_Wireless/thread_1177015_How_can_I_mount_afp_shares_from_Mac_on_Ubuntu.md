---
title: "How can I mount afp shares from Mac on Ubuntu?"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by darthpenguin on 2009-06-02
I have been all over these forums and others without success.

I have netatalk running on my Ubuntu box and set up avahi-daemon to broadcast netatalk and vnc to my apple computers. Ubuntu is behaving as a near-perfect Apple *server*. But how do I make is a good *client*? How can I get Avahi to discover AFP shares across the network and display them in Places --> Network? How can I mount afp on ubuntu? Thanks.

---

### Post by Homie Bongo on 2009-10-09
+1

---

### Post by lemonlovr on 2009-11-16
I agree - this information is too valuable to keep secret!

---

### Post by doobydave on 2010-01-04
Yup.

---

### Post by Fire_Chief on 2010-01-04
There is a command line AFP client you can install called afpfs-ng.
[http://sourceforge.net/projects/afpfs-ng/]("http://sourceforge.net/projects/afpfs-ng/")

I don't think there is a GUI for it or integration with Nautilus yet.

Cheers!

---

### Post by Goatrancer on 2010-02-09
Ugh I need to be able to access afp shares in GUI so that I can access music files from my mac and play the music in rhythmbox or other player on ubuntu. Samba was a no go for me (at least in terms of access the mac from ubuntu, the other way around worked fine for me). I guess I'll try FTP next.

---

### Post by Fire_Chief on 2010-02-11
Have you considered running a streaming server on your Mac instead of using file shares?

---

### Post by Goatrancer on 2010-04-21
> **Fire_Chief said:**
> Have you considered running a streaming server on your Mac instead of using file shares?

Oh just noticed this reply...
I tried Airfoil speakers but that seems to be a no-go in Karmic.
I'm not aware of any other streaming that I can use to go from Mac to Linux. I ended up just buying an audio splitter and a 50ft RCA cable. Sometimes the low-tech solution is the best :rolleyes:

---

### Post by darthpenguin on 2010-04-21
> **Goatrancer said:**
> Oh just noticed this reply...
I tried Airfoil speakers but that seems to be a no-go in Karmic.
I'm not aware of any other streaming that I can use to go from Mac to Linux. I ended up just buying an audio splitter and a 50ft RCA cable. Sometimes the low-tech solution is the best :rolleyes:

Hehe. I forgot about this thread. I like your music sharing solution lol. I use firefly (aka mt-daapd) on ubuntu to serve music to all my mac books. I think you can install firefly on OS X. It might work.

I have upgraded to 10.04 beta2 and I still can't connect to afp shares from ubuntu. Ubuntu's network browser has always been flaky anyway. Since I enabled ssh serves on all my mac books I can connect to them using sftp. It's not elegant, but it works.

---

### Post by Goatrancer on 2010-04-22
Yeah maybe I'll give firefly a try just for the fun of it... it's too bad that the Ubuntu network browser has a history of being flaky.. I'll have to do some research into whether other linux distros have similiar problems.

---

### Post by cygnl7 on 2010-05-02
I use [http://subsonic.sourceforge.net/](http://subsonic.sourceforge.net/) for listening to my music and love it.

---

### Post by Goatrancer on 2010-05-05
Sweet, I'll try this and post about how it works for me. Thanks for the info!

---

