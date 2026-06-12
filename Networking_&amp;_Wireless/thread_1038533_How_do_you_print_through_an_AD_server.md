---
title: "How do you print through an AD server?"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by davidkazuhiro on 2009-01-12
I'm running Ubuntu and trying to print to a Sharp MX-4501N Printer/Copier but it is behind an Active Directory server. I tried putting in the IP of the server but nothing happens. I also tried doing that with pre-entering the AD credentials, but nothing.

Is there a program out there I have to install? Or is this not possible at all?

---

### Post by srt4play on 2009-01-12
Is the printer connected to the server via usb or to the network via cat5? If usb, does the print share show up if you try to browse to it in the Ubuntu printer configuration?

---

### Post by davidkazuhiro on 2009-01-14
It's connected to the network via cat5

---

### Post by srt4play on 2009-01-17
So, within the printer setup application, did you try entering the ip address of the printer and then choosing the make and model?  I just went through the printer setup process and saw there is a driver for Sharp MX-4501N.

---

### Post by davidkazuhiro on 2009-01-20
The printer can't be accessed by IP. It's in a subdirectory of a print server, which uses Active Directory authentication. The best I could do was the following:

smb://ps1/MX4501N

I used that and used the same drivers you mentioned noticing and put in my AD credentials. When I printed a test page, the printer whirred but nothing happened. I can print as many test pages I want without errors, but all it does is whir.

---

### Post by davidkazuhiro on 2009-01-20
oh and when I clicked "verify", it said that the print share was available.

---

### Post by davidkazuhiro on 2009-01-20
One thing I noticed is that usually in windows you have to put in the printer/copier code number to authenticate against the machine itself. However, I don't see a field for this in the Ubuntu printer setup. Are you aware of if or how that works in Ubuntu?

---

### Post by davidkazuhiro on 2009-01-20
Looks like it's actually not an AD issue, since it's making whirring noises.

I upgraded from 1.1 drivers (which came with Ubuntu) to 1.3 drivers, off of the sharp website. I still don't see any job handling option in the printer preferences. Normally in Windows, under the "Job Handling" tab there is a user number field. This is in Mac OS X as well. I can't see this option in the Ubuntu drivers... any ideas?

This lack of the Job Handling thing seems to be the issue here.

---

### Post by cariboo on 2009-01-20
Most of the printer configuration can be done using the cups web interface. Open you browser and in the address bar type:

[http://localhost:631](http://localhost:631)

You printer should be listed under printers if it iistalled properly.

Jim

---

### Post by davidkazuhiro on 2009-01-26
I took a look at the CUPS interface (thanks for showing, I never knew it existed), but didn't see any option called "Job Handling" or "User Number". I took a scan through the documentation too but didn't see anything there.

The printer needs me to enter a user number field for it to accept my print jobs.

Does anybody have a clue why I can't find this field in the Ubuntu interfaces?

---

### Post by nipquad on 2009-05-29
Did you ever find out how to enter a user number in the Sharp driver?  I am have exact same issue as stated above.

---

