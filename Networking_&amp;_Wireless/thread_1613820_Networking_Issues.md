---
title: "Networking Issues"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by throese on 2010-11-04
So, I'm trying to set up Samba so that I can connect to the printer in the den since we have wireless access. Also, I can see my virtual box on the Windows XP Home Ed desktop, but can't access it (sorry, no screen short or pic).

So, how do I go about setting up Samba so stuff is visible between my Ubuntu machine and my families Windows orientated network?

I've tried these:

[Samba File Server]("http://doc.ubuntu.com/ubuntu/serverguide/C/samba-fileserver.html")

[Securing a Samba File and Print Server]("http://doc.ubuntu.com/ubuntu/serverguide/C/samba-fileprint-security.html") 

But no luck. I'm having a hard time finding anything on YouTube too. I'm taking a break from the Remastersys stuff so I can get the more important things done, such as connecting my Ubuntu machine to my families Windows Network. I don't know if the printer is wireless or not, but regardless, I can't find it. Please help.

(Also, sorry for the 3-5 topics I've made within the last 5 days, I've recently started Ubuntu in July and am still learning). Forgive me if I'm getting on anyone's nerves.

---

### Post by SeijiSensei on 2010-11-04
Is the printer connected to a machine running Linux or one running Windows?  Or is the printer itself wireless?  Can you ping its IP address from your Ubuntu box?

You may just need to set up printing on the Ubuntu box and point it at the network printer.  If you can print to it from Windows, you should be able to see the printer's share with CUPS if you have samba-common and smbclient installed.  I think they're installed by default, at least they were in the Kubuntu 10.10 installation I just did today.

---

### Post by throese on 2010-11-04
Well, here are pictures of the main network area: (View attachments)

Everything is connected to the Belkin router including the Scanner/Fax/Copy/Print Machine.

I can't even view the Windows Network through the Network folder. Wish someone could just make a video tutorial for all of this.

---

### Post by CharlesA on 2010-11-04
Are you able to ping the machine from a Windows box by using it's ip address?

---

### Post by throese on 2010-11-04
Well, when I ping my Linux through my Windows VBox, it gets replies from Ubuntu, but when I try to ping my Windows VBox with Ubuntu, it just...stops.

---

### Post by williejones on 2010-11-04
I just set up an HP all in one connected by usb to Ubuntu 10.04.  This computer is connected to the wireless router by usb wireless.  To alll my other machines (Ubuntu 10.10, Arch Linux, Windows Vista, Windows 7) to connect:

On the machine with the printer attached go to 
System
Administration
Printing
Server
Settings  and select Published Shared printers connected to this system


Still in the same place right click on the printer icon
select Policies
Check enabled, accept jobs, shared

Get the IP address of the computer (ifconfig) as you will need this to set up any other computer you want to remote print \

---

### Post by throese on 2010-11-04
Thanks Willejones. I'll try and see what happens.

---

### Post by CharlesA on 2010-11-04
> **throese said:**
> Well, when I ping my Linux through my Windows VBox, it gets replies from Ubuntu, but when I try to ping my Windows VBox with Ubuntu, it just...stops.

Since you are running it in a VM, what is the networking set to?

---

### Post by williejones on 2010-11-04
On the remote computer go to 
System
Administration
Printing 
Add Printer
add device URI
ipp://192.xxx.x.xx:631/printers/Photosmart-C5100-series

The 192.xxx... is the ip address of the computer with the printer attached

The Photosmart-C5100-series is the printer name which can be found on
the printer properties of the machine connected to the printer

edit change the Uri ipp to http for Windows

---

### Post by throese on 2010-11-04
Charles: Idk. I'm currently connected to the desktop in the Den through Remote Desktop (don't want to have to keep going back and forth from room to room). Well, my Ubuntu machine can communicate with my Windows VBox and the main Dell Desktop downstairs. At least now I know everything can communicate with one another.

What's the next step, now knowing that the machines communicate?

Williejones: My laptop is the ONLY machine in the ENTIRE house that has Linux on it. EVERY other computer in the house has Windows XP Home Edition on it except for my mom's laptop which has Windows 7. What you're asking me to do would mean that the Dell with Win XP Home would have to have Ubuntu, which it does not. But I will give what you suggest a try.

---

### Post by CharlesA on 2010-11-04
I think I may be confused.

If you are running the Windows box in VirtualBox, make sure that the networking says "Bridged" instead of NAT (which is the default).

---

### Post by throese on 2010-11-05
Charles: Okay, there is a Dell machine in the den. That has Win XP Home Edition on it. Connected to that computer is the router and modem. Connected to the router is the printer as well as the modem and desktop. That is our main work station, as shown in the attached pictures on the previous page. 

The Windows XP Professional Edition SP2 that I VBox off of is just there because I wanted to try some simple networking things with it. Other than that, my VBox has no real purpose.

---

### Post by CharlesA on 2010-11-05
Thanks for the clarification.

Does the printer have a NIC on it, or is it hooked up to the PC?

I've not done Samba printer sharing, unforunately, since all the printers I have are able to be hooked up directly to the network.

---

### Post by throese on 2010-11-05
Not sure if it has a NIC or not. I THINK it's hooked into the router via USB cable or maybe into the PC. I'll check and let you know once I get home.
 
Lets take these two situations.
 
Lets say it does have NIC, what would I do then?
 
If it is hooked up to the PC or router, what then?
 
(I ask ahead of time just in case it's one or the other)
 
=)

---

### Post by CharlesA on 2010-11-05
If it's got a NIC, you can plug it directly into the network and not have to worry about having it hooked up to the PC or router.

If it's hooked up to the pc or router directly, you'll have to jump thru some hooks to get it to work.

---

### Post by throese on 2010-11-05
My parents can connect to the printer wirelessly through their laptops, but I cannot. =/ (Forgot to mention that in my last post)

---

### Post by CharlesA on 2010-11-05
What OS are they using?

---

### Post by throese on 2010-11-06
Mom: Windows 7 Home Premium
Dad: Windows XP Home or Professional Edition
Dell in Den: Windows XP Home Edition

So, I was thinking, maybe if we installed a Virtual Box (I downloaded it for Windows) and installed in on the Dell in the den (that is the entire house's PRIMARY computer that the network is set up on) then I could install either Windows Server 2003 or Ubuntu Server, set it up and connect all the computers to it and the printer etc. etc.

Could it all work then?

---

### Post by CharlesA on 2010-11-06
It's probably a name resolution thing then, since Windows uses NetBIOS broadcasts and Linux doesn't.

Add the hostname and ip address of the machine the printer is hooked up to into the hosts file and see if you are able to connect to it.

```
gksu gedit /etc/hosts
```

---

### Post by throese on 2010-11-06
Last time all I had to do was install the printer drivers via USB. This new printer we have has Wi-Fi. Anyway, I'll do that. Lets hope this works. I'll keep everyone updated.

---

### Post by CharlesA on 2010-11-06
If the printer has wifi, then you should be able to connect to it with it's IP address.

Should be fairly easy to add the printer if you are able to do that.

---

### Post by throese on 2010-11-06
Well, using the computer's IP address didn't work. How do I find the printer's IP address?

---

### Post by CharlesA on 2010-11-06
You'd have to look at the router to see what ip address it assigned to the printer.

---

### Post by throese on 2010-11-06
But, how do I do that? I checked everywhere on the Belkin router and can't find the router's IP address on the label or anywhere on it. Is there anything I type into the command prompt or GUI to find the router's IP address?

---

### Post by CharlesA on 2010-11-06
Should be 192.168.0.1 or 192.168.1.1 to access the web interface.

Check ipconfig /all on a windows box and look for the gateway address.

---

### Post by throese on 2010-11-06
And...it said no network printers could be found at this address. =/

---

### Post by CharlesA on 2010-11-06
Were you trying to connect to the gateway address, or did you look in the router interface for the ip of the printer?

---

### Post by throese on 2010-11-06
Gateway address. "did you look in the router interface for the ip of the printer?" I don't know how to do that.

---

### Post by CharlesA on 2010-11-06
> **throese said:**
> Gateway address. "did you look in the router interface for the ip of the printer?" I don't know how to do that.

You'd need the IP of the router, not the gateway.

Find the model of the router and look here: [http://www.belkin.com/IWCatSectionView.process?Section_Id=4](http://www.belkin.com/IWCatSectionView.process?Section_Id=4)

---

### Post by throese on 2010-11-07
Okay, so, I have no idea as to what to do now. I got the model number, found my router and typed in what it told me into the browser, but idk what to do now. I'm on the router settings site thing.

---

### Post by CharlesA on 2010-11-07
You'd probably have to look at the status page for active leases to find the ip.

If you don't really know how the network is setup, perhaps ask yer parents how they added the printer?

---

### Post by throese on 2010-11-07
Then, if I can't find the IP myself, I'll talk to my dad tonight. They had to use an installation disk, but I can't find it.

---

### Post by CharlesA on 2010-11-07
I don't know how to get it set up then. Each network and printer is different. :(

Good luck.

---

### Post by throese on 2010-11-07
Then, I'll have a few options. 

1) Talk to my dad tonight on the phone about getting our hands on a NOS (Network Operating System) and installing it on Virtual Box and then hopefully set up Samba properly so my machine connects to the network.

2) Try to get the IP address of the router or printer.

3) Try to find the CD and if I do hope to God that the drivers work on Linux.

Thanks for all the help though everyone.

---

### Post by CharlesA on 2010-11-07
What model is the printer? I know some of the newer HP ones connect directly to the network and you should be able to install them from Ubuntu with little problems as long as it's being seen.

I guess the problem is that Ubuntu doesn't know where to look to find the printer.

---

### Post by throese on 2010-11-07
It's a Canon MX340 series Printer - USB003

---

### Post by CharlesA on 2010-11-07
Yeah, if it's a USB printer, you should be able to share it on the machine it's on.

---

### Post by throese on 2010-11-07
I'll try plugging my laptop into it directly tomorrow and see if that makes it work wireless for my computer. =)

---

### Post by CharlesA on 2010-11-07
Best of luck. :)

---

### Post by throese on 2010-11-08
Plugging in the printer directly didn't do a damn thing. Gonna try installing/setting up Samba and pray that it works. In my case it's "Plug and Pray" instead of "Plug and Play". XD

---

