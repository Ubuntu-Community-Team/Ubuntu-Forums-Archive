---
title: "Wire Connection Not Showing In Panel or Connecting"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by NotWindows on 2011-05-15
Hello All,

My sons Ubuntu installation on his computer hasn't showed the Network Connections Icon in the Panel for a long time. This weekend everything was working fine and we needed to go away for the weekend and unhooked the router. When we came back the computer wouldn't connect back up to the internet.

How can I fix the Wired Connections Icon on the Panel and get the Auto Connect to work again?

Thanks,
Kevin

---

### Post by garvinrick4 on 2011-05-16
Try off and on could do it.
                ```
sudo service network-manager stop
``````
sudo rm /var/lib/NetworkManager/NetworkManager.state
``````

[code]sudo service network-manager start 
```

---

### Post by garvinrick4 on 2011-05-16
I believe to launch the applet is:
```
nm-applet
```

---

### Post by NotWindows on 2011-05-16
Ok! Being a newbie of sorts what program do I use to type in those commands?

Would you know why the connection Icon doesn't show up in the panel?

Thanks,
Kevin

---

### Post by garvinrick4 on 2011-05-16
Open a terminal and copy and paste one at a time:
Do not remember or know what version of Ubuntu you are using
but if you hit ctrl/alt/t it will open a terminal.

---

### Post by garvinrick4 on 2011-05-16
> Would you know why the connection Icon doesn't show up in the panel?
In startup applications is network manager checked to start up.

---

### Post by Osogama on 2011-05-18
Thanks for the fix. I installed 10.10 server and had a wifi card attached and it never showed my wifi. I was able to connect thru the wire but unable to see if it connected. when i ran the stop rm and restart script it came back. 

 				 				**Re: Wire Connection Not Showing In Panel or Connecting** 			
 			 			 		   		 		 		Try off and on could do it.
                 	Code:
 	sudo service network-manager stop 
 	Code:
 	sudo rm /var/lib/NetworkManager/NetworkManager.state 
[CODE]
 	Code:
 	sudo service network-manager start

---

### Post by NotWindows on 2011-05-18
Ok Guys I tried it and nothing! Tried turning off the Network Manager and that was fine and turning back on what it didn't understand is the line of command with .state. It says no such file or directory.

When I try nm-applet it says couldn't initialize d-bus manager.

HELP! LOL

---

### Post by garvinrick4 on 2011-05-18
I have to say I would think it is the router then. What is in gedit /var/lib/NetworkManager/NetworkManager.state is used to see if anything enabled and if nothing there does
not look like it is getting anything. Network manager will set up by itself if it gets a signal.
Make sure router settings are right. (router will set itself up once it connects to your internet
provider. Look at the settings for your SSID name and password and such if have wifi.) If you just have a modem connecting to Internet provider make sure all cables plugged in.
Computer is not getting feed from your service.
Try this maybe can get into your router if cables all in and you do have a router and not just a modem:
192.168.1.1
Put that in your URL line (the line where you normally put www. something) hit enter.

You know I am in a different version than yours now but if you right click on upper panel
there is a item to be added that will have the network manager icon the sound icon and a 
little envelope icon, I will add that in a few minutes cannot think of name right now. Indicator applet.
Right click on upper panel and select add to panel and choose indicator applet. You can
right click on any applet on upper panel and remove, lock, move and what it is (about)
Can do same on lower bar.
Right click on network applet and see if enabled.
#This above is for Gnome desktop not Unity interface.

---

### Post by jacw on 2012-01-02
I have exactly this issue including "Couldn't initialise the D-Bus manager".    I know my router is working because several iPhones , a mac and windows PCs are connected.

---

