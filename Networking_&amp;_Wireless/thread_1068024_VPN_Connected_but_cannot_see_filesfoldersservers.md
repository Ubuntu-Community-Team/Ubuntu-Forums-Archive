---
title: "VPN Connected but cannot see files/folders/servers"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by scoobyNZ on 2009-02-12
Hi there,

I can connect to my work server through a VPN, however I cannot see any of the files/folders/work servers from my computer.

In windows I can connect to the two work servers by going  using the run command and then typing in \\192.168.0.3 (which is the work server ip address). 

How do I do a similar action in Ubuntu?

From Nautilus I have tried going File:Connect to Server...: Choosing the Service type as windows share and putting the IP address in (192.168.0.3) – to no avail. 

Any ideas / suggestions would be very much appreciated.

S

---

### Post by puppywhacker on 2009-02-12
just below 'file' you have a notepad&pen, when you click it you can type the windows share like this:

```
smb://192.168.0.3/
```

The "file" "connect to server" should work as well, as long as you change the service type to "windows share"

The reason why you can't browse file shares is because name finding doesn't work. Either you didn't specify the wins server or because broadcasting doesn't make it through your tunnel, so you don't find the master server.

---

### Post by Fire_Chief on 2009-02-12
Hey Scooby,

Are you able to ping the target server once the VPN is connected?

---

### Post by scoobyNZ on 2009-02-12
Hi there,

Thanks for the response. 

When I type in smb://192.168.0.3/ into nautilus nothing happens. I dont get any error messages but I also do not see any of the files.

I have tried to ping but typing ping 192.168.0.3 into a terminal and I get 

craig@craig-desktop:~$ ping 192.168.0.3

PING 192.168.0.3 (192.168.0.3) 56(84) bytes of data.

64 bytes from 192.168.0.3: icmp_seq=1 ttl=128 time=23.8 ms

64 bytes from 192.168.0.3: icmp_seq=2 ttl=128 time=23.5 ms

64 bytes from 192.168.0.3: icmp_seq=3 ttl=128 time=23.3 ms

64 bytes from 192.168.0.3: icmp_seq=4 ttl=128 time=23.7 ms

64 bytes from 192.168.0.3: icmp_seq=5 ttl=128 time=23.1 ms

64 bytes from 192.168.0.3: icmp_seq=6 ttl=128 time=23.0 ms

64 bytes from 192.168.0.3: icmp_seq=7 ttl=128 time=23.7 ms

64 bytes from 192.168.0.3: icmp_seq=8 ttl=128 time=23.6 ms

64 bytes from 192.168.0.3: icmp_seq=9 ttl=128 time=23.7 ms


so I assume that this is working?

Are you able to explain what the name finding issue may be?

S

---

### Post by Fire_Chief on 2009-02-12
Yes, the successful ping *should* mean that the tunnel is up and working properly.
Just to cover the bases, what IP range do you use on your home network?

The name resolution problem occurs for two reasons.
1- Linux does not use NetBIOS for name calls or resolution like Windows does
2- Most VPN connections to not forward name requests to DNS servers in the target network to reply with the correct machine IP.

Name resolution in this case is best accomplished by adding static entries in your hosts file (/etc/hosts) for the remote systems. But this is beside the point.

---

### Post by scoobyNZ on 2009-02-12
My home network is running on 192.168.2.xx, so shouldnt be any issues there.

Any other thoughts or suggestions? Thanks for the help.

S

---

### Post by Fire_Chief on 2009-02-12
I've found that when connecting to a Windows file server on my company network that I have to specify an actual share before I get an authentication prompt. I then enter my credentials and then I get to see the files and folders in the share.

i.e.  smb://servername/sharename

---

### Post by JK3mp on 2009-02-12
Well thats a step...

---

### Post by scoobyNZ on 2009-02-13
Thanks F_C,

When I input the windows share name I can now see all the folder etc.

Many thanks,
S

---

