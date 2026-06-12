---
title: "cat &amp; telnet"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by michaelvh on 2010-05-10
hello,

I need some help on using a file with the cat command.  I want to set up a telnet connection with a network device with the ip-adress 10.3.0.1.  Just executing the command 'telnet 10.3.0.1' gives a menu.  For example, to show the help of the menu, you need to type '?'.

Now I want to go through the menu with commands (like '?') that are in a file. For this I want to use the command:
cat filename | telnet 10.3.0.1

When I try this, the telnet connection is established, but then it closes immediately afterwards.  So I suppose something's wrong with the file.  But I have no idea what the file should look like.  For example, do you need to mention the enters after a command in a certain way?

just to be clear: the command in the menu that I want to execute are:
"?" -> enter
"projector" -> enter
"exit" -> enter


thanks in advance,

Michaël

---

