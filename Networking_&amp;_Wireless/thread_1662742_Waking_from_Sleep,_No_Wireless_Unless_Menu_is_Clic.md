---
title: "Waking from Sleep, No Wireless Unless Menu is Clicked and Computer Put to Sleep Again"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by corrytonapple on 2011-01-08
Hello Forum Community! :)
I had messed up my first Ubuntu install, a 10.04 install, then had to reinstall.  I did so, then went up to 10.10, which I had never tried before on this machine.  Well now when I put the computer to sleep, it drops the connection, like it is supposed to. But, upon waking it back up, it does not even try to connect. Instead, sometimes you have to just put it back to sleep and wake it again and it works.  Or, you have to wake it, click on the menu with the list of connections, and then put it to sleep again. I may have to go farther and go through to the point where I have to enter my password like I am editing the connection settings.  Sometimes it just works. :D  When I go to the menu with the connections, it says Wired: Disconnected and Wireless: Device not Ready.  Really, I do not know what I have to do to get it to do any of that to happen.  We also just replaced a bad router that would not let any computer connect to the Wireless internet without crawling (It was a new issue) and we were sent a new one by our ISP.  Though, I doubt it was the router.  Also, I am starting another thread on where the 10.10 install will not let me to go to sleep all the times.  It just, gives the flashing _ and then nothing but get hot.
My specs are: One year old (Not even) Toshiba L455-S5008; Ubuntu 10.10; Intel Processor
Thanks!

---

### Post by corrytonapple on 2011-01-10
Bump

---

### Post by PatchesTheCaveman on 2011-01-11
*Never mind, sorry.*

---

### Post by grahammechanical on 2011-01-11
Is the wireless connection set up to Automatically connect? Is Network Manager in the list of Startup Applications?

When the machine goes into sleep mode it powers down many of the electronic circuits. This saves battery power on a laptop. The wireless adapter is being switched off. It needs to be switched back on when the machine resumes from sleep and you want this to happen automatically. Some people may prefer the wireless adapter to remain switched off because they do not want internet access at that time and they want to conserve battery power. This would be my choice if I used a laptop. So, the OS has to keep both types of people happy.

Regards.

---

### Post by corrytonapple on 2011-01-11
Yes, the connection is set to connect automatically, and Network Manager is set as a Startup Program.

Your explanation is very good on how that stuff works. Thank you.  I would like it to just automatically connect, since it does not really matter anyway to me.  This laptop stays around the house normally.  Looks like another issue where sticking to Lynx might have been better.

---

### Post by corrytonapple on 2011-01-13
Bump.  It seems to have been working OK, but still does not work all the time.  Still need ideas here...

---

### Post by corrytonapple on 2011-01-18
It has been working recently.  Hmm, I have not had Gedit open, so that may be why.
Still not solved.  Think of this as a bump, a final bump, until I give up until 11.04 comes out.  If that does not work, then I will move on to openSUSE KDE 11.3.

---

### Post by grahammechanical on 2011-01-18
I have one more idea. Go to System>Preferences>Startup Applications. Under the options tab click the button that says Remember Currently Running Application. I do not really know what this is for. I suppose it can be used to load programs from boot. If you have no programs running but you do have a wireless connection, this might work. I do not know I have not tested it.

Regards.

---

