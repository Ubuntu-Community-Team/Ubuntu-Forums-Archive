---
title: "How will Ubuntu user telnet the Windows Client?"
date: 2013-04-21
forum: Networking &amp; Wireless
---

### Post by nerdyme on 2013-04-21
I have used "TELNET"/ "SSH" service in windows for remote login a LINUX server by enabling the telnet client at Windows and telnet server at LINUX. Now I want to telnet a windows server using LINUX TELNET CLIENT. I am unable to do it. Please tell me. Which packages I need in LINUX? What are the steps I should follow? And other prerequisites?

---

### Post by Cheesemill on 2013-04-21
To connect via telnet to another machine you just need to use the telnet command. I'm pretty sure that it's already installed on Ubuntu, but if not you can install it with...
```
sudo apt-get install telnet
```
Once it is installed you just run the telnet command followed by the address you want to connect to, for example...
```
telnet 192.168.1.100
```


Can I ask why you are using telnet? It does still have its uses but it's never really used for communicating between machines any more because it is so insecure. All of the data including your username and password is transmitted in plain text making it trivial to listen in on.

---

### Post by nerdyme on 2013-04-21
> **Cheesemill said:**
> To connect via telnet to another machine you just need to use the telnet command. I'm pretty sure that it's already installed on Ubuntu, but if not you can install it with...
```
sudo apt-get install telnet
```
Once it is installed you just run the telnet command followed by the address you want to connect to, for example...
```
telnet 192.168.1.100
```


Can I ask why you are using telnet? It does still have its uses but it's never really used for communicating between machines any more because it is so insecure. All of the data including your username and password is transmitted in plain text making it trivial to listen in on.

I am just trying using it in local virtual connection where Linux machine is running inside VMWare workstation and host machine is Windows. Actually I was locally hosting various servers like mail server, FTP server, DHCP using webmin GUI in linux directories. So, to directly access the directories of linux without switching to VMWare window again and again and pressing Ctrl+ Alt+ Enter, I just done telnet to the server in cmd of windows.:popcorn:

But I was unable to do its reverse.

Can you tell me how will i enable Telnet Client in Linux?

---

### Post by Cheesemill on 2013-04-21
> **nerdyme said:**
> Can you tell me how will i enable Telnet Client in Linux?

As I said, you already have it.

You just use the command telnet followed by the name or IP address of the machine you wish to connect to.
You'll have to have already set up a telnet server on your Windows machine for this to work though.

Because of the security implications of using telnet I really would recommend using something else instead such as SSH.

For Ubuntu the ssh client is already installed, for the server you need to install the openssh-server package.
For Windows you can use [Putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") as an ssh client, and there are a number of different [ssh servers]("https://www.google.co.uk/search?q=windows+ssh+server") you could use.

---

