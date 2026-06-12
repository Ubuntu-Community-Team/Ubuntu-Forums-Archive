---
title: "VNC problems"
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by Living2007 on 2010-03-01
I am trying to my ubuntu machine from my Macbook via VNC, and i know it works but I want to view the login screen and sign in! But the VNC server program on the Ubuntu machine will not launch until someone signs in. There is only one user on it, I choose to do this for security reasons

What is a possible solution

---

### Post by suseendran.rengabashyam on 2010-03-02
Hi,

Try the following steps in your Ubuntu machine

1) Go to System->Preferences->Remote Desktop and uncheck "Allow other users to view your desktop"

2) Open the terminal and enter the following command
```
sudo apt-get install x11vnc
```

3) After you have installed 'x11vnc' go to the file /etc/rc.local and add the following line just before 'exit 0'
```
x11vnc -safer -nopw -once -display :0
```

4) Reboot the Ubuntu Machine and see whether you can VNC from your MacBook.

Hope this helps.

---

### Post by Living2007 on 2010-03-02
Cheers, i'll give it a try :)

---

### Post by juancarlospaco on 2010-03-02
Use NxNoMachine...

---

### Post by Living2007 on 2010-03-02
Problems. It will only display when I log in still. I want the VNC to be available when the machine boots, not when I log in.

---

### Post by krunge on 2010-03-03
Have a look in this thread:  [http://ubuntuforums.org/showpost.php?p=8896377&postcount=4](http://ubuntuforums.org/showpost.php?p=8896377&postcount=4)

---

### Post by Living2007 on 2010-03-04
OK, I;ve just discovered that I can launch the X11 apps that i need through SSH an view them on my Mac. Now my only concern is getting Ubuntu to recieve an IP address during boot. How can I do this?!

---

