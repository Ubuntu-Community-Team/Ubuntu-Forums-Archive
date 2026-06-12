---
title: "Start remote desktop via SSH (Jaunty)"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by shelzmike on 2009-08-10
Hello - I am using a headless server, simply by using the remote desktop (built-in vnc) in Ubuntu and connecting from my Vista machine using TightVNC. All works well, UNTIL I have to restart the Linux server for one reason or another. So, I am guessing that remote-desktop does not start until the first log in on the machine itself. Quite a catch 22 with a headless server. 

I know that I can (and have already set up) SSH into the machine, but what is the terminal command that starts the remote-desktop via ssh. IS this possible?

oh, the info I have may be old, but I tried running: gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true

and that does not seem to work.

Thanks.

Mike

---

### Post by Macchi on 2009-08-10
Mike,

Sorry I don't have a prompt solution for your VNC desktop access, but facing a similar situation for remote access of a headless server I have used FreeNX. It allows ssh-encrypted remote desktops from Win/Mac/Linux clients.
Just download the [packages]("http://www.nomachine.com/download-package.php?Prod_Id=992") (only free as free beer) for the node, client and server, install them with dpkg -i and you are ready to go.
NX is fast, secure and easy to set up. Unfortunately it is not a true open source since the free version is limited to two users. So we don't see so many warm recommendations for nomachine products around here.



PS: A warning is that Ubuntu may have some issues with authorization for remote administration of some functions. I hope that you will not run into that as I did.

---

### Post by shelzmike on 2009-08-10
Thank you for the reply. I appreciate your suggestion, but I am just sure there has got to be a way to start the remote desktop via the terminal (or at least hope that there is!) using SSH. I may end up having to try your solution; however, I really like to keep this box lean and the less things that are on it the better. 

Does anyone know - is remote desktop a service? If so, I should be able to set it up to start on start-up? I will keep looking! Thanks again!

Mike

---

### Post by kerouac888 on 2009-08-11
I have a similar setup. I ssh into the server when it starts up and use the command vncserver :1 . Where the ":1" is the workspace number. If you dont have gdm running you can use ":0" . It works for me at least.

---

### Post by shelzmike on 2009-08-11
Thanks for the suggestion. I knew that you could start it this way, but thought that was only if I was using VNC secondary with what comes with Ubuntu remote desktop. (When I use TightVNC to connect, I do not have to specify any port, so I think that :0 would work) Next time I reboot, I will try that. Thanks again!

Mike

---

### Post by iseeuu on 2009-08-13
> **shelzmike said:**
> Hello - I am using a headless server, simply by using the remote desktop (built-in vnc) in Ubuntu and connecting from my Vista machine using TightVNC. All works well, UNTIL I have to restart the Linux server for one reason or another. So, I am guessing that remote-desktop does not start until the first log in on the machine itself. Quite a catch 22 with a headless server.There is a really simple solution to using the vino Remote Desktop in Ubuntu 9.04. I don't require all the "security" here in my home network as I allow no outside access to the home network. (If I did, I would want a secure connection. As it is, in order to access my home network remotely I would have to pay for a static IP address service. Not!) I just want to be able to read my Thunderbird mail running on my Linux box from my windows box in another room.

Solution: "Auto Login"  You can select this option when installing Ubuntu or use the "Login Window Preferences."

[IMG]http://ubuntuforums.org/picture.php?albumid=1299&pictureid=4583[/IMG]

You can still require a passwd in the "Remote Desktop Preferences."

[IMG]http://ubuntuforums.org/picture.php?albumid=1299&pictureid=4584[/IMG]

This feature allows me to connect via ultraVNC from windows to the Remote Desktop on Ubuntu without hours or days of experimentation and configuration. NOT secure, but simple.

Robert

---

### Post by shelzmike on 2009-08-13
LOL! I ALWAYS make things way too hard! I really need to remember to keep it simple..that is an excellent solution. Thanks for that!

Mike

---

### Post by MeumFidet on 2009-08-17
Hi,

How would you do this without physical access to the server?  I am trying to get remote access to a virtual server as my command line skills are crap (linux newbie).  I have installed tightvnc viewer and putty to my vista system, and putty connects with no problem.  Typing in:
*vncserver :1*

 to putty gives me 

[I]The program 'vncserver' can be found in the following packages:
 * tightvncserver
 * vnc4server[/I]

so I installed tightvnc server to the ubuntu server.  I then typed in:

*vncserver: 1*

which gave me:

[I]Creating default startup script /home/paul/.vnc/xstartup
Starting applications specified in /home/paul/.vnc/xstartup
Log file is /home/paul/.vnc/Server:1.log[/I]

which I assume means the vncserver is up and running?

But...trying to access via tightvnc viewer gives me:

*"failed to connect to server*"

!!

How do I access the remote desktop from my vista machine?  The server is on my home network so there are no port/firewall issues, but I am testing the system as though the server were on the net.. which I would not have physical access to.

Any help would be welcomed! Cheers,

MF

---

### Post by shelzmike on 2009-08-17
Have you allowed remote connections through Nautilis?(the way that iseeuu posted above). If so, it sounds like everything is set up right. What are you typing into your VNC viewer on your Vista machine? VNC listens on port 5900+N (so, in this case above, it would be 5901). So you could type the following in your VNC viewer:

*ipaddress*:5901  or you could use the computer name - like ubuntubox:5901. 

As far as firewall issues, if it is on the network internally, then you may be right; however, just to be sure that is NOT an issue, just open TCP traffic port 5901 and direct it to your Linux box. 

Hopefully that helps.

Mike

---

### Post by Jose Catre-Vandis on 2009-08-17
With autologin, the gui desktop should fire up, for you to then connect with vnc etc

You can use:
```
sudo /etc/init.d/gdm stop
```
and
```
sudo /etc/init.d/gdm start
```

to stop and start the gui as needed from your ssh connection.

---

### Post by MeumFidet on 2009-08-17
> **shelzmike said:**
> Have you allowed remote connections through Nautilis?(the way that iseeuu posted above). If so, it sounds like everything is set up right. What are you typing into your VNC viewer on your Vista machine? VNC listens on port 5900+N (so, in this case above, it would be 5901). So you could type the following in your VNC viewer:

*ipaddress*:5901  or you could use the computer name - like ubuntubox:5901. 

As far as firewall issues, if it is on the network internally, then you may be right; however, just to be sure that is NOT an issue, just open TCP traffic port 5901 and direct it to your Linux box. 

Hopefully that helps.

Mike

Thanks Mike.  I have sorted the router to allow 5900-5909 (& restarted) just in case.  In vncviewer I have just typed in the address of the linux box (191.168.0.100) and have left everything else on default.  Still no joy!



> **Jose Catre-Vandis said:**
> With autologin, the gui desktop should fire up, for you to then connect with vnc etc

You can use:
```
sudo /etc/init.d/gdm stop
```and
```
sudo /etc/init.d/gdm start
```to stop and start the gui as needed from your ssh connection.


Thanks Jose.  I have tried this and all it seems to do is stop and then start the gui on the remote machine - it doesn't appear to have affected the vncviewer login at all.  

Thanks for the speedy replies! 

Cheers,

MF

---

### Post by MeumFidet on 2009-08-17
> **iseeuu said:**
> There is a really simple solution to using the vino Remote Desktop in Ubuntu 9.04. I don't require all the "security" here in my home network as I allow no outside access to the home network. (If I did, I would want a secure connection. As it is, in order to access my home network remotely I would have to pay for a static IP address service. Not!) I just want to be able to read my Thunderbird mail running on my Linux box from my windows box in another room.

Solution: "Auto Login"  You can select this option when installing Ubuntu or use the "Login Window Preferences."

[IMG]http://ubuntuforums.org/picture.php?albumid=1299&pictureid=4583[/IMG]

You can still require a passwd in the "Remote Desktop Preferences."

[IMG]http://ubuntuforums.org/picture.php?albumid=1299&pictureid=4584[/IMG]

This feature allows me to connect via ultraVNC from windows to the Remote Desktop on Ubuntu without hours or days of experimentation and configuration. NOT secure, but simple.

Robert

Hi iseeuu,

I have been looking at how my server is set up and I am sure that you are on the right track.  The system-->preferences-->remote desktop is still saying that no-one can access the desktop. Is there a way to change this via command line? If so, then I guess it would work via ssh wouldn't it?

Cheers,

MF

---

### Post by Jose Catre-Vandis on 2009-08-17
> **MeumFidet said:**
> Thanks Jose.  I have tried this and all it seems to do is stop and then start the gui on the remote machine - it doesn't appear to have affected the vncviewer login at all.MF

Sorry perhaps I wasn't clear enough - or assumed too much!

Assumption 1

That your headless server boots up to a gdm login screen?

Assumption 2

That you can set up an auto login so that instead of booting to the login in screen, your server boots all the way to the desktop without intervention

Assumption 3

That when your server has a "desktop" you can VNC to it

Assumption 4

That you can, even just while setting up, attach a monitor to your server to configure the remote requirements. I think you need to do this one!

The gdm start/stop stuff I posted was simply about shutting down the gui to save on resources, and providing the ability to get the "desktop" back up

---

### Post by MeumFidet on 2009-08-18
> **Jose Catre-Vandis said:**
> Sorry perhaps I wasn't clear enough - or assumed too much!
 
Yeah, sorry Jose - relative newbie here... :-)
 
> **Jose Catre-Vandis said:**
> Assumption 1
 
That your headless server boots up to a gdm login screen?
 
Yes, I have a fixed IP 9.04 desktop edition running with a LAMP installation, FTP and VNC server services running.  I can connect with Firefox, Filezila and Putty, so I know most services are running correctly. (or at least I think I know that is the case)
 
 
> **Jose Catre-Vandis said:**
> Assumption 2
 
That you can set up an auto login so that instead of booting to the login in screen, your server boots all the way to the desktop without intervention
 
 
Um... haven't done that...nope.  But I will have a look at doing that.
 
> **Jose Catre-Vandis said:**
> Assumption 3
 
That when your server has a "desktop" you can VNC to it
 
Erm, well, Putty works and gives me a command line terminal-like interface. But tightVNC viewer doesn't connect.
 
 
> **Jose Catre-Vandis said:**
> Assumption 4
 
That you can, even just while setting up, attach a monitor to your server to configure the remote requirements. I think you need to do this one!
 
Well... yes and also no.  The system I am testing is on my home network, so 'yes' I can do this.  But...the system I will be 'live' on is a virtual server hosted on the net, so 'no' I won't have that option :-(
 
BUt hey... Many thanks for your advice.. I have some bits to go away and look at, even if the learning curve is vertical! Thanks!
 
Cheers,
 
MF

---

### Post by shelzmike on 2009-08-18
Are you specifying the port on your VNC viewer? In the example you gave:

192.168.0.100:5901? (assuming you have started vncserver :1 like you mentioned above. You have to specify the port or you will not get in.

---

### Post by MeumFidet on 2009-08-18
> **shelzmike said:**
> Are you specifying the port on your VNC viewer? In the example you gave:

192.168.0.100:5901? (assuming you have started vncserver :1 like you mentioned above. You have to specify the port or you will not get in.

Hi shelzmike,

Thanks for the help.  Yep, port specified (although error comes back as 192.168.0.100:1 for some reason)....

tricky huh?

MF :-)

---

### Post by shelzmike on 2009-08-18
Is your Ubuntu machine logged in (meaning, if you went to it right now, would you be seeing Nautilis, or would you be seeing a login screen). If you are logged in, try this: just type in the IP address without the port. Under normal circumstances that should connect you directly using the built in Remote Desktop that comes with Ubuntu. 

Can you ping that machine at all? Can you SSH into it? 

I know it must be frustrating, but there has got to be something that we are missing. 

Mike

---

### Post by MeumFidet on 2009-08-20
> **shelzmike said:**
> Is your Ubuntu machine logged in (meaning, if you went to it right now, would you be seeing Nautilis, or would you be seeing a login screen). If you are logged in, try this: just type in the IP address without the port. Under normal circumstances that should connect you directly using the built in Remote Desktop that comes with Ubuntu. 

Can you ping that machine at all? Can you SSH into it? 

I know it must be frustrating, but there has got to be something that we are missing. 

Mike

Hi Mike,

Yeah, frustrating isn't the word! Yep, I can ssh/ftp/https into the 9.04 server quite happily, but in TightVNCViewer on my vista machine, I type in 192.168.0.200 and get "failed to connect to server).

On my other system, 9.04 desktop, I have enabled remote desktop in gui preferences-->remote desktop and this appears to work well, typing in 192.168.0.100 .... so, there must be a way of enabling this via command-line for the 9.04 server system so that I can install a desktop and then use it remotely.  I think.

Just a thought, and this is probably blindingly obvious to anyone who isn't me... does the server *have* to have the desktop enabled to access via vnc?  If so, I will *still* need the cli instruction to enable remote viewing before being able to use vnc anyway(chicken and egg), so I guess that doen't get me much further forward?

Cheers, MF

---

