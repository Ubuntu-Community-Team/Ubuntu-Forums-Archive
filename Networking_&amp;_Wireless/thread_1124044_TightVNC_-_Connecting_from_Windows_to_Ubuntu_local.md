---
title: "TightVNC - Connecting from Windows to Ubuntu locally"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by LLMNSTR on 2009-04-12
Hi,

I have installed Ubuntu 8.04 LTS successfully on an older PC. I would like to be able to remote desktop to it and take control of the desktop, for the purpose of watching movies off of it while working on my main PC. I have decided to use TightVNC for this. I successfully installed every tight VNC package via synaptic package manager, and have started a server process by running "vncserver :1". When I use the windows client to try and connect, I get a "Failed to connect to server: [ipaddress]". I have confirmed that I am using the proper internal IP address, but I am having no luck. Any suggestions on where to go from here?

---

### Post by ninjapirate89 on 2009-04-12
If I understand you correctly you are trying to connect to ubuntu from windows right? If so go to System -> Preferences -> Remote Desktop in Ubuntu and make sure that Allow others to view your desktop is checked. You will also want to uncheck the Ask for confirmation box. Then in windows open tightvncviewer and try putting in the ip.

---

### Post by LLMNSTR on 2009-04-13
Still getting the same error message. Is there any way to run a diagnostic or get a connection log? Or perhaps there's more configuration on the Unbuntu side I need to do?

---

### Post by ninjapirate89 on 2009-04-13
Hmmmm.....I'm not sure what could be the problem. I actually do the opposite of what you're trying to do. I use Ubuntu as the host and windows as the guest so all I have to do is set up the server on xp and I'm done. I'll keep looking for an answer though.

Edit -> what windows OS are you using? XP?

---

### Post by LLMNSTR on 2009-04-13
It seems that's what most people do also. Thanks for your help so far.

Are there any other free VNC solutions for my problem?

---

### Post by ninjapirate89 on 2009-04-13
Did you also install tightvnc on your windows computer?

---

### Post by LLMNSTR on 2009-04-13
Yes, I installed the TightVNC Viewer for Windows.

---

### Post by ninjapirate89 on 2009-04-13
Did you set a password to connect in Ubuntu? If so, maybe it's not connecting because the password is wrong or not entered. If not then I'm all out of ideas.

---

### Post by LLMNSTR on 2009-04-13
I did use the command "vnc passwd" to set a password, but I'm not asked for it while connecting to the server from Windows. And there is no option in the TightVNC Viewer options to enter a password.

---

### Post by ninjapirate89 on 2009-04-13
The only thing I could recommend now is to just uninstall tightvnc from ubuntu (because it's not really necessary just use the Remote Desktop option I mentioned instead) and also remove tightvnc from windows and reinstall it (you only need tightvncviewer in Windows). The reason I would use Remote Desktop in Ubuntu instead is because it is easier to configure since it isn't done in the terminal.

---

### Post by Frijolie on 2009-05-01
I was having this same problem myself and came across this posting. 

Here's what I did to get it to work:

1. Make sure that you enable remote connections on your remote host.

2. Make sure you have the server/service running vncserver :1

3. Disable "allow confirmation" on remote host

4. Set a password for security

5. Connect to the remote host by typing ```
<ip address>:x
```
       (e.g. 192.168.1.3:1)


I did all of the above besides that last step. I think the ":1" part tells tightvnc which screen (tty) to connect to. So make sure steps 2 and 5 match. I dunno if this will work for you but it got me connected!

Now that I'm connected, I'm having keyboard troubles. When I type on the remote host random characters are being displayed--insetad of the ones that I'm typing. One step forward and two steps back I guess...

Lemme know if this helps.

---

