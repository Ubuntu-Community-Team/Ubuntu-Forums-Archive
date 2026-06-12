---
title: "OpenVPN"
date: 2013-01-03
forum: Networking &amp; Wireless
---

### Post by nabz0r on 2013-01-03
Hi folks,

First and foremost I am a VERY noob Ubuntu user and I have moved to Ubuntu exactly one week ago and before that, NEVER worked with it though been interested but didn't have time to learn it and now it's time to move on from MS and use something more fun stuff, anyway long story short, I need help with OpenVPN.

I have set up OpenVPN to my work with certification and everything seems like to work but the connection fails after few minutes and that I think due to the OpenVPN should be started as Admin (which was in Windows and root in Ubuntu I guess) which I don't know how to start it as Admin/root, could anyone tell me how to do that?

Another question is that I need to change the password which we give away to people when we setup OpenVPN for them and they change they password by write clicking it and changing the pass and again this is how it's done in Windows and I'd appreciate it if someone tells me how to do it in Ubuntu.

Thank for the input and help in advanced and please wish me luck using this System correctly. :D


//nabz0r

---

### Post by ahallubuntu on 2013-01-03
Can you clarify what you are doing?  You have an OpenVPN server at work that's Ubuntu-based?  Or you are using a Ubuntu machine (a "client") and are trying to connect to your OpenVPN server with the Ubuntu machine?

If you are using Ubuntu as the client, you don't need to run it as root.  It's not a service when running as the client.

On the OpenVPN server (the server you are connecting to), yes the OpenVPN service needs to be started as admin or root.  But this should happen automatically when you setup OpenVPN in the first place.

The password you give to people depends on how you have setup the password on the OpenVPN server. You could post your server config file here (with public IPs and personal information removed) if you want some feedback on it.

---

### Post by TheFu on 2013-01-03
This [https://help.ubuntu.com/community/OpenVPN#Getting_Clients_Connected](https://help.ubuntu.com/community/OpenVPN#Getting_Clients_Connected) might help?

---

### Post by nabz0r on 2013-01-03
Hi and thanks for the reply guys.

What I am trying to do or say is that:

People when they want to connect to the Office use OpenVPN which works fine and we give them a default password which they change later on their hosts. (this worked fine with my windows machine and now problems whatsoever) 

No when I changed to Ubuntu I have configured the OpenVPN client on my host (Ubuntu) which works fine for a couple of minutes then it drops the connection (and as I stated before that might be due to not starting it as admin/root like what we do in Windows environment, not sure though if you need to do this in Ubuntu). Just our OpenVPN based on pfSense and we have no problem what so ever and the only thing people need to do when they run the OpenVPN GUI is to start it as admin in Windows and since no one is using Ubuntu hosts now we have a Unix team at work but since I am not working for another two weeks I'll have to work from work time to time so I need my setup to work.

As I know the program should start as admin even though I have admin rights on my Windows and Ubuntu machines but I don't know how to start it as admin/root on Ubuntu.

I don't what more I could say but please let me know if you need to know more stuff I'll be more than happy to provide you and thank you in advanced for your input (s). 

As for the Link I didn't get it well because it goes through command lines which I am not so familiar with at the moment so I didn't understand it well and I don't think it will help me solve my problem. :)

Thanks!

//nabz0r

---

### Post by ahallubuntu on 2013-01-03
> **nabz0r said:**
> No when I changed to Ubuntu I have configured the OpenVPN client on my host (Ubuntu) which works fine for a couple of minutes then it drops the connection (and as I stated before that might be due to not starting it as admin/root like what we do in Windows environment, not sure though if you need to do this in Ubuntu).

You DO NOT need to run OpenVPN client as root/admin in Ubuntu.  I use OpenVPN all the time on my laptop.  I just login as my regular user account and connect to  my OpenVPN connection through network manager.  It is reliable and stays connected for hours.  I just did a clean install of Ubuntu 12.04 and setup OpenVPN without thinking and it was easy.

I DID have to give my admin password once to install the OpenVPN plug-in for Network manager - but I've never needed to enter it again.  Since then, I just choose my OpenVPN connection from the "VPN Connections" menu and it connects.  No admin password required.

Yes, I'm not surprised the admin password is required in Windows.  Ubuntu is not Windows.

Perhaps you could explain how you setup OpenVPN client on your Ubuntu computer?  What version of Ubuntu are you using? If you are using Network Manager to connect to networks (what most people using Ubuntu use, by default), it's really best to install the "network-manager-openvpn" package so you can start your VPN from the "VPN Connections" menu of Network manager, with your mouse.  I didn't do any command line stuff to setup my VPN and don't do any to start it.  I choose it from the menu with my mouse to start it.  I suggest trying to do it that way, too, if you aren't already.

---

### Post by ahallubuntu on 2013-01-03
By the way, to run any command in Ubuntu as "root" just put the prefix "sudo " (with the space) in front of it.  You'll be asked for your admin password and then the command will run with admin user privileges.  If want to connect to your VPN with a command line, try that.

---

### Post by nabz0r on 2013-01-03
Yeah, I've not done it via command line, I've used the GUI and the setup was really easy not problems there at all.

Then the first question regarding if I need to start it with admin right or not is answered. Thanks!

The second one was how to change password? I don't wanna use the default password and want to change it. In Windows when you're connected to your OpenVPN you just right click and change password which changes the password for your connection and when you connect to VPN you have to give the password or you can save it and auto login when you start it if you want but in Ubuntu, I don't know how to do that. 

I use 12.04 TLS and I have run the network-manager-openvpn command when I installed the OpenVPN first time.

---

### Post by nabz0r on 2013-01-03
By the way, I have watched this [**video**]("https://www.youtube.com/watch?v=HuzLjR-1pgE") and installed the client on my system.

---

### Post by ahallubuntu on 2013-01-03
What is the "Type" of OpenVPN connection you have setup in Network Manager?

In the 12.04 LTS version, when I go to "Configure VPN" and choose my connection and click on the "VPN" tab I see four types of connections:

Certificates(TLS)
Password
Password with Certificates(TLS)
Static Key

Which one are you using?

There are also two passwords: the login password for the middle two types and the "Private Key Password" if you are using certificates.

The login password: obviously you can change it right there in the configuration but that doesn't change it on the server.  I know of no way to change it on the server automatically without logging in to the server.

I'm not sure how to change the "private key password."

---

### Post by nabz0r on 2013-01-03
OK. I am using the Password with Certificates (TLS) they I use my User Certificate, CA Certificate, Private Key and Private Key Password. 

When I change the password there I should provide my old pass and then write the new password I guess, so there is no option to provide the old and then give the new pass.

I just tested it again and took a look at the route and they're looking fine but again and I got disconnected after exactly one minute and I was not able to ping anything in the remote network. (The same problem appears in Windows environment if you don't run it as admin and that's why I was wondering if I should start it as Admin or not) :)

---

### Post by ahallubuntu on 2013-01-03
So maybe there's something else wrong in your config?  Maybe you simply aren't connecting at all.  Anything else funny in your config?  Did you look at the "Advanced Options?"


> **nabz0r said:**
> OK. I am using the Password with Certificates (TLS) they I use my User Certificate, CA Certificate, Private Key and Private Key Password. 

When I change the password there I should provide my old pass and then write the new password I guess, so there is no option to provide the old and then give the new pass.

I just tested it again and took a look at the route and they're looking fine but again and I got disconnected after exactly one minute and I was not able to ping anything in the remote network. (The same problem appears in Windows environment if you don't run it as admin and that's why I was wondering if I should start it as Admin or not) :)

---

### Post by nabz0r on 2013-01-03
In advanced option everything is by default and haven't changed anything there. What is the command for network-manager-openvpn? I can run it again, right?

Connected again and the same problem, disconnects after one minute.

---

### Post by ahallubuntu on 2013-01-03
> **nabz0r said:**
> In advanced option everything is by default and haven't changed anything there. What is the command for network-manager-openvpn? I can run it again, right?

Connected again and the same problem, disconnects after one minute.

"network-manager-openvpn" is the name of the package you install, not a command.

The "Advanced Options" would be chosen by the OpenVPN server config.  You need to set yours to match theirs.  For example, if the server setting is to "Use LZO Data Compression," you have to set the client the same way.  All of those advanced options need to match the server settings.

Did you import your OpenVPN config? Or did you just try setting it up manually?  It sounds like you are connecting at least briefly so the certificates and keys are probably right.  Maybe the other options are tripping you up.

---

### Post by nabz0r on 2013-01-03
> **ahallubuntu said:**
> "network-manager-openvpn" is the name of the package you install, not a command.

The "Advanced Options" would be chosen by the OpenVPN server config.  You need to set yours to match theirs.  For example, if the server setting is to "Use LZO Data Compression," you have to set the client the same way.  All of those advanced options need to match the server settings.

Did you import your OpenVPN config? Or did you just try setting it up manually?  It sounds like you are connecting at least briefly so the certificates and keys are probably right.  Maybe the other options are tripping you up.

Yeah, that package is installed already and by command I meant what is the command to re-install it. :)

In the Advanced Option is still as it is and I haven't changed anything since I configured my client. I imported the key, cert and ca actually. Now when I write sudo openvpn --config "name.ovpn" and then the password it seems everything goes normally and after this "Initialization Sequence Completed" I don't get any other message. Does this mean the connection failed?

---

### Post by ahallubuntu on 2013-01-03
> **nabz0r said:**
> In the Advanced Option is still as it is and I haven't changed anything since I configured my client. I imported the key, cert and ca actually. Now when I write sudo openvpn --config "name.ovpn" and then the password it seems everything goes normally and after this "Initialization Sequence Completed" I don't get any other message. Does this mean the connection failed?

FYI, this command

```
sudo openvpn --config "name.ovpn"
```

doesn't change the settings in Network Manager's OpenVPN config.

If you're using the Network Manager menu to connect to the OpenVPN, use the options there.  (You could try importing "name.ovpn" but I've had mixed luck with that.)  If you don't want to use the Network Manager add-on, use the command line for everything.

---

### Post by nabz0r on 2013-01-03
> **ahallubuntu said:**
> FYI, this command

```
sudo openvpn --config "name.ovpn"
```

doesn't change the settings in Network Manager's OpenVPN config.

If you're using the Network Manager menu to connect to the OpenVPN, use the options there.  (You could try importing "name.ovpn" but I've had mixed luck with that.)  If you don't want to use the Network Manager add-on, use the command line for everything.

That command only starts OpenVPN, right? Now I am confused and don't exactly know what do you mean by Network Manager. It is installed on my machine though.

---

### Post by nabz0r on 2013-01-03
Ok, you know what troubleshooting this could take 4 days without figuring out why it doesn't work. Do you have any tutorial where it shows how to configure it by command lines or by GUI? Thanks for your effort and inputs man, really appreciate it! :)


//nabz0r

---

### Post by ahallubuntu on 2013-01-03
If you want to dig in to OpenVPN, go to [www.openvpn.net](www.openvpn.net) .  There should be plenty of tutorials there, mostly based on command line options, not Network Manager.

My suggestion is to go back to Network Manager, VPN Connections, click on the "Import" button and try to import the file "name.ovpn" (if that's where your OpenVPN settings for your server are saved).  That may get the settings but might not get the paths to your certificates correct.  If your admin created that file for the Windows client, it may not import properly.

Alternately, pop open the "name.ovpn" file in a text editor and look at the various options.  You should be able to find options that correspond to the "Advanced Options" in the Network Manager OpenVPN settings.  For example, LZO compression - what's that set to?  What about TLS Authentication? (tab)  Is your server using a TAP or TUN connection?  You can look up the lines in your ovpn file at [www.openvpn.net](www.openvpn.net) to see what they mean, if you want.  (The lines in that config file are the same as command line options.) Network Manager is basically issuing the openvpn command for you when you connect, using the advanced options to determine which command line options to use.

You could do both approaches.  Try the import first.  That may import the advanced settings correctly but not get the certificates right.  At least you can review the advanced settings there and try to go back to your original config and change the advanced settings there to match.

---

### Post by nabz0r on 2013-01-03
> **ahallubuntu said:**
> If you want to dig in to OpenVPN, go to [www.openvpn.net](www.openvpn.net) .  There should be plenty of tutorials there, mostly based on command line options, not Network Manager.

My suggestion is to go back to Network Manager, VPN Connections, click on the "Import" button and try to import the file "name.ovpn" (if that's where your OpenVPN settings for your server are saved).  That may get the settings but might not get the paths to your certificates correct.  If your admin created that file for the Windows client, it may not import properly.

Alternately, pop open the "name.ovpn" file in a text editor and look at the various options.  You should be able to find options that correspond to the "Advanced Options" in the Network Manager OpenVPN settings.  For example, LZO compression - what's that set to?  What about TLS Authentication? (tab)  Is your server using a TAP or TUN connection?  You can look up the lines in your ovpn file at [www.openvpn.net](www.openvpn.net) to see what they mean, if you want.  (The lines in that config file are the same as command line options.) Network Manager is basically issuing the openvpn command for you when you connect, using the advanced options to determine which command line options to use.

You could do both approaches.  Try the import first.  That may import the advanced settings correctly but not get the certificates right.  At least you can review the advanced settings there and try to go back to your original config and change the advanced settings there to match.

I'll take a look at their site later. I have just deleted everything and re-done everything but still connect for one minute and then baaam loses the connection. 

As of importing, I have imported everything, like ca, user cert, user key, etc and the LZO comp is ticked as we use it the security is also is the same as in the name.ovpn but still loses connection after one minute. :/

I had done both with command lines and via GUI like I choose network, vpn connection, configure vpn and add, create vpn and then imported everything but no luck. :(

---

### Post by nabz0r on 2013-01-15
After troubleshooting and looking around for like almost a week, I found out that with certification you should use the command line and not the gui and it works like a charm without any disconnection AT ALL.

Thank you guys for trying to help :)

EDIT: One more thing, why can't I change the status to SOLVED?

---

### Post by ahallubuntu on 2013-01-15
> **nabz0r said:**
> After troubleshooting and looking around for like almost a week, I found out that with certification you should use the command line and not the gui and it works like a charm without any disconnection AT ALL.

FYI to anyone else reading: I use Network Manager with an OpenVPN config with certificates daily and go for hours without getting disconnected, if ever.  I don't know why nabz0r couldn't get it to work that way, but I've never had an issue with certificates using the Network Manager OpenVPN plug-in.  The only thing that does NOT work (this may be a Network Manager bug) is that "Connect Automatically" option in the VPN setup does not work and never as as long as I've been using it in Ubuntu.  You still have to connect to your VPN manually but it's easy: just choose it from the "VPN Connections" menu.

---

### Post by nabz0r on 2013-01-15
> **ahallubuntu said:**
> FYI to anyone else reading: I use Network Manager with an OpenVPN config with certificates daily and go for hours without getting disconnected, if ever.  I don't know why nabz0r couldn't get it to work that way, but I've never had an issue with certificates using the Network Manager OpenVPN plug-in.  The only thing that does NOT work (this may be a Network Manager bug) is that "Connect Automatically" option in the VPN setup does not work and never as as long as I've been using it in Ubuntu.  You still have to connect to your VPN manually but it's easy: just choose it from the "VPN Connections" menu.
That's really weird, and I am sure it's me who's doing something wrong and that's why it doesn't work properly and disconnects after one minute.

---

