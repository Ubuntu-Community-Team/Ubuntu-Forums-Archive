---
title: "WHITE SCREEN on update ==DELL Inspiron mini 1020 -upgraded to Ubun11.10 Beta(2) Natty"
date: 2011-04-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by dvenkatesan@yahoo.com on 2011-04-21
Hello all,

I was running UBUNTU MOBLIN (Karmic 9.10) edition on my Dell Inspiron Minin 1020 netbook.(Intel atm SMP x86).

I did not like the desktop so decided to upgrade to Ubuntu Lucid 10.04. I changed the update repository in /etc/apt/ to lucid (from default karmic ).

After running update, upgrade, my system booted up and failed to load Xwindows desktop AND INSTEAD fell back to terminal mode. I could login as ROOT and tried to set up x- configuration but not successful. So I thought going to latest version might help in all and went to upgrade my system to U-11.2 Beta2 NATTY NARWELL.

So I again changed the repository to Ubuntu 11.0 Natty and run update, upgrade.I set UXLAUNCH.conf as the default desktop.


After reboot I AM able to load X but get PURE WHITE SCREEN. (failed to load default desktop like Gnome/Kde). If press power-off button "Dalston power applet" comes up asking for direction and similarly if I insert/remove my ethernet cable bubble tip comes up to indicate what is happening to netwrok interface. It means my X-server /video configuration is OK and i am not getting garbled screen.

HOWEVER since no desktop is comming & I am getting white screen I am unable to use the system. No application could be launched.

I am UNABLE to go to the command prompt/terminal also by pressing CNTRL+ALT+F1.

I am UNABLE to arrest the boot up process/inint script  at the startup (by presing ESC etc..)to go to command prompt. (actaully I get termianl mode and it allows me enter root password and gave me root prompt. But subsequently init script continued to run --without halting and allowing me use terminal to do administration -- and continued to go ahead and launch a WHITE desktop screen hiding my logged in terminal.

Any help will be thanked.

D.Venkatesan

---

### Post by Mark Phelps on 2011-04-21
Ubuntu 11.04 is still in testing.  This thread is reserved for Ubuntu versions that have already been released.

You will get better and faster responses if you post your 11.04 questions to the Natty Development forum.  That is located at: Other Community Discussions --> Development & Programming --> Natty Narwhal Testing and Discussion

thanks

---

