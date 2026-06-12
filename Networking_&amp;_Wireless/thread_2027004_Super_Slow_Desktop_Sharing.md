---
title: "Super Slow Desktop Sharing"
date: 2012-07-16
forum: Networking &amp; Wireless
---

### Post by omiazad on 2012-07-16
Hi,
[IMG]http://i45.tinypic.com/o0e2l4.png[/IMG]

This is the sharing server running on my desktop, but when I access the desktop from a remote machine (client is Ubuntu, Windows with UVNC), refrash rate is VERY slow. 

[IMG]http://i45.tinypic.com/2h2dxg4.png[/IMG]
However when I shared my Linux Mint desktop, it's not as slow as Ubuntu.

Do you know any solution for this problem?

---

### Post by Ubun2to on 2012-07-16
Have you ever tried TeamViewer?
Just saying, it works across Windows, OSX, and Linux without a hitch.
Anyway, I think it sounds like it's a problem with the application itself. Try reinstalling GNOME Desktop Sharing.

---

### Post by omiazad on 2012-07-16
> **Ubun2to said:**
> Have you ever tried TeamViewer?
Just saying, it works across Windows, OSX, and Linux without a hitch.
Anyway, I think it sounds like it's a problem with the application itself. Try reinstalling GNOME Desktop Sharing.

TeamViewer is a very bad choice as that is not an native app for Linux. It runs on Wine and VERY BAD performance. :(

---

### Post by Ubun2to on 2012-07-17
> **omiazad said:**
> TeamViewer is a very bad choice as that is not an native app for Linux. It runs on Wine and VERY BAD performance. :(

For me, it works great.

---

### Post by omiazad on 2012-07-17
> **Ubun2to said:**
> For me, it works great.

Glad to know that :)

---

### Post by TheFu on 2012-07-17
> **omiazad said:**
> Hi,
This is the sharing server running on my desktop, but when I access the desktop from a remote machine (client is Ubuntu, Windows with UVNC), refrash rate is VERY slow. 

However when I shared my Linux Mint desktop, it's not as slow as Ubuntu.

Do you know any solution for this problem?

Are you trying this over WiFi? Try wired first, to see if wifi is your issue.

Do you need VNC or would a more efficient protocol be possible, like NX?
**FreeNX** is the server. It must be twice as efficient as VNC. I think the pkg is  freenx-server on ubuntu. You'll need a client, but those exist for most of the popular OSes (OSX, Windows, Linux, BSD).
Another option is called SPICE. [http://www.spice-space.org/](http://www.spice-space.org/)  It is new and claims to make remote desktops almost native performance.

I use NX when a GUI is needed to remote into Mom's PC 4 states away. I've used it over a 14.4K dial up and was happy. It is THAT good.  Of course, ssh is much more efficient when you don't need a GUI.


If you need to keep using VNC, which specific options are used on each client and the server? Are they compatible or does the negotiation fall-back automatically?  Does one have compression enabled or does it reduce the color map more?  What do the log files show?   At this point you have a general, "maybe" problem. Without specific data from running processes and log files, there isn't much we can use.  Did you measure how much slower doing the same thing is with a stopwatch? While that isn't too useful, it would be a fact - better than "slower" from a quantitative perspective.

Facts and data are needed.

---

### Post by omiazad on 2012-07-17
> **TheFu said:**
> Are you trying this over WiFi? Try wired first, to see if wifi is your issue.

Do you need VNC or would a more efficient protocol be possible, like NX?
**FreeNX** is the server. It must be twice as efficient as VNC. I think the pkg is  freenx-server on ubuntu. You'll need a client, but those exist for most of the popular OSes (OSX, Windows, Linux, BSD).
Another option is called SPICE. [http://www.spice-space.org/](http://www.spice-space.org/)  It is new and claims to make remote desktops almost native performance.

I use NX when a GUI is needed to remote into Mom's PC 4 states away. I've used it over a 14.4K dial up and was happy. It is THAT good.  Of course, ssh is much more efficient when you don't need a GUI.


If you need to keep using VNC, which specific options are used on each client and the server? Are they compatible or does the negotiation fall-back automatically?  Does one have compression enabled or does it reduce the color map more?  What do the log files show?   At this point you have a general, "maybe" problem. Without specific data from running processes and log files, there isn't much we can use.  Did you measure how much slower doing the same thing is with a stopwatch? While that isn't too useful, it would be a fact - better than "slower" from a quantitative perspective.

Facts and data are needed.

Thanks for your detail response. See, I'm not a geek and don't want to be. Just want to use Ubuntu for my day to day work. So shell is not a solution for me.

Did you use Free NX on Ubuntu 12.04? I tried Nomachine NX server as it's less pain to install, but when I connect with client, I don't see any menu or anything from the client. In the Nomachine NX client, you have to select the desktop environment and Unity is not available there. So if Free NX do not have any magic, that may not work. :(

I tried Wifi, wired everything. No luck. Mint is working, Ubuntu is not. I don't know where to set options in VNC server in Linux.

---

### Post by TheFu on 2012-07-17
> **omiazad said:**
> Thanks for your detail response. See, I'm not a geek and don't want to be. Just want to use Ubuntu for my day to day work. So shell is not a solution for me.

Did you use Free NX on Ubuntu 12.04? I tried Nomachine NX server as it's less pain to install, but when I connect with client, I don't see any menu or anything from the client. In the Nomachine NX client, you have to select the desktop environment and Unity is not available there. So if Free NX do not have any magic, that may not work. :(

I tried Wifi, wired everything. No luck. Mint is working, Ubuntu is not. I don't know where to set options in VNC server in Linux.

What OS and version is your server running? Our remote access server runs 10.04 still - 12.04 is too new for us to trust yet.

Do you have the ability to install programs on the server?

I've used qtnx on 10.04 desktop.  Don't use Unity, sorry.  Haven't needed to try NX on 12.04, but I'll try that now .... qtNX from the Ubuntu 12.04 repository is on protocol v3.0.0, but my nx-server (Ubuntu 10.04) from 2+ yrs ago is on v3.3.0.

I'll look into an easier NX solution ... but can you install programs on the server?  If not, you really need to find the log files and look for the settings for your VNC client program. Log files are usually in /var/log/ somewhere.  syslog, messages, and if there is anything with a "vnc" in the name, that would be good to look at too.

---

### Post by QIII on 2012-07-17
I use Nomachine NX to remote to a Unity machine.  It's a GNOME session.

However, I think I had to replace lightdm on the server with gdm.

I'll check after work when I get home.

NX is fairly secure (it uses SSH) and much faster and higher quality than VNC.

---

### Post by omiazad on 2012-07-17
> **TheFu said:**
> What OS and version is your server running? Our remote access server runs 10.04 still - 12.04 is too new for us to trust yet.

Do you have the ability to install programs on the server?

I've used qtnx on 10.04 desktop.  Don't use Unity, sorry.  Haven't needed to try NX on 12.04, but I'll try that now .... qtNX from the Ubuntu 12.04 repository is on protocol v3.0.0, but my nx-server (Ubuntu 10.04) from 2+ yrs ago is on v3.3.0.

I'll look into an easier NX solution ... but can you install programs on the server?  If not, you really need to find the log files and look for the settings for your VNC client program. Log files are usually in /var/log/ somewhere.  syslog, messages, and if there is anything with a "vnc" in the name, that would be good to look at too.

The server is running on 12.04 I can try to install things on the server but need step by step GUI solution.

> **QIII said:**
> I use Nomachine NX to remote to a Unity machine. It's a GNOME session.

However, I think I had to replace lightdm on the server with gdm.

I'll check after work when I get home.

NX is fairly secure (it uses SSH) and much faster and higher quality than VNC.

Will appreciate if you let me know the solution QIII.

---

### Post by TheFu on 2012-07-17
> **omiazad said:**
> The server is running on 12.04 I can try to install things on the server but need step by step GUI solution.


The real question was do you have "root" or "sudo" to admin equiv access on the server or does someone else do that work? If someone else does it, then I doubt they are interested in you installing any programs on it. Ask him/her if they are willing to install and setup an NX-Server for you and others. If not, you should troubleshoot your VNC connection issues instead.

There is no GUI on a server. None. Zip. Nada. "Servers" don't have a GUI. Should we bother with CLI commands at all?

---

### Post by QIII on 2012-07-17
The machine hosting the desktop to be shared is called a "server" in both VNC and NX.

---

### Post by QIII on 2012-07-17
@omiazad --

I'm using gdm as my display manager with Unity on the Nomachine server, connecting via Nomachine NX from Xubuntu:

---

### Post by omiazad on 2012-07-17
> **TheFu said:**
> The real question was do you have "root" or "sudo" to admin equiv access on the server or does someone else do that work? If someone else does it, then I doubt they are interested in you installing any programs on it. Ask him/her if they are willing to install and setup an NX-Server for you and others. If not, you should troubleshoot your VNC connection issues instead.

There is no GUI on a server. None. Zip. Nada. "Servers" don't have a GUI. Should we bother with CLI commands at all?

Like I said, I can install things on the server, but before I do, I have to know that the solution will work. I can even check that on my test machine. :)

---

### Post by omiazad on 2012-07-17
> **QIII said:**
> @omiazad --

I'm using gdm as my display manager with Unity on the Nomachine server, connecting via Nomachine NX from Xubuntu:

Is it possible for you to share the settings of the client and a screen shot of the desktop from the client (preferred Windows)?

---

### Post by omiazad on 2012-07-18
Removed Compiz and problem solved.

Thanks for your help.

---

### Post by bmullan on 2012-08-10
Look at x2go.
[URL="http://www.x2go.org/doku.php/wiki:components:start"]
x2go wiki[/URL]

Its the best remote desktop I know of and its open source.   Its also very easy to install.

x2go is under rapid development, works great on windows, mac & linux and is every bit as good as NoMachine's NX... possibly better.

There is also a Python based x2go available.



On you Ubuntu PC that you want to log into from windows:
install x2goserver
install x2goserver-xsession
add any user's to the x2gouser "group"
on client install appropriate x2goclient (windows, mac, linux)
on client create a new session preferences:
put in IP or domain name of Linux server to reach from your client
on the connection tab move the slider as far to the right as you find gives best performance.. understanding that the farther to the right you go on the slider the less compression (re cpu) is used

Click on your new x2go menu session Icon to start the session & login.
The first time you log into a new x2goserver you may get prompted to accept or not the connection to a server that hadn't been seen before... say yes.

Audio, remote printing, remote file/directory sharing all work.

---

