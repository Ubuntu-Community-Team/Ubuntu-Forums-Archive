---
title: "VNC on ubuntu 11.04 unable to fully control"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by scar1 on 2011-09-04
Hi,


I just upgrade my machine to 11.04 and enabled configured the remote desktop option within the O/S, I believe its Vino.

I checked the help to make sure I configured correctly [https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers) and my goal is to share my desktop and remotely access from another machine using TightVNC client.

Now I had no problem wit this when on uBuntu 9.04 however on this version of o/s seem to not be able to achieve same goal.

In preferences I have ticked **Allow other users to control your desktop** and I am able to connect to the machine ok however I cannot control....

Any help/advice on this would be great!

Thanks
Scar1

---

### Post by spiky001 on 2011-09-04
Can you explain more about problem. Look at this Thread earlier today [http://ubuntuforums.org/showthread.php?t=1497635](http://ubuntuforums.org/showthread.php?t=1497635)

---

### Post by scar1 on 2011-09-04
Thanks for your response....
I have checked the thread, I do not think its the same problem as mine.

I want to remotely control my Natty machine from a another workstation (currently running windows xp).

On the uBuntu machine, I set the properties of the default remote desktop config. I have ticked **Allow other users to control your desktop** and closed down the box.

I then launch TightVNC client on the windows xp machine, provide the ip address of the ubuntu machine and password. The VNC session starts and I can see my uBuntu desktop on my windows xp workstation, however I cannot control.

Am I missing something?

Thanks
Scar1

---

### Post by spiky001 on 2011-09-04
I have just tried tightvnc on my win xp all works as expected

---

### Post by scar1 on 2011-09-04
Are you using the default VNC server on ubuntu?

---

### Post by spiky001 on 2011-09-04
This is of my server

---

### Post by scar1 on 2011-09-04
Thanks, ill retest mine. Not sure why I have this issue... its not that difficult :-(

---

### Post by spiky001 on 2011-09-04
No all work straight away for me, do you have another ubuntu you can try on it?

---

### Post by scar1 on 2011-09-05
Ah, ok looks like my problem is not control related.
After moving machines so they are next to each other I noticed that my TightVNC session is indeed controlling the other machines however I cannot the updates on my tightVNC session.
On my actual uBuntu screen I can see the actions I am performing.

So I should rephrase my problem to VNC session is not refreshing maybe.

Ill check your original link to see if I have the same problem.

Cheers
Scar1

---

### Post by scar1 on 2011-09-05
Hi,

In the end I installed x11VNC, configured and connected from tightvnc client first time!
There must be some sort of bug or issue on my machine using the default VNC server....

Thanks for all the advice...

Cheers
scar1

---

