---
title: "What to use for Remote Desktop, Ubuntu 2 Windows Vista"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by Sillywombat on 2009-02-20
Hi, I have to use a remote desktop program to get into a PC.
The PC i will be using is my trusty Ubuntu 8.04, and the computer that i would like to connect to is an evil MW Vista.

So my questions is the following:
1- Can I use the remote desktop tool that comes with ubuntu 8.04? Or is there a better alternative?
2- What MS program should i use on the vista computer?
3- How would one make the connection? Would i have to set up a VPN? Is there any important need to know facts or guides i should be aware of?

Any help on this would be great,
Thanks

---

### Post by jonobr on 2009-02-20
Hello

You need to enable remnote desktop on Vista, its disabled by default.
right-click the Computer icon and choose properties

Select remote settings link.
UNder the remote tab select allow connections from any (less secure)

I connected using the terminal server client in ubuntu 8.04 and 8.10 to windows and it worked fine 

Application-> intenet->terminal services client.

One other question, are you going to be connecting across the same network?
If so, nothing special required.
IF connecting across the internet , its doable just a bit more invovled

---

### Post by Sillywombat on 2009-02-20
> **jonobr said:**
> 
One other question, are you going to be connecting across the same network?
If so, nothing special required.
IF connecting across the internet , its doable just a bit more invovled

Yeah, im trying to do it over the net. What would i have to do to get round that?
By the way, love the father ted pick.
SW.

---

### Post by jonobr on 2009-02-23
Hey

You could use a service like logmein,
its pretty easy to use and most importantly,. free!


Copying files is a problem but there are ways around that as well if required.

And lastly , in the words of a great man


> GIRLS

---

### Post by miguel64086 on 2009-02-24
Hello,
I'm very new to ubuntu. I actually installed it for the first time last weekend. You know, I needed something new to learn  ;)
My question:
How do you do this the other way around?
I have a laptop PC running WinXP Professional and I would like to use a remote desktop utility into my Ubuntu (same network).  What do I need?  any guide I can use?

I know I can use SSH... but I would also like the graphical interface... I already set up SSH and SAMBA and UFW so I can manage editing files using vi and stuff

The reason I want to do this is for lazyness... ;)  My ubuntu is running on a desktop down in the basement, and I would like to be able to access it from anywhere using my laptop

Thanks

---

### Post by jonobr on 2009-02-24
hello

and welcome to the forums.

If you download an application called vnc viewer (thats free and you can get dofferent versions of it in different places.

You use that to connect to the ubuntu server.

Remote desktop needs to be enabled on the Ubuntu server.

Im not on my ubuntu machine at the moment, so I cant remember if its in preferences or admin, but in there you should see something that says remote desktop.
Change the settings on that to allow sharing.
Once done, get the IP of the ubuntu machine and then place it in the vnc viewer, hopefully it should work.

As you a re running over an internal network there is no need for tunneling etc, unless you are very very very very (very) worried about security

Cheers

---

### Post by miguel64086 on 2009-02-24
that worked. After enabling port 5900 on my ufw, it worked.
thanks

---

### Post by 005587 on 2009-03-01
Application-> intenet->terminal services client.

One other question, are you going to be connecting across the same network?
If so, nothing special required.
IF connecting across the internet , its doable just a bit more invovled

Can you walk me through the steps needed to connect to a remote server we have at work that runs Windows 2000 small business server by using the Terminal Services client.  I have tried multiple times to connect and can't get the settings correct.  I can connect my windows laptop to this server but don't understand which settings to use.  I have a domain name, and IP address with login name and password to work with.

Thanks,
Dianna

---

### Post by Al Fischer on 2009-03-02
I could use some guidance here too! Actually have been using Windows Remote Desktop from Xp to Xp with no problems. Is it possible to use Ms RDC to connect to Ubuntu too? How?

Looks like two of us need the same info.

---

### Post by linuxisevolution on 2009-03-02
If you want to see the Ubuntu machien on windows vista, it is actually simple. On the Ubuntu machine click system >> admin >> remoted destop and set it up correctly. THen on the vista machine install a vncviewer and connect to the other machine's IP.

---

### Post by 005587 on 2009-03-02
Actually this seemed to give me the answers I needed. 

[http://www.youtube.com/watch?v=n33yl1jAqgQ](http://www.youtube.com/watch?v=n33yl1jAqgQ)

Dianna

---

### Post by Al Fischer on 2009-03-02
NEAT! Well, that would have been my NEXT question. What I would like to do is connect from one of my XP boxes to Ubuntu using Windows Remoted Desktop Connection Client.

I normally use this from Xp to XP without problems. However it comes back a not being able to connect to the Ubuntu machine. I can connect with the VNC Viewer, so connectivty is not a problem. Any thoughts?

---

