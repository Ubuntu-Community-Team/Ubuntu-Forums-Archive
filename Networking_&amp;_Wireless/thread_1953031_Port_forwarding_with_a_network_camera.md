---
title: "Port forwarding with a network camera"
date: 2012-04-05
forum: Networking &amp; Wireless
---

### Post by pyrojoe on 2012-04-05
Hello,
I have searched for information on how to do this, but all the discussions I found on the topic were either not applicable, or did not work. Right now, I have two computers. One of them, lets call it "Server", has an Axis IP camera attached to it, and a wireless that is broadcasting an ad-hoc network. I have another computer, called "Client", that is connected to the wireless network. Both computers are running Ubuntu 11.04. The setup looks something like this:

```

[IP-Camera]->eth0->[Server]->wlan1->"adHoc-Network"->wlan0->[Client]
```

All three have static IP addresses for the network as follow:
```
IP Camera:
192.168.0.60

Server:
to IP-Camera: 192.168.0.100
to Client: 10.42.43.2

Client:
10.42.43.3

```


What steps do I need to take to view the camera feed on the client computer? If I need to provide more details, please let me know. Any help would be greatly appreciated.

Thank you,
-Joe

---

### Post by Vishal Agarwal on 2012-04-06
Hi Joe,

I am also searching solution for the same problem. I want to access my local CCTV network in my factory from outside world.

SO let us start with pl find out the port is being used by IP camera.

 you can use "nmap 192.168.0.60".

---

### Post by pyrojoe on 2012-04-06
Here are the results of nmap:

```
oryx@oryx-server:~$ nmap 192.168.0.60

Starting Nmap 5.21 ( http://nmap.org ) at 2012-04-06 17:58 EDT
Nmap scan report for 192.168.0.60
Host is up (0.0060s latency).
Not shown: 996 closed ports
PORT      STATE SERVICE
21/tcp    open  ftp
80/tcp    open  http
554/tcp   open  rtsp
49152/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.41 seconds
```

I am likely going to be using rtsp, so 554 seems like the best port for my purposes.

---

### Post by Recidivist on 2012-04-09
Depending on your router it should be fairly straightforward to port forward any port of your choice to your camera.

[IP camera port forwarding guide]("http://www.networkwebcams.com/ip-camera-learning-center/2010/02/16/howto-ip-camera-remote-access/")

Here's a step-by-step HOWTO which has helped me and others.

---

