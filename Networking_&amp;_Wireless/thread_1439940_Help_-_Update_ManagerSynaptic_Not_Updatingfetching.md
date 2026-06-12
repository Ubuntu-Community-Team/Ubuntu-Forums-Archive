---
title: "Help - Update Manager/Synaptic Not Updating/fetching!"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by flashyrox on 2010-03-26
Hi There, please excuse my "newbness"

I am running NBR 9.10 

I recently used "Janitor" to clean up programs that I did not need, well apparently I must have let it accidently delete a critical program i did need!

**I am able to surf the internet, I am able to use apt-get in terminal to install packages without any problems.**

I am **unable** to fetch updates using update manager/software center/ or synaptic :

i get this error when trying to fetch updated packages or install new software with the gui programs mentioned above:

W:failed to fetch [http://ftp.iinet.net.au/pub/ubuntu/dists/karmic/](http://ftp.iinet.net.au/pub/ubuntu/dists/karmic/) release.gpg could not connect to 127.0.0.1:8118 (127.0.0.1) connect (111:connection refused) 

What i have tried to do so far, 

I have booted into recovery mode and repaired packages ( this updated my system but not much else)
I have installed wicd which removed network manager (did nothing)
then i installed nwm again and restarted ( did nothing)
then i tried to run sudo apt-get *clean *then *update *then *upgrade* ( did nothing)
then i removed synaptic manager and reinstalled it using apt-get (did nothing)
my resolve.conf file is empty and so is my apt.conf i dont know if this is normal
i have used different software sources other than iinet , i have used the main software source too.

I am not sure what to do, i would just like to restore the settings (which ever settings are controlling update manager/synaptic/swc)  to their original defaults but i dont know how.

I find it weird that apt-get is working and the internet is working normally but i am getting a local host / port refusal on the gui update apps ( swc, update manager and synaptic)

There must be a setting which is preventing the programs from using the local host address / port ??

Please help this is driving me nuts! im going round in circles :(

---

### Post by Trendane on 2010-03-26
I've been having a similar issue for a month and just solved it on my system.  I don't know if this will help you or not...but I hope so.

I looked in my system log ***(System > Administration > System Log)***  and saw several instances where the hostname had failed to resolve.

When I went and looked at /etc/hosts  I found that the hostname did not match what was in my /etc/hostname file (it still had my old domain name tacked on the end)

Once I set the name in /etc/hosts to match...the "Starting Administrative Application" window came up just fine and I was able to input my password.

---

### Post by flashyrox on 2010-03-26
Hi there, 

Thank you for your reply, 

I am running Ubuntu Netbook remix, 

I do not seem to have a etc/hostname or etc/hosts directory when i go to gedit and try to "edit" these files the result is blank. I am not sure if ubuntu nbr is setup differently to the desktop version.

---

### Post by flashyrox on 2010-03-27
I FIXED IT!!

If you are having a similar problem this may help you :

First , I ran synaptic package manager and temporarily used my isp's proxy to download any updates that were needed.

Secondly, I went into System > Network proxy 

and i noticed under "ignore" hosts i had 127.0.0.1/8

then i also noticed that there was no selection made under the proxy configuration tab, the checkbox "direct connection" nor "manual proxy" was checked..

anyway the things above seemed to solve my problem!!

---

### Post by flashyrox on 2010-03-27
OK...

seems to be working

---

