---
title: "Help with VNC through SSH"
date: 2010-12-17
forum: Networking &amp; Wireless
---

### Post by new2linux09 on 2010-12-17
Hello,

I'm trying to connect to my Ubuntu box from the WAN side with VNC tunneled through SSH. I've set up the port forward for SSH on the router and can successfully connect to SSH from the WAN side but when I try to forward my VNC session through SSH it times out or does not connect. 
On the LAN side I can also connect via SSH and also connect with VNC through SSH on LAN. 
Any ideas why I wouldn't be able to do the same from the WAN side when it works within the LAN?

SSH port has been changed to 3250 and the VNC server is the defualt, Vino, with Ubuntu 10.10.

The SSH command used was:
```
ssh -L 5901:local-host-IP:5900 USER@WAN IP -p 3250

```

This followed with:  localhost:5901  within the VNC client connecting to the box.

This command worked fine within the LAN, substituting the WAN IP for the internal IP. 

Any ideas would be greatly appreciated.

---

### Post by CharlesA on 2010-12-17
Are you logged into the box locally? In order for vino to launch, a user needs to be logged in.

---

### Post by new2linux09 on 2010-12-17
Yes I am.
I even tested the process within the local before leaving for work to try it from the WAN.

---

### Post by CharlesA on 2010-12-17
The tunnel looks like it's set up correctly. If the SSH server is running on the same machine as you are VNCing into, try using localhost instead of the machine's ip, in the tunnel.

Could be that the firewall is blocking the connection, as I have had that happen before.

---

### Post by new2linux09 on 2010-12-17
Ok, I tried the local host addition (5901:localhost:5900) but it was unable to connect to the VNC session. SSH still connected correctly. 

Also, There is no firewall installed on the Ubuntu box at this point. I'm also trying this from OS X to Ubuntu, although in my reading I don't see why that would make much difference especially when It works flawlessly within the LAN.

Could the router still be blocking something? It doesn't seem like it would since the tunnel establishes without error.

---

### Post by CharlesA on 2010-12-17
Oh I see.

I seem to recall seeing something mentioning that you need to change a setting in OSX to allow it to connect to services tunneled over SSH, but I cannot find the thread.

---

### Post by new2linux09 on 2010-12-17
Oh ok, I did try disabling the OS X firewall momentarily to be sure that wasn't interfering.
I would like to use the native Screen Share with OS X, which did work in the LAN, but for test purposes I've also tried Chicken of the VNC and Jolly Fast VNC as well.

---

### Post by CharlesA on 2010-12-17
You able to connect by using localhost:5901 from the local network, right?

---

### Post by new2linux09 on 2010-12-17
Yeah, I went through the entire tunneling command on the LAN and it worked fine. 
I'm inclined to think something on the router but since the tunnel establishes properly I dont know what it would be.

---

### Post by new2linux09 on 2010-12-17
Yeah, I went through the entire tunneling command on the LAN and it worked fine. 
I'm inclined to think something on the router but since the tunnel establishes properly I dont know what it would be.

---

### Post by CharlesA on 2010-12-17
I don't know, really. I've had no problems with tunneling over SSH with only the SSH port open to the internet.

If you had a livecd around, you could try booting off it and trying to connect from there to see if it works.

---

### Post by new2linux09 on 2010-12-17
You mean to try it from an Ubuntu machine? 
I'm finishing one up right now I can try in a few minutes.

---

### Post by CharlesA on 2010-12-17
Yeah, try from another machine/OS.

---

### Post by new2linux09 on 2010-12-17
Alright I'll repost in a few minutes with the results.

---

### Post by new2linux09 on 2010-12-17
After trying a few different scenarios within a Ubuntu machine I got the same results. SSH connected fine but no vnc session established.

---

### Post by CharlesA on 2010-12-17
I'm guessing there is either a firewall problem or something isn't running.

Can you post the output of this when run on the remote machine:

```
netstat -nl
```

---

### Post by new2linux09 on 2010-12-17
Sure, here is the output:

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:3250            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN     
tcp6       0      0 :::3250                 :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
tcp6       0      0 :::5900                 :::*                    LISTEN     
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 0.0.0.0:43315           0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp6       0      0 :::5353                 :::*                               
udp6       0      0 :::48571                :::*                               
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     30236    /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     8651     @/tmp/dbus-gxKZVmNUCZ
unix  2      [ ACC ]     STREAM     LISTENING     7220     /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     5893     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     11762    @/tmp/dbus-viJs4kyLmB
unix  2      [ ACC ]     STREAM     LISTENING     7938     /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     8638     /tmp/ssh-SDPHYm1202/agent.1202
unix  2      [ ACC ]     STREAM     LISTENING     8764     /tmp/.ICE-unix/1202
unix  2      [ ACC ]     STREAM     LISTENING     8850     /tmp/orbit-knights/linc-53a-0-5530ae11c51a3
unix  2      [ ACC ]     STREAM     LISTENING     9044     /tmp/orbit-knights/linc-4b2-0-64950779d3c58
unix  2      [ ACC ]     STREAM     LISTENING     9271     /tmp/keyring-vqiUE0/control
unix  2      [ ACC ]     STREAM     LISTENING     9298     /tmp/orbit-knights/linc-55c-0-283a9cbabe55d
unix  2      [ ACC ]     STREAM     LISTENING     9306     /tmp/keyring-vqiUE0/pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     9308     /tmp/keyring-vqiUE0/ssh
unix  2      [ ACC ]     STREAM     LISTENING     9334     /tmp/orbit-knights/linc-550-0-2dbb653cf052a
unix  2      [ ACC ]     STREAM     LISTENING     10422    /tmp/orbit-knights/linc-5a9-0-386bd43c754e5
unix  2      [ ACC ]     STREAM     LISTENING     10007    /tmp/orbit-knights/linc-5aa-0-6754c1a1ef0ea
unix  2      [ ACC ]     STREAM     LISTENING     10149    /tmp/orbit-knights/linc-5c6-0-141deaaf70c5c
unix  2      [ ACC ]     STREAM     LISTENING     10152    /tmp/orbit-knights/linc-5ac-0-2e10d4c670f4e
unix  2      [ ACC ]     STREAM     LISTENING     10183    /tmp/orbit-knights/linc-5a8-0-56b780ce7e7a1
unix  2      [ ACC ]     STREAM     LISTENING     10192    /tmp/orbit-knights/linc-5bb-0-3a6fa645a6013
unix  2      [ ACC ]     STREAM     LISTENING     10267    /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     10270    /home/knights/.pulse/a655b817f417e2185dc8d01700000005-runtime/native
unix  2      [ ACC ]     STREAM     LISTENING     10326    /tmp/orbit-knights/linc-5f8-0-52815f821eca6
unix  2      [ ACC ]     STREAM     LISTENING     7937     @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     10352    /tmp/orbit-knights/linc-5f5-0-13e07c085173d
unix  2      [ ACC ]     STREAM     LISTENING     10606    /tmp/orbit-knights/linc-5a3-0-610aca8fe99e0
unix  2      [ ACC ]     STREAM     LISTENING     10728    /tmp/orbit-knights/linc-617-0-2be5bee665809
unix  2      [ ACC ]     STREAM     LISTENING     10734    /tmp/orbit-knights/linc-614-0-d5e31dd5edaf
unix  2      [ ACC ]     STREAM     LISTENING     7527     /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     10910    /tmp/orbit-knights/linc-620-0-43f78c2345f56
unix  2      [ ACC ]     STREAM     LISTENING     10914    /tmp/orbit-knights/linc-622-0-2dd3d8d24615a
unix  2      [ ACC ]     STREAM     LISTENING     11007    /tmp/orbit-knights/linc-623-0-394c3016d117b
unix  2      [ ACC ]     STREAM     LISTENING     11239    /tmp/orbit-knights/linc-637-0-145e195c7ca58
unix  2      [ ACC ]     STREAM     LISTENING     11268    /tmp/orbit-knights/linc-63a-0-178f2806b4266
unix  2      [ ACC ]     STREAM     LISTENING     12296    /tmp/orbit-knights/linc-67b-0-6c85d4909735c
unix  2      [ ACC ]     STREAM     LISTENING     12360    /tmp/orbit-knights/linc-67d-0-2f63b9e2dd191
unix  2      [ ACC ]     STREAM     LISTENING     8415     @/tmp/gdm-session-IdcoJPrn
unix  2      [ ACC ]     STREAM     LISTENING     8763     @/tmp/.ICE-unix/1202
unix  2      [ ACC ]     STREAM     LISTENING     7628     /var/run/acpid.socket

```

---

### Post by CharlesA on 2010-12-17
Well it's listening. That's a plus.

If you change the source port in the tunnel to something different, like 25900, does it let you connect?

---

### Post by new2linux09 on 2010-12-17
Change the port for the VNC or for SSH? 

I'd have to look around for the VNC port change methodology.

---

### Post by CharlesA on 2010-12-17
Just change the port the tunnel is using:

```
ssh -L 25900:localhost:5900 USER@WAN IP -p 3250
```

---

### Post by new2linux09 on 2010-12-17
Still nothing.


Would another VNC server be any different?

---

### Post by CharlesA on 2010-12-17
I doubt it, since it's listening on the remote machine.

I still think it's a firewall problem.

Can you post the output of this please:

```
sudo iptables -L
```

---

### Post by new2linux09 on 2010-12-17
Sure

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

---

### Post by CharlesA on 2010-12-17
Figured as much. I'm out of ideas. Are you able to forward X over SSH, at least?

```
ssh -X -C -c blowfish user@host gnome-panel
```

---

### Post by new2linux09 on 2010-12-17
No I can't. I got this error:

```
(gnome-panel:4347): Gtk-WARNING **: cannot open display:
```

---

### Post by balloooza on 2010-12-17
Two things I sometimes forget are

1)
That when I connect to VNC I need to use localhost, not the remote IP, that is just me spacing out. So I need to use vncviewer localhost

2) I sometimes forget that vnc has 2 things, port number and display number, use vncviewer -help/--help to see if you mixed them up

Sorry if I am no assistance, just trying to see if it was a silly mistake!

---

### Post by CharlesA on 2010-12-17
Hrm. Try using -Y instead of -X.

@balloooze: Good point about display vs port number.

---

### Post by new2linux09 on 2010-12-17
Still nothing. The error message number did change though. 

```
(gnome-panel:4428): Gtk-WARNING **: cannot open display: 

```

How would I fit the display number into the command? 

I'll try anything at this point. lol

---

### Post by new2linux09 on 2010-12-17
I just remembered I did have firestarter installed awhile back but did remove it. Could their be anything left over from that causing the connections to not go through on the WAN side?

---

### Post by CharlesA on 2010-12-17
> **new2linux09 said:**
> Still nothing. The error message number did change though. 

```
(gnome-panel:4428): Gtk-WARNING **: cannot open display: 

```

How would I fit the display number into the command? 

I'll try anything at this point. lol

I'm not too sure, as I only use -X to forward X over SSH. :(

> **new2linux09 said:**
> I just remembered I did have firestarter installed awhile back but did remove it. Could their be anything left over from that causing the connections to not go through on the WAN side?

If it's been purged, it should be fine. There are no rules listed in iptables, so it should be accepting everything.

---

### Post by new2linux09 on 2010-12-19
Sorry I had to abandon this project as other things came up.
When I got home to actually look at the Ubuntu box it had gone to "sleep" and was showing the login box to unlock the keychain. (The background still showed the logged in session, behind the keychain box) 
Since Vino requires login to start its services could this be a reason why the VNC sessions were timing out?
Even though SSH could still connect?

---

### Post by CharlesA on 2010-12-19
> **new2linux09 said:**
> Sorry I had to abandon this project as other things came up.
When I got home to actually look at the Ubuntu box it had gone to "sleep" and was showing the login box to unlock the keychain. (The background still showed the logged in session, behind the keychain box) 
Since Vino requires login to start its services could this be a reason why the VNC sessions were timing out?
Even though SSH could still connect?
That was the problem. To get around the keyring password part, you would have to set the keyring password to <blank>.

If it's prompting for you to enter the keyring password, it won't let you connect.

---

### Post by new2linux09 on 2010-12-19
Ok, It was set to auto login for that user account and this was the first I'd seen it ask for the keyring. 
So if I simply remove the password for that account and set it to auto login that should solve the issue?

---

### Post by CharlesA on 2010-12-19
> **new2linux09 said:**
> Ok, It was set to auto login for that user account and this was the first I'd seen it ask for the keyring. 
So if I simply remove the password for that account and set it to auto login that should solve the issue?
You can leave a password on the account, but you'd have to set the keyring password to nothing.

See here: [http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

---

### Post by new2linux09 on 2010-12-19
Ok, I'll give this a try and see if that solves it. It will be a few weeks before I'm able to fully test it again from a WAN connection. Since this worked fine within the LAN I'm guessing this will solve it.

Thank you for the help in resolving it.

---

