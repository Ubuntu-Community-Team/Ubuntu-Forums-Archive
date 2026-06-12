---
title: "Remote Desktop from PDA (hTC Touch Diamond)"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by marginean.m on 2009-10-18
Hi all! I have a PDA with WinMo 6.1 and I want to remotely connect it to my ubuntu desktop. 

**DETAILS:**
  -my PDA: hTC Touch Diamond

  -my ubuntu connects to the internet through a (MSI) router that has a PPPoE connection

  -I set up the Remote Desktop in ubuntu and got something like "*Your desktop is only reachable over the local network. Others can access your computer using the address 192.168.x.xxx , x.local.*"

  -Then I noticed that "192.168.1.100" was a link to "vnc://192.168.x.xxx::5000"

  -Also the "x.local" was a link to "vnc://x.local::5000"

 - oh...and yes...I'd like to remote connect NOT only from the local network![-X

If someone already got this kind of connection working, please,please share.

 **Thanks!** 
                   *over&out* ):P):P](*,)

---

### Post by marginean.m on 2010-02-20
ok! After some searching/learning/trying I finally got it working. Here is how you do it:

NOTES:
- PDA: hTC Touch Diamond with custom ROM (DiaDuit)
- PC: ubuntu 9.10 karmic koala
- internet connection (PC): through a MSI wireless router
- internet connection (PDA): orange 3G (my provider)

1. get the VNC Client (for PDA) from below this post (vncviewer).
2. set your linux box:
- press ALT+F2 to open the "Run App" dialog
- enter "gconftool -u /desktop/gnome/remote_access/network_interface" and hit RUN
(if you don't have karmic see this for help: [https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers))
- configure the Vino application (this is the default VNC server in ubuntu based distros): [http://www.debianadmin.com/remote-de...in-ubuntu.html](http://www.debianadmin.com/remote-de...in-ubuntu.html)
3. configure your router (if you have one): just forward the ports 5800 and 5900 for your local IP (mine is 192.168.1.100). You can use other ports; just have to change these default ones in vncviewer and ofcourse to forward them properly. 
4. find your external IP ([http://www.ip-adress.com/](http://www.ip-adress.com/)) and enter it in the vncviewer. Type your password. Hit ENTER!
5. scare your girlfriend and make her think the computer is possessed. (Well...in fact it is ! ;))

---

