---
title: "Using lan and internet simulataneously through a single NIC"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by philosophers-stone on 2010-12-22
I have been using ubuntu for more than 3 months now :KS. I was wondering if could use LAN and Internet simultaneously in windows, why that should not work in ubuntu??:confused:

I tried as much as I could, searched different forum and thought there is no way I can get around with it....until recently I found a solution in a forum:lolflag:. For your information I use ppoe for connecting to Internet.

The solution was as simple as running this simple command [B][COLOR=Red]sudo ifconfig eth0 192.168.x.x netmask 255.x.x.x
[/COLOR]I have replaced those x with my desired number.....

[/B]Guess what??? It worked like a charm! Now I could browse LAN shares and Internet simultaneously!!!!!!\\:D/

Great,huh??? Until I found that I have to repeat the command every time I redial my connection...:-k

So my question to the geeks is -*** How to do it and forget it?*** I mean I don't want to do it every time I dial my connection.

Bye the way Ubuntu :guitar: rocks!! And thanks in advance for your time to solve my problem.

---

### Post by dineshs on 2010-12-22
If you have Network manager installed try
[http://ubuntuforums.org/showpost.php?p=9467538&postcount=5](http://ubuntuforums.org/showpost.php?p=9467538&postcount=5)

---

### Post by philosophers-stone on 2010-12-22
> **dineshs said:**
> If you have Network manager installed try
[http://ubuntuforums.org/showpost.php?p=9467538&postcount=5](http://ubuntuforums.org/showpost.php?p=9467538&postcount=5)

I have already tried this;). In this way I have to use either LAN or Internet , not simultaneously.
I have mentioned that I use **[COLOR=Red]ppoe[/COLOR]**. For Internet connection I have to use ***DSL tab*** where User-name and password is given. If I give manual ip for that setting i would not be able to connect.
If I set wired connection using manual ip configuration , I can browse lan without internet.

But I want to use both at the same time. Thats what above command does. But I have to it every time I connect. 
[SIZE=2]**[FONT=Comic Sans MS]I think I have made myself clear!!I want a permanent solution for that problem.[/FONT]**[/SIZE]:popcorn:

---

### Post by dineshs on 2010-12-22
I dont think network manager can do that.But you may try another method if you havent already.
Let the manual NM settings be unchanged.
Run ```
sudo pppoeconf
```to configure your DSL connection
Run```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```and backup your /etc/network/interfaces
Edit /etc/network/interfaces using ```
gksudo gedit /etc/network/interfaces
```so that it contains only the following lines```
auto lo
iface lo inet loopback
```
Now connect DSL using ```
sudo pon dsl-provider
```If you want to disconnect do```
sudo poff dsl-provider
```
Note:If you want DSL during startup you can do so while configuring the connection using sudo pppoeconf
Network manager will manage LAN automatically
BTW Can you configure your DSL modem in pppoe mode?

---

### Post by philosophers-stone on 2010-12-22
> **dineshs said:**
> I dont think network manager can do that.But you may try another method if you havent already.
Let the manual NM settings be unchanged.
Run ```
sudo pppoeconf
```to configure your DSL connection
Run```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```and backup your /etc/network/interfaces
Edit /etc/network/interfaces using ```
gksudo gedit /etc/network/interfaces
```so that it contains only the following lines```
auto lo
iface lo inet loopback
```Now connect DSL using ```
sudo pon dsl-provider
```If you want to disconnect do```
sudo poff dsl-provider
```Note:If you want DSL during startup you can do so while configuring the connection using sudo pppoeconf
Network manager will manage LAN automatically
BTW Can you configure your DSL modem in pppoe mode?
[B][SIZE=2][FONT=Comic Sans MS]I wish I had not have used your command. I followed your instruction and you know what I was not even enable to go in any page.
I then restarted To my surprise network notification systray is gone!!! Now how do I connect to Internet.Your solution only increased my problem.
Now please help me to go back with my earlier configuration.
Do Ubuntu has something like system restore??
I should be careful................................. 
[/FONT][/SIZE][/B]

---

### Post by grahammechanical on 2010-12-22
At this very moment I have two active network connections - wired and wireless. I do not have another computer. so, I do not have a LAN. I am only connecting to the Internet. At the moment it is going through the wired connection. I do not know if it is possible under Ubuntu to connect to the Internet using wireless and at the same time connect to a LAN using ethernet. I cannot try that out. But I do know that it is possible under a standard Ubuntu set up to have both ethernet and wireless connections to a router/modem at the same time.

Regards.

---

### Post by dineshs on 2010-12-22
> I wish I had not have used your command. I followed your instruction and you know what I was not even enable to go in any page.
running sudo pppoeconf or pon dsl-provider will not do any harm but editing /etc/network/interfaces will(anyway we have a backup ie /etc/network/interfaces.bak).
> To my surprise network notification systray is gone!!! Right click on the top panel-click add to panel-select notification area -click add
If your icon is not back,run
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```and set ```
managed=true
```then [COLOR="Red"]restart[/COLOR]
If there is no luck still,please post the output of ```
cat /etc/network/interfaces
```and ```
cat /etc/network/interfaces.bak
```

---

### Post by psusi on 2010-12-22
You need to get yourself a router, then you can use the Internet from all the machines on the LAN.

P.S. PPPoE is the devil.  Smack retarded ISPs that use it upside the head.

---

### Post by dineshs on 2010-12-22
> **psusi said:**
> You need to get yourself a router, then you can use the Internet from all the machines on the LAN.

P.S. PPPoE is the devil.  Smack retarded ISPs that use it upside the head.
+1 so that you can configure your router in pppoe mode,share internet and use LAN

---

### Post by philosophers-stone on 2010-12-22
> **dineshs said:**
> running sudo pppoeconf or pon dsl-provider will not do any harm but editing /etc/network/interfaces will(anyway we have a backup ie /etc/network/interfaces.bak).
 Right click on the top panel-click add to panel-select notification area -click add
If your icon is not back,run
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```and set ```
managed=true
```then [COLOR=Red]restart[/COLOR]
If there is no luck still,please post the output of ```
cat /etc/network/interfaces
```and ```
cat /etc/network/interfaces.bak
```
Mr. dineshs **[COLOR=Red]Sorry for blaming you![/COLOR]!** :oops: I was searching about restoring this icon and found the solution in another thread .It was solved by [COLOR=SeaGreen]***you!!***[/COLOR] =D>And that solved my problem too!!!

[COLOR=Magenta]I have to be careful about blaming people for my low knowledge. [/COLOR]

---

