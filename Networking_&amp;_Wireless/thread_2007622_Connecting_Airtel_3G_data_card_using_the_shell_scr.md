---
title: "Connecting Airtel 3G data card using the shell script they provide is inconsistent"
date: 2012-06-21
forum: Networking &amp; Wireless
---

### Post by daudiam on 2012-06-21
I have an Airtel 3G data card (from Huawie). I opened the Airtel folder that pops up when we insert the device and copied the contents into another folder. From there, I ran 
```
 sudo ./install_linux
```The script ran and said that it has been correctly installed but it wasn't able to find '/dev/ttyUSB'. When I ran the script again, it showed the same message but then went on to say that the installation was complete. It then opened up an Airtel window where I was able to press the 'Connect' button. Although I wasn't able to access the net for some reason, I have not been able to get the same Airtel popup again when I go to Applications -> Internet -> Airtel or by running the script again (it says that it is already installed)

---

### Post by daudiam on 2012-06-22
These are the steps that worked for me :

1. After inserting the AIrtel 3G data card, wait for sometime and then open the terminal and type :
```
cd /media
ls

```You should see a folder named Airtel there. If not, then the device hasn't been detected.
2. 
```
cd Airtel
cd Linux
sudo bash  install
```

3. A script will ask you whether you want to accept the default installation location. Just press enter to accept the default. Wait for the script to finish (till it says 'Press any key to exit')

4. An Airtel dialog box will open up from where you can connect to the net.

5. Next time you insert the device, the Airtel dialog box will come up automatically.

Hope that helps others

---

### Post by vasa1 on 2012-06-22
@daudiam,
Nice to know the Airtel 3G card is working for you. If I come across queries, I'll link to your post. If you would be so kind, do keep us updated on how things play out for you especially if and when you move up to 12.10.

---

### Post by krishnendra89 on 2013-03-06
[h=2]i AM NAVE USER OF UBUNTU 
So How to **connect iball DATA CARD in ubuntu 12.10** .
[COLOR=#222222]When i cnnect device it detect but not open also .[/COLOR][/h]

---

