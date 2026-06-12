---
title: "Remote Desktop Connection to Ubuntu from Windows 7"
date: 2012-01-12
forum: Networking &amp; Wireless
---

### Post by oakridge on 2012-01-12
I am an escapee from Mandrake/Mandriva after eight years or more, sadly they just seemed to losing their way.

After settling for Ubuntu and solving a networking problem which was largely my fault I like Ubuntu very much.

So to the problem....  My eyesight is pretty poor so I have a large high definition monitor on my Windows 7 Ultimate machine and if I need to do any administration on I use RDC from that machine.  Now I can connect easily from the Ubuntu to any Windows machine, but not the other way around, which is the way I need it.  On 'Desktop Sharing Preferences I have ticked allow other users to view and control your desktop.  I was not sure what to do about the Security choices so I have tried various combinations without success.  

Thank you.

Malcolm

---

### Post by oakridge on 2012-01-13
Just a further note  The Windows Explorer connects fine and I can ping by IP address and computer name, so it would seem that it is something to do with security on the Ubuntu.  No Firewall is installed.

Thank you.

Malcolm

---

### Post by oakridge on 2012-07-21
I am very anxious to solve this problem so I have been making further tests.

I can control the Windows 7 machine from Ubuntu using 'Remote Desktop Viewer', but the Windows 7 monitor is much higher quality so I lose quite a lot. Unfortunately the monitors cannot be changed.

From the Windows 7 machine using 'TightVNC' I just get a static screen and it is just a grey screen using 'Remote Desktop Connection'.

Thank you.

Malcolm

---

### Post by steeldriver on 2012-07-21
Hi Malcolm it works for me using the UltraVNC viewer on Windows with the standard x11vnc server on Ubuntu - I don't see why TightVNC wouldn't work.

[I have also used remote Desktop Connection from an XP box to Xubuntu 11.10 but not tried it from Windows 7. It doesn't work out of the box though - you will need to install xrdp on the Ubuntu end, and several people have reported issues with that so I'd persevere with VNC if I were you.]

Maybe it's a firewall issue? Windows 7 is kind of funny, even with outbound connections (although the TightVNC client install should have handled that side of things). 

What flavor / version Ubuntu are you running? iirc recent releases have ufw enabled by default - if so have you checked that the appropriate VNC port (5900 + display number) is indeed open?

---

### Post by oakridge on 2012-07-22
Thank you for reply SteelDriver.

The TightVNC port was set to 5500 which I have changed to 5902 to match Ubuntu.

I have checked Windows Firewall and TightVNC Server and Viewer  are checked.

Ubuntu is the latest version - er - 11.04, is it?

Thank you.

Malcolm

---

### Post by steeldriver on 2012-07-22
Hi Malcolm I just installed TightVNC server in a 12.04 virtual machine and TightVNC viewer on the host Windows 7 box and it worked right away

```
steeldriver@desk01-vm:~/Downloads$ tightvncserver

You will require a password to access your desktops.

Password: 
Verify:   
Would you like to enter a view-only password (y/n)? n

New 'X' desktop is desk01-vm:1

Creating default startup script /home/steeldriver/.vnc/xstartup
Starting applications specified in /home/steeldriver/.vnc/xstartup
Log file is /home/steeldriver/.vnc/desk01-vm:1.log

steeldriver@desk01-vm:~/Downloads$ 

```I was also able to connect to the TightVNC server using UltraVNC viewer. In both cases I connected using the IP:DISPLAY format (192.168.137.125:1) so I didn't need to worry about port numbers but fyi it appears to be using port 5901 (i.e. 5900+DISPLAY as per normal VNC - not 5500 as in your case).

When installing the viewer I checked the box to allow the installer to create an exception in the Windows firewall.

Maybe look in your tightvnc server log file to see if there's any hint what's going wrong?

Hope this helps.

---

### Post by oakridge on 2012-07-23
Thank you SteelDriver for your patience.

I have done as you suggested and now when I connect from the Windows 7 machine the Ubuntu image is still static but an error 'The application Compiz has closed unexpectedly' is generated.

Malcolm

---

### Post by steeldriver on 2012-07-23
Hi Malcolm I've done a bit more searching and it looks like this is a known bug with compiz-based sessions - the solution seems to be to create a better startup script which is able to choose a 2D session (which is what VirtualBox is doing by default)

[http://kb.realvnc.com/questions/196/VNC+Server+in+Virtual+Mode+does+not+start+correctly+on+Ubuntu+12.04](http://kb.realvnc.com/questions/196/VNC+Server+in+Virtual+Mode+does+not+start+correctly+on+Ubuntu+12.04)

I 'broke' my VirtualBox by enabling 3D and the ~/.vnc/xstartup file above fixed it (I don't know why it kills the server at the bottom... but it worked for me... ymmv)

---

### Post by oakridge on 2012-08-01
Thanks again for your reply Steeldriver and I apologise for being so slow to reply myself.

I have not worked through the solution in your link yet, but it has almost got to the top of the 'todo' list.  I will let you know how I get on.

Who said that retirement was the time for taking life easy?

Malcolm

---

### Post by steeldriver on 2012-08-01
No problem Malcolm - I since found out there is a ubuntu-specific guide (including a recommended ~/.vnc/xstartup file) here

[https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)

Regards - let us know how it goes

---

### Post by oakridge on 2012-08-27
I am sorry for the slow reply SteelDriver, normal life gets in the way sometimes.

Anyway I am delighted to report that all is now working.

Thank you very much for your help.

Malcolm

---

