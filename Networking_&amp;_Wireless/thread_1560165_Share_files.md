---
title: "Share files"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by mje1708 on 2010-08-24
Hi

Probably a stupid question but here goes -

I have a desktop downstairs connected via ethernet cable to a (wireless) router. I wish to store movie files, photos, music files etc on this desktop and have them accesible by other computers scattered around my house - these are mainly laptops connected wirelessly to the router but there is one other desktop upstairs connected via ethernet  cable to the router downstairs. 

How do I achieve this? Although I am fairly familiar with Windows and have in the past created windows networks to do just this, I am not sure how to start with Ubuntu/ Linux. 

I also have a couple of questions -

1, Is it possible for Windows computers to connect to this "network"  or must all network members be running Ubuntu?
2. Can files be accessed fast enough so that, for instance, a remote computer could view a movie file which is stored on the downstairs desktop?

Thanks for all help.

Mike

---

### Post by gordintoronto on 2010-08-24
In the file manager Nautilus, you can right-click on a folder and select "sharing options." You have to give it a "share name" which may be the name of the folder, or some other name. Nautilus might tell you to install some software at that point.

Click all the options. The computer and shared folder should be visible to/usable by both Windows and Linux computers. In Ubuntu, start at Places/Network.

The characteristics of your network and the resolution of the video will determine whether you can play it from the server. If that is flakey, just copy the file to a temporary-files folder.

---

### Post by mje1708 on 2010-08-24
Thanks - that sounds relatively painless - I am away from home at the moment but will give it a go when I get back tomorrow.

Just one question - your answer seems to imply that I already have a network. I have not done anything on either windows or Linux to create this network. Is there automatically a network by virtue of the fact that all of my computers are either wirelessly or by ethernet plugged into the same router?

Sorry to be so dumb :)

---

### Post by gordintoronto on 2010-08-24
If you plug your computer into a modem, router or switch, it is "on a network." (smile)

One thing which might make a difference, especially with older versions of Windows, is to make everything part of your (unique) workgroup. In Windows, it is one of the Properties under "Computer", in Linux it's in /etc/samba/smb.conf about 20 or 25 lines from the top of the file. I suggest using a name such as mjenet, so you won't get confused by common or default names.

---

### Post by Ghost_Mazal on 2010-08-25
Same ip and subnet range is important too. But if all your pcs and laptops ip option is set to DHCP they should get ip information automatically from the router.

---

### Post by mje1708 on 2010-08-25
Thanks - sounds pretty straightforward :)

I will give it a try when I get home tonight.

---

### Post by mje1708 on 2010-08-28
Thanks everyone.

Everything works fine - easy and no problems. I can now access files from my desktop from any other computer in the house - just what I wanted. Streaming videos works fine too so I can keep all of my videos on the PC downstairs and access them from my netbook, laptop, whatever :)

I am now thinking about accessing this desktop PC through the internet whilst I am away from home. What is the easiest way to do this?

Thanks

Mike

---

### Post by gordintoronto on 2010-08-29
I suggest a new message thread, please.

The first step is to review the terms of service for your ISP, to see if they will allow you to operate a server.

---

