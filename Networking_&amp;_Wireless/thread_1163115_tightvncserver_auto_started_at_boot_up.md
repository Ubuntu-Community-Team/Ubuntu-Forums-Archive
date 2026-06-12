---
title: "tightvncserver auto started at boot up"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by linuxtest on 2009-05-18
I've got tightvncserver to run on a Ubuntu 9.04 Server and have no problems connecting to the machine, but each time the machine is rebooted "tightvncserver" has to been entered into the terminal to start the service.  If the power goes out and then back on the BIOS knows to power up the machine and it would be nice if Ubuntu started tightvncserver at boot up.  Is there a way to allow tightvncserver to start at boot up?  Using Windows "Computer Manager" it is possible to add services to a list and when the service is started... does Ubuntu have that same capability?

---

### Post by rbc on 2009-05-18
System-->Preferences-->Startup Applications, then Add. Is this what you are looking for?

---

### Post by linuxtest on 2009-05-18
Yes, that works, thanks, but I need to login at the computer for a vnc session to connect.  Is there a way for the machine to boot up and allow for vnc sessions?  A scenerio is:

The power to this server was lost and has now been restored, the BIOS has detected the power outage and the system is booted and running.  No one is physically able to reach the machine, but they are able to vnc to it and administer.

---

