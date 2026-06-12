---
title: "Bluetooth Apple Keyboard and Trackpad"
date: 2015-05-25
forum: Mythbuntu
---

### Post by ashtangiman on 2015-05-25
I have just installed MythBuntu on my Mac mini (Snow Leopard . . . with integral slot loading DVD) and cannot get my wireless keyboard to auto connect after a reboot.  I have to quit MythTV, open a terminal, and on a wired keyboard run the command to connect:

sudo hidd --connect AA:BB:CC:XX:EE:FF

at which point the keyboard works fine (I'm using it right now).  But if I reboot it does not work.

So I installed bluetooth monitor (Blueman) which gives me a graphical bluetooth devices list.  When the keyboard is already connected it shows it, but without the trust icon.  I set it to trust the device, then reboot. At this point the myth TV screen will be up, and I get a dialog box to always accept, accept, or deny the wireless keyboard.  Nothing I do here will actually accept the keyboard.  I have to plug in the wired keyboard and then quit, type in the command to get the keyboard to connect.  This is less than optimal.

The trackpad is similar . . . I can connect it, it works now even, but a restart will not auto connect it.  I have a shell file with execute permission that I can run to get them to connect which I think I could somehow get to run at startup, but have not figured out the right way to do it so far.

Has anyone gotten this to work?  I have installed Ubuntu desktop thinking that it would help with configuration, but it does not seem to be.  My version is 14.04.2 LTS.

---

### Post by ashtangiman on 2015-05-25
I solved this by putting my hidd commands into /etc/init.d/rc.local.  Everything works correctly now, and I have put away the wired keyboard and mouse so that my living room looks good again :).  I don't know why the blueman application seemed to be the answer that worked for others that I found asking this question, but it did not work correctly for me, so I uninstalled it.

---

