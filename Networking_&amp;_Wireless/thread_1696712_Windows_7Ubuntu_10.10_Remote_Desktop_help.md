---
title: "Windows 7/Ubuntu 10.10 Remote Desktop help"
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by steaksauce on 2011-02-27
Hello there! While I may be a new user on the forum, I am not new to Ubuntu or networking. I'm wanting to play around with the remote desktop using Windows 7 on one computer and 10.10 on this computer. I know it seems weird to play around with remote desktops on the same home network, but in the end, I want to be able to troubleshoot a computer here at the house while I'm away.

Right now I have the remote desktop set up on this computer, but the program says computers only have access to it on the local network. So here's what I need to know.

1.) How to access the remote desktop on this computer from Windows 7
2.) How to access a Windows 7 remote desktop from this computer
3.) Setting up a file share network between Ubuntu and Windows systems (I've searched and searched and cannot find what I am looking for! :( )
                  -I have set up a Windows Homegroup on a Windows 7 PC
                  -I have downloaded Samba
                  -A folder labeled "workgroup" shows up in my network folder, however, it fails to mount.
4.) I set up a remote desktop for Ubuntu to Ubuntu systems, but I can only access the other laptop if it is wired into the network, not wireless. Can this be fixed and how?
-The internal IP address is different for each the wireless connection and wired connection, and I have both saved into the wireless desktop viewer

I thank you for any help I can receive :)

---

### Post by Boondoklife on 2011-02-28
> **steaksauce said:**
> Hello there! While I may be a new user on the forum, I am not new to Ubuntu or networking. I'm wanting to play around with the remote desktop using Windows 7 on one computer and 10.10 on this computer. I know it seems weird to play around with remote desktops on the same home network, but in the end, I want to be able to troubleshoot a computer here at the house while I'm away.
Not weird at all, most people do use remote desktop within their own networks and even remotely.

> **steaksauce said:**
> 
Right now I have the remote desktop set up on this computer, but the program says computers only have access to it on the local network. So here's what I need to know.

1.) How to access the remote desktop on this computer from Windows 7

You will need to use a VNC application such as tightvnc to make the connection.

> **steaksauce said:**
> 
2.) How to access a Windows 7 remote desktop from this computer

This would depend on what service you are using to share the desktop. If you are using an app like tightvnc then you should be able to use the remote desktop app that comes with ubuntu. If you are trying to make an rdp connection, see [here]("http://ubuntuforums.org/showthread.php?t=335548").

> **steaksauce said:**
> 
3.) Setting up a file share network between Ubuntu and Windows systems (I've searched and searched and cannot find what I am looking for! :( )
                  -I have set up a Windows Homegroup on a Windows 7 PC
                  -I have downloaded Samba
                  -A folder labeled "workgroup" shows up in my network folder, however, it fails to mount.

Check [here]("http://ubuntuforums.org/showthread.php?t=1169149&highlight=samba") and follow what they mention, it should help

> **steaksauce said:**
> 
4.) I set up a remote desktop for Ubuntu to Ubuntu systems, but I can only access the other laptop if it is wired into the network, not wireless. Can this be fixed and how?
-The internal IP address is different for each the wireless connection and wired connection, and I have both saved into the wireless desktop viewer

I thank you for any help I can receive :)
This sounds like a settings issue to me, make sure you are trying to connect to the correct IP's and that you don't have any traffic filtering going on. Are you sure your wireless and wired connections are bridged and on the same subnet, try pinging and see if that works.

---

### Post by steaksauce on 2011-02-28
Thanks Boondok, with the exception of the settings for the remote desktop (#4), this problem is solved. And I can tinker with that :)

---

### Post by steaksauce on 2011-03-03
The problem with not being able to connect wireless to another computer (on the same network as far as I know) was that I had the connection to my computer open as well. I'm not for certain, but it is disabled on my computer now and I just messed with my fiance without having her wired in. ;)

---

### Post by steaksauce on 2011-03-09
I just got around to doing this and got it working pretty fast with tightvnc on Windows 7 ;) Thanks again!
Oh and question 4 resolved after I reinstalled Ubuntu. I believe that it was a connection was open both ways or something? But my laptop is no longer set up to be viewed and it works

---

