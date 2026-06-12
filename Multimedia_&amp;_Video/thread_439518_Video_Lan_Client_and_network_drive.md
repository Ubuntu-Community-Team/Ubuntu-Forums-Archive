---
title: "Video Lan Client and network drive"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by superyounan1 on 2007-05-10
I have a media folder on another computer that I mount on my laptop. 

When I try to play the video files with VLC, the video hangs and skips every few seconds, as though the connection is not fast enough. I attributed this to the slow computer and wireless connection, but when I tested the transfer rate out, it seemed MORE than enough by a long shot.

I tried watching the same shows in totem... not a problem! smoothe as butter. I tried messing with VLC's cache settings, but it only got worse. 

I like VLC more, and it doesnt do that with any locally stored files.

Anyone else having the same problem?

---

### Post by disturbed1 on 2007-05-11
What OS is the other PC using? If you are mounting the share using Samba, it's known to have some file locking issues. Try CIFS instead.

Also, do a long file transfer test, one that will take 10-15 minutes. This will help you determine if the connection is bogging down or dropping. Try getting an applet that will tell you your network speed during the transfer so you can rule out wireless, router, and/or other PC issues. Gnome has a panel applet in Synaptic called Netspeed.

---

### Post by superyounan1 on 2007-05-11
> **disturbed1 said:**
> What OS is the other PC using? If you are mounting the share using Samba, it's known to have some file locking issues. Try CIFS instead.

Also, do a long file transfer test, one that will take 10-15 minutes. This will help you determine if the connection is bogging down or dropping. Try getting an applet that will tell you your network speed during the transfer so you can rule out wireless, router, and/or other PC issues. Gnome has a panel applet in Synaptic called Netspeed.

I manually did a transfer test, the average speed was about 360KBytes/sec, and I double checked it by transferring the same file over http.

Both computers running ubuntu, but the same problem happens when I boot into windows XP on the computer serving the files.

yes, samba.

The strange thing is that VLC plays the videos perfectly smoothly when the laptop ( the computer on which I'm streaming to ) is connected through ethernet as opposed to wireless, which is what led me to believe that it was a speed issue, but the shows i'm watching are average 60Kbytes/sec, compared to the 360KB/s speed I measured, thats nothing. Plus they play fine in gxine and totem.

I'm thinking I'll just buck up and use another player when streaming, installing CIFS is more troublesome.

---

### Post by disturbed1 on 2007-05-11
CIFS is alreay installed. If you've declared smb in the fstab, just change it to CIFS.

That is weird that it works fine with a wired connection, but not wireless. Just pulling stuff out of the air here ;) but I wonder if VLC is at a higher priority that causes the wireless not to perform as well as it should. Just strange.

About that CIFS, since it is installed by default, it is worth looking into. It's been a while since I've used Samba, but here's the basic fstab entry for a CIFS share
```

//IP.ADD.OF.WINDOWS.MACHINE/WINDOWS.SHARE.NAME    /media/windows    cifs    username=$username,password=$password,noauto,uid=1000,guid=1000 0    0
```I moved to CIFS sometime between Warty and Dapper because of file locking issues, and poor wired network speed. Samba gave me ~4.8MBs, CIFS gives me ~11.2MBs.

---

### Post by superyounan1 on 2007-05-12
> **disturbed1 said:**
> CIFS is alreay installed. If you've declared smb in the fstab, just change it to CIFS.

That is weird that it works fine with a wired connection, but not wireless. Just pulling stuff out of the air here ;) but I wonder if VLC is at a higher priority that causes the wireless not to perform as well as it should. Just strange.

About that CIFS, since it is installed by default, it is worth looking into. It's been a while since I've used Samba, but here's the basic fstab entry for a CIFS share
```

//IP.ADD.OF.WINDOWS.MACHINE/WINDOWS.SHARE.NAME    /media/windows    cifs    username=$username,password=$password,noauto,uid=1000,guid=1000 0    0
```I moved to CIFS sometime between Warty and Dapper because of file locking issues, and poor wired network speed. Samba gave me ~4.8MBs, CIFS gives me ~11.2MBs.

interesting, I will try it this weekend and post results. Thanks!!

---

