---
title: "Can't get Network Manager icon"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by beachgirl on 2010-01-04
So I just installed Ubuntu 9.10 Netbook Remix on my son's new Dell Mini 10v that came with Windows 7 Starter. Once the install was done and I logged onto Ubuntu, I had this message that I had a "very bad disk", but everything was working in perfect order in both OSs... Got rid of the message, then tried to establish a connection to my wireless network - and couldn't find where to do this. 

After researching, I found out that the Network Manager icon was missing from the panel. So I tried some suggestions I found here - removing and re-adding the panel, checked to see that the command line in the startup application list was correct, etc. I am new to this OS (I'm mostly a Mac user), and not so familiar with terms such as "terminal" etc. I don't know how to go about updating the OS without an internet connection. 

Help please? Thanks!!!!

---

### Post by beachgirl on 2010-01-07
Nobody has an answer to my question??? Am I going to have to give up on Ubuntu Netbook Remix and just do the full upgrade to Windows 7??? :(

---

### Post by iponeverything on 2010-01-07
Go to 

Application -> Accessories -> Terminal

At prompt type:

```

nm-applet&
disown %1

```

does network manager show up?

You can also try grabing 9.04 and using it instead 9.10, it has been working better for some people..

just go to [http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors) 
click on any of mirrors and you can get the 9.04 iso's.

---

