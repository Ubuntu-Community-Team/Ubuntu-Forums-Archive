---
title: "Connecting to Windows Network - newbie"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by pastorblue on 2008-12-18
Just setting up a Ubuntu machine and I would like to connect it to our Windows 2003 Server network. So I need to give the machine a name so I can register that on the server. Where/how do I give the machine a network name in Ubuntu?
Secondly, I need to log on to the network from the Ubuntu machine using an existing login. Where do I do that in Ubuntu, please?
I'd like to setup an Ubuntu server but I expect you don't want to hear about that!!

Thanks.

---

### Post by S_e_P_p on 2008-12-18
Hello,

To communicate with a Windows network you have to install SAMBA.

Greets,
SePp

---

### Post by pastorblue on 2008-12-18
Thank you for that, will do. And then the procedure is . . . ?

---

### Post by zman58 on 2008-12-18
Step ONE:
You will need an IP address. This is the very first step that you MUST resolve. Can you tell if you have an IP address on the Ubuntu workstation?  Start a command prompt and enter the command "ifconfig". It should provide your network configuration for your primary Ethernet device "eth0" which will look something like this:

eth0      Link encap:Ethernet  HWaddr 00:b0:d0:78:85:83  
          inet addr:10.9.73.171  Bcast:10.9.73.255  Mask:255.255.255.0
          inet6 addr: fe80::2b0:d0ff:fe78:8583/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57092 errors:0 dropped:0 overruns:1 frame:0
          TX packets:13315 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19006339 (18.1 MB)  TX bytes:4031176 (3.8 MB)
          Interrupt:17 Base address:0xc00 

If you see an "inet addr" number assigned, then you are getting an ip address assigned to you from the server. If you are not, then you must first resolve this issue. You can do nothing without an ip address. This can be resolved by knowing how the Windows server is set up. Will it auto assign IP addresses, or perhaps do you need to set one up manually. If the Windows server is set up to auto-assign, using DHCP, then you should get an ip address.

Step TWO:
Try your route to the internet. Assuming here that the windows server is providing the full network configuration to your workstation and also is providing the route to the outside network; you should get a default route along with that IP configuration... So to test your default route, just try to ping a host name somewhere out there in Internet land. At a command prompt type "ping yahoo.com". You should see something that looks like this.

zahorek@zdell420:~$ ping yahoo.com
PING yahoo.com (68.180.206.184) 56(84) bytes of data.
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=1 ttl=52 time=61.2 ms
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=2 ttl=52 time=60.6 ms
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=3 ttl=52 time=61.2 ms

--- yahoo.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 60.617/61.019/61.238/0.284 ms

So if you can get this far--and you must be able to do this before you can move on; you can claim that you have a host established on the network and can use the " Windows network". Now on to more....

Step THREE:
Connecting to Windows shares:
You can use Nautilus to do this. Just select "Places - Connect to Server" on the Ubuntu desktop. Select the appropriate service type in the combo-box (Windows share). Provide the credentials and you should be able to connect.
Alternatively, you can set up mounts to Windows shares in /etc/fstab.
I use a simple bash script called "smb_net" for attaching to Windows shares which I have on my website. Instructions are provided and the solution is VERY effective and reliable. You will want to download the smb_net tar file (tar is like a zip file), unpack it, and follow examples and instructions provided as comments in the smb_net script file in that package.
[http://home.roadrunner.com/~zahorec/gatekeeper.html](http://home.roadrunner.com/~zahorec/gatekeeper.html)

Summary:
So at this point you should be able to use the Ubuntu host for Internet access and connect to file shares provided on Windows server(s).

BTW - my website link provided above provides full instructions and config files for setting up a multitude of network services on Ubuntu 8.04.1 server. The server name is "gatekeeper". I have been setting these up for several years now and it has worked out very well. Feel free to use anything you see there for your solution. The system I have up and running now has executed flawlessly for me. Just follow the instructions provided and use the config files for good examples. In most cases you will be able to use exact copies of those config files for your system.
[http://home.roadrunner.com/~zahorec/gatekeeper.html](http://home.roadrunner.com/~zahorec/gatekeeper.html)

---

### Post by zman58 on 2008-12-18
> **pastorblue said:**
> Just setting up a Ubuntu machine and I would like to connect it to our Windows 2003 Server network. So I need to give the machine a name so I can register that on the server. Where/how do I give the machine a network name in Ubuntu?
Secondly, I need to log on to the network from the Ubuntu machine using an existing login. Where do I do that in Ubuntu, please?
I'd like to setup an Ubuntu server but I expect you don't want to hear about that!!

Thanks.

"Windows network" can mean just about anything. It usually refers to a multitude of network based services, such as CIFS/SMB (windows) file shares for example.
You don't log into a Windows network. You use services on a network, some of which may require specific user credentials--depending on how they are set up. Typically you will have a user account established on the Ubuntu box. You will log into the Ubuntu box. If you need access to services within the Windows network such as network shares, printer, proxy, other servers, etc., then you will access those services using the required components at the Ubuntu box and provide the necessary credentials (required user name and password--if actually required) by the services at that time. In most cases the Ubuntu box will be able to store and manage these credentials for you or challenge you when it is necessary to provide them.

---

### Post by pastorblue on 2008-12-19
Thank you for the really helpful posts.

In our case 'Windows Network' refers to a server running Windows Server 2003 with 30 or so desktop machines. To logon to the network one needs a valid username and logon and that is what I do not know how to get Ubuntu to do! Thank you though Ken, and I really appreciate it. Your longer post I will read through. Getting help here in Zambia would be impossible without this.

---

### Post by eder.apt-get on 2008-12-19
In order to your Ubuntu talk to a Windows network, you gonna need to install winbind and samba. This way, Ubuntu can connect to the Active Directory, "pretending" it is a Win machine. Follow the official instructions here:
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto")

---

