---
title: "Ubuntu Server 11.04 [running in hyper-v] networking stops"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by bderemer on 2011-09-04
Ubuntu Networking Community:

I'm having a sporadic (i.e. once every 12 +/- hours) network problem where my networking services seems to just stop working.  I have outlined the problem and background below.  If you need any more details, don't hesitate.

Thanks,
bderemer

===================

PROBLEM:
The ethernet networking on my 11.04 ubuntu server instance seems to just stop [no errors in any of the system logs that I can see].  If I run /etc/init.d/networking restart, it comes back to life.

The only thing I've found in the forums so far has to do with cloning a Hyper-V image of Ubuntu.  This hyper-v image is a clone of an existing Ubuntu hyper image.  As a result, I ended up with an Eth0 and Eth1 entry in the /etc/udev/rules.d/70-persistent-net.rules file.

I have since deleted the file, rebooted the hyper-v image and ubuntu regenerated the file so I only have Eth0.  Hopefully this will fix the problem, but I figured I would post this now and see if anyone has any feedback, guidance, suggestions.


**[COLOR="Red"]QUESTIONS: [/COLOR]**
1) is it possible that 2 entries in here could cause this?
2) if not, does anyone know what might cause this and/or what additional log files, etc I might check for answers?

BACKGROUND:
I have the OpenSSH Server, along with Natty-based (Sun 6.0.26 JDK) and (Tomcat 6.0.28) packages installed so I can test my web application stability/duration.  As part of this, I am using VisualVM and JMeter remotely to monitor and send HTTP requests respectively.

Unfortunately, when the networking stops, so does the monitoring and web traffic simulation.

I'd like to figure out why it stopped because I'm trying to run duration tests and it makes it a little hard to monitor

I have ubuntu server 11.04 installed in hyper-v [server 2008 R2 SP1].

---

### Post by bderemer on 2011-09-05
UPDATE: removing the 2 Eth entries didn't solve the problem.  The networking has stopped responding again.

-bderemer

---

### Post by bderemer on 2011-09-05
UPDATE #2: after running for less than 8 hours, the networking stopped again.  This time, I had to reboot the hyper-v instance to get networking running again.

Any thoughts/suggestions?

Thanks,
bderemer

---

### Post by DJonsson2008 on 2011-09-06
Hyper-V seems to be under documented and under internet chattered in the area of NIC troubleshooting.

We are unable to get Ubuntu 11.04 to have any Network connectivity at all under Hyper-V, either Legacy NIC (which shows under lspci) or via the separate Intel NIC we have installed for this purpose. We have installed/verified the full set of hv_* drivers and tried numerous strategies to get it to work. 

I've posted elsewhere in these forums regarding this get no reply so far.

Sorry to bring other questions to your question, but we are also vexed by Hyper-V/Ubuntu NIC issues.

_How did you get the limited NIC connectivity you now have with Hyper-V/11.04 to work? 

_What other resources exist for better discussion of Hyper-V/Ubuntu issues?

_Hyper-V's virtual NIC configuration does not elicit confidence, as it seems over complicated and void of capacity
to test/verify the various layers involved with it. What other
VM host software is more mature and direct in this area for 
possible Windows/Ubuntu VMs?

---

### Post by bderemer on 2011-09-06
I've found numerous links that discussed Ubuntu Server 10.10 and Ubuntu Server 11.04 in hyper-v.  Here are the 2 that I have successfully used:

[http://blogs.msdn.com/b/virtual_pc_guy/archive/2010/10/21/installing-ubuntu-server-10-10-on-hyper-v.aspx]("http://blogs.msdn.com/b/virtual_pc_guy/archive/2010/10/21/installing-ubuntu-server-10-10-on-hyper-v.aspx")

[http://narendrapatel.com/2011/05/installing-ubuntu-serve-11-04-64bit-on-hyper-v/]("http://narendrapatel.com/2011/05/installing-ubuntu-serve-11-04-64bit-on-hyper-v/")

I have successfully gotten 1 instance of ubuntu server 11.04 working without NIC issues, but in that case I did not install the OpenSSH server during my ubuntu installation process.  Perhaps OpenSSH Server is part of the problem - don't know at this point.  Either that, or the fact that I copied the hyper-v instance - which caused problems with the recognized ethernet devices.

regards,
bderemer

---

