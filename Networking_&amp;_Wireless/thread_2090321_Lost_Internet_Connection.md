---
title: "Lost Internet Connection"
date: 2012-12-01
forum: Networking &amp; Wireless
---

### Post by avanboekel11 on 2012-12-01
I'm running ubuntu 12.04. After turning my desktop off for a couple of days, I lost internet connection. 

I am new to linux, and I'm not sure how to solve this problem.

Thanks
AVanBoekel11

---

### Post by Sef on 2012-12-01
1) Did you update or make any other changes before you logged off?

2) Have you tried to start the computer again?

---

### Post by avanboekel11 on 2012-12-01
> **Sef said:**
> 1) Did you update or make any other changes before you logged off?

2) Have you tried to start the computer again?

I don't believe that I did any updates. And yes, I tried rebooting the computer.

---

### Post by USAGeorge on 2012-12-01
Have you checked the icon,,,top right side of screen,,,,,,the one just left of the volume icon? Does it say your connected or not.....

---

### Post by avanboekel11 on 2012-12-01
> **USAGeorge said:**
> Have you checked the icon,,,top right side of screen,,,,,,the one just left of the volume icon? Does it say your connected or not.....

it's an empty dark grey quarter circle. I also tried connecting it with an Ethernet cable, and that didn't work either.:confused:

---

### Post by Hank_The_Dog on 2012-12-01
Open up a terminal (ctrl+shift+t)

type the following
```
ifconfig
```
press enter

paste the results back here

---

### Post by avanboekel11 on 2012-12-01
> **Hank_The_Dog said:**
> Open up a terminal (ctrl+shift+t)

type the following
```
ifconfig
```
press enter

paste the results back here

How am I supposed to paste it online if I cant connect to the internet?

---

### Post by Hank_The_Dog on 2012-12-02
Touche! :lolflag: Sometimes you need to put the pipe down..

Anyway can you give us more detail on your network?

Are you connecting via wifi? What security does it have? 
You said you plugged in with an Ethernet cable, plugged into what?
Is there any way you can verify that it is the Ubuntu computer that is not working, and not your internet?
[I]IE: It works on your other computer/smartphone but not on your Ubuntu distro?
[/I]
Have you tried right-clicking on the icon? 
I believe you can open your network manager by opening a terminal and typing
```
network-manager
```

---

### Post by avanboekel11 on 2012-12-02
It's a desktop with a wireless card in it. I was previously only connected to the wifi, and that was working fine. When that didn't work, I plugged in an ethernet cable, and that didn't do anything either.

Other devices are working fine on the network.

The network-manager command did nothing.

---

### Post by Hank_The_Dog on 2012-12-02
Try this, plug ethernet cable in, and type the following:
*(What are we plugging in to? a router or modem?)*

```
sudo service network-manager restart
```

after that right click the gray quarter circle>Edit Connections
Wired Connection 1>Edit

Check the following: 

[LIST]
[*]That the box by connect automatically is checked
[*]Under IPv4 settings you should be using the DHCP method
[/LIST]




Can you see your wifi network whenever you rightclick the gray quarter circle?

---

### Post by avanboekel11 on 2012-12-02
> **Hank_The_Dog said:**
> Try this, plug ethernet cable in, and type the following:
*(What are we plugging in to? a router or modem?)*

```
sudo service network-manager restart
```

after that right click the gray quarter circle>Edit Connections
Wired Connection 1>Edit

Check the following: 

[LIST]
[*]That the box by connect automatically is checked
[*]Under IPv4 settings you should be using the DHCP method
[/LIST]




Can you see your wifi network whenever you rightclick the gray quarter circle?
I cannot see my wifi network under the quarter circle. It is not detecting any wired network. It is wired to a router.

---

### Post by Hank_The_Dog on 2012-12-02
There should be indicator lights on your network card. Are those lighting up whenever you plug it into your router?

if you run the ifconfig command 

under "eth0" do you get an ip for "inet addr"?

Does your computer have more than one network card?
Is there a switch to disable wireless on your computer?
Does your patch cable work with other devices?

---

