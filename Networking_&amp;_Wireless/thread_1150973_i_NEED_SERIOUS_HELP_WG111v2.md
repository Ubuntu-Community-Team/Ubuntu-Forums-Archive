---
title: "i NEED SERIOUS HELP WG111v2"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by zenial on 2009-05-06
OK SO I MANAGED TO CHANGE THE DRIVER FOR THIS ADAPTER USING "NDISWRAPPER" AND NOW I CANT SEEM TO GET IT TO WORK IN ITHER UBUNTU OR WINDOWS>..

IS THERE A WAY I CAN "RESET" MY ADAPTER??  :confused::confused::(:(

---

### Post by rvrijmoed on 2009-05-06
Hi, I had the same issue and how I got it back to work was selecting a driver in ndiswrapper (using front-end) that didn't match my specific hardware version. After reboot Ubuntu automatically switched back to the default driver. I also tried uninstalling ndiswrapper, but this didn't help. Not an ideal solution but doing this I managed to get my network connection up and running again. If anyone else has suggestions how to reïnstall default network drivers, I am interested to know.

---

### Post by Crafty Kisses on 2009-05-06
> **zenial said:**
> OK SO I MANAGED TO CHANGE THE DRIVER FOR THIS ADAPTER USING "NDISWRAPPER" AND NOW I CANT SEEM TO GET IT TO WORK IN ITHER UBUNTU OR WINDOWS>..

IS THERE A WAY I CAN "RESET" MY ADAPTER??  :confused::confused::(:(

If you remember the driver you installed through ndiswrapper, you can run the following command and it will remove the driver:
```
sudo ndiswrapper –e <drivername>
```
Just for example, if the driver name was "b43" you would do the following:
```
sudo ndiswrapper –e b43
```

---

