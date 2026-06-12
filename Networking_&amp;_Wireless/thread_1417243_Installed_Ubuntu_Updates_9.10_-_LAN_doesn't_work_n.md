---
title: "Installed Ubuntu Updates 9.10 - LAN doesn't work now..."
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by own3mall on 2010-02-27
I just installed a series of Ubuntu 9.10 updates, and after rebooting the machine, I can no longer connect via ethernet / lan to the internet.  The connection manager just shows the spinning graphic showing the adapter is attempting to connect to the internet. 

I don't know which update caused it, and I'm not very good with linux.

I was using network manager, and I believe that package was uploaded!  Help, what should I do now?

My Ubunutu is completely useless without a connection to the internet.

---

### Post by aextance on 2010-02-27
Hi again own3mall!

Yeah, I just got exactly the same thing! Can't connect via ethernet or wirelessly. Obviously it's not that our networks our down, because I can still connect to it in windows. 

I'm going to have a look around and try and find out what the deal is - unless some wise person comes on here and solves it for us.

---

### Post by aextance on 2010-02-27
Here's a thought own3mall - did you add that source for networkmanager that as I suggested at this thread:

[http://ubuntuforums.org/showthread.php?t=1369335](http://ubuntuforums.org/showthread.php?t=1369335)

Maybe it's something to do with that if we both have it?

Trouble is, I'm not sure how there's any way to fix it without network support...

---

### Post by aextance on 2010-02-27
OK, I fixed it, but in a very roundabout way.

The problem was with networkmanager itself, presumably because of an update on the "fix" for the wireless problem we've both been having. 

I think nominally the advice at this thread about reinstalling networkmanager from CD should have sorted it:

[http://ubuntuforums.org/showthread.php?t=1416973](http://ubuntuforums.org/showthread.php?t=1416973)

But my CD player is also not behaving, so I had to download the repository offline and port it to my laptop using a USB stick:

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

I also had to port the packages for networkmanager from this directory, as well as the repositories themselves:

[http://archive.ubuntu.com/ubuntu/pool/main/](http://archive.ubuntu.com/ubuntu/pool/main/)

PM me if you need some more guidance. 

Man - I had hoped to get a load of work done before lunchtime so I could enjoy the rest of the day, but this has really screwed that up. Angry!

---

### Post by own3mall on 2010-03-03
I'll give it a try.  Damn I hate Ubuntu.  I've got a Windows Server up, and it's so easy to use!  

Thanks for the information man.  I really appreciate it.  I will try it this weekend.

---

### Post by margemoosh on 2010-03-03
> **aextance said:**
> OK, I fixed it, but in a very roundabout way.

The problem was with networkmanager itself, presumably because of an update on the "fix" for the wireless problem we've both been having. 

I think nominally the advice at this thread about reinstalling networkmanager from CD should have sorted it:

[http://ubuntuforums.org/showthread.php?t=1416973](http://ubuntuforums.org/showthread.php?t=1416973)

But my CD player is also not behaving, so I had to download the repository offline and port it to my laptop using a USB stick:

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

I also had to port the packages for networkmanager from this directory, as well as the repositories themselves:

[http://archive.ubuntu.com/ubuntu/pool/main/](http://archive.ubuntu.com/ubuntu/pool/main/)

PM me if you need some more guidance. 

Man - I had hoped to get a load of work done before lunchtime so I could enjoy the rest of the day, but this has really screwed that up. Angry!

can you tell me what should i exactly do to fix this problem?

---

