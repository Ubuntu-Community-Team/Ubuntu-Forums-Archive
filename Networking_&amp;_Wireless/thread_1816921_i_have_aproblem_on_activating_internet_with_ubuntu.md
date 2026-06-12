---
title: "i have aproblem on activating internet with ubuntu"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by egyption rebel on 2011-08-02
[SIZE=4][COLOR=Black]hello every body
firstly/ i want you to forgive me for my weak English 
my problem is/
i installed ubuntu 10.04 ltc after that i could not activate my connection with internet 
iam a memeber of a network (dsl)
my ip is 192.168.1.14 
my gateway is 192.168.1.1
i used ti put it manually when i was using windows 
how i can put my ip manually in ubuntu like windows ??????????????
another exeprecession for my question how i can activate my internet with the given information that i said ?????????? 
thank you
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
[/COLOR][/SIZE]

---

### Post by galtech on 2011-08-02
Hi egyption rebel, 

To manually configure your connection: 

In the top right of your screen you should see either 2 arrows (wired connection) or wave bands (wireless connection). 

- click on this icon
- click 'edit connection' 
- Press on wired or wireless tab
- select the connection name and press the Edit button to the right
- select the IPV4 tab and you will be able to enter your IP address, default gateway, net mask, and DNS addresses manually. 

Hope this helps. 
galtech

---

### Post by egyption rebel on 2011-08-02
thank you Mr galtech,
i did what you said exactly but with no benefit still no connection 
 can you help me?

---

### Post by dineshs on 2011-08-03
Wired or wireless?
Do you use a PPPoE dialler in windows?If yes try [this]("http://ubuntuforums.org/showpost.php?p=9611335&postcount=9")
Can you post the output of the following terminal commands (applications-accessories-terminal)```
sudo lshw -C network
ping 192.168.1.1 -c3
ping 4.2.2.1 -c3
```

---

