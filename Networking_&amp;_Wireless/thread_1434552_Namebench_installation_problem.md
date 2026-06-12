---
title: "Namebench installation problem"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by alexeix on 2010-03-20
Hi,

I'm trying to install Namebench and although I've successfully gone through the following process, I can't get the application to install (it doesn't appear in any menus and can't be added to a menu manually):

[http://www.ubuntugeek.com/increase-your-internet-speed-with-namebench.html]("http://www.ubuntugeek.com/increase-your-internet-speed-with-namebench.html")

It seems to run from the Terminal, but the output doesn't make much sense, so I want a GUI.

Can anyone assist please?
Thanks.

---

### Post by RobsonGrangeiro on 2010-05-05
Hi,

A. Are you installed "python-tk" package?
B. After untar the **[COLOR=#ff0000]namebench[/COLOR]**.tar file, are you run this installation command?
[FONT=Courier New]
sudo python setup.py install[/FONT]

If the two steps are ok, follow this other steps.

To execute (after installation process) try this:

1. Go to folder /usr/local/lib/python2.6/dist-packages/
2. Verify if the file "**[COLOR=#ff0000]namebench[/COLOR]**.py" exists. 
3. If exists, you can run this command:
[FONT=Courier New]
sudo python ./namebench.py[/FONT]

This work with me, good luck!

---

