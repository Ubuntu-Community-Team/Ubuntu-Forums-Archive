---
title: "Change read only permissions on a Samba share"
date: 2013-03-15
forum: Networking &amp; Wireless
---

### Post by AmbiguousOutlier on 2013-03-15
Hello, I have a NAS drive which I've created a samba share to Ubuntu, I'm then trying to make the share read write so I can use Picard to write changes to it.

```
sudo mkdir /home/rhys/samba_flac
sudo mount -t smbfs //berry/flac_music /home/rhys/samba_flac
sudo chmod -R 777 /home/rhys/samba_flac
```

I'm expecting this work but it doesn't, the share is created but it's read only. 

I'm sure there's an obvious command or options statement. Could someone please be so kind as to let me know.

Thank you.

---

### Post by AmbiguousOutlier on 2013-03-22
Is there an alternative to using Samba?

---

### Post by mike acker on 2013-03-22
> **RhysGM said:**
> Is there an alternative to using Samba?

cheer cheer cheer

we need to form a Fix Networking Group. which needs to start by junking samba 
we need a product that is easy to configure and reliable .

... although in my case i am suspecting more and more the real problem is msft\windows; very possible not samba at all...

...any info?

i have 1 other Linux box maybe i should fire it up and work on more testing .

Fussing with Windows: I discovered... Windows offers to report "devices not connected to the net" .  selecting this option I found the missing computer and right clicked it. windows offers to open it in a new window and this succeeded: i got access tot he Samba share

i'm thinking more and more this is just msft..... making an * of themself as usual .

---

### Post by prodigy_ on 2013-03-22
First, smbfs is deprecated, I'd use CIFS instead. Second, you should specify permissions as a mask at mount time. Example:
```
sudo mount -t cifs //berry/flac_music /home/rhys/samba_flac -o dir_mode=0777,file_mode=0666
```

More info here: [CIFS man page](http://www.samba.org/samba/docs/man/manpages-3/mount.cifs.8.html). Or simply type **man mount.cifs** in terminal.

---

