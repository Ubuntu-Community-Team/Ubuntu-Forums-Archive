---
title: "Network Connection Logging"
date: 2010-11-10
forum: Networking &amp; Wireless
---

### Post by LaMbChOpS on 2010-11-10
Hi all,

Wondering if anyone can point me in the right direction to setup some form of network connection monitoring and logging?

As Australia has CRAP broadband and ISP's utilize Peak & Off-Peak download limits I schedule downloads for my Off-Peak times. 

Well recently my connection drops out exactly when my off-peak time kicks in and requires my modem to be reset to re-establish my connection. 

My ISP is denying they are doing this but I happens everyday now and is getting really frustrating. 

What I want to try and set up is some sort of monitoring to ping my ISP's default gateway so I can prove it drops at a specific time each day. 

I am sure there would be something I could configure in Ubuntu but I am a newbie to Ubuntu so don't really know how to achieve this.

I am running Ubuntu 10.10 using KDE 4.5.3.

Thanks for your help!!

Cheers.

---

### Post by Cheesehead on 2010-11-10
How do you connect to the internet? Through a router? Directly to the modem? Several clever solutions come to mind for different architectures.

A very simple solution using ping:

Step 1: Create a logfile.
```
touch my-ping-logfile
```

Step 2: Create a simple shell script to do one ping, timestamp it, and add the timestamped result to the logfile.
```
#!/bin/sh
TIMESTAMP =$(date)
PINGRESULT=$(ping -c1 www.google.com | grep packets)
echo $TIMESTAMP $PINGRESULT >> my-ping-logfile
```
Let's call this file pinger.sh.
The 'ping -c1' tells ping to just send a single ping. You can change that number.
You can change the URL you want to ping, of course.

Use this command to make the file executable.
```
chmod +x pinger.sh
```


Step 3: Create a cron job to run the script once every 10 minutes (You can easily change the frequency, as you can see below)
Use the command 'crontab -e' to access your crontab. Append to the bottom of the file a line that looks like the bottom row:
```
# m h  dom mon dow   command
*/10 * * * * /home/my-username/pinger.sh
```
To ping once each minute, just use '*' instead of '*/10'

That's it. Now it will ping whatever URL you wish as frequently as you wish (without flooding them), and save each result to a log. Just check the log regularly.


To remove all this:
Step 1: Remove the cron job. Use the command 'crontab -e' to open your crontab, and simply remove the entire pinger.sh line.

Step 2: Drag the 'pinger.sh' and 'my-ping-logfile' files to the trash.

---

### Post by LaMbChOpS on 2010-11-11
Awesome reply **Cheesehead** you are a legend!! :)

Got everything setup and it is working great, I tweaked the grep to include statistics so it also shows the website pinged. 

Thanks again for you time.

Cheers

---

