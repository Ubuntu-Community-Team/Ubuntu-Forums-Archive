---
title: "Backend database unavailable"
date: 2009-02-27
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-02-27
I recently tried to watch a recording and received the error message that my backend database was unavailable. I foolishly didn't write down the exact wording of the error message, but the gist of it was that it suggested either my backend server wasn't running or I had the wrong IP address.

I'm using a combined frontend/backend machine (Mythbuntu 8.10) with the default localhost IP address, so it's hard to imagine what's going on here.

The problem was cured by a reboot, but I'd be interested to know if there's anything I can do to stop it happening again.

Thanks
NM

---

### Post by uncle hammy on 2009-02-27
First guess, the backend service had crashed.  If it happens again, try simply restarted in the backend service and see if that resolves it.

---

### Post by parker13 on 2009-02-27
An error should still be in the logs:

/var/log/mythtv

You can restart the backend using:

```
sudo /etc/init.d/mythtv-backend restart
```

I also have a script for monitoring the backend. It may help until you find the problem:

[http://parker1.co.uk/mythtv_restart.php](http://parker1.co.uk/mythtv_restart.php)

---

### Post by newlinux on 2009-02-27
I use monit to monitor and keep my backend (and other services) up:

[http://www.mythtv.org/wiki/StatusMonitoringHowTo](http://www.mythtv.org/wiki/StatusMonitoringHowTo)

---

### Post by NautiusMaximus on 2009-02-28
Thanks for the suggestions. I've had a look in the log files, and found this:
> 
2009-02-26 08:35:11.390 Preview Error: Previewer file '/var/lib/mythtv/recordings/13866_20090226083508.mpg' is not valid.
2009-02-26 08:35:11.391 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/13866_20090226083508.mpg'
2009-02-26 08:35:11.398 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/13866_20090226083508.mpg.png) exists: 0 readable: 0 size: 0

Could this be relevant? Any idea what it means?

Thanks
NM

---

### Post by NautiusMaximus on 2009-02-28
The last post was from the backend log. I've found this in the frontend log, which looks like it could be more relevant:

> 2009-02-26 11:03:50.960 Event socket closed. No connection to the backend.
2009-02-26 18:33:13.327 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/ui.xml
2009-02-26 18:33:13.521 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-26 18:33:13.521 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-02-26 18:33:31.921 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-26 18:33:31.922 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-02-26 18:33:34.646 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-26 18:33:34.646 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-02-26 18:34:01.702 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-26 18:34:01.702 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-02-26 18:34:04.990 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-26 18:34:04.990 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-02-26 18:34:08.934 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-02-26 18:34:08.934 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
Destroying SipFsm object 
2009-02-26 18:34:16.866 Deleting UPnP client...
Starting mythfrontend.real..

Any ideas?

---

### Post by NautiusMaximus on 2009-03-07
I'm a bit confused by the message "You probably should modify the Master Server settings in the setup program and set the proper IP address."

Given that frontend and backend are on the same machine, I thought 127.0.0.1 was the proper IP address?

---

### Post by newlinux on 2009-03-07
what backend IP do you have set in the backend (mythtv-setup)? The actual IP or localhost? Try making sure they are the frontend and backend are using the exact same IP, even though localhost should point to right one.

---

