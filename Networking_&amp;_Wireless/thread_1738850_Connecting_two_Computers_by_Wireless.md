---
title: "Connecting two Computers by Wireless?"
date: 2011-04-25
forum: Networking &amp; Wireless
---

### Post by jimford on 2011-04-25
I want to be able to control a stand-alone desktop computer with a wireless PCI card, from a laptop with a wireless PCMCIA card.

The chipsets of the wireless cards I intend to use are supported by Linux.

There's going to be an easy way, and a hard way of doing this. If I try doing it all myself, I'm bound to choose the hard way!

Can anyone give me any pointers to doing this please (I'm sure it must have been done many times before)?

Jim

---

### Post by josephmills on 2011-04-25
if you go to system-->preferences-->remote desktop  then make it so you can connect

---

### Post by collisionystm on 2011-04-25
> **jimford said:**
> I want to be able to control a stand-alone desktop computer with a wireless PCI card, from a laptop with a wireless PCMCIA card.

The chipsets of the wireless cards I intend to use are supported by Linux.

There's going to be an easy way, and a hard way of doing this. If I try doing it all myself, I'm bound to choose the hard way!

Can anyone give me any pointers to doing this please (I'm sure it must have been done many times before)?

Jim

Will you be using a wireless router?

If not, you can setup your Ubuntu to be an adhoc wireless access point. Then your desktop can just browse for its network and connect directly. If SSH is enabled on both you can SSH between them, share files...etc.

I see remote desktop was suggested. I am not exactly sure what you are trying to do, but remote desktop should be your most obvious choice. Linux uses VNC and Windows uses RDP.

The 'Remote Desktop' That comes with ubuntu uses VNC and is extremely slow. I suggest trying out different VNC clients from the Software Center.

---

### Post by lz1dsb on 2011-04-25
> **collisionystm said:**
> .... ubuntu uses VNC and is extremely slow. I suggest trying out different VNC clients from the Software Center.
Agree with that. He can also try out the NX server from NoMachine. There's a free version. It's quite easy to install and manage. And you only need one open port - SSH. Here's a link:
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)
I believe that it's not hard to install it even for an unexperienced user. Just stick to the instructions.
Regarding the Wireless. You should open you Network-Manager and create a new wireless SSID in the RadioNetworks tab (the name might not be exactly this, sorry but I'm having a German version here, so my translation might not be entirely correct) and select the mode of operation „Adhoc“. You should not forget also that in this mode you have to take care for the IP addresses being used. You can start a DHCP server on one of the machines, but I believe that this would only complicate the matters in this case. So just configure two different IP addresses in the same subnet and this should be enough.


Cheers,
Boyan

---

### Post by josephmills on 2011-04-25
I knew If I mentioned vnc people would react. thanks for the answers its helping me too.:)

---

### Post by jimford on 2011-04-25
Many thanks for the replies so far.

I actually have an 'Actiontec' access point available - would it make the setup easier with one?

The project I want it for is for a PC running 'motion' with a security camera. The PC will be in an outhouse and I don't want to have to go there to control it and check the output from 'motion'.

Jim

---

### Post by lz1dsb on 2011-04-26
> **jimford said:**
> Many thanks for the replies so far.

I actually have an 'Actiontec' access point available - would it make the setup easier with one?

The project I want it for is for a PC running 'motion' with a security camera. The PC will be in an outhouse and I don't want to have to go there to control it and check the output from 'motion'.

Jim
If you have an Access Point that it's "business as usual" sort of speak. You'll need to configure an SSID on the Access Point, configure whatever encryption method you prefer (WPA2 with pre-shared keys is prefered) and than you'll just need to associate the PCs running Ubuntu within the range of the Access Point.
From the NetworkManager icon you should be able to see the SSID.
Once you've established a connection you could disable the SSID broadcasting from the AP, if this configuration is suported. It doesn't provide 100% security, but it could hide your AP from curious neighbours for example ;)

Cheers, 
Boyan

---

### Post by jimford on 2011-04-26
Thanks again for the helpful replies.

I've now got the two computers wirelessly connected using this link:

[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

I had to use the 'CLI' method before it would work.

I can now ping each computer and the next step is to (probably) configure a VNC.

Jim

---

### Post by lz1dsb on 2011-04-26
That's cool. Great. About the GUI... Well usually the GUI is more convenient, but only when it works. The link you mentioned is quite good. Actually I've never done it using a CLI. But now I know how. Thank you.


Cheers,
Boyan

---

### Post by jimford on 2011-04-26
I can now ssh and use Filezilla between the two computers OK. I've installed FreeNX and it appears to connect, but I just get a black window on the client, with the remote (server) machine's name on the banner. This seems to be a common problem with FreeNX+Kubuntu+XFCE. I've tried several of the 'fixes' mentioned on the 'net, but none of them work!

Maybe I'll have to make do with ssh and Filezilla, or go with the Ubuntu VNC.

Jim

---

### Post by lz1dsb on 2011-04-26
That's strange. But it really could be an issue with the NX server though. I've  never used it with KDE, neither with Xfce. 
The VNC should be quite easy to set up. By default Ubuntu comes with vino-server package preinstalled. You can enable it from System->Settings->Remote Desktop. 
Which Ubuntu version do you use? I noticed that in the latest versions there's also another VNC package preinstalled: x11vnc. You can also use that one. 

Let me check tomorrow in which directory the NX server stores its logs. Maybe there's something there which can give us a clue why it's not working as expected...
And by the way. Did you wait enough when you saw the black screen with the NoMachine logo? Sometimes it takes a while. For me it's probably more than 30 seconds.

---

### Post by lz1dsb on 2011-04-27
So here it is. The config file is /etc/nxserver/node.conf
In the config file you'll need to change the logging level:
NX_LOG_LEVEL=5 (the default is 0, which means no logging)
Than make sure that the log file is enabled:
NX_LOGFILE=/var/log/nxserver.log
After that reset the service 
nxserver  --restart
And you're ready to troubleshoot. The next time you try to login using the NX client you can also open a SSH session to the server and monitor what's is being logged into the log file.

---

