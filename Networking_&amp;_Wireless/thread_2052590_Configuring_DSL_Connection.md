---
title: "Configuring DSL Connection"
date: 2012-09-03
forum: Networking &amp; Wireless
---

### Post by chriswt on 2012-09-03
[FONT=Times New Roman][SIZE=3]I installed Ubuntu 12.04 SERVER on a new HP Pavilion p6-2117c desktop PC.[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]I am a beginner in Linux! This is my first install.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The install went well, no errors and I selected to have LAMP installed.[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]One thing that is keeping me from moving foreword for now is that:[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]I cannot connect to the Internet. I would like to use the command apt-get but I need to know how to connect the Internet connection.[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman]Please Help[/FONT]

---

### Post by ajgreeny on 2012-09-03
Wireless or cable connection?
Modem or router?
If wireless, what wireless adapter?  Run ```
lspci
``` if you're not sure.
Please show the output of ```
ifconfig
```

---

