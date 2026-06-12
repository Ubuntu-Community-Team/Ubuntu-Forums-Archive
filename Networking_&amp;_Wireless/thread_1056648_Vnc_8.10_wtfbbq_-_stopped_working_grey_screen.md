---
title: "Vnc 8.10 wtfbbq - stopped working grey screen"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by syborfical on 2009-02-01
I had VNC working just the way I wanted it on my sever. To be able to run it headless so I can just login and do stuff. 

I also have VNC and 8.10 it on a VM. The VM still works fine.

Today I booted my server and rather than just getting the normal login screen i get a grey window with a curse. WTF?

can anyone help.

Also here is all the stuff i did to get VNC working with resume able sessions 


 HOW TO: setup vnc4server
(a bunch of this was taken from L4mp's guide, with sirspiddy's input, all of which appears to be adapted from Tichondrius' guide. I've just defragged and recompiled them to form this

The HOW TO: setup vnc4server guide

this is for those of you who agree that 'remote desktop' is too slow, and freenx is too complicated.

############ Begin ############

1) setup XDMCP:
click System -> Administration -> Login Window
click Remote tab
select "Same as Local"
click Configure XDMCP
remove check from Honour indirect requests

2) configure remote greeter:
Code:

sudo gedit /etc/gdm/gdm.conf

find this line:
Code:

# RemoteGreeter=/usr/lib/gdm/gdmlogin

replace with:
Code:

RemoteGreeter=/usr/lib/gdm/gdmlogin

Note: Before doing the next step, you need to make sure the extra repositories (e.g. universe) are enabled:
[http://easylinux.info/wiki/Ubuntu#Ho...a_repositories](http://easylinux.info/wiki/Ubuntu#Ho...a_repositories)

3) Install required packages:
Code:

sudo apt-get install vnc4server xinetd

sudo apt-get install vnc4server/edgy

Note to AMD64 users: The current version of vnc4server in the repositories has a bug, so you need to download and install the fixed vnc4 packages as shown below:
Code:

wget [http://qt1.iq.usp.br/download/vnc4server_4.0-7.3_amd64.deb](http://qt1.iq.usp.br/download/vnc4server_4.0-7.3_amd64.deb) wget [http://qt1.iq.usp.br/download/xvnc4viewer_4.0-7.3_amd64.deb](http://qt1.iq.usp.br/download/xvnc4viewer_4.0-7.3_amd64.deb) sudo dpkg -i vnc4server_4.0-7.3_amd64.deb sudo dpkg -i xvnc4viewer_4.0-7.3_amd64.deb

4) Set the VNC passwd:
Code:

sudo vncpasswd /root/.vncpasswd

5) Define the VNC service criteria:
Code:

sudo gedit /etc/xinetd.d/Xvnc

and copy this into it:
Code:

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5901
}

###### REAL WORKIN 
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5901
}
 ######


save and exit

6) Reinitialize the service with new criteria:
Code:

sudo /etc/init.d/xinetd stop
sudo killall Xvnc
sudo /etc/init.d/xinetd start

7) add to xorg.conf
***By it self or at the top of the file***

Section "Module"
	Load "vnc"
EndSection

****remember to add the VNC bits :P****

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        Option "SecurityTypes" "VncAuth"
        Option "UserPasswdVerifier" "VncAuth"
        Option "PasswordFile" "/root/.vnc/passwd"
EndSection


7) Test the connection:
Code:

vncviewer localhost:1

---

### Post by syborfical on 2009-02-02
[IMG]http://members.wideband.net.au/syborfical/Xvnc.png[/IMG]
This is what i get when ether VNCing from a remote machine or 
from by typing vncviewer localhost:1

---

### Post by syborfical on 2009-02-20
Bump !!!

---

### Post by jaket on 2009-05-12
I'm having the same problem - any luck fixing this?

---

### Post by switch10 on 2009-06-06
same prob.  It seems like Ubuntu works great at first, and then stuff just stops working with no explanation.  I don't get it

---

### Post by pkutter on 2009-07-21
Edit /home/username/.vnc/xstartup

# Uncomment the following two lines for normal desktop:

#unset SESSION_MANAGER
#exec /etc/X11/xinit/xinitrc

---

### Post by superprash2003 on 2009-07-21
have you tried disabling compiz or extra effects on that machine?

---

### Post by onurbiccud on 2009-11-07
it worked for me, thanks

---

