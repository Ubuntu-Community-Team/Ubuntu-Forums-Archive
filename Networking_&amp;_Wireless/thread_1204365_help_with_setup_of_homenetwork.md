---
title: "help with setup of homenetwork"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by jcm1107 on 2009-07-04
Hi I have cable internet and a linksys wrt160 router and a computer that dual boots windows xp and Ubuntu 8.04. I want to setup this computer to host a network so my brother can get on the internet on his windows only computer. I mostly use ubuntu but use windows when I have to so I want to get the router to work no matter which os I am using at the time. I have got the router to work with windows xp but I don't know how I need to set my dual boot computer up to manage this network. If you need any more info just ask. Thanks

---

### Post by Boondoklife on 2009-07-04
Well all you should have to do is connect to the network in ubuntu and in windoes. Im not sure what the complication would be.

---

### Post by Iowan on 2009-07-04
Is your network set for static or (more likely) DHCP addresses.  *probably* your router is the DHCP server.  Will your brother's computer be connecting *through* your computer - or do they both connect to the router?

---

### Post by jcm1107 on 2009-07-04
> **Iowan said:**
> Is your network set for static or (more likely) DHCP addresses.  *probably* your router is the DHCP server.  Will your brother's computer be connecting *through* your computer - or do they both connect to the router?

My problem is when I plug the router to the cable modem and power cycle everything I can't connect to the internet. The connection to the router seems fine but no internet.I think I need my computer to host the network and control the router. I like to use ubuntu more than so I want to be able to set it up or find an application to control or be able to connect in ubuntu. The software that came with the router worked when I was using windows xp but now that I use ubunt i don't know how to set things up.Oh I forgot both computers connect though the router but I think the instructions said one had to be a host if I remember right.

---

### Post by Iowan on 2009-07-04
Sounds like the modem and/or router needs to be configured to work with the other.  Ubuntu *can* be configured to act as a router (or share internet connection), but this wouldn't help when you boot the machine into Windows.

---

### Post by Sky Pixie on 2009-07-04
If I understand correctly, the following is a diagram of your network.

Cable Modem > Router > Ubuntu/Windows Computer
[COLOR="White"].....................................[/COLOR]> Windows Computer

Both computers connect to the router through an ethernet cable, yes?

The router, if configured with DHCP, serves both computers a local IP address using DHCP.

There should be no need to cycle the cable modem and router when booting from Windows to Ubuntu or vice versa.

I think it's a good idea to start with a clean slate.

1.  Turn off the Ubuntu/Windows computer.
2.  Unplug the router.
3.  Unplug the cable modem.
4.  Connect the router to the dual boot Ubuntu/Windows computer.
5.  Connect the router to the Windows-only computer.
6.  Wait twenty seconds for the ISP to detect the disconnected modem
7.  Plug in the cable modem.  Wait for all lights to illuminate.
8.  Plug in the router.  Wait ten seconds.
9.  Turn on the Ubuntu/Windows computer and boot into Ubuntu.

Check the status of the network connection by opening a terminal/command line and enter the following:
```
ifconfig
```
There will be an IP address assigned to, I assume, eth0.  You should be able to access the internet from within Ubuntu.  If not, post the output of ifconfig as well as the contents of the network interfaces file /etc/network/interfaces.
```
gedit /etc/network/interfaces
```
The above command uses the text editor gedit to open the file interfaces.

---

### Post by jcm1107 on 2009-07-04
the above is exactly what I am trying to do I will try it now and post back if it worked or not. Thanks very much.

---

### Post by jcm1107 on 2009-07-05
> **Sky Pixie said:**
> If I understand correctly, the following is a diagram of your network.

Cable Modem > Router > Ubuntu/Windows Computer
[COLOR="White"].....................................[/COLOR]> Windows Computer

Both computers connect to the router through an ethernet cable, yes?

The router, if configured with DHCP, serves both computers a local IP address using DHCP.

There should be no need to cycle the cable modem and router when booting from Windows to Ubuntu or vice versa.

I think it's a good idea to start with a clean slate.

1.  Turn off the Ubuntu/Windows computer.
2.  Unplug the router.
3.  Unplug the cable modem.
4.  Connect the router to the dual boot Ubuntu/Windows computer.
5.  Connect the router to the Windows-only computer.
6.  Wait twenty seconds for the ISP to detect the disconnected modem
7.  Plug in the cable modem.  Wait for all lights to illuminate.
8.  Plug in the router.  Wait ten seconds.
9.  Turn on the Ubuntu/Windows computer and boot into Ubuntu.

Check the status of the network connection by opening a terminal/command line and enter the following:
```
ifconfig
```
There will be an IP address assigned to, I assume, eth0.  You should be able to access the internet from within Ubuntu.  If not, post the output of ifconfig as well as the contents of the network interfaces file /etc/network/interfaces.
```
gedit /etc/network/interfaces
```
The above command uses the text editor gedit to open the file interfaces.

This got me on the internet with the dual boot computer but not my brothers windows, so what would I need to do now? THANKS!!! I also need to set the security on the router it is wireless.

---

### Post by jcm1107 on 2009-07-05
Ok, I have my network all setup. Thanks for everyones help!!

---

### Post by Sky Pixie on 2009-07-05
I am not familiar with the WRT160 so I can't give you step by step instructions.

To access the router, open your internet browser of choice and enter the following in the address bar:
```
http://192.168.1.1
```

You will be prompted for a username and password.  According to [this](http://forums.linksys.com/linksys/board/message?board.id=Wireless_Routers&message.id=109651) link, leave the username field blank.  Enter the following in the password field:
```
admin
```

I remember my WRT54G requiring the username field be
```
admin
```
and the password field blank.  Or enter admin into both the username and password fields.  One combination will work.

I don't know what the user control panel looks like therefore you will need to check every tab.

At the very least:
1.  Make sure the router is set to DHCP.

2.  In the SSID field, enter a random combination of characters such as
```
ke49?dL38$9dW
```
Write this down and keep it in a safe place.

3.  Turn the SSID broadcast to OFF.  If the wireless network is unused, disable it.

4.  Enter a wireless network password comprised of random characters.  Write down this password.

The previous three actions makes it very difficult for others to detect and leech your connection.

5.  Change the router name to a random string of characters different from the SSID and wireless password.  Write down this name.

6.  Enter an obscure router username.  Write down this username.

7.  Change the router password to a random string of characters different than the SSID and wireless password.  Write down this password.

If someone in your family wants to connect to the router using the wireless connection, they will need to enter the SSID and wireless password in whatever application they use to set up the wireless connection.

To connect your brother's computer to the router, I think you click on Control Panel and then Networking.  There are icons within the window displaying a network connection.  Double click on the icon to open a new window.  Within that new window is an option to restart the network.  If there are no icons, you will need to add a network icon.  I have not used Windows for months therefore someone else will need to help you if the above did not work on the Windows computer.

For future use, instead of restarting the cable modem and router, from Ubuntu enter the following in a terminal/command line:
```
sudo /etc/init.d/networking restart
```
The above command restarts the network for Ubuntu.  Restarting the network requires superuser privileges so we use sudo to gain those privileges.  You may check the network status by entering
```
ifconfig
```

---

