---
title: "Uninstall Songbird"
date: 2009-01-22
forum: Multimedia Software
---

### Post by Squegee on 2009-01-22
I am trying to completely uninstall songbird from my kubuntu computer, the songbird package does not exist in synaptic so I can not use that. The songbird website gives me instructions to plug this into the terminal
      rm -rf ~/.songbird2
I am new to linux and the line they give me does nothing. I have tried 
      sudo rm -rf ~/.songbird2     
                and
      sudo apt-get rm -rf ~/.songbird2
Neither do anything. Can someone please explain how I correctly execute commands like the one given and others that I can't just copy and paste into the terminal.

---

### Post by rifak on 2009-01-22
the instructions from songbird are fine. the rm command is a remove/delete command. the other -rf (i think they are called flags, but i may be wrong) just say to delete the whole directory and everything inside. .songbird2 is a hidden folder within the home directory that is placed when you setup songbird (to list all your hidden folder within home, type "ls -a" without the quotations). when you type that, it did do something. it deleted the .songbird2 hidden folder that was in your home directory...it just didn't give you feedback to tell you that...but it did work.

 you are right when you say nothing happens when you use apt-get (also referred to as synaptics) on songbird because it wasn't and can't be installed through synaptics. also, when getting rid of songbird, go to the actual application directory where your songbird app is located and delete that also. hope this helps

---

