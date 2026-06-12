---
title: "vcn viewer"
date: 2009-10-23
forum: Networking &amp; Wireless
---

### Post by craigtrom on 2009-10-23
hi everyone, since i`ve installed ubuntu i`ve been using remote desktop (ubuntu as server), and on the other computer i run windows xp, i use vncviewer, but today just stopped working. i installed a newer version of vnc trying to sort the problem but no good, and i use the built in remote desktop on ubuntu.
when i go to connect, everything is normal, ask me for password, and then gives me the screen from remote desktop, the problem is when i move the cursor it moves on the ubuntu but not on the window in vncviewer, i can move files and folders just cant see it happening on the vcnviewer.


thank you

---

### Post by Cybie257 on 2009-10-23
> **craigtrom said:**
> hi everyone, since i`ve installed ubuntu i`ve been using remote desktop (ubuntu as server), and on the other computer i run windows xp, i use vncviewer, but today just stopped working. i installed a newer version of vnc trying to sort the problem but no good, and i use the built in remote desktop on ubuntu.
when i go to connect, everything is normal, ask me for password, and then gives me the screen from remote desktop, the problem is when i move the cursor it moves on the ubuntu but not on the window in vncviewer, i can move files and folders just cant see it happening on the vcnviewer.


thank you

Is this being done via local network or the Internet? Also, is the XP using SP2 or SP3? Another question, to clarify, is the VNCViewer window showing a blank/black screen, or does it actually show you the desktop? By your description, I am assuming your are doing this through a local network where you can see both computers at the same time. I use VNC religiously and have run into many different scenarios. Overall, I found that installing SP3 on the XP machine(s) has always resolved a lot of remote issues as it improves networking by far. 

-Cybie

---

### Post by craigtrom on 2009-10-24
thank you for your reply.
i`m using xp SP3, the vncviewer screen shows the screen from ubuntu all the icons are there, i see the cursor moving and i can open and moves the icons around, just doesnt show on the vncviewer.
i have the ubuntu plugged to the modem from my broadband provider , and the xp is running wireless through the same modem.
everything was working fine until yesterday.


i have a spare modem same as the one im using now. wanted to plug the ubuntu on to it on a different phone socket at home and have the 2 modems working at the same time but when i turned on it disconnects the other. 

the reason i need to use vncviewer is because i dont have a monitor for the ubuntu. 
if there is any other way of controlling the ubuntu please let me know.

thank you for all the help

---

### Post by Cybie257 on 2009-10-24
Haven't forgotten, so check back and I will post another idea. On my way out the door.
-Cybie

---

### Post by kd4dii on 2009-10-25
Hello
     I am having similar problems with 2 machines running 9.1 RC.  I can see the cursor moving in the remote window but if I click on something I can't see anything happen on the remote machine. If I go to the remote machine I can see that the action I selected did happen, but it doesn't show in the viewer.  If I close the viewer and start a new connection it will show what happened but still acts the same.  An example is if I click to open my home folder on the remote machine, I don't see anything happen.  If I break the connection or go to the remote machine the folder is open.  But it doesn't show in the viewer unless I start a new connection.  I have tried some of the other VNC programs but all act the same.  Thanks in advance for any help anyone can offer.

Bob

---

### Post by Cybie257 on 2009-10-25
Well, thinking about what you both are saying, it seems you are both using the standard vncviewer. I've been using UVNC (uvnc.com) without any problems logging in from a friends house on his computer, from school on my laptop, and from a vista machine on the local network. I know that I have had some weird issues in the past with vncviewer whereas uvncviewer seemed to do a better job. 

If you google "uvnc" it'll pop right up and take you there for the download. If I recall correctly, uvnc doesn't have a standalone viewer to download, but when you go to install the package, you can de-select the server part and install only the viewer.

Give this a try and see if that remedies your problems.

-Cybie

---

### Post by kd4dii on 2009-10-25
Thanks for the suggestion Cybie257, but unfortunately it doesn't help my problem as it is a Windows program and both my boxes are running Ubuntu 9.1 RC.  I have tried running some of the other VNC flavors for Linux but it is the same with all of them.  Thanks again though.

Bob

---

### Post by Cybie257 on 2009-10-25
> **kd4dii said:**
> Thanks for the suggestion Cybie257, but unfortunately it doesn't help my problem as it is a Windows program and both my boxes are running Ubuntu 9.1 RC.  I have tried running some of the other VNC flavors for Linux but it is the same with all of them.  Thanks again though.

Bob

OK, so that would be more for the OP, but for you, I would suggest installing the xvnc4viewer via synaptics and log in via the Terminal Server Client. It's been working 100% for me the entire time I've been dealing with Ubuntu since V6.04

-Cybie

---

### Post by craigtrom on 2009-10-26
> **Cybie257 said:**
> Well, thinking about what you both are saying, it seems you are both using the standard vncviewer. I've been using UVNC (uvnc.com) without any problems logging in from a friends house on his computer, from school on my laptop, and from a vista machine on the local network. I know that I have had some weird issues in the past with vncviewer whereas uvncviewer seemed to do a better job. 

If you google "uvnc" it'll pop right up and take you there for the download. If I recall correctly, uvnc doesn't have a standalone viewer to download, but when you go to install the package, you can de-select the server part and install only the viewer.

Give this a try and see if that remedies your problems.





-Cybie




thank you very for all the help.
unfortunately the problem remains. 

thank you

---

### Post by craigtrom on 2009-10-28
so i tested with different computers and different viewers and they all had the same result. its definitely a problem with ubuntu probably the last update.

---

### Post by StewartG on 2009-11-05
I thought this was just going to be me suffering with this.

Someone must have a solution.

Tried a few clients on my windows machine and still no luck.


More googling reveals that turning off desktop effects cures this. So there is a choice... effects or vnc.

---

### Post by Tony Ricena on 2009-11-06
Yep I'm having this problem too.. but this is the funny thing...

It doesn't work when i try vnc between two desktops, doesn't work when i vnc from my laptop to the desktop.. BUT it does work when i vnc from my desktop to the laptop.. makes absolutely no sense!!  Please someone help us!!

---

### Post by StewartG on 2009-11-07
> **Tony Ricena said:**
> Yep I'm having this problem too.. but this is the funny thing...

It doesn't work when i try vnc between two desktops, doesn't work when i vnc from my laptop to the desktop.. BUT it does work when i vnc from my desktop to the laptop.. makes absolutely no sense!!  Please someone help us!!
Does your desktop PC have desktop effects enabled? If so turn them off and try again.

---

### Post by JBAlaska on 2009-11-07
It seems using [TightVNC](http://www.tightvnc.com/download.php) solves the problem for most ppl using compiz and VNC. You need to use both server and client of TightVNC. It comes in both Linux and Win versions.

---

### Post by brundles on 2009-11-07
Another one for disabling desktop affects here - had similar behaviour to the above only re-connecting still didn't show anything. 

Changing the remote desktop server software might work but I'd be surprised if changing the client software does (we tried 5 different clients across 3 platforms including Ubuntu's own remote desktop access before finding this thread)

---

### Post by Tony Ricena on 2009-11-07
> **StewartG said:**
> Does your desktop PC have desktop effects enabled? If so turn them off and try again.

But the thing is my laptop has desktop effects turned on as well, and it works if I remote into it.  But will give it a shot and see what happens.

*update* Well that seems to do the trick.  I am now updating this via remote desktop on the desktop computer.  Well its a shame, guess will have to tell my father to disable desktop effects everytime i need to remote into his computer.  Thanks though

---

### Post by kazbear on 2009-11-11
Figured I would chime into this thread, as I am having the same kind of issue.  Though I get a Black screen.

I just upgraded to 9.10 on my remote machine, using the standard remote desktop option.  I VNC from an XP machine (SP3).  Black Screen.  I tried TightVNC, but that does not do anything, but sit there (I need to look at program more, as I have never used it).  I also have tried the Remote Desktop Viewer from my Ubuntu 9.10 laptop (Though that has always been slower).  Black screen.

Previously had desktop effects enabled on the remote machine when it was 8.04 and it worked fine.  When I first set up again with 9.10, no effects, and no screen.  I turned them on again to check a few things, so I will go back and turn them all the way off and try again.

---

### Post by kazbear on 2009-11-13
I have disabled Desktop Effects, but no change.

---

### Post by kazbear on 2009-11-15
I guess it would have helped if I unchecked the box that required you to acknowledge the user trying to remote in...:)

Well I got it now.  Nevermind

---

