---
title: "network manager applet enable networking unchecked"
date: 2011-04-02
forum: Networking &amp; Wireless
---

### Post by mrxubu on 2011-04-02
Hi im pretty new to xubuntu/linux.
Here is my question.

Whenever I start up my laptop i do not get a wireless connection automatically.
I have to rightclick network manager applet and select enable networking.
After that everything works fine untill i shutdown and restart my laptop.
I would like a way to change this so that my wifi connection is working whithout having to click something first..

OS:Xubuntu 10.04 LTS!       
hardware: dell inspiron 6000
nm applet: 0.8.?

GRts,
Mr Xubu

---

### Post by matt_symes on 2011-04-02
Hi

Please post the output of 

```
cat /var/lib/NetworkManager/NetworkManager.state
```

I assume it's the same in xubuntu.

Kind regards

---

### Post by mrxubu on 2011-04-05
thx for your reply: here is the output

$cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=false
WirelessEnabled=true
WWANEnabled=true

---

### Post by matt_symes on 2011-04-05
Hi

> **mrxubu said:**
> thx for your reply: here is the output

$cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=false
WirelessEnabled=true
WWANEnabled=true

Open a terminal and type

```
sudo nano /var/lib/NetworkManager/NetworkManager.state
```

Enter your password. It will not be echoed to the screen.

Change

```
NetworkingEnabled=false
```

to 

```
NetworkingEnabled=true
```

Press ctrl + o to save the file and ctrl + x to exit.

Then type

```
sudo service network-manager restart
```

Does this fix it ?

Kind regards

---

### Post by mrxubu on 2011-04-08
Hi and thx again,
 
I followed your steps, and the network was enabled. Also the file /var/lib/NetworkManager/NetworkManager.state now read:
..."NetworkingEnabled=true"...
So it seemed to work.
 
But after that I rebooted my laptop and found networking was disabled again.
Also the setting in the file /var/lib/NetworkManager/NetworkManager.state was back to 
..."NetworkingEnabled=false"...
again
 
Now I did a search on google, found : [http://www.harshj.com/2010/06/02/network-manager-disabled/](http://www.harshj.com/2010/06/02/network-manager-disabled/)
 
and followed the advise there to delete the file /var/lib/NetworkManager/NetworkManager.state
After this I did two reboots and got a working network connection.
 
Only after rebooting the third time the problem was back. 
 
 
Then I started to experiment with the way I shut down the laptop: 
 
When I shut down by pressing the powerbutton once, which causes xubuntu to show its logo briefly  and then shut down fast, the next time i boot my laptop the network is disabled.
 
When I shut down by logging off first and then shutting down from the log on screen, the next time I boot up the network is enabled.
 
So I went to applications->Settings->Xfce 4 Settings Manager->Power Manager and changed the following setting: "When Power button is pressed" from "Shut Down" to "Ask"
 
This seems to solve it (rebooted 3 times already)
 
Now I'm left with the following questions:
1. How long will it last?? 
2. Why does this happen?
3. Is this a bug?
4. Maybe there is work around: Perhaps a script that checks the networking state periodically and then resets it, or a bootup script to delete the file /var/lib/NetworkManager/NetworkManager.state before the service networkmanager is started. Only I don't know how to make this...
 
Best regards,

---

### Post by matt_symes on 2011-04-08
Hi

> How long will it last?? 
2. Why does this happen?
3. Is this a bug?
4. Maybe there is work around: Perhaps a script that checks the networking state periodically and then resets it, or a bootup script to delete the file /var/lib/NetworkManager/NetworkManager.state before the service networkmanager is started. Only I don't know how to make this...

I am unsure of the first three as have never had it happen to me.

There may be a work around though. You could set up the files values and then make the file immutable. That might fix it. So set NetworkingEnabled=true and then

```
sudo chattr +i /var/lib/NetworkManager/NetworkManager.state
```

Kind regards

---

### Post by mrxubu on 2011-04-11
Hi,

 thanks a lot for your replies. 

For the past few days the problem hasnt returned so i'm glad. If it does return i'm  gonna change the permissions on the file like you suggested. But for now i'll leave it, because it seems to work after changing the energy settings.

Best regards,

---

