---
title: "wicd icon dissappear after restart"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by sham08 on 2009-11-18
Hello.Yesterday I shut down my PC before I went to sleep,and this morning when I restarted the PC all went well except the usual wicd icon on my upper panel disappeared.Oddly,I can connect and browse the Internet without any problem.I thought that I can make the icons reappeared again by reconfigured on the GUI,but when I clicked on the only wicd icon that left on my desktop nothing happened.Is there any way I can get back the GUI and icon back on my desktop? Any help will be much appreciated.

---

### Post by lidex on 2009-11-18
Try right-clicking on your panel, select "add to panel" and from list highlight "notification area" and click "add".

---

### Post by crucialhoax on 2009-11-18
When Wicd is installed it places an icon in: Applications > Internet > Wicd. In there click on Wicd to start it up, when it pops up click on preferences > general settings tab > make sure auto reconnect is checked as well as display notifications. Hope this helps.

---

### Post by sham08 on 2009-11-18
Thanks lidex and crucialhoax for responding.Neither of both suggestions works.lidex tips for adding the notification area return nothing,while crucialhoax's tips gave me a brief/flash of Wicd tab in the bottom panel and then vanished.By the way,I've right clicked the wicd icon on the quick start panel and chose the Wicd launcher properties,and oddly in the comment section it says 'start the Wicd client without system tray icon'.I wonder if it was the problem source.Any suggestion?

---

### Post by lidex on 2009-11-18
> **sham08 said:**
> I've right clicked the wicd icon on the quick start panel and chose the Wicd launcher properties,and oddly in the comment section it says 'start the Wicd client without system tray icon'.I wonder if it was the problem source.Any suggestion?
Could very well be. What is the command for that launcher?

---

### Post by sham08 on 2009-11-19
Sorry to all whom respond to my thread (including you,lidex).For the moment I'm out on holiday and I'll only be back on Tuesday.The problem (as mentioned in my thread) is still there.Looking ahead to solve it.Anyway,thanks guys.

---

### Post by sham08 on 2009-11-25
Sorry guys and I'm back.Okay for lidex,the command is 'wicd-client--no-tray'. Is it possible if I revert the command and how should I do it?Thanks in advance for any response.

---

### Post by lidex on 2009-11-25
I'm thinking edit out "--no-tray" from the command.

---

### Post by sham08 on 2009-11-26
Thanks lidex,but still nothing happen.And another development,there's no sign of wicd exist in 'System Monitor' like before.

---

### Post by lidex on 2009-11-26
Enter key combo Alt+F2. In the run application dialog enter "wicd-client" and press enter. If that works you'll just need to edit the command in "system>preferences>startup applications.

---

### Post by sham08 on 2009-11-26
Making progress.The icon appears after Alt+F2,but still can't open the GUI. It says 'Wicd daemon unreachable' and message 'Wicd error-could not connect to Wicd's D-Bus interface.Check the Wicd log for error messages'.

---

### Post by lidex on 2009-11-27
Would imagine there is a client and daemon and the daemon needs to autostart at boot. Try system>administration>services and/or system>preferences>startup applications. In the latter case you'll need the command. Test this using Alt+F2: 
```
wicd-daemon
```

---

### Post by sham08 on 2009-11-27
Tried Alt+F2 and wicd-daemon,and get error message 'could not open location 'file:///home/sam1430/wicd-daemon'.'Error stating file 'home/sam1430/wicd- daemon': No such file or directory.I wonder where had gone the daemon file/ folder when I first installed it (wicd).

---

