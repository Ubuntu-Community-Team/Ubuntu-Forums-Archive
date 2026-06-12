---
title: "MSN and webcam on Ubuntu"
date: 2010-02-02
forum: Multimedia Software
---

### Post by cbert78 on 2010-02-02
I have recently switched over to Ubuntu 9.10 and it's working well but I can't seem to get webcam chat working with others who use MSN on Windows. I have tried Empathy, aMSN and have just tried installing Wine and getting Microsoft MSN through that program. None of these have worked for me. Does anyone have a better solution that doesn't involve going back to windows?

---

### Post by Icarus315 on 2010-02-03
I use Skype myself for web-cam chat, [> HERE <]("http://www.skype.com/").  There is a Linux client available, just get the .deb file for Ubuntu 8.10, it works fine in 9.10.  Of course your Windows friends will also have to use the Windows version of Skype, but the protocol of talking between the platforms works absolutely fine.  I've had web-cam chats between Ubuntu and Windows: works fine.

---

### Post by cbert78 on 2010-02-03
Yes, this is good advice. Skype is the best for video chat. However, I have many friends who use MSN for their video chatting and I'm trying to adapt to them. I cannot get them all to switch to Skype. Has anyone found an effective solution to this problem?

---

### Post by portentum on 2010-02-03
I use aMSN on a daily basis myself. Could you describe the issues you've had with it?

I suggest trying out the version in the PPA, if you haven't.
[https://launchpad.net/~amsn-daily/+archive/ppa](https://launchpad.net/~amsn-daily/+archive/ppa)

---

### Post by cbert78 on 2010-02-06
I go through the steps to set up the webcam, I can adjust the settings and can see myself. However when I send my webcam to a Windows MSN user and they accept, the session is immediately cancelled and the camera goes black. Is there perhaps something in the settings that I can alter to solve this issue?

---

### Post by portentum on 2010-02-06
I had the same issue when I first used it. I *believe* that it was because I didn't have the necessary ports forwarded (6891-6900). If I remember correctly my webcam worked without forwarding any ports in Windows, but for some reason it wouldn't in Linux.

[portforward.com]("http://portforward.com") may be able to show you a quick guide on port forwarding if you need it, and can navigate the advertising minefield they seem to have.

The [aMSN wiki]("http://www.amsn-project.net/wiki/Frequently_Asked_Questions#You_are_firewalled_or_behind_a_router") seems to suggest the same. Of course, this assumes that you are behind a router and haven't forwarded the ports.

Hope this helps.

---

### Post by cbert78 on 2010-02-07
Thankyou, I'll try this.

---

