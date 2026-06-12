---
title: "dial up problems"
date: 2006-02-02
forum: Networking &amp; Wireless
---

### Post by curds on 2006-02-02
Hello All,

I've installed UL 5.10 and am getting very pleased with it.   It coped easily enough with my Oki mono laser, which is a real boon.

However, like many on this forum I can't get a connection to my ISP.  Oh, I can dial it out and it seems to connect but if I select send/receive in Evolution I get "Error in fetching mail.  [www.toucansurf.com:](www.toucansurf.com:)  temporary failure in name resolution".

Sudo wvdial gives "section dialer defaults does not exist in wvdial.conf.  Cannot open /dev/modem: no such file or directory".

/usr/sbin/pppd /dev/ttys0 57600 debug connect "/usr/sbin/chat -v'' AT OK ATD08089933465 CONNECT '\d\c'"   gives "the remote system is required to authenticate itself but I couldn't find any suitable secret (password) for it to do so.  None of the available passwords would let it use an ip address".

Any help here would be greatly appreciated.  My ISP uses Chap authentication but I've tried the other two without any success.  

Could you please bear in mind that I don't really know what I'm doing.  I copied the commands from other threads in the forum.

---

### Post by towsonu2003 on 2006-02-02
[QUOTE=curds]
Sudo wvdial gives "section dialer defaults does not exist in wvdial.conf.  Cannot open /dev/modem: no such file or directory".
[/QUOTE]
0) the error code looks like your /etc/wvdial.conf is empty...

1) first things first ;) if any chance you have a winmodem, did you get the drivers for it?

2) secondly, did you run ```
sudo wvdialconf /etc/wvdial.conf
``` bf connecting with wvdial? if you did, what was the output? if you didn't, do it, than open the file up with ```
sudo cp /etc/wvdial.conf /etc/wvdial.conf.backup0001
sudo gedit /etc/wvdial.conf
```and input your information where it asks you to, save, close, and try connecting again ;)

3) PS. and you are running wvdial like this right? ```
sudo wvdial
```

4) ok, I'm done editing my own post, finally ehehe

---

### Post by curds on 2006-02-03
Hello Towsonu2003,

Thanks for your reply.  

1.          I have an external serial modem on the ttys0 port.

2.          No, I didn't.  So I tried your long command sudo cp /etcwvdial, and so on, but got 'no such file 
            or directory'

3.         Yes.

So it looks as if you are right - something is empty.

Now your question no 1 above has reminded me that I have the installation cd for my modem.  I'm going to try to install its program on Ubuntu and see what happens.  I'll let you know how I get on.

---

### Post by curds on 2006-02-03
Hi again,

No luck with my install cd for my Hayes modem.  It's for Windows only.

Best wishes,

---

### Post by towsonu2003 on 2006-02-03
In the following order, do: ```

sudo wvdialconf /etc/wvdial.conf
sudo cp /etc/wvdial.conf /etc/wvdialconfbackup.0001
sudo gedit /etc/wvdial.conf
``` and input your ISP info and password in the file where it asks for it. save, close, sudo wvdial
1st will configure and write configuration file for vwdial o dial out; 2nd will back up wvdial configuration file; 3rd will open up the configuration file. if 1st fails, don't go further and port error output here. hopefully, we can make sense of it. serial modems are suposed to work with linux without hassle... 

driver cds won;t work in linux, but may come in handy later. similarly, games and stuff written for windows wont work in linux without great effort.

---

### Post by curds on 2006-02-03
Hello,

Oh dear, things have gone wrong.  When I went to try your commands I found I couldn't bring Ubuntu up.  I have Windows XP, another distro, and UL on the hard disk, but only the first two were showing.

So I tried to re-install UL and couldn't complete the partitioning.  I kept getting a message about 'no root file system is defined' whatever that means.  I had formatted the UL partition before trying to re-install but now I'm now going to delete it altogether and start again.

Incidentally, found that, while trying to re-install, I didn't understand the manual configuration commands of the network.  This is probably where I went wrong in the first place.

I'll be in touch again, eventually.

Thanks for your willingness to help.

---

### Post by curds on 2006-02-03
Hello again,

Well, that didn't work either.  I deleted the partition altogether, created a new one, formatted it with the EXT3 file system, and, on a re-install try, still got the message 'no root file system is defined'.

It's just occured to me that maybe UL only uses EXT2 file system.  I might give this a try but now I'm tired and fed up.  

Curds

---

### Post by towsonu2003 on 2006-02-03
I don't know what UL is but the error message seems to say you don't have / (in linux terms). 
During (or just after) partitioning & formatting, make sure you let the installer to mount your UL root partition as / (or whatever UL calls its root... linux calls it / while windows calls it c: or d: or e: etc)
good luck

---

### Post by curds on 2006-02-04
I meant Ubuntu Linux by UL.  Sorry about that.

You are of course quite right.   What Ubuntu showed me at the partitioner was a mount point /media/hda4 and i thought that was okay.  When I replaced this with a simple  /  things proceeded further.

However, something has happened.  During the base install, I got a message about 'retrieving zlibig' had failed and then another about 'unable to install initrd-tools: check /target/var/log/bootstrap.log for details'.  (Quite how I was to do that without having the system installed wasn't clear).

So I had to abort the installation altogether.  I'm now going to try to install another distro on the same partition to see if this throws any light on the failure. 

It may be some time before I come back so don't hold your breath.

Look, I'm really grateful for your input into this.  Many thanks,

---

### Post by towsonu2003 on 2006-02-04
usually, when an installation fails in such a way, I hear two most common advices: 
1. check the md5sum of the iso you downloaded
2. burn the cd as slow as possible
if these don't help, you might wanna post a new thread in the installation / upgrade forum section with an informative title after searching the forum about the error. if opening a new thread, make sure you mention that you checked the md5sum and burnt the cd at (low speed here).

---

### Post by curds on 2006-02-04
Hi Towsonu2003,

Well, I have to say that my installation of Mepis on the same partition has gone extremely smoothly.  So there's nothing wrong there.

I think you're right about the burning of the Ubuntu cd.  I'll pursue this in due course when I've recovered a bit.  I've been on this for 3.5 hours since 4am and need to go back to bed.

I like the philosophy of Ubuntu and will get to grips with it eventually.

Many many thanks for your kind attention.  Don't think that your efforts to help haven't been appreciated.

Curds

---

