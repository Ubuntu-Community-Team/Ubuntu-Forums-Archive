---
title: "HOWTO: Headless GNOME VNC Server on Lucid Lynx Desktop"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by regstraton on 2010-05-09
[COLOR="Gray"]I had to do quite a lot of digging before I managed to work out how to do this. It turns out to be reasonably straight forward, and so here is my howto all in one place.[/COLOR]

_Objective:_ [COLOR="RoyalBlue"]Connect to my Ubuntu (Lucid Lynx) Desktop machine (which does not have a screen or keyboard) using a remote desktop viewer and get my usual GNOME desktop interface. And have the desktop persist while I am not disconnected.[/COLOR]

[I][COLOR="YellowGreen"]NOTE: I have recently discovered one niggly issue with some of the keys being messed up. 'm' and 's' in particular? I am looking into it and will update this post when I have resolved it.
[/COLOR][/I]
*The following steps were performed on a freshly installed version of Ubuntu 10.04-desktop. Just for clarity:*
```
user@MyServer:~$ uname -r
2.6.32-21-generic
user@MyServer:~$ cat /etc/issue
Ubuntu 10.04 LTS
```

Install a VNC server. There is a choice of servers I chose the "tight" one.
```
user@MyServer:~$ sudo apt-get install tightvncserver
```

Setup your VNC password. This password isn't very important as my setup will only allow for connections via SSH, so 123456 is what I used. One can possibly disable it?
```
user@MyServer:~$ vncpasswd 
```

At this point or the first time you run 'vncserver' (I forgot to check) the all important and much discussed **~/.vnc/xstartup** file is auto generated. This is the make or break place where  you can either get GNOME over VNC or not. My xstartup which required NO changes was:
```
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession
```

Give the VNC server a test, by running it from the command line.
```
user@MyServer:~$ vncserver

New 'X' desktop is Local:1

Creating default startup script /home/user/.vnc/xstartup
Starting applications specified in /home/user/.vnc/xstartup
Log file is /home/user/.vnc/Local:1.log
```

Try connecting to the VNC server:
```
user@MyServer:~$ vinagre &
* Click [Connect]
* Select Protocol: VNC
* Select Host: localhost:1
* Click [Connect]
```

Ok if that all worked then great!!! It all did for me and my machine was fresh from the CD.

Now we setup the VNC server to run all the time.
*[COLOR="Gray"]There are a variety of ways of doing this. Since this howto requires the use of a SSH shell one could quite easily run the **vncserver** (as we did above to test it) and then **disown** (haven't tested if this is actually required) commands the first time you connect. This would leave the VNC server running until you used the **vncserver --kill** command. This would be a suitable approach if you had many different users wanting to have VNC GNOME desktops.[/COLOR]*

For convenience in a single user setup we can get the VNC server to be started at boot time:
```
user@MyServer:~$ sudo gedit /etc/init.d/vncserver.user &
```

Make the contents of 'vncserver.user' (credits to some smart guy on some blog out there that I couldn't find again. and then I made a few improvements):
```
#!/bin/sh -e
### BEGIN INIT INFO
# Provides: vncserver
# Required-Start: networking
# Default-Start: S
# Default-Stop: 0 6
### END INIT INFO

PATH="$PATH:/usr/X11R6/bin/"

# The Username:Group that will run VNC
export USER="user"
#${RUNAS}

# The display that VNC will use
DISPLAY="1"

# Color depth (between 8 and 32)
DEPTH="16"

# The Desktop geometry to use.
#GEOMETRY="x"
GEOMETRY="800x600"
#GEOMETRY="1024x768"
#GEOMETRY="1280x1024"
#GEMOETRY="1024x600"

SECURE="-localhost"

# The name that the VNC Desktop will have.
NAME="My:VNC"

OPTIONS="-name ${NAME} -depth ${DEPTH} -geometry ${GEOMETRY} ${SECURE} :${DISPLAY}"
#OPTIONS="-name ${NAME} -depth ${DEPTH} :${DISPLAY}"

. /lib/lsb/init-functions

case "$1" in
start)
log_action_begin_msg "Starting vncserver for user &#8216;${USER}&#8217; on localhost:${DISPLAY}"
su ${USER} -c "/usr/bin/vncserver ${OPTIONS}"
;;

stop)
log_action_begin_msg "Stoping vncserver for user &#8216;${USER}&#8217; on localhost:${DISPLAY}"
su ${USER} -c "/usr/bin/vncserver -kill :${DISPLAY}"
;;

restart)
log_action_begin_msg "Restarting vncserver for user &#8216;${USER}&#8217; on localhost:${DISPLAY}"
su ${USER} -c "/usr/bin/vncserver -kill :${DISPLAY}"
su ${USER} -c "/usr/bin/vncserver ${OPTIONS}"
;;
esac

exit 0
```

Set the correct file permissions on 'vncserver'. And check them just for fun;
```
user@MyServer:~$ sudo chmod 755 /etc/init.d/vncserver.user 
user@MyServer:~$ ls /etc/init.d/vncserver.user -l
-rwxr-xr-x 1 root root 1210 2010-05-09 01:40 /etc/init.d/vncserver.user
```

Install 'vncserver.user' to run as a service:
```
user@MyServer:~$ sudo update-rc.d vncserver.user defaults
```

Restart the VNC server:
```
user@MyServer:~$ sudo /etc/init.d/vncserver.user restart
```

Here you can attempt to connect the VNC server again using vinagre. If you want to do so, see above where we did it before. But I'm pretty sure it will work.

Ok if you look in the 'vncserver.user' script you will note I used the '-localhost' option. This permits the VNC server to accept connections *only* from localhost. Not very useful, unless we use SSH to forward in some ports.

Install a SSH server:
```
user@MyServer:~$ sudo apt-get install openssh-server
```

Test the SSH server (type exit to leave the SSH shell if it connects sucessfully):
```
user@MyServer:~$ ssh localhost
> exit
```

Your Secure VNC server is now setup. So now we move to your RemotePC.

[CENTER]--oOo--[/CENTER]

Firstly we need to check what of ssh, vnc and remote desktop clients you need to install:
```
user@RemotePC:~$ dpkg --get-selections | grep 'ssh\|vnc\|vinagre'
```

In the output lines we are looking for the following three lines, there will be other lines, but we are only looking to see if these three are already installed:
```

openssh-client           install
xtightvncviewer          install
vinagre                  install
```

If one or more of the above are missing install the relevant package with one of these commands. Naturally you don't HAVE to use these packages, but that is what this howto does:
```
user@RemotePC:~$ sudo apt-get install openssh-client
user@RemotePC:~$ sudo apt-get install xtightvncviewer
user@RemotePC:~$ sudo apt-get install vinagre
```

*[COLOR="Gray"]You may have noted that I have been using MyServer and RemotePC to refer to different computers. In the commands that follow you will need to replace these with the relevant IP address or network names of your computers.[/COLOR]*

Test a basic SSH connection to your VNC server (MyServer). If it connects type 'exit' to disconnect again:
```
user@RemotePC:~$ ssh user@MyServer
> exit
```

Run 'Remote Desktop Viewer':
```
user@RemotePC:~$ vinagre &
```

And now open a SSH connection, with a local port forwarding.
[COLOR="Gray"]The 127.**10**.0.1 is my choice for a _local_ binding address on RemotePC from which to forward the port 5901 to the MyServer. The 127.0.0.1 is simply the address to which the port is forwarded from MyServer's perspective. The 5901 is basically 5900 + the VNC view number (:1)[/COLOR]:
```
user@RemotePC:~$ ssh -L 127.10.0.1:5901:127.0.0.1:5901 user@MyServer
```

Now once the SSH connection is established, switch back to the 'Remote Desktop Viewer':
```
* Click [Connect]
* Select Protocol: VNC
* Select Host: 127.10.0.1:1
* Click [Connect]
```

And there you go. I hope it worked for you and has saved you a lot of time and hacking about with your "server" PC.

[CENTER]--oOo--[/CENTER]

Chances are that you want this setup so that you can hide your MyServer away some place, possibly without even having a keyboard or screen attached. In this case here are a few more tips to achieve this:

_Wake-On-Lan_: [Wikipedia]("http://en.wikipedia.org/wiki/Wake-on-LAN") This is a feature of a lot of network cards and BIOS's where you can switch the PC on remotely over a network. The configuration is purely a hardware and BIOS thing, no other changes are required on the system you wish to wake up. Unfortunately WOL does not work for WiFi, it has to be cable, though I have seen some interesting attempts at the same for WiFi.

There is a standard package for sending the wakeup packets:
```
user@RemotePC:~$ sudo apt-get install wakeonlan
```
It is easy to do if the machine is on the same network, but a bit more trickey over the internet (and you usually need a machine nearby to do the waking).

Basically to wake a machine it must have its BIOS correctly configured, then you need the MAC address of its network card, which you can find with:
```
user@MyServer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr [COLOR="Red"]**01:23:45:67:89:ab**[/COLOR]
          inet addr:192.168.1.45  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe70::214:aefe:fde6:f5e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:8
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251
```

And then you run wakeonlan like so:
```
user@RemotePC:~$ wakeonlan 01:23:45:67:89:ab
```
Wow! Cool!!

And of course if you can power it on remotely you will want to power it off remotely too. This is easier and you have the option of a variety of shell commands. Take a look at the following commands: **shutdown**, **poweroff**, **pm-hibernate**, **pm-powersave**, **pm-suspend**.

[CENTER]--oOo--[/CENTER]

Above I used the 127._10_.0.1 in the SSH port forwarding command. This is because I have done a fair bit of poor-mans VPN setups and I simply found that using localhost (127.0.0.1) can become constrictive. Especially if I am connecting to multiple machines at the same time. The 10 can actually be any number you like, my preference is just not zero.

If you don't understand SSH port forwarding I'm not surprised I didn't at first either. There is plenty of reading available on the subject.

You may also want to take time to make your SSH server on MyServer more secure by dis-allowing root user logins and only accepting Public Key accompanied logins. There are many other things you can do too. This is also well documented out there. So I'm not going to write yet-another.

---

### Post by Kytrix on 2010-05-14
Hi !

Thank you very much guy !

Before the lucid update I was still using a normal X starting without password with GDM, but after update gdm not want to lauch without screen.

With your tips it works great, thanks :)

---

### Post by poho on 2010-05-28
Awesome guide!

Any chance you got those 'm' and 's' problems sorted?

---

### Post by ceo51378 on 2010-05-28
Excellent guide!  Thank you.  This is exactly what I have been looking for.

---

### Post by getreal on 2010-05-29
> **Kytrix said:**
> Hi !

Before the lucid update I was still using a normal X starting without password with GDM, but after update gdm not want to laucnh without screen.



Yes, it seems that the latest GDM has simply taken away the option to turn on XDMCP, which is what the X terminal uses to log in.  

There's a crazy-long [thread about this in Launchpad]("https://bugs.launchpad.net/gdm/+bug/408417").  But the issue is classed as "won't fix".  There are some suggestions for editing configuration files by hand, which may or may not work for you.  There's also a suggestion to use KDM.  (Which I think was just meant to be sarcastic.)

Nick.

---

### Post by einjen on 2010-05-30
This is ALMOST what I need. The little last bit is that sound output is not working on "MyServer". 

In my setup MyServer is connected to my stereo, so sound output in the vnc-session would be nice (not sound redirected back to the connecting client).


Otherwise, great work!

---

### Post by Hulkiedulkie on 2010-06-04
Thank you very much!

---

### Post by RDV on 2010-06-19
Thanks for the easy to follow instructions. I got things working as described, unfortunately without a monitor attached Ubuntu Lucid will still not boot. I  guess I am back to grumbling and searching for a solution.

---

### Post by .nedberg on 2010-06-19
My solution for the same problem:

Buy this one from eBay: [15Pin HD SVGA VGA Male to Female Gender Adapter Changer]("http://cgi.ebay.com/15Pin-HD-SVGA-VGA-Male-Female-Gender-Adapter-Changer-/160408933774?cmd=ViewItem&pt=LH_DefaultDomain_0&hash=item25591e158e")

Build one of these: [http://www.soerennielsen.dk/mod/VGAdummy/index_en.php](http://www.soerennielsen.dk/mod/VGAdummy/index_en.php)

I used 100 Ohm resistors, I read somewhere that anything from 50-150 will work just fine! It works even if you use a DVI to VGA adapter.

---

### Post by alvaromartinez on 2010-08-05
It worked for me too. Now I can open a gnome session from my Windows notebook. I used putty.exe as ssh client and RealVncViewer as vnc client in the notebook.

Thanks a lot.

Alvaro 
Montevideo, Uruguay

---

### Post by jjjesus on 2010-08-12
I had the same 'm' and 's' problems and none of the recommended solutions worked for me.

Finally, I removed the Panel Widgets in the upper right to which the 'm' and 's' were going: Mail and Shutdown.

Now, 'm' and 's' behave correctly.

---

### Post by kodb on 2010-08-17
Ok, I've followed all the instructions but am still coming up with a grey'd out screen after configuring everything just like shown.  I've tried to connect with tightvncclient from both my 9.10 UNR machine and my windows work machine using win tightvnc with the same result.  All machines are currently on the same wired lan so it isn't an internet issue.

The server I'm working off is a newly installed 10.04 Lucid on a Proliant ml370 box which was running 9.10 flawlessly for about 6 months.  Just did clean reinstall this am and yesterday and want to get the gnome desk setup for ease of admin in the office and possible connection to while on the road teaching.

Any suggestions/fixes?
Thanks everybody in advance!
Bob

---

### Post by .nedberg on 2010-08-17
I think you will find that my solution is the easiest and least problematic. It is also guatanteed to work across updates and reinstalls.

---

### Post by kodb on 2010-08-17
> **.nedberg said:**
> I think you will find that my solution is the easiest and least problematic. It is also guatanteed to work across updates and reinstalls.
 
.nedberg-
The dummy video plugin will obviate/fix the greyscreen issue?
thanks,
Bob

---

### Post by .nedberg on 2010-08-17
It will fake a monitor. So if you get a gray screen telling you that Ubuntu will run in safe graphics mode, then yes, it will work! (not completely sure about the wording, I don't have the problem anymore).

---

### Post by mminorhsd on 2010-10-13
I am trying to connect to the linux server using tightvncserver on the linux machine and real vnc viewer (free version) on a windows machine. I have had the SSH working for several months using putty. When I try to connect using real vnc viewer, I get a message stating Unable to connect to host: Connection refused (10061).

Does anyone have any idea what is missing in my setup?

TIA

Mike

---

### Post by albundy79 on 2011-10-26
I got problem with VNC since the last update in Ubuntu 11.1,
VNC simply dont work! I just get a black screen.

I even tried to install KDE and XFCE without any success.

Is there any way to get back Ubuntu 10 or do you know a solution to this issue?

---

### Post by abmurphy on 2011-10-28
really well done howto. I had been messing with this for a while and once I found your post I got it to work straight away. thanks!

BTW my setup is as follows: 
 my remote machine is actually a 10.04 running in virtual box on a windows 7 host system at my home. 

 My server is a Ubuntu 10.04 running on an older pc tower I am configuring to run as an headless server at a remote location in another state.

again, thanks for the great post

---

