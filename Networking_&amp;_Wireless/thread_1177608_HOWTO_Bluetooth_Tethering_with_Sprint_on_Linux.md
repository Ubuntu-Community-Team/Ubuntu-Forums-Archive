---
title: "HOWTO: Bluetooth Tethering with Sprint on Linux"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by zukakog on 2009-06-03
After having to try to remember how to setup bluetooth tethering every time I tried out a new distro (Ubuntu derived, of course) for my netbook, I decided to document the procedure, for myself and others.

_My setup_
Netbook:     Asus EPC 1000HE
Cell Phone:  Samsung a900m
Distro:      Various, based on Ubuntu 9.04 (Jaunty)


**Assume all code is to be entered into a terminal, not a run dialog!!!**

[list=A]
  [*]Pair cell phone with computer.
    [list]
      Make sure you have bluetooth enabled on your phone.
    [/list]
    [list]
      Make sure your phone is discoverable
    [/list]
    [list]
      Make sure your computer has some bluetooth manager installed.
      [list]
	I believe most Ubuntu flavors have bluetooth utilities installed, but if not, you can install them easily.```
sudo aptitude install bluetooth bluez bluez-gnome bluez-utils
```
      [/list]
    [/list]
  
  [*]Configure phone as modem.
    [list=1]
      [*]Find your phone's MAC address```
hcitool scan
```
	[list]You should see something like the following. The string of numbers and semicolons is your MAC address.```
Scanning ...
	00:FF:33:CC:66:AA	a900m
```[/list]
      [*]Find which channel your phone uses for dialup networking. **Replace the fake MAC address with your own.**```
sdptool browse 00:FF:33:CC:66:AA
```
	[list]Look for the section labled "Service Name: Dialup Networking" and take note of the channel number. My phone uses channel 4.```
Service Name: Dialup Networking
Service RecHandle: 0x10003
Service Class ID List:
  "Dialup Networking" (0x1103)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 4
Profile Descriptor List:
  "Dialup Networking" (0x1103)
    Version: 0x0100
```[/list]

      [*]Edit rfcomm.conf.```
sudo gedit /etc/bluetooth/rfcomm.comf
```
      [list]Uncomment the document (remove the #'s)[/list]
      [list]Change bind to yes.[/list]
      [list]Enter your MAC address as the device.[/list]
      [list]Change the channel to the one your phone uses.[/list]
      [list]Change the comment to reflect your device (I use my phone model, but you can use anything)[/list]
      [list]Save and close[/list]
      [list]Mine looks like this:```
rfcomm0 {
	# Automatically bind the device at startup
	bind yes;

	# Bluetooth address of the device
	device 00:FF:33:CC:66:AA;

	# RFCOMM channel for the connection
	channel	4;

	# Description of the connection
	comment "a900m";
}
```[/list][/list]
  [*]Configure Dialup Networking using gnome-ppp (you could use kppp or wvdial also. Just use the same settings that are explained here)
    [list=1][*]Install gnome-ppp```
sudo aptitude install gnome-ppp
```
	    [*]Edit menu entry to run as superuser.
	      [list]Depening on how you access the Gnome PPP icon, you can either right click on the icon and select properties, or use gedit.```
sudo gedit /usr/share/app-install/desktop/gnome-ppp.desktop
```[/list]
	      [list]change "gnome-ppp" to "gksu gnome-ppp", without the quotes.
	    [*]Launch Gnome PPP.
	      [list]If you aren't asked to enter your password, make sure you did the previous step correctly.[/list][/list]
	    
[*]Configure the connection settings using the GUI.
	      [list]Username = ;[/list]
	      [list]Password = ;[/list]
	      [list]Check the "Remember password" box.[/list]
	      [list]Phone Number = #777[/list]
	      [list]Press the "Setup" button.
		 [list]On the "Modem" tab
		    [list]Device = /dev/rfcomm0[/list]
		    [list]Type = Analog Modem[/list]
		    [list]Speed = highest it'll go (vroom vroom!!!)[/list]
		    [list]Phone Line = Tone[/list]
		    [list]Wait for dialtone = checked[/list]
		 [/list]
		 [list]On the "Options" tab.
[list]Ignore terminal strings (stupid mode) = checked[/list]
[list]I recommend checking "Minimize" and "Dock in notification area", as well as setting the "Idle Time" to 0.[/list]
		 [/list]
	      [/list]
	  
	
    [/list]
  [*]Test the connection
    [list=1][*]Disconnect any wired network connection, and disable any wireless (a,b,g,n) devices.
	    [*]Press "Connect" in the Gnome PPP GUI. (Also an excellent time for finger-crossing or invocational dance)
	    [*]If you do connect, make sure to try and browse the web for at least 10 minutes.
	      [list]If you stay connected, you're all done![/list]
	      [list]If you get disconnected after about 2 minutes, you need to edit /etc/ppp/options.```
sudo gedit /etc/ppp/options
```Just change "lcp-echo-interval" and "lcp-echo-failure" to 0, and test the connection again.
[/list]
    [/list]
[/list]

I gathered this info from all over the Internet over the past few months, and then typed this up from memory while I was configuring bluetooh on a new distro. If you see any errors in this HOWTO, let me know and I'll edit it. Oh, and a special thanks goes out to all those who created the software to make this work!

---

### Post by caish5 on 2009-06-09
With this i can get a connection for about 4 seconds. And then it disconnects with error 16. Apparently that means the modem disconnected the call. 

Any idea how to avoid that. I'm using a Nokia 6220c to connect to Vodafone.

---

### Post by Pinteiro on 2009-06-09
What if I wanted to do this the other way aroung (in other words: to have the phone use the computer as a gateway to the internet), is that possible?

---

### Post by zukakog on 2009-07-01
> **caish5 said:**
> With this i can get a connection for about 4 seconds. And then it disconnects with error 16. Apparently that means the modem disconnected the call. 

Any idea how to avoid that. I'm using a Nokia 6220c to connect to Vodafone.
Did you set the lcp-echo entries to 0 like it says at the very end of the original post? Each carrier is a bit different, and this guide is specifically for Sprint, so it may not work for you.

---

### Post by stephanunc on 2009-07-25
Thanks for the fine detail. I'm on sprint and am having problems with the password. 
Do I have a username and password? Do I need "Phone as modem" service with sprint for this to work? 

Thanks for your help!

---

### Post by discord on 2010-02-01
I'm getting this error, looks like it can't find the device. Can you offer any help?


GNOME PPP: STDERR: --> Cannot open /dev/rfcomm0: No such file or directory

---

