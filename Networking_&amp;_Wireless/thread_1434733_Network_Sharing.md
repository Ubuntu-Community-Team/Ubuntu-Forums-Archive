---
title: "Network Sharing"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by marx321_10 on 2010-03-20
I have 3 computer all running kubuntu 9.10. 2 are wired to the router and the other 1 is wireless. Its a belkin N router and a Netgear N 300 usb adapter.
When I open Dolphin and goto networks I see all 3 desktops on all 3 computers ,but when I click on any of them they say they don't exist.
What do I have to do to get all computers sharing? 

This is my first time networking computers so I'm a bit stupid here.
Normally I find everything I need on the forums and never have to ask any questions but this time I'm lost.
Thanks for any help

---

### Post by Iowan on 2010-03-21
I've never used Kubuntu - so I'm kinda feeling around in the dark...
A couple of general questions - have you set up shares, and which method are you using for shares: SSH, FTP, Samba, NFS...?

---

### Post by marx321_10 on 2010-03-21
No I haven't. I'm pretty new to networking.
What would you suggest? 
Thank you for your reply

---

### Post by marx321_10 on 2010-03-21
I don't know if this will help any ( or hurt )but one of my computers I dual boot with vista. I setup a samba network. My Kubuntu computer can share with my vista computer but the vista computer has no access to my Kubuntu computer. The icon for the kubuntu computer is there under networks on the windows computer. It say it is not accessible and I might not have permission.

In the end I would like to learn how to network with both a kubuntu and a windows computer. 

Thanks again for your help

---

### Post by Iowan on 2010-03-21
You'll need some shares before they'll show - and you'll need to install Samba's server to share from a machine (the client is already installed - so you *should* be able to see shares on a Windows machine). To share from Ubuntu-to-Ubuntu, you *can* use Samba, but NFS is more native.

I have (or can find) some help page links :
[http://ubuntuforums.org/showthread.php?t=249889]("http://ubuntuforums.org/showthread.php?t=249889")
[https://help.ubuntu.com/9.10/serverguide/C/index.html]("https://help.ubuntu.com/9.10/serverguide/C/index.html")

---

### Post by ndefontenay on 2010-03-21
Hi.

You right click on the folder you want to share and go to "share" in the menu. The moment you enable the file sharing, you'll be asked to download samba files. Just do whatever it says.

once you got some files shared, your computer will show in the network area on the other computers.

Nico

---

### Post by marx321_10 on 2010-03-22
I did the right click share thing last night and it did nothing.........nothing tonight after some thinking it worked with samba. Thank you. I still can't stream video but I'll play around with it.

I will look into nfs thank you

---

