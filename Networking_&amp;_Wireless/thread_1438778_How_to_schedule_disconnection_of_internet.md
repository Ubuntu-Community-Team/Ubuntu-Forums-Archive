---
title: "How to schedule disconnection of internet"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by Kbipinkumar on 2010-03-25
[COLOR=#000000][FONT=Times New Roman][FONT=arial]hi all, 

 i am using ubuntu 9.10.i connect to net through the gnome netwok manager via a mobile broadband connection. can anyone suggest any commands or tools with the help of which i can disconnect  the net at a preset time or after a fixed interval has expired. [COLOR=#000000][FONT=Times New Roman][FONT=arial]i know that by executing "poff" command in terminal  i  can disconnect the connection, but i want the same to happen 
automatically without any kind of user intervention  at a scheduled time[/FONT][/FONT][/COLOR]


thanks in advance
[COLOR=#000000][FONT=Times New Roman][FONT=arial]
 
[/FONT][/FONT][/COLOR]
[/FONT][/FONT][/COLOR]

---

### Post by jfparis on 2010-03-25
If you want it to happen regularly then you can use the cron daemon

If you want it to happen only one time you can use the "at" command.

---

### Post by chili555 on 2010-03-25
You might try:```
sudo at 2:00 PM poff &
```

---

