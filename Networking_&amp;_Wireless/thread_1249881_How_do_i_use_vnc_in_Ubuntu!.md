---
title: "How do i use vnc in Ubuntu?!"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by keiichidono on 2009-08-25
I try different programs and Google time after time but it never works! Someone, please tell me how to vnc Ubuntu to Ubuntu and Windows to Ubuntu! :confused: :(

---

### Post by dmizer on 2009-08-25
What programs have you tried? What doesn't work? Do you get any errors? What do the errors say?

You should be able to configure remote desktop by going to system > preferences > remote desktop, and you should be able to view your remote desktop by going to applications > network > remote desktop

---

### Post by keiichidono on 2009-08-25
Pretty much all the vnc apps in the repo. "Your desktop is only reachable over the local network. Others can access your computer using the address 10.0.2.15 , keiichi-desktop.local" is all i get outta remote desktop.

---

### Post by dmizer on 2009-08-25
> **CalvinB said:**
> Pretty much all the vnc apps in the repo. "Your desktop is only reachable over the local network. Others can access your computer using the address 10.0.2.15 , keiichi-desktop.local" is all i get outta remote desktop.

Are you trying to VNC over the internet? This is unsafe unless you tunnel it through SSH.

---

### Post by keiichidono on 2009-08-25
> **dmizer said:**
> Are you trying to VNC over the internet? This is unsafe unless you tunnel it through SSH.

Yeah, and why? How to set up ssh?

---

### Post by dmizer on 2009-08-25
Because VNC is not hardened for internet access. The only thing that keeps you from getting pwned is a password. Even if you have an extremely long password and lots of random characters, this isn't enough anymore.

For Ubuntu to Ubuntu, it's fairly simple:
```
vncviewer -via user@host localhost:0
```

---

### Post by keiichidono on 2009-08-26
That'll set up ssh from my machine to someone else's if they have vnc client open?

---

### Post by peepingtom on 2009-08-26
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

Best of luck, don't get owned.
Use SSH, it's important and pretty cool! You can do lots of stuff like proxies and low-bandwidth remote administration with it. VNC isn't necessary for many things, you might find.

---

### Post by dmizer on 2009-08-26
> **CalvinB said:**
> That'll set up ssh from my machine to someone else's if they have vnc client open?

No. That will allow you to connect to your own desktop from a remote location.

Neither VNC nor SSH can pass through firewalls unless the person you are trying to connect to has opened and forwarded the correct port.

---

### Post by keiichidono on 2009-08-27
I am still terribly confused.

---

### Post by nhanquy on 2009-08-27
**SSH and VNC**

see : /etc/ssh/sshd_config to select port for SSH
 
for example [http://www.brainonfire.net/blog/vnc-over-ssh/](http://www.brainonfire.net/blog/vnc-over-ssh/)     use  port 8443

VNC client on port 5900 talking to SSH client port 5900 talking to SSH server port 8443
VNC server receives messages from port 5900 locally which came from SSH server who listens to port 8443

The machine running VNC server has to have port 8443 open so the client can get through.

**more on VNC **

read 
[https://help.ubuntu.com/community/VNC?action=show&redirect=VNCOverSSH](https://help.ubuntu.com/community/VNC?action=show&redirect=VNCOverSSH)

remember to put this in .vnc/xstartup:

[INDENT]export XKL_XMODMAP_DISABLE=1

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-window-manager &
/etc/X11/Xsession
[/INDENT]
on the server start** vncserver** (through ssh session for example) then the client can connect with **vncviewer**

---

### Post by keiichidono on 2009-10-10
I need to connect to a friend's computer to help him out with his new Linux Mint install, how do I do this? I looked up on ssh and it's really confusing, I want to do vnc. Can I get some help with this, maybe someone can connect to my machine and show me how?

---

### Post by keiichidono on 2009-10-10
[bump]

---

### Post by Zoandar on 2009-10-11
I am new to Linux too, but I'll try to help as much as I can. 

i am using Ubuntu 9.04 on a notebook and able to VNC to a Windows XP PC, but I can't help you VNC to another Linux PC. All I can tell you is that I was able to do this only after I set up the freeware "RealVNC" running on the Windows PC (so it is a server). I was not able to figure out how to install the Linux version of RealVNC, so I installed GTK VNC Viewer for Ubuntu, and that let me through to the Windows PC. 

The Remote Desktop Viewer will also do the same thing from Ubuntu for me now, and it comes with Ununtu when you install it. So I think what you are needing to do is install some sort of Linux VNC Server program on your friend's PC, and you can probably just use Remote Desktop Viewer on your own Linux PC to view his once it is set up. 

In my case, I have to identify (log in) the Windows PC running RealVNC by supplying the DHCP-assigned IP address my router gives that PC, and then a password that I set when I installed RealVNC. 

Maybe some of this info will be helpful. I haven't tried doing this from Windows to Linux or could be a bit more helpful maybe. Sorry. 

Keep searching the forums and the internet. I know sometimes that takes a lot of time, but it is how you will find the answer eventually. 

I should mention that I had LogMeIn's free VNC set up between windows PCs here and it works fine, but for some reason the plug-in they have for Firefox in the Linux OS doesn't work. It seems to be logging me in, but then Firefox crashes and closes. Many people report this issue online. Unfortunately, LogMeIn isn't dedicated to supporting the Linux OS. 

Good luck!

Zoandar

---

### Post by Zoandar on 2009-10-11
You may also find this interesting:

[https://launchpad.net/remote-help-assistant/+announcement/2311](https://launchpad.net/remote-help-assistant/+announcement/2311)

This is a project called "Remote Help Assistant" that is being developed to do exactly what it is you are wanting to do, yet make doing it easier. I would try it, but I think it only works between Linux PCs.  They have released 2 versions of the software, so it may be up and running by now. 

Zoandar

---

### Post by quixote on 2009-11-22
Zoandar: thanks for the tip about Remote Help Assistant.  That's an excellent program!  I just tried it out.  It really works and it really is easy to use.  I'm pretty much with CalvinB on my eyes glazing over with all the ssh / vnc /vpn intricacies.  But even I could get RHA working flawlessly in a couple of minutes.  Don't be put off by the beta tag.  It seems to just work.  (I tried it on two ubuntu 9.04 machines.)

---

### Post by em3raldxiii on 2009-12-04
Okay, first off, I will try to bring this down to layman speak because I am like that ... I often have a hard time with the technical stuff.

1.  Sounds like you want to be able to see & control your friend's computer using Remote Desktop.  From what I can tell, Ubuntu comes with a program called *vino* which apparently does all this stuff.

2.  By default, these programs are not intended to be used across the WAN (internet outside your home network) due to security reasons.  Apparently using SSH is supposed to make it magically safer, but I don't really know about all that junk.  I like to point and click to make stuff go, know what I am saying?

3.  In order to make Remote Desktop (vino) work outside your (and your friend's) home networks (across the internet), you may have to configure your router and/or firewall to open certain ports and/or port-forward specific ports to specific computers on your LAN.

Now, here is what I did to make it work (*** REMEMBER, THIS IS NOT VERY SECURE, SO PLEASE LOOK INTO THE MORE SECURE METHODS OTHERS HAVE MENTIONED ***).  This is quite specific to Ubuntu 9.10 because I make use of the Ubuntu Software Centre.

A.  Open Ubuntu Software Center and ensure you have "Remote Desktop" and "Remote Desktop Viewer" installed.  You can check by clicking on Installed Software and doing a search for VNC.  If not, you will want to make sure you install those pieces of software.

B.  On the "computer that needs to be viewed", click on System > Preferences > Remote Desktop, and check the boxes that apply to you.  To take full control of your friend's computer, you want to have the boxes for  "allow other users to view", and "allow other users to control" selected.  Also, make sure you have "You must confirm", "Use this password", and "Configure to Automatically ..." selected.  Choose a good strong password that has upper and lower case letters, as well as numbers and maybe the odd symbol.  Going with a weak password here is REALLY asking for trouble.

Make note of the section near the top of that window where it tells you the IP address that others can use to connect to your computer.  You may want to write that down (should be your WAN IP address).  If you don't get a WAN address there (something starting with 192.0.x.x would only be your Local address, for example), you may have to configure your router or your firewall to open those ports.  That is beyond the scope of this article because I didn't have to do that, and I don't really know which specific ports are required.  Some of the previous posts seem to cover that though.

C.  On your computer (the one that will be viewing the other computer), go to Applications > Internet > Remote Desktop Viewer.  Click on the CONNECT button.  In the new window, you want to choose VNC (should already be that), and put in the IP address we wrote down in step B (for the other computer).  I have found that Full Screen kinda sucks (stuff might go off-screen), and Scaling is good (makes their screen fit inside a window on your computer).  Click on Connect.  You will now have to enter the password you chose in step B, hopefully it is a nice long, complicated password.

D.  You should now have control of the other computer.  If you see the mouse, that is good, if you can move the mouse to click on menus that is good, and if you see the menu when you click, then you are good to go.  However, if you click on the menu and you do not see it drop down on your screen (but your friend DOES see his menu drop down), then you will have to disable the advanced desktop effects (the compiz-fusion stuff, like wobbly windows).  Just get your friend to turn the effects right off while you are doing the remote desktop control.  You may have to reconnect and stuff ... not sure about that part.

E.  When you are totally done controlling his computer, and are ready to end your session, you can just close that tab in your viewer.  On your friend's computer, it would be a VERY good idea to disable the remote desktop stuff again in order to return to a more secure state.

F.  Now, go and learn the more complicated stuff about SSH and whatnot in order to do all of the above a lot more safely.  That's what I am going to do right now.

I hope this helps you!

---

