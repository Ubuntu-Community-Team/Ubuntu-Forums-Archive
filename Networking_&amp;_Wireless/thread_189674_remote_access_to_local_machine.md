---
title: "remote access to local machine"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by kriding on 2006-06-05
I have 2 machines running on a local network, using a powerline router as my network interface and internet connection.

One machine is Ubuntu Dapper and the other is WinXP, I would like to have remote access over the XP box so I don't have to keep trapsing over to it whenever it goes wrong (just call me lazy, but if i can access it via my machine..why not:D )

I have Samba installed and can see/access files on the XP box, and the shares i setup work fine (although i still can't manipulate files on the UBUNTU box from the XP box)

I have searched the forum and the wiki, but everything I have found I have problems working out. Is there a real 'thick gits' idots guide to setting this up?

I know very little about SSH and i tried freenx but couldn't set it up.

TIA for any help you can give me

---

### Post by Belarios on 2006-06-05
You've named two excellent ways of accessing your computer remotely.  SSH is text only.  FreeNX gives you a remote graphical user interface.

First decide what you want to do remotely.  Then decide whether you need the full graphical desktop to do it, or whether you can learn the text command line way of doing it.  If you're just issuing a few commands, like doing security updates, those can be done simply through a text interface.

Some specific applications also have a web browser interface, which can be very convenient.  (Samba has a web interface called SWAT.  Although I didn't manage to get it working on earlier versions of Ubuntu, I hear it might work easier on Dapper.)

---

### Post by kriding on 2006-06-05
I would like to access the XP box in the same/similar way as 'remote desktop' or PC Anywhere, that way, if something needs attention which would take very little time, or would be easier for me to do then try and talk my girlfriend through it. Eventually i would like to expand it to accessing either box from a remote location, but small steps and all that.

I have managed to install putty on the XP box and access my UBUNTU from it, but I can't get VNC to work or even installed on my UBUNTU

---

### Post by Belarios on 2006-06-05
OK, so you want the full graphical desktop.  There are a few ways to do it.

VNC and TightVNC are both in the Ubuntu repositories, that is, they are maintained by Ubuntu developers and tailored for Ubuntu.  Freenx is not in the official Ubuntu repositories and so requires a few extra steps to set up.  I've messed around with all three, and Freenx was zippier for me (I believe that it does a better job of compressing the data that is traveling the network).

Basically you run a server on the Ubuntu box which listens for connections, and you run a client application on the Windows box.  Since being able to control a computer remotely raises security concerns, setup usually involves creating some type of security key files.

So now decide if you want to stick with the system maintained by the Ubuntu people and install TightVNC (or VNC) or if you want to go the extra few steps and install Freenx.

You said that you tried to do Freenx and couldn't configure it.  So if you want to do Freenx, you need to describe everything you did, and what error messages you got so people here can help diagnose the problem.    Did you use a HOWTO from this forum such as the one in this thread?  [http://ubuntuforums.org/showthread.php?p=917050#post917050](http://ubuntuforums.org/showthread.php?p=917050#post917050)

---

### Post by Belarios on 2006-06-05
I see from looking at that HOWTO that it's a few weeks old and that the Seveas repositories have a Dapper branch now, so you should use 

```
deb http://free.linux.hp.com/~brett/seveas/freenx dapper-seveas freenx
deb-src http://free.linux.hp.com/~brett/seveas/freenx dapper-seveas freenx
```

instead of the breezy ones.  (see [here](http://free.linux.hp.com/~brett/seveas/freenx/dists/dapper-seveas/freenx/)).

---

### Post by kriding on 2006-06-05
I have managed to install freenx (took some time and effort, and I have a splitting headache now) but I can't seem to connect it to my windows box

edit: I installed the client onto the windows box, and can connect from there to my ubuntu box with limited capability, just need to figure out how to conect to the windows box

---

### Post by Belarios on 2006-06-05
Good work.  So you've downloaded the windows client from [http://www.nomachine.com/download_client_windows.php](http://www.nomachine.com/download_client_windows.php) and put in the ip address of the ubuntu box and the windows client gives you an error?

---

### Post by kriding on 2006-06-05
I can connect to the ubuntu box from the xp one, there's no problem there (other then I can't access many of the things from ubuntu via the windows box, but that is not a real problem as it's my girlfriends machine and she doesn't need to do anything)

I now need to setup the app on my machine to access the windows box.

When I go through the setup, I change the server host to my localhost ip, the desktop is set to 'windows'. Under the settings tab, the windows terminal server has me baffled, I set it to the IP of the box i'm trying to connect and set the domain to the mshomew which is the default one. The user name and password I set to show me the windows login screen

Under session type, i set that to desktop

Is there something I'm setting wrong or missing?

---

### Post by Belarios on 2006-06-05
OK, so you're trying to connect to the WinXP machine from Ubuntu.  Are you using the NX for Linux client?  Is Remote Desktop on the Windows machine set to Allow Users to Connect Remotely?  Is the Windows firewall allowing connections on port 3389?  What error are you getting from the NX for Linux client?

This sounds like a Windows issue and I know almost nothing about setting up the RDP server on WindowsXP, but I'd check those things first.

Perhaps someone with more Windows administration experience can help with this one.

---

### Post by Belarios on 2006-06-05
Also, instead of using the NX client for linux, try 
```
rdesktop [ip address of the windowsxp machine]
```

---

### Post by unicycler on 2006-06-05
Are you using Windows XP home or XP Pro? Pro will allow for a Remote Desktop Connection, while home will only allow for Remote assistance. On the Windows side, instead of doing the Windows Remote connection, you can run an "UltraVNC" server and use a VNC client on Ubuntu.

---

### Post by kriding on 2006-06-06
@ Belarios; on my linux box i'm using the nx server app I installed, and theclient on my windows (should this be reversed so I use the windows as a server instead?) the windows firewall is disabled and the error message i get is "session 'kevin' failed" It does go through the authentication ok and starts the x server connection just before it fails.

I tried the rdesktop method and that says the connection was refused.

@ unicycler; I'm using XP home

---

### Post by kriding on 2006-06-06
I have installed ulrtaVNC on the windows box, and have tried installing the client from the repos, but nothing shows up on my linux ](*,)

---

### Post by edm1 on 2006-06-06
[QUOTE=kriding]I have installed ulrtaVNC on the windows box, and have tried installing the client from the repos, but nothing shows up on my linux ](*,)[/QUOTE]

have you tried

```
$ vncviewer
```

?

---

### Post by fgr on 2006-06-29
One machine is Ubuntu Dapper and the other is WinXP, I would like to have remote access over the XP box so I don't have to keep trapsing over to it whenever it goes wrong (just call me lazy, but if i can access it via my machine..why not:D )

I use krdc on dapper and it works perfect! (vnc and rdp)!

---

