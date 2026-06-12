---
title: "Not able to see Ubuntu from windows 7 but am able to see windows from Ubuntu 12.10"
date: 2013-03-01
forum: Networking &amp; Wireless
---

### Post by Robert98374 on 2013-03-01
Good Afternoon!

I'm trying to setup a small system to have running in the house to serve as an NAS/Torrent Downloader etc. Ive been following [http://lifehacker.com/5919558/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-ubuntu](http://lifehacker.com/5919558/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-ubuntu). I couldnt find the exact option to turn on windows sharing within 12.10 so i started a samba server, which works wonderfully from the ubuntu side but i am not able to see the computer from the windows 7 side. I followed the article on [http://www.liberiangeek.net/2012/10/share-files-between-windows-7-and-ubuntu-12-10-quantal-quetzal/](http://www.liberiangeek.net/2012/10/share-files-between-windows-7-and-ubuntu-12-10-quantal-quetzal/) 

The really weird thing is i am able to see the plex media server under media devices but not an actual computer with the computers name.

---

### Post by Robert98374 on 2013-03-01
I am also able to connect through Tightvnc so i can remote desktop

---

### Post by Robert98374 on 2013-03-02
Bump
Anyone else gone this route?

---

### Post by prodigy_ on 2013-03-02
> **Robert98374 said:**
> i am not able to see the computer
Could you be more specific? Do you mean you can't ping it even by IP? Or only by name? The latter is easily fixed using **hosts** file.

---

### Post by Robert98374 on 2013-03-02
Under Computer>Network Its not listed there, but the plex media server is

---

### Post by PhilGil on 2013-03-02
There's some security settings that need to be changed in Win 7 before it will see other computers on the network. Take a look at the first few steps of [this guide]("http://www.howtogeek.com/howto/windows-7/share-files-and-printers-between-windows-7-and-xp/").

---

### Post by Robert98374 on 2013-03-02
Yeppers all those setting are on since ive already have my other computers in the house networked

---

### Post by Robert98374 on 2013-03-02
Those settings are all running correctly

---

### Post by Robert98374 on 2013-03-02
OK so now i can see the ubuntu computer from windows when i directly open the ip address of the computer

---

### Post by prodigy_ on 2013-03-03
Like I said before, the easiest way to get name resolution working is to edit [hosts](http://en.wikipedia.org/wiki/Hosts_%28file%29) file on your Windows machine.

---

### Post by Robert98374 on 2013-03-03
Gotcha, so i would just add the ip address to the host file and t will show up?

---

### Post by Morbius1 on 2013-03-03
That ip address static by any chance?
 If it isn't then the hosts file may have to be changed every time you boot into that box - and if you know the ip address then you can access it that way...... 

Just out of curiosity run the following command and count the number of characters:
```
hostname
```
Is it 16 or more characters long? If it is then that's your problem. A minor change to /etc/samba/smb.conf will fix that.

---

### Post by Robert98374 on 2013-03-03
The IP address is static, i set it on my router so i could keep the address in VNC, it is more than 16 characters, how would that make a difference?

---

### Post by prodigy_ on 2013-03-03
Netbios names should be 15 or less characters long to be recognized by Windows. Since your hostname is longer, you need to add **netbios name** line to the [global] section of your smb.conf. E.g. ```
netbios name = myhost
```

---

### Post by Robert98374 on 2013-03-03
Kewl thanks! I just changed the host name to nas instead what it was

---

