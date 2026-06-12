---
title: "Not sharing - x2 Ubuntu 12.04 LAN to router ?"
date: 2013-07-03
forum: Networking &amp; Wireless
---

### Post by grey1beard on 2013-07-03
I've connected two laptops with 12.04 to my router, via LAN cables, in order to copy several files over, in a 'one-off' exercise.
Using 'Sharing Options', I've run into the attached error window on the first machine that I installed samba onto.
Can anyone interpret the message for me ?

John

---

### Post by grey1beard on 2013-07-03
I've been looking at the smb.conf file, and I can see that I might have to do some editing !

EDIT  More reading leads me to notice I have no settings in the Global Settings between the heading [global] and the first commented out line ##Browsing/Identification. 
Is this the problem ?

I assume I need Samba set up on both laptops, but should I edit both .conf files to be the same, when I've managed to work out what changes I need ?
A  .conf example for this set-up would be a great help. 

John

---

### Post by DeathByDenim on 2013-07-03
You only need to set up the .conf file on the machine where you would like to share from (the server). On the other PC (the client), you should be able to connect to it. In your file manager you can type in the location bar something like: "smb://myserver", where you need to replace myserver with the name of the server (or IP address).

 I find that Samba is usually a bit of a pain to set up though and since you are doing this only one time, it might be simpler to install openssh-server on the server and from the client type "sftp://myserver". No configuring required as far as I know.

---

### Post by Bashing-om on 2013-07-03
grey1beard;

While "samba" can be made to work ..in this situation is a overkill.
Sometime past I pulled my files off my old system onto the new system - common router-  and all I had to do was to enable "filesharing: -right click on directory, set up for this purpose - on both systems. Accessed the old system via nautilus's "network" and copy paste all the files I wanted from one window to the other ... and done ! No other configuration was needed.

[INDENT][INDENT]simple is better[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-07-03
@ grey1beard;

Talk about simple ... see this that I just ran across !
[http://ubuntuforums.org/showthread.php?t=2159449](http://ubuntuforums.org/showthread.php?t=2159449)

[INDENT][INDENT]binding to me notes[/INDENT][/INDENT]

---

### Post by grey1beard on 2013-07-04
> **Bashing-om said:**
> @ grey1beard;

Talk about simple ... see this that I just ran across !
[http://ubuntuforums.org/showthread.php?t=2159449](http://ubuntuforums.org/showthread.php?t=2159449)


Thanks Bashing-om, that worked first time !

My set was - the 'server' laptop that had the files I needed to copy was connected with a LAN cable to my wireless router. 
On this I used the Terminal  to set up the code** python -m SimpleHTTPServer**, having used** cd** to change to the directory the files were in.
I then clicked on the network icon , and went to 'Connection Information' to obtain the Wired IP address of this laptop (192.168.2.10 in my case)

The 'client' laptop was connected wirelessly to the router, and I typed the url http : // 192.168.2.10:8000 (without spaces) into the Firefox browser, and there was the directory, which I copied, (right clicked, and 'save link as'), into my Download directory.

Doddle, as we say in these parts, and kudos to Morbius1.
John

---

### Post by Bashing-om on 2013-07-04
grey1beard; Outstanding.

Glad to be of some aid...
And yes indeed  "kudos to Morbius1" a fount of knowledge on many fronts !

[INDENT][INDENT]cheerily on our way
[/INDENT][/INDENT]

---

