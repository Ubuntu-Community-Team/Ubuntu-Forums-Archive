---
title: "MythTV, PVR-150 Remote Control Troubles"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by maeks84 on 2007-04-30
Simply put...  Can't get it to work.

For it to work, I think I need two files.  lircd.conf in ~/etc/lirc and lircrc in ~/.lircrc as well as linked in ~/.mythtv/lircrc   Which I've done.

When I do an irw, it returns things like  *0000000000001794 00 Up Hauppauge_350*  but I don't have a 350.  I have a 150.  Does this means I need a different lircd or lircrc file?  The files I used are the ones in the guide at [https://help.ubuntu.com/community/Install_Lirc_Feisty]("https://help.ubuntu.com/community/Install_Lirc_Feisty").  Are these good ones to use for a PVR-150?  The remote does nothing in MythTV.

Using Feisty.  Blaster/Receiver connected to the tuner card.
Not sure what I need to mess with.  Help appreciated

---

### Post by donhamilton on 2007-04-30
The source for the Lirc code is not incouded with mythTV  install.

Does anyone know why ??

thanks

donald

---

### Post by maeks84 on 2007-04-30
[COLOR="Red"]Bump[/COLOR]  :-\"

---

### Post by maeks84 on 2007-04-30
Okay, I don't think the problem is in my *lircd.conf* file anymore.  When I type irw, I get *00000000000017a5 00 OK grayHauppauge*.  This sounds more like my remote.  (Remote is Gray top and Black bottom)  So I don't think this is the problem.

So it must be the *.lircrc* file?  (*~/.lircrc*)  I've linked it to *~/.mythtv/lircrc* .  However MythTV doesn't seem to respond to it.  All I have in the *lircrc* file is...
```
begin
	prog = mythtv
	button = OK
	config = Enter
end

begin
	prog = mythtv
	button = Back-Exit
	config = Esc
end
```

Is this wrong?  What could be wrong that MythTV won't respond?  All I can figure out is that the above should work.  Help please?

---

### Post by maeks84 on 2007-05-03
I didn't realize that there was two user accounts created.  I was connecting via ssh and placing the lircrc file in my personal user account.  Instead, I had to connect as user mythtv and place the lircrc file under it.  I couldn't figure out the password for the default, mythtv, account so I had to boot as root and change it.  If anyone knows what that password might've been by default, please post.  I tried leaving it blank and "mythtv".  Anyway the remote works now.

Thanks to Rage at mythtvtalk.com for setting me on the right track.

---

