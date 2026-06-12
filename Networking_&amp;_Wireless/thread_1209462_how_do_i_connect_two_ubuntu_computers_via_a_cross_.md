---
title: "how do i connect two ubuntu computers via a cross over cable"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by junglejuice on 2009-07-10
hi 
i have a desktop with ubuntu 8.10 and a laptop with ubuntu 9.04. all i have is a cross over cable no router or anything like that and i'd simply like to get files from the desktop computer to the laptop. can someone pls give me step by step instructions on how to do this?

---

### Post by wojox on 2009-07-10
Connect the cables then go to Places > Connect to server

Pick ssh 
Enter ip address and enter.

---

### Post by Iowan on 2009-07-10
You will need to set up a manual (static) address on both machines in the same subnet. *Might* need to list the other machine as gateway... but try it first without.  You will need to install a file server one one/both machines - Ubuntu comes with clients for most filesystems, but must have server installed for SSH, NFS, Samba, etc.

---

### Post by junglejuice on 2009-07-10
> **Iowan said:**
> You will need to set up a manual (static) address on both machines in the same subnet. *Might* need to list the other machine as gateway... but try it first without.  You will need to install a file server one one/both machines - Ubuntu comes with clients for most filesystems, but must have server installed for SSH, NFS, Samba, etc.
can you recommend a server? when i try places ->connect to server choose ssh and input the other computers ip address ubuntu connects to my local machine and show only the contents of my local machine. btw both machines have the same main user name and password, is this a problem?

---

### Post by issih on 2009-07-10
Between two ubuntu machines the easiest is probably to install the package openssh-server.

this will do it from a terminal:

```
sudo apt-get install openssh-server
```

and enter your login password when asked.

Alternatively just install it from synaptic package manager.

You can then connect from a machine to the one with the server package installed on it(an openssh-clent is installed by default, so they both have that). For ease of use having the server on both is probably best, but it is not strictly necessary.

Having the same user details is absolutely fine.

Oh and do make sure that you have network connectivity using something like ping before you go any further, because obviously that is the first and most important requirement :)

Hope that helps

---

### Post by anystupidname on 2009-07-10
So, to recap:

-on both computers "sudo aptitude install ssh"
-on both computers "sudo nano /etc/network/interfaces"
-set one to
```
auto eth0
iface eth0 inet static
network 10.0.0.0
gateway 10.0.0.1
address 10.0.0.2
netmask 255.255.255.0
broadcast 10.0.0.255
```
-set the other to:
```
auto eth0
iface eth0 inet static
network 10.0.0.0
gateway 10.0.0.1
address 10.0.0.1
netmask 255.255.255.0
broadcast 10.0.0.255
```

-confirm the first one can reach the second:
"ping 10.0.0.1"

-transfer files from one to the other:
"scp [email]junglejuice@10.0.0.1:/home/junglejuice/Desktop/porn.jpg[/email] /localpath/porncollection/"

---

### Post by junglejuice on 2009-07-10
thanks all for the help, but it's just still not working. i've installed openssh server on both machines, they are definitely connected cause i can ping one from the other and when i disable networking on one computer the other tells me that a network connection has been dropped. is it possible that they are connected but i'm just not using the right interface to transfer files between them? i've tried places>connect to server change to ssh and enter the other computers ip address in the server text field. but all that does is show me the file system of the local machine that i ran the command from (not the other machine's file system). i also tried the scp command as per anystupidname's instruction and ubuntu tells me that the file has copied across but when i check for the file on the other computer, it's not there. does anyone have any further suggestions, i'm sure the problem is really simple and i'm just being a dope...

---

### Post by jonobr on 2009-07-10
what file did you copy across?

If you get the name of it eg myfile.txt

go to the other machine you copied it to and open a terminal window

in the window type

find . -name myfile.txt

I reckon you are looking for it on your desktop when its in your home folders

in windows world its in documents and settings/yourname

and not documents and settings/yourname/Desktop

However, the find should tell you where its at

---

### Post by issih on 2009-07-10
can you ssh into the other box.

i.e. at a terminal what happens if you type:
```
ssh user@192.168.0.1
```
replacing user with your username and 192.168.0.1 with the remote boxes ip address.

If ssh is working you should get prompted for your password, then be presented with a terminal prompt which is a terminal on the remote machine..you can check this by looking around the file system with the ls and cd commands.

If that works then ssh is functioning and you are just screwing up the sharing somewhere.

Hope that helps

---

### Post by junglejuice on 2009-07-10
> **issih said:**
> can you ssh into the other box.

i.e. at a terminal what happens if you type:
```
ssh user@192.168.0.1
```
replacing user with your username and 192.168.0.1 with the remote boxes ip address.

If ssh is working you should get prompted for your password, then be presented with a terminal prompt which is a terminal on the remote machine..you can check this by looking around the file system with the ls and cd commands.

If that works then ssh is functioning and you are just screwing up the sharing somewhere.

Hope that helps
when i input the command substituting my username and the remote computers ip address, ubuntu asks me for a confirmation to continue by typing "yes" then it asks me for a password, which i input and i get taken to a terminal prompt, but when i run the ls command ubuntu lists the contents of the local computers home directory (not the remote computer) why does this keep happening?

---

### Post by issih on 2009-07-10
Ok first make absolutely sure you can tell which filesystem is which... you are logging in from one ubuntu machine to another, and you are using the same username on both, so the filesystems are going to be VERY similar.

Try creating a filecalled I_AM_NUMBER_1 on one machine and I_AM_NUMBER_2 on the other, in the respective home directories, just so you have an easy definite way to tell where you are.

after that make sure that both machines have unique ip addresses (not the same) and that you are entering the ip address of the remote computer not the local one. You can ssh into the box you are already working on if you use its own ip address.

Its going to be one of those... you just have to be methodical and careful to sort it out

---

### Post by junglejuice on 2009-07-11
> **issih said:**
> Ok first make absolutely sure you can tell which filesystem is which... you are logging in from one ubuntu machine to another, and you are using the same username on both, so the filesystems are going to be VERY similar.

Try creating a filecalled I_AM_NUMBER_1 on one machine and I_AM_NUMBER_2 on the other, in the respective home directories, just so you have an easy definite way to tell where you are.

after that make sure that both machines have unique ip addresses (not the same) and that you are entering the ip address of the remote computer not the local one. You can ssh into the box you are already working on if you use its own ip address.

Its going to be one of those... you just have to be methodical and careful to sort it out
i followed anystupidname's instructions on creating ip addresses for eth0 on both computers. i definitely can identify one computer from another as the contents of each home dir is different.
however when i right click on the network icon in the panel and choose connection information the ip addresses are different to the one's i've specified. so when i try to connect to the remote computer with ssh i use the ip address that i get from the remote computer when i right click on the network icon and choose connection information. so it would seem to me that this would be the correct ip address i'm inputing, am i doing something wrong? (i must be cause it aint workin') the laptop is ubuntu 9.04 and the desktop is ubuntu studio 8.10. do these two versions use different network managers? could my problem have something to do with this? thanks for the help, i really am stuck...

---

### Post by issih on 2009-07-11
Are you by any chance using the ip address 127.0.0.1?

because that address always maps back to the local host.

What precisely is the output of "ifconfig -a" on each machine?

I suspect you have your networking screwed up...assuming I'm right then you'd be better off doing it via the network manager rather than in the /etc/network.interfaces file unless you are pretty confident.

so undo the changes you did in there and edit the connection on each machine, selecting a static ip and entering details like this:

ip address 10.0.0.X 
subnet mask 255.255.255.0

simply substituting X with a unique number for each machine, 1 and 2 will do, as will 200 and 201 , just don't make them 0 or bigger than 255.

the gateway and dns don't really matter for this scenario. the former is the machine that knows how to route traffic outside the current network (which we aren't trying to do) and the dns machine is the one that provides a domain name service to map urls to ip addresses (which we don't need)

Once the connection information states that the ip address matches what you set it to be, try again.

---

### Post by junglejuice on 2009-07-11
> **issih said:**
> Are you by any chance using the ip address 127.0.0.1?

because that address always maps back to the local host.

What precisely is the output of "ifconfig -a" on each machine?

I suspect you have your networking screwed up...assuming I'm right then you'd be better off doing it via the network manager rather than in the /etc/network.interfaces file unless you are pretty confident.

so undo the changes you did in there and edit the connection on each machine, selecting a static ip and entering details like this:

ip address 10.0.0.X 
subnet mask 255.255.255.0

simply substituting X with a unique number for each machine, 1 and 2 will do, as will 200 and 201 , just don't make them 0 or bigger than 255.

the gateway and dns don't really matter for this scenario. the former is the machine that knows how to route traffic outside the current network (which we aren't trying to do) and the dns machine is the one that provides a domain name service to map urls to ip addresses (which we don't need)

Once the connection information states that the ip address matches what you set it to be, try again.
issih, i think you might have solved the problem. i'll test it and let you know very soon. yes indeed my ip address on one of the computers was set to 127.0.0.1. i have certainly learned alot from your explanation, thank you a million times over for your help, i really really appreciate it :)
the output of the desktop machine when i run ifconfig -a is
```
eth0      Link encap:Ethernet  HWaddr 00:30:18:a5:51:73  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56108 (56.1 KB)  TX bytes:47394 (47.3 KB)
          Interrupt:23 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:31065 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31065 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:38519054 (38.5 MB)  TX bytes:38519054 (38.5 MB)

pan0      Link encap:Ethernet  HWaddr 26:d3:0b:06:37:2c  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:172.28.103.90  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:521 errors:0 dropped:0 overruns:0 frame:0
          TX packets:529 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:397789 (397.7 KB)  TX bytes:94833 (94.8 KB)

vnet0     Link encap:Ethernet  HWaddr 3a:ac:47:da:b5:7f  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::38ac:47ff:feda:b57f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:250 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:31542 (31.5 KB)

```
i'll have to save the output from the laptop to a memory stick to get it onto this computer so that i can post it, please bear with me...

---

### Post by junglejuice on 2009-07-11
hi
when i disconect from the internet and run the same command on the same desktop computer the output is different form my previous post. when not connected to the internet the output of ifconfig -a on the desktop is
```
eth0      Link encap:Ethernet  HWaddr 00:30:18:a5:51:73  
          inet addr:127.0.0.2  Bcast:127.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:18ff:fea5:5173/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56108 (56.1 KB)  TX bytes:47862 (47.8 KB)
          Interrupt:23 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:31245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:38533270 (38.5 MB)  TX bytes:38533270 (38.5 MB)

pan0      Link encap:Ethernet  HWaddr 26:d3:0b:06:37:2c  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vnet0     Link encap:Ethernet  HWaddr 3a:ac:47:da:b5:7f  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::38ac:47ff:feda:b57f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:250 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:31542 (31.5 KB)

``` 
and on the laptop which is not online (don't know if that has anything to do with this problem or not?)
```
eth0      Link encap:Ethernet  HWaddr 00:1b:38:4e:ba:40  
          inet addr:127.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe4e:ba40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:492 (492.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:1c:26:73:bf:46  
          inet6 addr: fe80::21c:26ff:fe73:bf46/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pan0      Link encap:Ethernet  HWaddr 1e:d9:bc:8c:09:6e  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

there are some other issues that might help, after i messed around with the /etc/network/interfaces file the laptop does not recognise that a connection is present any more. when i click on the network icon in the panel it con brings up a menu under which is listed wired networks, and below that is the greyed out text saying device not managed. does that help?

---

### Post by junglejuice on 2009-07-11
thanks for the help, it seems to be working!
i followed this tutorial on how to set an ip address [http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html)
leaving out the part about removing network manager. then used "ssh username@ipaddress" and this brought up the remote computers file system in nautilus which is exactly what i wanted :-)
thanks issih and others for the help i've learnt quite a bit from your help and hopefully will be able to help some1 else that may have a similar problem if the need arises.
many thanks jj

---

### Post by issih on 2009-07-12
Glad you got it sorted :)

---

### Post by junglejuice on 2009-07-12
> **issih said:**
> Glad you got it sorted :)

yea thanks largely to your info on the ip stuff :-) very much appreciated. only problem is that the connection is not permanent. so when i restart one of the computers i have to fiddle around again with the settings to get them to see each other again. do you happen to know of any software that can make this sort of thing easier to deal with? like, i read that removing network manager makes he process more permanent. although i just don't want to mess up my internet connection inadvertently, if you know what i mean?

---

### Post by issih on 2009-07-12
Theres a lot of information and misinformation about this stuff.

The traditional way of doing IP assignments in linux is via the /etc/network/interfaces file, but, network manager does not use that any more. In theory it tries to honour any settings in it, but the whole system is a bit of a mess. Network manager has been undergoing some fairly heavy development recently, which has meant it has been a bit buggy, and people have consequently been advising yanking it out and using the traditional methods instead. It seems to have stabilised though, at least in my experience, and is pretty useable now.

To be honest, as a newish user, I'd follow the modern methodology and stick with using network manager, and stay away from the file based technique unless you have trouble.

For example, my /etc/network/interfaces file contains just this:
```
auto lo
iface lo inet loopback
```

So try using a file with just that in it (that bit IS vital) and do the rest graphically.

The rest is configured by right clicking on the network icon and choosing edit connection. and authenticating, then select your wired connection and edit it. In the ipv4 settings tab you then want to select manual as the method, and enter your chosen address and subset mask (again in theses circumstances, gateway and dns are an irrelevance) 

make sure connect automatically is ticked and that should do it.

Hope that helps.

---

