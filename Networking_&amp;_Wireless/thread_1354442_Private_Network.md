---
title: "Private Network??"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by duthieamber on 2009-12-13
I have recently purchased a Belkin wireless router my laptop picks up the wireless internet but i want to make it private. Like where you have to know the password in order to connect to the internet I have Ubuntu 9.10 and am very very new to Ubuntu. I am not sure where i go to set my settings for the wireless network at. I don't want people stealing my internet. If anybody could please help me i would greatly appreciate it. Thanks!!

---

### Post by shairozan on 2009-12-14
Hey there, 

I'll be more than happy to help, but this will actually all be done outside of Ubuntu first. We will have to enable the security on your wireless router. Once that is done, we will set it so that Ubuntu matches the security settings on the router, and all is good. 

First we need to determine the address of the router. Do me a favor. Once you're connected, open a terminal and enter the following:

```
sudo ifconfig
```

Post that for me. Could you also give me the model # of the router? I need to find the default username and password for it so that we can get in and make the changes.

---

### Post by duthieamber on 2009-12-14
the Model # for the router is F5D7234-4 v3
this is what i got when i typed in that code you gave me
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:d1:58:da  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:14:f1:5b  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fe14:f15b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1887 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2103662 (2.1 MB)  TX bytes:365218 (365.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-14-F1-5B-31-34-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by shairozan on 2009-12-14
Alright, here we go. First off, you will want to have an ethernet cable handy, just in case you have any issues with your wireless connection once you make the change. 

**Step (1)** Login to your Router

Open up firefox and enter the following into your address bar: 

192.168.2.1

You should see a login screen asking for a username and password. Unless you have changed this, your username will be admin and leave password blank. 

**Step (2)** Get to Wireless Security

Once logged in, you should see a screen similar to the below:

[IMG]http://techsupweb.satoamerica.com/temp/wireless1.jpeg[/IMG]

If you notice, wireless is highlighted. You will look for the one beneath it labeled as "Security". Click the link labeled security. Once you click on this page you should see something remotely similar to this:

[IMG]http://techsupweb.satoamerica.com/temp/wireless2.jpeg[/IMG]

**Step 3** Set Wireless Security

This is where things get kind of tricky. I would recommend using WPA as a security method, but not all cards really support it as an encryption method. It used to be a big problem back in the day, but not so much anymore. If you want to use WPA, you will select "WPA/WPA2" as your "allowed client type". Leave authentication as PSK (Pre shared Key) and leave the type as passphrase. 

Then all you have to do is enter a pre-shared key. Whenever someone wants to access your network, it will ask them for a key, and this is what you will enter. It basically becomes a password for your wireless network. Remember to hit "Apply changes" when you are done.  

If this doesn't work well for you, you can repeat steps 1-3 to get here again (you'll probably have to plug the computer into the router if you're having issues with wireless) and change it to WEP. Older, and easier to break, WEP is supported on practically every card out there. For WEP you will have to generate a 64 / 128 bit key (which can be hard to remember). 

**Step 4** Connect to Wireless

Now we have to connect with a client and double check the connection. Try to connect to the wireless like you normally do, and it should ask you for a key or a passphrase. Enter the passphrase you entered earlier and hit ok. If it connects, you've got a working network that's fully protected. If it doesn't connect, make sure you typed the password correctly, and if that doesn't work, we will have to change the authentication method to WEP.

Let me know how it goes :)

---

