---
title: "gnome-network-admin"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by krishna3456 on 2009-05-20
I am noob and just installed ubuntu 9.04
I downloaded gnome-network-admin package and installed on linux.
When i run System>administrator>Network
Iam getting an error called 
(network-admin:22818): Gtk-WARNING **: Unknown property: GtkComboBox.items

I could not see the unlock button on the network applet that is opened up thus it is not allowing me to change the settings of my internet and iam not able to connect to the internet.

i also tried using terminal and used sudo network-admin command.It asked for password and i gave it and it opened the window and the same problem there after.

How do i solve this problem?plz someone give me a solution.Without internet i cannot use ubuntu os.

---

### Post by dmizer on 2009-05-20
Bug is here: [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/227383](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/227383)

Fix is here: [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/227383/comments/20](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/227383/comments/20)

google knows all :guitar:

---

### Post by krishna3456 on 2009-05-21
Demizer that didnt worked even after i changed setting as expalined in your fix the problem ppersisted exactly the same.

When i run network admin command i got this error
(network-admin:xxxx):Gtk-WARNING **.Unknown property:Gtk ComboBox.items

and i could not se the unlock option in the network-admin applet which is opened after that command.

---

### Post by dmizer on 2009-05-21
Are you running a highly customized theme?

---

### Post by krishna3456 on 2009-05-21
No i just installed the ubuntu 9.04 and i didnt change anything yet.So iam using default theme available on ubuntu 9.04 version.

---

### Post by dmizer on 2009-05-21
Found this: [https://answers.launchpad.net/ubuntu/+source/gnome-system-tools/+question/32334](https://answers.launchpad.net/ubuntu/+source/gnome-system-tools/+question/32334)

One of the suggestions was to run this command:
```
sudo apt-get install --reinstall dbus
```

---

### Post by krishna3456 on 2009-05-21
As internet is not connected in gnu/linux i tried to download that package from debian packages  and when i tried to install in ubuntu it sait the later version already exists so did not install.

This internet connection is working well when i used ubuntu 8.x version but now the 9.04 version removed that facilty and asked to download a package explicitly from debian which has caused this problem.

What could i possibly do if i want to connect internet in any other way.I use ADSL 2 modem and i connect to a broadband connection using this modem which is working fine on windows xp.

plz suggest me the alternatives for connecting to internet.

---

### Post by dmizer on 2009-05-21
What kind of connection are you attempting to make? Wired or wireless?

---

### Post by krishna3456 on 2009-05-21
Wired connection.

---

### Post by dmizer on 2009-05-21
Okay, are you connected to a router, is it dhcp or static, or do you need to make a pppoe dialer?

And, do you know which device (eg eth0) is your network adapter?

---

### Post by krishna3456 on 2009-05-21
iam using a router.iam on a dynamic type of connection.I have to dial my netwrk when ever i want to connect to internet.I think eth0 is our network adapter.
This link would explain you about the connection iam using.
[http://www.indiabroadband.net/linux/10828-how-configure-bsnl-broadband-connection-ubuntu.html](http://www.indiabroadband.net/linux/10828-how-configure-bsnl-broadband-connection-ubuntu.html)

---

### Post by dmizer on 2009-05-21
If you have a router, your router should handle the authentication for you. Is this not the case? Try this:

```
sudo dhclient eth0
```

---

### Post by krishna3456 on 2009-05-22
> **dmizer said:**
> If you have a router, your router should handle the authentication for you. Is this not the case? Try this:

```
sudo dhclient eth0
```


dmizer even that command didnt work.I mean it didnt change any thing.
But now i switched from 9.04 version to 8.04 version  in which i had configured internet quite easily.
In 8.04 version System>Administrator>Network is working quite good and is it possible that i can copy some files from that and paste in the new 9.04 version such that the network applet works well in this also.
 
And can u suggest the network monitoring tools which help me in monitoring the network speed and the amount transferred on the internet.:D

---

### Post by dmizer on 2009-05-25
You can download the deb package for the Jaunty version of gnome-network-admin here: [http://launchpadlibrarian.net/24739956/gnome-network-admin_2.22.2-0ubuntu3_i386.deb](http://launchpadlibrarian.net/24739956/gnome-network-admin_2.22.2-0ubuntu3_i386.deb)

If it says you're missing dependencies, you can find and download them individually here: [https://launchpad.net/ubuntu/jaunty/i386/gnome-network-admin/2.22.2-0ubuntu3](https://launchpad.net/ubuntu/jaunty/i386/gnome-network-admin/2.22.2-0ubuntu3)

---

