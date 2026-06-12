---
title: "CyberGhost connects, but then times out. Help?"
date: 2011-06-07
forum: Networking &amp; Wireless
---

### Post by mufar on 2011-06-07
I know similar questions have been asked on this, but with my searches I was unable to find a resolution. So here goes:

I am trying to get CyberGhost working on my Ubuntu laptop. I am running 11.04 and using the "Network Connections" dialog in Gnome to "Configure VPN". I have the OpenVPN plugin installed and using the information provided by CyberGhost
> 
Configuration on Ubuntu with Gnome
To comfortably configure your OpenVPN settings you might want to install network-manager-openvpn using Synaptic.

Open the menu with a click on the network manager icon. Move to VPN conncetion and add a new connection.

Now choose OpenVPN and set followign settings, alternatively import the config file directly (Username.ovpn):

Choose a name for your new VPN connection.
Insert a gateway on the tab VPN. Available gateways are: de.openvpn.cyberghostvpn.com, us.openvpn.cyberghostvpn.com, nl.openvpn.cyberghostvpn.com, ch.openvpn.cyberghostvpn.com and ua.openvpn.cyberghostvpn.com.
Please choose type: Password and Certificate (TLS)
Enter your CyberGhost VPN username.
Enter your CyberGhost VPN password.
Now choose your user certificate from the ZIP file. It begins with your CyberGhost username with the extension .crt
Now choose the ca.crt from the ZIP file.
Now choose your private key from the ZIP file. The filename is your CyberGhost username followed by .key extension.

There are more settings on Advanced settings:

Gateway port have to be 9081
Activate LZO compression
Activate Use custom tunnel Maximum Transmission Unit (MTU) and set it to 1500
Activate Use custom UDP fragment size and set to 1300
Enable Restrict tunnel TCP Maximum Segment Size (MSS)
Change the cipher under security to AES-128-CBC


I am successfully connecting to the VPN server, but then I am unable to browse the internet. I am currently using the "free service" to test it out. 

Does anyone know how to get this working? what the potential problem could be? or any good close alternatives? (a free/trial VPN that I can connect to using no client, just gnome)

Thanks.

---

