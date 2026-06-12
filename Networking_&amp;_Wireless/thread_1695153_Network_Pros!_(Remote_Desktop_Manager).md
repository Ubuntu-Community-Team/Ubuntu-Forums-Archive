---
title: "Network Pros! (Remote Desktop Manager)"
date: 2011-02-25
forum: Networking &amp; Wireless
---

### Post by stephanmir on 2011-02-25
Hey guys,

I need some assistance. I am attempting to log into my ubuntu system from my Windows 7 laptop. No success so far.

Here's what I've done:

Activated Remote Desktop under System >> Preferences
Checked "Allow others to view / control desktop"
Security put a check on "Require Password"
(Those are the only checked pieces)

In the windows 7, I attempt to connect by putting in the local IP under the Remote Desktop tool. 192.168.1.101 (as normal) and no connection. It says that the system is either not online or not accepting incoming requests.

What did I miss?

Thanks my Ubuntu forum Gurus!

Stephan

---

### Post by BHEJU on 2011-02-25
install VNC (tight vnc) server on ubuntu and vnc client on win7.
and use VNC instead of RDP.

Cheers

---

### Post by cjhabs on 2011-02-25
> **stephanmir said:**
> Hey guys,

I need some assistance. I am attempting to log into my ubuntu system from my Windows 7 laptop. No success so far.

Here's what I've done:

Activated Remote Desktop under System >> Preferences
Checked "Allow others to view / control desktop"
Security put a check on "Require Password"
(Those are the only checked pieces)

In the windows 7, I attempt to connect by putting in the local IP under the Remote Desktop tool. 192.168.1.101 (as normal) and no connection. It says that the system is either not online or not accepting incoming requests.

What did I miss?

Thanks my Ubuntu forum Gurus!

Stephan

You need to access the machine via VNC, not windows RDP.

---

### Post by stephanmir on 2011-02-25
Installed VNC on both the laptop and the ubuntu systems.

Loading Applications >> Internet >> x11vnc server on the ubuntu box brings up:

Select Port:
I placed 5900 in there with "Listen on localhost" and "File Transfer TightVNC"

After I click OK it brings up "x11vnc Properties" where I click "Accept Connections" and click "OK"

On the windows 7 laptop I click

All Programs >> TightVNC >> TightVNC Viewer
In the TightVNC server box I place "192.168.1.101"

I click accept and no result.  I attempted to ping 192.168.1.101 and I am getting a reply. What did I miss?

Thanks

Stephan

---

### Post by CharlesA on 2011-02-25
You set vnc to listen on localhost. Clear that box and try again.

---

### Post by vedster on 2011-02-25
Try using UltraVNC. 

1. Download [UltraVNC]("http://www.uvnc.com/download/index.html") on the Windows 7 PC.
2. Run through the standard installation, **make sure you say yes when it asks you to install something that improves performance under vista. **(Yes, I know it's a Windows 7 PC but it works with the vista fix because they both use Aero).
3. After installed, right click on the UltraVNC icon on your task bar and click settings.
4. Make sure "Allow loop back connections" is checked. 
5. Open UltraVNC viewer.
6. ON UBUNTU go to Remote Desktop.
7. Remote Desktop preferences should open, check "Allow other users to view your desktop"
8. Check "Allow other users to control your desktop"
9. Check "You must confirm each access to this machine" (OPTIONAL)
10. Check "Require the user to enter this password"; enter password (OPTIONAL)
11. BACK TO YOUR WINDOWS PC
12. In the UltraVNC viewer type the IP address that Ubuntu gave you in the remote desktop connection. For example; 192.168.1.xxx
13. Press connect. 


Just tried this for you on Windows 7 64bit and Ubuntu 10.10. Works perfectly.:D

---

### Post by stephanmir on 2011-02-25
Downloaded UVNC x64 stable 1.0.8.2 for windows
Ran through installation, didn't give an option for vista
Checked loopback under settings
Ubuntu Remote Desktop has everything checked as u stated, and included a password to try.
Went to UltraVNC viewer and put in 192.168.1.101 (the ubuntu box IP)
Failed to connect

I did not use VNC server when attempting it, just relied on the Ubuntu remote desktop software. Also attempted to use the x11vnc server software, no go.

These are the times which I wish you guys were here at my house and I could grab u all a drink to help me out.

Is it an option in the ubuntu that's denying the VNC from connecting?

---

### Post by stephanmir on 2011-02-25
Are there any built in firewalls in ubuntu I need to open ports on?

---

### Post by CharlesA on 2011-02-25
Ubuntu has ufw, but it's not enabled by default.

---

### Post by stephanmir on 2011-02-26
Fixed it!!!

So it looks like in 10.10 firewall was enabled. I made an exception for port 5900 and gave my laptop access.


Thanks everyone!!!

---

### Post by BHEJU on 2011-02-26
Glade things worked out. 
kindly mark this thread closed.

---

