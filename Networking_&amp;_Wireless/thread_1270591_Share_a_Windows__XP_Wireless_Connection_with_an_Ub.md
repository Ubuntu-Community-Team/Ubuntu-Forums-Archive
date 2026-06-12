---
title: "Share a Windows  XP Wireless Connection with an Ubuntu Box?"
date: 2009-09-19
forum: Networking &amp; Wireless
---

### Post by Breath! on 2009-09-19
Hi,

  I'm using a Dell Windoze XP laptop and wish to share it's wireless connection with my Ubuntu desktop, by connecting them directly together with an Ethernet cable, without the use of a router. Is this possible? I've tried Ubuntu 7, 9, and Fedora 11 and none have even recognized the laptop. What am I doing wrong?

---

### Post by dreamingdarkness on 2009-09-19
Is the Windows XP box set up for Internet Connection Sharing? Check by the steps from: [http://support.microsoft.com/kb/306126](http://support.microsoft.com/kb/306126)
The instructions for the 'client computer' are right on the IP address steps but wrong on the step-by-step, you need to edit the settings in the network connection on the Ubuntu desktop manually.
You'll need to configure the Ubuntu PC with settings similar to:
IP Address      192.168.0.2
   Subnet mask     255.255.255.0
   Default gateway 192.168.0.1

---

### Post by Breath! on 2009-09-20
Well  when I go to the Advanced... tab all I see is a  Windows Firewall settings button. Is there something different about wireless.

---

### Post by dreamingdarkness on 2009-09-21
You need to set up the internet connection sharing on the ethernet/LAN on the Windows box. This sets your Windows PC up as the 'gateway', and lets it connect to the other machine as a 'client' for the Internet Connection Sharing. I think it should automatically forward internet requests from the 'client'(linux) computer that come in via the ethernet to the wireless as it detects that as the gateway for the Windows PC.
Sort of hard to be absolutely sure, I don't have a setup that matches yours to test it with and I've never actively used connection-sharing.

---

### Post by Breath! on 2009-09-22
I had tried that earlier, but when I enabled internet connection sharing on my 1394 connection my lan option disappeared and I can't get it back.

  I also had Windows create a net-setup disk... Would that work if I installed Wine? 

  Encase it matters, I'm running Jaunty not Hardy.

---

### Post by dreamingdarkness on 2009-09-25
The 1394 connection is fire-wire, I don't know that you can do internet connection sharing through fire-wire.
You really are only able to do it through ethernet or wireless I believe.

---

### Post by Breath! on 2009-09-26
Ok. Do you know if Wine would know what to do with a net-setup.exe file from Windows?

---

