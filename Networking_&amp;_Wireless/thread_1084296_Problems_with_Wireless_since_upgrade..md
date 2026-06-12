---
title: "Problems with Wireless since upgrade."
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by jfinner1 on 2009-03-01
I just upgraded from Hardy to Intrepid a few days ago. Ever since, I have been having problems with my wireless. When I boot up my computer, it acts normal, auto-connects like normal, and is fine. If I disconnect from the wireless network, by going out of range or un-checking the "Enable Wireless" option, and then try to reconnect, it won't connect and won't show any available wireless connections. If I hibernate the computer, and then wake it up in range of a wireless connection, it will show the available networks, and "Attempt to connect" to my automatic network for a while. Then it will pop up asking for the password, which is saved, so I'll tell it to connect, and it will do the same thing, Attempt to connect, ask for password, hit connect.... It will continue doing this until I restart the computer. I have no idea what's going on, or how to fix it. Any help would be greatly appreciated. Thanks in advance.

---

### Post by Atrophy on 2009-03-01
I just recently solved a very similar problem. Here are the steps I took:

First, find a wired connection. Connect to that, and then run your package manager and install all updates and program fixes and whatnot. Then open terminal and run 'sudo apt-get install linux-backports-modules-intrepid-generic' and reboot.

---

### Post by jfinner1 on 2009-03-02
Followed above advice, and a bit of improvement, but not fixed. Now, if I un-check and re-check the "Enable Wireless" box, it will re-connect to the automatic network. I can't check the whole 'going out of range' thing right now, because even if I turn my router off, I can pick up my neighbor's connection, so I'm not sure if there's any change there. But the problem with Hibernating the computer is still there. Thanks for the help so far.

---

### Post by Atrophy on 2009-03-02
Make sure your connections under the wireless tab in 'edit connections' are set to NOT connect automatically. 

Also, as far as the hibernation issue goes: When you installed Ubuntu did you install with the "Inside of Windows" option? I know that when I tried that a message came up that specifically stated hibernation is not supported in this mode.

---

### Post by jfinner1 on 2009-03-02
Question, why would I want it to not connect automatically? Just wondering. As for your question, I'm not sure I know what you mean when you say "inside of Windows". I have no clue if I installed it that way or not. I was having some problems with my computer hibernating before the upgrade, but those problems went away when I upgraded. Before the upgrade, every time I'd tell the computer to hibernate I would have to wait for a minute until I saw two lines of text pop up on a black screen. it was something like "Unable to access KDE" and "Unable to access AUX" or something like that... I'm not sure, I only really paid attention to it the first few times it happened. I'd hit enter, and the computer would hibernate. When I woke it up I would get the same message, hit enter, it would wake up like normal. Not sure if that will help any...

---

### Post by Atrophy on 2009-03-02
Personally i've never any issues with the automatic connection feature. Some friends of mine have though. They said what was happening was that every connection was set to connect automatically, thus Ubuntu was trying connect to all networks continuously, which could be a problem. What he specifically told me was, "This last one was something I had to deal with recently - there were like 7 networks in range (!?) and it kept trying to connect to all of them! I had to explicitly configure it to not try and connect with each of the other networks (kinda dumb setup, but it was a one-time thing)."

As for the "Install inside of Windows", when you put in your LiveCD to install/upgrade it is one of the installation options given to choose from. That specific option will go on to tell you that some features (specifically Hibernation) do not work, as well as disk performance being decreased. The first time I installed I accidentally chose this option without even realizing it. I hibernated and never returned. Whoops! After realizing the mistake I had to reinstall. Thinking back, I know that when I installed Ubuntu under this option I never had to boot from the LiveCD, and it just went ahead and did the whole installation process with Windows still running.

---

### Post by jfinner1 on 2009-03-02
I've never had a problem with the auto connect. I think I can confidently say that I did not install "inside of Windows". I'm still having the problem connecting after hibernation. Any other ideas?

---

