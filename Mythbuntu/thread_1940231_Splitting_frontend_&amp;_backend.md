---
title: "Splitting frontend &amp; backend"
date: 2012-03-13
forum: Mythbuntu
---

### Post by se99paj on 2012-03-13
My main question is when should you decide to split a combined frontend/backend system?

I have a combined frontend/backend system which I've been running for sometime, I'm happy with how this is working at the moment but I'm keen to (a) make it quieter and (b) reduce the overall cost.

Making the system quieter would require some changes to the PC Case which aren't too difficult to do I just need to get around to this.

But reducing the cost isn't as easy, I did initially think that splitting the frontend and backend would reduce the cost, but I'd always need the backend to be on when the frontend is on, so instead of running one PC I'd be running two.

I've read projects on the internet of people that have split the frontend & backend but I think they have mainly done this so they can hide the backend in a cupboard (which I can't do) or because they have multiple frontends.

---

### Post by wyliecoyoteuk on 2012-03-13
A front-end system can run on a low energy device.

I use a combined back/front, but I also use other PCs as frontends.
These include a couple of netbooks and a MiniITX system with an Atom processor, which draws >25W.
The main unit is also a security camera server and home server with backups of all my other devices.
It has an Athlon X2 4850e (the e denotes energy efficiency) which draws 45W maximum.

I don't think disabling the GUI would make a noticeable difference to energy use.

---

### Post by klc5555 on 2012-03-14
> **wyliecoyoteuk said:**
> 

I don't think disabling the GUI would make a noticeable difference to energy use.

Disabling the gui in Ubuntu, though possible I guess, would have to be a real chore. Particularly since even basic functions like networking were moved into the graphical shell beginning with 8.04. If you want to run your mythbackend-only in text mode, you'd probably use a more streamlined distro like maybe Vector or Slackware.  You'd set up MYSQL from the CLI, then run X once to do the backend setup with mythtv-setup (since there's no ncurses interface for this) and then basically never run X again.

I moved the last of my backend-only machines from Xubuntu + Myth to Slackware + Myth about 2 weeks ago. (I still use Xubuntu + Myth on some of my frontend-only machines.) Though whether there's any real energy savings on these backend-only machines in their current configuration is unclear, I have noticed that their CPUs run consistently 4 to 6 degrees cooler without X than they did before.

---

### Post by se99paj on 2012-03-14
Thanks for the response guys.

wyliecoyoteuk - Do you run your main system 24x7?
At the moment I have my system setup to wakeup for recordings, I don't use it for anything else so thats not a problem for me.

I think I'll stay away from disabling the GUI as this sounds complicated.

I think I might split the work into two:

1.) Purchase a low power PC which I can try and use as a frontend. I can then try and make sure that this is working before doing anything else.

2.) Rebuild the backend by reusing the components from my existing PC, but think a bit more about noise and power consumption.

Then again I could just leave as it is, I might try and see what my current power consumption is at the moment. If I'm not going to reduce it by much then there might be no point in making the changes at all.

---

