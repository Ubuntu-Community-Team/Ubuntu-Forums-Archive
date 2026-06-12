---
title: "MAC Adress in Ubuntu"
date: 2006-04-27
forum: Networking &amp; Wireless
---

### Post by vanalex on 2006-04-27
Hello everybody! Can anyone tell me how can i change my MAC Address in Ubuntu?I just don't want to show my real MAC Address on the net but a fake number i want. Can i do this? Thank you very much for reading my topic...

vanalex

---

### Post by Qrk on 2006-04-28
Yes, the command is:

```
sudo ifconfig eth0 hw ether XX:XX:XX:XX:XX:XX
```

Where the X is your new mac address and assuming you use eth0. After this you'll probably have to reconnect using,

```
sudo dhclient
```

If you get an error/it doesn't connect, edit your /etc/network/interface file

```
sudo gedit /etc/network/interfaces
```

add this line right above the line containing "auto eth0" (again, assuming your using eth0)
```

hwaddress ether XX:XX:XX:XX:XX:XX

```

Now it should connect using the new MAC address automatically at startup.

---

### Post by vanalex on 2006-04-28
Thank you very much for your help..

vanalex

---

### Post by fallencan on 2006-05-08
i have a related question about this problem so i didn't start another tread. i now i can change my mac adress after system boots normally. but i have to do this every time i start my computer. is there any command makes this change for me every time? there is an option in windows so i don't have to change it every time i start my comp.

---

