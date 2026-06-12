---
title: "Modem installed but wont dial out"
date: 2006-02-08
forum: Networking &amp; Wireless
---

### Post by Rashid on 2006-02-08
Hi

After many hours or struggling, I managed to install my winmodem. When I ran the wvdial.conf it detected the modem. Hoewever when I try to dial to the internet, nothing happens. I dont even hear the number being dialled. When I use wvdial, it says that it is waiting for carrier. My phone line is Tone dialling. Could someone please help.

---

### Post by z|x on 2006-02-08
I would like to know how you installed your winmodem. please tell.

---

### Post by Razorback on 2006-02-08
This maybe a silly question but did you edit your wvdial.conf file to add your isp and logon information?

---

### Post by Rashid on 2006-02-09
If you want to install your winmodem, you need to download a tool called scanmodem. Once you download scanmodem comile and run it, you can copy it to the desktop. Follow the instructions on this page [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

I configured the file wvdial.conf. Strangely f I set the number to pulse dial, the line dials out but does not connect. If its set to tone dialling, the modem does not even dial out. My line is definitely a tone line.

---

### Post by StefanoCole on 2006-02-09
Rashid, instead of wvdial you could try pppconfig. Open a terminal and do:
sudo pppconfig
Enter the information as needed. Use the name provider for your default connection. Add your user to the dip group using the advanced options.
Save and exit.
sudo pon
If you get nothing or if you run into trouble, open another terminal and do:
sudo tail -f /var/log/messages

This may give you an up-to-the-second idea of what is going on. Post the result in your question to the forum.
sudo poff hangs up.
You need to log out and back in for your user/group settings to be updated. You can then pon and poff without the sudo. 
Some people have said that pppconfig worked better than wvdial while some have said that wvdial was the only utility that could get them on the net. Go figure.

Bye, Stefano

---

