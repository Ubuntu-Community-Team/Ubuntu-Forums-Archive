---
title: "X11 connection rejected because of wrong authentication."
date: 2013-04-11
forum: Networking &amp; Wireless
---

### Post by ultimateabhi on 2013-04-11
I am using "ssh -X <ip>" to connect to my lab computer. But when I try to run any application it gives me this error : 
[I]
X11 connection rejected because of wrong authentication. 
[/I]
I have tried scouring the net and ubuntuforums, but none of the presented solutions have worked. I have tried the solutions posted here :[http://www.cyberciti.biz/faq/x11-connection-rejected-because-of-wrong-authentication/](http://www.cyberciti.biz/faq/x11-connection-rejected-because-of-wrong-authentication/) and here [http://blog.subaquatic.net/archives/lack-of-xauthority/](http://blog.subaquatic.net/archives/lack-of-xauthority/) . 

I have also tried removing openssh-server from the target machine using apt-get purge and reinstalling it. The same error repeats again.

Can somebody give me a hint for solving this problem?

---

### Post by ultimateabhi on 2013-04-11
EDIT: Turns out, the problem is not with the ssh connection or the X server. Its with the application I was running : gedit.

---

