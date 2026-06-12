---
title: "help plz wireless wont work on my compaq laptop"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by dustin148 on 2009-09-29
ok i have my right driver i thnak im nto sure but i can see my router when i go to the wifi thing but when i try to connect i get an error the error message says

An error occured :
Can't set operating mode : Managed
Code : 16

---

### Post by Iowan on 2009-09-29
Connecting via Network Manager, or do you have configuration in */etc/network/interfaces* (aside from "lo")?

---

### Post by dustin148 on 2009-09-29
ok im trying to go to system amin than to rutil wlan manager i thank that is how i connect idk im kinda new but i have a  Atheros AR5007 wireless network adapter so ho can i get that to work on ubuntu linx? i mean i go to it n see my router n all but i get this error when i try to connect
 An error occured :
Can't set operating mode : Managed
Code : 16

---

### Post by dustin148 on 2009-09-29
help plz i cant connect heres my prob  ok im trying to go to system amin than to rutil wlan manager i thank that is how i connect idk im kinda new but i have a Atheros AR5007 wireless network adapter so ho can i get that to work on ubuntu linx? i mean i go to it n see my router n all but i get this error when i try to connect
 An error occured :
Can't set operating mode : Managed
Code : 16

---

### Post by overdrank on 2009-09-29
Please do not create multiple threads on the same issue. This can cause confusion. Threads merged.

---

### Post by dustin148 on 2009-09-29
ok i wont srry but no one is helping me

---

### Post by Iowan on 2009-09-29
> **dustin148 said:**
> ok i wont srry but no one is helping me

Thanks, I guess I'd be the "no one"... :)

---

### Post by cariboo on 2009-09-29
It looks like English is not your first language, so I'll try to make this easy. We need to know if your wireless device is detected and the driver loaded. Open an Applications-->Accessories-->Termianl and type:

```
sudo lshw -C network > network.txt
```

The above command will list all of your network devices and tell us whether the drivers are loaded or not. The above command also will create a text file called network.txt. You can copy the text file to your Windows partition, or transfer it to whatever computer you are using to log on here. Paste the text file in your next post.

Edit: All of us here are volunteers, please don't bump your threads until 24 hours has elapsed. It may be that the person that can answer your question just hasn't seen it yet.

---

