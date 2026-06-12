---
title: "Ubuntu 11.04 Beta 1 mouse issue quick question..."
date: 2011-04-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by MisterGaribaldi on 2011-04-08
Is anyone else having a problem where, every time they boot 11.04 Beta that they have to unplug and reconnect their mouse because it's frozen?

That's what's happening to me.

Admins/Mods: Please feel free to move this post to a more appropriate area if *this* isn't it.

---

### Post by fish11 on 2011-04-08
hi,

i have the same problem

---

### Post by KegHead on 2011-04-08
Hi!

Not me!

11.04b/classic/2.6.39 rc2.

KegHead

---

### Post by KegHead on 2011-04-08
Hi!

Have you tried to adjust via:

System...preferences...mouse?

just an idea!

KegHead

---

### Post by Iowan on 2011-04-08
Moved to Natty Narwhal Testing and Discussion

---

### Post by 5149.5 on 2011-04-08
I'm not sure if it's related but my mouse acts a little strange at times. Some of the links on a page stop responding properly. Two links can be side by side or one line above another and one will work and the other one doesn't. Restarting FF will clear the problem. ????

---

### Post by michillin212 on 2011-04-08
I have 11.04 on my laptop and sometimes my mouse just freezes.  It also seems to skip around quite frequently.  Also, I have noticed that some links don't work.  For example I can't click on the Google logo on my iGoogle page.  If I plug in a different mouse the touch pad seems to work fine.  I hope this helps a little bit.  Thanks!

---

### Post by MisterGaribaldi on 2011-04-09
Hi Folks!
 
I apologize for not sticking this thread in quite the right spot earlier, and for not getting a little more in-depth in my original post. I will rectify that now.
 
First off, the computer I have is an [eMachines W5243](http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?CategoryID=1&DetailID=685&DetailName=Feature&MenuID=24&LanID=9). The link will take you to the page on ECS's web site for the motherboard.
 
Basically, this is a GeForce 6100/nForce 405-chipset mobo. Clearly, it's not the newest thing in the world, but it's still quite functional and serviceable.
 
The only time I've ever seen this kind of issue before (although it will then frequently lock up the keyboard, too) is if an OS hangs the computer and I have to turn the computer off manually. It's like the USB bus controller and the keyboard and mouse attached to it are no longer able to talk to each other.
 
And, just like in that kind of case, unplugging and reconnecting (in this case) the mouse resolves the problem.
 
This occurs whether I've warm-rebooted or cold-started the computer back into Ubuntu 11.04; however, if I reboot (warm or cold) into Windows, or if I warm or cold reboot out of Windows and either into Ubuntu or back into Windows, this problem does not continue.
 
(Typically, when there's been a crash or some kind of glitch in shutting down, no OS on the system will talk to the keyboard or mouse.)
 
If you folks should require any further details, just ask and I will respond as quickly as I can.
 
Thanks so much in advance for the patience and the help!

---

### Post by MisterGaribaldi on 2011-04-11
Not to bump my own thread (bumpity bump, btw.) but I'm curious to see if any of the latest updates have helped anyone else who's had this problem.

I mean, I know it's a beta and I'm not in any way complaining, but this obviously points to some weird quirkiness and I just want to see what's the deal.

---

### Post by rburkartjo on 2011-04-12
yes i have had this problem periodically with b1.i thought it was just me. glad to know i am not alone.

---

### Post by Hogashi on 2011-04-14
I have another problem with my mouse. It seems there is an area my mouse can't click on and it can't click on some buttons either. It's weird that sometimes I have to hover my mouse above some buttons a little bit to click them.

Sorry for my bad English.

---

### Post by Harry33 on 2011-04-14
> **Hogashi said:**
> I have another problem with my mouse. It seems there is an area my mouse can't click on and it can't click on some buttons either. It's weird that sometimes I have to hover my mouse above some buttons a little bit to click them.
Sorry for my bad English.

We have beta-2 now.

---

### Post by AhronZombi on 2011-04-21
> **Hogashi said:**
> I have another problem with my mouse. It seems there is an area my mouse can't click on and it can't click on some buttons either. It's weird that sometimes I have to hover my mouse above some buttons a little bit to click them.

Sorry for my bad English. Im running the latest 64 bit version of Natty and i have the same issue. Some buttons and text boxes down allow selection via the mouse. Its something that doesn't always happen but its very frustrating. If i use the tab key to make the selection it works fine. This happens with app buttons and also things like links on  web sites, some will be click-able and others wont.

---

### Post by lucazade on 2011-04-21
> **AhronZombi said:**
> Im running the latest 64 bit version of Natty and i have the same issue. Some buttons and text boxes down allow selection via the mouse. Its something that doesn't always happen but its very frustrating. If i use the tab key to make the selection it works fine. This happens with app buttons and also things like links on  web sites, some will be click-able and others wont.

I've seen this issue today for the first time, it was a website link in chrome that wasn't clickable (usualy is).. also re-opening chrome didn't solve :|
IIRC there was an old issue of unity, a small area not clickable that appears randomly.

---

### Post by AhronZombi on 2011-04-21
> **lucazade said:**
> I've seen this issue today for the first time, it was a website link in chrome that wasn't clickable (usualy is).. also re-opening chrome didn't solve :|
IIRC there was an old issue of unity, a small area not clickable that appears randomly.

Looks like its not just me. And it seems to be a problem across all apps for me not just chrome. Hope we can find a fix or workaround thats better than using tab for selections.

(right now i cant click the "submit reply" button on this page

---

### Post by lucazade on 2011-04-21
> **AhronZombi said:**
> Looks like its not just me. And it seems to be a problem across all apps for me not just chrome. Hope we can find a fix or workaround thats better than using tab for selections.

(right now i cant click the "submit reply" button on this page

I'm trying to find that old unity bug (a small are not clickable - dead zone) but without success.

I've found this report and beside original description the third comment seems close to what i've seen here 

"It seems there is a zone, in the middle of my screen, that is un-click-able. example: I open a web page ( no matter which one, it could have been an other, non web browser application too) : I chosed my launchpad account page ([https://launchpad.net/~winniemiel05](https://launchpad.net/~winniemiel05) ), but it just an example, chosen because there are lot of links. I tried to clicked on a link in the middle on the page ( the karma link in this case). Impossible. I used scroll bars, to have the link higher on the desktop, and it became click able, but the link that were approximatively in the middle of the page now, became, them, un-click able. I used scrollbar to come back in first state, and I wasn't able to click on karma anymore.

More funny. If my mouse is in this "dead zone"... the wheel become unusable anymore too.... I really don't know where it can come from...It sort of No-mouses-land. What coult it come from? Which log files or informations would you like to have"

[https://bugs.launchpad.net/light-themes/+bug/741112](https://bugs.launchpad.net/light-themes/+bug/741112)

---

