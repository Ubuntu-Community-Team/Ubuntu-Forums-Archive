---
title: "Adding desktop packages"
date: 2012-06-20
forum: Mythbuntu
---

### Post by timswait on 2012-06-20
I have one machine that I use as a TV and as a desktop computer, so I wanted to add the kubuntu desktop files to my Mythbuntu installation, so I checked the "Kubuntu desktop" in MCC and clicked apply. It has installed a lot of files, but the desktop still looks exactly the same (i.e. like xfce not kde) and although I have applications like Dolphin, I also still have Thunar. Also, none of the kde applications run properly, they don't seem to be given the permissions, for example dolphin says "Configuration file "/home/trilby/.kde/share/config/dolphinrc" not writable.
Please contact your system administrator." Gwenview etc do similar. Is there something else I need to do to make my desktop more kde and less xfce?

---

### Post by klc5555 on 2012-06-21
Since you've installed the KDE desktop and all related files, you should be able to choose "KDE" from the Session Drop-down Menu before you login.

---

### Post by timswait on 2012-06-21
OK, thanks, that's solved one problem :) I had auto log-in enabled so I didn't get the drop down option. Disabled auto log in in lightdm.conf and got the drop down, so I could log in on kde. I've now re-enabled auto log in and it's still logging me into kde which is good :)
However the problem with the permissions is still there :( 
Now as soon as I log in via kde I get a whole list of applications complaining along the lines that they can't write their configuration files. How do I give these applications the necessary permissions?
Cheers

---

### Post by klc5555 on 2012-06-21
First guess: make sure the .kde directory (and all its subdirectories) in your user directory exist and have owner:group set as [you]:users.   In particular .kde/share/config/

---

### Post by Lester_Burnham on 2012-06-22
Hi,

Would you be better off, by installing Kubuntu first and then just install mythbuntu-desktop?
Just curious.

Lester

---

### Post by timswait on 2012-06-22
klc: thanks for that, the .kde directory did exist and permissions were correct, but it turned out that some of the files within it had their owner set to root. Changed these to my username and it now all works, woohoo! :)
Lester: In hindsight you may have been right, but it now seems to be working well and doing what I want so I'm happy.

---

